# Zero-Shot Human Activity Recognition (HAR) using Transformer and BERT

This project implements a Zero-Shot Learning (ZSL) framework to classify human activities from sensor/time-series data — including activities the model has never seen during training.  
It combines Transformer encoders for sensor data representation and BERT embeddings for semantic label understanding.

---

## Project Overview

Traditional human activity recognition (HAR) models require labeled data for every possible activity.  
However, in real-world settings, new activities (like "folding laundry" or "rope jumping") may appear that were not part of the training set.

This project uses Zero-Shot Learning (ZSL) so the model can recognize unseen activities by leveraging semantic information (text embeddings of activity names).

---

## Core Idea

| Component | Description |
|------------|-------------|
| Sensor Encoder | A Transformer-based model that converts raw sensor sequences into high-level embeddings. |
| Text Encoder | A pre-trained BERT model that converts activity names (e.g., “walking”, “vacuum cleaning”) into semantic embeddings. |
| ZSL Alignment | The model learns to align sensor embeddings with their corresponding text embeddings using a contrastive loss (cosine similarity). |
| Zero-Shot Inference | At test time, the model predicts unseen activities by finding the most similar text embedding among all activity classes. |

---

## Dataset

The dataset contains multivariate time-series sensor readings (e.g., accelerometer, gyroscope) with 33 features per time step.
II. Data format
II.1. Synchronized and labeled raw data from all the sensors (3 IMUs and the HR-monitor) is merged
into 1 data file per subject per session (protocol or optional), available as text-files (.dat). Each of the data-files contains 54 columns per row, the columns contain the following data:
 – 1
– 2
– 3
– 4-20
– 21-37
– 38-54
timestamp (s)
activityID (see II.2. for the mapping to the activities) heart rate (bpm)
IMU hand
IMU chest
IMU ankle
The IMU sensory data contains the following columns:
– 1
– 2-4
– 5-7
– 8-10
– 11-13
– 14-17
temperature (°C)
3D-acceleration data (ms-2), scale: ±16g, resolution: 13-bit 3D-acceleration data (ms-2), scale: ±6g, resolution: 13-bit* 3D-gyroscope data (rad/s)
3D-magnetometer data (μT)
orientation (invalid in this data collection)
