# rgb-to-hyperspectral images for skin cancer classification

#abstract
 This work presents a comprehensive approach to enhancing skin cancer diagnosis using hyper
spectral imaging (HSI) generated from RGB images through the fine-tuning of MST++ (Multi
Stage Spectral Transformer++), a state-of-the-art deep learning model originally developed for
 HSI reconstruction. MST++ combines spectral self-attention with convolutional operations in a
 multi-stage encoder-decoder architecture, effectively capturing both spectral and spatial dependen
cies. While the model was initially trained on natural scene data (CAVE dataset), it was fully
 f
 ine-tuned—without freezing any layers—on a domain-specific dataset consisting of 290 hyper
spectral image cubes derived from skin lesion samples. To match the model’s 31-band output
 format, the original 16-band HSI data were upsampled, and synthetic RGB images were gener
ated by averaging selected spectral bands. Fine-tuning was conducted using the Mean Squared
 Error (MSE) loss function and the Adam optimizer. The updated model was then employed
 to reconstruct 31-band hyperspectral images from 2239 RGB inputs spanning nine skin cancer
 classes. These reconstructed images were subsequently used in classification experiments, with
 an emphasis on identifying discriminative spectral bands. Performance metrics such as accu
racy, precision, recall, F1-score, and statistical significance (p-values) validated the utility of the
 approach. The fully fine-tuned MST++ model enabled high-fidelity hyperspectral reconstruction
 and meaningful spectral analysis, contributing to more accurate and interpretable skin cancer
 classification.

 ## 🎯 Comparison: Without vs. With Fine-Tuning

<p float="left">
  <img src="0%20figures/Screenshot%202025-05-06%20205355.png" width="45%" />
  <img src="0%20figures/Screenshot%202025-05-06%20205215.png" width="45%" />
</p>

<p align="center">
  <b>Left:</b> Without Fine-Tuning &nbsp;&nbsp;&nbsp;&nbsp; <b>Right:</b> With Fine-Tuning
</p>


RGB to Hyperspectral Imaging for Skin Cancer Classification
Welcome to the RGB to Hyperspectral Imaging for Skin Cancer Classification project! This repository presents a novel approach to enhance skin cancer detection by converting RGB images to hyperspectral images (HSI) and leveraging advanced machine learning models for classification. Our work achieves state-of-the-art performance by combining fine-tuned hyperspectral conversion models with robust classifiers, focusing on melanoma detection using the HSIDermoscopy dataset.

Project Overview
This project aims to improve skin cancer classification, specifically melanoma detection, by transforming standard RGB dermoscopy images into hyperspectral images (31 bands) and applying machine learning classifiers. We evaluated four hyperspectral conversion models (MST++, AWAN, HRNet, HSCNN+) and four classifiers (2D-CNN, 3D-CNN, SVM, RF). After extensive experimentation, the fine-tuned MST++ model paired with a 2D-CNN classifier achieved the best performance, with detailed metrics on accuracy, p-value, F1 score, and optimal wavelength identification.
Key Contributions

RGB to HSI Conversion: Converted RGB images (3 bands) to hyperspectral images (31 bands) using four models, with MST++ fine-tuned on real HSI datacubes for enhanced accuracy.
Classification: Evaluated four classifiers, identifying 2D-CNN as the most effective for skin cancer classification.
Wavelength Analysis: Identified the best wavelengths for classification, providing insights into spectral features critical for melanoma detection.
Comprehensive Evaluation: Reported accuracy, p-value, and F1 score for robust performance assessment.

![rgb skin cancer table](0%20figures/Screenshot%202025-05-14%20000018.png)

Methodology

Dataset: Utilized the HSIDermoscopy dataset for fine-tuning and evaluation.
RGB to HSI Conversion:
Four models (MST++, AWAN, HRNet, HSCNN+) were used to convert RGB images to 31-band HSI.
MST++ was fine-tuned using real HSI datacubes from the HSIDermoscopy dataset to improve conversion accuracy.


Classification:
Four classifiers (2D-CNN, 3D-CNN, SVM, RF) were applied to the generated HSI data.
2D-CNN outperformed others, achieving the highest accuracy and F1 score.


