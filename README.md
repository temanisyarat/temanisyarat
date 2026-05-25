# Teman Isyarat

[![Status](https://img.shields.io/badge/status-active-brightgreen)]()

> **Teman Isyarat** (Indonesian for "Sign Friend") — an AI-powered Indonesian Sign Language (BISINDO) recognition system. Built by a student team at **Universitas Sebelas Maret (UNS)** under the Hibah Jarprak program, in partnership with **GERKATIN Solo**.

## Overview

This monorepo contains the full stack of the Teman Isyarat project: from raw video recording through landmark extraction, deep learning training, to on-device real-time inference on Android.

```
Video (raw MP4)  ──►  lm/      ──►  .npz landmarks
                                (MediaPipe extraction)

.npz landmarks   ──►  model/   ──►  .tflite model
                                (GRU training & export)

.tflite model    ──►  android/ ──►  Live predictions
                                (On-device inference)
```

## Repositories

| Directory | Purpose |
|-----------|---------|
| [`lm/`](lm/) | MediaPipe holistic landmark extraction pipeline — converts raw BISINDO video recordings into `.npz` landmark arrays (pose + hands) with ffmpeg-based data augmentation |
| [`model/`](model/) | GRU-based neural network with temporal attention — trains on extracted landmarks, evaluates with signer-independent cross-validation, exports TFLite models for mobile deployment |
| [`android/`](android/) | Flutter + Kotlin Android app — real-time BISINDO translation via CameraX and MediaPipe, running the TFLite model fully offline with temporal smoothing and skeleton overlay |
| [`manager/`](manager/) | Obsidian vault for project management — architecture decision records (ADRs), technical specifications, sprint tracking, and team documentation |
| [`dataset/`](dataset/) | Raw BISINDO video dataset collected with GERKATIN Solo |
| [`web/`](web/) | Landing page and web platform |

## Vocabulary

The system recognizes **20 BISINDO vocabulary words** (Central Java dialect):

| Category | Words |
|----------|-------|
| **Pronouns** | Aku, Kamu, Dia |
| **Common** | Salam, Terima Kasih, Maaf, Nama |
| **Time** | Hari Ini, Besok |
| **Color** | Merah, Kuning |
| **Family** | Ayah, Ibu |
| **Count** | Satu, Dua, Tiga |
| **Other** | Teman, Buku |
| **Fruit** | Apel, Pisang |

## Team

| Name | Role |
|------|------|
| Dunhill William | Project Lead |
| Fredy Ramadhan | R&D |
| Hany Wachidatul | R&D |
| Febrian Jamaludin | R&D |
| Ivan Wahyu | R&D |
| Kevin Marchelino | R&D |
| Mutia Rahman | R&D |
| Usrotun Saidah | R&D |

## Acknowledgments

- **GERKATIN Solo** — Dataset collection, validation, and field testing
- **Universitas Sebelas Maret (UNS)** — Hibah Jarprak funding and academic support
- Built with [MediaPipe](https://mediapipe.dev), [TensorFlow](https://www.tensorflow.org/), and [Flutter](https://flutter.dev)
