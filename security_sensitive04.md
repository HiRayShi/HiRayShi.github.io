<img src="30.PNG" >

# Setting loose POSIX file permissions is security-sensitive

* ใน Unix คลาส "others" หมายถึงผู้ใช้ทั้งหมดยกเว้นเจ้าของไฟล์และสมาชิกของกลุ่มที่กำหนดให้กับไฟล์นี้

* การให้สิทธิ์แก่กลุ่มนี้อาจนำไปสู่การเข้าถึงไฟล์โดยไม่ได้ตั้งใจ 

## Ask Yourself Whether

* Application ได้รับการออกแบบให้ทำงานบนสภาพแวดล้อมที่มีผู้ใช้หลายคน
files และ directories ที่เกี่ยวข้องอาจมีข้อมูลที่เป็นความลับ

There is a risk if you answered yes to any of those questions.

## Recommended Secure Coding Practices

* ควรกำหนดสิทธิ์ที่ จำกัด มากที่สุดให้กับ files และ directories

## Sensitive Code Example

* When creating a file or directory with permissions to "other group":
<img src="31.PNG" >
* When explicitly adding permissions to "other group" with chmod, fchmod or filesystem::permissions functions:
<img src="32.PNG" >
* When defining the umask without read, write and execute permissions for "other group":
<img src="33.PNG" >
## Compliant Solution

* When creating a file or directory, do not set permissions to "other group":
<img src="34.PNG" >
* When using chmod, fchmod or filesystem::permissions functions, do not add permissions to "other group":
<img src="35.PNG" >
When defining the umask, set read, write and execute permissions to other group:
<img src="36.PNG" >

Author : Jaray Paensong

Ref : https://rules.sonarsource.com/c/type/Security%20Hotspot/RSPEC-5816
