# Latthawan-Mini-Project_Midterm_DADS5001
การวิเคราะห์ข้อมูลปริมาณน้ำฝนกับพื้นที่เสี่ยงน้ำท่วมในประเทศไทย ปี 2022

บทความวิเคราะห์นี้ จัดทำขึ้นเพื่อหาคำตอบว่าในพื้นที่จังหวัดที่มีฝนตกในปริมาณมากๆ จะมีความเสี่ยงที่จะน้ำท่วมหรือไม่?

แหล่งข้อมูลที่ใช้ในการทำ สามารถดาวน์โหลดได้จากทาง link หรือไฟล์ excel ด้านบนค่ะ
  1. https://data.go.th/dataset/spatial-rain 
  2. https://data.go.th/dataset/flood-area 
  3. https://data.go.th/dataset/proviceandregionthailand 
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

![image](https://user-images.githubusercontent.com/105144684/195764282-4d38452f-d0d7-48d6-a635-23b32770cd88.png)

เนื่องจากต้องการนำข้อมูลจากไฟล์ spatial-rain และ area-flood มารวมกัน เเต่ทั้ง 2 นี้มีรายเอียดลงถึงรายเดือน จึงต้องทำการสร้าง Key โดยการนำรหัสจังหวัด-เดือน เพื่อใช้ในการ join ข้อมูล

![image](https://user-images.githubusercontent.com/105144684/195760020-f11c73ab-4042-449b-8fea-5a88d829b8d7.png)
![image](https://user-images.githubusercontent.com/105144684/195760096-4ff04d90-5c33-46a0-b26b-7a5416ca1f67.png)
![image](https://user-images.githubusercontent.com/105144684/195760146-c606b7f8-b0e5-4ad7-be89-da6c83fedfba.png)
![image](https://user-images.githubusercontent.com/105144684/195762008-edfcc91a-9ca7-444f-90c3-9e2f56d6e8ae.png)
![image](https://user-images.githubusercontent.com/105144684/195762055-d6ed0b51-902d-4503-a0cb-18e33d50f883.png)
![image](https://user-images.githubusercontent.com/105144684/195762170-277992d1-3ce9-47c6-9aa2-8f2c61a54143.png)

Rename ชื่อ column ให้เป็นภาษาไทยเพื่อให้เข้ากับ dataset เเละอ่านเข้าใจง่ายขึ้น 

![image](https://user-images.githubusercontent.com/105144684/195762223-a55caa13-b01d-4630-a6c8-706d094e3087.png)

นำข้อมูลมาจัดทำกราฟ เพื่อแสดงเทรนของปริมาณน้ำฝนในประเทศไทย ตามเดือนในปี 2018-2022
![image](https://user-images.githubusercontent.com/105144684/195765066-295991d6-7c94-4c7a-befd-e547febac213.png)
![output_20_0](https://user-images.githubusercontent.com/105144684/195765174-92066c39-9619-4ce5-98bb-3db1e8d4ed1d.png)

ดูรายละเอียดตามปี

![image](https://user-images.githubusercontent.com/105144684/195766464-4a3edbab-4f53-40f1-b9c9-874fe2e05a7a.png)
![output_22_0](https://user-images.githubusercontent.com/105144684/195766429-8780cc92-cbf6-4e24-bdb6-f5d8a7041dd2.png)

นำข้อมูลมาจัดทำกราฟ เพื่อแสดงเทรนของปริมาณน้ำฝนในประเทศไทย ตามภูมิภาคในปี 2018-2022
![image](https://user-images.githubusercontent.com/105144684/195766533-748d9747-8dc1-40da-9b4c-e7a1d0e42a21.png)
![output_23_0](https://user-images.githubusercontent.com/105144684/195766562-650a5d7c-2b4f-4ef4-b40a-44bdcdf04990.png)
![image](https://user-images.githubusercontent.com/105144684/195766590-16ac41c4-45b9-4ce5-bce8-9842abf39546.png)

ดูรายละเอียดตามปี

![output_24_0](https://user-images.githubusercontent.com/105144684/195766612-8476971e-7188-4257-9a6b-c40be0799a0f.png)

กรองข้อมูลเฉพาะปี 2022 

![image](https://user-images.githubusercontent.com/105144684/195768421-a39ad1f2-a17e-4f9e-aae6-9c5227e3079f.png)
![image](https://user-images.githubusercontent.com/105144684/195768498-3e25de02-96d6-478f-9f1a-e5151f7eb452.png)

นำข้อมูลมาจัดทำกราฟ เพื่อแสดงเทรนของปริมาณน้ำฝนในประเทศไทย ตามภูมิภาคในปี 2022

![output_26_0](https://user-images.githubusercontent.com/105144684/195768520-c98da16a-621b-48bd-952b-d31ebb31c920.png)

กรองข้อมูลเฉพาะปี 2022 เดือน 8 ซึ่งเป็นข้อมูลที่อัปเดตล่าสุด เพื่อนำมาวิเคราะห์ จังหวัดที่ปริมาณน้ำฝนสูง จะเป็นพื้นที่เสี่ยงน้ำท่วมหรือไม่

![image](https://user-images.githubusercontent.com/105144684/195769149-06199e10-ff75-4f74-aea5-c08c8fd2dd24.png)

นำข้อมูลมาจัดทำกราฟ เพื่อแสดงเทรนของปริมาณน้ำฝนในประเทศไทย ตามภูมิภาคในปี 2022 เดือน 8
จะเห็นว่า ภูมิภาคที่มีปริมาณน้ำฝนมากที่สุด คือ ภาคตะวันออกเฉียงเหนือ

![image](https://user-images.githubusercontent.com/105144684/195770309-c7285bdd-e114-4fc4-be59-dd873a3c90d0.png)
![output_28_0](https://user-images.githubusercontent.com/105144684/195770323-98105531-a1c9-4a2f-ba1e-556bd7a9ae9e.png)

คำนวณค่าสถิติของปริมาณน้ำฝนในปี 2022 เดือน 8 

![image](https://user-images.githubusercontent.com/105144684/195770464-c12fb39c-c12b-4bb3-98e1-a882084a3ed4.png)

นำข้อมูลมาจัดทำกราฟ เพื่อแสดงเทรน 10 อันดับแรกของปริมาณน้ำฝนในประเทศไทย ตามจังหวัดในปี 2022 เดือน 8
จะเห็นว่า จังหวัดที่มีปริมาณน้ำฝนมากที่สุด คือ จังหวัดนครนายก 

![image](https://user-images.githubusercontent.com/105144684/195771383-9dd9b695-7569-4c03-8222-5d2a91ea551d.png)
![output_30_0](https://user-images.githubusercontent.com/105144684/195771711-fecd7bba-bc02-4338-afd7-4aa2301990ea.png)

นำข้อมูลมาจัดทำกราฟ แสดงจำนวนตำบล ตามประเภทความเสี่ยง เพื่อดูสัดส่วนของความเสี่ยง

![image](https://user-images.githubusercontent.com/105144684/195772798-444e27a5-fbc3-48cb-9d89-96d4b7b8fc92.png)
![image](https://user-images.githubusercontent.com/105144684/195773461-bef799aa-e0af-4af6-9c45-a22bc4c9ee75.png)
![output_32_1](https://user-images.githubusercontent.com/105144684/195773480-4ab3cab8-44c9-49fe-915c-8dda6cbdae4a.png)

จากนั้นกรองข้อมูลเฉพาะ ประเภทความเสี่ยงสูง  เพื่อนำมาดูว่าจังหวัดที่มีจำนวนตำบล ที่มีความเสี่ยงสูงที่จะเกิดน้ำท่วมมากที่สุด
จะเห็นว่า จังหวัดที่มีจำนวนตำบล ที่มีความเสี่ยงสูงที่จะเกิดน้ำท่วมมากที่สุด คือ จังหวัดสุโขทัย 

![image](https://user-images.githubusercontent.com/105144684/195773584-ddeba6b7-b59a-4b54-a230-d923237f96cc.png)
![image](https://user-images.githubusercontent.com/105144684/195773894-6dbe615e-d1f6-4ea3-91b7-4e4019ab228a.png)
![output_34_0](https://user-images.githubusercontent.com/105144684/195773917-d4e68570-afe7-4e40-afc1-bce4b00be1a5.png)

บทสรุป จากคำถามที่ว่า ในพื้นที่จังหวัดที่มีฝนตกปริมาณมากๆ จะมีความเสี่ยงที่จะน้ำท่วมหรือไม่?
โดยจากการที่ได้นำข้อมูล ปริมาณน้ำฝนเชิงพื่นที่ และ ข้อมูลพื่นที่เสี่ยงน้ำท่วม จะเห็นได้ว่า จังหวัดนครนายก ที่มีปริมาณน้ำฝนมากที่สุด ไม่ได้เป็นจังหวัดที่มีความเสี่ยงน้ำท่วมสูง เเต่ก็จะมีบางจังหวัด(จังหวัดหนองคาย จังหวัดนครพนม และจังหวัดบึงกาฬ)ที่มีปริมาณน้ำฝนอยู่ใน 10 อันดับแรก เป็นจังหวัดที่มีความเสี่ยงน้ำท่วมสูง ดังรูปด้านล่าง

![image](https://user-images.githubusercontent.com/105144684/195792257-a3e0ccd8-37cc-4989-a3c7-3a12ad776ff0.png)

ดังนั้น จึงสรุปได้ว่า ปัจจัยที่ทำในการนำท่วมอาจจะไม่ได้มีเพียงเเค่ปริมาณน้ำฝน อาจจะมีปัจจัยอื่นๆ ที่ส่งผลให้เกิดน้ำท่วม เช่น  น้าทะเลหนุนสูง พื้นที่เป็นแอ่งกระทะ  น้าไหลจากภูเขา(น้ำป่า) หรือการก่อสร้างถนนขวางทางน้า เป็นต้น





