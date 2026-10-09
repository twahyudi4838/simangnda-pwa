SIMANGNDA PWA - PAKET DENGAN LOGIN SERVER-SIDE

ISI PAKET
- index.html: aplikasi SIMANGNDA Revisi 3; logika simulasi asli dipertahankan, hanya menambahkan manifest dan registrasi service worker.
- login.html: halaman login tim.
- functions/: pemeriksaan sesi dan endpoint login Cloudflare Pages Functions.
- manifest.webmanifest, icon.svg, sw.js: instalasi PWA dan cache offline.

PENTING: PASSWORD TIDAK DISIMPAN DI KODE
Saat menyiapkan Cloudflare Pages, buat dua environment variables/secrets: 
1. SIMANGNDA_PASSWORD = password tim yang dipilih pemilik.
2. AUTH_SECRET = string acak panjang minimal 32 karakter, berbeda dari password.
Atur keduanya untuk Production (dan Preview bila memang diperlukan). Jangan menuliskan password di HTML atau membagikan AUTH_SECRET.

CARA PUBLIKASI
1. Upload folder SIMANGNDA_PWA ke repository Git pribadi atau deploy sebagai project Cloudflare Pages yang mendukung folder functions/.
2. Build command: kosong / none; output directory: folder SIMANGNDA_PWA (atau root project jika isi folder dipindahkan ke root). Pastikan folder functions berada di root project Pages.
3. Tambahkan kedua environment variables di Settings > Variables and Secrets.
4. Deploy ke HTTPS; uji login dengan password benar dan salah, kemudian coba buka halaman utama.
5. Dari Chrome Android saat online, login lalu tunggu aplikasi termuat penuh. Pilih menu Chrome > Install app / Tambahkan ke layar utama.
6. Uji offline dengan memutus internet setelah aplikasi selesai dimuat. Cache offline memungkinkan aplikasi yang sudah diotorisasi digunakan di perangkat tersebut; WhatsApp tetap membutuhkan internet.

CATATAN KEAMANAN & OFFLINE
- Ini adalah proteksi berbasis satu password bersama. Siapa pun yang mengetahui password dapat masuk; ganti secret/password jika dibagikan di luar tim.
- Session cookie berlaku 7 hari saat online. Service worker meng-cache halaman aplikasi setelah kunjungan yang berhasil; offline setelah instalasi/cache diuji pada perangkat. Jangan mengandalkan logout atau kedaluwarsa online sebagai penghapusan salinan offline di perangkat yang sudah diotorisasi.
- Link belum dipublikasikan oleh paket ini. Pemilik perlu memiliki akun hosting dan melakukan deployment serta konfigurasi secrets.
- Untuk hasil paling aman, jangan menaruh spreadsheet sumber yang tidak ingin dibagikan dalam folder publik; tabel/logika aplikasi memang tersedia di sisi klien agar simulasi dapat berjalan offline.
