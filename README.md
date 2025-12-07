# APPLIED_ML_TugasMID_Rahmadani_105841117123

# Prediksi Jenis Wilayah Sekolah (Urban vs Rural)  
**Rahmadani – 105841117123 – 5AI-A – Desember 2025**

## 1. Business Understanding  
Konteks: Sekolah dasar & menengah di Indonesia  
Permasalahan: Ketimpangan fasilitas dan kualitas pendidikan Urban vs Rural  
Tujuan: Membantu Dinas Pendidikan memetakan kebutuhan sekolah & mengidentifikasi faktor paling berpengaruh  

## 2. Data Understanding  
**Sumber**: Rapor Publik Asesmen Nasional 2024–2025  
Link: https://data.kemendikdasmen.go.id/...  
**Target**: `jenis_wilayah` → Urban / Rural  
**Fitur utama** (numerik): jumlah_peserta_didik, rasio_pendidik_peserta_didik, APK, BBS, COP, …  
**Fitur kategorikal**: jenis_sek, kurikulum, ketersediaan_internet, status_sekolah  

## 3. Data Preparation  
- Hapus duplikat  
- Missing value: numerik → median, kategorikal → mode  
- Outlier → IQR clipping  
- Encoding: One-Hot & Label Encoding  
- Normalisasi tidak dilakukan (Random Forest)  

## 4. Modeling  
**Algoritma**: Random Forest Classifier  
**Alasan pemilihan**: tahan noise, tidak butuh scaling, mixed data type, feature importance  
**Parameter**: n_estimators=200, max_depth=15, class_weight='balanced'  

## 5. Evaluation  
| Metrik          | Nilai    |
|-----------------|----------|
| Accuracy        | 92.4%    |
| Precision Rural | 0.94     |
| Recall Rural    | 0.87     |
| F1-Score (macro)| 0.92     |

## 6. Deployment (Gradio)  
Input: jumlah siswa, guru, rasio, APK, BBS, kurikulum, status sekolah, dll.  
Output: Prediksi Urban/Rural + probabilitas + 5 fitur paling berpengaruh  
`python PROGRAM/deploy_gradio.py`

## File Penting  
- LK Perancangan Project → `Reports/Rahmadani - LK Perancangan Project.pdf`  
- Notebook lengkap → `Notebook/model_prediksi_jenis_wilayah.ipynb`  
- Model → `Models/rf_pipeline_model.pkl`  
- Aplikasi → `PROGRAM/deploy_gradio.py`
