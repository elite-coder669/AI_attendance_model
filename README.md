# AI Attendance Model

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![OpenCV](https://img.shields.io/badge/OpenCV-4.x-green)
![License](https://img.shields.io/badge/license-View--Only-lightgrey)
![Status](https://img.shields.io/badge/status-active-brightgreen)

A face recognition-based attendance system that uses computer vision to register and authenticate users via webcam.

## Stack

- Python 3
- OpenCV — real-time video capture and frame processing
- face_recognition — face detection and encoding comparison
- dlib — 68-point facial landmark detection
- tkinter / PIL — desktop GUI
- HOG + CNN — face detection models

## How it works

The system has two modes:

```mermaid
flowchart TD
    A[Launch App] --> B{Choose option}
    B -->|1 - Register| C[Enter name]
    C --> D[Open webcam]
    D --> E{Face detected?}
    E -->|No| D
    E -->|Yes| F[Capture photo]
    F --> G[Save with landmarks]
    G --> H[User stored]
    B -->|2 - Login| I[Open webcam]
    I --> J[Stream frames]
    J --> K[Detect faces]
    K --> L[Encode face]
    L --> M{Match in DB?}
    M -->|Yes| N[Log attendance]
    M -->|No| O[Tag as Unknown]
```

**Registration** — A new user enters their name. The webcam opens and automatically captures their photo when a face is detected. The image is saved to disk with facial landmarks overlaid.

**Login / Attendance** — The webcam streams live video. Each frame is scanned for faces. Detected faces are encoded and compared against the registered user database. A match triggers an attendance record; unknown faces are tagged accordingly.

Facial landmarks (eyes, nose, jawline) are computed using dlib's shape predictor and drawn as blue dots on the video feed — providing real-time feedback that the face is being properly analyzed.

## Key features

- Real-time face detection and recognition via webcam
- 68-point facial landmark visualization
- Automatic photo capture on face detection
- Tkinter GUI with live video preview
- HOG-based detection (lightweight, CPU-friendly)

## What this demonstrates

- Practical computer vision pipeline integration
- Working with multiple CV libraries (OpenCV, dlib, face_recognition) in a single application
- Building a desktop GUI with live video streaming
- Image processing and encoding algorithms

## Run locally

```bash
pip install opencv-python face_recognition dlib pillow
python PROTOTYPE.PY
```

> Note: Download `shape_predictor_68_face_landmarks.dat` from dlib's model zoo and place it in the project root.
