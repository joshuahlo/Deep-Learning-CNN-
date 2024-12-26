<h1>Deep Learning: Image Classification of Tomato Leaves</h1> <h2>Description</h2> Built deep learning models using Convolutional Neural Networks (CNNs) to classify tomato leaf images and determine their condition (e.g., healthy or diseased). Leveraged transfer learning with pre-trained VGG16 and ResNet18 architectures for performance comparison, achieving high accuracy while optimizing computational efficiency. The project also explored a custom CNN architecture to understand model design and hyperparameter tuning. <h2>Languages and Utilities Used</h2>
<b>Python</b>
<b>PyTorch</b>
<b>Kaggle API</b> (for dataset import)
<h2>Environments Used</h2>
<b>Google Colab GPU</b>
<h2>Program Walk-Through</h2>
<h3>1. Dataset Preparation:</h3>

- Imported a large tomato leaf image dataset using the Kaggle API to avoid local storage limitations.
- Cleaned the dataset by removing unnecessary folders and duplicates.


<h3>2. Data Preprocessing and Augmentation:</h3>

- Applied transformations such as RandomHorizontalFlip, RandomRotation, and normalization to enhance model generalization.
- Performed an 80-20 train-validation split for the dataset.

Example batch after transformations:
![batch ex](https://github.com/user-attachments/assets/fef9598a-f377-48ab-b5e1-d5b8edf29a14)

<h3>3. Model Development:</h3>

- Custom CNN:

  - Built a CNN architecture with convolutional layers, max pooling, dropout layers, and fully connected linear layers to classify the images.
 
Code of model:

<img width="598" alt="image" src="https://github.com/user-attachments/assets/239556d5-1d48-408f-8a82-43b9032ac908" />


  - Initial experiments with the model showed overfitting, prompting adjustments to hyperparameters and architecture.
  - Used cross-entropy loss to train the model for multi-class classification.
  - Fine-tuned hyperparameters such as learning rate, batch size, and number of epochs to improve validation performance and reduce overfitting.
  - Implemented advanced regularization techniques such as dropout, weight decay, and early stopping to reduce overfitting. 



Model Performance:

![image](https://github.com/user-attachments/assets/c3fc6ccb-7c59-4a0c-937b-f31ddd43354b)


Compared model's predictions with the actual classification in the testing set using a confusion matrix: 88% accuracy
![image](https://github.com/user-attachments/assets/b3876103-93f3-40bb-a037-3bba2685c8b1)


<h3>Transfer Learning</h3>

  - Implemented VGG16 and ResNet18, two pre-trained deep learning models, to leverage their feature extraction capabilities:
    - VGG16
        - Consists of 16 weight layers (13 convolutional layers and 3 fully connected layers).
        - Simple and can extract features well.
        - Efficiently captured spatial hierarchies in the tomato leaf images.
    - ResNet18
        - A 18-layer deep Residual Neural Network.
        - Leveraged residual connections to overcome vanishing gradient issues and achieve faster convergence.
  - Fine-tuned the pre-trained models on the tomato leaf dataset by:
    - Replacing the final fully connected layers with a custom layer for the classification task (10 classes).
    - Freezing the initial layers of the pre-trained models to retain general image features while allowing fine-tuning on tomato-specific data.
    - Compared the performance of these models to evaluate trade-offs between accuracy and computational efficiency.
    - Utimately used 400 epochs for final model, in the future could use more if no GPU limit.

Confusion matricies : 
<h4>VGG16: 89.5% accuracy </h4>

![image](https://github.com/user-attachments/assets/329e15c5-f7ee-4528-b8b0-ffcf506dcbf3)


<h4>ResNet18: 86% accuracy</h4>

<h3>4. Challenges Addressed:</h3>

![image](https://github.com/user-attachments/assets/f5cd561c-9115-47ce-bcd5-108ae8a2c475)

 - Initial validation loss trends suggested overfitting; modifications to the model architecture and data augmentation helped mitigate this.
 - Optimized training time as early runs took ~30 minutes for 30 epochs. Using ResNet18 reduced training time significantly due to its computational efficiency, however accuracy was lower.



<h2>Results</h2> 

   - Achieved high classification accuracy on the validation set with both custom and transfer learning models. 
   - Observed that the custom CNN model outperformed the ResNet18 model in accuracy and training speed, while VGG16 provided slightly higher accuracy but required more computation. 
   - Could run more epochs if more computational power, RAM, and no GPU limitations
   - Visualized training and validation performance to identify areas for improvement. 
  
<h2>Future Work</h2> 

   - Further optimize the custom CNN architecture for faster training and improved accuracy. 
   - Explore additional pre-trained models (e.g., EfficientNet) for transfer learning to enhance performance. 
   - Conduct experiments with a larger dataset to improve model generalizability.
