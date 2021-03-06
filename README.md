## Description   
DOL 框架描述(随着实验进行迭代添加、修改) 
![image](https://cloud.githubusercontent.com/assets/22589015/19217664/45194f82-8e13-11e6-8c76-be07557b449b.png)
## How to install  
 DOL 安装笔记 

1. [下载文件](http://jingyan.baidu.com/article/c33e3f48a5c153ea15cbb5b2.html)(使用Vmware虚拟机，也可以从主机拷贝到虚拟机中)：
sudo wget http://www.accellera.org/images/downloads/standards/systemc/systemc-2.3.1.tgz
sudo wget http://www.tik.ee.ethz.ch/~shapes/downloads/dol_ethz.zip1

2. 解压文件
新建dol的文件夹 
$	mkdir dol
将dolethz.zip解压到 dol文件夹中
$	unzip dol_ethz.zip -d dol
解压systemc
$	tar -zxvf systemc-2.3.1.tgz

3. 编译systemc
解压后进入systemc-2.3.1的目录下
$	cd systemc-2.3.1
新建一个临时文件夹objdir
$	mkdir objdir
进入该文件夹objdir
$	cd objdir
运行configure(能根据系统的环境设置一下参数，用于编译)
$	../configure CXX=g++ --disable-async-updates
运行完之后如下图
![image](https://cloud.githubusercontent.com/assets/22589015/19217770/f6237cd8-8e15-11e6-957f-60b47f8f65cf.png)
$	sudo make install
编译完后文件目录如下($ cd ..        $ ls)，能看到include, lib-linux64(对于32位系统，这里是lib-linux)
![image](https://cloud.githubusercontent.com/assets/22589015/19217778/2a0d6824-8e16-11e6-8107-8a3fd2b16856.png)
记录当前的工作路径(会输出当前所在路径，记下来，待会有用)
$	pwd
![image](https://cloud.githubusercontent.com/assets/22589015/19217781/495dfe28-8e16-11e6-90d3-44e57a069cbe.png)
这里表示我当前的工作路径为 /home/wang/systemc-2.3.1

4. 编译dol
进入刚刚dol的文件夹
$	cd ../dol
修改build_zip.xml文件
找到下面这段话，就是说上面编译的systemc位置在哪里，
<property name="systemc.inc" value="YYY/include"/>
<property name="systemc.lib" value="YYY/lib-linux/libsystemc.a"/>
把YYY改成上页pwd的结果（注意，对于  64位 系统的机器，lib-linux要改成lib-linux64）
然后是编译
$	ant -f build_zip.xml all
若成功会显示build successful
接着可以试试运行第一个例子
进入build/bin/mian路径下
$	cd build/bin/main
然后运行第一个例子
$	sudo ant -f runexample.xml -Dnumber=1
成功结果如图
![image](https://cloud.githubusercontent.com/assets/22589015/19217793/9fade87e-8e16-11e6-8d48-79b3eb18fb92.png)

## Experimental experience   
在这次实验中，不但学会了怎样安装DOL，还学会了使用git、markdown，感觉自己的能力和逼格都得到了提升