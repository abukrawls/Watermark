# Atelier — Watermark Studio

Aplikasi watermark kamera bertema elegan. Single-file, tanpa dependency server (semua logika ada di `index.html`, memakai HTML Canvas).

## Isi Folder
- `index.html` — aplikasi utama
- `manifest.json` — metadata PWA (nama, ikon, warna tema)
- `icon-192.png`, `icon-512.png` — ikon sementara (ganti dengan ikon final kamu)
- `README.md` — file ini

## Menjalankan Lokal
Buka `index.html` langsung di browser, atau jalankan server statis:
```
npx serve .
```

## Upload ke GitHub
```
git init
git add .
git commit -m "Atelier Watermark Studio"
git branch -M main
git remote add origin <url-repo-kamu>
git push -u origin main
```
Aktifkan **GitHub Pages** (Settings → Pages → branch `main`) supaya app bisa diakses lewat URL publik — ini yang dibutuhkan sebagian tool pembungkus APK.

## Menjadikan APK
Tiga cara paling umum:

**1. PWABuilder (paling mudah, tanpa coding)**
1. Deploy dulu ke GitHub Pages (langkah di atas) supaya punya URL publik.
2. Buka https://www.pwabuilder.com, masukkan URL tersebut.
3. Pilih platform Android → download paket APK/AAB.

**2. Capacitor (butuh Android Studio, lebih fleksibel)**
```
npm init -y
npm install @capacitor/core @capacitor/cli @capacitor/android
npx cap init "Atelier" "com.yourname.atelier"
npx cap add android
npx cap copy
npx cap open android
```
Lalu build APK dari Android Studio.

**3. Median.co / Appilix** — layanan online, tinggal masukkan URL GitHub Pages, mirip PWABuilder.

## Catatan Teknis
- Penyimpanan preferensi & logo custom memakai `localStorage` (bertahan di browser/WebView perangkat, tidak sinkron ke perangkat lain).
- Semua proses watermark terjadi di sisi klien (canvas) — tidak ada foto yang dikirim ke server mana pun.
- Ganti `icon-192.png` / `icon-512.png` dengan ikon final sebelum build APK produksi.
- Template bawaan pakai nama & lencana generik (Rosso, Optik, Mono, Cinema, Minimal, White Bar) — bukan logo merek kamera asli, untuk menghindari masalah hak cipta/merek dagang. Logo asli bisa ditambahkan sendiri lewat fitur "Logo Picker" di dalam app.
