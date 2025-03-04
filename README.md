video_corner_detection# **ENPM673 - Perception for Autonomous Robots - Project 2**

## **Project Overview**
This project is part of **ENPM673 - Perception for Autonomous Robots** at the **University of Maryland, College Park**. It consists of two main tasks:  
1. **Video Processing for Paper Corner Detection**  
2. **Image Stitching for Panoramic Mosaicing**  

The goal of this project is to develop **computer vision pipelines** for:
- **Processing video frames** to extract the four corners of a sheet of paper.
- **Detecting and removing blurry frames** using the **Variance of Laplacian**.
- **Extracting edges and corners** using techniques like **Hough Transform** and **Harris Corner Detection**.
- **Stitching images** to generate a **panoramic image** using **feature extraction and homographies**.

---

## **Table of Contents**
- [Project Overview](#project-overview)
- [Features](#features)
- [Installation](#installation)
  - [Step 1: Clone the Repository](#step-1-clone-the-repository)
  - [Step 2: Install Dependencies](#step-2-install-dependencies)
  - [Step 3: Running the Jupyter Notebook](#step-3-running-the-jupyter-notebook)
- [Running the Project](#running-the-project)
  - [Problem 1: Paper Corner Detection](#problem-1-paper-corner-detection)
  - [Problem 2: Image Stitching for Panorama](#problem-2-image-stitching-for-panorama)
- [Project Structure](#project-structure)
- [How the Code Works](#how-the-code-works)
- [Authors](#authors)
- [License](#license)

---

## **Features**
✔ **Video Processing:** Reads frames, detects edges, and finds corners of a sheet of paper.  
✔ **Blurry Frame Removal:** Uses **Variance of Laplacian** to remove blurry frames.  
✔ **Edge & Corner Detection:** Uses **Hough Transform and Harris Corner Detector**.  
✔ **Homography Computation:** Stitches images using **feature matching and RANSAC**.  
✔ **Panoramic Mosaicing:** Generates **stitched panoramic images** from input images.  
✔ **Overlay Visualization:** Draws **blue edges and red corner points** on the output video.  

---

## **Installation**
### **Prerequisites**
Ensure you have the following dependencies installed:
- **Python 3.8+**
- **Jupyter Notebook**
- **OpenCV**
- **NumPy**
- **Matplotlib**

### **Step 1: Clone the Repository**
```bash
git clone <your-repository-url> enpm673_project2
cd enpm673_project2
```
### **Step2: Install Dependencies**
Install the required Python packages:

```bash
pip install -r requirements.txt

```

### **Step 3: Running the Jupyter Notebook**
```
jupyter notebook

```
Then, open harshav_project2.ipynb in Jupyter and execute the code step by step.
## **Running the Project**
### **Problem 1: Paper Corner Detection**
Command to Run
```
python paper_corner_detection.py --input video.mp4 --output processed_video.mp4
```
**Processing Pipeline**
- Reads video frames using OpenCV.
- Removes blurry frames using Variance of Laplacian (Threshold = 150).
- Converts images to grayscale.
- Detects edges using Canny Edge Detection.
- Extracts Hough Lines from detected edges.
- Identifies intersecting lines as potential corners.
- Verifies corners using Harris Corner Detector.
- Overlays the boundary (blue lines) and corners (red dots) on the output video.
**Expected Output**
- A video file with corner-detected frames.
- Removed blurry frames count displayed in the console.

### **Problem 2: Image Stitching for Panorama**
Command to Run
```
python image_stitching.py --input images/ --output panorama.jpg
```
**Processing Pipeline**
Loads 4 input images.
- Extracts features using SIFT, ORB, or another feature extractor.
- Matches features using FLANN or brute-force matcher.
- Uses RANSAC to filter out bad matches.
- Computes homographies between image pairs.
- Warps images onto a common plane.
- Blends images to create a final stitched panorama.
**Expected Output**
- A stitched panoramic image saved as panorama.jpg.

## **Project Structure**
```
enpm673_project2/
├── harshav_project2.ipynb      # Jupyter Notebook for full execution
├── paper_corner_detection.py   # Python script for video processing (Problem 1)
├── image_stitching.py          # Python script for image stitching (Problem 2)
├── input/
│   ├── video.mp4               # Input video for corner detection
│   ├── images/                 # Folder containing 4 input images for stitching
│
├── output/
│   ├── processed_video.mp4      # Output video with detected corners
│   ├── panorama.jpg             # Stitched panoramic image
│
├── requirements.txt             # Dependencies for the project
├── README.md                    # Documentation

```

## **How the Code Works**
**1. Paper Corner Detection**
- Reads each video frame.
- Removes blurry frames using Variance of Laplacian.
- Detects edges using Canny.
- Finds lines using Hough Transform.
- Extracts intersections (putative corners).
- Validates corners using Harris Corner Detector.
- Overlays the edges and corners onto the video.
**2. Image Stitching**
- Extracts keypoints using SIFT/ORB.
- Matches keypoints between consecutive images.
- Filters incorrect matches using RANSAC.
- Computes homographies to warp images together.
- Blends images to create a seamless panoramic output.
