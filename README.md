# gcc-upgrade 
ubuntu gcc g++升级方法

1、添加源

sudo add-apt-repository ppa:ubuntu-toolchain-r/test
sudo apt-get update
2、安装 gcc-6、g++-6

sudo apt-get install gcc-6 g++-6
3、配置 gcc，g++ 链接

我们查看系统当前使用的 gcc，发现是个符号链接：

ll /usr/bin/gcc
lrwxrwxrwx 1 root root 5 Nov 16 16:49 gcc -> gcc-5
g++ 也是：

ll /usr/bin/g++
lrwxrwxrwx 1 root root 5 Nov 16 16:49 g++ -> g++-5
所以我们重定向 gcc 链接到 gcc-6 即可：

cd /usr/bin
sudo sudo rm gcc
sudo ln -s gcc-6 gcc
同样 g++ 重新链接到 g++-6：

sudo rm g++
sudo ln -s g++-6 g++
重新查看下 gcc、g++ 的链接：

ll /usr/bin/gcc
lrwxrwxrwx 1 root root 5 Nov 16 16:49 gcc -> gcc-6

ll /usr/bin/g++
lrwxrwxrwx 1 root root 5 Nov 16 16:49 g++ -> g++-6
顺便查看下 gcc、g++ 的版本：

gcc --version

gcc (Ubuntu 6.5.0-2ubuntu1~16.04) 6.5.0 20181026
Copyright (C) 2017 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
g++：

g++ --version

g++ (Ubuntu 6.5.0-2ubuntu1~16.04) 6.5.0 20181026
Copyright (C) 2017 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
