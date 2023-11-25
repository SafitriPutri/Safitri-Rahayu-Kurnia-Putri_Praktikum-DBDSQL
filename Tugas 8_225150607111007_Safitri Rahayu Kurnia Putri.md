# Laporan SQL Tugas 8

### 1. Lakukan perintah Insert seperti yang ada pada Perintah 6.7 untuk menambahkan data pada table Mahasiswa
```sql
INSERT INTO AKADEMIK.MAHASISWA
VALUES('155150404', 1,212,'JESSY',2016,'1999-2-10','BANDUNG','F'),
      ('155150405', 2 ,219,'BAMBANG',2014,'1996-9-27','MAKASSAR','M');
```
Perintah 6.7

### 2. Lakukan perintah DDL seperti yang ada pada Perintah 6.8 untuk membuat sebuah table baru Mahasiswa_Pindahan
```sql
CREATE TABLE AKADEMIK.MAHASISWA_PINDAHAN(
	NIM VARCHAR(15) NOT NULL PRIMARY KEY,
	ID_SELEKSI_MASUK SMALLINT,
	FOREIGN KEY (ID_SELEKSI_MASUK) REFERENCES AKADEMIK.SELEKSI_MASUK(ID_SELEKSI_MASUK),
	ID_PROGRAM_STUDI SMALLINT,
	FOREIGN KEY (ID_PROGRAM_STUDI) REFERENCES AKADEMIK.PROGRAM_STUDI(ID_PROGRAM_STUDI),
	NAMA VARCHAR(45),
	ANGKATAN SMALLINT,
	TGL_LAHIR DATE,
	KOTA_LAHIR VARCHAR(60),
	JENIS_KELAMIN CHAR(1) CHECK (JENIS_KELAMIN IN ('M','F'))
);
```
Perintah 6.8

### 3. Lakukan perintah Insert seperti yang ada pada Perintah 6.9 untuk menambahkan data pada table Mahasiswa_Pindahan
```sql
CREATE TABLE AKADEMIK.MAHASISWA_PINDAHAN(
	NIM VARCHAR(15) NOT NULL PRIMARY KEY,
	ID_SELEKSI_MASUK SMALLINT,
	FOREIGN KEY (ID_SELEKSI_MASUK) REFERENCES AKADEMIK.SELEKSI_MASUK(ID_SELEKSI_MASUK),
	ID_PROGRAM_STUDI SMALLINT,
	FOREIGN KEY (ID_PROGRAM_STUDI) REFERENCES AKADEMIK.PROGRAM_STUDI(ID_PROGRAM_STUDI),
	NAMA VARCHAR(45),
	ANGKATAN SMALLINT,
	TGL_LAHIR DATE,
	KOTA_LAHIR VARCHAR(60),
	JENIS_KELAMIN CHAR(1) CHECK (JENIS_KELAMIN IN ('M','F'))
);
```
Perintah 6.9

### 4. Tampilkan NIM, NAMA, JENIS_KELAMIN, KOTA LAHIR dan ANGKATAN dari Mahasiswa yang memiliki Kota Lahir dengan inisial B dan dari Mahasiswa_Pindahan yang memiliki Nama dengan inisial D. Urutkan berdasarkan NIM.

### 5. Tampilkan NIM, NAMA, JENIS_KELAMIN, KOTA LAHIR dan ANGKATAN dari Mahasiswa Angkatan 2015 dan dari Mahasiswa_Pindahan tetapi kecuali Mahasiswa_Pindahan yang memiliki Kota Lahir dengan inisial M urutkan berdasarkan NIM.

