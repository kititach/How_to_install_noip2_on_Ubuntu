# How-to-install-the-noip2-on-Ubuntu

### update os Ubuntu
```
sudo apt update
```
### ติดตั้ง โปรแกรม make และ gcc
```
sudo apt install make gcc -y
```
### เข้าไปที่โฟล์เดอร์ /usr/local/src/
```
cd /usr/local/src/
```
### ดาวโหลดไฟล์ noip duc และแตกไฟล์
```
sudo wget http://www.noip.com/client/linux/noip-duc-linux.tar.gz
sudo tar xf noip-duc-linux.tar.gz
```
### เปิดโฟล์เดอร์ noip หลังจากแตกไฟล์
```
cd noip-2.1.9-1/
```
### ติดตั้ง noip โดยใช้ make install 
```
sudo make install
``` 
1. username and password ที่ได้สมัครกับ noip ลิ้ง https://www.noip.com/
2. ระยะเวลาที่ต้องการให้อัปเดต DDNS
3. ต้องการให้ RUN โปรแกรมอื่นไหม

![5-20-2022 11-58-26 AM](https://user-images.githubusercontent.com/48780839/169454285-e900be14-ad84-45c5-98db-c35b22e70d22.png)
### ย้ายไฟล์ configuration
```
mv /tmp/no-ip2.conf /usr/local/etc/no-ip2.conf
```
### เปิดการใช้งาน Service/init.d ให้กับ noip
```
chmod 600 /usr/local/etc/no-ip2.conf
chown root:root /usr/local/etc/no-ip2.conf
```
### copy ไฟล์ตามด้านล่างนี้
```
#######################################################
#! /bin/sh
# . /etc/rc.d/init.d/functions # uncomment/modify for your killproc
case "$1" in
start)
echo "Starting noip2."
/usr/local/bin/noip2
;;
stop)
echo -n "Shutting down noip2."
killproc -TERM /usr/local/bin/noip2
;;
*)
echo "Usage: $0 {start|stop}"
exit 1
esac
exit 0
#######################################################
```
### แก้ไขให้ระบบ ปรับปรุงและอัปเดต
```
sudo chmod +x /etc/init.d/noip2.sh
sudo update-rc.d noip2.sh defaults
```
### แก้ไขให้ระบบ ทำงาน Auto reboot
```
vi /etc/systemd/system/noip2.service
```
### copy ไฟล์ตามด้านล่างนี้
```
[Unit]
Description=noip2 service

[Service]
Type=forking
ExecStart=/usr/local/bin/noip2
Restart=always

[Install]
WantedBy=default.target
```
### Reload ระบบ daemon
```
sudo systemctl daemon-reload
```
### คำสั่ง status ต่างๆ
```
sudo systemctl start noip2    #เริ่มการทำงาน
sudo systemctl status noip2   #ดูสถานะ
sudo systemctl stop noip2     #หยุดการทำงาน
```
### คำสั่ง เปิด-ปิด การใช้งานหลัง reboot
```
sudo systemctl enable noip2   #เปิดใช้งาน
sudo systemctl disable noip2  #ปิดใช้งาน
```
