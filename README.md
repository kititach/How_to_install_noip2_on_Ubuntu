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
### ติดตั้ง noip โดยใช้ make install หลังจากรันให้ใส่ account username and password ที่ได้สมัครกับ noip ลิ้ง https://www.noip.com/
```
sudo make install
```
### 
![5-20-2022 11-58-26 AM](https://user-images.githubusercontent.com/48780839/169454285-e900be14-ad84-45c5-98db-c35b22e70d22.png)

