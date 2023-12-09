# CentOS环境配置

##  安装 docker 和 docker-compose

> 官方文档：https://docs.docker.com/engine/install/centos/

### 1. 安装 Docker

- 打开终端安装 **yum-utils**


```bash
sudo yum install -y yum-utils
```

![](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-202311211511630.png)

- 修改 **yum** 的 **docker** 下载源

 ```bash
sudo yum-config-manager --add-repo http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
 ```

![](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231103003038221.png)

- 安装 **docker**

```bash
sudo yum install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

> 加上 **`-y`** 是因为在安装过程中会有安装确认，加上后就不用手动确认了

- 检查是否安装成功

 ```bash
docker version
 ```

![](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231103003901115.png)

- 运行 **docker**

 ```bash
sudo systemctl start docker
 ```

- 查看 **docker** 运行状态

 ```bash
sudo systemctl status docker
 ```

![](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231103004133571.png)

> **`disable`** 表示 **`docker`** 服务不会开机自启动

- 设置开机自启动

 ```bash
sudo systemctl enable docker
 ```

- 修改 **docker** 官方下载源为国内下载源

> 腾讯云：https://cloud.tencent.com/document/product/1207/45596

### 2. 安装 Docker compose

#### 有两种安装方式：

###### 1. 按照官方文档进行安装

- 直接从 **GitHub** 上下载到服务器，可能有点慢，几个小时也有可能

> 官方文档：https://docs.docker.com/compose/install/standalone/

```bash
sudo curl -SL https://github.com/docker/compose/releases/download/v2.23.3/docker-compose-linux-x86_64 -o /usr/local/bin/docker-compose
```

- 查看是否下载成功

```bash
ll /usr/local/bin
```

- 如果 **docker-compose** 显示的颜色是白色，表示这是不可执行的文件，需要将其变成可执行文件

```bash
sudo chmod +x /usr/local/bin/docker-compose
```

- 检查 **docker-compose** 是否可执行

```bash
docker-compose version
```

![](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231103012208891.png)

###### 2. 先从 GitHub 上下载到本地，再上传到服务器

> 下载地址：https://github.com/docker/compose/releases

- **上传文件到 `/opt` **

```bash
cd /opt
# 移动文件
sudo mv docker-compose /usr/local/bin/
# 变成可执行文件
sudo chmod +x /usr/local/bin/docker-compose
# 验证
docker-compose version
```

## 安装jdk

### 方式一：使用 yum 安装

```bash
yum install java-1.8.0-openjdk* -y
```

> 安装的目录为： **`/usr/lib/jvm/java-1.8.0-openjdk`**



**验证是否安装成功**

```bash
java -version
```

### 方式二：下载源码手动安装

**1. 删除系统自带的 jdk**

```bash
# 查看系统自带jdk
rpm -qa | grep java
# 卸载
yum -y remove <java-1.8.0-openjdk>
```

**2. 使用工具将jdk源码上传到系统中，（放在`/opt`目录下）**

**3. 在 `/usr/local` 目录下创建一个 `jdk` 文件夹**

```bash
sudo mkdir /usr/local/jdk
```

**4. 进入`/opt`目录并解压**

```bash
cd /opt
# 解压到/usr/local/jdk
sudo tar -zxvf jdk-8u361-linux-x64.tar.gz -C /usr/local/jdk
```

**5. 修改系统环境变量**

```bash
sudo vim /etc/profile
或
sudo vi /etc/profile
```

- **按`i`键进行编辑，添加以下配置**

```bash
export JAVA_HOME=/usr/local/jdk/jdk1.8.0_361
export JRE_HOME=$JAVA_HOME/jre
export CLASSPATH=.:$CLASSPATH:$JAVA_HOME/lib:$JRE_HOME/lib
export PATH=$PATH:$JAVA_HOME/bin:$JRE_HOME/bin
```

- **按`Esc`键，输入`:wq`保存退出**

```bash
# 刷新 profile 文件
source /etc/profile
```

**6. 验证是否安装成功**

```bash
java -version
```

## CentOS 8 更换 yum 源为阿里云

```bash
# 先将已有的yum源仓库配置文件备份
sudo mkdir backup && mv CentOS-Linux-*.repo backup
# curl 命令下载阿里的yum源仓库配置文件
sudo curl -o /etc/yum.repos.d/CentOS-Linux-Base-ali.repo https://mirrors.aliyun.com/repo/Centos-vault-8.5.2111.repo
```

## 安装 **vim**

```bash
# 查看本机是否有vim包
rpm -qa|grep vim
# 安装
yum -y install vim*
```

