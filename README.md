# The Conjuring Universe Reviews - Dokumentasi Lengkap

Website ulasan film The Conjuring Universe dengan desain modern, interaktif, dan aksesibel. Dibangun dengan HTML5, CSS3, dan Vanilla JavaScript.

## 📁 Struktur File
```
conjuring-reviews/
├── index.html           # Halaman beranda
├── tentang.html         # Halaman tentang kami
├── review.html          # Halaman katalog review
├── kontak.html          # Halaman form kontak
├── assets/
│   ├── styles.css       # Stylesheet utama
│   └── app.js           # JavaScript interaktif
└── images/
    └── posters/         # Folder poster film
```

---

## 📄 File HTML

### 1. **index.html** - Halaman Beranda

**Tujuan**: Landing page dengan hero section yang menarik perhatian pengunjung.

#### Fitur Utama:
- **Hero Section**: 
  - Grid 2 kolom (copy text + gambar hero)
  - Judul besar dengan `clamp()` untuk responsivitas
  - CTA buttons: "Lihat Review" dan "Pelajari Kami"
  - Image dengan lazy loading
  
- **Optimasi Performance**:
  - `preload` untuk CSS critical
  - `loading="lazy"` pada gambar
  - Defer JavaScript execution

#### Struktur Khusus:
```html
<section class="hero">
  <div class="hero__inner">
    <div class="hero__copy">
      <!-- Judul + CTA buttons -->
    </div>
    <aside class="hero__card">
      <!-- Hero image -->
    </aside>
  </div>
</section>
```

#### Custom Styling:
```css
/* Inline styles untuk override card hero */
.hero__card { 
  background: transparent !important;
  min-height: 0 !important;
  padding: 0 !important;
}
```

**Best Practices**:
- Semantic HTML (`<section>`, `<aside>`, `<nav>`)
- Skip link untuk keyboard navigation
- ARIA labels untuk accessibility
- Meta theme-color untuk mobile browsers

---

### 2. **tentang.html** - Halaman Tentang Kami

**Tujuan**: Menjelaskan identitas, misi, dan prinsip editorial situs.

#### Fitur Utama:
- **Card Container**: Konten dalam single card dengan padding besar
- **Section Breakdown**:
  - Siapa kami?
  - Prinsip Kami (Transparansi, Konsistensi, Aksesibilitas)
  - Struktur Konten
  - Mengapa The Conjuring Universe?

#### Custom Styling (Inline):
```css
/* Padding khusus untuk paragraf dan list dalam card */
.prose .card > h2 + p,
.prose .card > h3 + p,
.prose .card > h3 + ul {
  padding: 1.25rem 1.5rem;
}

/* Indentasi bullet list */
.prose .card > h3 + ul { 
  padding-left: 1.4rem; 
}
```

#### Struktur Konten:
```html
<main class="container prose">
  <article class="reveal" style="max-width: 800px;">
    <div class="card" style="padding: 2rem;">
      <h2>Siapa kami?</h2>
      <p>...</p>
      
      <h3>Prinsip Kami</h3>
      <ul>...</ul>
      
      <!-- dst -->
    </div>
  </article>
</main>
```

**Accessibility Features**:
- Max-width 800px untuk optimal reading length
- Clear heading hierarchy (h2 → h3)
- List untuk scannability
- `.prose` class untuk typography optimization

---

### 3. **review.html** - Halaman Review & Katalog

**Tujuan**: Hub utama untuk browsing film dengan filter dan modal detail.

#### Fitur Utama:

##### A. Filter Toolbar
```html
<section class="filters reveal" role="toolbar">
  <button class="chip is-active" data-filter="all">Semua</button>
  <button class="chip" data-filter="Utama">Utama</button>
  <button class="chip" data-filter="Annabelle">Annabelle</button>
  <button class="chip" data-filter="The Nun">The Nun</button>
  <button class="chip" data-filter="Lainnya">Lainnya</button>
</section>
```

**Attributes**:
- `data-filter`: Kategori untuk JavaScript filtering
- `aria-pressed`: State toggle untuk screen readers
- `role="toolbar"`: Semantic role

##### B. Film Grid
```html
<section class="grid grid--cards" id="film-grid" 
         aria-live="polite" aria-label="Daftar film">
  <!-- Kartu di-render via JavaScript -->
</section>
```

