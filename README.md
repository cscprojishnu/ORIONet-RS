# ORIONet-RS

### Orientation- and Scale-Adaptive Feature Learning for Arbitrarily Oriented Object Detection in Optical Remote Sensing Imagery

ORIONet is an **orientation- and scale-adaptive, anchor-free framework** for object detection in high-resolution optical remote-sensing imagery. It is designed to address arbitrary object orientation, small-object information loss, spatial context, and multi-scale representation.

## Dataset

**DIOR — Dataset for Object Detection in Optical Remote Sensing Images**

🔗 **[IEEE DataPort – DIOR](https://ieee-dataport.org/documents/dior)**

* **Images:** 23,463
* **Object Instances:** 192,472
* **Categories:** 20
* **Spatial Resolution:** ~0.5–30 m
* **Application:** Optical remote-sensing object detection
* **Annotations:** Horizontal bounding boxes

## Architecture

```text
Input Image (512 × 512)
        ↓
CNN Backbone
        ↓
Hierarchical Features (C2, C3, C4)
        ↓
RAFM — Rotation-Aware Feature Module
        ↓
FOEM — Fine-Grained Object Enhancement Module
        ↓
SCA — Spatial Context Aggregation
        ↓
AMSF — Adaptive Multi-Scale Fusion
        ↓
Anchor-Free OBB Detection Head
        ├── Classification
        ├── Bounding Box Regression
        └── Orientation Estimation
```

## Key Components

* **RAFM** — captures direction-sensitive patterns using multi-branch convolution and channel gating.
* **FOEM** — preserves fine-grained information for small and densely distributed objects.
* **SCA** — models multi-scale spatial context using dilated convolutions.
* **AMSF** — adaptively fuses hierarchical features based on scale and scene complexity.
* **OBB Head** — jointly predicts object category, geometry, and orientation using sine–cosine angle representation.

## Training

| Setting    | Value                        |
| ---------- | ---------------------------- |
| Epochs     | **50**                       |
| Input Size | **512 × 512**                |
| Model Type | **Anchor-Free OBB Detector** |
| Parameters | **22.54M**                   |

## Results

| Metric        |    ORIONet |
| ------------- | ---------: |
| Test Accuracy | **97.01%** |
| Precision     | **90.76%** |
| Recall        | **95.80%** |
| F1-Score      | **92.12%** |
| Parameters    | **22.54M** |

> **Evaluation Note:** The reported accuracy, precision, recall, and F1-score correspond to **GT-center classification evaluation** in the current implementation. Complete OBB validation using rotated IoU, OBB mAP, scale-specific AP, orientation error, and rotated NMS remains part of the planned evaluation.

## Ablation

The component-wise study evaluates the progressive contribution of **FOEM, SCA, Adaptive Multi-Scale Fusion, and RAFM**.

| Configuration     | Test Accuracy |         F1 |
| ----------------- | ------------: | ---------: |
| Baseline          |        25.47% |      3.79% |
| + FOEM            |         0.47% |      0.07% |
| + SCA             |         1.42% |      0.46% |
| + Adaptive Fusion |        79.25% |     47.45% |
| **Full ORIONet**  |    **97.17%** | **92.03%** |

## Citation

```bibtex
@article{dandamudi2026orionet,
  title={ORIONet: Orientation- and Scale-Adaptive Feature Learning for Arbitrarily Oriented Object Detection in Optical Remote Sensing Imagery},
  author={Dandamudi, Jishnu Teja and Chhetri, Yogendra and Anandkumar, V. and Ainapure, Bharati and Kosna, Srinivas Reddy and Shahare, Yogesh},
  year={2026}
}
```

## Code

🔗 **[ORIONet-RS — GitHub](https://github.com/cscprojishnu/ORIONet-RS)**

```

The architecture and DIOR statistics are documented in the paper, while the current evaluation limitation is explicitly noted there as well. 
```
