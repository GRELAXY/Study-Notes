# 工程创建



[真的很喜欢小鱼，这本书很适合新手](https://fishros.com/d2lros2/#/)（以下基本都是看书笔记）

## 一、节点

### 1.是什么

每一个节点只负责一个**单独的模块化的功能**

（比如一个节点负责控制车轮转动，一个节点负责从激光雷达获取数据、一个节点负责处理激光雷达的数

据、一个节点负责定位等等）

___



### 2.节点的交互方式

- 话题、服务、参数、动作，具体介绍在 前置.md 里介绍力

___



### 3. 节点相关的CLI

CLI（Command-Line Interface）：终端或者命令行界面

#### （1）启动节点:+1:

````python
ros2 run <package_name> <executable_name>

#package_name:功能包名字
#executable_name:可执行节点名
````

#### （2）查看节点列表:+1:

````python
ros node list
````

#### （3）查看节点信息:+1:

````python
ros2 node info <node_name>
````

#### （4）重映射节点名称

````python
ros2 run <package_name> <executable_name> --ros-args --remap __node:=<name>

例如：
ros2 run turtlesim turtlesim_node --ros-args --remap __node:=my_turtle
````

#### （5）运行节点时设置参数

````python
ros2 run example_parameters_rclpy parameters_basic --ros-args -p rcl_log_level:=10
````

___



### 4.创建和运行节点:fire:

#### 创建节点

````python
#导入创建节点的库
import rclpy
from rclpy.node import Node

def main():
    rclpy.init() #初始化，分配资源
    mynode = Node("python_node") #创建Node类的节点变量，传入参数为节点名
    rclpy.spin(mynode)#运行节点，阻塞式，不打断或者退出就会一直运行
    rclpy.shutdown()#关闭节点
    
    
if __name__=="__main__":
    main()
````

#### setup.py定义可执行节点

如果有一个名为 `my_node.py` 的节点文件，路径为 `my_package/my_node.py`，并且节点的入口函数是 `main()`，则可以这样配置：

````python
entry_points={
    'console_scripts': [
        'my_node = my_package.my_node:main',
    ],
},
````

- `my_node`：可执行文件的名称（在终端中运行的命令）。
- `my_package.my_node`：Python 模块的路径。
- `main`：节点的主函数。

___




在终端里运行脚本：

````
pyhthon3 文件名
````

运行后可以用`ros2 node list`来查看运行的节点

#### 打印日志

≈print

````python
def main():
    rclpy.init() 
    mynode = Node("python_node") 
    mynode.get_logger().info('节点已经创建')#打印日志，用info级别打印出（）内的内容
    rclpy.spin(mynode)
    rclpy.shutdown()
````

打印出的日志包括：

`[级别][打印时候的时间][节点的名字]：内容`

级别用：

- Info
- Warn

##### 改变打印处的日志格式

在终端中用`export`修改环境变量`RCUTILS_CONSOLE_OUTPUT_FORMAT`

````
export RCUTILS_CONSOLE_OUTPUT_FORMAT =[{function_name}:{line_number}]:{message} 
#打印出的格式：
[main:7]:节点已经创建
````

#### 打断节点运行

在Linux中，节点运行后可以用`ctrl+C`打断命令运行



___



## 二、功能包和工作空间

功能包和工作空间和节点的关系：工作空间->功能包->节点

*一个工作空间下可以有多个功能包，一个功能包可以有多个节点存在*

### 1.介绍

#### 工作空间&创建

工作空间一般包含`src`、`build`、`install`、`log`这几个目录，其中`src`目录用于存放 ROS 2 软件包的源代码，`build`目录用于存放编译过程中生成的中间文件，`install`目录用于存放编译好的软件包。`log` 目录包含有关每个`colcon`调用的各种日志信息

> 小鱼said：工作空间是包含若干个功能包的**目录**，一开始大家把工作空间理解成一个文件夹就行了。这个文件夹包含下有`src`（用于放ROS的源代码）。所以一般新建一个工作空间的操作就和创建文件夹一样

````
mkdir  ~/ros2_worksapce_name/src
cd ~/ros2_worksapce_name/src
````

然后就在src目录下安装or创建功能包

之后用`colcon`构建完成后，在`src`同级目录会看到 `build` 、 `install` 和 `log` 目录

#### 功能包

功能包可以理解为存放节点的地方，ROS2中功能包根据**编译方式**的不同分为三种类型。

- ament_python，适用于python程序
- cmake，适用于C++
- ament_cmake，适用于C++程序,是cmake的增强版

~~但目前俺只会用python捏所以俺们只记python捏~~

### 2.创建（获取）功能包

#### 安装获取

直接

````python
sudo apt install ros-<version>-package_name
````

#### 手动编译安装

> 如果作者没有测试上传可执行文件到仓库里就不能直接apt安装，需要手动编译安装力（悲）
>
> or要对功能包的源代码进行修改时也需要手动编译安装（显然俺还没到这境界）



#### 功能包相关的CLI 

ros2 pkg

##### （1）创建功能包:fire:

- 在src目录下创建or克隆（git clone 网址）

```
ros2 pkg create <package-name>  --build-type  ament_python  --dependencies <依赖名字>
```

一般来说dependencies选`rclpy`捏（`rclpy` 是 ROS 2 的 Python 客户端库）

##### （2）列出可执行文件

列出所有

```
ros2 pkg executables
```

列出功能包的所有可执行文件

```
ros2 pkg executables <package_name> 
```

##### （3）列出所有功能包

````
ros2 pkg list
````

##### （4）输出某个包所在路径的前缀

```
ros2 pkg prefix  <package-name>
```

比如小乌龟

```
ros2 pkg prefix turtlesim
```

###### （5）列出包的清单描述文件

> 每一个功能包都有一个标配的manifest.xml文件，用于记录这个包的名字，构建工具，编译信息，拥有者，干啥用的等信息。
>
> 通过这个信息，就可以自动为该功能包安装依赖，构建时确定编译顺序等

```
ros2 pkg xml <package-name> 
```

### 3.编译工作空间

回到工作空间的根目录下用`colcon`工具来编译

````
cd ~/ros2_worksapce_name
colcon build
````

#### 补充`colcon`指令:
(1)只编译一个包：`colcon build --packages-select YOUR_PKG_NAME `



(2)不编译测试单元:`colcon build --packages-select YOUR_PKG_NAME  --cmake-args -DBUILD_TESTING=0Copy to clipboardErrorCopied`

(3)运行编译的包的测试
`colcon testCopy to clipboardErrorCopied`

(4)允许通过更改src下的部分文件来改变install（重要）

#### 每次调整 python 脚本时都不必重新build了
==`colcon build --symlink-install`==

*每个节点build的时候都要来一次*

### 4.运行节点

编译之后cd到创建的工作空间

先source一下资源

````
source install/setup.bash
````

然后就按之前的 `ros2 run <package_name> <executable_name> `
