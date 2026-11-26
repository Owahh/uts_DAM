# UTS Data Acquisition & Management

## Profil Mahasiswa
| **Name** | **Value** |
| :--- | :--- |
| Nama | I Gusti Agung Ngurah Bayu Hemaweda Jelantik |
| NIM | 2501010239 |
| Kelas | F |
| Jurusan | Informatika Manajemen Data Analis |

## Sumber Data
| Sumber | Judul | URL | Waktu Akses |
| :---: | :--- | :--- | :---: |
| Kaggle | Sales Minimarket Retail and Tourist in Bali | https://www.kaggle.com/datasets/trysuharso/sales-minimarket-retail-and-tourist-in-bali?select=bali_tourist.csv | 26 November 2026 |
| Portal Data KKP | Jumlah Kawasan Wisata Bahari yang dikelola oleh Kementerian Kelautan dan Perikanan | https://portaldata.kkp.go.id/api/portal/list_kawasan_bahari | 26 November 2026 |
| Wikipedia Bahasa Indonesia | Pariwisata di Bali | https://id.wikipedia.org/wiki/Pariwisata_di_Bali | 26 November 2026 |

## Data Ethics Checklist
| Aspek | Status (Ya/Tidak/NA) |
| :--- | :---: |
| Sumber data dan URL dicantumkan | YA |
| Lisensi data diperiksa dan dicatat | YA |
| robots.txt / Terms of Service diperiksa | TIDAK |
| Kolom PII diidentifikasi | TIDAK |
| PII dihapus, di-mask, atau di-pseudonimisasi | NA |
| Prinsip minimalisasi data diterapkan | YA |
| Potensi bias sampel dianalisis | NA |
| Tujuan penggunaan data dinyatakan eksplisit | NA |
| Rencana retensi dan penghapusan data ada | NA |

## Data Provenance Notes

### Berkas
#### A. Informasi Sumber Data
| Komponen | Keterangan |
| :--- | :--- |
| Nama sumber | Kaggle |
| Website | https://www.kaggle.com |
| Halaman Target | https://www.kaggle.com/datasets/trysuharso/sales-minimarket-retail-and-tourist-in-bali?select=bali_tourist.csv |
| Format Data | CSV |
| Bahasa pemrograman | Python 3.11 (3.11.4) |
| Library | `Pandas`, `OS` |
| Format output | CSV |
| Jenis Data | `Terstruktur` |

#### B. Informasi yang dikumpulkan
| Nama kolom | Keterangan |
| :--- | :--- |
| `year` | Tahun pencatatan kunjungan wisatawan |
| `area` | Kawasan geografis asal wisatawan (seperti `ASIA PACIFIC`, `ASEAN`, `AFRICA`, `AMERICA`, `EUROPE`, `MIDDLE EAST`, `OTHER NATIONALITIES`) |
| `country` | Negara asal wisatawan |
| `January` | Jumlah kunjungan wisatawan pada bulan Januari |
| `February` | Jumlah kunjungan wisatawan pada bulan Februari |
| `March` | Jumlah kunjungan wisatawan pada bulan Maret |
| `April` | Jumlah kunjungan wisatawan pada bulan April |
| `May` | Jumlah kunjungan wisatawan pada bulan Mei |
| `June` | Jumlah kunjungan wisatawan pada bulan Juni |
| `July` | Jumlah kunjungan wisatawan pada bulan Juli |
| `August` | Jumlah kunjungan wisatawan pada bulan Agustus |
| `September` | Jumlah kunjungan wisatawan pada bulan September |
| `October` | Jumlah kunjungan wisatawan pada bulan Oktober |
| `November` | Jumlah kunjungan wisatawan pada bulan November |
| `December` | Jumlah kunjungan wisatawan pada bulan Desember |

