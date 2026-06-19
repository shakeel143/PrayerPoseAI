---
title: Namaz Posture Identification API
emoji: 🕌
colorFrom: green
colorTo: blue
sdk: docker
pinned: false
license: mit
app_port: 7860
---

# Namaz Posture Identification — Backend API

REST API for real-time Namaz posture detection using MediaPipe pose landmarks + ML classifier.

## Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/` | Health check |
| POST | `/predict` | Predict posture from 132 landmark features |
| GET | `/postures` | List all posture classes |

## POST /predict

**Request body:**
```json
{
  "landmarks": [0.12, 0.45, -0.03, 0.99, ...]
}
```
132 floats: 33 MediaPipe pose landmarks × [x, y, z, visibility]

**Response:**
```json
{
  "prediction": "qiam",
  "confidence": 0.98,
  "probabilities": {"qiam": 0.98, "rukooh": 0.01, "Sajdah": 0.00, "julsa": 0.01},
  "arabic": "قيام",
  "description": "Standing upright — the opening position of prayer",
  "color": "#2196F3",
  "emoji": "🧍"
}
```

## Classes
- **qiam** قيام — Standing
- **rukooh** ركوع — Bowing
- **Sajdah** سجدة — Prostration
- **julsa** جلسة — Sitting