----------------
### Jawaban
### 1. Pertama membuat code sql dari desain sql berikut :
![image](https://github.com/SafitriPutri/Safitri-Rahayu-Kurnia-Putri_Praktikum-DBDSQL/assets/117289241/31040a01-7180-41c9-995f-b391b175e4e4)

### Code sql :
```sql
CREATE DATABASE akademik;
USE akademik;

CREATE TABLE FAKULTAS (
  ID_FAKULTAS SMALLINT UNSIGNED NOT NULL AUTO_INCREMENT,
  FAKULTAS VARCHAR(45) NULL,
  PRIMARY KEY(ID_FAKULTAS)
);

CREATE TABLE JURUSAN (
  ID_JURUSAN SMALLINT UNSIGNED NOT NULL AUTO_INCREMENT,
  FAKULTAS_ID_FAKULTAS SMALLINT UNSIGNED NOT NULL,
  JURUSAN VARCHAR(45) NULL,
  PRIMARY KEY(ID_JURUSAN),
  INDEX JURUSAN_FKIndex1(FAKULTAS_ID_FAKULTAS)
);

CREATE TABLE MAHASISWA (
  NIM VARCHAR(15) NOT NULL AUTO_INCREMENT,
  SELEKSI_MASUK_ID_SELEKSI_MASUK SMALLINT UNSIGNED NOT NULL,
  PROGRAM_STUDI_ID_PROGRAM_STUDI SMALLINT UNSIGNED NOT NULL,
  NAMA VARCHAR(45) NULL,
  ANGKATAN SMALLINT UNSIGNED NULL,
  TGL_LAHIR DATE NULL,
  KOTA_LAHIR VARCHAR(60) NULL,
  JENIS_KELAMIN CHAR(1) NULL,
  PRIMARY KEY(NIM),
  INDEX MAHASISWA_FKIndex1(PROGRAM_STUDI_ID_PROGRAM_STUDI),
  INDEX MAHASISWA_FKIndex2(SELEKSI_MASUK_ID_SELEKSI_MASUK)
);

CREATE TABLE PROGRAM_STUDI (
  ID_PROGRAM_STUDI SMALLINT UNSIGNED NOT NULL AUTO_INCREMENT,
  STRATA_ID_STRATA SMALLINT UNSIGNED NOT NULL,
  JURUSAN_ID_JURUSAN SMALLINT UNSIGNED NOT NULL,
  PROGRAM_STUDI VARCHAR(60) NULL,
  PRIMARY KEY(ID_PROGRAM_STUDI),
  INDEX PROGRAM_STUDI_FKIndex1(JURUSAN_ID_JURUSAN),
  INDEX PROGRAM_STUDI_FKIndex2(STRATA_ID_STRATA)
);

CREATE TABLE SELEKSI_MASUK (
  ID_SELEKSI_MASUK SMALLINT UNSIGNED NOT NULL AUTO_INCREMENT,
  SINGKAT VARCHAR(12) NULL,
  SELEKSI_MASUK VARCHAR(45) NULL,
  PRIMARY KEY(ID_SELEKSI_MASUK)
);

CREATE TABLE STRATA (
  ID_STRATA SMALLINT UNSIGNED NOT NULL AUTO_INCREMENT,
  SINGKAT VARCHAR(10) NULL,
  STRATA VARCHAR(45) NULL,
  PRIMARY KEY(ID_STRATA)
);
```
### Setelah itu lakukan seperti soal nomor 1
Code sql :
```sql
INSERT INTO AKADEMIK.MAHASISWA
VALUES('155150404', 1,212,'JESSY',2016,'1999-2-10','BANDUNG','F'),
      ('155150405', 2 ,219,'BAMBANG',2014,'1996-9-27','MAKASSAR','M');
```
### Penjelasan code :
Kode SQL tersebut berfungsi untuk memasukkan data ke dalam tabel AKADEMIK.MAHASISWA. Perintah INSERT INTO berfungsi untuk menunjukkan bahwa user akan memasukkan data ke dalam tabel AKADEMIK.MAHASISWA.
Kemudian, perintah VALUES digunakan untuk menentukan nilai-nilai yang akan dimasukkan ke dalam tabel. Setiap nilai diapit oleh tanda kurung dan dipisahkan oleh tanda koma.

### 2. Membuat sebuah table baru Mahasiswa_Pindahan
Code sql :
```sql
CREATE TABLE AKADEMIK.MAHASISWA_PINDAHAN(
	NIM VARCHAR(15) NOT NULL PRIMARY KEY,
	ID_SELEKSI_MASUK SMALLINT,
	FOREIGN KEY (ID_SELEKSI_MASUK) REFERENCES AKADEMIK.SELEKSI_MASUK(ID_SELEKSI_MASUK),
	ID_PROGRAM_STUDI SMALLINT,
	FOREIGN KEY (ID_PROGRAM_STUDI) REFERENCES AKADEMIK.PROGRAM_STUDI(ID_PROGRAM_STUDI),
	NAMA VARCHAR(45),
	ANGKATAN SMALLINT,
	TGL_LAHIR DATE,
	KOTA_LAHIR VARCHAR(60),
	JENIS_KELAMIN CHAR(1) CHECK (JENIS_KELAMIN IN ('M','F'))
);
```
### Penjelasan code :
Kode SQL di atas digunakan untuk membuat tabel baru bernama `AKADEMIK.MAHASISWA_PINDAHAN` yang memiliki beberapa kolom dengan tipe data yang berbeda.
1. `NIM`: Kolom ini memiliki tipe data `VARCHAR(15)` yang artinya kolom teks dengan panjang maksimal 15 karakter. Kolom ini juga diberikan batasan `NOT NULL`, yang artinya nilai di kolom ini tidak boleh kosong. Kolom `NIM` ditetapkan sebagai kunci utama (`PRIMARY KEY`).
2. `ID_SELEKSI_MASUK`: Kolom ini memiliki tipe data `SMALLINT` (tipe data bilangan bulat kecil). Kolom ini digunakan sebagai `FOREIGN KEY` yang merujuk pada kolom `ID_SELEKSI_MASUK` pada tabel `AKADEMIK.SELEKSI_MASUK`.
3. `ID_PROGRAM_STUDI`: Kolom ini memiliki tipe data `SMALLINT` dan digunakan sebagai `FOREIGN KEY` yang merujuk ke kolom `ID_PROGRAM_STUDI` pada tabel `AKADEMIK.PROGRAM_STUDI`.
4. `NAMA`: Kolom ini memiliki tipe data `VARCHAR(45)` yang artinya kolom teks dengan panjang maksimal 45 karakter. Kolom ini menyimpan nama mahasiswa.
5. `ANGKATAN`: Kolom ini memiliki tipe data `SMALLINT` dan menyimpan tahun angkatan mahasiswa.
6. `TGL_LAHIR`: Kolom ini memiliki tipe data `DATE` dan menyimpan tanggal lahir mahasiswa.
7. `KOTA_LAHIR`: Kolom ini memiliki tipe data `VARCHAR(60)` yang artinya kolom teks dengan panjang maksimal 60 karakter. Kolom ini menyimpan kota kelahiran mahasiswa.
8. `JENIS_KELAMIN`: Kolom ini memiliki tipe data `CHAR(1)` yang artinya kolom teks dengan panjang 1 karakter. Kolom ini memiliki batasan (`CHECK`) yang memastikan bahwa nilai yang diterima hanya boleh 'M' atau 'F', yang mewakili jenis kelamin laki-laki atau perempuan.

### 3. Melakukan perintah Insert
Code sql :
```sql
INSERT INTO MAHASISWA_PINDAHAN
	VALUES('155150500', 1, 211, 'BUDI', 2015, '1997-03-03', 'BANYUWANGI', 'M'),
	      ('155150501', 2, 212, 'ANDI', 2015, '1997-02-21', 'JAKARTA', 'M'),
	      ('155150502', 2, 211, 'DIMAS', 2015, '1998-04-11', 'SURABAYA', 'M'),
	      ('155150503', 2, 211, 'DIDIN', 2015, '1997-02-26', 'BANDUNG', 'M');
```
### Penjelasan code :
Kode SQL tersebut berfungsi untuk memasukkan data ke dalam tabel AKADEMIK.MAHASISWA_PINDAHAN. Perintah INSERT INTO berfungsi untuk menunjukkan bahwa user akan memasukkan data ke dalam tabel AKADEMIK.MAHASISWA_PINDAHAN.
Kemudian, perintah VALUES digunakan untuk menentukan nilai-nilai yang akan dimasukkan ke dalam tabel. Setiap nilai diapit oleh tanda kurung dan dipisahkan oleh tanda koma.

### 4. Menampilkan NIM, NAMA, JENIS_KELAMIN, KOTA LAHIR dan ANGKATAN dari Mahasiswa yang memiliki Kota Lahir dengan inisial B dan dari Mahasiswa_Pindahan yang memiliki Nama dengan inisial D. Diurutkan berdasarkan NIM
Code sql :
```sql
SELECT NIM, NAMA, JENIS_KELAMIN, KOTA_LAHIR, ANGKATAN
FROM MAHASISWA
WHERE KOTA_LAHIR LIKE 'B%'
UNION
SELECT NIM, NAMA, JENIS_KELAMIN, KOTA_LAHIR, ANGKATAN
FROM MAHASISWA_PINDAHAN
WHERE NAMA LIKE 'D%'
ORDER BY NIM;
```
### Penjelasan code : 
Kode SQL tersebut menggunakan perintah SELECT untuk mengambil data dari dua tabel, yaitu tabel `MAHASISWA` dan `MAHASISWA_PINDAHAN`, dengan beberapa kondisi tertentu.
Pertama, perintah SELECT akan mengambil kolom-kolom `NIM`, `NAMA`, `JENIS_KELAMIN`, `KOTA_LAHIR`, dan `ANGKATAN` dari tabel `MAHASISWA`.
Kemudian, perintah WHERE digunakan untuk menerapkan kondisi pada kolom `KOTA_LAHIR`. Hanya baris yang memiliki nilai `KOTA_LAHIR` yang diawali dengan huruf 'B' yang akan dipilih.
Selanjutnya, kata kunci UNION digunakan untuk menggabungkan hasil dari perintah SELECT sebelumnya dengan hasil dari perintah SELECT lainnya.
Pernyataan SELECT kedua akan mengambil kolom-kolom yang sama dari tabel `MAHASISWA_PINDAHAN`.
Kemudian, perintah WHERE digunakan untuk menerapkan kondisi pada kolom `NAMA`. Hanya baris yang memiliki nilai `NAMA` yang diawali dengan huruf 'D' yang akan dipilih.
Terakhir, perintah ORDER BY NIM digunakan untuk mengurutkan hasil berdasarkan kolom `NIM`.

### 5. Menampilkan NIM, NAMA, JENIS_KELAMIN, KOTA LAHIR dan ANGKATAN dari Mahasiswa Angkatan 2015 dan dari Mahasiswa_Pindahan tetapi kecuali Mahasiswa_Pindahan yang memiliki Kota Lahir dengan inisial M, diurutkan berdasarkan NIM
Code sql :
```sql
SELECT NIM, NAMA, JENIS_KELAMIN, KOTA_LAHIR, ANGKATAN
FROM MAHASISWA
WHERE ANGKATAN = 2015
UNION
SELECT NIM, NAMA, JENIS_KELAMIN, KOTA_LAHIR, ANGKATAN
FROM MAHASISWA_PINDAHAN
WHERE ANGKATAN = 2015 AND KOTA_LAHIR NOT LIKE 'M%'
ORDER BY NIM;
```
### Penjelasan code : 
Kode SQL tersebut menggunakan perintah SELECT untuk mengambil data dari dua tabel, yaitu tabel `MAHASISWA` dan `MAHASISWA_PINDAHAN`, dengan beberapa kondisi tertentu.
Pertama, perintah SELECT akan mengambil kolom-kolom `NIM`, `NAMA`, `JENIS_KELAMIN`, `KOTA_LAHIR`, dan `ANGKATAN` dari tabel `MAHASISWA`.
Kemudian, perintah WHERE digunakan untuk menerapkan kondisi pada kolom `ANGKATAN`. Hanya baris dengan nilai `ANGKATAN` dengan tahun 2015 yang akan dipilih dari tabel `MAHASISWA`.
Selanjutnya, kata kunci UNION digunakan untuk menggabungkan hasil dari perintah SELECT sebelumnya dengan hasil dari perintah SELECT lainnya.
Pernyataan SELECT kedua akan mengambil kolom-kolom yang sama dari tabel `MAHASISWA_PINDAHAN`.
Kemudian, perintah WHERE digunakan untuk menerapkan kondisi pada kolom `ANGKATAN` dan `KOTA_LAHIR`. Hanya baris dengan nilai `ANGKATAN` dengan tahun 2015 dan `KOTA_LAHIR` yang bukan berawalan huruf 'M' yang akan dipilih dari tabel `MAHASISWA_PINDAHAN`.
Terakhir, perintah ORDER BY NIM digunakan untuk mengurutkan hasil berdasarkan kolom `NIM`.
