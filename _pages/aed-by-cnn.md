---
layout: page
title: Audio Event Detection
permalink: research/aed-by-cnn/
subtitle: Weakly Supervised Learning on Audio Event Detection
---

This page is a description of the following paper:

T.-W. Su, J.-Y. Liu, Y.-H. Yang, **Weakly-Supervised Audio Event Detection using Event-Specific Gaussian Filters and Fully Convolutional Networks**, in proceedings of *the IEEE International Conference on Acoustics, Speech and Signal Processing (ICASSP)*, New Orleans, USA. March, 2017
<!-- In this topic, we try to discover not only **the sound events happened in an audio clip** (clip-level information) but also **the temporal positions of the detected sounds** (frame-level information). Since creating frame-level annotated data can be extremely time-consuming, we proposed a model based on **convolutional neural networks** that relies on **data with only clip-level labels (weakly supervised data) for training**.
 -->

### Abstract

Audio event detection aims at **discovering the elements inside an audio clip**. 
In addition to labeling the clips with the audio events, we want to **find out the temporal locations of these events**. 
However, creating clearly annotated training data can be very time-consuming. 
Therefore, we provide a model based on **convolutional neural networks** that relies only on **weakly supervised data for training**. 
These data can be directly obtained from online platforms, such as Freesound, with the clip-level labels assigned by the uploaders. 
The structure of our model is extended to a **fully convolutional networks**, and an **event-specific Gaussian filter layer** is designed to advance its learning ability. 
Besides, this model is able to detect frame-level information, e.g., the temporal position of sounds, even when it is trained merely with clip-level labels.

### Datasets

