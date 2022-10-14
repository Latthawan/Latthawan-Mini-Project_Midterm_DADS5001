# Latthawan-Mini-Project_Midterm_DADS5001
การวิเคราะห์ข้อมูลปริมาณน้ำฝนกับพื้นที่เสียงน้ำท่วมในประเทศไทย ปี 2022

บทความวิเคราะห์นี้ จัดทำขึ้นเพื่อหาคำตอบว่าในพื้นที่ที่มีฝนตกมากๆ จะทำให้เกินน้ำท่วมหรือไม่?

แหล่งข้อมูลที่ใช้ในการทำ สามารถดาวน์โหลดได้จากทาง link หรือไฟล์ excel ด้านบนค่ะ
https://data.go.th/dataset/spatial-rain 
https://data.go.th/dataset/flood-area 
https://data.go.th/dataset/proviceandregionthailand 
เริ่มเเรก โดยการติดตั้ง Libraly เพื่อการพร้อมใช้งาน

![image](https://user-images.githubusercontent.com/105144684/195758208-130d490c-3534-49a0-a8d9-9b746f495d28.png)

โหลดข้อมูลเข้าตัวแปร DataFrame ของ Pandas โดยจะจัดเก็บข้อมูลในตัวแปรเป็นตาราง มีแถวและมีคอลัมน์ โดยจะโหลดข้อมูลทั้งหมด 3 ไฟล์ 
1. area-flood  คือไฟล์ข้อมูลปริมาณน้ำฝนเชิงพื่นที่
2. spatial-rain คือไฟล์ข้อมูลพื่นที่เสี่ยงน้ำท่วม
3. Province-Master คือไฟล์ข้อมูลจังหวัดและภูมิภาคในประเทศไทย

![image](https://user-images.githubusercontent.com/105144684/195758093-9499bcf1-1a75-4383-a1f5-49c1822f7588.png)

ตรวจสอบข้อมูลที่เข้า โดยใช้ groupby เพื่อตรวจสอบชื่อจังหวัดว่าเขียนรูปแบบเดียวกันหรือไม่ เช่น จ.กำแพงเพชร/จังหวัดกำแพงเพชร/กำแพงเพชร และ df.inf() เพื่อตรวจสอบค่า na

![image](https://user-images.githubusercontent.com/105144684/195757808-0a5c79c2-1aa0-46c5-8bca-d8d855c3dd4b.png)
![image](https://user-images.githubusercontent.com/105144684/195757840-b41afdea-b54a-4561-9307-a9ee14b13419.png)
![image](https://user-images.githubusercontent.com/105144684/195757869-91a4ebbf-cb81-4fde-b551-b909e3123a69.png)

จากการตรวจสอบพบว่าในไฟล์ area-flood มีชื่อจังหวัดที่เขียนรูปแบบไม่เหมือนกันอยู่ ดังนั้นจึงใช้รหัสจังหวัดเป็น key ในการ join ข้อมูลระหว่างไฟล์เพื่อนำชื่อจังหวัดจากไฟล์ Province-Master ไปใช้ รวมไปถึงนำข้อมูลภูมิภาคมาใช้ด้วย

![image](https://user-images.githubusercontent.com/105144684/195760050-dcdba04c-059c-4872-9fc6-dab7f2c81b94.png)

เนื่องจากต้องการนำข้อมูลจากไฟล์ spatial-rain และ area-flood มารวมกัน เเต่ทั้ง 2 นี้มีรายเอียดลงถึงรายเดือน จึงต้องทำการสร้าง Key โดยการนำรหัสจังหวัด-เดือน เพื่อใช้ในการ join ข้อมูล

![image](https://user-images.githubusercontent.com/105144684/195760020-f11c73ab-4042-449b-8fea-5a88d829b8d7.png)
![image](https://user-images.githubusercontent.com/105144684/195760096-4ff04d90-5c33-46a0-b26b-7a5416ca1f67.png)
![image](https://user-images.githubusercontent.com/105144684/195760146-c606b7f8-b0e5-4ad7-be89-da6c83fedfba.png)
![image](https://user-images.githubusercontent.com/105144684/195762008-edfcc91a-9ca7-444f-90c3-9e2f56d6e8ae.png)
![image](https://user-images.githubusercontent.com/105144684/195762055-d6ed0b51-902d-4503-a0cb-18e33d50f883.png)
![image](https://user-images.githubusercontent.com/105144684/195762170-277992d1-3ce9-47c6-9aa2-8f2c61a54143.png)

Rename ชื่อ column ให้เป็นภาษาไทยเพื่อให้เข้ากับ dataset เเละอ่านเข้าใจง่ายขึ้น 
![image](https://user-images.githubusercontent.com/105144684/195762223-a55caa13-b01d-4630-a6c8-706d094e3087.png)




