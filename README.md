<div align="center">

# XRSign
### Real-Time Traffic-Sign Recognition via In-Browser Deep Neural Inference

*A reproducible, client-side computer-vision system for the detection and classification of road signs, built on a YOLO detector exported to the Open Neural Network Exchange (ONNX) format and executed entirely within the web browser.*

<br/>

<!-- Status & Metadata Widgets -->
<img alt="Status" src="https://img.shields.io/badge/status-active-brightgreen?style=for-the-badge" />
<img alt="Task" src="https://img.shields.io/badge/task-object%20detection-blueviolet?style=for-the-badge" />
<img alt="Model" src="https://img.shields.io/badge/model-YOLO%20%E2%86%92%20ONNX-blue?style=for-the-badge&logo=onnx&logoColor=white" />
<img alt="Inference" src="https://img.shields.io/badge/inference-in--browser-success?style=for-the-badge&logo=googlechrome&logoColor=white" />
<br/>
<img alt="Runtime" src="https://img.shields.io/badge/runtime-ONNX%20Runtime%20Web-lightgrey?style=for-the-badge" />
<img alt="Domain" src="https://img.shields.io/badge/domain-computer%20vision-0A66C2?style=for-the-badge" />
<img alt="License" src="https://img.shields.io/badge/license-non--commercial-red?style=for-the-badge" />

<br/><br/>

<img width="860" alt="XRSign real-time road-sign detection demonstration" src="https://github.com/user-attachments/assets/8c14af1a-f3c9-4ab3-b423-cc894b67ea20" />

</div>

---

## Abstract

**XRSign** presents an end-to-end pipeline for real-time traffic-sign recognition that operates without server-side computation. A single-stage YOLO detector is trained offline and exported to the ONNX intermediate representation (`best.onnx`), enabling hardware-agnostic deployment. Inference is performed on the client via ONNX Runtime Web, yielding low-latency predictions while preserving user privacy, as no visual data is transmitted off-device. The system demonstrates that a compact detection model can be delivered as a set of static assets and executed directly in a standard web browser, lowering the barrier to reproducible, deployable computer-vision research.

## 1. Motivation

Modern object-detection research is frequently constrained by heavyweight serving infrastructure. XRSign investigates a *serverless, client-side* alternative in which the trained model is shipped alongside the front end and evaluated locally. This design offers three advantages of practical and pedagogical value:

1. **Privacy by construction** — imagery never leaves the client device.
2. **Zero-infrastructure deployment** — the application is fully static and portable.
3. **Reproducibility** — a single versioned weight file (`best.onnx`) determines all predictions.

## 2. Methodology

| Stage | Description |
| :--- | :--- |
| **Training** | A YOLO single-stage detector is trained offline on annotated road-sign imagery. |
| **Export** | The trained network is serialized to ONNX (`best.onnx`) for portable, framework-independent inference. |
| **Pre-processing** | Input frames are resized and normalized into a fixed-shape tensor. |
| **Inference** | ONNX Runtime Web executes the detector directly in the browser. |
| **Post-processing** | Confidence thresholding and non-maximum suppression produce final bounding boxes and class labels. |
| **Visualization** | Detections are overlaid on the source media in real time. |

## 3. Repository Structure

| File | Description |
| :--- | :--- |
| `index.html` | Front-end interface and client-side inference logic. |
| `best.onnx` | Trained YOLO detector exported to the ONNX format. |
| `README.md` | Project documentation. |

## 4. Reproduction

```bash
# Clone the repository
git clone https://github.com/Derrickmirindi/XRSign.git
cd XRSign

# Serve the static assets (any static HTTP server is sufficient)
python -m http.server 8000

# Open the application
# http://localhost:8000/index.html
```

> A local HTTP server is recommended so that the browser may fetch `best.onnx` without cross-origin restrictions.

## 5. Technology Stack

<p align="center">
<img alt="HTML5" src="https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white" />
<img alt="JavaScript" src="https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black" />
<img alt="ONNX" src="https://img.shields.io/badge/ONNX-005CED?style=flat-square&logo=onnx&logoColor=white" />
<img alt="ONNX Runtime Web" src="https://img.shields.io/badge/ONNX%20Runtime%20Web-005CED?style=flat-square&logo=onnx&logoColor=white" />
<img alt="YOLO" src="https://img.shields.io/badge/YOLO-00FFFF?style=flat-square&logoColor=black" />
</p>

## 6. Authors

- **Derrick Mirindi**
- **David Sinkhonde**
- **Frederic Mirindi**

## 7. Citation

If you reference this work, please cite it as:

```bibtex
@software{mirindi_xrsign,
  author  = {Mirindi, Derrick and Sinkhonde, David and Mirindi, Frederic},
  title   = {{XRSign}: Real-Time Traffic-Sign Recognition via In-Browser Deep Neural Inference},
  url     = {https://github.com/Derrickmirindi/XRSign},
  note    = {Research and educational use only}
}
```

## 8. License and Usage

> **Do not sell this product.** XRSign is distributed for research and educational purposes only. Commercial redistribution or sale is strictly prohibited without the explicit written consent of the authors.
