# RPi5_Bookworm_WiFi_AP
Raspberry Pi 5をWi-Fi APとして動かす

# OS
Raspberry Pi OS Bookworm  
  
kernel情報  
```
uname -a
```
```
Linux Pi5BAP 6.1.0-rpi8-rpi-2712 #1 SMP PREEMPT Debian 1:6.1.73-1+rpt1 (2024-01-25) aarch64 GNU/Linux
airpocket@Pi5BAP:~ $ 
```

# setup

OSやアプリ類のアップデートを行う
```
sudo apt update && sudo apt -y upgrade
```
RealVNCを使用するためwindowシステムをwaylandからX11に変更する。  
X11上でVNCを使用する場合はtigerVNCを使用する（めんどくさい）
```
sudo raspi-config
```
6 Advanced Options -> A6 Wayland -> W1 X11  
X11に変更したらrebootする。

rebootしたらVNCを有効化する。
```
suod raspi-config
```
3 Interface Options -> I2 VNC  
設定出来たらreboot。  

メニューのpreferenceとかsettingから日本語化、local設定など行う。

# RTL8812au WiFiドングルのドライバインストール
参考:https://github.com/morrownr/8812au-20210629
```
sudo apt update && sudo apt upgrade
sudo apt install -y raspberrypi-kernel-headers build-essential bc dkms git
mkdir -p ~/src
cd ~/src
git clone https://github.com/morrownr/8812au-20210629.git
cd ~/src/8812au-20210629
sudo ./install-driver.sh
```

# WiFiの設定
ネットワークアイコン -> Advanced Options -> Create Wi-Fi Hotspot
