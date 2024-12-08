# NCSU-CSC_591-RealTime_AI_and_Machine_Learning_Systems-CourseProject-LPRNet : Efficient Vehicle Plate Recognition - LPRNet 
<br>

## Course Project Report  
<br>


### Name: Yogesh Hasabe  
**UnityID**: yhasabe  

---

## Introduction  
Efficient license plate recognition is essential for real-time applications such as traffic monitoring and smart parking systems. This project optimizes the LPRNet model to enhance its accuracy, speed, and space efficiency. The report documents the original model, applied optimizations, performance outcomes, lessons learned, and repository details.

---

## Original DNN Model  
The project employs **LPRNet**, a lightweight and efficient model for license plate recognition.  

### Baseline Metrics:  
- **Accuracy**: 90.20%  
- **Inference Speed**: 0.21 seconds per 1/1000 images  
- **Model Size**: 1816.74 KB  

---

## Model Optimizations  
### 1. **Quantization**  
Quantization reduced model weights and activations to 8-bit integers, decreasing size while maintaining near-baseline accuracy.  

**Results**:  
- **Accuracy**: 89.80% (-0.30%)  
- **Speed**: 0.33 seconds per 1/1000 (slower inference)  
- **Model Size**: 533.57 KB (70.6% reduction)  

### 2. **Pruning**  
Pruning removed redundant connections, reducing model complexity.  

**Results**:  
- **Accuracy**: 90.10% (-0.10%)  
- **Speed**: 0.32 seconds per 1/1000  
- **Model Size**: 1816.74 KB (no change)  

---

## MLC Optimizations  
### 1. **Manual Optimization**  
Custom layer fusion and parallelization techniques were applied using TensorRT.  

**Results**:  
- **Accuracy**: 89.90% (-0.30%)  
- **Speed**: 0.036 seconds per 1/1000 (80.8% improvement)  
- **Model Size**: 840.7 KB (53.7% reduction)  

### 2. **AutoTuning Optimization**  
Automated optimization tools like NVIDIA NNI were used to explore optimal configurations.  

**Results**:  
- **Accuracy**: 89.80% (-0.40%)  
- **Speed**: 0.031 seconds per 1/1000 (83.7% improvement)  
- **Model Size**: 840.7 KB (53.7% reduction)  

---

## Combined Optimizations  
The best results were achieved by combining **pruning** and **AutoTuning** techniques.  

**Results**:  
- **Accuracy**: 90.00% (+0.30%)  
- **Speed**: 0.032 seconds per 1/1000 (84.7% improvement)  
- **Model Size**: 850.87 KB (53.2% reduction)  

---

## Performance Metrics Comparison  

| **Optimization**                | **Accuracy (%)** | **Speed (s/1k imgs)** | **Model Size (KB)** |
|----------------------------------|------------------|------------------------|----------------------|
| **Baseline Model**               | 90.20            | 0.21                   | 1816.74              |
| **Quantization**                 | 89.80            | 0.33                   | 533.57               |
| **Pruning**                      | 90.10            | 0.32                   | 1816.74              |
| **Manual Optimization**          | 89.90            | 0.036                  | 840.7                |
| **AutoTuning**                   | 89.80            | 0.031                  | 840.7                |
| **Combined (Pruning + AutoTuning)** | 90.00          | 0.032                  | 850.87               |

---

## Lessons Learned  
1. **Quantization Trade-offs**: Significantly reduces model size but may degrade accuracy and increase inference time.  
2. **Importance of Pruning**: Simplifies models effectively without severely impacting performance.  
3. **MLC Optimization Benefits**: Tools like TensorRT and NNI are invaluable for achieving high-speed performance but require extensive experimentation.  
4. **Combining Methods**: Combining optimizations yields the best balance of size, speed, and accuracy.  
5. **ONNX Compatibility**: ONNX format is incompatible with quantization techniques, thus not used.  

---

## Repository Details  
**GitHub Repository**: [Yogesh31Hasabe/NCSU-CSC_591-RealTime_AI_and_Machine_Learning_Systems-CourseProject-LPRNet](https://github.com/Yogesh31Hasabe/NCSU-CSC_591-RealTime_AI_and_Machine_Learning_Systems-CourseProject-LPRNet)  

### Repository Structure:  
- `./`: Contains all model training and optimization scripts (`.py` & `.ipynb`).  
- `/data`: Test dataset for validation.  
- `/weights`: Saved models and weights (baseline and optimized).  
- `README.md`: Detailed instructions for testing and reproducing results.  

---

## Instructions for Running the Project  
**Clone the repository** (if running locally) & execute the .ipynb files accordingly:
   ```bash
   git clone https://github.com/Yogesh31Hasabe/NCSU-CSC_591-RealTime_AI_and_Machine_Learning_Systems-CourseProject-LPRNet
  ``` 
Or 

- Run the following **.ipynb** files in Google Colab.
(NOTE: The entire file system setup required for respective executions of the `.ipynb` scripts on Google Colab is already included in the .ipynb scripts/notebooks)

  - For Model Optimizations:
    - Quantization: `yhasabe_Course_Project_Model_Optimization_Quantization.ipynb`
    - Pruning: `yhasabe_Course_Project_Model_Optimization_Pruning.ipynb`
      
  - For Model Optimizations:
      - Manual & AutoTuning: `yhasabe_Course_Project_MLC_Optimization_Manual_and_Auto.ipynb`
        
  - For Combined Optimizations:
      - `yhasabe_Course_Project_Combined_Optimizations_Pruning_and_AutoTuning.ipynb`

---

## Conclusion
The project successfully optimized the LPRNet model, achieving:

- **53.2%** reduction in model size
- **84.7%** improvement in inference speed
- **90%** accuracy (maintained from baseline)

These results demonstrate the effectiveness of combining **Pruning** and **Automated MLC** techniques for **real-world deployment** of lightweight DNNs.

---
