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



