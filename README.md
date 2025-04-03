# 🚀 CUDA-Accelerated Scharr Edge Detection
Final Integrating Project

## 📂 Repository Structure
This repository includes both **sequential (C)** and **parallel (CUDA)** implementations of the Scharr edge detection filter.

### 📄 Contents
- `/sequential/` – C implementation of Scharr filter
- `/cuda_parallel/` – CUDA (global memory) version
- `/cuda_shared/` – CUDA with shared memory
- `/cuda_texture/` – CUDA with texture memory
- `/screenshots/` – Execution screenshots for both versions
- `/docs/` – Conference paper and measurement data

---

## ✅ Project Deliverables

### 1. 🔗 Source Code
Both sequential and CUDA implementations are included. You can run each version independently using the provided Makefiles or compile commands.

### 2. 🖼️ Screenshots
- CUDA output (Parallel)
![image](https://github.com/user-attachments/assets/feffe9da-e413-4463-b302-dd35c9299224)

- CUDA output (Shared)
![image](https://github.com/user-attachments/assets/00fdb228-3db1-49b8-8de9-dc6d306a1604)

### 3. 🧵 Parallel Algorithms Discussion
The program converts the **nested for-loop pixel convolution** from the sequential C version into **parallelized GPU kernels** using:
- Thread-per-pixel execution
- Shared memory tiling
- Texture memory access for cache-optimized reads

Each CUDA version leverages specific memory strategies to optimize performance and reduce latency.

### 4. ⏱️ Execution Time Comparison

| Sample | C Code (μs) | CUDA Parallel (μs) | Shared Memory (μs) | Texture Memory (μs) |
|--------|-------------|---------------------|----------------------|----------------------|
| SP 1   | 11983.4     | 19.414              | 44.859               | 27.174               |
| SP 2   | 4665.367    | 9.349               | 20.336               | 12.868               |
| SP 3   | 2323.1      | 12.001              | 20.110               | 8.107                |
| ...    | ...         | ...                 | ...                  | ...                  |

> Full tables in `Conference Paper`

### 5. 📹 Demo Video
**Watch it here:** [👉 *[(https://youtu.be/iJHPFc4jMaI)*](#)

### 6. 📘 Conference Paper (Optional)
**Read it here:** [📄 *(https://docs.google.com/document/d/1YTEGht7gkyQsIa16bt_FBKTlApV9aRRHZKru94vA99A/edit?usp=sharing)*](#)

---

## 📌 How to Run
You need:
- A CUDA-compatible GPU
- OpenCV installed

### Compile (example):
```bash
nvcc Scharr_CUDA.cu -o Scharr_CUDA `pkg-config --cflags --libs opencv4`
./Scharr_CUDA
