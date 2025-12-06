# 🌌 AnimeVerse

![Flutter](https://img.shields.io/badge/Flutter-3.0%2B-02569B?logo=flutter)
![Dart](https://img.shields.io/badge/Dart-3.0%2B-0175C2?logo=dart)
![Firebase](https://img.shields.io/badge/Firebase-Auth%20%26%20Firestore-FFCA28?logo=firebase)
![License](https://img.shields.io/badge/License-MIT-green)

**AnimeVerse** adalah aplikasi mobile modern berbasis Flutter yang dirancang untuk penggemar anime. Aplikasi ini memungkinkan pengguna menjelajahi database anime yang luas, mencari judul favorit, melihat detail mendalam, serta menyimpan koleksi pribadi ke cloud secara real-time.

Dibangun dengan prinsip **Clean Architecture**, aplikasi ini menggunakan **Provider** untuk manajemen state, **GoRouter** untuk navigasi yang efisien, dan terintegrasi penuh dengan ekosistem **Firebase**.

---

## 👤 Identitas Pengembang

| Atribut | Detail |
|---------|--------|
| **Nama** | Muhammad Aryasatya |
| **NIM** | 231401094 |
| **Lab** | 2 |

---

## 📸 Dokumentasi Aplikasi

### 🔐 Autentikasi
| Sign In | Sign Up |
|:-------:|:-------:|
| ![Sign In](documentation/signin.png) | ![Sign Up](documentation/signup.png) |
| *Login dengan Email/Google* | *Registrasi Akun Baru* |

### 🎬 Fitur Utama
| Home (Dashboard) | Pencarian & Filter | Detail Anime |
|:----------------:|:------------------:|:------------:|
| ![Home](documentation/home.png) | ![Search](documentation/search.png) | ![Detail](documentation/detail.png) |
| *Top Anime & Kategori* | *Cari Anime & Genre* | *Info Lengkap & Sinopsis* |

### 👤 User & Favorit
| List Favorit | Profil User |
|:------------:|:-----------:|
| ![Favorites](documentation/favorites.png) | ![Profile](documentation/profile.png) |
| *Koleksi Pribadi (Cloud)* | *Pengaturan Akun* |

---

## ✨ Fitur Utama

### 🔐 Autentikasi & Pengguna
- **Login & Register:** Autentikasi aman menggunakan Email & Password via Firebase Auth
- **Google Sign-In:** Login cepat satu ketukan menggunakan akun Google
- **Manajemen Profil:** Pengguna dapat mengubah password, melihat informasi akun, dan logout dengan aman

### 🎬 Eksplorasi Anime
- **Top Anime:** Menampilkan daftar anime terpopuler saat ini (menggunakan [Jikan API v4](https://jikan.moe/))
- **Pencarian Pintar:** Cari anime berdasarkan judul dengan fitur *debounce* untuk efisiensi API
- **Filter Genre:** Temukan anime berdasarkan kategori (Action, Adventure, Fantasy, dll)
- **Detail Lengkap:** Sinopsis, rating, jumlah episode, status tayang, dan trailer gambar

### ❤️ Favorit (Cloud Sync)
- **Simpan ke Favorit:** Menandai anime yang disukai
- **Sinkronisasi Real-time:** Data favorit disimpan di **Cloud Firestore**, sehingga tetap tersinkronisasi meskipun berganti perangkat

### 🎨 UI/UX Modern
- **Responsive Grid:** Tampilan kartu anime yang menyesuaikan ukuran layar (ponsel & tablet)
- **Glassmorphism:** Desain antarmuka transparan dan elegan dengan tema gelap
- **Optimasi Gambar:** Menggunakan *caching* gambar untuk menghemat kuota dan mempercepat loading

---

## 🛠️ Teknologi yang Digunakan

| Kategori | Teknologi / Library | Deskripsi |
|----------|---------------------|-----------|
| **Framework** | Flutter & Dart | SDK utama pengembangan aplikasi |
| **State Management** | Provider | Mengelola state aplikasi (AppState & Auth) |
| **Navigation** | GoRouter | Routing, deep linking, dan manajemen stack navigasi |
| **Backend** | Firebase Auth | Menangani registrasi dan login user |
| **Database** | Cloud Firestore | NoSQL Database untuk menyimpan data favorit user |
| **Data Source** | Jikan API (V4) | API publik unofficial MyAnimeList |
| **Network** | HTTP Package | Melakukan request REST API |
| **UI Components** | Cached Network Image | Menampilkan gambar dengan cache manager |

---

## 📂 Struktur Project

```
lib/
├── config/
│   └── routes.dart                  # Konfigurasi GoRouter dan Guard navigasi
├── models/
│   └── anime.dart                   # Data Model untuk objek Anime (JSON Serialization)
├── providers/
│   ├── app_state_provider.dart      # Logic utama data anime & interaksi UI
│   └── auth_provider.dart           # Logic autentikasi & bridge ke UI
├── repositories/
│   └── anime_repository.dart        # Layer komunikasi ke Jikan API
├── screens/
│   ├── detail_screen.dart           # Halaman detail anime
│   ├── favorite_screen.dart         # Halaman list favorit user
│   ├── home_screen.dart             # Dashboard utama
│   ├── profile_screen.dart          # Halaman profil & settings
│   ├── signin_screen.dart           # Halaman login
│   └── signup_screen.dart           # Halaman registrasi
├── services/
│   ├── auth/                        # Service layer untuk Firebase Auth
│   └── firestore_service.dart       # Service layer untuk Cloud Firestore
├── utils/
│   ├── snackbar_helper.dart         # Helper global untuk notifikasi
│   └── validators.dart              # Validasi input form (Regex Email, Password)
├── widgets/
│   ├── anime_card.dart              # Widget kartu anime grid
│   ├── anime_view.dart              # Layout grid responsif
│   ├── app_scaffold.dart            # Wrapper dasar halaman dengan background
│   ├── bottom_navigation_shell.dart # Navigasi bar bawah (Persistent)
│   ├── favorite_anime_card.dart     # Widget kartu list favorit
│   ├── genre_list.dart              # Horizontal list filter genre
│   ├── gradient_background.dart     # Background gradien aplikasi
│   └── profile_button.dart          # Tombol menu profil
└── main.dart                        # Entry point & inisialisasi App
```

---

## 🚀 Instalasi & Konfigurasi

### 📋 Prasyarat Sistem

Pastikan Anda telah menginstal:

- **Flutter SDK:** Versi 3.0 atau lebih baru
- **Java (JDK):** Versi 11 atau 17
- **IDE:** Android Studio atau VS Code (dengan ekstensi Flutter & Dart)
- **Emulator Android** atau **Perangkat Fisik** (dengan USB Debugging aktif)

### 📥 Step 1: Clone Repository

```bash
# Clone repository
git clone https://github.com/aryasatya2204/anime-verse.git

# Masuk ke folder project
cd anime-verse

# Install dependencies
flutter pub get
```

### 🔥 Step 2: Konfigurasi Firebase

#### 2.1 Buat Firebase Project

1. Buka [Firebase Console](https://console.firebase.google.com/)
2. Klik **"Add project"** dan buat project baru (contoh: **AnimeVerse**)
3. Ikuti wizard setup hingga selesai

#### 2.2 Tambahkan Android App

1. Di Firebase Console, klik **"Add app"** dan pilih **Android**
2. Masukkan informasi berikut:
    - **Package Name:** `com.example.project_lab`
      > ⚠️ **Penting:** Pastikan sesuai dengan `applicationId` di `android/app/build.gradle.kts`
    - **App Nickname:** AnimeVerse (opsional)
3. Klik **"Register app"**

#### 2.3 Download google-services.json

1. Download file **`google-services.json`** dari Firebase Console
2. Pindahkan file ke: `android/app/google-services.json`

```
android/
└── app/
    └── google-services.json  ← Letakkan di sini
```

#### 2.4 Aktifkan Firebase Authentication

1. Di Firebase Console, buka **Build > Authentication**
2. Klik tab **"Sign-in method"**
3. Aktifkan metode berikut:
    - ✅ **Email/Password**
    - ✅ **Google**

#### 2.5 Aktifkan Cloud Firestore

1. Di Firebase Console, buka **Build > Firestore Database**
2. Klik **"Create database"**
3. Pilih **Start in test mode** (untuk development)
4. Pilih lokasi server terdekat (contoh: **Singapore** atau **Jakarta**)
5. Klik **"Enable"**

### 🔐 Step 3: Konfigurasi Keystore (Signing)

#### 3.1 Buat File key.properties

Buat file baru `android/key.properties` dengan isi:

```properties
storePassword=your_keystore_password
keyPassword=your_key_password
keyAlias=upload
storeFile=../app/upload-keystore.jks
```

> 💡 **Ganti** `your_keystore_password` dan `your_key_password` dengan password Anda

#### 3.2 Generate Keystore (Jika Belum Punya)

Jalankan perintah berikut di terminal:

```bash
keytool -genkey -v -keystore android/app/upload-keystore.jks -keyalg RSA -keysize 2048 -validity 10000 -alias upload
```

Ikuti instruksi dan masukkan password yang sama dengan di `key.properties`.

### 🔑 Step 4: Daftarkan SHA-1 Fingerprint

> ⚠️ **Wajib untuk Google Sign-In!** Tanpa ini, Google login akan error.

#### 4.1 Dapatkan SHA-1

```bash
cd android
./gradlew signingReport
```

atau di Windows:

```bash
cd android
gradlew.bat signingReport
```

#### 4.2 Salin SHA-1

Cari bagian **Variant: release** dan salin kode **SHA1** (format: `AA:BB:CC:...`)

#### 4.3 Tambahkan ke Firebase

1. Buka **Firebase Console > Project Settings > General**
2. Scroll ke **Your apps** > Android app
3. Klik **"Add fingerprint"**
4. Paste SHA-1 yang telah disalin
5. Klik **"Save"**

> 💡 **Tips:** Daftarkan juga SHA-1 dari **Variant: debug** jika ingin test Google Sign-In di mode development

---

## 🏗️ Build APK

### Development Build (Debug)

```bash
flutter build apk --debug
```

### Production Build (Release)

```bash
flutter build apk --release
```

File APK akan tersimpan di:

```
build/app/outputs/flutter-apk/app-release.apk
```

---

## 📱 Instalasi APK ke Perangkat

### Metode 1: Via USB

1. Sambungkan HP ke komputer via USB
2. Aktifkan **USB Debugging** di HP
3. Jalankan:

```bash
flutter install
```

### Metode 2: Manual

1. Transfer file `app-release.apk` ke HP (via WhatsApp/Google Drive/USB)
2. Buka file di HP
3. Izinkan **"Install from Unknown Sources"** jika diminta
4. Klik **"Install"**

---

## 🐛 Troubleshooting

### ❌ Google Sign-In Error (Code 10 / DEVELOPER_ERROR)

**Solusi:**
- Pastikan SHA-1 sudah terdaftar di Firebase
- Download ulang `google-services.json` dan timpa yang lama
- Rebuild aplikasi: `flutter clean && flutter build apk --release`

### ❌ Firebase Connection Failed

**Solusi:**
- Cek apakah `google-services.json` ada di `android/app/`
- Pastikan package name di Firebase sama dengan di `build.gradle.kts`
- Sinkronkan gradle: `cd android && ./gradlew --refresh-dependencies`

### ❌ Keystore Error saat Build

**Solusi:**
- Periksa password di `key.properties` sudah benar
- Pastikan path `storeFile` mengarah ke file `.jks` yang valid

---

## 📄 Lisensi

Project ini menggunakan lisensi [MIT License](LICENSE).

---

## 🙏 Kontribusi

Kontribusi sangat diterima! Silakan fork repository ini dan submit pull request.

---

**Dibuat oleh Muhammad Aryasatya**