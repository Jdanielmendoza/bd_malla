# bd_malla
base de datos


/*------------------------------------------------------------------*/

create database malla_curricular; 
use malla_curricular; 

CREATE TABLE MATERIA (
	sigla varchar(20) primary key not null,
    nombre varchar(50) not null,
    credito	int 
); 
insert into materia(sigla,nombre,credito) values("INF211","ARQUITECTURA DE COMPUTADORAS",5),
												("MAT207","ECUACIONES DIFERENCIALES",4),
                                                ("INF312","BASE DE DATOS I",5);
SELECT * FROM materia;                                                 

/*-------------------------------------------------------------------------------------------------------*/

create table docente(
	ci int not null primary key,
    nombre varchar(60),
    sexo varchar(10),
    telefono varchar(10)
); 

insert into docente (ci,nombre,sexo,telefono) values(111,"alberto mollo","m","74504217"),
													(222,"francisco lopez","m","76504917"),
													(333,"angelica garzon","f","68045604"); 

create table grupo(
	id int not null primary key,
    nombre varchar(50),
    cupo int ,
    sigla_materia varchar(20),
    foreign key(sigla_materia) references materia(sigla) on update cascade on delete cascade
);

insert into grupo(id,nombre ,cupo, sigla_materia) values();

create table horario(
	idgrupo int ,
    idsigla varchar(20),
    dia varchar(20),
    horain varchar(20),
    horafin varchar(20),
    aula varchar(20),
    foreign key(idgrupo) references grupo(id) on update cascade on delete cascade,
     foreign key(idsigla) references materia(sigla) on update cascade on delete cascade
);



