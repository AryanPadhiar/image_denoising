# Image-Denoising
### Introduction 
Image denoising is used in image processing and computer vision, focused on enhancing image quality by eliminating noise. Noise can be introduced during image acquisition due to factors such as poor lighting conditions, sensor inaccuracies, or high ISO settings. In this project, I developed a model that transforms noisy images into denoised versions using a straightforward autoencoder architecture
### Dataset
I have made 2 iypnb files one trained on cifar-10 and other Brain MRI images.
the MRI images  shows huge improvement in PSNR due to many normalisations along with median filter.
My dataset is divided into two parts: training and testing. 

- Training Dataset :This consists of pairs of noisy (low-quality) images and their corresponding denoised (high-quality) images.
- Testing Dataset:This contains noisy images and their corresponding ground truth denoised images. 
### Preprocessing
- We resize the images as (32,32)
- then convert them into gray 'L'
- rescale the images to 255 
- and then reshape the images into (32,32,1)
### Model
- I have constructed my own architechure model.
- This contain two part first encoder and second decoder part.
<br>*Encoder*:</br>
- It consists two CNN operation and two max pooling operation
- First operation has 32 filter as size of (3,3) and second has 32 filter as size of (3,3)
- and in both cnn operation max pooling operation has kernel of size (2,2)
<br>*Decoder*:</br>
- Decoder part has two upsampling operation and one cnn operation 
- Both has kernel of size of (3,3) and 32 kernel
- last we have output cnn operation which has size (3,3) and one kernel
- We compile our model using adam optimization algorithm and binary cross entropy loss 
- We use split the train data into train and val and then perform early stopping concept
### Evaluation 
- We use our train model on test low images and then predict the denoised images then calculate their psnr value corresponding to ground denoised images present in test folder.
- mean psnr value I get for my test dataset is around 19.
