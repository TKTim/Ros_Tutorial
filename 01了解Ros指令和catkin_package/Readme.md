# 使用Ros指令

---
## 1.　Using rospack

>rospack允許你獲取有關package的信息。
```
$ rospack find <PackageName>
```
## 2.　Using roscd

>roscd 讓你能夠移動到package的目錄下
```
$ roscd <PackageName>
```
### 實驗：
> 先使用reospack查詢 "roscpp"的位置，不使用cd而是使用roscd移動到目錄下。

![img](https://github.com/TKTim/Ros_Tutorial/blob/master/%E4%BA%86%E8%A7%A3Ros%E6%8C%87%E4%BB%A4%E5%92%8Ccatkin_package/01.png)

>！！！但是要記住的是使用這些方法查詢的package一定要是在ROS_PACKAGE_PATH中的。

## 3. 查詢ROS_PACKAGE_PATH收錄的位置
```
$ echo $ROS_PACKAGE_PATH

```
## 4. 使用 roscd log
>roscd日誌將帶您到ROS存儲日誌文件的文件夾。請注意，如果尚未運行任何ROS程序，這將產生一條錯誤消息，指出它尚不存在。 如果您以前運行過一些ROS程序，請嘗試：
```
$ roscd log
```

## 5. 使用 rosls
>有cd，當然就要有ls拉。
```
$ roscd <PackageName>
```

製作一個Package
=
---

>要稱為catkin的package，必須滿足一些要求：該軟件包必須包含兼容catkin的package.xml文件。package.xml文件提供有關軟件包的元信息。另外還需要包含使用catkin的CMakeLists.txt。大概長這樣：
```
my_package/
  CMakeLists.txt
  package.xml
```
## 6. Catkin 資料夾應該要長的樣子
```
workspace_folder/        -- WORKSPACE
  src/                   -- SOURCE SPACE
    CMakeLists.txt       -- 'Toplevel' CMake file, provided by catkin
    package_1/
      CMakeLists.txt     -- CMakeLists.txt file for package_1
      package.xml        -- Package manifest for package_1
    ...
    package_n/
      CMakeLists.txt     -- CMakeLists.txt file for package_n
      package.xml        -- Package manifest for package_n
```

## 7. 試著設立自己的檔案夾
>在做這一部份時，先前再安裝Ros時，你應該要將catkin_workplace建立起來
，若是沒有的話，到[這裡](http://wiki.ros.org/catkin/Tutorials/create_a_workspace)再看清楚吧！ 記得按照自己的版本安裝，我是Melodic。

>現在，使用catkin_create_pkg腳本創建一個名為“ beginner_tutorials”的新程序包，該程序包取決於std_msgs，roscpp和rospy：
```
$ catkin_create_pkg beginner_tutorials std_msgs rospy roscpp
```
>這會創建一個beginner_tutorials文件夾，裡面會有剛剛說的package.xml和CMakeLists.txt，其中已經放入了你剛剛給catkin_create_pkg的信息，也就是上面那行指令。

## 8. Build剛剛設立的檔案夾
```
$ cd ~/catkin_ws
$ catkin_make

$ . ~/catkin_ws/devel/setup.bash
$ source /root/catkin_ws/devel/setup.bash

```
>前兩行是將我們剛剛新增與修改的行為編入整個檔案中，後面那一行，則是將這台電腦能根據這個檔案找到一切需要的東西。最後一行為設定環境變數。

## 9. 補充應用

```
$ rospack depends1 beginner_tutorials 

$ rospack depends beginner_tutorials
```
>第1行指令能為你顯示你在建立時給予他的依賴檔案，後面一句則是因為依賴檔案是有很多連結的，他可以透過遞歸確定所有嵌套的依賴項。

>另外如果遇到比較細節的package.xml問題了話，建議你花點時間細看[官方網站](http://wiki.ros.org/ROS/Tutorials/CreatingPackage)第6點的部份。

---
## 參考網站

 http://wiki.ros.org/ROS/Tutorials/NavigatingTheFilesystem
 http://wiki.ros.org/ROS/Tutorials/CreatingPackage




