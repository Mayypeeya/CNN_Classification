# CNN Classification
##  <font color="#8450B2">_Group: 3PM 👧🏻👩🏻👩🏼👦🏻_</font> <br>


## _💫Key Highlight💫_

## 📖Contents
[Code.ipynp]()
 - [1. Introduction🍆🍅](https://github.com/Mayypeeya/CNN_Classification#1-introduction)
 - [2. Dataset🔎](https://github.com/Mayypeeya/CNN_Classification#2-data%EF%B8%8F)
 - [3. Network architecture🌐](https://github.com/Mayypeeya/CNN_Classification#3-network-architecture)
 - [4. Training👻](https://github.com/Mayypeeya/CNN_Classification#4-training)
 - [5. Results📈](https://github.com/Mayypeeya/CNN_Classification#5-results)
 - [6. Discussion💭](https://github.com/Mayypeeya/CNN_Classification#6discussion)
 - [7. Conclusion👑](https://github.com/Mayypeeya/CNN_Classification#7-conclusion)
 - [8. References✍🏼](https://github.com/Mayypeeya/CNN_Classification#8-references)


## 1. Introduction🍆🍅
Transfer Learning is about pre-trained model usage or weights of models that were trained with another huge dataset to be used with an interesting dataset. This helps to reduce the process and time for training the model manually and also improves the efficiency of the model's learning.
<br>Our group used weight from a pre-trained of CNN model that was trained by ImageNet Dataset. And used it with multi-class classification. The eggplant 3 types and tomato were classified as having individual characteristics along with this dataset has never been trained before. The classes of different data that be used have different characteristics as follows:

![image](https://user-images.githubusercontent.com/101736826/197330900-847b5260-5ccc-479c-93ac-8d12f763eda0.png)


## 2. Dataset🖼️
- We have compiled images by searching on the internet total of 4 types which total 600 images. See details in each class in the table.
#### 🔎Data collection (Internet Seaching) 
[🔗Link to download the dataset:](https://github.com/Mayypeeya/CNN_Classification/tree/main/01_DataSet_image)
<img width="523" alt="image" src="https://user-images.githubusercontent.com/69892468/197325994-e3aa997e-634f-4615-92fe-96e2a92702eb.png">

<img width="635" alt="image" src="https://user-images.githubusercontent.com/69892468/197326053-fa8b8df7-bacb-4e64-ad59-8ba1eaf65c49.png">

#### 📑Data preparation
In the process, all images were converted to .jpg files and manually extracted into sub-folders for easy access in the next steps.
1. **Transform the image dataset** to NUMPY array in 3 channels by using "cv2.imread"
2. **Resize the image dataset** to 224x224 pixels
3. **Split Dataset** by mannual selection at 30% for testing set.
- **`test_size`** = 0.3
- **`Train Data`**: 105 images
- **`Test Data`**: 45 images
4. **Data Augmentation** filp images in Herizontal and Vertical
```
train_datagenerate = tf.keras.preprocessing.image.ImageDataGenerator(
                                samplewise_center=True,
                                samplewise_std_normalization=True,
                                horizontal_flip=**True**,
                                vertical_flip=**True**,
                                validation_split=0.2) 
train_datagenerate.fit(x_train)
````



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
