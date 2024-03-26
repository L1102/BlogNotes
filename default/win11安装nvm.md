### 下载nvm

下载地址：https://github.com/coreybutler/nvm-windows/releases

#### 相关nvm命令

- **nvm arch**：显示node是运行在32位还是64位
- **nvm install [version] [arch]** ：安装node， version是特定版本也可以是最新稳定版本latest。可选参数arch指定安装32位还是64位版本，默认是系统位数。可以添加–insecure绕过远程服务器的SSL。
- **nvm list [available]** ：显示已安装的列表。可选参数available，显示可安装的所有版本。list可简化为ls。
- **nvm on** ：开启node.js版本管理。
- **nvm off** ：关闭node.js版本管理。
- **nvm proxy [url]** ：设置下载代理。不加可选参数url，显示当前代理。将url设置为none则移除代理。
- **nvm node_mirror [url]** ：设置node镜像。默认是https://nodejs.org/dist/。如果不写url，则使用默认url。设置后可至安装目录settings.txt文件查看，也可直接在该文件操作。
- **nvm npm_mirror [url]** ：设置npm镜像。https://github.com/npm/cli/archive/。如果不写url，则使用
- 认url。设置后可至安装目录settings.txt文件查看，也可直接在该文件操作。
- **nvm uninstall [version]** ：卸载指定版本node。
- **nvm use [version] [arch]** ：使用制定版本node。可指定32/64位。
- **nvm root [path]** ：设置存储不同版本node的目录。如果未设置，默认使用当前目录。
- **nvm version** ：显示nvm版本。version可简化为v。



![image-20240324172207776](../../pictures/img/image-20240324172207776.png)

### 安装node

> https://registry.npmmirror.com/binary.html?path=node/



下载完成后解压到nvm的安装目录中

![image-20240324171453968](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20240324171453968.png)

### 配置npm

- 查看全局安装地址和缓存地址

```bash
# 查看npm 全局安装地址
npm config get prefix

# 查看npm 缓存位置
npm config get cache
```

- 设置全局安装地址和缓存地址（需要提前创建好文件夹)

```bash
# 设置npm安装的地址
npm config set prefix "E:\path\node_global"

# npm缓存位置设置
npm config set cache "E:\path\node_cache"
```

- 添加环境变量

![image-20240324170444532](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20240324170444532.png)

- 配置npm镜像加速

```bash
# 查看当前镜像，默认为官方的 https://registry.npmjs.org/
npm config get registry

# 设置镜像
npm config set registry https://registry.npmmirror.com
```



### 安装yarn

- 使用管理员权限打开终端输入以下代码

```bash
npm install yarn -g
```

- 查看yarn的全局、缓存目录

以下三个命令分别为：bin是yarn存储命令的二进制文件，global存储全局node_modules ，cache[存储](https://link.csdn.net/?target=https%3A%2F%2Fauth.huaweicloud.com%2Fauthui%2Fsaml%2Flogin%3FxAccountType%3Dcsdndev_IDP%26isFirstLogin%3Dfalse%26service%3Dhttps%3A%2F%2Factivity.huaweicloud.com%2Ffree_test%2Findex.html%3Futm_source%3Dhwc-csdn%26utm_medium%3Dshare-op%26utm_campaign%3D%26utm_content%3D%26utm_term%3D%26utm_adplace%3DAdPlace070851)用下下载缓存，查看本机目前的目录：

```bash
# 查看bin目录命令：
yarn global bin
# 查看global目录命令：
yarn global dir
# 查看cache目录命令：
yarn cache dir
```

- 修改yarn的全局、缓存目录

```bash
yarn config set prefix "自定义bin目录路径"

yarn config set global-folder "自定义node_modules目录路径"

yarn config set cache-folder "自定义cache目录路径"
```

- 配置环境变量，同nvm

- 更换下载源

```bash
# 查看当前源：
yarn config get registry

# 更换源：
yarn config set registry https://registry.npmmirror.com
```









