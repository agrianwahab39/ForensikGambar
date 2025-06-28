# ForensikGambar

ForensikGambar adalah sistem analisis forensik gambar dan video berbasis Python.
Repo ini menyediakan pipeline lengkap untuk mendeteksi tanda-tanda manipulasi
pada citra maupun video. Modul inti mencakup analisis ELA, pendeteksian
copy-move, analisis frekuensi, tekstur, tepi, iluminasi, serta sistem
klasifikasi berbasis pembelajaran mesin.

## Fitur Utama

- **Validasi dan Pra-pemrosesan** – pemeriksaan format, ekstraksi metadata EXIF,
  dan optimalisasi ukuran gambar.
- **Error Level Analysis** – ELA multi-kualitas untuk menilai artefak kompresi.
- **Deteksi Copy‑Move** – kombinasi SIFT/ORB/AKAZE dan pencocokan blok.
- **Analisis Noise, Frekuensi, Tekstur, Edge, dan Iluminasi** untuk menemukan
  inkonsistensi.
- **Klasifikasi Manipulasi** – penggabungan skor tradisional dengan model
  Random Forest, SVM, dan simulasi Neural Network.
- **Ekspor Hasil** ke PNG, PDF, dan DOCX serta paket komprehensif.
- **Manajemen Riwayat** – penyimpanan ringkasan analisis beserta thumbnail.
- **Dukungan Video** melalui modul `ForensikVideo` dan dashboard Streamlit.

## Instalasi

Proyek ini memerlukan Python 3.8 atau lebih baru. Beberapa dependensi utama:

- `opencv-python` dan `opencv-contrib-python`
- `numpy`, `scipy`, `scikit-image`, `scikit-learn`
- `Pillow`, `imagehash`
- `matplotlib`, `seaborn`, `reportlab`
- `streamlit`, `plotly` (untuk dashboard)

Instalasi dapat dilakukan dengan `pip`:

```bash
pip install opencv-python opencv-contrib-python numpy Pillow scikit-image
pip install scikit-learn matplotlib seaborn reportlab streamlit plotly imagehash
```

Pastikan juga paket `python-docx` dan `weasyprint` terpasang bila ingin mengekspor
laporan DOCX/PDF.

## Penggunaan

### Analisis Gambar

Jalankan `main.py` dengan path gambar yang ingin dianalisis:

```bash
python main.py contoh.jpg --output-dir ./hasil
```

Opsi tambahan:

- `--export-all` – mengekspor paket lengkap (visualisasi, laporan DOCX/PDF).
- `--export-vis` – hanya menyimpan visualisasi hasil.
- `--export-report` – hanya mengekspor laporan DOCX.

Hasil analisis akan disimpan di folder yang ditentukan.

### Analisis Video

Modul `ForensikVideo.py` menyediakan pipeline lima tahap untuk mendeteksi
manipulasi video. Contoh pemanggilan:

```bash
python ForensikVideo.py -i video.mp4 -o ./hasil_video
```

### Dashboard Streamlit

Antarmuka web interaktif tersedia melalui `streamlit_app.py`:

```bash
streamlit run streamlit_app.py
```

Dashboard ini memudahkan peninjauan riwayat analisis serta visualisasi berbagai
metrik forensik.

## Struktur Repo Singkat

- `validation.py` – fungsi validasi file dan pra‑proses.
- `ela_analysis.py` – implementasi Error Level Analysis multi-kualitas.
- `feature_detection.py` dan `copy_move_detection.py` – deteksi fitur dan
  copy‑move.
- `advanced_analysis.py` – analisis noise, frekuensi, tekstur, edge, iluminasi,
  serta statistik citra.
- `jpeg_analysis.py` – pemeriksaan artefak JPEG dan JPEG ghost.
- `classification.py` – sistem klasifikasi manipulasi.
- `export_utils.py` – ekspor hasil ke berbagai format.
- `visualization.py` – pembuatan visualisasi hasil.
- `history_manager.py` dan `utils.py` – manajemen riwayat dan fungsi utilitas.
- `streamlit_app.py` – dashboard berbasis Streamlit.

## Lisensi

Kode dalam repositori ini dirilis dengan lisensi MIT.

