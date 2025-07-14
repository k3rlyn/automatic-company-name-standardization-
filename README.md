# Automatic Company Name Standardization Tool

Aplikasi web berbasis Streamlit untuk melakukan standardisasi nama perusahaan menggunakan fuzzy matching dan AI (Google Gemini).

## Fitur Utama

- **Fuzzy Matching**: Mencocokkan nama perusahaan dengan database referensi
- **AI Standardization**: Menggunakan Google Gemini API untuk standardisasi nama
- **Double Check**: Fuzzy matching kedua untuk hasil AI
- **Batch Processing**: Memproses multiple files sekaligus
- **Location-aware**: Penanganan khusus berdasarkan alamat (contoh: Shopee Singapore vs Indonesia)

## Instalasi

### 1. Clone atau Download Files
Pastikan Anda memiliki file-file berikut:
- `app.py` (file utama aplikasi)
- `requirements.txt` (dependencies)

### 2. Install Dependencies
```bash
pip install -r requirements.txt
```

### 3. Dapatkan Google Gemini API Key
1. Kunjungi [Google AI Studio](https://makersuite.google.com/app/apikey)
2. Buat API key baru
3. Simpan API key dengan aman

### 4. Jalankan Aplikasi
```bash
streamlit run app.py
```

## Cara Penggunaan

### 1. Upload Files
- **Main Data File**: File Excel yang berisi nama perusahaan yang akan distandarisasi
- **Reference Files**: File Excel yang berisi nama perusahaan yang sudah distandarisasi (opsional)

### 2. Konfigurasi
- Masukkan **Gemini API Key** di sidebar
- Pilih kolom yang berisi **nama perusahaan**
- Pilih kolom **alamat** (opsional, membantu untuk matching berdasarkan lokasi)
- Atur **rate limit** untuk API calls

### 3. Proses
1. Klik "Start Processing"
2. Aplikasi akan melakukan 3 tahap:
   - **Fuzzy Matching 1**: Mencocokkan dengan database referensi
   - **AI Standardization**: Menggunakan Gemini untuk nama yang tidak cocok
   - **Fuzzy Matching 2**: Double check hasil AI

### 4. Download
- Download hasil dalam format Excel
- Lihat statistik dan nama yang tidak berhasil distandarisasi

## Format File Input

### Main Data File
Harus mengandung kolom:
- Nama perusahaan (bisa nama kolom apa saja)
- Alamat (opsional)

### Reference Files
Harus mengandung kolom:
- `company_name_standardized`: Nama perusahaan yang sudah distandarisasi
- `company_name`: Nama perusahaan asli (opsional)

## Contoh Hasil Standardisasi

| Input | Output |
|-------|--------|
| BCA | PT Bank Central Asia Tbk |
| Mandiri | PT Bank Mandiri (Persero) Tbk |
| Shopee Indonesia | PT Shopee Internasional Indonesia |
| Shopee (Singapore) | Shopee Pte. Ltd. |

## Troubleshooting

### Error: "API connection failed"
- Pastikan API key valid
- Cek koneksi internet
- Pastikan quota API belum habis

### Error: "File loading failed"
- Pastikan file dalam format Excel (.xlsx atau .xls)
- Cek apakah file tidak corrupt
- Pastikan file memiliki kolom yang diperlukan

### Performance Issues
- Kurangi rate limit jika terlalu banyak error
- Proses file dalam batch yang lebih kecil
- Pastikan koneksi internet stabil

## Rate Limiting

- Default: 10 requests per minute
- Dapat disesuaikan di sidebar
- Terlalu tinggi dapat menyebabkan error quota
- Terlalu rendah akan memperlambat proses

## Catatan Penting

1. **API Cost**: Setiap request ke Gemini API dikenakan biaya
2. **Data Privacy**: Data diproses lokal di browser, tidak disimpan di server
3. **File Size**: Untuk file besar, proses mungkin membutuhkan waktu lama
4. **Backup**: Selalu backup data asli sebelum memproses

## Support

Jika mengalami masalah:
1. Cek console browser untuk error messages
2. Pastikan semua dependencies terinstall
3. Verifikasi format file input
4. Cek API key dan quota

---

**Dibuat oleh Kerlyn Deslia Andeskar menggunakan Streamlit dan Google Gemini AI**
