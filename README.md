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






/*-------------------BASE DE DATOS RECURSIVA PERSONA---------------------------*/


create table Persona(
    id integer primary key,
    idPadre integer ,
    idMadre integer,
    nombre varchar(60),
    sexo varchar(20)
);

ALTER TABLE Persona ADD foreign key (idPadre) references Persona(id) on update NO ACTION on delete NO ACTION; 
ALTER TABLE Persona ADD foreign key (idPadre) references Persona(id) on update NO ACTION on delete NO ACTION; 


insert into Persona(id,idPadre,idMadre , nombre,sexo) values(1 ,NULL,NULL, "Joaquin Chumasero", "M")
,(2 ,NULL,NULL, "Fabiola Colque", "F")
,(3 ,1,2, "Pedro Chumasero Colque", "M")
,(4 ,null,null, "Ana Aguilera P.", "F")
,(5 ,3,4, "Joaquin Chumasero Aguilera", "M")
,(6 ,null,null, "Fabiola Mendez", "F")
,(7 ,5,6, "Joaquin JR. Chumasero Mendez", "M")
,(8 ,5,6, "Carla JR. Chumasero Mendez", "F")
,(9 ,null,null, "Patricia Fernandez", "F")
,(10 ,5,9, "Juan Chumasero Fernandez", "M");


/*select * from Persona; */




/* mostrar el id y nombre del papa de joaquin chumacero aguilera --------------------------------------------------*/

/*
select Padre.id, Padre.nombre
from Persona Hijo , Persona Padre
where Hijo.idPadre = Padre.id and Hijo.nombre = "Joaquin Chumasero Aguilera";   */
/* anidado------------*/
/*select id,nombre 
from Persona 
where id = (select idPadre
        from Persona
        where nombre = "Joaquin Chumasero Aguilera");
*/        
        
        

/*mostrar los hijos de joaquin chumasero aguilera --------------------------------------------------*/
select hijo.id, hijo.nombre
from Persona Hijo , Persona Padre
where hijo.idPadre = hijo.id and Padre.nombre = "Joaquin Chumasero Aguilera";   




