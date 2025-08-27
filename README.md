# AI Subtitle Translator (.ass) via Gemini API

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/rafiq8k-moga/Gemini-AI-Subtitle-Translator/blob/main/Subtitle_ass_Translator.ipynb)

Proyek ini adalah sebuah *tool* canggih untuk menerjemahkan file subtitle berformat Advanced SubStation Alpha (`.ass`) secara otomatis menggunakan kekuatan model AI generatif dari Google, yaitu Gemini.

Merupakan evolusi signifikan dari proyek sebelumnya, [`Gemini-TXT-Translator`](https://www.google.com/search?q=%5Bhttps://github.com/rafiq8k-moga/Gemini-TXT-Translator%5D\(https://github.com/rafiq8k-moga/Gemini-TXT-Translator\)), tool ini dirancang untuk mengatasi kelemahan utama dari versi lama. Sebelumnya di `Gemini-TXT-Translator`, proses terjemahan menggunakan sistem per baris pada file `.txt` biasa, sebuah proses yang bisa sangat melelahkan dan menghilangkan semua konteks format subtitle.

Aplikasi baru ini, yang dibangun dengan Gradio dan dirancang untuk berjalan di Google Colab, menghadirkan alur kerja yang cerdas, efisien, dan jauh lebih ramah pengguna.

## Kelebihan & Fitur Utama

Tool ini dibangun untuk merevolusi proses fansubbing dengan AI, berikut adalah keunggulannya:

  * **Pemahaman Format `.ass` Cerdas**: Tidak seperti versi sebelumnya, tool ini secara cerdas mem-parsing file `.ass`, hanya mengambil teks dialog untuk diterjemahkan, sementara **menjaga semua metadata penting** seperti timing, style, positioning, dan efek tetap utuh.
  * **Terjemahan Batch (Kelompok)**: Proses terjemahan tidak lagi dilakukan baris per baris. Aplikasi ini mengirimkan dialog dalam kelompok (misalnya, 100 baris per permintaan), membuatnya **jauh lebih cepat dan efisien** dalam menggunakan API.
  * **Antarmuka Web Interaktif (Gradio)**: Lupakan proses manual salin-tempel ke file teks. Semua interaksi dilakukan melalui antarmuka web yang bersih dan intuitif langsung di dalam notebook Colab.
  * **Live Logging Real-time**: Anda tidak akan lagi bertanya-tanya apakah prosesnya berjalan atau tidak. Sidebar "Live Log" akan memberi Anda **update status secara langsung** untuk setiap langkah, mulai dari membaca file hingga setiap batch yang selesai diterjemahkan.
  * **Kontrol Penuh atas AI**: Anda bisa memberikan **konteks** (seperti nama karakter atau istilah khusus) dan **instruksi gaya bahasa** untuk mengarahkan AI agar menghasilkan terjemahan yang lebih akurat dan konsisten.
  * **Portabel dan Tanpa Setup**: Dijalankan sepenuhnya di **Google Colab**, Anda tidak perlu melakukan instalasi Python atau library yang rumit di komputer Anda. Cukup buka, jalankan, dan gunakan.

## Panduan Penggunaan

Ikuti langkah-langkah sederhana ini untuk memulai.

### Langkah 0: (Penting) Siapkan File Subtitle Anda

File `.ass` seringkali berisi baris-baris kompleks yang bukan merupakan dialog lisan, seperti template karaoke (KFX), motion graphic, atau *shape*.

**Kabar baiknya, parser di tool ini sudah cukup cerdas.** Ia secara spesifik hanya akan mencari dan menerjemahkan baris yang diawali dengan `Dialogue:`. Baris lain akan diabaikan oleh proses terjemahan dan akan tetap ada di file hasil akhir, sehingga semua efek visual Anda aman.

Namun, jika ada baris `Dialogue:` yang berisi kode atau teks yang tidak ingin Anda terjemahkan (misalnya, teks pada papan tanda atau efek khusus), Anda bisa dengan mudah menyuruh tool ini untuk melewatinya.

**Caranya:** Buka file `.ass` Anda di editor subtitle (seperti Aegisub),![Capture.PNG](https://raw.githubusercontent.com/rafiq8k-moga/Gemini-AI-Subtitle-Translator/refs/heads/main/comment.png)

Dengan begitu, Anda bisa memastikan hanya dialog yang relevan yang akan dikirim ke AI.

### Langkah 1: Buka Notebook & Siapkan API Key

1.  Buka notebook ini lewat tombol berikut [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/rafiq8k-moga/Gemini-AI-Subtitle-Translator/blob/main/Subtitle_ass_Translator.ipynb)
.
2.  Siapkan API Key Gemini Anda. Cara paling aman adalah menggunakan fitur **Secrets** di Colab:
      * Klik ikon **kunci (🔑)** di sidebar kiri.
      * Klik **"Add a new secret"**.
      * **Name:** `GEMINI_API_KEY`
      * **Value:** Tempel API Key Anda di sini.
      * Nyalakan tombol **"Notebook access"**.

### Langkah 2: Jalankan Semua Sel

Jalankan sel-sel di notebook secara berurutan dari atas ke bawah, dimulai dari sel instalasi hingga sel terakhir yang akan meluncurkan aplikasi Gradio.

### Langkah 3: Gunakan Antarmuka Gradio

Setelah sel terakhir dijalankan, sebuah antarmuka web akan muncul. Gunakan URL publik yang tersedia untuk membukanya di tab baru.

1.  **Unggah File**: Klik dan pilih file `.ass` yang ingin Anda terjemahkan.
2.  **Atur Bahasa**: Tentukan bahasa sumber dan target.
3.  **Pilih Model**: Pilih model AI yang ingin digunakan. "2.0 Flash" direkomendasikan untuk pengguna gratis karena batas kuotanya lebih longgar.
4.  **Isi Konteks & Instruksi (Opsional)**: Berikan informasi tambahan kepada AI untuk hasil yang lebih baik.
5.  **Mulai Terjemahkan**: Klik tombolnya dan saksikan prosesnya berjalan secara real-time di sidebar log.
6.  **Unduh Hasil**: Setelah proses selesai, sebuah tombol unduh akan muncul secara otomatis.

## Perbandingan dengan Versi Lama (`Gemini-TXT-Translator`)

| Fitur                 | Gemini-TXT-Translator (Lama)                                             | AI Subtitle Translator (Baru)                                                              |
| :-------------------- | :----------------------------------------------------------------------- | :----------------------------------------------------------------------------------------- |
| **Proses Kerja** | Manual: Ekstrak dialog ke `.txt`, terjemahkan, lalu masukkan kembali.      | **Otomatis**: Unggah file `.ass`, terjemahkan, dan unduh file `.ass` yang sudah jadi.      |
| **Konteks Subtitle** | Semua timing, style, dan efek **hilang** saat diekstrak ke `.txt`.         | Semua timing, style, dan efek **100% terjaga**.                                            |
| **Efisiensi** | Menerjemahkan **baris per baris**, sangat lambat dan banyak panggilan API. | Menerjemahkan dalam **batch (100 baris)**, lebih cepat dan efisien.                        |
| **Feedback Proses** | Tidak ada. Hanya bisa menunggu hingga semua baris selesai.                | **Live Log**: Memberikan update status untuk setiap langkah.                               |
| **Antarmuka** | Tidak ada. Proses berbasis file manual.                                  | **Antarmuka Web Interaktif** dari Gradio.                                                  |

## Teknologi yang Digunakan

  * **Python**
  * **Google Generative AI (Gemini API)**
  * **Gradio**
  * **Google Colab**
