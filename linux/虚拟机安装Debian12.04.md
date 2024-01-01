# win11虚拟机安装Debian12.4.0

## 1.下载Debian

- Debian下载地址：https://www.debian.org    -->  **debian-12.4.0-amd64-netinst.iso**

![image-20231212210157576](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231212210157576.png)

下载到的ISO文件一般都是几百M大小，因为这只是一个小型的安装映像，最终还是需要联网安装

![image-20231212210144363](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231212210144363.png)

> 附上旧版的Debian11.8下载地址：https://www.debian.org/releases/bullseye/debian-installer
>
> Debian CD/DVD档案地址：https://cdimage.debian.org/cdimage/archive

## 2. 新建虚拟机

- 选择稍后安装操作系统

![image-20231212202701612](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231212202701612.png)

- 选择客户机

​	**VMware17没有Debian12.x，选择11的就行**

![image-20231212203026368](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231212203026368.png)

- 选择处理器配置，具体是多少看自己的电脑是什么配置，下一步

![image-20231212203447676](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231212203447676.png)

- 选择虚拟机内存，同样看自己电脑的配置来选就行，下一步

![image-20231212203649404](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231212203649404.png)

- 选择网络类型，下一步

![image-20231212203759004](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231212203759004.png)

- I/O控制器类型和磁盘类型安装推荐的选择，下一步

- 创建新的虚拟磁盘，下一步

![image-20231212204400801](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231212204400801.png)

- 磁盘容量大小一般20G就够了，然后选择存储为单个文件

![image-20231212204435861](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231212204435861.png)

- 这里可以根据需求自己选择哪些硬件，最后点击完成

![image-20231212210512831](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231212210512831.png)

- 点击选择ISO映像文件的位置，然后开启此虚拟机

![image-20231212210627297](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231212210627297.png)



![image-20231212210757495](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231212210757495.png)

## 3. 安装Debian

- 选择第一个，会带有安装界面，按下回车

![image-20231212211306800](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231212211306800.png)

- 选择系统语言为英文，也可以选择中文的，方便理解

![image-20231212224017927](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231212224017927.png)

- 选择时区，这里只有香港的，那就选香港，也是东八区的

![image-20231212224436151](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231212224436151.png)

- 键盘映射选择为美式英语

![image-20231212224614833](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231212224614833.png)

- 填写主机名

![image-20231212225055933](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231212225055933.png)

- 设置域名，可以不用写，直接跳过

![image-20231212225332420](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231212225332420.png)

- 设置root用户的密码

![image-20231212225502661](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231212225502661.png)

- 创建一个新的账户，名字随意，也可以按系统要求来填

![image-20231212230319432](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231212230319432.png)

- 给新账户选择一个用户名

![image-20231212230632933](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231212230632933.png)

- 填写用户密码

![image-20231212230654622](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231212230654622.png)

- 磁盘分区方式，选择第二个

| 英文表述                                        | 解释                                                         |
| ----------------------------------------------- | ------------------------------------------------------------ |
| Guided-use entire disk                          | 带引导模式方式直接使用整块磁盘                               |
| Guided-use entire disk and set up LVM           | 带引导模式方式使用整块磁盘并使用LVM，LVM(Logical Volume Mananger)逻辑卷管理，可对磁盘进行弹性管理 |
| Guided-use entire disk and set up encrypted LVM | 带引导模式方式使用整块磁盘并配置加密的LVM                    |
| Manual                                          | 手动                                                         |

![image-20231212231147721](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231212231147721.png)

- 直接下一步

![image-20231212231401537](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231212231401537.png)

- 选择分区方案，这里选择第二个

![image-20231212232149593](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231212232149593.png)

- 选择 "是"

![image-20231212232626959](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231212232626959.png)

- 使用的全部的磁盘大小

![image-20231212232912847](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231212232912847.png)

- 选择 "是"

![image-20231212233332751](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231212233332751.png)

- 等待安装基本系统

![image-20231212233426404](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231212233426404.png)

- 选择 "否"

![image-20231212234307462](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231212234307462.png)

- 选择仓库镜像站点所在地为中国

![image-20231212234413383](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231212234413383.png)

- 选择国内的镜像

![image-20231212234552213](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231212234552213.png)

- 选择代理，不用填，直接下一步

![image-20231212234709200](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231212234709200.png)

- 等待配置，如果前面配置了镜像就会比较快

![image-20231212234751525](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231212234751525.png)

> 如果觉得很慢可以点击右下角的取消，然后重新选择镜像即可

- 选择 "否"

![image-20231212235043368](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231212235043368.png)

- 选择下面三个，如果需要图形化界面的话可以再把最上面的两个选上

![image-20231212235518582](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231212235518582.png)

- 选择 "是"

![image-20231212235708831](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231212235708831.png)

- 选择第二个，等待安装完成，然后重启即可

![image-20231212235809423](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231212235809423.png)

- 选择第一个，回车

![image-20231213000003735](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231213000003735.png)

- 输入账户密码登录

![image-20231213000133455](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231213000133455.png)

## 4. 基本设置

> Debian使用的包管理工具是 **apt**，和ubuntu的相同

### 设置用户为管理员

```bash
# 1. 通过 usermod 命令
sudo usermod -aG sudo <username>
# 验证新用户是否已添加到 sudo 组
groups user_name

# 2. 通过 gpasswd 命令
sudo gpasswd -a <user_name> sudo
```

### 修改系统语言

```bash
sudo dpkg-reconfigure locales
```







