# Flutter + FastAPI + SQLite Project

Proyek ini merupakan integrasi antara:

* Flutter (Frontend Mobile App)
* FastAPI (Backend API)
* SQLite (Database lokal)

---

# Struktur Project

```
register_system/
│
├── backend/
│   ├── main.py
│   ├── cek.py
│   └── flutter_app/
│       └── lib/main.dart
```

---

# Requirements

Pastikan sudah terinstall:

* Flutter SDK
* Python 3.8+
* pip
* uvicorn

---

# Cara Menjalankan Aplikasi

## 1. Menjalankan Flutter App

```
cd register_system/backend/flutter_app
flutter pub get
flutter run lib/main.dart
```

---

## 2. Menjalankan Backend (FastAPI)

Buka terminal baru:

```
cd register_system/backend
uvicorn main:app --reload
```

API akan berjalan di:

```
http://127.0.0.1:8000
```

---

## 3. Testing Python Script

Untuk mengecek script:

```
python cek.py
```

---

# CI/CD dengan Jenkins

Project ini dapat diintegrasikan dengan Jenkins untuk otomatisasi build APK.

## Flow CI/CD

1. Jenkins clone repository
2. Build Flutter APK
3. Archive hasil build

## Contoh Pipeline

```
pipeline {
    agent any

    stages {
        stage('Build APK') {
            steps {
                dir('register_system/backend/flutter_app') {
                    sh 'flutter pub get'
                    sh 'flutter build apk --release'
                }
            }
        }
    }
}
```

---

# Output Build

File APK akan berada di:

```
build/app/outputs/flutter-apk/
```

---

# Notes

* Pastikan Flutter sudah terdeteksi:

  ```
  flutter doctor
  ```
* Pastikan environment Jenkins sudah memiliki:

  * Flutter SDK
  * Android SDK
  * Java

---

# Tips

Gunakan `.gitignore` untuk menghindari file besar:

* build/
* .venv/
* *.apk

---

# Author

Aqshal Nur Ikhsan