Our model is trained with **[UrbanSound](https://serv.cusp.nyu.edu/projects/urbansounddataset/urbansound.html) Dataset (US)**. We tested our clip-level result on [UrbanSound8K](https://serv.cusp.nyu.edu/projects/urbansounddataset/urbansound8k.html) Dataset (8K) and frame-level result on US. We used ten-folded cross-validation for testing. There are totally 1302 files in US and 8732 files in 8K.

| Class            | # of Data (US)      | # of Data (8K) | 
| ---------------- | -------------------:| -------------------:| 
| Air conditioner  | 64                  | 1000                |
| Car horn         | 125                 | 429                 |
| Children playing | 158                 | 1000                |
| Dog bark         | 337                 | 1000                |
| Drilling         | 119                 | 1000                |
| Engine idling    | 97                  | 1000                |
| Gun shot         | 117                 | 347                 |
| Jackhammer       | 45                  | 1000                |
| Siren            | 74                  | 929                 |
| Street music     | 166                 | 1000                |
| **Total**        | **1302**            | **8732**            |


### Evaluation Settings

**Input data: log-melspectrogram and its delta**

#### Log-melspectrogram:
- Sampling rate: 44100Hz
- Window size of STFT: [1024, 4096, 16384] for multi-scale
- Hop size of STFT: 512
- Number of Mel bands: 128

#### Delta:
- Width to compute: 9
- The order of the difference operator: 1


### Clip-level Result

We achieved an overall accuracy of 59.88%, and the accuracy of each class is shown below.

| Class            | Accuracy (%)  | Class            | Accuracy (%)  |
| ---------------- | -------------:| ---------------- | -------------:|
| Air conditioner  | 76.7          | Engine idling    | 51.8          |
| Car horn         | 69.0          | Gun shot         | 94.4          |
| Children playing | 41.8          | Jackhammer       | 39.8          |
| Dog bark         | 79.5          | Siren            | 59.0          |
| Drilling         | 52.3          | Street music     | 61.3          |



 To be more precise, we provide the confusion matrices.

| Abbr | Class            | Abbr | Class            |
| ---- | ---------------- | ---- | ---------------- |
| AC   | Air conditioner  | EI   | Engine idling    |
| CH   | Car horn         | GS   | Gun shot         |
| CP   | Children playing | JA   | Jackhammer       |
| DB   | Dog bark         | SI   | Siren            |
| DR   | Drilling         | SM   | Street music     |

<img style="width: 60%;" src="/assets/img/aed-by-cnn/confusion_matrix.png">
<img style="width: 60%;" src="/assets/img/aed-by-cnn/n_confusion_matrix.png">

From these matrices, we can see that the model correctly classified most of the clips. 
The largest problem appears in the first column, that is, most of the incorrect results are predicted to be "air conditioner" (AC).
As we analyze the result, we found that most of the clips classified to AC have a final prediction smaller than 0.01 (the scale is from 0 to 1). 
This phenomenon only severely happened in AC, so we speculate that the AC class has learned something that not only appears in many clips but also generally small in magnitude -- **the noise**.

### Frame-level Result

The overall area-under-ROC-curve (AUC) score of 0.738, and the AUC score of each class is shown below.

| Class            | AUC score     | Class            | AUC score     |
| ---------------- | -------------:| ---------------- | -------------:|
| Air conditioner  | 0.612         | Engine idling    | 0.688         |
| Car horn         | 0.807         | Gun shot         | 0.921         |
| Children playing | 0.594         | Jackhammer       | 0.704         |
| Dog bark         | 0.790         | Siren            | 0.763         |
| Drilling         | 0.764         | Street music     | 0.737         |

**In the following part, we will discuss the frame-level result by looking into their final predictions.** 

First, let's see some plots of the successful results. *Blue line represents the final prediction, and red line denotes the ground truth*.

<center>
<img class="frame-level-plot" src="/assets/img/aed-by-cnn/frame-level/42937_4.png">
<img class="frame-level-plot" src="/assets/img/aed-by-cnn/frame-level/174276_7.png">
<img class="frame-level-plot" src="/assets/img/aed-by-cnn/frame-level/186936_5.png">
<img class="frame-level-plot" src="/assets/img/aed-by-cnn/frame-level/194753_3.png">
<img class="frame-level-plot" src="/assets/img/aed-by-cnn/frame-level/194910_9.png">
<img class="frame-level-plot" src="/assets/img/aed-by-cnn/frame-level/46391_1.png">
<img class="frame-level-plot" src="/assets/img/aed-by-cnn/frame-level/49313_2.png">
<img class="frame-level-plot" src="/assets/img/aed-by-cnn/frame-level/34708_6.png">
<img class="frame-level-plot" src="/assets/img/aed-by-cnn/frame-level/157866_8.png">
<img class="frame-level-plot" src="/assets/img/aed-by-cnn/frame-level/189985_0.png">
<img class="frame-level-plot" src="/assets/img/aed-by-cnn/frame-level/9674_1.png">
<img class="frame-level-plot" src="/assets/img/aed-by-cnn/frame-level/135528_6.png">
<img class="frame-level-plot" src="/assets/img/aed-by-cnn/frame-level/22347_3.png">
<img class="frame-level-plot" src="/assets/img/aed-by-cnn/frame-level/104998_7.png">
<img class="frame-level-plot" src="/assets/img/aed-by-cnn/frame-level/189989_0.png">
</center>
---

However, there are still some flaws in the results. Take "children playing" (CP) for example, we expect the event to be a long continuous event, but our model *detected only the particularly loud parts, such as yelling and shouting, of children's sound*. Therefore, the frame-level results appear to be like this:

<center>
<img class="frame-level-plot" src="/assets/img/aed-by-cnn/frame-level/6902_2.png">
<img class="frame-level-plot" src="/assets/img/aed-by-cnn/frame-level/13579_2.png">
<img class="frame-level-plot" src="/assets/img/aed-by-cnn/frame-level/17973_2.png">
</center>

The same problem happens in "street music" (SM) as well:

<center>
<img class="frame-level-plot" src="/assets/img/aed-by-cnn/frame-level/7390_9.png">
<img class="frame-level-plot" src="/assets/img/aed-by-cnn/frame-level/16860_9.png">
<img class="frame-level-plot" src="/assets/img/aed-by-cnn/frame-level/14385_9.png">
</center>

---

Another problem occurs in "air conditioner" (AC). As mentioned in clip-level evaluation, many clips of AC *result in small predicted values* (smaller than 0.01 in the scale of 0~1). This problem leads to the following plots:

<center>
<img class="frame-level-plot" src="/assets/img/aed-by-cnn/frame-level/83502_0.png">
<img class="frame-level-plot" src="/assets/img/aed-by-cnn/frame-level/166942_0.png">
<img class="frame-level-plot" src="/assets/img/aed-by-cnn/frame-level/55018_0.png">
</center>

Similarly, the problem sometimes also occurs in other classes:

<center>
<img class="frame-level-plot" src="/assets/img/aed-by-cnn/frame-level/128607_4.png">
<img class="frame-level-plot" src="/assets/img/aed-by-cnn/frame-level/26184_5.png">
<img class="frame-level-plot" src="/assets/img/aed-by-cnn/frame-level/22973_3.png">
</center>

---

Even though we have done data augmentation on volume, the model is still relatively weak at detecting background sound. In the following file, we can hear two dogs barking, one in the foreground and the other in the background. The model detected only the sounds from foreground dog.

<img class="frame-level-plot" src="/assets/img/aed-by-cnn/frame-level/72261_3.png">
<audio controls>
  <source src="/assets/audio/aed-by-cnn/72261.wav" type="audio/wav">
  Your browser does not support the audio element.
</audio>

---

In some examples, we found *wrong annotations*. As in 77927.wav, we detected a large amount of street music, but the ground truth only labeled several small dog barks.

<img class="frame-level-all" style="width: 60%;" src="/assets/img/aed-by-cnn/frame-level/77927.png">
<audio controls>
  <source src="/assets/audio/aed-by-cnn/77927.mp3" type="audio/mp3">
  Your browser does not support the audio element.
</audio>

The same error appears in 106905.aif. While the ground truth is engine idling, we can still hear the siren and street music.

<img class="frame-level-all" style="width: 60%;" src="/assets/img/aed-by-cnn/frame-level/106905.png">
<audio controls>
  <source src="/assets/audio/aed-by-cnn/106905.mp3" type="audio/mp3">
  Your browser does not support the audio element.
</audio>