#### C. Tahapan pengumpulan data
| No | Tahapan | Deskripsi |
| :--- | :--- | :--- |
| 1 | Impor library | Mengimpor library `pandas` dan `os` untuk kebutuhan pembacaan, agregasi, serta pengelolaan file dataset. |
| 2 | Pembacaan dataset | Memuat dataset mentah dari file `data/raw/bali_tourist.csv` ke dalam DataFrame (`df`) menggunakan Pandas. |
| 3 | Pemeriksaan struktur data | Memeriksa daftar nama seluruh kolom (15 kolom) dan dimensi awal dataset yang terdiri dari 362 baris dan 15 kolom (`(362, 15)`). |
| 4 | Agregasi data | Mengelompokkan data berdasarkan kolom `year` dan `area` menggunakan `groupby(['year', 'area'], as_index=False).sum(numeric_only=True)` untuk menjumlahkan kunjungan bulanan per kawasan dan tahun (`df_area_year`), menghasilkan dimensi 14 baris dan 14 kolom. |
| 5 | Penyimpanan dataset | Menyimpan hasil akhir agregasi data ke dalam format CSV pada direktori `data/process/bali_tourist_aggregated.csv` tanpa indeks (`index=False`). |

---

### REST API
#### A. Informasi Sumber Data
| Komponen | Keterangan |
| :--- | :--- |
| Nama sumber | Portal Data Kementerian Kelautan dan Perikanan (KKP) |
| Website | https://portaldata.kkp.go.id |
| Halaman Target | https://portaldata.kkp.go.id/api/portal/list_kawasan_bahari (dengan parameter `limit=200`) |
| Format Data | JSON (respons REST API) |
| Bahasa pemrograman | Python 3.11 (3.11.4) |
| Library | `Requests`, `Pandas`, `JSON`, `OS` |
| Format output | CSV |
| Jenis Data | `Semi Terstruktur` |

#### B. Informasi yang dikumpulkan
| Nama kolom | Keterangan |
| :--- | :--- |
| `id` | ID unik data kelompok pengelola wisata bahari |
| `tahun` | Tahun pembentukan atau pencatatan data kelompok pengelola |
| `provinsi` | Nama provinsi lokasi wisata bahari |
| `id_prov` | Kode ID wilayah provinsi |
| `kabupaten` | Nama kabupaten atau kota lokasi wisata bahari |
| `id_kab` | Kode ID wilayah kabupaten atau kota |
| `kecamatan` | Nama kecamatan lokasi wisata bahari |
| `id_kec` | Kode ID wilayah kecamatan |
| `desa` | Nama desa atau kelurahan lokasi wisata bahari |
| `id_desa` | Kode ID wilayah desa atau kelurahan |
| `kelompok_pengelola` | Nama kelompok masyarakat atau lembaga pengelola wisata bahari |
| `lat` | Koordinat lokasi (tercatat nilai garis bujur pada respons API) |
| `long` | Koordinat lokasi (tercatat nilai garis lintang pada respons API) |
| `created_on` | Waktu (*timestamp*) pembuatan rekaman data pada sistem |
| `created_by` | Identitas pembuat rekaman data pada sistem |
| `updated_on` | Waktu (*timestamp*) pembaruan terakhir rekaman data |
| `updated_by` | Identitas pengguna yang terakhir memperbarui rekaman data |

