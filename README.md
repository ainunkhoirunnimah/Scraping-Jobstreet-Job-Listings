# Scraping Data Lowongan Pekerjaan Jobstreet
Implementasi scraping data menggunakan Python dari website Jobstreet untuk analisis informasi lowongan pekerjaan terkini di Indonesia.

## Penjelasan Data

Data yang diambil berasal dari situs Jobstreet Indonesia, khususnya lowongan pekerjaan Data Scientist dengan kriteria berikut:

* Gaji minimal Rp 2.000.000,-
* Status pekerjaan: Full-time
* Waktu posting: Dalam 30 hari terakhir

### Fitur yang dikumpulkan:

* Judul pekerjaan
* Perusahaan
* Lokasi
* Rentang gaji
* Deskripsi singkat pekerjaan

Jumlah data yang dikumpulkan bergantung pada banyaknya lowongan yang tersedia di halaman hasil pencarian pada saat scraping dilakukan.

## Proses Scraping

### Tools:

* **Python**: bahasa pemrograman utama.
* **requests**: library Python untuk mengirim permintaan HTTP.
* **BeautifulSoup (bs4)**: parsing HTML untuk ekstraksi data dari halaman web.
* **pandas**: untuk menyusun dan menyimpan data dalam bentuk tabel.

### Flow Scraping:

1. Menentukan URL pencarian pekerjaan dengan parameter yang diinginkan.
2. Menyiapkan header HTTP agar terlihat seperti permintaan dari browser biasa (menggunakan User-Agent).
3. Mengirim permintaan HTTP menggunakan `requests.get()`.
4. Mengambil dan parsing konten HTML menggunakan BeautifulSoup.
5. Mengekstraksi fitur yang diinginkan dari konten HTML tersebut.

## Proses Preprocessing

Proses preprocessing dilakukan untuk membersihkan dan menyusun ulang data sebelum digunakan lebih lanjut.

Contoh hasil preprocessing:

| Sebelum Preprocessing                    | Setelah Preprocessing              |
| ---------------------------------------- | ---------------------------------- |
| 'Rp. 3,000,000 - Rp. 5,000,000'          | \[3000000, 5000000]                |
| 'Jakarta Selatan'                        | 'Jakarta Selatan'                  |
| '\n\nData Scientist\nPT. XYZ\nJakarta\n' | 'Data Scientist, PT. XYZ, Jakarta' |

## Refleksi

### Kendala:

* Beberapa permintaan HTTP kadang diblokir atau menghasilkan data kosong karena deteksi aktivitas bot oleh situs Jobstreet.
* Format data yang tidak konsisten menyebabkan kesulitan saat preprocessing.

### Solusi:

* Menggunakan User-Agent yang menyerupai browser umum untuk menghindari pemblokiran.
* Mengimplementasikan logika parsing tambahan untuk menangani data yang memiliki format berbeda.

