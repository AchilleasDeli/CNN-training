# CNN-training
This repository contains a Convolutional Neural Network (CNN) model trained on the Fashion-MNIST dataset using TensorFlow/Keras. The model's architecture includes multiple convolutional layers, max-pooling, dropout, and dense layers to classify fashion items into 10 categories.

Fashion-MNIST CNN Classifier
This repository contains a Convolutional Neural Network (CNN) model trained on the Fashion-MNIST dataset using TensorFlow/Keras. The model is designed to classify grayscale images of clothing items into one of 10 categories.

Key Features
Trains a deep learning model using convolutional and max-pooling layers.
Evaluates training accuracy, validation accuracy, and loss across 5, 10, and 20 epochs.
Experiments with an additional convolutional + pooling layer to analyze its impact on performance.
Implements regularization techniques such as Dropout, L2 regularization, Early Stopping, and Data Augmentation to improve generalization.
Classes in Fashion-MNIST Dataset
Label	Class Name
0	T-shirt/top
1	Trouser
2	Pullover
3	Dress
4	Coat
5	Sandal
6	Shirt
7	Sneaker
8	Bag
9	Ankle boot
Added Layers and Their Functions
A new Convolutional + Max-Pooling layer was added before flattening to extract deeper hierarchical features from the images.

Original Architecture:
Conv2D (32 filters, 5x5, ReLU) – Detects low-level features like edges and textures.
MaxPooling2D (2x2) – Reduces spatial dimensions, making computation more efficient.
Conv2D (64 filters, 5x5, ReLU) – Extracts more complex patterns like curves and shapes.
MaxPooling2D (2x2) – Further reduces dimensions while retaining important features.
Flatten → Dense(1024, ReLU) → Dropout(0.2) → Dense(10, Softmax)
Modified Architecture (Extra Layer Added):
Conv2D (128 filters, 3x3, ReLU) [NEW] – Extracts finer details and hierarchical representations.
MaxPooling2D (2x2) [NEW] – Prevents loss of spatial information while reducing feature map size.
Flatten → Dense(1024, ReLU) → Dropout(0.2) → Dense(10, Softmax)
This was added before the Flatten layer to allow the model to learn deeper representations before classification.
Results
Original Model (Before Extra Layer)
Epochs	Training Accuracy	Validation Accuracy	Validation Loss
5	92.96%	91.14%	0.2558
10	97.68%	91.39%	0.4074
20	98.90%	91.14%	0.8807
New Model (With Extra Layer)
Epochs	Training Accuracy	Validation Accuracy	Validation Loss
20	96.73%	90.55%	0.5117
Analysis of Results
Validation Accuracy did not improve with the extra layer.

The best test accuracy (91.14%) was achieved with the original model.
With the extra layer, accuracy slightly decreased to 90.55%.
Validation Loss increased in both cases.

This shows that overfitting occurred after 10 epochs.
Even with the additional layer, the model did not generalize better.
Training Accuracy was lower in the new model.

The extra layer slowed down learning slightly, but it did not prevent overfitting.
Conclusion
Adding the extra layer did not improve generalization. Instead of increasing model complexity, regularization techniques are needed.

Next Steps to Improve Generalization
Use Early Stopping – Stop training when validation loss stops improving.
Increase Dropout (0.4 instead of 0.2) – Reduces dependency on specific neurons.
Apply L2 Regularization – Penalizes large weights to prevent overfitting.
Use Data Augmentation – Introduces variations in the dataset to improve robustness.
Final Thoughts
This experiment highlights that increasing model depth does not always improve performance. Instead, proper regularization is more effective for reducing overfitting and improving test accuracy.
