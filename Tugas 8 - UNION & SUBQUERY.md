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
