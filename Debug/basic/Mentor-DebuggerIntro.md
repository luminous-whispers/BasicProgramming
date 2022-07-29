纯理论化的东西新同学不易接受, 决定以实践的方式进行介绍和传授, 具体形式如下:
1. 以命令行方式进行计算机系统介绍(文件系统)
2. 写一个demo文件, 先介绍c语言
3. 然后介绍debug

具体步骤如下:
1. 在cmd下介绍文件系统(echo, cd 和 dir命令, 树结构)
2. 环境变量设置(path, 安装mingw途中使用setx编辑环境变量)
	- setx Path "%Path%;path/to/mingw"(间接引用% %, 环境变量的作用)
3. 配置gcc:(不采用)
	- cd path/to/mingw/bin
	- mingw-get install gcc (默认从当前文件夹执行程序)
	- mingw-get install g++
	- mingw-get install gdb
	- minw-get install mingw32-make

4. 配置clang:
	- 命令: where clang, clang --version
	- linux下:
```bash
sudo apt-get update
dpkg --get-selections | grep hold
sudo apt-get autoremove

sudo apt-get install clang
```