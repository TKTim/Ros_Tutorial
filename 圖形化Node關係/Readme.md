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
![img]()
>由上可知，各Node的傳輸路徑


#### **開新終端機** 
```
rostopic echo /turtle1/cmd_vel 
```
![img]()
>由於多了一個echo做偵測，因此傳輸多了一條topic。