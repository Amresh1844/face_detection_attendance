# 🎯 Real-Time Face Recognition Attendance System

A real-time facial recognition attendance system built with **Python** and **OpenCV**. It detects and recognizes faces via webcam, matches them against a registered database of face encodings, and automatically logs attendance with timestamps — eliminating manual roll calls and proxy attendance.

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![OpenCV](https://img.shields.io/badge/OpenCV-4.x-green)
![License](https://img.shields.io/badge/License-MIT-yellow)
![Status](https://img.shields.io/badge/Status-Active-brightgreen)

---

## 📖 Overview

Traditional attendance methods — roll calls, fingerprint scanners, RFID cards — are slow, contact-based, and easy to manipulate through proxy attendance. This project automates the entire process using **computer vision**: a camera feed detects faces in real time, matches them against registered identities, and logs attendance automatically with a date-time stamp, with zero manual effort after setup.

---

## ✨ Features

- 📸 **Real-time face detection** from a live webcam/CCTV feed
- 🧠 **Face recognition** using encoded facial features (128-d embeddings)
- 🗂️ **Automatic attendance logging** with name, date, and timestamp
- 🚫 **Duplicate-entry prevention** — one entry per person per session
- 👥 **Multi-face detection** — handles multiple people in a single frame
- 💾 **Exportable attendance records** (CSV / Excel / database)
- 🖥️ Simple, lightweight, and easy to extend with a GUI or web dashboard

---

## 🏗️ System Architecture

```
Webcam Feed
    │
    ▼
Face Detection (Haar Cascade / DNN)
    │
    ▼
Preprocessing (grayscale, resize, alignment)
    │
    ▼
Face Encoding (face_recognition / LBPH)
    │
    ▼
Match Against Registered Database
    │
    ▼
Attendance Logged (CSV / SQLite) with Timestamp
```

---

## 🛠️ Tech Stack

| Component            | Technology                              |
|-----------------------|------------------------------------------|
| Language              | Python 3.8+                              |
| Face Detection         | OpenCV (Haar Cascade / DNN module)       |
| Face Recognition       | `face_recognition` (dlib-based) / LBPH   |
| Data Storage           | CSV / SQLite / MySQL                     |
| Data Handling          | Pandas, NumPy                            |
| Optional GUI           | Tkinter / Streamlit / Flask              |

---

## 📂 Project Structure

```
face-recognition-attendance/
│
├── dataset/                  # Registered users' face images
├── encodings/                # Stored face encodings (.pickle)
├── attendance/                # Generated attendance CSV files
├── src/
│   ├── register_faces.py     # Capture & encode new faces
│   ├── recognize_attendance.py # Real-time detection + attendance marking
│   └── utils.py               # Helper functions
├── requirements.txt
├── README.md
└── LICENSE
```

---

## ⚙️ Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/ashirbad003/face-recognition-attendance.git
   cd face-recognition-attendance
   ```

2. **Create a virtual environment (recommended)**
   ```bash
   python -m venv venv
   source venv/bin/activate      # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

   > **Note:** `dlib` installation can be tricky on Windows. If you face issues, install via `conda install -c conda-forge dlib` or use a prebuilt wheel.

---

## 🚀 Usage

### 1. Register a new face
```bash
python src/register_faces.py --name "Ashirbad Sahoo" --id "21CSE001"
```
This captures a few images via webcam and stores the face encoding in the `encodings/` folder.

### 2. Start real-time attendance
```bash
python src/recognize_attendance.py
```
The webcam feed opens, detects faces, matches them against registered users, and logs attendance automatically to `attendance/attendance_<date>.csv`.

### 3. Sample attendance log

| Name             | ID         | Date       | Time     | Status  |
|-------------------|------------|------------|----------|---------|
| Ashirbad Sahoo    | 21CSE001   | 2026-09-10 | 09:03:12 | Present |

---

## 📦 Requirements

```
opencv-python
face_recognition
numpy
pandas
dlib
```

(Full list in `requirements.txt`)

---

## ⚠️ Known Limitations

- Accuracy can drop in poor lighting or extreme face angles
- No built-in liveness detection (susceptible to photo/video spoofing) — planned in future scope
- Recognition speed depends on hardware (CPU-only setups may lag with many registered faces)

---

## 🔮 Future Scope

- [ ] Liveness/anti-spoofing detection (blink/texture-based)
- [ ] Cloud database integration (Firebase) for multi-branch sync
- [ ] Web-based admin dashboard for reports and analytics
- [ ] Mobile app for remote attendance marking
- [ ] Email/SMS alerts on absentees

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome!
1. Fork the repo
2. Create your feature branch (`git checkout -b feature/new-feature`)
3. Commit your changes (`git commit -m 'Add new feature'`)
4. Push to the branch (`git push origin feature/new-feature`)
5. Open a Pull Request

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

## 👤 Author

**Ashirbad Sahoo**
- GitHub: [@Amresh1844](https://github.com/Amresh1844)

