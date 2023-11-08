# Laporan SQL Sample University

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

## 2. Menampilkan semua nama Mahasiswa beserta nama department
```sql
SELECT student.name AS Nama_Mahasiswa, department.dept_name AS Nama_Department
FROM student
LEFT JOIN department ON student.dept_name = department.dept_name;
```
Setelah di jalankan maka hasilnya seperti berikut :

![image](https://github.com/SafitriPutri/Safitri-Rahayu-Kurnia-Putri_Praktikum-DBDSQL/assets/117289241/427e6dd2-ebf3-42b6-aa63-0217612ee272)


## 3. Menampilkan Nama Student dan Nama Department dengan Total SKS Lebih dari 100
