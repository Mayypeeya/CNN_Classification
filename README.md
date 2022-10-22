# CNN Classification
##  <font color="#8450B2">_Group: 3PM 👧🏻👩🏻👩🏼👦🏻_</font> <br>


## _Key Highlight✨✨_


## 1. Introduction🍆
<img width="175" alt="image" src="https://user-images.githubusercontent.com/69892468/197326383-4b305664-70b8-454d-83f6-14231974a77d.png">
<img width="137" alt="image" src="https://user-images.githubusercontent.com/69892468/197326388-5e235574-87ab-4f98-95d8-d89fa0991fc8.png">
<img width="147" alt="image" src="https://user-images.githubusercontent.com/69892468/197326411-54a6827f-3c2a-4a66-b8f1-64047861a2c3.png">
<img width="121" alt="image" src="https://user-images.githubusercontent.com/69892468/197326425-bc6a7762-3938-43e5-a9fb-0d259212833f.png">




## 2. Data🖼️

### Data source
<img width="523" alt="image" src="https://user-images.githubusercontent.com/69892468/197325994-e3aa997e-634f-4615-92fe-96e2a92702eb.png">


<img width="635" alt="image" src="https://user-images.githubusercontent.com/69892468/197326053-fa8b8df7-bacb-4e64-ad59-8ba1eaf65c49.png">






### Data preparation



```
train_datagen = tf.keras.preprocessing.image.ImageDataGenerator(
                                samplewise_center=True,
                                samplewise_std_normalization=True,
                                horizontal_flip=True,
                                vertical_flip=True,
                                validation_split=0.2) 
train_datagen.fit(x_train)
 ```
 
<img width="641" alt="image" src="https://user-images.githubusercontent.com/69892468/197327680-d17e2514-ea09-4e6d-a002-75554b2d2539.png">
<img width="635" alt="image" src="https://user-images.githubusercontent.com/69892468/197327699-0db3a12a-e520-4c93-aaa6-14a2d43e07a3.png">

## 3. Network architecture🌐

### 3.1 Transfer learning
<img width="452" alt="image" src="https://user-images.githubusercontent.com/69892468/197329795-06d98ea5-affd-4234-a9ad-cb1d14b624f3.png">




### 3.2 No Fine-tuning
<img width="393" alt="image" src="https://user-images.githubusercontent.com/69892468/197326003-86613aa4-271f-4b58-bcef-c24430e9148b.png">

### 3.3 Fine-tuning







## 4. Training👻



## 5. Results📈


  

## 6.Discussion💭


## 7. Conclusion👑



## 8. References✍🏼

 
## _End Credit_


_งานชิ้นนี้เป็นส่วนหนึ่งของ วิชาการวิเคราะห์เชิงกำหนดและการหาค่าเหมาะสุดประยุกต์ หลักสูตรวิทยาศาสตรมหาบัณฑิต สาขาวิชาการวิเคราะห์ข้อมูลและวิทยาการข้อมูล มหาวิทยาลัยสถาบันบัณฑิตพัฒนบริหารศาสตร์_
