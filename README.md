# Introduction

**In this project for a test task I needed to complete a task from kaggle**
**from Deep Learning Satellite Image Ship Detection(https://www.kaggle.com/competitions/airbus-ship-detection).**

---

### Detecting Ships using Satellite Images with Deep Learning

![image](https://github.com/boghtml/Test_Exercise_Ship_Segmentation-Final-/assets/119760440/2e76c762-0b49-42f3-a734-5932a88b6ace)

---

### In this project, I used the following:

**Run Length Encoding (RLE):**
- RLE is a data compression method.

**U-NET Architecture:**
- This architecture consists of three sections: reduction, compression, and expansion.
- However, the heart of this architecture is the expansion partition.
- This action ensures that features learned when compressing an image are used to reconstruct it.

**Keras:**
- Keras is a high-level machine learning library that runs on top of TensorFlow or Theano.

**Keras Callbacks:**
- I used Keras Callbacks to set some functions while training the model:
  - **ModelCheckpoint:** Stores model weights with results during training.
  - **ReduceLROnPlateau:** Reduces learning rate.
  - **EarlyStopping:** Stops training if a certain metric does not improve within a certain number of "patience=15" epochs.

## Dataset & Aim<a class="anchor"  id="h1"></a>
    
![image](https://github.com/boghtml/Test_Exercise_Ship_Segmentation-Final-/assets/119760440/23e4e27b-19f9-4571-97ef-a5f2e7311962)

       
- We will be dealing with this [dataset](https://www.kaggle.com/competitions/airbus-ship-detection/data).
- Search "Airbus Ship Detection Dataset" and add it to this kernel.
- It consists of train and test image folders along with sample_submission and train_ship_segmentation csv files.
- Soon we will jump into more details of these files.
- We will build and train UNET model from scratch for image segmentaion.

## Image Classification, Object Detection and Semantic Segmentation <a class="anchor"  id="h2"></a>

- These are some of the most common applications of machine learning in computer vision.

![image](https://github.com/boghtml/Test_Exercise_Ship_Segmentation-Final-/assets/119760440/9c4d669a-399d-42c0-b6b1-3bd8b72b49c0)

* **Image Classificaton:-** Determines whether a certain type of object is present in an image or not.    
* **Object Detection:-** Object detection takes image classification one step further and provides the bounding box where detected objects are located.        
* **Semantic Segmentation:-** Specifies the object class of each pixel in an input image. This is what we are targeting in this notebook!  
* **Instance Segmentation:-** Separates individual instances of each type of object. 

## Run Length Encoding (RLE) and Decoding <a class="anchor"  id="h4"></a>

- Run Length Encoding (RLE) is a form of compression that retains all the original data, ensuring perfect reconstruction from the compressed version.

- Lossless compression, as employed by RLE, guarantees that the compressed data can be fully reconstructed to its original form without any loss of information.

- The methodology involves traversing the data and tallying the repetitions of each data point consecutively without interruptions.

- RLE is particularly effective when dealing with data sequences that exhibit prolonged stretches of identical values.

![image](https://github.com/boghtml/Test_Exercise_Ship_Segmentation-Final-/assets/119760440/a53b9013-4ec0-43ec-bc48-04dd6646c992)

- However, if the data lacks extended sequences and is inherently intricate, the application of RLE may lead to suboptimal compression results.

- Various RLE variations exist, such as running across rows, running across columns, running until a pixel changes, etc.

- To utilize RLE data, it is imperative to undergo a decompression process known as run length decoding.    


## U-NET architecture <a class="anchor"  id="h6"></a>
​
<img src="https://miro.medium.com/max/720/1*f7YOaE4TWubwaFF7Z1fzNw.png" width = 80%>
​
![image](https://github.com/boghtml/Test_Exercise_Ship_Segmentation-Final-/assets/119760440/692b7b89-92a7-4ff6-8538-669925ac0d1f)

- The U-NET is named after the configuration of its architecture.
- Each blue box corresponds to a feature map with multiple channels.
- The number of channels is indicated at the top of each box.
- The x-y size is displayed at the lower left corner of the box.
- Arrows illustrate the respective operations, as described in the bottom right of the image.
- This architecture comprises three segments: Contraction, Bottleneck, and Expansion.
- However, the core of this architecture resides in the expansion segment.
- This process ensures that the features learned during the contraction phase are utilized to reconstruct the image.
​
## Building and Training U-NET from Scratch <a class="anchor"  id="h7"></a>
​
<img src = "https://i.stack.imgur.com/o5TBk.png" width = 45%>       
​
![image](https://github.com/boghtml/Test_Exercise_Ship_Segmentation-Final-/assets/119760440/29dd83ad-db34-47d3-ae2f-844aeac201a5)
