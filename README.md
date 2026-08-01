# 🎓 SnapClass – AI Powered Attendance System

SnapClass is an AI-powered attendance management system that automates classroom attendance using **Face Recognition** and **Voice Recognition**. Built with **Streamlit**, **Supabase**, **Dlib**, and **Resemblyzer**, it provides separate portals for teachers and students while eliminating manual attendance.

---

# ✨ Features

## 👨‍🏫 Teacher Portal

- Teacher Registration & Login
- Create and manage subjects
- Generate subject join links & QR codes
- Take attendance using:
  - Face Recognition
  - Voice Recognition
- Review attendance before saving
- Attendance reports
- Manage enrolled students

---

## 👨‍🎓 Student Portal

- Student registration
- Face enrollment
- Voice enrollment
- Join subjects using:
  - Subject Code
  - QR Code
  - Shared Join Link
- View enrolled subjects
- View attendance statistics
- Unenroll from subjects

---

# 🧠 AI Modules

## Face Recognition

The face recognition pipeline uses:

- Dlib Face Detector
- Dlib Face Landmark Predictor
- Dlib Face Recognition Model (128-D embeddings)
- Support Vector Machine (SVM) classifier

### Workflow

1. Capture student face
2. Generate 128-dimensional embedding
3. Store embedding in Supabase
4. Train SVM classifier
5. During attendance:
   - Detect faces
   - Generate embeddings
   - Predict student identity
   - Verify similarity using Euclidean Distance

---

## Voice Recognition

Voice attendance uses:

- Resemblyzer
- Librosa

### Workflow

1. Student records voice during enrollment
2. Generate speaker embedding
3. Store embedding
4. During attendance:
   - Split audio into speech segments
   - Generate embeddings
   - Compare with enrolled students
   - Mark attendance based on cosine similarity

---

# 📁 Project Structure

```
ai-attendance-project-app/
│
├── app.py
├── requirements.txt
│
├── src/
│   ├── components/
│   ├── database/
│   ├── pipelines/
│   ├── screens/
│   └── ui/
```

## Components

Contains reusable Streamlit dialogs and UI components such as:

- Subject cards
- Attendance confirmation dialog
- Student enrollment dialog
- QR code sharing
- Face enrollment
- Voice attendance
- Header/Footer

---

## Database

Uses **Supabase** as backend.

Handles:

- Teacher accounts
- Student accounts
- Subjects
- Attendance logs
- Student enrollment

Authentication uses **bcrypt** password hashing.

---

## Pipelines

### face_pipeline.py

Responsible for

- Face detection
- Face embedding extraction
- SVM training
- Student prediction

---

### voice_pipeline.py

Responsible for

- Voice embedding generation
- Speaker identification
- Bulk classroom audio processing

---

## Screens

### Home Screen

Landing page allowing users to choose:

- Student Portal
- Teacher Portal

---

### Teacher Dashboard

Teachers can:

- Create subjects
- Share QR codes
- Take attendance
- View reports
- Manage classes

---

### Student Dashboard

Students can:

- Join classes
- Enroll face
- Enroll voice
- View attendance
- Leave subjects

---

# 🗄 Database (Supabase)

The application stores data in Supabase.

Main tables include:

- teachers
- students
- subjects
- subject_students
- attendance_logs

Student records include:

- Face embedding
- Voice embedding

Attendance logs store:

- Student ID
- Subject ID
- Timestamp
- Present / Absent status

---

# ⚙️ Technologies Used

### Frontend

- Streamlit

### Backend

- Python

### Database

- Supabase

### Face Recognition

- Dlib
- face_recognition_models
- NumPy
- Scikit-Learn

### Voice Recognition

- Resemblyzer
- Librosa

### Authentication

- bcrypt

### QR Code Generation

- Segno

---

# 🚀 Installation

## Clone Repository

```bash
git clone https://github.com/yourusername/snapclass.git

cd snapclass
```

---

## Install Dependencies

```bash
pip install -r requirements.txt
```

---

## Configure Supabase

Create a `.streamlit/secrets.toml` file.

```toml
SUPABASE_URL="YOUR_SUPABASE_URL"

SUPABASE_KEY="YOUR_SUPABASE_KEY"
```

---

## Run the Application

```bash
streamlit run app.py
```

---

# 📷 Attendance Workflow

### Student Enrollment

```
Student
    │
Capture Face
    │
Generate Face Embedding
    │
Store in Database
```

```
Student
    │
Record Voice
    │
Generate Voice Embedding
    │
Store in Database
```

---

### Face Attendance

```
Class Image
      │
Face Detection
      │
Generate Embeddings
      │
SVM Prediction
      │
Verify Similarity
      │
Attendance List
```

---

### Voice Attendance

```
Audio Recording
        │
Speech Segmentation
        │
Voice Embeddings
        │
Speaker Identification
        │
Attendance List
```

---

# 🔒 Security

- Passwords hashed using bcrypt
- Face embeddings stored instead of images
- Voice embeddings stored instead of raw voice samples
- Teacher authentication before attendance management

---

# 📦 Major Libraries

- Streamlit
- NumPy
- Pandas
- Dlib
- face_recognition_models
- Scikit-learn
- Supabase
- bcrypt
- Segno
- Pillow
- Librosa
- Resemblyzer

---

# 📌 Future Improvements

- Multi-face live webcam attendance
- Liveness detection to prevent spoofing
- Face + Voice multimodal verification
- Attendance analytics dashboard
- Export attendance to Excel/PDF
- Email notifications
- Mobile application
- Real-time attendance monitoring
- Role-based administration
- Cloud deployment with CI/CD

---

# 👨‍💻 Developed With

- Python
- Streamlit
- Supabase
- Dlib
- Resemblyzer

Built to make classroom attendance faster, smarter, and more secure using Artificial Intelligence.
