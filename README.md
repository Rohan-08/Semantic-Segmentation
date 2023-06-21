# Semantic-Segmentation
Implementation of Semantic Segmentation algorithm on CamSeq dataset

# Dataset
The dataset can be found here: https://www.kaggle.com/datasets/rohanchhabra/camseq01-semantic-segmentation
It consists of 101 images (960x720 pixel) in which each pixel was manually assigned to one of the following 32 object classes that are relevant in a driving environment:

![image](https://github.com/Rohan-08/Semantic-Segmentation/assets/25502096/ab1be687-8c36-4696-b39f-91f88f0d2e81)

The "void" label indicates an area which ambiguous or irrelevant in this context. The colour/class association is given in the file label_colors.txt. Each line has the R G B values (between 0 and 255) and then the class name.

I used various segmentation methods to perform semantic segmentation on the above dataset, such as DeepLabV3+, UNet and PSPNet and then compared their performance over each other. 

**DeepLabV3+:** DeepLabV3+ is one of the finest models used nowadays for image/instance./semantic segmentation. The model is an improvement to its predecessor (DeepLabV3) by adding another decoder layer at the end, which further refines the segmentation results. It is designed by the Google Tech team and is supposed to be used in cameras of their flagship phones. The architecture of the model first encodes the images it receives as input and then passes them to the ASPP layer. Atrous spatial pyramid pooling (ASPP) captures different resolutions of the image to better understand the spatial layout of the object. This is further passed to the decoder to the original resolution, which defines a feature map. The final layer is the classification layer which then segments each pixel into one class (usually done by Softmax function). 

**UNet:** It is also a type of convolutional neural network (CNN) commonly used for segmentation tasks. It consists of an encoder and a decoder. The encoder consists of several convolutional layers that try to decrease the spatial resolution of the input while increasing their depth. The decoder then consists of up-sampling layers which increases the spatial resolution while decreasing their depth. Additionally, it has also got a skip connection, which allows to propagate detailed information during back-propagation, which keeps details intact. 

**PSPNet** This is the third kind of model we have chosen for our dataset. Pyramid Scene Parsing Network (PSPNet) is again a CNN model primarily used for image segmentation. Its architecture is based on pyramid pooling scheme, which tries to capture different contextual information from the input images. It consists of several pooling layers, which extracts information at different scales. It is further passed to up-sampling and convolutional layers to generate final segmentation. Additionally, it consists of skip level connections between the encoder and the decoder, so that image details are kept intact during back-propagation, which further enhances the accuracy of predictions. 

Further, used SMP library (Segmentation models pytorch) to call these models and use it with pre-trained weights and backbones. The code covers in-depth methods of hyperparameter tuning using trial and error and getting the best results possible.

Evaluation was performed using Jaccard matrix or Intersection over Union method.
