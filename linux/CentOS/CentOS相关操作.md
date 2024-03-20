# CentOS相关操作

- **给普通用户授予该目录的上传文件权限**

```bash
sudo chown -R 用户名:用户名 /opt/
```

- **移动文件或目录**		

```bash
sudo mv <源文件路径> <目标文件路径>
# 例如：
sudo mv /opt/docker-compose /usr/local/bin/
# 移动目录及其内容
mv -r /path/to/source /path/to/destination
```

- **防火墙配置**

```bash
# 部分操作
systemctl status firewalld # 查看防火墙状态
sudo systemctl stop firewalld # 临时关闭防火墙
sudo systemctl start firewalld # 开启防火墙
sudo systemctl restart firewalld # 重启防火墙
sudo systemctl disable firewalld # 关闭防火墙开机启动
sudo systemctl enable firewalld # 开启防火墙开机启动
# 开放端口
sudo firewall-cmd --zone=public --add-port=3306/tcp --permanent
# 关闭端口
sudo firewall-cmd --zone=public --remove-port=3306/tcp --permanent
# 刷新防火墙配置
sudo firewall-cmd --reload
# 查看已开放的端口
sudo firewall-cmd --list-ports
```

- **解决 network 和 NetworkManager 冲突导致无法联网的问题**

```bash
# 查看NetworkManager状态
systemctl status NetworkManager
# 关闭NetworkManager
sudo systemctl stop NetworkManager
# 设置开机不启动
sudo systemctl disable NetworkManager
# 重启网络
sudo systemctl restart network
# 查看网络状态
systemctl status network
```

- 解决 **sudo: command not found** 问题

```bash
yum -y install sudo
```