**Karakteristik**:
- `aria-live="polite"`: Announce filter changes
- `id="film-grid"`: Target untuk JavaScript DOM manipulation
- Responsive grid: 3 kolom → 2 kolom → 1 kolom

##### C. User Reviews Section
```html
<section class="user-reviews reveal">
  <header class="section-head">
    <h3>Review Pengguna</h3>
    <p class="muted">Review yang Anda kirim dari halaman Kontak...</p>
  </header>
  <div id="user-reviews" class="stack"></div>
</section>
```

**Data Flow**:
```
kontak.html (form) → localStorage → review.html (display)
```

##### D. Modal Detail
```html
<dialog id="detail-modal" class="modal" aria-labelledby="modal-title">
  <article class="modal__content">
    <button class="modal__close" aria-label="Tutup detail" data-close>
      &times;
    </button>
    <div id="modal-body"><!-- Konten dinamis --></div>
  </article>
</dialog>
```

**Native Dialog Features**:
- `::backdrop` pseudo-element untuk overlay
- `.showModal()` untuk modal behavior
- ESC key untuk close (native browser)
- Focus trap otomatis

**JavaScript Integration Points**:
- `#film-grid`: Container untuk render cards
- `#detail-modal`: Modal dialog
- `#modal-body`: Dynamic content injection
- `#user-reviews`: User review list

---

### 4. **kontak.html** - Halaman Form Kontak

**Tujuan**: Formulir interaktif untuk pengunjung mengirim review film.

#### Fitur Utama:

##### A. Form Structure
```html
<form id="review-form" class="form reveal" novalidate>
  <fieldset>
    <legend>Kirim Review Anda</legend>
    <!-- Fields -->
  </fieldset>
</form>
```

**Attribute `novalidate`**: Disable browser validation untuk custom handling.

##### B. Input Fields

**1. Nama**
```html
<label for="nama">Nama <span aria-label="wajib diisi">*</span></label>
<input id="nama" name="nama" type="text" required 
       minlength="2" maxlength="40" 
       placeholder="Nama Anda" autocomplete="name" />
```

**2. Email**
```html
<input id="email" name="email" type="email" required 
       placeholder="nama@contoh.com" autocomplete="email" />
```

**3. Judul Film**
```html
<select id="judul" name="judul" required>
  <option value="">Pilih film...</option>
  <option>The Conjuring (2013)</option>
  <!-- 8 film lainnya -->
</select>
```

**Film List**:
1. The Conjuring (2013)
2. Annabelle (2014)
3. The Conjuring 2 (2016)
4. Annabelle: Creation (2017)
5. The Nun (2018)
6. Annabelle Comes Home (2019)
7. The Curse of La Llorona (2019)
8. The Conjuring: The Devil Made Me Do It (2021)
9. The Nun II (2023)

**4. Rating**
```html
<input id="rating" name="rating" type="number" 
       min="0" max="10" step="0.1" required 
       placeholder="cth. 7.5" />
```

**5. Review Text**
```html
<textarea id="pesan" name="pesan" rows="5" 
          minlength="10" maxlength="1000" required 
          placeholder="Apa yang Anda suka/tidak suka?"></textarea>
```

##### C. Form Actions
```html
<div class="form__actions">
  <button class="btn btn--primary" type="submit">Kirim Review</button>
  <button class="btn btn--ghost" type="reset">Reset Form</button>
</div>

<p id="form-status" role="status" aria-live="polite" class="muted"></p>
```

**Accessibility**:
- `role="status"`: Status messages region
- `aria-live="polite"`: Announce updates
- `aria-label` untuk required indicators

#### Validasi HTML5:
- `required`: Field wajib
- `minlength` / `maxlength`: Panjang karakter
- `min` / `max`: Range angka
- `step`: Increment untuk number input
- `type="email"`: Email format validation

#### Data Storage:
```javascript
// Disimpan ke localStorage dengan key "userReviews"
{
  nama: "...",
  email: "...",
  judul: "...",
  rating: 8.5,
  pesan: "...",
  time: "2025-10-16T10:30:00.000Z"
}
```

---

## 🎨 CSS (styles.css)

### Arsitektur & Filosofi Desain

