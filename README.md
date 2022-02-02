# Stanford_Dog_Breed_Identification
Created and optimised a Breed Image Classification model using Stanford Dog Breed Dataset, 

In this project, I tried to create a Dog Breed Identification Model by using Keras Framework and Standford Dog Breed Dataset.

There are 20580 images of 120 different dog breeds.
The characteristics of Standford Dog Breed Dataset are:
+ There exist dog breeds which are hard to distinguish by human level without any advanced knowledge.
+ Not only dog, but also human and other objects may exist in the image.
+ Dog may not locate in the middle of the image

<img width="1381" alt="스크린샷 2022-02-03 오전 2 08 09" src="https://user-images.githubusercontent.com/52812351/152202324-cabc14f5-f918-4443-a456-a6397748dba5.png">
<img width="222" alt="스크린샷 2022-02-03 오전 2 08 29" src="https://user-images.githubusercontent.com/52812351/152202366-df2be231-2fb7-401a-a1aa-ee1d8841c021.png">
<img width="209" alt="스크린샷 2022-02-03 오전 2 08 40" src="https://user-images.githubusercontent.com/52812351/152202390-6291f46e-e70a-4732-a52a-15dd8f02f69c.png">

Therefore, an appropriate use and selection of augmentation methods were required.

When splitting the dataset into train, valid, and test dataset, I used 'stratify' factor to maintain the original distribution (# of dogs in each breed).
<img width="984" alt="스크린샷 2022-02-03 오전 2 13 32" src="https://user-images.githubusercontent.com/52812351/152203246-f4206c9f-d3f6-4b46-9ef6-2776cd96c938.png">

In [dog-breed-aug-lr-ft.ipynb] file, I only Early Stopping, Reduce lr on Plateau callbacks and Horizontal Flip augmentation with pretrained Xception, EfficientNetB0 model to briefly investigate a room for improvement.

<img width="759" alt="스크린샷 2022-02-03 오전 2 21 10" src="https://user-images.githubusercontent.com/52812351/152204498-1d4495c2-927c-4290-882d-9e5700c01a38.png">
It was shown that our model failed to inference particular dog breeds and as we can see from the image at the bottom, it doesn't look easy to clearly distinguish the difference between two particular breeds.
<img width="1262" alt="스크린샷 2022-02-03 오전 2 23 47" src="https://user-images.githubusercontent.com/52812351/152204951-e7ca7c00-ef8e-41f9-bf92-2a51b65355ac.png">


Hence in [dog-breed-aug-lr-ft.ipynb] file, I tried to promote the test data accuracy(about 80% in the previous file) by adopting different augmentation options, learning rate scheduler, and fine-tuning method.

I used combinations of some light augmentations and heavy augmentations, Ramp up and Step Decay learning rate scheduler, and fine-tuning with pretrained EfficientNetB0 and B1. 
<img width="751" alt="스크린샷 2022-02-03 오전 2 32 35" src="https://user-images.githubusercontent.com/52812351/152206423-e4d08b53-884c-4761-b9cc-9de7d5f22cd8.png">
The test data accuracy was raised from about 80% to 84.7%.
However, the changes made in [dog-breed-aug-lr-ft.ipynb] file was not enough to hide the lack of distinguishability in similar dog breeds. Hence, in further project, I would like to study a method that may help distinguishing two particular object classes.
