# Windows Terminal美化教程

## 安装 Windows Terminal

> **win10需要自己手动安装，win11已经默认安装好了，如果没有再自己安装**

- **从微软商店下载（推荐）**

![image-20231209145223108](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231209145223108.png)

- 手动安装

> github地址：https://github.com/microsoft/terminal/releases

## 创建 Windows PowerShell 配置文件

创建一个 PowerShell 配置文件来自定义环境并将特定于会话的元素添加到启动的每个 PowerShell 会话中。

PowerShell 配置文件是在 PowerShell 启动时运行的脚本，可以将配置文件用作登录脚本来自定义环境，可以添加命令、别名、函数、变量、管理单元、模块和 PowerShell 驱动器，
还可以将其他特定于会话的元素添加到您的配置文件中，以便在每个会话中都可以使用它们，而无需导入或重新创建。

- **一些常用的变量：**

| 变量名                          | 说明                              |
| :------------------------------ | --------------------------------- |
| $HOME                           | 用户的主目录                      |
| $PSHOME                         | PowerShell 安装目录               |
| $PROFILE                        | 当前用户、当前主机 配置文件的路径 |
| $PROFILE.CurrentUserCurrentHost | 当前用户、当前主机 配置文件的路径 |
| $PROFILE.CurrentUserAllHosts    | 当前用户，所有主机 配置文件的路径 |
| $PROFILE.AllUsersCurrentHost    | 所有用户，当前主机 配置文件的路径 |
| $PROFILE.AllUsersAllHosts       | 所有用户、所有主机 配置文件的路径 |

![image-20231209160710044](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231209160710044.png)

> **`PowerShell 的配置文件是不会自己生成的，需要手动创建！`**

```bash
# 查看当前是否存在 PowerShell 配置文件
# False ：不存在配置文件
# True ：存在配置文件
Test-Path $PROFILE
```

- **创建配置文件**

````bash
# 创建一个 PowerShell 配置文件
New-Item -Path $PROFILE -Type File -Force
````

## 安装 oh-my-posh

> 官网：https://ohmyposh.dev
>
> github：https://github.com/JanDeDobbeleer/oh-my-posh

### **使用微软商店进行安装**

- **默认会安装在`C`盘，一般不推荐把软件安装在系统盘，如果`C`盘容量足够大请随意**👍

![image-20231209151018838](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231209151018838.png)

### 使用 winget 安装（推荐）

**1. 首先查看 Windows PowerShell 的执行策略**

```bash
# 获取 Windows PowerShell 当前的执行策略
get-ExecutionPolicy
```

**执行策略状态说明**：

- **Restricted**：表示状态是禁止的，不载入配置文件也不执行脚本，是执行策略的默认值。
- **RemoteSigned**：所有从互联网上下载的脚本必须通过信任的出版商签名(trusted publisher)。
- **AllSigned**：所有的配置文件和脚本必须通过信任的出版商签名(trusted publisher)，这里所指的脚本页包括在本地计算机上创建的脚本。
- **Unrestricted**：载入所有的配置文件和脚本，如果运行了一个从互联网上下载且没有数字签名的脚本，在执行前都会被提示是否执行。

```bash
# 修改 Windows PowerShell 中执行策略的用户首选项(preference)
set-ExecutionPolicy RemoteSigned
```

**2. 执行安装命令**

```bash
// oh-my-posh 安装命令
winget install JanDeDobbeleer.OhMyPosh -s winget --location D:\你的安装路径

// oh-my-posh 更新命令
winget upgrade JanDeDobbeleer.OhMyPosh -s winget --location D:\你的安装路径
```

> **--location D:\你的安装路径：表示安装到`D`盘下的某个目录下，例如：**
>
> **--location D:\software\oh-my-posh**



![image-20231209164230161](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231209164230161.png)

## 安装 Nerd Font 字体

> 下载地址：https://www.nerdfonts.com/font-downloads
>
> JetBrainsMono Nerd Font 字体：https://github.com/ryanoasis/nerd-fonts/releases/download/v3.1.1/JetBrainsMono.zip

- **解压后，全选安装**

![image-20231209165227384](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231209165227384.png)

- **终端配置 Nerd Font 字体**

![image-20231209170247768](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231209170247768.png)

## 配置oh-my-posh主题

```bash
# 打开 Windows Terminal 查看本地已安装的 op-my-posh 主题
get-Poshthemes
```

![image-20231209165919064](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231209165919064.png)

- **用户记事本或其他编辑器打开之前创建的配置文件**

```bash
# 配置 oh-my-posh 主题，方式一：
oh-my-posh init pwsh --config 'D:/你的op-my-posh安装目录/themes/sim-web.omp.json' | Invoke-Expression

# 配置 oh-my-posh 主题，方式二（使用远程地址）：
oh-my-posh init pwsh --config 'https://raw.githubusercontent.com/JanDeDobbeleer/oh-my-posh/main/themes/sim-web.omp.json' | Invoke-Expression

# 配置 oh-my-posh 主题，方式三，使用安装 oh-my-posh 时自动配置好的系统路径（推荐使用这种方式）：
oh-my-posh init pwsh --config "$env:POSH_THEMES_PATH/sim-web.omp.json" | Invoke-Expression
```

![image-20231209171622730](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231209171622730.png)

## 安装并配置 PowerShell

![image-20231209154322403](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231209154322403.png)

> **配置步骤和 Windows PowerShell 相同**

## 配置个性化 cmd

### 下载 clink

> github地址：https://github.com/chrisant996/clink/releases

- 安装后在 **clink** 安装目录下新建一个 **Comletions** 文件夹，用于存放 **lua** 脚本配置

![image-20231209172350340](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231209172350340.png)

```bash
# 查看 clink 信息
clink info
# 设置 lua 脚本位置
clink set clink.path <你的 Comletions 目录的路径>
```

- **编写 lua 脚本**

在**Comletions** 文件夹下创建一个文件名后缀为 **lua** 的文件

![image-20231209173245386](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231209173245386.png)

```bash
# 打开文件写入以下内容，保存文件后再次打开 cmd 即可生效
load(io.popen('oh-my-posh init cmd --config D:/你的op-my-posh安装目录/themes/sim-web.omp.json'):read("*a"))()
```

## 配置插件

- **安装文件图标库**

```bash
# 在 PowerShell 中执行
Install-Module -Name Terminal-Icons -Repository PSGallery
# 把下面的配置写入之前创建的配置文件
Import-Module -Name Terminal-Icons
```

![image-20231209193200685](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231209193200685.png)

![image-20231210123724517](https://cdn.jsdelivr.net/gh/L1102/pictures/img/image-20231210123724517.png)