**Theme**: Modern dark mode dengan accent biru-cyan, terinspirasi gaming/studio aesthetics.

#### Color Palette
```css
:root {
  /* Backgrounds */
  --bg: #0a1224;           /* Deep blue-black */
  --bg-2: #0c1a34;         /* Slightly lighter */
  --card: #0f1a3a;         /* Card background */
  
  /* Surfaces (light mode elements) */
  --surface: #eaf3fb;      /* Light blue-white */
  --surface-2: #f4f7fb;    /* Softer variant */
  
  /* Text */
  --text: #e7eaf6;         /* Primary text (light) */
  --muted: #a9b0d2;        /* Secondary text */
  
  /* Brand Colors */
  --primary: #3b82f6;      /* Blue */
  --primary-700: #1e5fe2;  /* Darker blue */
  --accent: #64e1ff;       /* Cyan */
  --accent-700: #1fb6e0;   /* Darker cyan */
  
  /* Shadows & Borders */
  --shadow: 0 10px 30px rgba(8, 16, 40, 0.35), 
            0 2px 8px rgba(0, 0, 0, 0.25);
  
  /* Border Radius */
  --radius-xl: 24px;
  --radius-lg: 18px;
  --radius: 12px;
  --radius-sm: 10px;
}
```

---

### Layout Components

#### 1. **Background System**

##### Multi-layer Gradients
```css
body {
  background: 
    /* Grid pattern (subtle) */
    linear-gradient(rgba(255, 255, 255, 0.03) 1px, transparent 1px),
    linear-gradient(90deg, rgba(255, 255, 255, 0.03) 1px, transparent 1px),
    
    /* Radial glows */
    radial-gradient(1100px 700px at -10% -20%, #1e40af1a, transparent 60%),
    radial-gradient(900px 560px at 115% 0%, #3b82f61a, transparent 60%),
    radial-gradient(1200px 780px at 50% 115%, #0ea5e91a, transparent 60%),
    
    /* Base color */
    linear-gradient(180deg, #0a1224, #0a1224);
    
  background-size: 44px 44px, 44px 44px, auto, auto, auto, auto;
}
```

##### Cursor Glow (Dynamic)
```css
body::after {
  content: "";
  position: fixed;
  inset: -15%;
  pointer-events: none;
  filter: blur(30px) saturate(120%);
  background: 
    radial-gradient(300px 240px at var(--mx, -20%) var(--my, -20%), 
                    #64e1ff22, transparent 60%),
    radial-gradient(420px 360px at calc(var(--mx) + 8%) calc(var(--my) + 6%), 
                    #3b82f61a, transparent 65%);
  z-index: 0;
}
```

**JavaScript Integration**:
```javascript
window.addEventListener("pointermove", (e) => {
  document.body.style.setProperty("--mx", `${e.clientX}px`);
  document.body.style.setProperty("--my", `${e.clientY}px`);
});
```

---

#### 2. **Header (Sticky Navigation)**
```css
.site-header {
  position: sticky;
  top: 0;
  z-index: 50;
  background: rgba(20, 24, 60, 0.5);
  backdrop-filter: blur(10px);
  border-bottom: 1px solid rgba(255, 255, 255, 0.08);
}
```

**Features**:
- Glassmorphism effect
- Sticky positioning
- Blur backdrop
- Responsive grid layout

##### Navigation Links
```css
.site-nav a {
  padding: .55rem .9rem;
  border-radius: 999px;
  background: linear-gradient(180deg, rgba(255, 255, 255, 0.06), 
                                      rgba(255, 255, 255, 0.03));
  border: 1px solid rgba(255, 255, 255, 0.12);
}

.site-nav .is-active {
  background: linear-gradient(#ffffff, #f3f8ff) padding-box,
              linear-gradient(180deg, var(--accent), var(--primary)) border-box;
  border: 2px solid transparent;
  color: #0b1130;
  box-shadow: 0 8px 24px rgba(59, 130, 246, 0.22);
}
```

**Technique**: Gradient border using `padding-box` + `border-box`.

##### Mobile Toggle
```css
@media (max-width: 900px) {
  .nav-toggle { display: inline-block; }
  .site-nav { display: none; }
  .site-nav.is-open { 
    display: block;
    grid-column: 1 / -1;
  }
}
```

---

