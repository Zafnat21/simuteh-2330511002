# simuteh-2330511002

SIMUTEH - Evaluasi Praktikum P1-P4 dan UTS P5-P6 Computer Vision UMMI - Zafnat Paaneah Matusal

# SIMUTEH: Evaluasi Praktikum Computer Vision P1-P4 dan UTS P5-P6

Repositori ini berisi pengerjaan evaluasi praktikum Computer Vision Pertemuan 1 sampai 4 dan UTS Pertemuan 5 sampai 6, studi kasus SIMUTEH (deteksi bercak cacar daun teh Exobasidium vexans).

- Nama: Zafnat Paaneah Matusal
- NIM: 2330511002
- Kelas: 7A
- SEED dataset: 1002

## Struktur

- `notebook/`: notebook pengerjaan per bagian (B1 sampai B5, P5_tepi, P6_morfologi)
- `src/`: kode sumber (buat_dataset_sintetis.py, utils_cv.py, praproses.py, utils_tepi.py, bercak.py)
- `hasil/`: tabel, grafik, panel, dan parameter hasil pengerjaan
- `requirements.txt`: versi pustaka yang dipakai

## Cara menjalankan

1. Buka notebook di Google Colab.
2. Clone repositori ini, lalu masuk ke folder repo.
3. Bangkitkan dataset dengan perintah `python src/buat_dataset_sintetis.py` (folder `data/` tidak ikut di-commit).
4. Masuk ke folder `notebook`, lalu jalankan notebook dari atas sampai bawah (Restart & Run All).

## Ringkasan hasil

### P1-P4
- Kanal terbaik untuk kontras bercak adalah kanal R (Bagian 2).
- Perbaikan terbaik per kondisi: gamma untuk gelap dan terang, peregangan persentil untuk kontras rendah, CLAHE clip 2,0 tile 4 untuk bayangan (Bagian 3).
- Penapis pilihan median kernel 3 menaikkan PSNR 12 citra normal dari 31,84 ke 38,94 dB; kernel median besar menghapus bercak kecil (Bagian 4).
- Rangkaian praproses final menaikkan KB kanal R pada 4 dari 5 kondisi (gelap +69,5%, bayangan +63,2%, kontras rendah +43,6%, normal +22,1%) dan menurunkan simpangan baku daun sehat di semua kondisi tanpa menimbulkan bercak palsu (Bagian 5).

### P5-P6 (UTS)
- Deteksi tepi terbaik: Canny kanal R (F1 0,971 praproses; sigma 1,0 ambang 100/200 F1 0,981). Ambang otomatis dari median intensitas gagal di gelap/bayangan; ambang persentil ke-98 magnitudo setara ambang tetap pada kanal R.
- Bercak awal (median + 4xMAD kanal R) kasar: 171-222 komponen vs acuan 11/3/0; IoU daun awal 0,996-0,998.
- Opening SE elips 5 menurunkan komponen 222 ke 3, tetapi tulang daun lolos; closing hampir tidak mengubah apa pun. Eksperimen SE (1620 kombinasi): ukuran 7 menurunkan galat jumlah paling besar; elips 3x3 identik dengan silang 3x3.
- Saringan bentuk (luas >= 20, kebulatan >= 0,5, rasio <= 1,8) menurunkan galat jumlah ke 0,60/0,70/0,85 (berat/ringan/sehat); 11 dari 20 daun sehat tetap memiliki bercak palsu.
- Modul `bercak.py`: galat absolut rerata persen bercak 0,549; korelasi prediksi vs acuan 0,973; akurasi kelas 0,867 (52/60). Akurasi per kondisi: gelap 1,00; normal 0,92; bayangan 0,83; terang 0,83; kontras rendah 0,75.

## Parameter praproses final

Tersimpan di `hasil/param_praproses.json`: lebar 640, gamma 1,0 (nonaktif), CLAHE kanal V clip 2,0 tile 4, penapis median kernel 3, penajaman k 0,0 (nonaktif).

## Parameter bercak final

Tersimpan di `hasil/param_bercak.json`: kanal 2 (R), k 4,0, SE elips 5/5, luas_min 20, bulat_min 0,5, rasio_maks 1,8, batas_ringan 0,1%, batas_berat 2,0%, mm_per_px 0,4375.
