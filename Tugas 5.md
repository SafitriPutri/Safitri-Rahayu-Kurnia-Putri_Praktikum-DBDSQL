# Laporan SQL Tugas 5

## 1. Mendownload dan menjalankan code sql database_universitas
```sql
create database sampel_university;
use sampel_university;

create table classroom
	(building		varchar(15),
	 room_number		varchar(7),
	 capacity		numeric(4,0),
	 primary key (building, room_number)
	);
--- (dan seterusnya sesuai dengan code yang diberikan)
```
code sql database_universitas : https://drive.google.com/file/d/1GKNNDOIfTS4f3dfVZdmr7suOlx5_MKyL/view?usp=drive_link

## 2. Menampilkan kolom NIM, Nama, Angkatan, Program_Studi, Seleksi_Masuk Mahasiswa dari database Akademik yang telah dibuat sebelumnya
```sql
SELECT 
    student.ID AS NIM,
    student.name AS Nama,
    student.dept_name AS Program_Studi,
    takes.semester AS Seleksi_Masuk,
    takes.year AS Angkatan
FROM student
JOIN takes ON student.ID = takes.ID;
```
Penjelasan :
SQL di atas digunakan untuk mengambil data dari tabel "student" dan "takes" dengan menggabungkan kedua tabel tersebut berdasarkan nilai kolom "ID" yang sama. Hasilnya akan menampilkan kolom-kolom seperti NIM (ID mahasiswa), Nama, Program Studi, Seleksi Masuk, dan Angkatan. Dengan menggunakan query tersebut, user dapat melihat informasi tentang mahasiswa, termasuk nama, program studi, semester seleksi masuk, dan tahun angkatan.

Setelah dijalankan maka hasilnya seperti berikut : 

![image](https://github.com/SafitriPutri/Safitri-Rahayu-Kurnia-Putri_Praktikum-DBDSQL/assets/117289241/568d7d73-986c-47ce-8760-23cd6e1d6cb0)



## 3. Menampilkan semua nama student beserta nama department yang memiliki total SKS (total credit) lebih dari 100
```sql
SELECT s.name AS student_name, d.dept_name AS department_name
FROM student s
JOIN department d ON s.dept_name = d.dept_name
WHERE s.tot_cred > 100;
```
Penjelasan :
SQL di atas digunakan untuk mengambil data dari tabel "department" dan "student" dengan menggabungkan kedua tabel tersebut berdasarkan nilai kolom "dept_name" yang sama. Hasilnya akan menampilkan kolom-kolom seperti Program Studi dan Jurusan. Dengan menggunakan query, user dapat melihat daftar program studi beserta jurusan yang terdapat dalam tabel tersebut, yang diurutkan berdasarkan nama program studi dan jurusan.

Setelah dijalankan maka hasilnya seperti berikut :

![image](https://github.com/SafitriPutri/Safitri-Rahayu-Kurnia-Putri_Praktikum-DBDSQL/assets/117289241/f1390ae8-f8d7-4d13-9791-ffdd284aa91e)
