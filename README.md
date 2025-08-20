# Deep-Learning-PCB-Defect-Detection-with-YOLO


YOLO11s model is trained on PCB (printed circuit board) defect dataset: https://robotics.pkusz.edu.cn/resources/datasetENG/

pcb_defect_data.ipynb:
1. Label preprocessing - parses XML files for annotations, converts bounding boxes to YOLO format, creates yaml file for YOLO
2. Image preprocessing - resize to uniform size of 640 x 640
3. Dataset preparation - split into train, validation, and test datasets

The results are YOLO_dataset (includes train and val) and YOLO_test_dataset. As my Intel ARC GPU is not quite suitable for training YOLO models, I zipped the datasets and uploaded them onto Google Colab for training using NVIDIA Tesla T4 GPU.

Example detection image:
<img width="640" height="640" alt="image" src="https://github.com/user-attachments/assets/69907352-18ee-43b5-a92d-0ad47ebea135" />
After training, the model can detect and classify defects on a PCB, giving its relative confidence in each prediction, as seen above.
