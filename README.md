# Oracle-VPS-Scripts
Oracle VPS 常用脚本。

Root权限：
sudo -i

Root密码修改：
bash <(curl -Ls https://github.com/baoqihui/script/raw/main/root.sh)
或
sudo -i
wget -N https://cdn.jsdelivr.net/gh/Misaka-blog/rootLogin@master/root.sh && chmod -R 777 root.sh && bash root.sh

更新系统，开放端口
bash <(curl -Ls https://github.com/baoqihui/script/raw/main/init.sh)

1.安装相关依赖
centos系统下
yum update -y                                                                                                
apt-get update -y && apt-get install curl -y

ubuntu系统下
apt update -y
apt-get update -y && apt-get install curl -y

2: Ubuntu系统依赖升级
apt-get update
apt-get upgrade
apt-get dist-upgrade

3：删除、关闭、打开各自系统的无用附件、防火墙、端口及规则
注意Centos系统下：
删除多余附件
systemctl stop oracle-cloud-agent
systemctl disable oracle-cloud-agent
systemctl stop oracle-cloud-agent-updater
systemctl disable oracle-cloud-agent-updater

停止firewall
systemctl stop firewalld.service
禁止firewall开机启动
systemctl stop firewalld.service
systemctl disable firewalld.service

注意Centos和Ubuntu系统下：
开放所有端口
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT
iptables -F

Ubuntu镜像默认设置了Iptable规则，关闭它
apt-get purge netfilter-persistent
reboot
或者强制删除
rm -rf /etc/iptables && reboot

关闭防火墙:
systemctl stop firewalld.service && systemctl disable firewalld.service

甲骨文云开启IPV6
参考https://51.ruyo.net/17105.html

V2ray 搭建：
sudo apt install -y curl

wget -N --no-check-certificate -q -O install.sh "https://raw.githubusercontent.com/wulabing/V2Ray_ws-tls_bash_onekey/master/install.sh" && chmod +x install.sh && bash install.sh

八合一脚本
wget -P /root -N --no-check-certificate "https://raw.githubusercontent.com/mack-a/v2ray-agent/master/install.sh" && chmod 700 /root/install.sh && /root/install.sh


Xray 搭建
wget -N https://raw.githubusercontents.com/Misaka-blog/Xray-script/master/xray.sh && bash xray.sh


Misaka工具箱
wget -N https://cdn.jsdelivr.net/gh/Misaka-blog/MisakaLinuxToolbox@master/MisakaToolbox.sh && chmod -R 777 MisakaToolbox.sh && bash MisakaToolbox.sh

x-ui搭建
bash <(curl -Ls https://raw.githubusercontents.com/vaxilu/x-ui/master/install.sh)

BBR加速（系统自带BBR）：
参考 https://www.qiuvps.com/699.html

或#首先先更新下系统，然后安装依赖组建：
apt-get update
apt-get update && apt-get install -y wget curl

#之后开启原生BBR：
echo "net.core.default_qdisc=fq" >> /etc/sysctl.conf
echo "net.ipv4.tcp_congestion_control=bbr" >> /etc/sysctl.conf
sysctl -p

#检测是否正常开启BBR：
sysctl net.ipv4.tcp_available_congestion_control
lsmod | grep bbr


tcp优化加速脚本
wget http://sh.nekoneko.cloud/tools.sh -O tools.sh && bash tools.sh

VPS内存日志自动清理
bash <(curl -Lso- https://vmshell.com/adpic/vmshellvps.sh)

MTPorxy
参考 https://github.com/seriyps/mtproto_proxy
或 https://github.com/HirbodBehnam/MTProtoProxyInstaller

netfilx检测：
参考 https://github.com/CoiaPrant/MediaUnlock_Test
或  https://github.com/lmc999/RegionRestrictionCheck

Warp:
参考 https://github.com/kkkyg/CFwarp
或 https://github.com/fscarmen/warp

SuperSpeed 全面测速版
bash <(curl -Lso- https://git.io/Jlkmw)

SuperBench测试脚本
wget -qO- --no-check-certificate https://raw.githubusercontent.com/oooldking/script/master/superbench.sh | bash
#或者
curl -Lso- -no-check-certificate https://raw.githubusercontent.com/oooldking/script/master/superb


检测VPS回程国内三网路由：
curl https://raw.githubusercontent.com/zhucaidan/mtr_trace/main/mtr_trace.sh|bash

支持的线路为：电信CN2 GT，电信CN2 GIA，联通169，电信163，联通9929，联通4837，移动CMI

Speedtest测速
apt install speedtest-cli
speedtest
