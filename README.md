# Signal Analysis and Wavelet Transform README

## Overview
This project revolves around analyzing signals using **Wavelet Transform techniques**, with a particular focus on compressing and reconstructing signals efficiently. Signal compression is vital in fields like biomedical engineering (e.g., ECG signal analysis), telecommunications, and data processing, where storage and bandwidth constraints demand innovative solutions.

Wavelets provide a powerful tool for signal decomposition and reconstruction because of their ability to analyze signals across different scales and frequencies. In this project, multiple methods were implemented and evaluated to explore the capabilities of wavelet-based signal reconstruction, including methods to reduce bandwidth while retaining critical features of the signal.

---

## Objectives
The primary goals of this project include:
1. **Signal Decomposition**: Breaking down signals into components at various scales using Haar wavelet and dyadic wavelet transforms.
2. **Signal Reconstruction**: Rebuilding the original signal using different methods:
   - Reconstruction from coefficients at a single scale.
   - Reconstruction from coefficients across multiple scales.
   - Reconstruction with bandwidth reduction using Matching Pursuit.
3. **Compression Analysis**: Reducing the number of coefficients used while evaluating trade-offs between compression and reconstruction quality.
4. **Performance Metrics**: Quantitatively assessing reconstruction accuracy through metrics like RMSE and Compression Ratio.
5. **Visualization**: Generating plots to visually compare decomposition results and reconstruction fidelity.

---

## Project Structure

### 1. **Introduction**
Provides the theoretical background of wavelet transforms and explains why these methods are suitable for signal analysis.

### 2. **Data Preprocessing**
Outlines steps for cleaning and preparing raw signal data for analysis. This ensures the signals are ready for transformation and reconstruction.

### 3. **Dyadic Wavelet Transform**
Details how signals are transformed into wavelet components at varying scales. Subtopics include:
- **Mexican Hat Wavelet**: Introduction to the mother wavelet used.
- **Dyadic Wavelet Atoms**: How wavelet functions are generated.
- **Wavelet Atoms for Various Scales and Shifts**: Exploring signal decomposition across different resolutions.

### 4. **Wavelet Transform Calculation**
Describes the step-by-step procedure for performing wavelet transforms on signals. Subtopics include:
- Interpreting the results of wavelet decomposition.
- Understanding plots of wavelet coefficients and their significance.

### 5. **Dyadic Wavelet Decomposition**
Focuses on Haar wavelet transformation, with in-depth analysis of:
- **Wavelet Atoms**: Representation of high-frequency components.
- **Scaling Functions**: Representation of low-frequency components.
- **Plots**: Visualizing wavelet atoms and scaling functions.

### 6. **Dyadic Haar Wavelet Decomposition**
Details decomposition results, with a focus on:
- **Detail Coefficients**: Capturing fine-grained signal variations.
- **Approximation Coefficients**: Representing the overall structure of the signal.
- Visual analysis through plots.

### 7. **Wavelet Decomposition for Different Scales**
Compares decomposition results at finer and coarser scales (e.g., \( j = 1 \) vs \( j = 3 \)) to illustrate how scale impacts signal representation.

### 8. **Signal Reconstruction**
Outlines methods to reconstruct signals using wavelet coefficients:
- **(v0)**: Reconstruction at a single scale using Haar wavelet coefficients.
- **(v1)**: Reconstruction combining coefficients across multiple scales.
- **(v2)**: Bandwidth-reduced reconstruction using Matching Pursuit.

### 9. **Reduced Bandwidth Signal Reconstruction (v2)**
Explains how Matching Pursuit reduces the number of coefficients used for reconstruction to \( N/4 \), prioritizing significant coefficients while maintaining fidelity.

### 10. **Analysis of Chosen Methods**
Discusses the techniques applied for reconstruction, their advantages (e.g., compression efficiency), and limitations (e.g., computational cost).

### 11. **Results**
Summarizes the results of the three reconstruction methods:
- Quantitative comparison using RMSE and Compression Ratio.
- Insights into compression vs reconstruction quality trade-offs.

### 12. **Discussion**
Evaluates the overall effectiveness of Matching Pursuit, explores potential limitations, and highlights applications in real-world scenarios.

### 13. **Conclusion**
Concludes the findings and reflects on the broader implications of wavelet-based signal compression and reconstruction.

---

## Implementation Instructions

### Signal Decomposition
- Use Haar wavelet transforms to decompose signals into detail and approximation coefficients.
- Generate plots to visualize coefficients and their behavior at different scales and shifts.

### Signal Reconstruction
#### **Method v0: Single Scale Reconstruction**
Reconstruct the signal using coefficients at a single scale (\( j = 1 \)) with the `get_reconstructed_signal_v0` function.

#### **Method v1: Multi-scale Reconstruction**
Combine coefficients across multiple scales using `get_reconstructed_signal_v1`, capturing both high- and low-frequency signal components.

#### **Method v2: Bandwidth-reduced Reconstruction**
Compress the signal by limiting the number of coefficients to \( N/4 \) using the `get_reconstructed_signal_v2` function. This method applies the Matching Pursuit algorithm to select the most significant coefficients iteratively.

---

## How to Evaluate Performance
## Root Mean Squared Error (RMSE)

RMSE measures the difference between the original and reconstructed signals, providing a quantitative assessment of reconstruction accuracy. The formula is:

$$
\text{RMSE} = \sqrt{\frac{1}{N} \sum_{i=1}^{N} \left( \hat{x}_i - x_i \right)^2 }
$$

Where:

- \( N \): The total number of samples in the signal.  
- \( x_i \): The original signal value at the \( i \)-th sample.  
- \( \hat{x}_i \): The reconstructed signal value at the \( i \)-th sample.  

A lower RMSE value indicates a closer match between the reconstructed and original signals, signifying higher reconstruction accuracy.  

---

## Compression Ratio (CR)

CR evaluates how effectively the signal has been compressed by comparing the number of coefficients used to reconstruct the signal to the original signal length. The formula is:

$$
\text{CR} = \frac{\text{Number of Coefficients Used}}{\text{Signal Length}}
$$

Where:

- **Number of Coefficients Used**: The number of wavelet coefficients retained for reconstruction.  
- **Signal Length**: The total number of samples in the original signal.  

The CR indicates the degree of compression. For example:

$$
\text{CR} = 0.25
$$  

implies the signal has been compressed to 25% of its original size, using only a quarter of the original coefficients.


---
---

## Plotting Results
Visualize reconstructed signals alongside the original signals to compare fidelity and compression effects. Specific plots include:
- Coefficients at different scales (\( j = 1 \) and \( j = 3 \)).
- Signal reconstruction quality for methods v0, v1, and v2.

---

## Documentation Notes
- Sections 8, 9, and 10 detail different reconstruction methods, offering insights into their processes and trade-offs.
- Section 11 describes the rationale behind choosing these methods, exploring techniques and limitations.
- Results and discussions (sections 12 and 13) analyze RMSE, compression efficiency, and practical applications.

---