#### 3. **Hero Section**
```css
.hero__inner {
  display: grid;
  gap: 2rem;
  grid-template-columns: 1fr 1.15fr;
  align-items: center;
}

.hero__card {
  background: linear-gradient(180deg, #ffffff, #ffffff) padding-box,
              linear-gradient(180deg, var(--accent), var(--primary)) border-box;
  border: 2px solid transparent;
  border-radius: var(--radius-xl);
  min-height: clamp(260px, 36vw, 420px);
}
```

**Responsive**:
- Desktop: 2 kolom (text + image)
- Mobile: 1 kolom (stacked)
- Fluid sizing dengan `clamp()`

---

#### 4. **Button System**

##### Base Button
```css
.btn {
  display: inline-flex;
  align-items: center;
  gap: .5rem;
  padding: .75rem 1rem;
  border-radius: 999px;
  transition: transform .15s ease, box-shadow .15s ease;
  box-shadow: 0 6px 16px rgba(0, 0, 0, 0.15);
}

.btn:hover {
  transform: translateY(-1px);
}
```

##### Primary Button (Gradient + Shine Effect)
```css
.btn--primary {
  background: linear-gradient(180deg, var(--accent), var(--primary));
  color: #0c1030;
  position: relative;
  overflow: hidden;
}

.btn--primary::after {
  content: "";
  position: absolute;
  inset: 0;
  background: linear-gradient(120deg, 
                              transparent 30%, 
                              rgba(255, 255, 255, 0.5) 45%, 
                              transparent 60%);
  transform: translateX(-120%);
  transition: transform .6s ease;
}

.btn--primary:hover::after {
  transform: translateX(120%);
}
```

**Effect**: Shine sweep animation on hover.

##### Ghost Button
```css
.btn--ghost {
  background: #ffffff10;
  border: 1px solid rgba(255, 255, 255, 0.18);
  color: var(--text);
}
```

---

#### 5. **Film Cards**

##### Grid Container
```css
.grid--cards {
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 1.25rem;
  padding: clamp(0.75rem, 1vw + 0.5rem, 1.25rem);
  border-radius: 28px;
  background: linear-gradient(135deg, #e1f0ff 0%, #d6e6ff 50%, #d0f4ff 100%);
}

@media (max-width: 1000px) {
  .grid--cards { grid-template-columns: repeat(2, 1fr); }
}

@media (max-width: 640px) {
  .grid--cards { grid-template-columns: 1fr; }
}
```

**Design**: Light gradient background untuk kontras dengan dark theme.

##### Film Card
```css
.film {
  background: #ffffff;
  color: #101223;
  border-radius: 18px;
  box-shadow: 0 6px 18px rgba(20, 22, 50, 0.12);
  transform: translateZ(0) rotateX(var(--rx, 0deg)) rotateY(var(--ry, 0deg));
}

.film:hover {
  transform: translateY(-4px) rotateX(var(--rx)) rotateY(var(--ry));
  box-shadow: 0 10px 24px rgba(20, 22, 50, 0.18);
}
```

**3D Tilt**: Controlled via CSS variables set by JavaScript.

##### Poster Area
```css
.film__media {
  aspect-ratio: 16 / 10;
  background: 
    radial-gradient(220px 160px at 85% 75%, #bcd5ff, transparent 60%),
    radial-gradient(160px 120px at 15% 25%, #9be1ff, transparent 65%),
    linear-gradient(135deg, #cfe4ff, #f2f7ff);
}

.film__img {
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
}
```

**Fallback**: Gradient background jika gambar gagal load.

##### Year Pill Badge
```css
.film__pill {
  position: absolute;
  top: 10px;
  right: 10px;
  background: linear-gradient(180deg, #6aa8ff, #2f7ae5);
  padding: 4px 10px;
  border-radius: 999px;
  box-shadow: 0 4px 10px rgba(47, 122, 229, 0.35);
  border: 1px solid #ffffff44;
}
```

---

#### 6. **Modal Dialog**
```css
.modal {
  border: 0;
  outline: none;
  padding: 0;
  background: transparent;
  width: min(920px, calc(100vw - 2rem));
}

.modal::backdrop {
  background: 
    radial-gradient(900px 500px at 50% 15%, rgba(53, 132, 255, 0.28), transparent 65%), 
    rgba(5, 10, 26, 0.55);
  backdrop-filter: blur(2px);
}
```

