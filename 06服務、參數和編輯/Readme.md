ROS 服務、參數和編輯
=

Service
-
>rosservice可以通過服務輕鬆附加到ROS的客戶端/服務框架。 rosservice有許多可用於服務的命令，有點類似給你正在開啟的程式下指令：
```
rosservice list         print information about active services
rosservice call         call the service with the provided args
rosservice type         print service type
rosservice find         find services by service type
rosservice uri          print service ROSRPC uri
```

```
利用
$ rosservice list 可以顯示已開啟節點內的所有服務
例如
/clear
/kill
/reset
```
```
若要使用他們可利用
rosservice type [service]
實作的部分，我就不多解釋了，可以就由本文下方的網址去練習。
```

---

Parameter
-
>rosparam允許您在ROS參數服務器上存儲和處理數據。參數服務器可以存儲整數，浮點數，布爾值，字典和列表，透過設定參數來更改顯示或是輸出。
```
rosparam set            set parameter
rosparam get            get parameter
rosparam load           load parameters from file
rosparam dump           dump parameters to file
rosparam delete         delete parameter
rosparam list           list parameter names
```

```
至於怎麼用，其實大同小異
$ rosservice type /clear    這一行便能拿來清除turtlesim之前的路徑
$ rosservice call /spawn 2 2 0.2 "" 在指定位置新增turtle
```
---
rosed 
-
>顧名思義，就是拿來編輯ros內文件的，但有一個蠻酷的用法。
```
用法
$ rosed [package_name] [filename]
實例
$ rosed roscpp Logger.msg
下面這行，會幫你顯示 [package_name] 內的檔案，算是很實用的。
$ rosed [package_name] <tab><tab>
```

---
## 參考網站
http://wiki.ros.org/ROS/Tutorials/UnderstandingServicesParams
