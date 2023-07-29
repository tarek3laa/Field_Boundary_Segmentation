# Crop Field Boundary Segmentation

## Problem Description

The aim of this competition was to predict field boundaries in satellite imagery using a time series of satellite imagery from Planet’s NICFI basemaps and labels for field boundaries that were annotated on the same imagery source. The labels were digitized over Planet Basemaps for the months of March, April (on season) and August (off season) of 2021 and an additional 3 months of imagery (October, November, and December) were provided for the time series data to match with corresponding field boundary labels. The dataset was split into training and test sets, with the training set containing 57 chips and the test set containing 13 chips. The labels were created only for fields large enough to be distinguished on the planet basemaps and for fields completely contained in the chip.

## Solution Overview

To tackle this problem, I used a U-Net model with a custom architecture, which takes as input the first three channels of the satellite imagery (RGB) and outputs the predicted field boundaries. I preprocessed the data by standardizing the images and applying contrast stretching. Additionally, I used data augmentation techniques such as flipping, rotating, and zooming to increase the size of the training set. I also used the soft dice loss function to train the model.

## Model Architecture

My custom U-Net architecture consists of an encoder and a decoder. The encoder consists of custom convolutional layers and group normalization, which normalize the weights and activations of the convolutional filters, respectively. The decoder consists of upsampling and convolutional layers. I experimented with using a pre-trained ResNet50 backbone for the encoder, but ultimately found that the custom architecture performed better.

## Training Details

I trained the model on Google Colab with a batch size of 4 and a learning rate of 0.1 times the batch size divided by 32. The model was trained using the Adam optimizer for 30 epochs.

## Results

My model achieved good results and I was ranked in the top 20% . The final model was trained on a GPU for 30 epochs with a batch size of 4 and a learning rate of 0.025. The soft dice loss function was used as the training loss, with the Adam optimizer.
