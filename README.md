## Models

### Model1
a. Preprocessing
- prioritize all good images such as diagnostic, characteristic, potentially, and other into training dataset based on qc column in the datatset
- Split train and validation dataset by skin colors and skin disease. The inution behind this is ro ensure we don't have all white skin color in training dataset and only have black skin color in validation dataset
- Apply efficient preprocess inpunt function and data gumentation to training and validation dataset

b. Model Structure
- use EfficentNetB2 with weights = imagenet
- apply one Dense layer with 256 neurons, BatchNormlization layer, DropOut layer
- loss function = Categorical Focal Cross Entropy, Optimizer Adam and the learning rate = 0.0003
- Unfreeze all layers to fine tune the model for 20 epochs
- The overall accuracy is 58%

### Model2
a. Preprocessing
- It is the same as model1

b. Model Structure
- I changed optimzier to adamW because adamW can help model to generalize data better than adam, according to what keras documentation says
- One additional feature I added was that the loss learning rate scheduler, that can help us to reduce learning rate based on loss values in previous n epochs
- Anything else reamined the same
-  Unfreeze all layers to fine tune the model for 20 epochs
- The overall accuracy is 58.9%

### Model3
a. Preprocessing
- I choose to oversample data by label as a target variable in the oversampling function
- I balance the dataset by generating fake images

b. Model Structure
- The model structure is the same as the model2
- Unfreeze all layers to fine tune the model for 10 epochs
- The overall accuracy is 54%

### Model4
a. Preprocessing
- I choose to oversample data by a combination of skin color and label as a target variable in the oversampling function
- Initially, I have 21 labels. After I combine the label with skin color, I get 34 labels
- This new smapling idea can help me generate more fake data

b. Model Structure
- The model structure is the same as the model2
- Unfreeze all layers to fine tune the model for 10 epochs
- The overall accuracy is 55%

### Model5
a. Preprocessing
- I choose to oversample data by a combination of skin color and label as a target variable in the oversampling function
- Initially, I have 21 labels. After I combine the label with skin color, I get 34 labels
- This new smapling idea can help me generate more fake data

b. Model Structure
- Since the preprocessing steps in model4 and model5 cannot build a better model, I decided to use the oversampled data to fine tune my model2
- Unfreeze all layers to fine tune the model for 7 epochs
- The overall accuracy is 61%

### Model6
a. Preprocessing
- I choose to oversample data by a combination of skin color and label as a target variable in the oversampling function
- Initially, I have 21 labels. After I combine the label with skin color, I get 34 labels
- This new smapling idea can help me generate more fake data

b. Model Structure
- Model6 is gonna do the same thing as model5, but I am using data oversampled bya combination of skin color and label as a target variable in the oversampling function
- I am goona use the fine-tuned model2 from model5
- Unfreeze all layers to fine tune the model and decrease learning to 0.0001 from 0.0003 for 5 epochs
- Unfreeze all layers to fine tune the model and decrease learning to 0.00005 from 0.0001 for 5 epochs
- The overall accuracy is 64%

### Model7
a. Preprocessing
- The preprocessing step is a bit different from model6. I decided to throw all data into training and wanted model to learn more from minority classes.
- I still did a little bit train test split 0.05. This just ensure I can set a smaller learning rate to my model6 by adpative learning rate function.
- I oversampled the image data by only label

b. Model Structure
- Model7 is the same as model6.
- I changed learning rate from 0.00005 to 3.4299999356335316e-07. 3.4299999356335316e-07 was achieved by many experiments.
- I trained the model by 20 epochs and achieved a 66.9% accuracy.





