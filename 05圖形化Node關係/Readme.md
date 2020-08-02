圖形化Node關係
=

#### **安裝檔案**
```
$ sudo apt-get install ros-melodic-rqt
$ sudo apt-get install ros-melodic-rqt-common-plugins
```

#### **開新終端機** 
```
roscore
```
#### **開新終端機** 
```
rosrun turtlesim turtlesim_node
開啟烏龜程式
```
#### **開新終端機** 
```
rosrun turtlesim turtle_teleop_key  
讓你能使用方向鍵操控烏龜
```
#### **開新終端機** 
```
rosrun rqt_graph rqt_graph
圖形化
```
![img](https://github.com/TKTim/Ros_Tutorial/blob/master/%E5%9C%96%E5%BD%A2%E5%8C%96Node%E9%97%9C%E4%BF%82/1.png)
>由上可知，各Node的傳輸路徑


#### **開新終端機** 
```
rostopic echo /turtle1/cmd_vel 
```
![img](https://github.com/TKTim/Ros_Tutorial/blob/master/%E5%9C%96%E5%BD%A2%E5%8C%96Node%E9%97%9C%E4%BF%82/2.png)
>由於多了一個echo做偵測，因此傳輸多了一條topic。
---
## 參考網址
http://wiki.ros.org/ROS/Tutorials/UnderstandingTopics