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
Setelah dijalankan maka hasilnya seperti berikut :

![image](https://github.com/SafitriPutri/Safitri-Rahayu-Kurnia-Putri_Praktikum-DBDSQL/assets/117289241/427e6dd2-ebf3-42b6-aa63-0217612ee272)


## 3. Menampilkan semua nama student beserta nama department yang memiliki total SKS (total credit) lebih dari 100
```sql
SELECT s.name AS student_name, d.dept_name AS department_name
FROM student s
JOIN department d ON s.dept_name = d.dept_name
WHERE s.tot_cred > 100;
```
Setelah dijalankan maka hasilnya seperti berikut :

![image](https://github.com/SafitriPutri/Safitri-Rahayu-Kurnia-Putri_Praktikum-DBDSQL/assets/117289241/c8724971-c2f1-4d8f-b453-1caafb463d6a)


## 4. Menampilkan nama student dan nama instructor yang bekerja pada department yang sama
```sql
SELECT s.name AS student_name, i.name AS instructor_name
FROM student s
JOIN instructor i ON s.dept_name = i.dept_name;
```
Setelah dijalankan maka hasilnya seperti berikut :

![image](https://github.com/SafitriPutri/Safitri-Rahayu-Kurnia-Putri_Praktikum-DBDSQL/assets/117289241/1c8ffeef-0736-49e5-af78-9533a0775bd6)
