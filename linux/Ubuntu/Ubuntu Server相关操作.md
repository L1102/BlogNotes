# Ubuntu Server相关操作

- **允许`root`用户远程登陆**

```bash
sudo vim /etc/ssh/sshd_config
# 修改 #PermitRootLogin Prohibit-password 
PermitRootLogin yes
# 重启 ssh 服务
sudo service sshd restart
```

- **Ubuntu开放指定端口**

```bash
# 安装 ufw
sudo apt install ufw
```

> ```bash
> ufw 命令行示例：
> sudo ufw enable/disable：打开/关闭防火墙
> sudo ufw reload：重启防火墙
> sudo ufw status：查看已经定义的ufw规则
> sudo ufw default allow/deny：外来访问默认允许/拒绝
> sudo ufw allow/deny 20：允许/拒绝访问20端口，20后可跟/tcp或/udp，表示tcp或udp封包。
> sudo ufw allow proto tcp from 192.168.0.0/24 to any port 22：允许自192.168.0.0/24的tcp封包访问本机的22端口。
> sudo ufw delete allow/deny 20：删除以前定义的"允许/拒绝访问20端口"的规则
> ```

```bash
sudo ufw allow 22 # 开放22端口，允许外部访问22端口(tcp/udp)
```

- **更新软件仓库包索引并升级**

```bash
sudo apt update # 更新索引
sudo apt upgrade # 升级
```

- **修改系统时区**

> 系统时区通过链接文件`/etc/localtime`配置，该链接指向`/usr/share/zoneinfo`目录下的一个二进制时区标识文件。
>
> ```bash
> ls -l /etc/localtime # 查看这个链接文件指向的实际路径
> ```
>
> 默认输出路径：`/etc/localtime -> /usr/share/zoneinfo/Etc/UTC`

```bash
# 查看当前系统时区
timedatectl
# 列出所有可用的时区
timedatectl list-timezones
# 修改为上海时间
sudo timedatectl set-timezone Asia/Shanghai
# 验证
timedatectl
```

- 解决 **bash: sudo: command not found** 问题

```bash
# 切换到root账户，安装sudo
apt-get install sudo
```















