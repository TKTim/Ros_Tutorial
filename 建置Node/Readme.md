建置Node
=

還記得我們在[了解Ros指令和catkin_package]()時，我們建立了自己的catkin工作環境，也建立了引用 **std_msgs** 、**rospy**、 **roscpp**的pkg。 現在我們就要利用 **rospy** 來寫一個簡單的應用程式。

1. 下載talker .py

```
$ cd ~/catkin_ws/src/beginner_tutorials  (你的位置)
$ mkdir scripts
$ cd scripts
$ wget https://raw.github.com/ros/ros_tutorials/kinetic-devel/rospy_tutorials/001_talker_listener/talker.py
$ chmod +x talker.py
```

2. 將以下程式碼放入 CMakeLists.txt
```
catkin_install_python(PROGRAMS scripts/talker.py
  DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)
```

3. 解析talker. py

   ```
   1 #!/usr/bin/env python   //使用python
   2 # license removed for brevity
   3 import rospy            //編寫node文件，必須引用rospy
   4 from std_msgs.msg import String //可以讓我們使用字串符
   5 
   6 def talker():
   7     pub = rospy.Publisher('chatter', String queue_size=10)
   //定義talker()
   //pub可稱作**發布者**。
   //將其發佈在chatter主題(topic)裡，利用String型態。
   //如果設置queue_size=10，即如果收到的數據大於10，則將開始拋棄最初收到的第一個數據。
   ```

   ```
   8     rospy.init_node('talker', anonymous=True)
   //初始化名為 "talker"的node，anonymous=True 通過在NAME的末尾添加隨機數來確保您的節點具有唯一名稱。
   9     rate = rospy.Rate(10) # 10hz
   //每秒經過10次循環
   10     while not rospy.is_shutdown():
   11         hello_str = "hello world %s" % rospy.get_time()
   //輸出字串(hello + time)
   ```
   ```
   12         rospy.loginfo(hello_str)
   //loginfo() 做三件事
     1.打印到屏幕上。
     2.被寫入節點的日誌文件，也就是node。
     3.並被寫入rosout。 rosout是一個方便的調試工具，之後會說到。
   
   13         pub.publish(hello_str)
   14         rate.sleep()
   15 
   ```
   ```
   16 if __name__ == '__main__':
   17     try:
   18         talker()
   19     except rospy.ROSInterruptException:
   20         pass
   //用意為，若是程式遭到Ctrl+c或強制關閉，便會停止再次運行talker。

4.下載 listener. py
```
$ roscd beginner_tutorials/scripts/
$ wget https://raw.github.com/ros/ros_tutorials/kinetic-devel/rospy_tutorials/001_talker_listener/listener.py
$ chmod +x listener.py
```

5. 將以下程式碼在 CMakeLists.txt 更改
```
catkin_install_python(PROGRAMS scripts/talker.py scripts/listener.py
  DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)
```

6. 解析 listener. py

```
   1 #!/usr/bin/env python
   2 import rospy
   3 from std_msgs.msg import String
   4 
   5 def callback(data):
   6     rospy.loginfo(rospy.get_caller_id() + "I heard %s", data.data)
   7     
   8 def listener():
   9 
  10     # In ROS, nodes are uniquely named. If two nodes with the same
  11     # name are launched, the previous one is kicked off. The
  12     # anonymous=True flag means that rospy will choose a unique
  13     # name for our 'listener' node so that multiple listeners can
  14     # run simultaneously.
  15     rospy.init_node('listener', anonymous=True)
  16 
  17     rospy.Subscriber("chatter", String, callback)
  18 
  19     
  20     rospy.spin()
  // spin（）只是阻止python退出直到該節點停止
  21 
  22 if __name__ == '__main__':
  23     listener()
```

我把實驗結果錄了下來
可以到[這裡](https://www.youtube.com/watch?v=x2IFQINL8tM)看看
