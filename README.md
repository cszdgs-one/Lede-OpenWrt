会本地编译的可以在本地提取.config文件夹
把要加的插件都用git clone下载到package文件夹里面
清除.config配置（可执行可不执行）：rm -rf ./tmp && rm -rf .config
更新源码：git pull
下载源+插件：./scripts/feeds update -a
安装源+插件：./scripts/feeds install -a
选好配置：make menuconfig
生成.config：make defconfig
差异部分就写入：./scripts/diffconfig.sh > seed.config
提取.config：cat seed.config
运行cat seed.config后在SSH中显示很多CONFIG的，那些就是了，都复制起来粘贴到github的diy.config就可以了
有些命令前面带点的，要注意看清楚
首次本地提取流程(随便说说，其实直接云编译的SSH生成.config也挺方便的，不过就是一定要编译一次固件比较费时而已)
安装ubuntu-18.04.4 (然后依次执行以下命令)
sudo apt-get update
sudo apt-get -y install build-essential asciidoc binutils bzip2 gawk gettext git libncurses5-dev libz-dev patch python3 python2.7 unzip zlib1g-dev lib32gcc1 libc6-dev-i386 subversion flex uglifyjs git-core gcc-multilib p7zip p7zip-full msmtp libssl-dev texinfo libglib2.0-dev xmlto qemu-utils upx libelf-dev autoconf automake libtool autopoint device-tree-compiler g++-multilib antlr3 gperf wget swig rsync
git clone https://github.com/coolsnowwolf/lede
cd lede
cd package 把要加的全部插件都用git clone下载到这里面比如增加clash出国插件 git clone https://github.com/frainzy1477/luci-app-clash.git
cd ..
./scripts/feeds update -a
./scripts/feeds install -a
make menuconfig
make defconfig
./scripts/diffconfig.sh > seed.config
cat seed.config
其实就是coolsnowwolf/lede大神源码的编译流程，就是不用编译而已，就提取.config



# 编译说明：
#
- 以下的说明教程都是在我另外的仓库的，查看说明时候就跳转到另外仓库了，浏览器回退就会回来，别拉取到我说明的仓库，注意了！
#
#
- 2020/8/31，增加可以单独提取.config配置文件，可以选择开跟关《[查看开关说明](https://github.com/danshui-git/shuoming/blob/master/yml%E4%B8%BB%E6%96%87%E4%BB%B6.md)》，方便个人需要，修复上次不小心弄的奶牛网盘网址错误问题，修复不打开上传固件到github空间就不能单独上传到网盘的问题
#
#
- 1、`注册及登录github账号`《[注册链接](https://github.com)》
#
- 2、`拉取我的仓库到你的仓库`《[拉取仓库教程](https://github.com/danshui-git/shuoming/blob/master/1%E6%8B%89%E5%8F%96%E4%BB%93%E5%BA%93.md)》
#
- 3、拉取仓库后，到根目录的【diy-lede.sh】修改登录IP，好等编译完成安装后顺利登录openwrt《[修改跟删除](https://github.com/danshui-git/shuoming/blob/master/%E5%88%A0%E9%99%A4%E5%92%8C%E4%BF%AE%E6%94%B9%E6%96%87%E4%BB%B6.md)》
#
- 4、`按☆Star启动编译`《[启动教程](https://github.com/danshui-git/shuoming/blob/master/2%E5%90%AF%E5%8A%A8%E8%AF%B4%E6%98%8E.md)》
#
- 5、`SSH远程连接服务器配置固件`《[SSH工具下载](https://github.com/danshui-git/shuoming/blob/master/Putty%E5%B7%A5%E5%85%B7%E4%B8%8B%E8%BD%BD.md)》《[SSH连接教程]
(https://github.com/danshui-git/shuoming/blob/master/3SSH%E8%BF%9E%E6%8E%A5%E8%AF%B4%E6%98%8E.md)》
#
- 6、`配置固件`《[youtube大神的固件配置视频教程](https://www.youtube.com/watch?v=jEE_J6-4E3Y)》《[恩山大神xtwz整理的插件中文对照](https://www.right.com.cn/forum/thread-3682029-1-1.html)》
#
- 7、`完成编译，下载固件`《[固件下载教程](https://github.com/danshui-git/shuoming/blob/master/4%E5%9B%BA%E4%BB%B6%E4%B8%8B%E8%BD%BD.md)》
#
- 8、`安装固件`，安装固件时出现“Please press Enter to activate this console”就表示安装好了，出现这个就不会跑码的，稍等1分钟就可以进入网页了
- 如果会跑码，就耐心等待跑码完成，应该不需要1分钟就能跑完的
#
- 9、当你成功编译一次后，看看这些东西，对你或者有点帮助的
《[根目录文件说明](https://github.com/danshui-git/shuoming/blob/master/%E6%A0%B9%E7%9B%AE%E5%BD%95%E6%96%87%E4%BB%B6%E8%AF%B4%E6%98%8E.md)》
《[.github/workflows里的主文件部分说明](https://github.com/danshui-git/shuoming/blob/master/yml%E4%B8%BB%E6%96%87%E4%BB%B6.md)》
《[定时触发编译说明](https://github.com/danshui-git/shuoming/blob/master/%E5%AE%9A%E6%97%B6%E7%BC%96%E8%AF%91%E8%AF%B4%E6%98%8E.md)》
《[本地提取.config](https://github.com/danshui-git/shuoming/blob/master/%E6%9C%AC%E5%9C%B0%E6%8F%90%E5%8F%96.config.md)》
《[其他说明](https://github.com/danshui-git/shuoming/blob/master/%E5%85%B6%E4%BB%96%E8%AF%B4%E6%98%8E.md)》
《[固件包减负](https://github.com/danshui-git/shuoming/blob/master/%E5%9B%BA%E4%BB%B6%E6%96%87%E4%BB%B6%E5%A4%B9%E6%95%B4%E7%90%86.md)》
《[banner的说明](https://github.com/danshui-git/shuoming/blob/master/banner%E8%AF%B4%E6%98%8E.md)》
#
- 10、建议准备梯子一把，虽然云编译不需要梯子，不过你使用SSH连接、下载固件、打开github网页也是需要梯子比较好的（没有也行，比较卡就是）
#
- 此编译脚本来自[P3TERX大神一键编译脚本](https://github.com/P3TERX/Actions-OpenWrt)，感谢P3TERX大神！！！

创建密匙 ssh-keygen -t rsa -b 4096 -C "2039206548@qq.com"

