# Setting Keymaps Sync (VSCode + Antigravity IDE)

Repository ini digunakan untuk menyimpan dan menyinkronkan keybindings antar perangkat menggunakan Git dan Symbolic Link (Symlink).

## Struktur Repository

```text
Setting-keymaps/
└── keybindings.json
```

## Lokasi File

### Antigravity IDE

```text
C:\Users\<USERNAME>\AppData\Roaming\Antigravity IDE\keybindings.json
```

### VSCode

```text
C:\Users\<USERNAME>\AppData\Roaming\Code\User\keybindings.json
```

### Repository

```text
X:\Programs\Setting-keymaps\keybindings.json
```

---

## Langkah Awal

Clone repository:

```bash
git clone https://github.com/<USERNAME>/Setting-keymaps.git
```

Masuk ke folder repository:

```bash
cd X:\Programs\Setting-keymaps
```

---

# Menghubungkan Antigravity IDE

## 1. Backup file lama (opsional)

```cmd
copy "C:\Users\<USERNAME>\AppData\Roaming\Antigravity IDE\keybindings.json" ^
     "C:\Users\<USERNAME>\AppData\Roaming\Antigravity IDE\keybindings.backup.json"
```

## 2. Hapus file lama

```cmd
del "C:\Users\<USERNAME>\AppData\Roaming\Antigravity IDE\keybindings.json"
```

## 3. Buat symlink

Jalankan Command Prompt sebagai Administrator:

```
cd /d X:\Programs\Setting-keymaps
```
```cmd
mklink "%APPDATA%\Code\User\keybindings.json" "X:\Programs\Setting-keymaps\keybindings.json"
```

---

# Menghubungkan VSCode

## 1. Backup file lama (opsional)

```cmd
copy "%APPDATA%\Code\User\keybindings.json" ^
     "%APPDATA%\Code\User\keybindings.backup.json"
```

## 2. Hapus file lama

```cmd
del "%APPDATA%\Code\User\keybindings.json"
```

## 3. Buat symlink

Jalankan Command Prompt sebagai Administrator:

```cmd
mklink "%APPDATA%\Code\User\keybindings.json" ^
       "X:\Programs\Setting-keymaps\keybindings.json"
```

---

# Verifikasi

Cek apakah symlink berhasil dibuat:

```cmd
dir "C:\Users\<USERNAME>\AppData\Roaming\Antigravity IDE"
```

Output yang diharapkan:

```text
<SYMLINK> keybindings.json
```

Cek VSCode:

```cmd
dir "%APPDATA%\Code\User"
```

Output yang diharapkan:

```text
<SYMLINK> keybindings.json
```

---

# Git Workflow

Lihat perubahan:

```bash
git status
```

Commit:

```bash
git add .
git commit -m "update keybindings"
```

Push:

```bash
git push origin main
```

Pull di device lain:

```bash
git pull origin main
```

---

# Catatan

* Jalankan `mklink` menggunakan Command Prompt (Administrator).
* Jangan edit file symlink secara manual dari repository jika IDE sedang berjalan.
* Semua perubahan keybinding yang dilakukan dari VSCode atau Antigravity IDE akan langsung tersimpan ke file yang sama.
* Setelah clone repository di perangkat baru, symlink harus dibuat ulang karena symlink bersifat lokal terhadap sistem operasi.
