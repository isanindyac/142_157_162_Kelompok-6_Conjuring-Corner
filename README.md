# 142_157_162_Kelompok-6_Conjuring-Corner
Website ini dapat menampilkan review dari seluruh universal film The Conjuring dan dapat menambahkan input review dari pengguna.

Berikut contoh **README.md** yang cocok untuk menjelaskan isi dan fungsi file `index.html` kamu agar terlihat profesional di GitHub 👇

---

# 🕯️ The Conjuring Universe Reviews — Landing Page

Proyek ini merupakan halaman beranda (`index.html`) dari situs **The Conjuring Universe Reviews**, sebuah website bertema horor yang membahas dan mengulas film-film dalam **The Conjuring Universe** secara estetis dan responsif.

---

## 📄 Deskripsi Umum

File `index.html` berfungsi sebagai **halaman utama** website. Halaman ini menampilkan pengenalan singkat tentang situs, navigasi utama, serta tautan menuju halaman lain seperti *Review*, *Tentang Kami*, dan *Kontak*.

Website ini menggunakan desain dengan palet warna biru gelap yang memberikan nuansa misterius, selaras dengan tema film horor supernatural.

---

## 🧩 Struktur Utama

### 1. `<head>`

Berisi meta informasi dan konfigurasi dasar seperti:

* **Meta charset & viewport** — memastikan kompatibilitas dengan perangkat mobile.
* **Meta description** — deskripsi singkat situs untuk SEO.
* **Theme color** — warna utama browser tab pada perangkat mobile.
* **Link stylesheet** — menghubungkan halaman dengan file `styles.css` di folder `/assets/`.

### 2. `<header>`

Menampilkan elemen navigasi utama:

* **Judul situs**: *The Conjuring Universe Reviews*
* **Subjudul**: deskripsi singkat tujuan website
* **Navigasi (menu)**: tautan menuju halaman *Beranda*, *Tentang Kami*, *Review*, dan *Kontak*
* **Tombol navigasi (nav-toggle)**: digunakan untuk menu versi mobile (*responsive menu*)

### 3. `<main>`

Menampilkan konten utama berupa **hero section**, terdiri dari:

* **Judul utama** dengan tagline:
  “Telusuri kengerian bergaya — Semua film The Conjuring Universe dalam satu tempat.”
* **Tombol ajakan (CTA)** menuju halaman *Review* dan *Tentang Kami*
* **Gambar ilustrasi (hero card)** yang menampilkan contoh layout ulasan

### 4. `<footer>`

Berisi hak cipta dinamis:

```html
<p>&copy; <span id="year"></span> Conjuring Reviews.</p>
```

Tahun pada footer akan diperbarui otomatis melalui JavaScript.

---

## ⚙️ File Pendukung

* **`/assets/styles.css`** → berisi seluruh gaya visual (layout, warna, tipografi)
* **`/assets/app.js`** → berisi skrip untuk interaktivitas seperti menu responsif dan pengaturan tahun otomatis di footer
* **`the conjuring univers.jpg`** → gambar hero utama di halaman beranda

---

## 🖥️ Cara Menjalankan

1. Clone repositori:

   ```bash
   git clone https://github.com/username/conjuring-universe-reviews.git
   ```
2. Buka folder proyek:

   ```bash
   cd conjuring-universe-reviews
   ```
3. Jalankan file `index.html` di browser.

---

## 🧠 Teknologi yang Digunakan

* **HTML5** untuk struktur halaman
* **CSS3** (via `styles.css`) untuk tampilan estetis dan responsif
* **JavaScript (ES6)** untuk fungsionalitas dasar (menu & tahun dinamis)

---

## ✨ Fitur Utama

* Desain **responsif** (mobile & desktop)
* Navigasi yang **mudah digunakan**
* Tampilan **aesthetic dengan nuansa biru gelap**
* **Optimasi SEO** dengan meta tag deskriptif

---

## 📸 Pratinjau

> ![Preview Hero Section](the%20conjuring%20univers.jpg)
> *Tampilan hero section pada halaman utama.*

---

Apakah kamu ingin saya tambahkan bagian **“Kontributor”** dan **“Lisensi”** juga agar README-nya lebih lengkap untuk GitHub publik?
