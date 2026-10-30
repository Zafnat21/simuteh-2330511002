# simuteh-2330511002

SIMUTEH - Evaluasi Praktikum P1-P4 Computer Vision UMMI - Zafnat Paaneah Matusal



\# SIMUTEH: Evaluasi Praktikum Computer Vision P1-P4



Repositori ini berisi pengerjaan evaluasi praktikum Computer Vision Pertemuan 1 sampai 4, studi kasus SIMUTEH (deteksi bercak cacar daun teh Exobasidium vexans).



\- Nama: Zafnat Paaneah Matusal

\- NIM: 2330511002

\- Kelas: 7A

\- SEED dataset: 1002



\## Struktur



\- `notebook/`: notebook pengerjaan per bagian (B1 sampai B5)

\- `src/`: kode sumber (buat\_dataset\_sintetis.py, utils\_cv.py, praproses.py)

\- `hasil/`: tabel, grafik, panel, dan parameter hasil pengerjaan

\- `requirements.txt`: versi pustaka yang dipakai



\## Cara menjalankan



1\. Buka notebook di Google Colab.

2\. Clone repositori ini, lalu masuk ke folder repo.

3\. Bangkitkan dataset dengan perintah `python src/buat\_dataset\_sintetis.py` (folder `data/` tidak ikut di-commit).

4\. Masuk ke folder `notebook`, lalu jalankan notebook dari atas sampai bawah (Restart \& Run All).



\## Ringkasan hasil



\- Kanal terbaik untuk kontras bercak adalah kanal R (Bagian 2).

\- Perbaikan terbaik per kondisi: gamma untuk gelap dan terang, peregangan persentil untuk kontras rendah, CLAHE clip 2,0 tile 4 untuk bayangan (Bagian 3).

\- Penapis pilihan median kernel 3 menaikkan PSNR 12 citra normal dari 31,84 ke 38,94 dB; kernel median besar menghapus bercak kecil (Bagian 4).

\- Rangkaian praproses final menaikkan KB kanal R pada 4 dari 5 kondisi (gelap +69,5%, bayangan +63,2%, kontras rendah +43,6%, normal +22,1%) dan menurunkan simpangan baku daun sehat di semua kondisi tanpa menimbulkan bercak palsu (Bagian 5).



\## Parameter praproses final



Tersimpan di `hasil/param\_praproses.json`: lebar 640, gamma 1,0 (nonaktif), CLAHE kanal V clip 2,0 tile 4, penapis median kernel 3, penajaman k 0,0 (nonaktif).



