# Blok Tembak Edu (versi Vercel)

Game tembak-tembakan 3D multiplayer edukatif bergaya blok. Cukup satu file `index.html`, tidak perlu server sendiri. Mabar memakai PeerJS (WebRTC): pemain pertama yang masuk ke sebuah kode room otomatis menjadi host, pemain lain tersambung ke host.

## Cara deploy ke Vercel (lewat GitHub, paling mudah)

1. Buat repository baru di GitHub, misalnya `blok-tembak-edu`.
2. Upload file `index.html` (dan README ini) ke repository itu. Bisa lewat tombol **Add file** lalu **Upload files** di GitHub.
3. Buka https://vercel.com, login pakai akun GitHub.
4. Klik **Add New...** lalu **Project**.
5. Pilih repository `blok-tembak-edu`, klik **Import**.
6. Di bagian **Framework Preset** pilih **Other**. Bagian lain biarkan kosong.
7. Klik **Deploy**. Tunggu sampai selesai.
8. Kamu dapat link seperti `https://blok-tembak-edu.vercel.app`. Link ini bisa dibuka siapa saja, tanpa login.

Setiap kali kamu mengubah `index.html` di GitHub, Vercel otomatis deploy ulang.

## Cara deploy lewat terminal (Vercel CLI)

1. Pasang Vercel CLI:
   ```
   npm i -g vercel
   ```
2. Masuk ke folder ini:
   ```
   cd blok-tembak-vercel
   ```
3. Login dan deploy:
   ```
   vercel login
   vercel
   ```
   Jawab pertanyaannya dengan Enter (pakai pilihan bawaan).
4. Untuk link produksi:
   ```
   vercel --prod
   ```

## Coba di laptop sebelum deploy

File ini harus dibuka lewat server, bukan klik dua kali. Di folder ini jalankan salah satu:
```
npx serve .
```
atau
```
python -m http.server 8000
```
lalu buka `http://localhost:3000` (serve) atau `http://localhost:8000` (python).

## Cara mabar

1. Host: isi nama, pilih map dan topik soal, klik **Buat Room**.
2. Klik **Salin** di sebelah kode room, kirim kodenya ke teman.
3. Teman: buka link yang sama, pilih tab **Gabung Room**, masukkan kode, klik **Gabung Room**.
4. Maksimal 10 pemain per room.
5. Kalau host keluar, salah satu pemain otomatis menjadi host baru dalam beberapa detik.

## Kontrol

| PC | HP | Fungsi |
| --- | --- | --- |
| W A S D | Joystick kiri | Jalan |
| Mouse | Geser layar kanan | Membidik |
| Klik kiri | Tombol 🔫 | Menembak |
| Spasi | Tombol ⬆ | Lompat |
| Shift (tahan) | Tombol ⚡ | Lari |
| R | Tombol ❓ | Jawab soal untuk isi peluru |
| 🏠 | 🏠 | Kembali ke menu |

## Kalau tidak bisa tersambung

1. Pastikan semua pemain memakai kode yang sama persis.
2. Coba ganti jaringan (misalnya dari WiFi sekolah ke data seluler). Beberapa WiFi kantor atau sekolah memblokir WebRTC.
3. Muat ulang halaman lalu coba lagi.
4. Server perantara yang dipakai (PeerJS cloud dan TURN openrelay) adalah layanan gratis publik, jadi kadang bisa lambat atau sedang gangguan.

## Mengubah soal

Cari `const BANK = {` di dalam `index.html`. Tambahkan soal dengan format:

```js
{ t: 'Pertanyaan', b: 'Jawaban benar', s: ['Salah 1', 'Salah 2', 'Salah 3'], e: 'Penjelasan singkat' },
```

Angka-angka game (damage, jumlah peluru, target kill, maksimal pemain) ada di baris `const MAX_AMMO = 10, DAMAGE = 25, TARGET_KILL = 10, MAX_PEMAIN = 10;`.
