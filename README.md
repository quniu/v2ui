
# v2ray-ui
支持多协议多用户的 v2ray 面板

## 功能介绍
 - 系统状态监控
 - 支持多用户多协议，浏览器可视化操作，无需敲命令
 - 支持的协议：vmess、shadowsocks、dokodemo-door、socks、http
 - vmess 支持的传输配置：tcp（http伪装、tls）、kcp（伪装）、ws（tls）、http（tls）、quic（tls）
 - 支持账号流量统计
 - 支持自定义 v2ray 配置模板
 - 支持 https 访问面板（需自备域名 + ssl 证书）
 - 更多高级配置项，详见面板
 
## 安装&升级

安装wget
```
yum -y install wget
# or
apt-get -y install wget
```
执行脚本
```
bash <(curl -L -s https://github.com/quniu/v2ui/raw/master/v2-ui.sh)
# 或者
wget -N --no-check-certificate https://raw.githubusercontent.com/quniu/v2ui/master/install.sh
chmod +x install.sh
./install.sh
```


## 面板其它操作
```
v2-ui                  # 显示管理菜单 (功能更多)
v2-ui start            # 启动 v2-ui 面板
v2-ui stop             # 停止 v2-ui 面板
v2-ui restart          # 重启 v2-ui 面板
v2-ui status           # 查看 v2-ui 状态
v2-ui enable           # 设置 v2-ui 开机自启
v2-ui disable          # 取消 v2-ui 开机自启
v2-ui log              # 查看 v2-ui 日志
v2-ui update           # 更新 v2-ui 面板
v2-ui install          # 安装 v2-ui 面板
v2-ui uninstall        # 卸载 v2-ui 面板
```

## 数据备份与迁移
面板所有数据包括账号信息等都存在 /etc/v2ui/v2-ui.db 中，只要备份此文件即可。

在新服务器安装了面板之后，先关闭面板，再将备份的文件覆盖新安装的，最后启动面板即可。

注意，若配置了面板 ssl 证书，确保新服务器的同样的路径下有相同的证书文件，否则将无法在新服务器启动面板。

若配置了 v2ray 的 tls，并且使用了证书文件配置，也要确保新服务器有证书文件，否则将无法启动 v2ray，若使用证书内容配置，则无需关心。

## 卸载面板
执行以下命令即可完全卸载面板，如果还需要卸载 v2ray，请自行找相关教程。
```
systemctl stop v2-ui
systemctl disable v2-ui
rm /usr/local/v2ui-linux/ -rf
rm /etc/v2ui/ -rf
rm /etc/systemd/system/v2-ui.service -f
systemctl daemon-reload
```

## 忘记用户名和密码
使用以下命令重置用户名和密码，默认都为 admin
```
/usr/local/v2ui-linux/v2-ui resetuser
```
## 面板设置修改错误导致面板无法启动
使用以下命令重置所有面板设置，默认面板端口修改为 65432，其它的也会重置为默认值

```
/usr/local/v2ui-linux/v2-ui resetconfig
```

注意，这个命令不会重置用户名和密码。

## 详细教程
https://blog.sprov.xyz/v2-ui/



