# 👁️ Room People Detection System

A computer-vision-powered backend application that detects and tracks people in rooms using camera feeds.  
It automatically records detection data (timestamp, camera ID, people count, etc.) in a PostgreSQL database,  
providing real-time insights via a FastAPI backend.

---

## 🧠 Technology Stack

This project is designed to detect and record human presence from camera feeds using modern computer vision and backend technologies.

### 🔹 Computer Vision
- **OpenCV** — Capture video frames from connected cameras (USB or IP) and handle basic image operations.  
- **YOLOv8 (Ultralytics)** — Perform real-time person detection on each video frame.

### 🔹 Backend
- **FastAPI** — Build a fast and asynchronous REST API for managing detections and camera data.  
- **Pydantic** — Validate and serialize request/response models for the API.  
- **attrs** — Simplify data class creation for internal logic and configurations.

### 🔹 Database Layer
- **PostgreSQL** — Store detection data (timestamp, camera id, people count, etc.).  
- **SQLAlchemy** — Object-relational mapper (ORM) for interacting with the database.  
- **Alembic** — Handle database schema migrations and version control.

### 🔹 Deployment & Environment
- **Docker** — Containerize the application and database for consistent deployment.  
- **Docker Compose** — Manage multi-service setup (FastAPI app + PostgreSQL) easily.

---

## 🏗️ Project Overview

This project is a **camera-based people detection system** that monitors rooms and records detection data into a database.  
It combines computer vision and backend technologies to provide a complete detection–to–data pipeline.

---

## ⚙️ How It Works

1. **Camera Feed (OpenCV)**  
   - The system connects to a local or IP camera.  
   - OpenCV continuously captures video frames for processing.

2. **People Detection (YOLOv8)**  
   - Each captured frame is sent to the YOLO model.  
   - YOLO detects all people in the frame and returns bounding boxes and confidence levels.  
   - The number of people detected is counted and passed to the backend.

3. **Data Storage (PostgreSQL + SQLAlchemy)**  
   - Detection results (camera ID, timestamp, people count, optional image path) are stored in a PostgreSQL database.  
   - SQLAlchemy handles ORM mapping, while Alembic manages schema migrations.

4. **Backend API (FastAPI)**  
   - FastAPI provides REST endpoints to:
     - Retrieve detection history  
     - Query data by camera, time, or count  
     - Register new cameras  
   - Pydantic and attrs ensure clean validation and serialization of data models.

5. **Containerization (Docker + Docker Compose)**  
   - The entire system (FastAPI app + PostgreSQL database + YOLO dependencies) runs inside Docker containers.  
   - Docker Compose makes it easy to set up, start, and scale services.

---

## 🔁 Data Flow Summary

```text
Camera (OpenCV)
   ↓
YOLO Model → Detect people
   ↓
Backend (FastAPI)
   ↓
Database (PostgreSQL via SQLAlchemy)
   ↓
API → Returns detection data
