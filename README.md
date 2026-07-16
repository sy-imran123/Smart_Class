<div align="center">
  <img src="https://i.ibb.co/YTYGn5qV/logo.png" alt="SnapClass Logo" width="120">
  
  # 📸 SnapClass: AI-Powered Attendance System
  
  **Making Attendance faster using AI**

  [![Python](https://img.shields.io/badge/Python-3.10+-blue?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
  [![Streamlit](https://img.shields.io/badge/Streamlit-FF4B4B?style=for-the-badge&logo=Streamlit&logoColor=white)](https://streamlit.io/)
  [![Supabase](https://img.shields.io/badge/Supabase-3ECF8E?style=for-the-badge&logo=supabase&logoColor=white)](https://supabase.com/)
  [![Machine Learning](https://img.shields.io/badge/Machine_Learning-FF9900?style=for-the-badge&logo=amazonaws&logoColor=white)](#)

  [**🖥️ View Live Demo**](#) • [**🐛 Report Bug**](#) • [**✨ Request Feature**](#) • [**👨‍💻 Developer LinkedIn**](#)
</div>

---

## 🚀 Project Overview

**SnapClass** is a modern, end-to-end educational web application engineered to solve the bottleneck of manual classroom roll calls[cite: 1, 2]. By leveraging state-of-the-art machine learning, this platform provides multi-modal biometric authentication—integrating both **Computer Vision** (Facial Recognition) and **Audio Processing** (Voice Recognition)[cite: 9, 16, 17, 20]. 

Designed with scalability in mind, SnapClass connects a dynamic Python frontend to a robust PostgreSQL cloud database, demonstrating full-stack ML deployment capabilities[cite: 3, 14].

---

## ✨ Core Features

### 👨‍🏫 For Educators (Teacher Portal)
* **📸 One-Click Face Attendance:** Capture or upload images of the classroom. The AI uses `dlib` and Support Vector Classification (`SVC`) to instantly detect faces, match them against the database, and log attendance[cite: 13, 16, 20].
* **🎙️ Voice Roll Call Processing:** Record a continuous audio snippet of students saying "I am present". The app automatically segments the audio and identifies students via `resemblyzer` voice embeddings[cite: 9, 17, 20].
* **📊 Analytics & Records:** Access historical attendance records grouped by timestamp, displaying comprehensive class attendance ratios[cite: 20].
* **🔗 Smart Class Management:** Create new subjects and generate shareable joining links or QR codes (via `segno`) for frictionless student onboarding[cite: 6, 8, 20].
* **🔐 Secure Access:** Enterprise-grade security with `bcrypt` password hashing for teacher credentials[cite: 15, 20].

### 🎓 For Learners (Student Portal)
* **👁️ Passwordless Biometric Login:** Students access their personalized dashboards securely by simply scanning their face through the device camera[cite: 19].
* **📲 Frictionless Enrollment:** Join a subject instantly via URL query parameters (`join-code`), a shared subject code, or QR scanning[cite: 1, 5, 7, 8].
* **👤 Multi-Modal Profile Setup:** New students can register a dual-biometric profile by providing a baseline facial snapshot and an optional voice vector[cite: 19].
* **📈 Performance Tracking:** A sleek dashboard visualizes enrolled courses and calculates personal attendance rates (Total Classes vs. Classes Attended)[cite: 19].

---

## 🛠️ Technology Stack & Architecture

### 🖥️ Frontend & Routing
* **[Streamlit](https://streamlit.io/):** Powers the reactive UI, session state management, and multi-page routing[cite: 1, 3].
* **Custom CSS:** Injected custom styling via `base_layout.py` for a polished, app-like UI (hiding default Streamlit headers, custom Google Fonts, and themed buttons)[cite: 21].

### 🧠 Machine Learning Pipelines
* **Vision (`scikit-learn`, `dlib-bin`, `face_recognition_models`):** Extracts 128-dimensional face descriptors and predicts student identities utilizing an SVM classifier[cite: 3, 16].
* **Audio (`librosa`, `resemblyzer`):** Processes classroom `.wav` files, applies decibel-based segmentation, and evaluates cosine similarity against stored voice embeddings[cite: 3, 17].

### 🗄️ Backend & Database
* **[Supabase](https://supabase.com/):** Acts as the primary PostgreSQL database handling relational mapping between students, teachers, subjects, and attendance logs[cite: 3, 14, 15].
* **Authentication:** Integrates `bcrypt` to salt and hash teacher passwords prior to database insertion[cite: 3, 15].

### 🧰 Utilities
* **[Pandas](https://pandas.pydata.org/) & [NumPy](https://numpy.org/):** Handles matrix operations for ML embeddings and data wrangling for attendance reporting.
* **[Pillow (PIL)](https://python-pillow.org/) & [Segno](https://segno.readthedocs.io/):** Manages image processing and renders scannable QR codes[cite: 3].

---

## 📂 Repository Structure

```text
📦 ai-attendance-project-app[cite: 2]
 ┣ 📜 app.py                      # Main application entry point & router[cite: 1]
 ┣ 📜 requirements.txt            # Python dependencies[cite: 3]
 ┣ 📂 src
 ┃ ┣ 📂 components                # Reusable UI elements & interactive dialogs
 ┃ ┃ ┣ 📜 dialog_attendance_results.py[cite: 4]
 ┃ ┃ ┣ 📜 dialog_auto_enroll.py       [cite: 5]
 ┃ ┃ ┣ 📜 dialog_create_subject.py    [cite: 6]
 ┃ ┃ ┣ 📜 dialog_enroll.py            [cite: 7]
 ┃ ┃ ┣ 📜 dialog_share_subject.py     [cite: 8]
 ┃ ┃ ┣ 📜 dialog_voice_attendance.py  [cite: 9]
 ┃ ┃ ┣ 📜 dialog_add_photo.py         [cite: 13]
 ┃ ┃ ┣ 📜 header.py & footer.py       [cite: 10, 11]
 ┃ ┃ ┗ 📜 subject_card.py             [cite: 12]
 ┃ ┣ 📂 database                  # Backend integration 
 ┃ ┃ ┣ 📜 config.py               # Supabase client initialization
 ┃ ┃ ┗ 📜 db.py                   # CRUD operations & bcrypt hashing
 ┃ ┣ 📂 pipelines                 # AI/ML logic
 ┃ ┃ ┣ 📜 face_pipeline.py        # dlib face embeddings & SVM classifier[cite: 16]
 ┃ ┃ ┗ 📜 voice_pipeline.py       # resemblyzer audio segmentation[cite: 17]
 ┃ ┣ 📂 screens                   # Core application views
 ┃ ┃ ┣ 📜 home_screen.py          # Portal selection[cite: 18]
 ┃ ┃ ┣ 📜 student_screen.py       # FaceID login & student dashboard[cite: 19]
 ┃ ┃ ┗ 📜 teacher_screen.py       # Attendance scanning & class management[cite: 20]
 ┃ ┗ 📂 ui                        
 ┃   ┗ 📜 base_layout.py          # Custom CSS definitions & theming[cite: 21]



