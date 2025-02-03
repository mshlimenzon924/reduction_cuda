# **CUDA Bitonic Sort - Jupyter Notebook (IPYNB) with GPU Support**

## **Overview**
This Jupyter Notebook (`.ipynb`) implements **Bitonic Sort** using both **CPU and GPU (CUDA)**. It leverages **parallel reduction** to efficiently sort an array of integers. The GPU version uses CUDA kernels to perform **bitonic comparison and swapping in parallel**, significantly speeding up the sorting process compared to the CPU version.

## **Features**
- Implements **Bitonic Sort** on both **CPU and GPU**.
- Uses **CUDA parallel processing** for faster execution.
- Measures and compares **GPU vs. CPU execution time**.
- Designed to be **run inside Jupyter Notebook** with **GPU support**.
- Supports sorting large arrays (`1 << 20` elements by default).

## **How It Works**
1. **Bitonic Sorting Structure**  
   - The array is divided into **bitonic sequences** (partially sorted subarrays).
   - These sequences are **merged** recursively using XOR-based comparisons.
  
2. **CUDA Parallel Execution**  
   - Each **GPU thread** processes a pair of elements (`i` and `ixj`).
   - The **comparison-swap operation** is done in **parallel** across the array.
   - The sorting is performed in **logarithmic passes (`log N` levels)**.

## **Running on Jupyter Notebook**
### **1. Setup Jupyter Notebook with CUDA Support**
- Ensure you have an **NVIDIA GPU** with CUDA support.
- Install **Jupyter Notebook** if not already installed:  
  `pip install notebook`
- Install **CUDA Toolkit** (if not installed):  
  `sudo apt update && sudo apt install -y nvidia-cuda-toolkit`

### **2. Launch Jupyter Notebook**
Run the following command in your terminal:  
`jupyter notebook`  
- Open the **Bitonic Sort Notebook (`.ipynb`)** in Jupyter.
- Ensure the **kernel is set to use GPU (CUDA).**  
  If using Google Colab, go to:  
  **Runtime → Change Runtime Type → Select GPU**

### **3. Compile and Run CUDA Code in Jupyter**
Jupyter supports CUDA execution via `%%writefile` and `!nvcc`. Follow these steps:
1. Write the CUDA program inside the notebook using:  
   `%%writefile reduction.cu`
2. Compile the program inside Jupyter:  
   `!nvcc reduction.cu -o bitonic_sort`
3. Run the compiled CUDA program:  
   `!./bitonic_sort`

## **Expected Output**
- Displays the **unsorted array** (if small).
- Displays the **sorted array (GPU and CPU)**.
- Prints **execution time** for both **CPU and GPU** versions.

## **Performance Comparison**
The program compares:
- **GPU Bitonic Sort time (parallel)**  
- **CPU Bitonic Sort time (sequential)**  

The GPU version should run significantly **faster**, especially for large arrays.
