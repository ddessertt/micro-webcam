# ⚡️Project-Microprocessor Raspberry pi-61070051⚡️
## 📸 Pi Webcam

โปรเจคนี้ได้นำ Raspberry pi กับ ตัวกล้อง มาประยุกต์ใช้แทนกล้องเว็บแคม สำหรับผู้ที่มีความจำเป็นที่จะต้องใช้กล้องเว็บแคมแต่ไม่มีกล้องเว็บแคมในการใช้
หากมี Raspberry pi กับ ตัวกล้อง ก็สามารถนำมาใช้ทดแทนได้ โปรเจคนี้จึงได้ออกแบบมาเพื่อเป็นการแก้ปัญหาในการไม่มีกล้องเว็บแคมได้

## 🔧 อุปกรณ์ Hardware
- Raspberry pi 4 Mogel B 
<img src="https://www.robot-advance.com/EN/ori-raspberry-pi-4-model-b-4go-2640.jpg" height="250" width="400"/>

- Raspberry NoIR Camera 
<img src="https://fp.lnwfile.com/5kz7ix.jpg" height="250" width="400"/>

## 🔧 โปรแกรม Software
- https://ip-webcam.appspot.com/ 
  เป็นโปรแกรมสำหรับนำ IP ที่ได้หลังจาก run mjpgstreamer เพื่อเป็นตัวแทนเว็บแคมสำหรับคอมพิวเตอร์
 
## 🔨 Configuration
1. `sudo apt-get install cmake libjpeg8-dev -y`<br>
ติดตั้ง library ที่จำเป็นในการใช้งาน
2. `sudo apt-get install gcc g++ -y`<br>
ติดตั้ง gcc และ g++ ที่เป็น plugin สำหรับ opencv
3. `git clone https://github.com/ddessertt/micro-webcam`<br>
GitHub
ทำการ clone mjpg streamer ตัว command ที่มี plugin ในการใช้งานร่วมกับตัวกล้อง
4. `cd micro-webcam/mjpg-streamer-experimental`<br>
ทำการเข้าโฟลเดอร์ mjpg-streamer-experimental
5. `make && sudo make install`<br>
ทำการติดตั้งตัว mjpg streamer
6. `sudo nano startcam.sh`<br>
ทำการแก้ไขไฟล์ startcam.sh<br>
ดังนี้<br>
`#!/bin/bash
mjpg_streamer -i "input_raspicam.so -x 1280 -y 720 -fps 30" -o output_http.so`
7. `sudo chmod a+x startcam.sh`<br>
ทำการสร้าง startcam.sh ให้สามารถทำงานได้
8. `startcam.sh`<br>
เพื่อเรียกใช้งาน
