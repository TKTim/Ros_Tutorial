了解 ROS Nodes
=

* Nodes：節點是使用ROS與其他節點通信的可執行文件。 
* Messages：訂閱或發布主題時使用的ROS數據類型。 
* Topics：節點可以將消息發佈到主題，也可以訂閱主題以接收消息。 
* Master：ROS的名稱服務（即幫助節點彼此查找）
* rosout：等效於 stdout / stderr 
* roscore：主服務器+ rosout +參數服務器（稍後將介紹parameter server(參數服務器)）

## 1.Nodes
>節點實際上只不過是ROS包中的可執行文件而已。 ROS節點使用ROS客戶端庫與其他節點進行通信。節點可以發布或訂閱主題。節點也可以提供或使用服務。

## 2.補充
* rospy = python client library
* roscpp = c++ client library

## 3. 進入實驗

### 1. roscore
>照裡來說，roscore會是你第一個輸入的指令。

### 2.rosnode
**開新的終端機**
```
$ rosnode list （秀出正在運行的Node）

$ rosnode info /rosout（用來檢查node運行狀況）
```
```
root@user-WS-ESC700-G4-WS880T-E700-G4:/home/user# rosnode list
/rosout
root@user-WS-ESC700-G4-WS880T-E700-G4:/home/user# rosnode info /rosout
--------------------------------------------------------------------------------
Node [/rosout]
Publications: 
 * /rosout_agg [rosgraph_msgs/Log]

Subscriptions: 
 * /rosout [unknown type]

Services: 
 * /rosout/get_loggers
 * /rosout/set_logger_level


contacting node http://user-WS-ESC700-G4-WS880T-E700-G4:36173/ ...
Pid: 14349


```
>為了讓我們看的到更多信息，我們來用一個試用程式。

### 3.rosrun
**開新的終端機**
##### 用法：
```
$ rosrun [package_name] [node_name]  (不要輸入這行)

$ rosrun turtlesim turtlesim_node
```
![img](https://github.com/TKTim/Ros_Tutorial/blob/master/%E4%BA%86%E8%A7%A3Node_in_Ros/03.png)


### 4. 回到rosnode的終端機
```
root@user-WS-ESC700-G4-WS880T-E700-G4:/home/user# rosnode list
/rosout
/turtlesim
root@user-WS-ESC700-G4-WS880T-E700-G4:/home/user# rosnode info /turtlesim 
--------------------------------------------------------------------------------
Node [/turtlesim]
Publications: 
 * /rosout [rosgraph_msgs/Log]
 * /turtle1/color_sensor [turtlesim/Color]
 * /turtle1/pose [turtlesim/Pose]

Subscriptions: 
 * /turtle1/cmd_vel [unknown type]

Services: 
 * /clear
 * /kill
 * /reset
 * /spawn
 * /turtle1/set_pen
                   .
                   .
                   .

```

### 5.更換Node名稱
```
$ rosrun turtlesim turtlesim_node __name:=my_turtle
```
>輸入後Node的名稱會變成 my_turtle，若想將程序停止，只需要Ctrl+c。


### 參考網站

##### http://wiki.ros.org/ROS/Tutorials/UnderstandingNodes