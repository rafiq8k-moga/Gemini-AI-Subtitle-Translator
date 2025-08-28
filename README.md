# AI Subtitle Translator (.ass) via Gemini API

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/rafiq8k-moga/Gemini-AI-Subtitle-Translator/blob/main/Subtitle_ass_Translator.ipynb)

Proyek ini adalah sebuah *tool* canggih untuk menerjemahkan file subtitle berformat Advanced SubStation Alpha (`.ass`) secara otomatis menggunakan kekuatan model AI generatif dari Google, yaitu Gemini.

Merupakan evolusi signifikan dari proyek sebelumnya, [`Gemini-TXT-Translator`](https://www.google.com/search?q=%5Bhttps://github.com/rafiq8k-moga/Gemini-TXT-Translator%5D\(https://github.com/rafiq8k-moga/Gemini-TXT-Translator\)), tool ini dirancang untuk mengatasi kelemahan utama dari versi lama. Sebelumnya di `Gemini-TXT-Translator`, proses terjemahan menggunakan sistem per baris pada file `.txt` biasa, sebuah proses yang bisa sangat melelahkan dan menghilangkan semua konteks format subtitle.

Aplikasi baru ini, yang dibangun dengan Gradio dan dirancang untuk berjalan di Google Colab, menghadirkan alur kerja yang cerdas, efisien, dan jauh lebih ramah pengguna.

## Kelebihan & Fitur Utama

Tool ini dibangun untuk merevolusi proses fansubbing dengan AI, berikut adalah keunggulannya:

  * **Pemahaman Format `.ass` Cerdas**: Tool ini mem-parsing file `.ass` dan hanya mengambil teks dialog untuk diterjemahkan, **menjaga semua metadata penting** seperti timing, style, positioning, dan efek tetap utuh.
  * **Konteks Episode**: Anda dapat membuat **ringkasan konteks dari episode sebelumnya** sehingga AI lebih konsisten dalam menerjemahkan episode selanjutnya.
  * **Terjemahan Batch (Kelompok)**: Proses terjemahan tidak lagi dilakukan baris per baris. Dialog dikirim dalam kelompok (misalnya, 100 baris per permintaan), membuatnya **lebih cepat dan efisien**.
  * **Antarmuka Web Interaktif (Gradio)**: Semua interaksi dilakukan melalui antarmuka web yang bersih langsung di Colab.
  * **Live Logging Real-time**: Sidebar "Live Log" menampilkan update status setiap langkah, mulai dari membaca file hingga batch selesai diterjemahkan.
  * **Kontrol Penuh atas AI**: Anda bisa memberikan **konteks** (nama karakter, istilah khusus) dan **instruksi tambahan** untuk hasil terjemahan lebih akurat.
  * **Portabel dan Tanpa Setup**: Dijalankan sepenuhnya di **Google Colab**, tanpa perlu instalasi Python atau library tambahan.

## Panduan Penggunaan

Ikuti langkah-langkah sederhana ini untuk memulai.

### Langkah 0: (Penting) Siapkan File Subtitle Anda

File `.ass` seringkali berisi baris-baris kompleks yang bukan dialog lisan, seperti template karaoke (KFX), motion graphic, atau *shape*.  

Parser tool ini **hanya akan menerjemahkan baris yang diawali `Dialogue:`**, baris lain akan tetap ada di file hasil akhir.  

Jika ada baris `Dialogue:` yang tidak ingin diterjemahkan, bisa diabaikan manual di editor subtitle seperti **Aegisub**.

### Langkah 1: Jalankan Cell Context

Sebelum menerjemahkan, **jalankan cell Context** untuk membuat ringkasan konteks dari episode sebelumnya.  
Ini penting agar AI memahami alur cerita, karakter, dan istilah khusus sebelum menerjemahkan episode baru.  

1. Unggah file `.ass` episode saat ini.
2. Opsional: unggah file `.txt` konteks episode sebelumnya.
3. Pilih model AI.
4. Isi instruksi tambahan (opsional).
5. Klik **Buat Konteks**. Hasil ringkasan akan muncul dan bisa diunduh.

### Langkah 2: Jalankan Cell Translator

Setelah konteks dibuat, jalankan cell Translator untuk menerjemahkan episode.  

1. Unggah file `.ass` episode yang sama.
2. Pilih bahasa sumber dan target.
3. Pilih model AI.
4. Opsional: masukkan ringkasan konteks dari Langkah 1.
5. Klik **Mulai Terjemahkan**.
6. Saksikan proses live di sidebar log dan unduh file `.ass` hasil terjemahan setelah selesai.

## Perbandingan dengan Versi Lama (`Gemini-TXT-Translator`)

| Fitur                 | Gemini-TXT-Translator (Lama)                                             | AI Subtitle Translator (Baru)                                                              |
| :-------------------- | :----------------------------------------------------------------------- | :----------------------------------------------------------------------------------------- |
| **Proses Kerja** | Manual: Ekstrak dialog ke `.txt`, terjemahkan, lalu masukkan kembali.      | **Otomatis**: Unggah file `.ass`, terjemahkan, dan unduh file `.ass` yang sudah jadi.      |
| **Konteks Subtitle** | Semua timing, style, dan efek **hilang** saat diekstrak ke `.txt`.         | Semua timing, style, dan efek **100% terjaga**. Bisa menambahkan **konteks episode**.     |
| **Efisiensi** | Menerjemahkan **baris per baris**, lambat dan banyak panggilan API. | Terjemahkan dalam **batch**, lebih cepat dan efisien.                                       |
| **Feedback Proses** | Tidak ada. | **Live Log**: Memberikan update status untuk setiap langkah.                               |
| **Antarmuka** | Tidak ada. | **Antarmuka Web Interaktif** dari Gradio.                                                  |

## Teknologi yang Digunakan

  * **Python**
  * **Google Generative AI (Gemini API)**
  * **Gradio**
  * **Google Colab**