##### Modal Content (Squircle Shape)
```css
.modal__content {
  border-radius: var(--radius-lg);
  background: linear-gradient(180deg, #ffffff 0%, #f5f9ff 100%);
  border: 1px solid rgba(47, 122, 229, 0.22);
  box-shadow: 
    0 16px 40px rgba(20, 40, 80, 0.28),
    0 0 0 1px rgba(255, 255, 255, 0.6) inset;
  padding: clamp(16px, 2vw, 24px);
  padding-right: calc(clamp(16px, 2vw, 24px) + 28px);
}
```

**Advanced**: Squircle shape using CSS mask (browser support check).
```css
@supports (mask: radial-gradient(#000, transparent)) {
  .modal__content {
    mask: 
      radial-gradient(130% 130% at 0% 0%, #000 98%, transparent) top left,
      radial-gradient(130% 130% at 100% 0%, #000 98%, transparent) top right,
      radial-gradient(130% 130% at 100% 100%, #000 98%, transparent) bottom right,
      radial-gradient(130% 130% at 0% 100%, #000 98%, transparent) bottom left;
    mask-size: 51% 51%;
    mask-repeat: no-repeat;
  }
}
```

##### Close Button
```css
.modal__close {
  position: absolute;
  top: 12px;
  right: 12px;
  width: 32px;
  height: 32px;
  border-radius: 10px;
  background: #e6efff;
  color: #1e3a8a;
  transition: transform .12s ease;
}

.modal__close:hover {
  transform: translateY(-1px);
  box-shadow: 0 6px 16px rgba(30, 58, 138, 0.28);
}
```

---

#### 7. **Filter Chips**
```css
.filters {
  display: flex;
  flex-wrap: wrap;
  gap: .5rem;
  padding: .6rem;
  border-radius: 18px;
  background: linear-gradient(180deg, rgba(255, 255, 255, 0.08), 
                                      rgba(255, 255, 255, 0.04)) padding-box,
              linear-gradient(180deg, #6ee7ff33, #3b82f633) border-box;
  border: 1px solid transparent;
  backdrop-filter: blur(8px);
}

.chip {
  padding: .5rem .9rem;
  border-radius: 999px;
  background: linear-gradient(180deg, rgba(255, 255, 255, 0.14), 
                                      rgba(255, 255, 255, 0.06));
  box-shadow: 
    inset 0 1px 0 rgba(255, 255, 255, 0.35),
    0 1px 2px rgba(3, 8, 20, 0.25);
}

.chip.is-active {
  background: linear-gradient(#ffffff, #eef5ff) padding-box,
              linear-gradient(180deg, var(--accent), var(--primary)) border-box;
  border: 2px solid transparent;
  box-shadow: 0 10px 22px rgba(59, 130, 246, 0.25);
}
```

**State Management**:
- Default: Translucent glass effect
- Active: Gradient border + elevated shadow
- Hover: Lift animation

---

#### 8. **Form Styling**
```css
.form fieldset {
  padding: clamp(16px, 2.2vw, 22px);
  border-radius: var(--radius-lg);
  background: linear-gradient(180deg, rgba(255, 255, 255, 0.12), 
                                      rgba(255, 255, 255, 0.06)) padding-box,
              linear-gradient(180deg, 
                              color-mix(in oklab, var(--accent) 35%, transparent),
                              color-mix(in oklab, var(--primary) 35%, transparent)) border-box;
  border: 1px solid transparent;
  box-shadow: 
    inset 0 1px 0 rgba(255, 255, 255, 0.35),
    0 12px 28px rgba(3, 8, 20, 0.28);
}
```

**Modern CSS**: `color-mix()` untuk gradient transparan.

##### Inputs
```css
.form input,
.form select,
.form textarea {
  padding: .75rem .9rem;
  border-radius: 12px;
  border: 1px solid rgba(47, 122, 229, 0.35);
  background: linear-gradient(180deg, #ffffff, #f5f9ff);
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.85);
}

.form input:focus {
  border-color: var(--primary);
  box-shadow: 
    0 0 0 3px color-mix(in oklab, var(--accent) 30%, transparent),
    inset 0 1px 0 rgba(255, 255, 255, 0.85);
}
```

