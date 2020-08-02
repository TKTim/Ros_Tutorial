了解catkin_make下載下來的package
=
#### 就如標題所示，我們很常從github上下載catkin檔案夾，現在來看看怎麼build他。

```
# In a CMake project
$ mkdir build
$ cd build
$ cmake ..
$ make
$ make install  # (optionally)
```
#### 基本上，不外乎上面幾個指令，那如果今天載下來的是workspace你可以這麼做。
```
# In a catkin workspace
$ catkin_make
$ catkin_make install  # (optionally)
```
#### 如果你要引用的source在別的地方，你可以用：
```
# In a catkin workspace
$ catkin_make --source my_src
$ catkin_make install --source my_src  # (optionally)
```



---
## 參考網站

http://wiki.ros.org/ROS/Tutorials/BuildingPackages