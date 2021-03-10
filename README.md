# EMAP-TRIGGERS
create database Empresa_Agua_Potable;

	create table empre(
	RUC int primary key not null,
	nombre varchar(20),
	direccion varchar(50),
	telefono int,
	correo varchar(50),
	sitioweb varchar(50));

	create table fact(
	id_factura int primary key not null,
	fecha_pago date,
	total_pago decimal(6,2));

	create table mesE(
	id_mes int primary key not null,
	nombre_mes varchar (15),
	año varchar (10));

	create table clientesE(
	cedula_cliente int primary key not null,
	nombres varchar(50),
	apellidos varchar(50),
	telefono int,
	sector_vive varchar(40),
	tiene_convenio varchar(5));

	create table empleadosE(
	cedula_empleado int primary key not null,
	nombre varchar (20),
	apellido varchar(20),
	telefono int,
	direccion_e varchar(40),
	fecha_ing date,
	RUCpk int
	foreign key(RUCpk) references empre(RUC));

	create table medidor(
	numero_medidor int primary key not null,
	cedula_clientepk int,
	foreign key (cedula_clientepk) references clientesE(cedula_cliente));

	create table ConsumodeAgua(
	id_consumo varchar(15) primary key not null,
	numero_medidorpk int,
	consumo_agua varchar(10),
	monto_pago decimal(6,2),
	descripcion varchar(10),
	total decimal(6,2),
 	id_mespk int,
	cedula_clientepk int,
	foreign key (numero_medidorpk) references medidor(numero_medidor),
	foreign key (id_mespk) references mesE(id_mes),
	foreign key (cedula_clientepk) references clientesE(cedula_cliente));

	create table descrpagoE(
	id_pago int primary key not null, 
	montopago decimal(6,2),
	descripcion varchar(30), 
	total decimal(6,2),
	cedula_clientepk int,
	id_mespk int,
	foreign key (cedula_clientepk) references clientesE(cedula_cliente),
	foreign key (id_mespk) references mesE(id_mes));

	insert into empre(RUC,nombre,direccion,telefono,correo,sitioweb) values
	(1313001,'EMAP','Av.La cultura y calle 13',052365987,'emap@gmail.com','www.emap.com');
	select * from empre;

	insert into fact(id_factura,fecha_pago,total_pago) values
	(001,'2020-10-08',23.12);
	insert into fact(id_factura,fecha_pago,total_pago) values
	(002,'2020-09-08',9.78);
	insert into fact(id_factura,fecha_pago,total_pago) values
	(003,'2020-11-08',10.45);
	insert into fact(id_factura,fecha_pago,total_pago) values
	(004,'2020-10-08',45.50);
	insert into fact(id_factura,fecha_pago,total_pago) values
	(005,'2020-10-08',25.65);
	insert into fact(id_factura,fecha_pago,total_pago) values
	(006,'2020-11-08',17.89);
	insert into fact(id_factura,fecha_pago,total_pago) values
	(007,'2020-10-08',30.23);
	insert into fact(id_factura,fecha_pago,total_pago) values
	(008,'2020-09-08',50.61);
	insert into fact(id_factura,fecha_pago,total_pago) values
	(009,'2020-11-08',37.05);
	insert into fact(id_factura,fecha_pago,total_pago) values
	(010,'2020-10-08',19.99);
	select * from fact;

	insert into mesE(id_mes,nombre_mes,año) values
	(1,'Enero','2020');
	insert into mesE(id_mes,nombre_mes,año) values
	(2,'Febrero','2020');
	insert into mesE(id_mes,nombre_mes,año) values
	(3,'Marzo','2020');
	insert into mesE(id_mes,nombre_mes,año) values
	(4,'Abril','2020');
	insert into mesE(id_mes,nombre_mes,año) values
	(5,'Mayo','2020');
	insert into mesE(id_mes,nombre_mes,año) values
	(6,'Junio','2020');
	insert into mesE(id_mes,nombre_mes,año) values
	(7,'Julio','2020');
	select * from mesE;

	insert into clientesE(cedula_cliente,nombres,apellidos,telefono,sector_vive,tiene_convenio) values
	(131345677,'Elver Dorado','Castro Altamirano',0996777555,'Norte-Av.La Cultura','Sí');
	insert into clientesE(cedula_cliente,nombres,apellidos,telefono,sector_vive,tiene_convenio) values
	(131535355,'Mauro Enrique','Pinargote Macías',0987857744,'Norte-El Guabito','No');
	insert into clientesE(cedula_cliente,nombres,apellidos,telefono,sector_vive,tiene_convenio) values
	(131455543,'Rafael Antonio','Correa Castro',0988855711,'Centro-Calle 15','No');
	insert into clientesE(cedula_cliente,nombres,apellidos,telefono,sector_vive,tiene_convenio) values
	(132367262,'Andrea Liz','Castillo Ortíz',0956656662,'Sur-San Mateo','No');
	insert into clientesE(cedula_cliente,nombres,apellidos,telefono,sector_vive,tiene_convenio) values
	(132872278,'María Carmen','Ochoa Cruz',0977222111,'Sur-Av Barbasquillo','Sí');
	insert into clientesE(cedula_cliente,nombres,apellidos,telefono,sector_vive,tiene_convenio) values
	(130988484,'Cirilo Andrés','Moreira Nepal',0984472344,'Centro-Santa Martha','Sí');
	insert into clientesE(cedula_cliente,nombres,apellidos,telefono,sector_vive,tiene_convenio) values
	(132161091,'Derian Martín','España Hurtado',0985711220,'Norte-Las Cumbres','No');
	insert into clientesE(cedula_cliente,nombres,apellidos,telefono,sector_vive,tiene_convenio) values
	(131762719,'Carlos Jesús','Zambrano Reyes',0974692821,'Sur-Las Orquideas','Sí');
	insert into clientesE(cedula_cliente,nombres,apellidos,telefono,sector_vive,tiene_convenio) values
	(131727333,'Alex José','López Carrascal',0998746362,'Centro-El Rosal','Sí');
	insert into clientesE(cedula_cliente,nombres,apellidos,telefono,sector_vive,tiene_convenio) values
	(131618043,'Erick Alberto','Díaz Cedeño',0998484840,'Norte-La Proaño','Sí');
	select * from clientesE;

	insert into empleadosE(cedula_empleado,nombre,apellido,telefono,direccion_e,fecha_ing,RUCpk) values
	(1313457898,'Julio','Castro',0990367673,'Las acacias','2010-09-12',1313001);
	insert into empleadosE(cedula_empleado,nombre,apellido,telefono,direccion_e,fecha_ing,RUCpk) values
	(1314673726,'Alberto','Pinargote',096788484,'Los Esteros','2011-07-01',1313001);
	insert into empleadosE(cedula_empleado,nombre,apellido,telefono,direccion_e,fecha_ing,RUCpk) values
	(1389009881,'Juan','Macías',0983737373,'Santa Martha','2009-01-23',1313001);
	select * from empleadosE;

	insert into medidor(numero_medidor,cedula_clientepk) values
	(0022,131345677);
	insert into medidor(numero_medidor,cedula_clientepk) values
	(0033,131535355);
	insert into medidor(numero_medidor,cedula_clientepk) values
	(0044,132161091);
	insert into medidor(numero_medidor,cedula_clientepk) values
	(0055,132872278);
	insert into medidor(numero_medidor,cedula_clientepk) values
	(006,131727333);
	select * from medidor;

	insert into ConsumodeAgua(id_consumo,numero_medidorpk,consumo_a,monto_pago,descripcion,total,id_mespk,cedula_clientepk)values
	(10,0022,'123m3',58.55,'Paga',58.55,1,131535355)
	insert into ConsumodeAgua(id_consumo,numero_medidorpk,consumo_a,monto_pago,descripcion,total,id_mespk,cedula_clientepk)values
	(20,0033,'234m3',21.04,'Adeuda',21.04,2,132161091)
	insert into ConsumodeAgua(id_consumo,numero_medidorpk,consumo_a,monto_pago,descripcion,total,id_mespk,cedula_clientepk)values
	(30,0044,'456m3',120.45,'Adeuda',120.45,2,131345677)
	insert into ConsumodeAgua(id_consumo,numero_medidorpk,consumo_a,monto_pago,descripcion,total,id_mespk,cedula_clientepk)values
	(40,0055,'156m3',66.98,'Adeuda',66.98,4,132872278)
	insert into ConsumodeAgua(id_consumo,numero_medidorpk,consumo_a,monto_pago,descripcion,total,id_mespk,cedula_clientepk)values
	(50,006,'56m3',16.08,'Adeuda',16.08,3,131727333)
	select * from ConsumodeAgua

	insert into descrpagoE(id_pago,montopago,descripcion,total,cedula_clientepk,id_mespk) values
	(101,10.50,'Deuda',0.00,131345677,1);
	insert into descrpagoE(id_pago,montopago,descripcion,total,cedula_clientepk,id_mespk) values
	(102,34.76,'Deuda',0.00,131535355,2);
	insert into descrpagoE(id_pago,montopago,descripcion,total,cedula_clientepk,id_mespk) values
	(103,30.15,'Paga',30.15,132161091,3);
	insert into descrpagoE(id_pago,montopago,descripcion,total,cedula_clientepk,id_mespk) values
	(104,54.07,'Deuda',0.00,131618043,4);
	insert into descrpagoE(id_pago,montopago,descripcion,total,cedula_clientepk,id_mespk) values
	(105,19.56,'Deuda',0.00,132367262,5);
	insert into descrpagoE(id_pago,montopago,descripcion,total,cedula_clientepk,id_mespk) values
	(106,78.99,'Paga',78.99,132872278,6);
	insert into descrpagoE(id_pago,montopago,descripcion,total,cedula_clientepk,id_mespk) values
	(107,10.79,'Paga',10.79,131762719,7);
	insert into descrpagoE(id_pago,montopago,descripcion,total,cedula_clientepk,id_mespk) values
	(108,55.90,'Paga',55.90,131455543,1);
	insert into descrpagoE(id_pago,montopago,descripcion,total,cedula_clientepk,id_mespk) values
	(109,220.71,'Paga',220.71,130988484,2);
	insert into descrpagoE(id_pago,montopago,descripcion,total,cedula_clientepk,id_mespk) values
	(110,64.22,'Paga',64.22,131727333,3);
	select * from descrpagoE;

	-- Esta tabla se crea para actualizar pagos mediante TRIGGERS -- 
	create table historialPagosE (
	fecha date,
	cedula_clientepk int,
	descripcion varchar(30),
	usuario varchar(80));
	select * from historialPagosE;

	-- ACTUALIZAR PAGO --
	create trigger TR_PagoActualizado 
	on descrpagoE for update 
	as
	set nocount on
	declare @cedula_clientepk int
	select @cedula_clientepk = cedula_clientepk  from inserted
	insert into historialPagosE values(GETDATE(),@cedula_clientepk,
	'Pago Actualizado',SYSTEM_USER)
	go
	update descrpagoE set total = 10.50, descripcion ='Paga' where 
	cedula_clientepk = 131345677
	select * from historialPagosE
	select * from descrpagoE


	-- CURSOR --
	declare  @cedula_cliente char(30),
			 @nombres char(60),
			 @numero_medidor char(12),
			 @consumo_agua char(12),
			 @mes char(10),
			 @descripcion char(10),
			 @total char(10)
	declare cursor8 cursor 
	for select cli.cedula_cliente,cli.nombres,M.numero_medidorpk,M.consumo_agua,j.nombre_mes,descripcion,total
	from clientesE cli inner join ConsumodeAgua M on  cli.cedula_cliente = M.cedula_clientepk 
	inner join mesE  j on j.id_mes = cli.cedula_cliente
	open cursor8
	fetch cursor8 into @cedula_cliente,
					   @nombres,@apellidos,
					   @numero_medidor,
					   @consumo_agua
	print 'cedula_cliente  nombres  apellidos  numero_medidor  consumo_agua'
	print'------------------------------------------------------------------'
	while @@FETCH_STATUS=0
		begin
		print @cedula_cliente+ '' +@nombres+ '' +@apellidos+ '' +@numero_medidor+ '' +@consumo_agua
		fetch cursor8 into @cedula_cliente,
					       @nombres,
					       @apellidos,
					       @numero_medidor,
					       @consumo_agua
		end
	close cursor8
	deallocate cursor8

	select * from ConsumodeAgua

	-- PROCEDIMIENTO ALMACENADO --
	create procedure consumo1
			 @cedula_cliente char (30)	
	as
	select cli.cedula_cliente,cli.nombres,M.numero_medidorpk,M.consumo_a,descripcion,total,j.nombre_mes
	from clientesE cli inner join ConsumodeAgua M on  cli.cedula_cliente = M.cedula_clientepk 
	inner join mesE  j on j.id_mes = M.id_mespk where cedula_cliente like '%77' and consumo_a >='300m3';
	go
	exec consumo1 '131345677'

