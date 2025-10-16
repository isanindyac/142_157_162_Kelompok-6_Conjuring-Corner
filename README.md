# 142_157_162_Kelompok-6_Conjuring-Corner
Website ini dapat menampilkan review dari seluruh universal film The Conjuring dan dapat menambahkan input review dari pengguna.

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

# Halaman Tentang Kami - The Conjuring Universe Reviews

Halaman "Tentang Kami" memberikan informasi lengkap mengenai misi, visi, dan prinsip editorial dari situs The Conjuring Universe Reviews.

## 📋 Deskripsi

Halaman ini dirancang untuk memperkenalkan identitas situs kepada pengunjung, menjelaskan pendekatan kurasi konten, serta menyampaikan komitmen terhadap transparansi dan aksesibilitas.

## ✨ Fitur Utama

### 1. **Identitas Tim**
- Penjelasan tentang tim penggemar film horor
- Misi untuk berbagi review jujur dan pandangan pribadi
- Tujuan membantu penonton memahami The Conjuring Universe lebih dalam

### 2. **Prinsip Editorial**
Tiga pilar utama:
- **Transparansi**: Sumber rating dan ringkasan dijelaskan dengan jelas
- **Konsistensi**: Gaya visual biru, tipografi rapi, dan kontras terjaga
- **Aksesibilitas**: Navigasi jelas, alt text deskriptif, dan fokus yang terlihat

### 3. **Struktur Konten**
Penjelasan format standar setiap review film:
- Sinopsis singkat yang padat
- Tahun rilis dan informasi kategori
- Rating ringkas untuk referensi cepat
- Tag tematik untuk navigasi mudah

### 4. **Latar Belakang**
Penjelasan mengapa The Conjuring Universe dipilih sebagai fokus, mencakup:
- Kesuksesan jagat sinematik horor
- Koneksi dari kisah nyata Ed dan Lorraine Warren
- Keterkaitan unik antar film dalam universe

## 🎨 Desain & Styling

### CSS Khusus Halaman
```css
/* Padding optimal untuk konten dalam card */
.prose .card > h2 + p,
.prose .card > h3 + p,
.prose .card > h3 + ul {
  padding: 1.25rem 1.5rem;
}

/* Indentasi bullet list yang rapi */
.prose .card > h3 + ul { 
  padding-left: 1.4rem; 
}
```

### Elemen Visual
- **Layout**: Card-based dengan max-width 800px
- **Spacing**: Margin dan padding yang konsisten
- **Typography**: Heading hierarchy yang jelas (h2, h3)
- **Color Scheme**: Konsisten dengan tema biru (#021024)

## 🏗️ Struktur HTML
```
<header>
  └── Navigasi dengan link aktif pada "Tentang Kami"

<main>
  └── <article class="reveal">
      └── <div class="card">
          ├── Siapa kami?
          ├── Prinsip Kami (list)
          ├── Struktur Konten (list)
          └── Mengapa The Conjuring Universe?

<footer>
  └── Copyright dengan tahun dinamis
```

## ♿ Aksesibilitas

- **Skip Link**: Navigasi cepat ke konten utama
- **ARIA Labels**: `aria-current="page"` untuk halaman aktif
- **Semantic HTML**: Penggunaan tag `<article>`, `<nav>`, `<header>`
- **Meta Description**: Deskripsi halaman yang jelas untuk SEO
- **Theme Color**: Meta tag untuk mobile browser (#021024)

## 📱 Responsive Design

- Meta viewport untuk mobile optimization
- Container dan card yang adaptif
- Navigasi toggle untuk layar kecil
- Typography yang scalable

## 🔗 Navigasi

Terintegrasi dengan halaman lain:
- `/index.html` - Beranda
- `/tentang.html` - Tentang Kami (halaman aktif)
- `/review.html` - Review
- `/kontak.html` - Kontak

## 📦 Dependencies

- `/assets/styles.css` - Stylesheet global
- `/assets/app.js` - JavaScript untuk interaktivitas (navigation toggle, dynamic year)

## 🎯 Tujuan Halaman

1. Membangun kredibilitas dan kepercayaan pengunjung
2. Menjelaskan standar kualitas konten
3. Menyampaikan komitmen terhadap user experience
4. Memberikan konteks tentang fokus niche situs

## 💡 Best Practices

- **Content First**: Informasi penting di awal
- **Scannable Content**: Penggunaan heading dan list untuk readability
- **Visual Hierarchy**: Spacing dan typography yang jelas
- **Brand Consistency**: Tone dan style sesuai tema horor

## 🔄 Update & Maintenance

- Periksa link navigasi secara berkala
- Update informasi jika ada perubahan prinsip editorial
- Pastikan copyright year ter-update otomatis via JavaScript
- Review konten untuk akurasi dan relevansi

---

**Catatan**: Halaman ini menggunakan bahasa Indonesia (lang="id") dan dioptimasi untuk pengalaman pengguna lokal.
