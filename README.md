**Fruit Shelf-Life Detection (Computer Vision)**


A deep learning pipeline that classifies fruit images as unripe, ripe, or rotten, built as group coursework for MSc Data Science at Bournemouth University (with Ifeoluwa Oguntimehin).



**Overview**

Fruit quality control in agriculture and food processing relies heavily on manual inspection. This project explores whether a computer vision model can automatically classify the shelf-life stage of five fruit types (apple, banana, mango, avocado, strawberry) across three freshness categories (unripe, ripe, rotten), from a single image.



**Method**

Data collection

•	Built a custom image dataset by scraping fruit images from Bing across all 15 fruit/category combinations

•	Filtered scraped images against Python-supported image formats to remove corrupt/unsupported files

•	Supplemented with manually captured and Pixabay-sourced test images for independent evaluation



**Preprocessing**

•	Computed dataset mean/std for normalisation

•	Resized images to 150x150 (custom CNN) and 224x224 (pretrained models, matching ImageNet input size)

•	Applied data augmentation via torchvision.transforms



**Modelling Trained and compared five architectures**:

•	A custom CNN built from scratch

•	ResNet18, ResNet34, ResNet50 (trained from scratch)

•	MobileNetV2 (trained from scratch)

•	The same four architectures again via transfer learning, fine-tuning ImageNet-pretrained weights




**Evaluation**

•	Accuracy, precision, recall, and F1-score via classification reports

•	Confusion matrices per model

•	Manual inspection of misclassified test images to understand failure modes



**Results**

Model	Test Accuracy

ResNet18 (Transfer Learning)	0.775

ResNet34 (Transfer Learning)	0.680

ResNet50 (Transfer Learning)	0.635

MobileNetV2 (Transfer Learning)	0.517

ResNet18 with transfer learning performed best, suggesting its capacity struck the right balance for a relatively small, custom-scraped dataset. Models were trained from scratch on the same data, with transfer learning outperforming scratch training.



**Key Learnings & Limitations**

•	Dataset size was a major constraint: hand-scraped and manually captured images limited both training volume and real-world variability

•	MobileNetV2's lower accuracy likely reflects its efficiency-first design trading off representational capacity

•	Reported accuracy alone doesn't fully capture model quality; precision/recall/F1 and confusion matrix analysis were used to cross-check performance


**Tech Stack**

Python · PyTorch · torchvision · OpenCV · BeautifulSoup (image scraping) · scikit-learn (metrics) · matplotlib / seaborn


**Files**

•	Fruit_Shelf_Life_Detection.ipynb — full pipeline: scraping, preprocessing, model training, evaluation


**Future Work**

•	Expand and diversify the training dataset (more images, more lighting/angle variation)

•	Hyperparameter tuning (learning rate, batch size, epochs) via grid/random search
•	Ensemble methods combining multiple architectures
•	Deployment considerations for edge devices (Raspberry Pi, IoT, mobile)

