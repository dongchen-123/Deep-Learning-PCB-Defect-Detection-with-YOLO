# Deep-Learning-PCB-Defect-Detection-with-YOLO


YOLO11s model is trained on PCB (printed circuit board) defect dataset from Peking University Open Lab on Human Robot Interaction: https://robotics.pkusz.edu.cn/resources/datasetENG/

pcb_defect_data.ipynb:
1. Label preprocessing - parses XML files for annotations, converts bounding boxes to YOLO format, creates yaml file for YOLO
2. Image preprocessing - resize to an uniform size of 640 x 640
3. Dataset preparation - split into train, validation, and test datasets

The results are YOLO_dataset (includes train and val) and YOLO_test_dataset. As my Intel ARC GPU is not quite suitable for training YOLO models, I zipped the datasets and uploaded them onto Google Colab for training using NVIDIA Tesla T4 GPU.

Example detection image:


<img width="640" height="640" alt="image" src="https://github.com/user-attachments/assets/69907352-18ee-43b5-a92d-0ad47ebea135" />


After training, the model can detect and classify defects on a PCB, giving its relative confidence in each prediction, as seen above.


Performance metrics analysis: 

Confusion Matrix:


<img width="3000" height="2250" alt="image" src="https://github.com/user-attachments/assets/2acf5d3e-1c93-4077-9e4d-ace504827e2f" />



Normalized Confusion Matrix:



<img width="3000" height="2250" alt="image" src="https://github.com/user-attachments/assets/dd2bf740-3360-4a6f-b1cf-ff1f58e36c4d" />


The diagonal line represents the percentages of correct predictions for each class. As all values here are above 0.90, my model has good recall values across all classes. Recall is an important metric in this case, as one objective of the model would be to detect all defects; the cost of false negatives (faulty PCBs not being detected) is relatively high.

