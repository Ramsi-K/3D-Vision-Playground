# Luna-Net3D (Archived)

> This project has been moved to a private repository. If you are a recruiter or collaborator and would like access, please feel free to reach out. Thank you for understanding!

**Project Overview:** [Summary of project goals, accomplishments, and progress here]

LunaNet3D is a deep learning project focused on lung nodule detection using 3D Convolutional Neural Networks (3D CNNs) trained on the Luna16 dataset. This project aims to leverage the capabilities of 3D CNNs to enhance the accuracy and efficiency of lung cancer detection from CT scans.

## Table of Contents

- [Introduction](#introduction)
- [Dataset](#dataset)
- [Model Architecture](#model-architecture)
- [Results](#results)
- [Contributing](#contributing)


## Introduction

Early detection of lung cancer is crucial for effective treatment and improved survival rates. Luna-Net3D utilizes advanced deep learning techniques to analyze CT scan images and identify potential lung nodules. By employing 3D CNNs, the model captures spatial information more effectively, leading to better performance in nodule detection.

## Dataset

The Luna16 dataset is used for training and evaluating the model. The dataset consists of labeled CT scans with annotations for lung nodules. More information about the dataset can be found [here](https://luna16.grand-challenge.org/). 

Dataset: [part 1](https://zenodo.org/record/3723295) and [part 2](https://zenodo.org/records/4121926)

### Structure

- **seg-lungs-Luna16:** zip file which contain a sample of all CT images
- **annotations.csv:** csv file that contains the annotations used as reference standard for the 'nodule detection' track
- **sampleSubmission.csv:** an example of a submission file in the correct format
- **candidates.csv:** the original set of candidates used for the LUNA16 workshop at ISBI2016. This file is kept for completeness, but should not be used, use candidates_V2.csv instead.
- **candidates_V2.csv:** csv file that contains an extended set of candidate locations for the ‘false positive reduction’ track.
- **evaluation script:** the evaluation script that is used in the LUNA16 framework
- **lung segmentation:** a directory that contains the lung segmentation for CT images computed using automatic algorithms
- **additional_annotations.csv:** csv file that contain additional nodule annotations from our observer study.

### Images

The complete dataset is divided into 10 subsets that should be used for the 10-fold cross-validation. All subsets are available as compressed zip files.

In each subset, CT images are stored in MetaImage (mhd/raw) format. Each .mhd file is stored with a separate .raw binary file for the pixeldata.

### Annotations

The annotation file is a csv file that contains one finding per line. Each line holds the SeriesInstanceUID of the scan, the x, y, and z position of each finding in world coordinates; and the corresponding diameter in mm. The annotation file contains 1186 nodules.

### Candidates

The candidates file is a csv file that contains nodule candidate per line. Each line holds the scan name, the x, y, and z position of each candidate in world coordinates, and the corresponding class.

The candidate locations are computed using three existing candidate detection algorithms. As lesions can be detected by multiple candidates, those that are located <= 5 mm are merged. Using this method, 1120 out of 1186 nodules are detected with 551,065 candidates. For convenience, the corresponding class label (0 for non-nodule and 1 for nodule) for each candidate is provided in the list. It has to be noted that there can be multiple candidates per nodule.

After ISBI 2016, a new set of candidates was released, candidates_V2.csv, for the false positive reduction track. This updated set is obtained by merging the previous candidates with the ones from the full CAD systems etrocad (jefvdmb2) and M5LCADThreshold0.3 (atraverso). The new combined set achieves a substantially higher detection sensitivity (1,166/1,186 nodules), offering the participants in the false positive reduction track the possibility to further improve the overall performance of their submissions.

### Lung segmentation

To aid the development of the nodule detection algorithm, lung segmentation images computed using an automatic segmentation algorithm [4] are provided. The lung segmentation images are not intended to be used as the reference standard for any segmentation study.

### DICOM images

An alternative format for the CT data is DICOM (.dcm). You can read a preliminary tutorial on how to handle, open and visualize .dcm images on the Forum page. The original DICOM files for LIDC-IDRI images can be downloaded from the LIDC-IDRI website.

## Model Architecture

The model uses a 3D Convolutional Neural Network (3D CNN) designed to capture spatial features from 3D CT scan volumes. The architecture includes multiple 3D convolutional layers, followed by max pooling, and fully connected layers.

## Results

Detailed results of the model's performance will be provided here, including accuracy, precision, recall, and F1-score.

## Contributing

Contributions are welcome!


<!-- ## Installation

To set up the project, follow these steps:

1. Clone the repository:

    ```bash
    git clone https://github.com/yourusername/LunaNet3D.git
    cd LunaNet3D
    ```

2. Create a virtual environment and activate it:

    ```bash
    python3 -m venv venv
    source venv/bin/activate
    ```

3. Install the required dependencies:

    ```bash
    pip install -r requirements.txt
    ```

## Usage

1. **Data Preprocessing:**
    Prepare the Luna16 dataset and preprocess the images.

    ```bash
    python preprocess.py
    ```

2. **Training the Model:**
    Train the 3D CNN model using the preprocessed data.

    ```bash
    python train.py
    ```

3. **Evaluating the Model:**
    Evaluate the trained model on the validation/test dataset.

    ```bash
    python evaluate.py
    ``` -->
