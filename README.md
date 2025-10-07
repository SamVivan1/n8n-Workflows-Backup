# ⚙️ Cadangan *Workflows* n8n ke GitHub

| [**Lompat ke Versi Inggris**](https://www.google.com/search?q=%23english-version) | [**Lompat ke Pengaturan**](https://www.google.com/search?q=%23pengaturan-indo) | [**Lompat ke Cara Kerja**](https://www.google.com/search?q=%23cara-kerja-indo) |
| :--- | :--- | :--- |

*Workflow* n8n ini berfungsi sebagai solusi **otomatis** dan **berkala** untuk membuat cadangan (*backup*) semua *workflow* aktif dari instans n8n Anda dan menyimpannya ke repositori GitHub ini.

Setiap *workflow* dicadangkan sebagai file `.json` individual, dan alur kerja akan secara cerdas membedakan antara membuat file baru dan memperbarui file yang sudah ada. Tujuannya adalah menjaga riwayat versi (*version history*) melalui *commit* di GitHub, memberikan Anda jaminan bahwa pekerjaan Anda selalu tersimpan dengan aman.

-----

\<a id="cara-kerja-indo"\>\</a\>

## 🚀 Cara Kerja (Indo)

Alur kerja ini bekerja dalam tiga fase utama:

1.  **Persiapan Data:** Memicu *workflow* sesuai jadwal dan mengambil tanggal/waktu saat ini (`dd-MM-yyyy/H:mm`) untuk digunakan dalam pesan *commit* GitHub (misalnya: `backup-07-10-2025/17:45`).
2.  **Pengambilan dan Pengecekan:**
      * **Retrieve Workflows [N8N]:** Mengambil data JSON dari semua *workflow* aktif di instans Anda.
      * **List files from repository [GITHUB]:** Mengambil daftar file yang sudah ada di repositori.
      * **Check if file exists:** Menggunakan *node* **IF** untuk membandingkan *workflow* baru dengan daftar file yang sudah ada di GitHub.
3.  **Aksi Cadangan (Backup Action):**
      * **Jika file ditemukan (True):** *Node* `Update file [GITHUB]` menimpa file `.json` yang sudah ada dengan versi terbaru.
      * **Jika file tidak ditemukan (False):** *Node* `Upload file [GITHUB]` membuat file `.json` baru di repositori.

-----

\<a id="pengaturan-indo"\>\</a\>

## 🛠️ Persyaratan dan Pengaturan (Indo)

Anda memerlukan dua jenis kredensial di n8n:

### 1\. Kredensial n8n (API Key)

  * Buat **Kredensial API Key** yang menunjuk ke instans n8n Anda sendiri.
  * **Node yang Digunakan:** `Retrieve workflows [N8N]`.

### 2\. Kredensial GitHub (OAuth2)

  * Buat **Kredensial GitHub (OAuth2)** dengan cakupan (*scope*) yang cukup untuk **membaca** dan **menulis** (`repo` scope) ke repositori.
  * **Nodes yang Digunakan:** Semua node GitHub.

### Konfigurasi GitHub Nodes

Pastikan semua *node* GitHub (List, Update, Upload) dikonfigurasi dengan informasi yang benar:

| Node | Parameter | Nilai yang Harus Anda Verifikasi |
| :--- | :--- | :--- |
| **Semua Node GitHub** | **Owner** | **SamVivan1** (Ganti dengan nama pengguna GitHub Anda) |
| **Semua Node GitHub** | **Repository** | **n8n-Workflows-Backup** (Ganti dengan nama repositori target Anda) |

-----

-----

\<a id="english-version"\>\</a\>

# ⚙️ n8n Workflows Backup to GitHub (English)

| [**Jump to Indonesian Version**](https://www.google.com/search?q=%23-cadangan-workflows-n8n-ke-github) | [**Jump to Setup**](https://www.google.com/search?q=%23setup-english) | [**Jump to How It Works**](https://www.google.com/search?q=%23how-it-works-english) |
| :--- | :--- | :--- |

This n8n *workflow* serves as an **automatic** and **periodic** solution to back up all active *workflows* from your n8n instance and store them in this GitHub repository.

Each *workflow* is backed up as an individual `.json` file. The workflow intelligently distinguishes between creating a new file and updating an existing one. Its main goal is to maintain version history via GitHub *commits*, providing assurance that your work is always securely saved.

-----

\<a id="how-it-works-english"\>\</a\>

## 🚀 How It Works (English)

The workflow operates in three main phases:

1.  **Data Preparation:** Triggers the *workflow* based on a set schedule and retrieves the current date and time (`dd-MM-yyyy/H:mm`) for use in the GitHub *commit* message (e.g.: `backup-07-10-2025/17:45`).
2.  **Retrieval and Checking:**
      * **Retrieve Workflows [N8N]:** Fetches the JSON data of all active *workflows* from your instance.
      * **List files from repository [GITHUB]:** Retrieves a list of all files currently existing in the repository.
      * **Check if file exists:** Uses an **IF** *node* to compare the new *workflow* name against the list of existing files on GitHub.
3.  **Backup Action:**
      * **If the file is found (True):** The `Update file [GITHUB]` *node* is executed to overwrite the existing `.json` file with the latest version.
      * **If the file is not found (False):** The `Upload file [GITHUB]` *node* is executed to create a new `.json` file in the repository.

-----

\<a id="setup-english"\>\</a\>

## 🛠️ Requirements and Setup (English)

You will need two types of credentials in n8n:

### 1\. n8n Credentials (API Key)

  * You must create an **API Key Credential** pointing to your own n8n instance.
  * **Node Required:** `Retrieve workflows [N8N]`.

### 2\. GitHub Credentials (OAuth2)

  * You must create a **GitHub (OAuth2) Credential**. Ensure your OAuth *token* has sufficient scope to **read** and **write** (`repo` scope) to this repository.
  * **Nodes Required:** All GitHub nodes.

### Configuring GitHub Nodes

Once credentials are added, ensure all GitHub *nodes* are configured with the correct information:

| Node | Parameter | Value You Must Verify |
| :--- | :--- | :--- |
| **All GitHub Nodes** | **Owner** | **SamVivan1** (Replace with your GitHub username) |
| **All GitHub Nodes** | **Repository** | **n8n-Workflows-Backup** (Replace with your target repository name) |

-----

## 📺 Credits and Support (English)

  * **Original Workflow Creator**: `SamVivan1`
  * **Complete Video Guide:** Watch the step-by-step guide on the [creator's YouTube channel](https://www.youtube.com/watch?v=dNuVuoPD0Jo) for credential configuration details.
