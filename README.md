# CNN Classification
##  <font color="#8450B2">_Group: 3PM 👧🏻👩🏻👩🏼👦🏻_</font> <br>


## _Key Highlight✨✨_


## 1. Introduction🍆
![image](https://user-images.githubusercontent.com/69892468/197326343-3eee8f54-391e-4746-b571-422ddbbf47b6.png)
![image](https://user-images.githubusercontent.com/69892468/197326353-2463e09c-09de-45a9-b52b-9c1ad0eb246d.png)
![image](https://user-images.githubusercontent.com/69892468/197326356-6a052f2e-27ce-445d-a563-3587f3b1aff8.png)
![image](https://user-images.githubusercontent.com/69892468/197326360-134a798c-f218-4556-824f-bbf2cb75ec25.png)



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



## 3. Network architecture🌐

### 3.1 Transfer learning
<img width="479" alt="image" src="https://user-images.githubusercontent.com/69892468/197325982-5bd3e9e3-9db0-4d72-9002-9b5c8e549953.png">




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
