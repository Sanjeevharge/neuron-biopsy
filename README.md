**# README: Axon Detection and Measurement Script**  

---

## **Introduction**  
This Python script processes microscopy images to detect and measure axons and RBC-like structures using OpenCV. It identifies the outer and inner boundaries of axons, calculates their radii, thickness, and diameter, and provides visual output with marked contours and measurement details. The script also generates processed images and saves them to an output directory.  

---

## **Dependencies**  
Ensure the following Python libraries are installed:  
```bash
pip install opencv-python-headless numpy matplotlib
```

---

## **File Structure**  
```
├── input_dir/                # Input directory containing image patches
│   ├── image1.png
│   ├── image2.jpg
│   └── ...
├── output_dir/               # Output directory for processed images
├── script.py                 # Main script file
└── README.md                 # This file
```

---

## **Setup Instructions**  
1. Clone the repository or copy the script files.  
2. Install the dependencies using `pip install`.  
3. Update the input and output directory paths in the script:  
   ```python
   input_dir = "C:/Users/sanje/Downloads/patches"
   output_dir = "C:/Users/sanje/Downloads/output_imagesdkjdbh"
   ```
4. Run the script:  
   ```bash
   python script.py
   ```

---

## **How It Works**  
### **1. Input Handling**  
- The script reads images (`.png`, `.jpg`, `.jpeg`) from the input directory.  
- An output directory is created automatically if it doesn't exist.  

---

### **2. Image Processing**  
- Converts images to HSV color space and extracts the brightness (V) channel.  
- Applies adaptive thresholding to detect axon boundaries.  
- Applies morphological operations (closing, erosion) and Gaussian blur to refine the contours.  

---

### **3. Contour Detection and Classification**  
- Finds contours in the processed image.  
- Outer boundaries are drawn in **blue**.  
- Inner boundaries are drawn in **green**.  
- RBC-like structures are marked separately in **red**.  
- Measurements include:  
  - **Outer radius**  
  - **Inner radius**  
  - **Thickness**  
  - **Diameter**  

---

### **4. Output and Visualization**  
- Saves processed images with contours to the output directory.  
- Generates side-by-side comparison plots of original, processed, and output images.  
- Outputs measurements in micrometers based on a scaling factor (`0.136`).  

---

## **Parameters**  
| Parameter | Description | Value |  
|-----------|-------------|-------|  
| `kernel` | Kernel size for morphological operations | `(3, 3)` |  
| `scale_factor` | Scaling factor for converting pixel measurements to micrometers | `0.136` |  
| `min_contour_area` | Minimum contour area for valid axons | `620` |  
| `adaptiveThreshold` | Block size and constant for adaptive thresholding | `(11, 2)` |  

---

## **Example Output**  
Sample output in the console:  
```
Image image1.png, Object 1:
  Center = 120.45, 230.78
  Outer Radius = 15.8763 micro meters
  Diameter = 31.7526 micro meters
  Inner Radius = 12.3489 micro meters
  Thickness = 3.5274 micro meters
```

---

## **Results**  
- Processed images and plots are saved in the `output_dir` folder.  
- Console displays detected axon measurements and classification.  

---

## **Troubleshooting**  
| Problem | Solution |  
|---------|----------|  
| No contours found | Adjust thresholding parameters or kernel size. |  
| Output images are blurry | Try reducing the Gaussian blur kernel size. |  
| RBC misclassification | Adjust the `min_contour_area` value. |  

---

## **License**  
This project is open-source and free to use under the MIT license.  

---

## **Author**  
**Sanjeev Harge**  
March 2025  