# Cara Menjalankan dan Mem-publikasikan CacheVR

Prototipe berupa satu file `index.html` (A-Frame via CDN), sehingga bisa dibuka langsung atau di-host gratis.

## 1. Jalankan di komputer (lokal)

Kamera (Mode AR) hanya aktif pada `https` atau `localhost`. Jalankan server statis:

```bash
cd ~/Pekerti/MiniProject_CacheVR
python3 -m http.server 8000
```

Buka `http://localhost:8000` di browser. Untuk mode VR, gunakan headset (Quest, Pico) atau browser dengan WebXR.

## 2. Publikasikan ke GitHub Pages (tautan publik untuk dikumpulkan)

```bash
cd ~/Pekerti/MiniProject_CacheVR
git init
git add index.html
git commit -m "CacheVR: prototipe media AR/VR hierarki memori"
git branch -M main
git remote add origin https://github.com/USERNAME/cachevr.git
git push -u origin main
```

Lalu di GitHub: **Settings > Pages > Source: Deploy from a branch > Branch: main / (root) > Save**. Tautan menjadi:

```
https://USERNAME.github.io/cachevr/
```

Alternatif tanpa Git: unggah folder ke Netlify Drop (https://app.netlify.com/drop) atau Vercel, lalu salin tautan yang dihasilkan.

## 3. Mengaktifkan GenAI langsung (opsional)

Buka **Lab Skenario GenAI** atau **Tanya AI**, tempel API key OpenAI pada kolom yang tersedia. Key hanya disimpan di `sessionStorage` perangkat pengguna dan dipakai untuk memanggil `gpt-4o-mini`.

Tanpa API key, aplikasi tetap berjalan penuh memakai **generator skenario lokal** (deterministik, berbasis aturan) dan bank penjelasan lokal. Ini penting agar prototipe tidak gagal saat dinilai tanpa koneksi atau tanpa kredit API.

## 4. Peta interaksi (minimal 3 titik aktif, sesuai ketentuan)

1. Memilih tingkat memori (L1/L2/L3/RAM) dengan klik atau gaze di VR.
2. Menjalankan **Akses Data** dan mengamati jalur data serta latensi.
3. Menyusun skenario di **Lab Skenario GenAI** (menentukan pola akses, jumlah akses, working set).
4. Menjalankan simulasi 3D dan membaca statistik hit/miss serta rata-rata latensi.
5. Menjawab kuis tiga soal dan menerima umpan balik penjelasan.
6. Menjelajah **Filosofi Lokal** (tudang sipulung dan sipakatau) sebagai kerangka berpikir.

## 5. Catatan teknis

- Mode AR: kamera perangkat menjadi latar (passthrough), model 3D tampak berada di ruang nyata. Membutuhkan izin kamera dan konteks aman (`https` atau `localhost`).
- Mode VR: tombol kacamata pada A-Frame; mendukung WebXR pada headset atau Cardboard.
- Perangkat target: laptop/PC (Chrome, Edge, Brave, Safari terbaru) dan smartphone Android/iOS modern.