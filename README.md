---

## 🚀 Deploy Ubuntu Server di Fly.io dengan GitHub Actions  

### **📌 Fitur:**
✅ Deploy **Ubuntu 22.04** di **Fly.io**  
✅ **Install paket dasar**, termasuk `build-essential`, `curl`, `git`, `vim`, `tmux`, dll.  
✅ **Setup SSH manual** dengan user `robby` dan password otomatis  
✅ **Public IP** untuk akses langsung  
✅ **Notifikasi Telegram** dengan info server  

---

## 🔧 **Instalasi & Penggunaan**  

### **1️⃣ Fork Repository Ini**
Klik tombol **Fork** di kanan atas untuk membuat salinan ke akun GitHub Anda.  

### **2️⃣ Tambahkan Secrets di GitHub**
Buka **Settings** → **Secrets and variables** → **Actions** → **New repository secret**  
Tambahkan dua secrets berikut:  

| Secret | Deskripsi |
|--------|-----------|
| `FLY_API_TOKEN` | API Token dari Fly.io |
| `TELEGRAM_BOT_TOKEN` | Token bot Telegram untuk notifikasi |
| `TELEGRAM_CHAT_ID` | ID chat Telegram Anda |

> **Catatan:**  
> - Untuk mendapatkan `FLY_API_TOKEN`, jalankan:  
>   ```sh
>   fly auth token
>   ```
> - Untuk `TELEGRAM_BOT_TOKEN`, buat bot di [@BotFather](https://t.me/BotFather).  
> - Untuk `TELEGRAM_CHAT_ID`, kirim pesan ke [@userinfobot](https://t.me/userinfobot).  

### **3️⃣ Jalankan Workflow di GitHub**
1. Buka tab **Actions**  
2. Pilih **Deploy Ubuntu Server to Fly.io**  
3. Klik **Run workflow**  

---

## 📜 **Detail Workflow**
**File:** `.github/workflows/deploy-ubuntu.yml`  

- **Membuat Fly.io App** jika belum ada  
- **Deploy Ubuntu 22.04** di Fly.io  
- **Install paket dasar**, termasuk:  
  ```sh
  build-essential software-properties-common
  ca-certificates locales wget curl git unzip zip tar
  nano vim screen htop neofetch tmux fail2ban ufw
  ```
- **Setup SSH user `robby`** dengan password acak  
- **Mengambil IP publik server**  
- **Kirim notifikasi Telegram** dengan detail login  

---

## 🔌 **Akses Server**
Setelah workflow selesai, Anda akan mendapat **notifikasi Telegram** berisi:  

```text
🖥️ Ubuntu Server Deployed!
🔹 IP: xxx.xxx.xxx.xxx
🔹 SSH User: robby
🔹 SSH Password: (password otomatis)
🔹 Installed: build-essential, curl, git, unzip, nano, vim, tmux, etc.
⚡️ Ready to use!
```

Gunakan perintah berikut untuk masuk ke server:  
```sh
ssh robby@xxx.xxx.xxx.xxx
```
Password ada di notifikasi Telegram.  

---

## 🎯 **Catatan**
- Pastikan akun Fly.io sudah aktif sebelum menjalankan workflow.  
- Bisa mengganti region Fly.io di workflow (`REGION="sin"`, `sjc`, `ams`, dll).  
- Bisa menambahkan paket lain sesuai kebutuhan di workflow.  

---

## ✨ **Kontribusi & Pengembangan**
Silakan **fork & pull request** jika ingin menambahkan fitur atau perbaikan! 🚀  

Happy coding! 🎉
