## **Descripiton**
DOL属于分布式操作系统，是一个软件，它是许多独立的，网络连接的，通讯的，并且物理上分离的计算节点的集合。每个节点包含全局总操作系统的一个特定的软件子集。每个软件子集是两个不同的服务置备的复合物。第一个服务是一个普遍存在的最小的内核，或微内核，直接控制该节点的硬件。第二个服务是协调节点的独立的和协同的活动系统管理组件的更高级别的集合。这些组件抽象微内核功能，和支持用户应用程序。  
分布式操作系统是分布式软件系统的重要组成部分，负责管理分布式处理系统资源、控制分布式程序运行等。  
分布式软件系统是支持分布式处理的软件系统，包括分布式操作系统、分布式程序设计语言及其编译(解释)系统、分布式文件系统和分布式数据库系统等。  
分布式操作层（DOL）是一个软件开发框架编程并行应用程序。DOL允许指定的基础上计算的Kahn过程网络模型应用程序和功能的基础上的SystemC模拟引擎。此外，DOL还提供了一个基于XML的规范格式来描述在一个多处理器系统，包括绑定和映射并行应用程序的执行。
## **How to install**  
#### **在ubuntu上安装一些必要的环境：**  
运行代码：   

    $	sudo apt-get update    
	$	sudo apt-get install ant  
	$ 	sudo apt-get install openjdk-7-jdk  
	$	sudo apt-get install unzip  

运行结果：  
<br />
<img src="https://cl.ly/1e0b2y2k312w/update.png" width = "400" height = "300"/>
<img src="https://cl.ly/360a3q032O03/install%20ant.png" width = "400" height = "300"/>
<img src="https://cl.ly/1D0O0f0X2339/install%20openjdk.png" width = "400" height = "300"/>
<img src="https://cl.ly/0u0U22051L0M/install%20unzip.png" width = "400" height = "300"/>
  
#### **下载systemc-2.3.1.tgz和dol_ethz.zip：**
运行代码：

    sudo wget http://www.accellera.org/images/downloads/standards/systemc/systemc-2.3.1.tgz
	sudo wget http://www.tik.ee.ethz.ch/~shapes/downloads/dol_ethz.zip

运行结果：
<br />
<img src="https://cl.ly/0j0H0M3Q173c/systemc-2.3.1.tgz.png" width = "400" height = "300"/>
<img src="https://cl.ly/2P383w1s1c3B/dol_ethz.png" width = "400" height = "300"/>


#### **解压文件**
运行代码：

    新建一个文件夹dol:  
	$	mkdir dol  
	将dolethz.zip解压到 dol文件夹中:
	$	unzip dol_ethz.zip -d dol  
	解压systemc:
	$	tar -zxvf systemc-2.3.1.tgz
<br />
运行结果：</br>
<img src="https://cl.ly/1M0g1u2D1g2C/mkdir%20dol.png" width = "400" height = "300"/>  
<img src="https://cl.ly/2Q1x1E1k0z3t/unzip.png" width = "400" height = "300"/>  
<img src="https://cl.ly/310J2t0f3m1e/unzip%20systemc-2.3.1.png" width = "400" height = "300"/> 

#### **编译systemc**
运行代码：

	解压后进入systemc-2.3.1的目录下
	$	cd systemc-2.3.1
	新建一个临时文件夹objdir
	$	mkdir objdir
	进入该文件夹objdir
	$	cd objdir
	运行configure(能根据系统的环境设置一下参数，用于编译)
	$	../configure CXX=g++ --disable-async-updates
	编译
	$	sudo make install
	查看编译完后文件目录
	$ cd ..        $ ls
	记录当前的工作路径
	$	pwd
<br />
运行结果:

![icon](https://cl.ly/233w0E331h3p/cd-mkdir.png)
<img src="https://cl.ly/341s3z3w092k/configure.png" width = "400" height = "300"/>
<img src="https://cl.ly/2M2x0m0h3f1j/sudo%20make%20install.png" width = "400" height = "300"/>

![icon](https://cl.ly/3P120W3W2F19/cdls.png)

#### **编译dol**
运行代码：

	进入刚刚dol的文件夹
	$	cd ../dol
	修改build_zip.xml文件
	<property name="systemc.inc" value="YYY/include"/>
	<property name="systemc.lib" value="YYY/lib-linux/libsystemc.a"/>
	编译
	$	ant -f build_zip.xml all
	进入build/bin/mian路径下
	$	cd build/bin/main
	然后运行第一个例子
	$	ant -f runexample.xml -Dnumber=1
	
运行结果：

![icon](https://cl.ly/38152m441i2z/into.png)<br />
修改dol文件：<br />
![icon](https://cl.ly/2J1J011e151c/build_zip.png)<br />
运行第一个例子：<br />
<img src="https://cl.ly/1K1o1O1e0d0i/first.png" width = "400" height = "300"/>
<img src="https://cl.ly/25020l1n1K2G/success.png" width = "400" height = "300"/>

## **Experimental experience** 
本次实验让我初步了解了分发式操作层DOL。安装过程中也遇到了一些问题，以下是我遇到的问题以及解决方法：  
**问题1：**
在运行configure(即../configure CXX=g++ --disable-async-updates)的时候出现了一下错误：<br />
![icon](https://cl.ly/0a3u2P0d0d2x/problem1.png)
<br />
**解决方法：**
这应该是编译环境出现了问题,采用一下命令行即可解决：
	
	sudo apt-get install build-essential

**问题2：**
在运行第一个例子的时候出现了“BUILD FAILED”

	ant -f runexample.xml -Dnumber=1
<br />
**解决方法：**
在配置configure的时候把PPT里面的命令行替换成以下命令行，其他继续往下执行：

	../configure --prefix=/usr/local/systemc-2.3.1
此是参考 
> [构建linux下SystemC编译环境](http://blog.chinaunix.net/uid-8867796-id-358801.html)
