###*Cartographer的安装与测试*
####一、安装所有依赖项
使用命令：</br>

	sudo apt-get install -y google-mock libboost-all-dev  libeigen3-dev libgflags-dev libgoogle-glog-dev liblua5.2-dev libprotobuf-dev  libsuitesparse-dev libwebp-dev ninja-build protobuf-compiler python-sphinx  ros-indigo-tf2-eigen libatlas-base-dev libsuitesparse-dev liblapack-dev
![](https://ooo.0o0.ooo/2016/11/11/5825c38b92c25.png)
####二、安装ceres solver
#####（1）执行命令
 	git clone https://github.com/hitcm/ceres-solver-1.11.0.git
![](https://ooo.0o0.ooo/2016/11/11/5825c38b735de.png)
#####（2）
######A、进入ceres-solver-1.11.0，新建一个文件夹build，然后再进入该文件夹
![](https://ooo.0o0.ooo/2016/11/11/5825c38b72dec.png)
######B、执行命令：
	cmake ..
![](https://ooo.0o0.ooo/2016/11/11/5825c38c0aa23.png)
######C、执行命令：
	make
![](https://ooo.0o0.ooo/2016/11/11/5825c38c0c5f0.png)
######D、执行命令：
	sudo make install
![](https://ooo.0o0.ooo/2016/11/11/5825c38c52842.png)
####三、安装 cartographer
#####（1）执行命令：
	git clone https://github.com/hitcm/cartographer.git
![](![](https://ooo.0o0.ooo/2016/11/11/5825c38c21f2a.png))
#####（2）执行命令：
	cd ceres-solver-1.11.0/build
	cmake ..
![](https://ooo.0o0.ooo/2016/11/11/5825c38c64458.png)
#####（3）执行命令：
	make
![](https://ooo.0o0.ooo/2016/11/11/5825c3b98eb9d.png)
#####（4）执行命令：
	sudo make install
![](https://ooo.0o0.ooo/2016/11/11/5825c3b9887ee.png)
####四、安装cartographer_ros
#####（1）执行命令：
	mkdir catkin_ws
	cd catkin_ws
	mkdir src
	cd src
![](https://ooo.0o0.ooo/2016/11/11/5825c3b8a8bc5.png)
#####（2）执行命令：
	git clone https://github.com/hitcm/cartographer_ros.git
![](https://ooo.0o0.ooo/2016/11/11/5825c3b8d841c.png)
#####（3）执行命令：
	cd ..
 	catkin_make
![](https://ooo.0o0.ooo/2016/11/11/5825c3ba101b2.png)
####五、下载demo，用于测试
######2d数据：
	wget -P ~/Downloads https://storage.googleapis.com/cartographer-public-data/bags/backpack_2d/cartographer_paper_deutsches_museum.bag
![](https://ooo.0o0.ooo/2016/11/11/5825c3c403cce.png)
####六、运行测试数据
######执行命令：
	roslaunch cartographer_ros demo_backpack_2d.launch bag_filename:=${HOME}/Downloads/cartographer_paper_deutsches_museum.bag
######运行结果截图：
![](https://ooo.0o0.ooo/2016/11/11/5825c6b96a7d8.png)
</br></br>
如果出现以下问题：</br></br>
![](https://ooo.0o0.ooo/2016/11/11/5825c3b9cd74a.png)
</br></br>使用一下命令行语句即可：
	
	source ~/catkin_ws/devel/setup.bash
	rospack profile
![](https://ooo.0o0.ooo/2016/11/11/5825c3b962124.png)

####七、实验感想
##########&#160; &#160; &#160; &#160;本次实验主要是根据[博客](http://www.cnblogs.com/hitcm/p/5939507.html)上的教程来实现的，根据教程遇到的问题比较少，而且最终也能成功实现运行cartographer的测试样例。而且通过本次实验，也让我了解了cartographer。它是一款制图工具，该技术利用同步定位与制图技术(SLAM)绘制室内建筑平面图，能同时用于二维与三维空间的移动映射。
##########&#160; &#160; &#160; &#160;同时，开源 Cartographer 还搭配有开源机器人操作系统(ROS)，使得该技术库更易于部署机器人、无人驾驶、无人机等系统。SLAM 技术是自动驾驶平台最重要的技术部分，适用于无人驾驶、仓库自动叉车、吸尘机器人和无人机等。Cartographer 基于此创建了全球范围内的实时地图，并且结合 ROS 及其他外部技术支持，Cartographer 现已经支持 Toyota HSR、TurtleBots、PR2、Revo LDS 这几个机器人平台。