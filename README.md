# CNN Classification
##  <font color="#8450B2">_Group: 3PM 👧🏻👩🏻👩🏼👦🏻_</font> <br>


## _💫Key Highlight💫_
- Transfer Learning and Fine-Tuning applied to our custom dataset, the EggPlant images clasification.
- Grad-CAM was used to understand which parts of CNN capture image to identify as belonging to a given class.
- The best Model is DenseNet121 which compatable with vegetable class and has less training time 


## 📖Contents
 - [1. Introduction🍆🍅](https://github.com/Mayypeeya/CNN_Classification#1-introduction)
 - [2. Dataset🔎](https://github.com/Mayypeeya/CNN_Classification#2-data%EF%B8%8F)
  <br> Link: [Code_Image_Preprocessing](https://github.com/Mayypeeya/CNN_Classification/blob/5caa66a5f75f44d3047028d52f707882f68e59de/image_preprocessing.ipynb)
 - [3. Network architecture🌐](https://github.com/Mayypeeya/CNN_Classification#3-network-architecture)
 - [4. Training📈](https://github.com/Mayypeeya/CNN_Classification#4-training)
   <br>***VGG16***
   <br>[Code_WithOut_Tune:](https://github.com/Mayypeeya/CNN_Classification/blob/main/VGG16_NoTune.ipynb)
   <br>[Code_With_Tune](https://github.com/Mayypeeya/CNN_Classification/blob/main/VGG16_Tune_FineTune_Unfreeze.ipynb)
   <br>***DenseNet121***
   <br>[Code_WithOut_Tune:](https://github.com/Mayypeeya/CNN_Classification/blob/main/DenseNet121_NoTune.ipynb)
   <br>[Code_With_Tune](https://github.com/Mayypeeya/CNN_Classification/blob/main/DenseNet121_FineTune_Unfreeze.ipynb)
   <br>***InceptionResNetV2***
   <br>[Code_WithOut_Tune:](https://github.com/Mayypeeya/CNN_Classification/blob/main/InceptionResNetV2_NoTune.ipynb)
   <br>[Code_With_Tune](https://github.com/Mayypeeya/CNN_Classification/blob/main/InceptionResNetV2_FineTune_Unfreeze.ipynb)
   
 - [5. Results📊](https://github.com/Mayypeeya/CNN_Classification#5-results)
 - [6. Discussion🗣️](https://github.com/Mayypeeya/CNN_Classification#6discussion)
 - [7. Conclusion👑](https://github.com/Mayypeeya/CNN_Classification#7-conclusion)
 - [8. References✍🏼](https://github.com/Mayypeeya/CNN_Classification#8-references)


## 1. Introduction🍆🍅
Transfer Learning is about pre-trained model usage or weights of models that were trained with another huge dataset to be used with an interesting dataset. This helps to reduce the process and time for training the model manually and also improves the efficiency of the model's learning.
<br>Our group used weight from a pre-trained of CNN model that was trained by ImageNet Dataset. And used it with multi-class classification. The eggplant 3 types and tomato were classified as having individual characteristics along with this dataset has never been trained before. The classes of different data that be used have different characteristics as follows:

![image](https://user-images.githubusercontent.com/101736826/197330900-847b5260-5ccc-479c-93ac-8d12f763eda0.png)


## 2. Dataset🖼️
- We have compiled images by searching on the internet total of 4 types which total 600 images. See details in each class in the table.
- 
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
<br>Inception-ResNet-v2 is a convolutional neural network that is trained on more than a million images from the ImageNet database. The network is 164 layers deep and can classify images into 1000 object categories, such as the keyboard, mouse, pencil, and many animals. As a result, the network has learned rich feature representations for a wide range of images.

![image](https://user-images.githubusercontent.com/39288060/197343528-3e38282d-ce01-4afe-b82c-60998c882b21.png)

### 3.2 Freezed the pre-trained parameters
**`Freezed the pre-trained CNN parameters to be non-trainable`** of three foundation models for transfer learning in part of feature extraction layer and created with a classification layer to be used classification image class that architecture of model has not learned before as in the detail of classification models below.

<img width="393" alt="image" src="https://user-images.githubusercontent.com/69892468/197326003-86613aa4-271f-4b58-bcef-c24430e9148b.png">

### 3.3 Fine-Tune Model
- Once we have transfer learning model, we will fine-tune the classification model to get the appropriate values for this dataset by starting with the following steps:
```
1. Set seed number to maintain the pattern in the sampling data to fit model and augmentation.
2. Change the batch size and number of epoch.
3. Perform fine-tuning model by adjusting nodes number in dense layer, and then train to confirm accuracy.
4. Increase Dense layers.
5. If the model shown Overfit, add dropout layer into model.
```


## 4. Training📈
### 4.1 Result after tuning model 
### Model #1 (VGG16 as Feature Extractor )
- **`Best Accuracy: 96.67%`**
![image](https://user-images.githubusercontent.com/39288060/197346962-7115df1d-0b93-4106-b5c4-0a87e74ca2c5.png)

### Model #2 (DenseNet121 as Feature Extractor)
- **`Best Accuracy: 98.33%`**
![image](https://user-images.githubusercontent.com/39288060/197346979-0a8bbaf9-1e72-4605-b120-d8f6693f5224.png)

### Model #3 (InceptionResNetV2 as Feature Extractor)
- **`Best Accuracy: 98.89%`**
![image](https://user-images.githubusercontent.com/39288060/197347036-5d8ab2aa-20cd-41ce-bbfe-284e72d32dfe.png)

## 5. Results📊
### 5.1 Freezed the pre-trained parameters 
The results of model training no fine-tuning With the parameters in 3.2, DenseNet121 is the model with the highest accuracy of 0.968±0.004 and the lowest average training time of 27.5 sec. InceptionResNetV2 and VGG16 provide accuracy and a lower training time respectively.

![image](https://user-images.githubusercontent.com/39288060/197344072-6b26b12a-084b-4126-acc9-8596c09c19b3.png)

### 5.2 Comparing Models
**The best model is DenseNet121 has accuracy increase 1.6% from 97.22% to 98.89% **
![image](https://user-images.githubusercontent.com/39288060/197352161-93c090f0-d1ef-41bc-82a3-071c71d682d3.png)
![image](https://user-images.githubusercontent.com/69892468/197368637-9ad2b853-57d4-4462-8818-e8d6b829bfa7.png)



### 5.3 Visualizing CNN learned with Grad-Cam
![image](https://user-images.githubusercontent.com/101736826/197352472-9e2ad472-bf61-4e01-97c8-97bebe1783ca.png)

  

## 6.Discussion🗣️
1. Import Data Method: Using **Numpy Array** to support multiple format of image dataset and make sure that augmentation is already arranged in the correct class.
2. From the experiment result, we found that adjusting the augmentation feature directly affects accuracy because augmentation is a regularization method that reduces data training is overfit.
3. When using layer dropout (0.2) in **InceptionResNetV2 Model**, it will **reduced 20% test accuracy** approximately.
4. **InceptionResNetV2 Model** provides lower accuracy when increasing batch size.

## 7. Conclusion👑
- In this experiment, we found that using some higher model architectures requiring computational power did not guarantee to work best with the dataset. On the other hand, DenseNet121 architecture with the less complexity that suitable with our dataset
- Transfer learning by using a pre-trained model that trains on the imagenet dataset and uses it as a feature extractor, resulting in a model with good performance in more than 90%. In other hand, we unfreeze some layer that closer clasification is better becuase it fit with our image dataset. 


## 8. References✍🏼

### Version:
![image](https://user-images.githubusercontent.com/39288060/197344245-e48a96d4-cf3a-47fe-823f-81d7423c3b5a.png)

### Appendix:
- [Keras Applications](https://keras.io/api/applications)
- [Asst.Prof.ThitiratSiriborvornratanakul, Ph.D.](https://www.facebook.com/thitirat.thelecturer)**GradCAM method: using example code in class06 of DADS7202**

### Citing:[citing.file](https://github.com/Mayypeeya/CNN_Classification/blob/5caa66a5f75f44d3047028d52f707882f68e59de/citing.bib)

 
## _End Credit_
This study is a part of **Deep Learning course (DADS7202)**, Businuss Analytics and Data Science, National Institute of Development Admistration (NIDA)

## 💟 3PM Member's Contribution and Responsibility 
|No  |ID                |Name                              |% Contribution |Responsibility                             |
|:---:|:---:             |---                               |:---:            |:---|
|1. |6410422005     |Metpiya Learakkakorn|25% |Prepare dataset, Train model-DenseNet121,  Conclusion|    
|2. |6410422015     |Khodchapan Vitheethum |25% |Prepare dataset, Train model-VGG16,  Conclusion|
|3. |6410422017     |Peerat Pookpanich |25% |Prepare dataset, Train model-InceptionResNetV2, Conclusion|
|4. |6410422031     |Anyamanee Pornpanvattana |25% |Prepare dataset, Freeze model, Report, Conclusion|
