# Object Detection in Flood Damage
## 🔹 Overview of the Problem
Floods cause more than [$40 billion](https://www.nationalgeographic.com/environment/article/floods) in damage worldwide annually. The severity of these damages is often compounded by ineffective post-event assessments and poorly coordinated rescue missions. Timely and accurate identification of people, vehicles, and buildings affected by floods is crucial for saving lives and minimizing property loss. <br/>
To address this, I developed an object detection model that identifies people, flooded cars, and flooded buildings from aerial or ground images of flood-affected areas. This model supports faster post-flood assessments and better-informed rescue operations. <br/>
This project supports: <br/>
- SDG 11: Sustainable Cities and Communities
- SDG 3: Good Health and Well-being
- SDG 13: Climate Action

## 🔹 Data Used
The dataset was sourced from [Roboflow](https://universe.roboflow.com/columbia-university-d9ggz/flood-object-detection-2olqp/dataset/1) and contained labeled images across four classes: flooded_building, flooded_car, person, and person_in_help. The data structure included: <br/>
- Roboflow.txt – Dataset overview.
- Dataset.txt – Dataset description and download link.
- Data.yaml – Configuration file for YOLO training.
- Train/ – Training images and labels.
- Valid/ – Validation set.
- Test/ – Testing set.

## 🔹 Methodology
### 1. Data Preprocessing
- Uploaded dataset to Kaggle Notebook.
- Verified YOLOv8 compatibility with class labels.
- Inspected label files to confirm structure.
- Merged person_in_help (class 3) into person (class 2) due to low representation and class similarity.
- Confirmed modifications in label annotations.

### 2. Exploratory Data Analysis (EDA)
Visualized 3 sample images per folder (Train, Valid, Test) to assess class representation and labeling accuracy. <br/>

![download](https://github.com/user-attachments/assets/3fbf72e7-3de2-4a21-aed5-031ab488600e)
![download](https://github.com/user-attachments/assets/fbf2d922-03f1-4f38-bacb-5a92a7b9a232)
![download](https://github.com/user-attachments/assets/2ad8eb1c-77cd-4af8-8bc4-6562a2b8d26a)

### 3. Model Training
- Framework: PyTorch
- Model: YOLOv8m
- Training Epochs: 10,000 (Early Stopping at Epoch 248)
- Configuration: Custom my_data.yaml file

## 🔹 Model Summary:

![Screenshot (126)](https://github.com/user-attachments/assets/d7a808f2-8a77-4cdd-b240-19c754779a74)

- 169 layers
- 25,858,057 parameters
- 25,858,041 gradients
- 79.1 GFLOPs

## 🔹 Model Performance
| Metric         | Value   |
|:---------------|:-------:|
| mAP@50         | 0.3564  |
| mAP@50-95      | 0.1370  |
| Mean Precision | 0.5005  |
| Mean Recall    | 0.3919  |

#### - Class-Wise Metrics:
| Class            | Precision | Recall  | AP@50   | AP@50-95 |
|:-----------------|:---------:|:-------:|:-------:|:--------:|
| Flooded Building |  0.3619   | 0.3333  | 0.2661  |  0.1048  |
| Flooded Car      |  0.5959   | 0.4625  | 0.4547  |  0.1836  |
| Person           |  0.5438   | 0.3800  | 0.3484  |  0.1227  |

#### - Confusion Matrix was Calculated and Displayed

![download](https://github.com/user-attachments/assets/1fd2207a-7273-451e-bc6d-3c79a3b417c1)

#### - Ran prediction on test images

![download](https://github.com/user-attachments/assets/e7848d11-8129-4783-ad3f-89b3fc022952)
![download](https://github.com/user-attachments/assets/b1a8df04-c5a3-443d-8fac-7231bae8fe7f)
![download](https://github.com/user-attachments/assets/457b65a3-f20a-42bb-88d6-1db4c2c8fef4)

## 🔹 Model Limitations
Despite stable training losses and robust architecture, the model's performance shows variability due to class imbalance, particularly the underrepresentation of flooded_building instances in the dataset. This skewed distribution led to uneven learning, where the model consistently favored more frequent classes, resulting in suboptimal recall and lower average precision across minority classes—even with augmentation strategies applied.

## 🔹 Business Use Cases
This object detection system can assist: <br/>
- Disaster Response Agencies: Automatically identify people and affected infrastructure to guide rescue operations.
- Insurance Companies: Automate damage assessment from drone images for faster claims processing.
- Urban Planners: Evaluate risk-prone zones for better city planning and response mechanisms.
- NGOs & Humanitarian Organizations: Target resource allocation effectively during crises.
- Supports SDG 9: Industry, Innovation and Infrastructure
- Aligns with SDG 8: Decent Work and Economic Growth by reducing the burden and risk on human assessors and emergency teams.

## 🔹 Impact
- By enabling real-time identification of critical elements in flood scenarios, this solution improves:
- Speed and efficiency of rescue operations
- Accuracy of damage assessment
- Allocation of emergency resources
- Long-term planning and mitigation strategies
- Contributes to SDG 1: No Poverty and SDG 2: Zero Hunger by protecting livelihoods and access to essentials in post-flood recovery.

================================================= <br/>
Abdullahi Olalekan Abdulmumeen <br/>
Applied Data Scientist <br/>
olalekanabdulmumeen3@gmail.com <br/>
+234 705 305 3024
