#Database Universias.md
Pertama mendownload dan menjalankan file sql berikut :

create database sampel_university;
use sampel_university;

create table classroom
	(building		varchar(15),
	 room_number		varchar(7),
	 capacity		numeric(4,0),
	 primary key (building, room_number)
  );
....
