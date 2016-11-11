###*ROS的配置*
####一、配置过程
####1.1 配置Ubuntu软件仓库
####1.2 添加 sources.list
	sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
 ![](https://ooo.0o0.ooo/2016/11/11/5825b6ec17048.png)
####1.3 添加 keys
	sudo apt-key adv --keyserver hkp://pool.sks-keyservers.net --recv-key 0xB01FA116
![](https://ooo.0o0.ooo/2016/11/11/5825b6f2a2d29.png)
####1.4 安装
#####(1)确保Debian软件包索引是最新的
使用命令：</br>

	sudo apt-get update
![](https://ooo.0o0.ooo/2016/11/11/5825b6f804476.png)
#####(2)桌面完整版安装
使用命令：</br>
	
	sudo apt-get install ros-jade-desktop-full
![](https://ooo.0o0.ooo/2016/11/11/5825b6fcc79f7.png)
####1.5 初始化 rosdep
使用命令：</br>
	
	sudo rosdep init
	rosdep update
![](https://ooo.0o0.ooo/2016/11/11/5825b704bdf25.png)
</br>
</br>
![](https://ooo.0o0.ooo/2016/11/11/5825b71035d39.png)
####1.6 环境配置
使用命令：</br>
	
	echo "source /opt/ros/jade/setup.bash" >> ~/.bashrc
	source ~/.bashrc
![](https://ooo.0o0.ooo/2016/11/11/5825b71e1729b.png)
####1.7 安装rosinstall
>rosinstall 是ROS中一个独立分开的常用命令行工具，它可以方便让你通过一条命令就可以给某个ROS软件包下载很多源码树。

使用命令：</br>
	
	sudo apt-get install python-rosinstall
![](https://ooo.0o0.ooo/2016/11/11/5825b724a3744.png)

以上ROS已经配置完毕

####二、实验感想
#####&#160; &#160; &#160; &#160;配置过程还是挺简单的，按照教程基本上能挺快完成的。通过本次实验，我对ROS（Robot operation system）有了一定的了解。ROS是开源的，是用于机器人的一种后操作系统，或者说次级操作系统。它提供类似操作系统所提供的功能，包含硬件抽象描述、底层驱动程序管理、共用功能的执行、程序间的消息传递、程序发行包管理，它也提供一些工具程序和库用于获取、建立、编写和运行多机整合的程序。ROS的首要设计目标是在机器人研发领域提高代码复用率。ROS是一种分布式处理框架(又名Nodes)。这使可执行文件能被单独设计，并且在运行时松散耦合。这些过程可以封装到数据包(Packages)和堆栈(Stacks)中，以便于共享和分发。ROS还支持代码库的联合系统。使得协作亦能被分发。这种从文件系统级别到社区一级的设计让独立地决定发展和实施工作成为可能。上述所有功能都能由ROS的基础工具实现。