Wavelength Analysis:
Analyzed the spectral bands to identify the most informative wavelengths for classification.
Visualized results in ![Figure Description](0%20figures/Screenshot%202025-04-11%20010432.png)




Fine-Tuning and Final Pipeline:
Fine-tuned MST++ with HSIDermoscopy datacubes.
Used the fine-tuned MST++ to convert RGB to HSI, followed by 2D-CNN for classification.




Results

Model Performance: 
![classification table](0%20figures/Screenshot%202025-05-14%20083131.png)




Dataset
This project uses the HSIDermoscopy dataset for fine-tuning and evaluation. The dataset is described in:
Citation:

Yanyang Gu, Yi-Ping Partridge, Jun Zhou. "A Hyperspectral Dermoscopy Dataset for Melanoma Detection." In OR 2.0 Context-Aware Operating Theaters, Computer Assisted Robotic Endoscopy, Clinical Image-Based Procedures, and Skin Image Analysis, pp. 268–276, Springer International Publishing, Cham, 2018.

BibTeX:
@InProceedings{Yanyng2018HSIData,
  author="Gu, Yanyang and Partridge, Yi-Ping and Zhou, Jun",
  title="A Hyperspectral Dermoscopy Dataset for Melanoma Detection",
  booktitle="OR 2.0 Context-Aware Operating Theaters, Computer Assisted Robotic Endoscopy, Clinical Image-Based Procedures, and Skin Image Analysis",
  year="2018",
  publisher="Springer International Publishing",
  address="Cham",
  pages="268--276",
}

Download Links:

Original Images: Google Drive or Dropbox
Data Cube (Corrected): Google Drive

We used the corrected HSI datacubes for fine-tuning the MST++ model and evaluating classification performance. Please cite the above paper if you use this dataset in your work.
Models
The project adapts four models (MST++, AWAN, HRNet, HSCNN+) originally developed by [Yuanhao Cai and Jing Lin and Zudi Lin and Haoqian Wang and Yulun Zhang and Hanspeter Pfister and Radu Timofte and Luc Van Gool},
  booktitle] . These models were fine-tuned using the HSIDermoscopy dataset to enhance RGB to HSI conversion for skin cancer classification.
Citation for Models:
# MST++

![mst++ architecture](0%20figures/Screenshot%202025-05-06%20141929.png)
@inproceedings{mst_pp,
  title={MST++: Multi-stage Spectral-wise Transformer for Efficient Spectral Reconstruction},
  author={Yuanhao Cai and Jing Lin and Zudi Lin and Haoqian Wang and Yulun Zhang and Hanspeter Pfister and Radu Timofte and Luc Van Gool},
  booktitle={CVPRW},
  year={2022}
}



Download the HSIDermoscopy dataset from the provided links and place it in the data/ folder.
Run the main script:python main.py



Usage

Preprocessing: Convert RGB images to HSI using the fine-tuned MST++ model (scripts/convert_rgb_to_hsi.py).
Classification: Use the 2D-CNN classifier (scripts/classify_hsi.py) to predict melanoma classes.
Wavelength Analysis: Run scripts/wavelength_analysis.py to identify key wavelengths.
Visualization: Generate plots using scripts/visualize_results.py. Results are saved in the figures/ folder.

Folder Structure

├── data/                 
├── figures/              
├── codes/              
├── models/               
├── README.md         
├── requirements.txt     

License
This project is licensed under the MIT License. See below for details.
MIT License
Copyright (c) 2022 Yuanhao Cai
Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:
The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.
THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
Contributing



Contributions are welcome! Please open an issue or submit a pull request with your improvements.
Contact
For questions or collaboration, contact Yuanhao Cai.

This project is a step toward advancing skin cancer detection using hyperspectral imaging. Star this repo if you find it useful!

## 🙋‍♂️ Author

**Nateesh Kumar**  
[GitHub Profile](https://github.com/Nateesh-Kumar) | [LinkedIn](http://www.linkedin.com/in/ninaniya-nateesh-kumar-8841b62a4)  
