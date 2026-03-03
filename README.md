# 🚀 CyberScrum Tracker (ProjectTrack)

CyberScrum Tracker adalah platform manajemen proyek berbasis web ringan yang dirancang khusus untuk mengadopsi kerangka kerja Agile/Scrum di lingkungan sekolah. Aplikasi ini berfungsi sebagai LMS (*Learning Management System*) mini yang memfasilitasi kolaborasi antara siswa dan guru (mentor) dengan antarmuka bertema *Cyberpunk / Retro-Futuristik*.

Sistem ini mengusung arsitektur *Serverless*, memanfaatkan **GitHub Pages** sebagai *frontend* statis dan **Google Apps Script (GAS)** sebagai jembatan *backend* / API menuju ekosistem Google Workspace (Google Sheets & Google Drive).

## ✨ Fitur Utama

* **🔐 Role-Based Access Control (RBAC):** Sistem otentikasi sederhana yang memisahkan hak akses, tampilan, dan kapabilitas antara `Guru` dan `Siswa`.
* **📌 Interaktif Scrum Board:** Papan *Kanban* dinamis dengan fitur *Drag-and-Drop* dan *Tap-to-Move* (Mobile Friendly) untuk melacak status tugas (*To Do, Work In Progress, Finished*).
* **📅 Sistem Penjadwalan Konsultasi:** Fitur kalender interaktif bagi siswa untuk mengajukan jadwal bimbingan. Guru dapat menyetujui atau memberikan jadwal pengganti (*reschedule*) secara langsung.
* **📂 Manajemen Dokumentasi Terpusat:** Integrasi langsung dengan Google Drive API yang memungkinkan siswa mengunggah bukti progres kerja (foto/dokumen) secara aman.
* **💬 Komunikasi Asinkron (Feedback):** Fitur komentar/obrolan bawaan pada setiap kartu tugas untuk memudahkan revisi dan diskusi tanpa harus menunggu tatap muka.
* **📊 Live Metrics & Grading:** *Dashboard* metrik persentase penyelesaian proyek (*Burndown Progress*) dan fitur penilaian langsung (0-100) oleh Guru pada tugas yang telah diselesaikan.

## 🛠️ Teknologi yang Digunakan

* **Frontend:** HTML5, CSS3 (Vanilla), JavaScript (ES6+), Fetch API.
* **Backend / API:** Google Apps Script (REST API via `doPost`).
* **Database:** Google Sheets.
* **Storage:** Google Drive.
* **Deployment:** GitHub Pages.

## ⚙️ Arsitektur Sistem

1. **Client-Side:** Aplikasi statis di-hosting di GitHub Pages. Mengirim *request* JSON melalui `fetch()` ke URL Web App Google Apps Script.
2. **Server-Side:** GAS menerima *request*, memproses logika bisnis (Otentikasi, CRUD Tugas, Modifikasi File), lalu berinteraksi dengan Google Sheets dan Google Drive.
3. **Response:** GAS mengembalikan respons dalam format JSON yang kemudian di-*render* ulang oleh antarmuka pengguna secara asinkron tanpa memuat ulang halaman.

## 🚀 Panduan Instalasi & Setup (Untuk Developer/Pengajar)

### 1. Setup Database (Google Sheets)
Buat Spreadsheet baru dan siapkan 5 *sheet* berikut:
* `Users` (Kolom: Username, Password, Role, JudulProject)
* `Tasks` (Kolom: TaskID, TaskName, Status, StartDate, EndDate, Assignee, Score)
* `Files` (Kolom: FileID, TaskID, FileName, FileURL, Uploader)
* `Consultations` (Kolom: ReqID, Kelompok, Tanggal, Status, PesanGuru)
* `Comments` (Kolom: CommentID, TaskID, Sender, Role, Timestamp, Message)

### 2. Setup Storage (Google Drive)
* Buat satu folder khusus di Google Drive untuk menyimpan *file* unggahan siswa.
* Salin **Folder ID** dari URL folder tersebut.

### 3. Setup Backend (Google Apps Script)
* Buka menu **Extensions > Apps Script** dari Google Sheets Anda.
* Salin seluruh kode *backend* ke `Code.gs`.
* Masukkan Folder ID ke dalam variabel `DRIVE_FOLDER_ID`.
* Lakukan **Deploy > New deployment** sebagai *Web App*.
* Set akses (*Who has access*) ke **"Anyone"**.
* Salin **Web App URL** yang dihasilkan.

### 4. Setup Frontend
* *Clone* repositori ini.
* Buka file `index.html`.
* Ganti nilai konstanta `GAS_URL` dengan Web App URL yang Anda dapatkan dari langkah 3.
* *Push* ke GitHub dan aktifkan **GitHub Pages**.

## 📱 Tangkapan Layar (Screenshots)
<img width="1891" height="869" alt="image" src="https://github.com/user-attachments/assets/c7c287c1-edd7-485c-b9f1-307de2c20d0e" />

*(Tambahkan gambar screenshot aplikasi Anda di sini dengan format: `![Deskripsi](link-gambar.png)`)*
* **Halaman Login & Otentikasi**
* **Dashboard Metrik & Scrum Board**
* **Panel Kalender Konsultasi**
* **Modal Detail Tugas & Fitur Chat**

## 👨‍🏫 Penulis & Pengembang

* **M. Aziz Al Assad, S.T., Gr.** * Dikembangkan untuk keperluan edukasi dan manajemen proyek siswa di SMA Gunung Madu / Warta Media (2026).

---
*Dibuat dengan 💻 dan ☕ untuk memajukan pendidikan Informatika.*