##### Validation States
```css
.is-invalid {
  box-shadow: 0 0 0 3px rgba(225, 29, 72, 0.08) !important;
  border-color: #e11d48 !important;
}

.error-message {
  color: #e11d48;
  font-size: .92rem;
  margin-top: .35rem;
}

.validation-status.status-error {
  color: #7f1d1d;
  background: #fff5f6;
  padding: .5rem .75rem;
  border-radius: 10px;
  border: 1px solid rgba(225,29,72,0.12);
}
```

---

#### 9. **3D Tilt Effect**
```css
.card,
.form,
.hero__card,
.modal__content,
.film {
  transform: perspective(1000px) 
             rotateX(var(--rx, 0deg)) 
             rotateY(var(--ry, 0deg));
  will-change: transform;
  transition: transform .12s ease;
}
```

**JavaScript Control**:
```javascript
element.style.setProperty("--rx", `${rx}deg`);
element.style.setProperty("--ry", `${ry}deg`);
```

---

#### 10. **Reveal Animation**
```css
.reveal {
  opacity: 0;
  transform: translateY(20px);
  transition: opacity .6s ease, transform .6s ease;
}

.reveal.is-visible {
  opacity: 1;
  transform: translateY(0);
}
```

**Triggered by**: Intersection Observer in JavaScript.

---

#### 11. **Utility Classes**
```css
.container {
  width: min(100% - 2rem, 1200px);
  margin-inline: auto;
}

.text-balance {
  text-wrap: balance;
}

.muted {
  color: var(--muted);
}

.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
}
```

---

### Responsive Breakpoints

| Breakpoint | Target | Grid Columns |
|------------|--------|--------------|
| < 640px | Mobile | 1 column |
| 640px - 1000px | Tablet | 2 columns |
| > 1000px | Desktop | 3 columns |
| > 900px | Nav | Horizontal menu |

---

### Performance Optimizations

1. **CSS Containment**: `contain: layout style;`
2. **Will-change**: `will-change: transform;`
3. **Transform over position**: Hardware acceleration
4. **Backdrop-filter**: GPU-accelerated blur
5. **Clamp()**: Fluid typography tanpa media queries

---

## ⚙️ JavaScript (app.js)

### Arsitektur Modular

**Pattern**: IIFE (Immediately Invoked Function Expression) untuk scope isolation.
```javascript
;(() => {
  // Selector helpers
  const $ = (sel, ctx = document) => ctx.querySelector(sel)
  const $$ = (sel, ctx = document) => Array.from(ctx.querySelectorAll(sel))
  
  // Main init
  document.addEventListener("DOMContentLoaded", () => {
    // All functionality here
  })
})()
```

---

### 1. **Core Utilities**

#### Dynamic Footer Year
```javascript
const y = $("#year")
if (y) y.textContent = new Date().getFullYear()
```

#### Mobile Navigation Toggle
```javascript
const toggle = $(".nav-toggle")
const nav = $("#menu")

if (toggle && nav) {
  const setExpanded = (val) => {
    toggle.setAttribute("aria-expanded", String(val))
    nav.classList.toggle("is-open", val)
  }
  
  toggle.addEventListener("click", () => {
    const expanded = toggle.getAttribute("aria-expanded") === "true"
    setExpanded(!expanded)
  })
  
  // Close on outside click
  document.addEventListener("click", (e) => {
    if (!nav.contains(e.target) && !toggle.contains(e.target)) {
      setExpanded(false)
    }
  })
}
```

**Accessibility**: ARIA attributes for screen readers.

---

### 2. **Intersection Observer (Reveal Animation)**
```javascript
const revealEls = $$(".reveal")

if (revealEls.length) {
  const io = new IntersectionObserver(
    (entries) => {
      entries.forEach((en) => {
        if (en.isIntersecting) {
          en.target.classList.add("is-visible")
          io.unobserve(en.target) // Trigger once
        }
      })
    },
    { threshold: 0.15 } // 15% visible
  )
  
  revealEls.forEach((el) => io.observe(el))
}
```

**Performance**: Unobserve setelah animation trigger untuk menghindari re-calculation.

---

### 3. **Film Data Structure**
```javascript
const films = [
  {
    title: "The Conjuring",
    year: 2013,
    cat: "Utama",
    rating: 8
