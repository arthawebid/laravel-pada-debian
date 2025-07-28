Untuk menginstal **Laravel** di **Debian**, kamu perlu menyiapkan beberapa komponen terlebih dahulu, termasuk PHP, Composer, dan (opsional) web server seperti Apache atau Nginx.

Berikut adalah langkah-langkah **lengkap dan terstruktur** untuk menginstal Laravel di Debian:

---

## ✅ **1. Prasyarat (Pastikan Sudah Terinstal)**

Laravel membutuhkan:

* PHP ≥ 8.1
* Composer
* Ekstensi PHP seperti: `mbstring`, `openssl`, `pdo`, `tokenizer`, `xml`, dll
* Web server (Apache/Nginx)
* Database (MySQL/PostgreSQL/SQLite)

---

## 🧱 **2. Instal PHP dan Ekstensi**

Jika belum, jalankan:

```bash
sudo apt update
sudo apt install php php-cli php-mbstring php-xml php-bcmath php-curl php-mysql php-zip unzip curl git -y
```

Cek versi PHP:

```bash
php -v
```

---

## 🛠️ **3. Install Composer (PHP Dependency Manager)**

```bash
curl -sS https://getcomposer.org/installer | php
sudo mv composer.phar /usr/local/bin/composer
```

Cek:

```bash
composer --version
```

---

## 🚀 **4. Instal Laravel (Via Composer)**

Kamu bisa install Laravel secara global atau langsung buat proyek.

### 🔹 Cara 1: Instal Global Laravel Installer

```bash
composer global require laravel/installer
```

Tambahkan Composer global bin ke PATH:

```bash
echo 'export PATH="$HOME/.config/composer/vendor/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

Lalu buat proyek baru:

```bash
laravel new nama-proyek
cd nama-proyek
php artisan serve
```

### 🔹 Cara 2: Install Laravel Langsung (tanpa installer)

```bash
composer create-project laravel/laravel nama-proyek
cd nama-proyek
php artisan serve
```

---

## 🌐 **5. Konfigurasi Web Server (Opsional)**

### 🔸 Jika Pakai Apache:

Install:

```bash
sudo apt install apache2 libapache2-mod-php
```

Buat virtual host:

```bash
sudo nano /etc/apache2/sites-available/laravel.conf
```

Isi:

```apache
<VirtualHost *:80>
    ServerName laravel.test
    DocumentRoot /path/ke/nama-proyek/public

    <Directory /path/ke/nama-proyek/public>
        AllowOverride All
        Require all granted
    </Directory>
</VirtualHost>
```

Aktifkan:

```bash
sudo a2ensite laravel
sudo a2enmod rewrite
sudo systemctl reload apache2
```

Tambahkan ke `/etc/hosts`:

```
127.0.0.1   laravel.test
```

---

## 🧪 **6. Uji Aplikasi**

Jalankan:

```bash
php artisan serve
```

Akses di browser:

```
http://127.0.0.1:8000
```

---

Kalau kamu ingin bantuan menghubungkan Laravel ke MySQL, mengatur `.env`, atau menjalankan dengan Nginx, tinggal bilang aja ya!
