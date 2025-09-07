Road Obstacle Detection – Pruning Deformable DETR

Authors: Ebin Royce Vadakkemulanjanal, Rishab Bohra, Shashank Shashidhar, Suhas Ungarala, Muhammed Shahbas V S

This project explores pruning techniques on Deformable DETR to reduce model size and inference latency while maintaining high detection accuracy for real-time obstacle detection in autonomous driving.

Overview

Deformable DETR achieves high accuracy but is computationally heavy. We applied:

Structured Filter Pruning – removes less important convolutional filters

Unstructured Weight Pruning – removes low-magnitude weights

to compress the model and improve deployment feasibility.

Dataset

KITTI Object Detection Dataset

Classes: Cars, Pedestrians, Cyclists

Preprocessed .txt annotations converted to COCO JSON format for MMDetection compatibility.

Methodology

Baseline: Deformable DETR with ResNet-50 + FPN backbone

Experiments:

Filter pruning: 10–50% filters

Weight pruning: 10–90% sparsity

Evaluation Metrics: mAP, mAP50, per-class AP, inference latency, FLOPs, model size

Key Results

Filter Pruning: ~32.5% parameter reduction, ~23.7% FLOPs savings, minor accuracy loss, inference latency improved (~205 ms → ~196 ms)

Weight Pruning: ~30–40% parameter reduction (sparsity), mainly reduces storage, no significant speedup

Repository Contents

torch_filter_pruning_final.ipynb → Filter pruning experiments

training+unstructured_weight_pruning.ipynb → Weight pruning experiments

README.md → Project summary
