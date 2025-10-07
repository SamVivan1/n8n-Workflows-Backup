# ⚙️ Cadangan *Workflows* n8n ke GitHub

[**English Version**](https://www.google.com/search?q=%23-n8n-workflows-backup-to-github-english)

*Workflow* n8n ini berfungsi sebagai solusi **otomatis** dan **berkala** untuk membuat cadangan (*backup*) semua *workflow* aktif dari instans n8n Anda dan menyimpannya ke repositori GitHub ini.

Setiap *workflow* dicadangkan sebagai file `.json` individual, dan alur kerja akan secara cerdas membedakan antara membuat file baru dan memperbarui file yang sudah ada. Tujuannya adalah menjaga riwayat versi (*version history*) melalui *commit* di GitHub, memberikan Anda jaminan bahwa pekerjaan Anda selalu tersimpan dengan aman.

-----

## 🚀 Cara Kerja (Indo)

Alur kerja ini bekerja dalam tiga fase utama:

1.  **Persiapan Data:**
      * **Schedule Trigger:** Memicu *workflow* sesuai jadwal yang ditentukan (misalnya, setiap hari).
      * **Date Formatting:** Mengambil tanggal dan waktu saat ini (`dd-MM-yyyy/H:mm`) untuk digunakan dalam pesan *commit* GitHub (misalnya: `backup-07-10-2025/17:45`).
2.  **Pengambilan dan Pengecekan:**
      * **Retrieve Workflows [N8N]:** Menghubungkan ke instans n8n Anda sendiri untuk mengambil data JSON dari semua *workflow* aktif.
      * **List files from repository [GITHUB]:** Mengambil daftar semua file yang saat ini ada di repositori untuk perbandingan.
      * **Check if file exists:** Menggunakan *node* **IF** untuk membandingkan *workflow* baru dengan daftar file yang sudah ada di GitHub.
3.  **Aksi Cadangan (Backup Action):**
      * **Jika file ditemukan (True):** *Node* `Update file [GITHUB]` dijalankan untuk menimpa file `.json` yang sudah ada dengan versi terbaru.
      * **Jika file tidak ditemukan (False):** *Node* `Upload file [GITHUB]` dijalankan untuk membuat file `.json` baru di repositori.

-----

## 🛠️ Persyaratan dan Pengaturan (Indo)

Untuk menjalankan *workflow* ini, Anda memerlukan kredensial berikut:

### 1\. Kredensial n8n (API Key)

  * Buat **Kredensial API Key** yang menunjuk ke instans n8n Anda sendiri. Pastikan kredensial ini memiliki akses untuk `retrieve workflows`.
  * **Node yang Digunakan:** `Retrieve workflows [N8N]`.

### 2\. Kredensial GitHub (OAuth2)

  * Buat **Kredensial GitHub (OAuth2)**. Pastikan *token* OAuth Anda memiliki cakupan (*scope*) yang cukup untuk **membaca** dan **menulis** (`repo` scope) ke repositori ini.
  * **Nodes yang Digunakan:** `List files from repository [GITHUB]`, `Update file [GITHUB]`, dan `Upload file [GITHUB]`.

### Konfigurasi GitHub Nodes

Setelah kredensial ditambahkan, pastikan semua *node* GitHub dikonfigurasi dengan benar:

| Node | Parameter | Nilai yang Harus Anda Verifikasi |
| :--- | :--- | :--- |
| **Semua Node GitHub** | **Owner** | **SamVivan1** (Ganti dengan nama pengguna GitHub Anda) |
| **Semua Node GitHub** | **Repository** | **n8n-Workflows-Backup** (Ganti dengan nama repositori target Anda) |

-----

## 📺 Kredit dan Dukungan (Indo)

  * **Pembuat Asli *Workflow***: `SamVivan1`
  * **Video Panduan Lengkap:** Tonton panduan langkah demi langkah di [saluran YouTube pembuat](https://www.youtube.com/watch?v=dNuVuoPD0Jo) untuk detail konfigurasi.

-----

\<a id="-n8n-workflows-backup-to-github-english"\>\</a\>

# ⚙️ n8n Workflows Backup to GitHub (English)

[**Versi Indonesia**](https://www.google.com/search?q=%23-cadangan-workflows-n8n-ke-github)

This n8n *workflow* serves as an **automatic** and **periodic** solution to back up all active *workflows* from your n8n instance and store them in this GitHub repository.

Each *workflow* is backed up as an individual `.json` file. The workflow intelligently distinguishes between creating a new file and updating an existing one. Its main goal is to maintain version history via GitHub *commits*, providing assurance that your work is always securely saved.

-----

## 🚀 How It Works (English)

The workflow operates in three main phases:

1.  **Data Preparation:**
      * **Schedule Trigger:** Triggers the *workflow* based on a set schedule (e.g., daily).
      * **Date Formatting:** Retrieves the current date and time (`dd-MM-yyyy/H:mm`) to use in the GitHub *commit* message (e.g.: `backup-07-10-2025/17:45`).
2.  **Retrieval and Checking:**
      * **Retrieve Workflows [N8N]:** Connects to your own n8n instance to fetch the JSON data of all active *workflows*.
      * **List files from repository [GITHUB]:** Retrieves a list of all files currently existing in the repository for comparison.
      * **Check if file exists:** Uses an **IF** *node* to compare the new *workflow* name against the list of existing files on GitHub.
3.  **Backup Action:**
      * **If the file is found (True):** The `Update file [GITHUB]` *node* is executed to overwrite the existing `.json` file with the latest version.
      * **If the file is not found (False):** The `Upload file [GITHUB]` *node* is executed to create a new `.json` file in the repository.

-----

## 🛠️ Requirements and Setup (English)

To run this *workflow*, you will need the following credentials:

### 1\. n8n Credentials (API Key)

  * You must create an **API Key Credential** pointing to your own n8n instance. Ensure this credential has access to `retrieve workflows`.
  * **Node Required:** `Retrieve workflows [N8N]`.

### 2\. GitHub Credentials (OAuth2)

  * You must create a **GitHub (OAuth2) Credential**. Ensure your OAuth *token* has sufficient scope to **read** and **write** (`repo` scope) to this repository.
  * **Nodes Required:** `List files from repository [GITHUB]`, `Update file [GITHUB]`, and `Upload file [GITHUB]`.

### Configuring GitHub Nodes

Once credentials are added, ensure all GitHub *nodes* are configured correctly:

| Node | Parameter | Value You Must Verify |
| :--- | :--- | :--- |
| **All GitHub Nodes** | **Owner** | **SamVivan1** (Replace with your GitHub username) |
| **All GitHub Nodes** | **Repository** | **n8n-Workflows-Backup** (Replace with your target repository name) |

-----

## 📺 Credits and Support (English)

  * **Original Workflow Creator**: `SamVivan1`
  * **Complete Video Guide:** Watch the step-by-step guide on the [creator's YouTube channel](https://www.youtube.com/watch?v=dNuVuoPD0Jo) for credential configuration details.
