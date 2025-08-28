# AI Subtitle Translator (.ass) via Gemini API

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/rafiq8k-moga/Gemini-AI-Subtitle-Translator/blob/main/Subtitle_ass_Translator.ipynb)

Proyek ini adalah sebuah *tool* canggih untuk menerjemahkan file subtitle berformat Advanced SubStation Alpha (`.ass`) secara otomatis menggunakan kekuatan model AI generatif dari Google, yaitu Gemini.

Merupakan evolusi signifikan dari proyek sebelumnya, [`Gemini-TXT-Translator`](https://www.google.com/search?q=%5Bhttps://github.com/rafiq8k-moga/Gemini-TXT-Translator%5D\(https://github.com/rafiq8k-moga/Gemini-TXT-Translator\)), tool ini dirancang untuk mengatasi kelemahan utama dari versi lama. Sebelumnya di `Gemini-TXT-Translator`, proses terjemahan menggunakan sistem per baris pada file `.txt` biasa, sebuah proses yang bisa sangat melelahkan dan menghilangkan semua konteks format subtitle.

Aplikasi baru ini, yang dibangun dengan Gradio dan dirancang untuk berjalan di Google Colab, menghadirkan alur kerja yang cerdas, efisien, dan jauh lebih ramah pengguna.

## Kelebihan & Fitur Utama

Tool ini dibangun untuk merevolusi proses fansubbing dengan AI, berikut adalah keunggulannya:

  * **Pemahaman Format `.ass` Cerdas**: Tool ini secara cerdas mem-parsing file `.ass`, hanya mengambil teks dialog untuk diterjemahkan, sementara **menjaga semua metadata penting** seperti timing, style, positioning, dan efek tetap utuh.
  * **Context Summary (Ringkasan Konteks)**: Sebelum terjemahan, AI membuat ringkasan konteks dari episode sebelumnya dan episode saat ini agar hasil terjemahan lebih konsisten.
  * **Terjemahan Batch (Kelompok)**: Proses terjemahan tidak lagi dilakukan baris per baris. Aplikasi ini mengirimkan dialog dalam kelompok (misalnya, 100 baris per permintaan), membuatnya **jauh lebih cepat dan efisien** dalam menggunakan API.
  * **Antarmuka Web Interaktif (Gradio)**: Semua interaksi dilakukan melalui antarmuka web yang bersih dan intuitif langsung di dalam notebook Colab.
  * **Live Logging Real-time**: Sidebar "Live Log" memberi Anda **update status secara langsung** untuk setiap langkah, mulai dari pembuatan konteks hingga setiap batch yang selesai diterjemahkan.
  * **Kontrol Penuh atas AI**: Bisa memberikan **konteks** tambahan (nama karakter, istilah khusus, atau instruksi gaya bahasa) agar hasil terjemahan lebih akurat dan konsisten.
  * **Portabel dan Tanpa Setup**: Dijalankan sepenuhnya di **Google Colab**, tidak perlu instalasi Python atau library rumit di komputer.

## Panduan Penggunaan

Ikuti langkah-langkah sederhana ini untuk memulai.

### Langkah 0: Siapkan File Subtitle Anda

File `.ass` seringkali berisi baris-baris kompleks yang bukan merupakan dialog lisan, seperti template karaoke (KFX), motion graphic, atau *shape*.

Tool ini hanya akan menerjemahkan baris yang diawali dengan `Dialogue:`. Baris lain akan tetap utuh di file hasil akhir. Jika ada baris `Dialogue:` yang tidak ingin diterjemahkan, Anda bisa menandainya atau melewatinya.

### Langkah 1: Buka Notebook & Siapkan API Key

1. Buka notebook ini lewat tombol berikut: [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/rafiq8k-moga/Gemini-AI-Subtitle-Translator/blob/main/Subtitle_ass_Translator.ipynb)
2. Siapkan API Key Gemini Anda melalui fitur **Secrets** di Colab:
   * Klik ikon **kunci (🔑)** di sidebar kiri.
   * Klik **"Add a new secret"**.
   * **Name:** `GEMINI_API_KEY`
   * **Value:** Tempel API Key Anda.
   * Aktifkan tombol **"Notebook access"**.

### Langkah 2: Jalankan Sel Context

1. Jalankan sel **Context Maker** terlebih dahulu.  
   Sel ini akan:
   * Mengekstrak dialog dari file `.ass` episode saat ini.
   * Membaca konteks dari episode sebelumnya (jika ada).
   * Membuat **ringkasan konteks** yang akan digunakan AI agar terjemahan lebih konsisten.
2. Hasil ringkasan konteks akan muncul di antarmuka, dan bisa diunduh sebagai file `.txt`.

### Langkah 3: Jalankan Sel Translator

1. Setelah konteks siap, jalankan sel **Translator**.  
   Sel ini akan:
   * Mengirim dialog ke AI untuk diterjemahkan.
   * Menggunakan konteks dari langkah sebelumnya agar hasil terjemahan akurat dan konsisten.
2. Hasil terjemahan akan muncul di antarmuka dan bisa diunduh sebagai file `.ass` yang sudah diterjemahkan.

### Langkah 4: Unduh Hasil

Setelah proses selesai, tombol **Download** akan muncul untuk mendapatkan file `.ass` yang sudah diterjemahkan beserta file konteks (opsional).

## Perbandingan dengan Versi Lama (`Gemini-TXT-Translator`)

| Fitur                 | Gemini-TXT-Translator (Lama)                                             | AI Subtitle Translator (Baru)                                                              |
| :-------------------- | :----------------------------------------------------------------------- | :----------------------------------------------------------------------------------------- |
| **Proses Kerja** | Manual: Ekstrak dialog ke `.txt`, terjemahkan, lalu masukkan kembali.      | **Otomatis**: Unggah file `.ass`, buat konteks, terjemahkan, unduh file `.ass`.            |
| **Konteks Subtitle** | Semua timing, style, dan efek **hilang** saat diekstrak ke `.txt`.         | Semua timing, style, dan efek **100% terjaga**, plus **ringkasan konteks**.                |
| **Efisiensi** | Menerjemahkan **baris per baris**, sangat lambat dan banyak panggilan API. | Menerjemahkan dalam **batch (100 baris)**, lebih cepat dan efisien.                        |
| **Feedback Proses** | Tidak ada. Hanya bisa menunggu hingga semua baris selesai.                | **Live Log**: Memberikan update status untuk setiap langkah, termasuk pembuatan konteks.  |
| **Antarmuka** | Tidak ada. Proses berbasis file manual.                                  | **Antarmuka Web Interaktif** dari Gradio.                                                  |

## Teknologi yang Digunakan

  * **Python**
  * **Google Generative AI (Gemini API)**
  * **Gradio**
  * **Google Colab**