#### C. Tahapan pengumpulan data
| No | Tahapan | Deskripsi |
| :--- | :--- | :--- |
| 1 | Impor library | Mengimpor library `requests`, `pandas`, `json`, dan `os` untuk kebutuhan pengambilan data API, pengolahan JSON/DataFrame, serta pengelolaan file. |
| 2 | Pengambilan data API | Mengirim permintaan HTTP `GET` ke endpoint `https://portaldata.kkp.go.id/api/portal/list_kawasan_bahari` dengan parameter `limit=200` dan *timeout* 30 detik, memvalidasi status respons (`response.raise_for_status()`), serta memetakannya ke format JSON (`result`). |
| 3 | Konversi & penyimpanan data mentah | Mengekstrak nilai `total_count` (`141`) dan array `"data"` menjadi DataFrame Pandas (`df_luwu`) berdimensi 141 baris dan 17 kolom, lalu menyimpannya ke direktori `data/raw/luwu_timur.csv`. |
| 4 | Seleksi kolom & agregasi data | Menghapus 4 kolom metadata (`created_on`, `created_by`, `updated_on`, dan `updated_by`) sehingga menyisakan 13 kolom utama (`df_cropped` berukuran `141 x 13`), serta membuat dataset agregasi berdasarkan `tahun` dan `provinsi` menggunakan `groupby(['tahun', 'provinsi'], as_index=False).agg(...)` dengan fungsi agregasi `first` pada kolom lokasi dan pengelola (`df_aggregat` berukuran `83 x 8`). |
| 5 | Penyimpanan dataset hasil olahan | Menyimpan dua file hasil pengolahan ke format CSV di direktori `data/process/`, yaitu `data/process/list_kawasan_bahari_cropped.csv` dan `data/process/list_kawasan_bahari_order_by.csv`. |

---

### Web Scrapping
#### A. Informasi Sumber Data
| Komponen | Keterangan |
| :--- | :--- |
| Nama sumber | Wikipedia Bahasa Indonesia |
| Website | https://id.wikipedia.org |
| Halaman Target | https://id.wikipedia.org/wiki/Pariwisata_di_Bali |
| Format Data | HTML |
| Bahasa pemrograman | Python 3.11 (3.11.4) |
| Library | `Requests`, `Pandas`, `BeautifulSoup`, `urllib.parse` (`urljoin`) |
| Format output | CSV |
| Jenis Data | `Tidak Terstruktur` |

#### B. Informasi yang dikumpulkan
| Nama kolom | Sumber HTML | Keterangan |
| :--- | :--- | :--- |
| `judul_tempat` | Atribut `title` pada tag `<a rel="mw:WikiLink">` di dalam `<section data-mw-section-id="8">` | Nama atau judul destinasi wisata di Bali |
| `url_tempat` | Atribut `href` pada tag `<a rel="mw:WikiLink">` di dalam `<section data-mw-section-id="8">` | Tautan URL menuju halaman Wikipedia masing-masing tempat wisata |

#### C. Tahapan pengumpulan data
| No | Tahapan | Deskripsi |
| :--- | :--- | :--- |
| 1 | Impor library | Mengimpor library `requests`, `pandas`, `BeautifulSoup` (`bs4`), dan `urljoin` (`urllib.parse`). |
| 2 | Pengambilan HTML | Menggunakan `requests.get()` dengan header `User-Agent` browser dan *timeout* 30 detik untuk mengakses halaman `https://id.wikipedia.org/wiki/Pariwisata_di_Bali` serta memvalidasi status respons (`200 OK`). |
| 3 | Parsing & seleksi bagian HTML | Menggunakan `BeautifulSoup` dengan parser `lxml` untuk membaca struktur HTML, kemudian memilih elemen `<section data-mw-section-id="8">` yang berisi daftar objek wisata di Bali. |
| 4 | Ekstraksi informasi | Menelusuri seluruh tag tautan `<a rel="mw:WikiLink">` di dalam `section` target, lalu mengekstrak atribut `title` sebagai `judul_tempat` dan atribut `href` sebagai `url_tempat` (terkumpul sebanyak 73 data). |
| 5 | Pembentukan DataFrame | Mengonversi hasil ekstraksi menjadi DataFrame Pandas (`df`) berdimensi 73 baris dan 2 kolom. |
| 6 | Penyimpanan dataset | Menyimpan hasil ekstraksi data mentah ke dalam file CSV di direktori `data/raw/data_wisata_bali.csv` dengan encoding `utf-8-sig` dan tanpa indeks (`index=False`). |
