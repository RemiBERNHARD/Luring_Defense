# Luring of transferable adversarial perturbations in the black-box paradigm

This repository contains pretrained models and python scripts to reproduce the results presented in the article "Luring of transferable adversarial perturbations in the black-box paradigm".

## Environment and libraries

The python scripts were executed in the following environment:

* OS: CentOS Linux 7
* GPU: NVIDIA GeForce GTX 1080 
* Cuda version: 9.0.176
* Python version: 2.7.5

The following version of some Python packages are necessary: 

* Tensorflow: 1.12.0
* Cleverhans: 3.0.1
* Keras: 2.2.4
* Numpy: 1.16.12


## Files

In order to get the SVHN data set (to have the same training, validation and testing tests, as well as to run attacks), and all pretrained models, download the "models", "models_p" and "SVHN_data" folders from https://drive.google.com/open?id=167Xo9DNRUCdVtv3bsJdo7kFuLPa1EQrl and place them in the same directory as all other files.


### Model files
    
The "models" repository contains the pretrained models for the datasets MNIST, SVHN and CIFAR10. As an example, on MNIST:    

* models/MNIST_float.h5 is the base classifier.
* models/MNIST_stacked.h5 is the model corresponding to the Stacked architecture.
* models/MNIST_auto.h5 is the model corresponding to the Auto architecture.
* models/MNIST_ce.h5 is the model corresponding to the C_E architecture.
* models/MNIST_luring.h5 is the model corresponding to the Luring architecture.

The "models_p" repository contains the components prepended to the base classifier for the datasets MNIST, SVHN and CIFAR10. As
an example, on MNIST:

* models_p/MNIST_auto_p.h5 is the auto encoder corresponding ot the Auto architecture.
* models_p/MNIST_ce_p.h5 is the preprended component corresponding ot the C_E architecture.
* models_p/MNIST_luring_p.h5 is the preprended component corresponding to the Luring architecture.


### Training files
        
Although pretrained models are provided, some python files allow to train and save your own models (in order for models to be saved, you need to have a "models" folder and a "models_p" folder in the same directory as the training files), 
for the MNIST, SVHN and CIFAR10 datasets. As an example, on MNIST:

    # Train the base classifier
    python train_mnist.py float 
    # Train the Stacked model
    python train_mnist.py stacked
    # Train the Auto model
    python train_mnist.py auto
    # Train the C_E model
    python train_mnist.py ce
    # Train the Luring model
    python train_mnist.py luring

### Evaluation under attack

#### Characterization of the *luring* effect

As an example, for a perturbation of ```epsilon=0.06``` (pixel values have been scaled between 0 and 1) on SVHN, the following command allows
to get the values to reproduce the figures of the part "Characterizaton of the *luring* effect":

    python verification_svhn.py 0.06

#### Using the luring effect as a defense

As an example, for a perturbation of ```epsilon=0.03``` (pixel values have been scaled between 0 and 1) on CIFAR10, the following command allows
to get the values to reproduce the tables "Using the luring effect as a defense" for the Luring approach:

    python attack_cifar10.py 0.03 luring

        
        
        
        
        
        
        
        
        
        
        
        
