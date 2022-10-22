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
4. **Data Augmentation** 
- Herizontal and Vertical Flip for training set
- Validation Split = 0.2
```
train_datagenerate = tf.keras.preprocessing.image.ImageDataGenerator(
                                samplewise_center=True,
                                samplewise_std_normalization=True,
                                horizontal_flip=**True**,
                                vertical_flip=**True**,
                                validation_split=0.2) 
train_datagenerate.fit(x_train)
````
5. **Continue pre-processing step of each model to be trained as table below**

|No  |Model Name      |Procesing code |
|:---:|:---:             |---                               |
| 1. |**`VGG16`**  | tf.keras.applications.**`vgg16`**.preprocess_input()  |   
| 2. |**`DenseNet121`**| tf.keras.applications.**`densenet`**.preprocess_input()| 
| 3. |**`InceptionResNetV2`** | tf.keras.applications.**`inception_resnet_v2`**.preprocess_input()| 


<img width="641" alt="image" src="https://user-images.githubusercontent.com/69892468/197327680-d17e2514-ea09-4e6d-a002-75554b2d2539.png">
<img width="635" alt="image" src="https://user-images.githubusercontent.com/69892468/197327699-0db3a12a-e520-4c93-aaa6-14a2d43e07a3.png">

## 3. Network architecture🌐

### 3.1 Transfer learning
#### Model selection 
- In the experiment, we have used twenty ImageNet pre-trained models such as **`VGG16, ResNet50, InceptionResNetV2, DenseNet121, etc.`** to reuse low-level layers of the models (part of the feature extractor) with our custom dataset due to the small dataset differing from the ImageNet dataset. This also resulted in a shorter training time when compared to Fine-Tuning.
<br>We select **`3 models are VGG16, InceptionResNetV2 and DenseNet121`** from 20 models.

![image](https://user-images.githubusercontent.com/39288060/197341422-8cec35b3-7fd1-4e0a-a999-5c5dd8fb8b95.png)

- The main principle to choos these because they show **`similar Accuracy in different model sizes`**. Nevertheless, we still compare accuracy and time for training classification models in each.
- **`VGG16 Architecture`**

![image](https://user-images.githubusercontent.com/39288060/197343198-9d8c7333-4dd3-454a-9883-617e3565a4c1.png)

- **`DenseNet121 Architecture`**'

![image](https://user-images.githubusercontent.com/39288060/197343633-fe06497f-3e9d-4748-ab04-b3259a9658d5.png)

- **`InceptionResNetV2 Architecture`**
Inception-ResNet-v2 is a convolutional neural network that is trained on more than a million images from the ImageNet database. The network is 164 layers deep and can classify images into 1000 object categories, such as the keyboard, mouse, pencil, and many animals. As a result, the network has learned rich feature representations for a wide range of images.

![image](https://user-images.githubusercontent.com/39288060/197343528-3e38282d-ce01-4afe-b82c-60998c882b21.png)


### 3.2 Freezed the pre-trained parameters
**`Freezed the pre-trained CNN parameters to be non-trainable`** of three foundation models for transfer learning in part of feature extraction layer and created with a classification layer to be used classification image class that architecture of model has not learned before as in the detail of classification models below.

<img width="393" alt="image" src="https://user-images.githubusercontent.com/69892468/197326003-86613aa4-271f-4b58-bcef-c24430e9148b.png">

### 3.3 Fine-Tune Model
Once we have a model that is ready for transfer learning, we will fine-tuning the model to get the appropriate values for the available dataset, starting with fine-tuning in the classification section. layer first, with the following steps:

1. Set the model seed for fit and data augmentation to maintain the pattern in the sampling data.
2. Change the batch size and number of epoch.
3. Perform fine-tuning model by adjusting the number of nodes in dense layer and train to test accuracy.
4. Increase the number of dense layers.
5. If the model is overfitted, a dropout layer will be added.

When fine-tuning the classification layer, the unfreeze feature extraction layer is tested and the results are compared.



## 4. Training👻



## 5. Results📈


  

## 6.Discussion💭


## 7. Conclusion👑



## 8. References✍🏼

 
## _End Credit_
This study is a part of **Deep Learning course (DADS7202)**, Businuss Analytics and Data Science, National Institute of Development Admistration (NIDA)

## 💟 3PM Member's Contribution and Responsibility 
|No  |ID                |Name                              |% Contribution |Responsibility                             |
|:---:|:---:             |---                               |:---:            |:---|
|1. |6410422005     |Metpiya Learakkakorn|25% |Prepare dataset, Data cleaning, EDA, ML, MLP, Report, Conclusion|    
|2. |6410422015     |Khodchapan Vitheethum |25% |Prepare dataset, Data cleaning, EDA, ML, MLP, Report, Conclusion|
|3. |6410422017     |Peerat Pookpanich |25% |Prepare dataset, Data cleaning, EDA, ML, MLP, Report, Conclusion|
|4. |6410422031     |Anyamanee Pornpanvattana |25% |Prepare dataset, Data cleaning, EDA, ML, MLP, Report, Conclusion |
