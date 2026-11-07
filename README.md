# Brain Tumor Model

Pipeline Computer-Aided Diagnosis (CAD) dua tahap untuk citra MRI otak:

1. **Segmentasi:** Attention U-Net untuk memprediksi mask tumor.
2. **ROI bridge:** masking dan cropping menggunakan mask prediksi.
3. **Klasifikasi:** ensemble EfficientNet-B4 dan ResNet-50 untuk kelas `glioma`, `meningioma`, `notumor`, dan `pituitary`.

## Isi repository

- `two_stage_brain_tumor_cad_trained.ipynb`: notebook berisi persiapan data, EDA, pelatihan, evaluasi, Grad-CAM, inferensi, serta ekspor artefak deployment. Output eksekusi yang tersimpan ikut disertakan.

## Menjalankan notebook

1. Buka notebook di Google Colab. GPU disarankan untuk pelatihan.
2. Siapkan dataset `indk214/brain-tumor-dataset-segmentation-and-classification` secara terpisah. Dataset dan bobot model tidak disertakan dalam repository ini.
3. Pada Tahap 0 dan Tahap 1, sesuaikan `USE_DRIVE`, `DATA_ROOT`, dan `WORK_DIR` dengan lokasi data serta folder keluaran Anda. Konfigurasi saat ini memakai Google Drive di Colab.
4. Pastikan direktori dataset memiliki folder `Segmentation` dan `Classification`; folder klasifikasi memiliki split `Training` dan `Testing`.
5. Jalankan sel secara berurutan. Tahap 0 memasang paket utama. Sesuaikan `TRAIN_SEG` dan `TRAIN_CLS` apabila ingin memuat checkpoint yang telah tersedia.
6. Tahap 20 mengekspor checkpoint, konfigurasi, histori, prediksi, dan script `cad_inference.py` ke direktori keluaran.

Notebook menyertakan pembagian data stratified, pemeriksaan duplikasi/kebocoran data, evaluasi segmentasi dan klasifikasi, confusion matrix, ROC, serta visualisasi prediksi.

Proyek ini ditujukan untuk pembelajaran dan penelitian; belum divalidasi untuk penggunaan klinis.
