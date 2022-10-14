# Latthawan-Mini-Project_Midterm_DADS5001
การวิเคราะห์ข้อมูลปริมาณน้ำฝนกับพื้นที่เสียงน้ำท่วมในประเทศไทย ปี 2022

บทความวิเคราะห์นี้ จัดทำขึ้นเพื่อหาคำตอบว่าในพื้นที่ที่มีฝนตกมากๆ จะทำให้เกินน้ำท่วมหรือไม่?

แหล่งข้อมูลที่ใช้ในการทำ สามารถดาวน์โหลดได้จาก link ด้านล่าง หรือโหลดได้จากไฟล์ excel ด้านบนค่ะ
https://data.go.th/dataset/spatial-rain (ข้อมูลปริมาณน้ำฝนเชิงพื่นที่รายเดือนรายจังหวัด)(ไฟล์ area-flood)
https://data.go.th/dataset/flood-area (ข้อมูลพื่นที่เสี่ยงน้ำท่วมรายเดือน)(ไฟล์ spatial-rain)
https://data.go.th/dataset/proviceandregionthailand (ชุดข้อมูลจังหวัดและภูมิภาคในประเทศไทย)(ไฟล์ Province-Master)


import sys
import pandas as pd
import numpy as np
import plotly.express as px
import matplotlib as mpl
%matplotlib inline
import matplotlib.pyplot as plt
import seaborn as sns
plt.rcParams['font.family']='Tahoma'
print( f"Python {sys.version}" )
print( f"Pandas {pd.__version__}" )
print( f"NumPy {np.__version__}" )
       
