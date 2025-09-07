# Pruning on Deformable DETR

**Authors:** Rishab Bohra, Shashank Shashidhar, Ebin Royce, Suhas Ungarala, Muhammed Shahbas V S

## Introduction

State-of-the-art object detectors such as Deformable DETR achieve high accuracy but are computationally expensive and memory-heavy. This limits deployment on edge devices and real-time systems.

This project explores pruning techniques (structured filter pruning and unstructured weight pruning) to compress Deformable DETR while analyzing the trade-off between accuracy, speed, and model size.

## Background

### Deformable DETR

- Faster convergence vs. DETR
- Better handling of small objects  
- Key innovation: Multi-Scale Deformable Attention
- Architecture: ResNet-50 + FPN backbone, Transformer Encoder/Decoder, prediction heads

### Pruning Approaches

1. **Structured Filter Pruning** – removes filters based on L1-norm
2. **Unstructured Weight Pruning** – removes individual low-magnitude weights

## Methodology

**Dataset:** KITTI Object Detection (Cars, Pedestrians, Cyclists)

**Preprocessing:** Converted KITTI `.txt` annotations → COCO JSON format

**Baseline Model:** Deformable DETR (ResNet-50 backbone) trained in MMDetection

**Pruning Experiments:**
- Filter pruning (10–50%)
- Weight pruning (10–90%)

## Evaluation Metrics

**Accuracy:** mAP, mAP50, per-class AP

**Efficiency:** Inference latency (CPU/GPU), FLOPs

**Model Size:** Parameters, checkpoint size, compression ratio

## Key Results

### Baseline
- mAP ≈ 0.117
- Latency ~205 ms
- ~205 GFLOPs

### Structured Filter Pruning
- Severe accuracy collapse (>20%)
- ~24% FLOP reduction at 50% pruning
- Minor runtime gain

### Unstructured Weight Pruning
- Better robustness at 30–40% sparsity
- Sharp collapse beyond 50–70%
- Reduced storage but no speedup

## Comparative Analysis

**Filter Pruning** → Least robust, fast accuracy collapse

**Weight Pruning** → Good storage reduction, no latency gain

## Conclusion

Pruning Deformable DETR is challenging due to its sensitivity.

- **Structured Filter Pruning** → Poor trade-off
- **Unstructured Weight Pruning** → Storage benefit only

The analysis reveals that while both pruning methods achieve compression, each comes with distinct limitations. Filter pruning shows rapid accuracy degradation, while weight pruning provides storage benefits without inference speedup.

## Repository Contents

- `torch_filter_pruning_final.ipynb` → Structured Filter Pruning experiments
- `training+unstructured_weight_pruning.ipynb` → Unstructured Weight Pruning experiments  
- `README.md` → Project summary (this file)
