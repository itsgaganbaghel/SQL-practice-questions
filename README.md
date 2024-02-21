# SQL-practice-questions

                                                      --  Practice -   01 

create database lab ;

use lab ;
	
create table employee( 
emp_no numeric (5) not null ,
emp_name varchar(30) ,
designation char(10) ,
doj  date ,
salary numeric,
addr varchar(30) ,
dept_name char(30) );

select * from employee ;

insert into employee values ( 1001 , 'amit' , 'officer' , '1995-12-20', 1000 , 'mathura' , 'marketing') ;
insert into employee values ( 1002 , 'sumit','clerk' ,'1982-05-12', 500 ,'delhi' , 'accoutns' );
insert into employee values ( 1003,'raj','manager','1984-12-23',3500,'bombay','sales' );
insert into employee values (1004,'james' ,'analyst','1990-07-22' ,5000,'mathura','software');
insert into employee values (1005,'amit','analyst' ,'1990-07-22' ,4900,'delhi','producton');
insert into employee values (1006 ,'jones','clerk' ,'1986-04-16' ,950,'delhi','production');

select*from employee ;
 

/* 1. list the emp_name , doj from employee table */
SQL :-
select emp_name , doj from employee ;
OUTPUT : -
  

/* 2. list the names of employee who is getting 1000 RS/- */
SQL :-
select emp_name from employee where salary=1000 ;

OUTPUT : -
 

/* 3. list the name of employee who is belong to mathura and dept_name is marketing */
SQL :-
select emp_name from employee where addr='mathura' and dept_name = 'marketing' ;

OUTPUT : -
 

/* 4. list the average salary of amit */
SQL :-
select avg(salary) from employee where emp_name ='amit' ;

OUTPUT : -
 

/* 5. list the name of emp  who are getting their salary between 800 and 2500 */
SQL :-
select emp_name from employee where salary between 800 and 2500 ;

OUTPUT : -
 

/* 6. list the experience of all employees */
SQL :-
select datediff(sysdate() , doj )/365 as experience from employee ;

OUTPUT : -
 

/* 7. list the employee who is earning between more than 1200 but less than 4000  */
SQL :-
select * from employee where salary between 1200 and 4000 ;

OUTPUT : -
 


/* 8. list the employee who have joined after 1-jan-84 in order of joing date */
SQL :-
select * from employee where doj >'1984-01-1' order by doj ;
						-- OR ---
SQL :-
select * from employee where doj >'1984-01-1' order by doj asc ;

OUTPUT : -
 

/* 9. list the employee who live in mathura */
SQL :-
select * from employee where addr = 'mathura' ;

OUTPUT : -
 
/* 10. list the employee who are in sales dept */
SQL :-
select * from employee where dept_name = 'sales' ;

OUTPUT : -
 
/* 11. list the department that are located in delhi */
SQL :-
select dept_name from employee where addr = 'delhi' ;

OUTPUT : -
 

/* 12. list the employees who are not woring in delhi */
SQL :-
select * from employee where addr != 'delhi' ;

OUTPUT : -
 

/* 13. find out how many employee are there in organization. */
SQL :-
select count(emp_no) from employee ;
OUTPUT : -
 


/* 14. find out the total salary of amit */
SQL :-
select sum(salary) from employee where emp_name = 'amit' ;

OUTPUT : -
 

/* 15. find out how many employee are working in the sales department */
SQL :-
select count(emp_no) from employee where dept_name ='sales' ;

OUTPUT : -
 

                                                 -- Practice - -02 –

use lab ;

create table employee01 (
emp_no numeric not null ,
emp_name varchar (30) ,
designation char(10),
doj date ,
salary numeric(10),
dept_no numeric (10)
);

select* from employee01 ;

create table department (
dept_no numeric(10),
dept_name char(30),
dept_locn varchar (250)
);

create table allowance (
designation char(10) ,
sp_allow numeric,
conveyance numeric
);

/* INSERT DATA IN THE TABLE */
/* how to insert */
insert into employee01 values( 1001 ,'ROBERT', 'OFFICER', '1985-12-21', 1000 , 10 );
insert into employee01 values (1002 , 'ALLAN', 'CLERK', '1985-05-15' , 500 ,10 );
insert into employee01 values ( 1003, 'MARTIN' ,'MANAGER' , '1984-12-23' , 3500 ,20 );
insert into employee01 values ( 1004 ,'JAMES' , 'ANALYST' ,'1990-07-22' ,5000, 30 );
insert into employee01 values ( 1005, 'JOHN' , 'ANALYST' ,'1990-07-22' ,4900 ,30 );

select * from employee01 ;
 

insert into allowance values('MANAGER',1000,500);
insert into allowance values('OFFICER',800,400);
insert into allowance values('ANALYST',1200,500);
insert into allowance values('CLERK',500,300);

select * from allowance ;
 

insert into department values (10 , 'MARKETING', 'LONDON');
insert into department values (20 ,'ACCOUNTS', 'AMERICA');
insert into department values (30 ,'SALES' , 'NEWYORK');
insert into department values (40 ,'SOFTWARE' ,'BOSTON');
insert into department values (50 ,'PRODUCTION' ,'BOSTON');






select * from department;

 

                                           -- SQL QUERIIES --
               
/* 1. List the employee belonging to department 20 */
SQL :-
select * from employee01  
where (employee01.dept_no = 20) ;

OUTPUT : -
 

/* 2. list the employee who are earning more than 1200 but less than 4000 */
SQL :-
select * from employee01 where salary between 1200 and 4000 ;

OUTPUT : -
 

/* 3. list the employee who have joined after 1984-01-01 in order of joing date */
SQL :-
select * from employee01 where doj > '1984-01-01' order by salary asc ;

OUTPUT : -
 

/* 4. List the employee who are either in Office or Manager position. */
SQL :-
select * from employee01 where designation = 'OFFICER' or 'Manager position'; 

OUTPUT : -
 

/* 5. List the name of the emp who are getting their salary between 800 and 2500. */
SQL :-
select * from employee01 where salary between 800 and 2500 ;

OUTPUT : -
 

/* 6. List the employee who are in Sales Department. */
SQL :-
select * from employee01 , department where department.dept_no = employee01.dept_no 
and department.dept_name = 'SALES';

OUTPUT : -
 

/* 7. List the departments that do not have an employee. */
SQL :-
select distinct dept_name from department where 
department.dept_no not in ( select dept_no  from employee01 );

OUTPUT : -
 

/* 8. List the employee who are earning more than Robert. */
SQL :-
select * from employee01 where 
employee01.salary > (select salary from employee01 where emp_name ='ROBERT');



OUTPUT : -
 

/* 9. Find out how many employees are there in organization */
SQL :-
select count(emp_no) from employee01 ;

OUTPUT : -
 

/* 10. Find out the total salary paid to the employee. */
SQL :-
select sum(salary) from employee01 ;

OUTPUT : -
 

/* 11. Find out how many employee are working in Sales department */
SQL :-
select count(emp_no) from employee01 , department where department.dept_no = employee01.dept_no 
and department.dept_name = 'SALES';

OUTPUT : -
 

/* 12. What is the average salary paid to the employees? */
SQL :-
select avg(salary) from employee01 ;

OUTPUT : -
 

/*13. What is the minimum salary paid in DEPT 30? */
SQL :-
select min(salary) from employee01 ;

OUTPUT : -
 

/* 14. Display names and grades of employee based on their designation
DESIGNATION GRADE
Manager A
Officer B
Analyst C
Clerk   D */

/*ALTER TABLE table
ADD [COLUMN] column_name column_definition [FIRST|AFTER existing_column];*/
-- EXAMPLE --
/* ALTER TABLE vendors
ADD COLUMN phone VARCHAR(15) AFTER name;
*/
-- SOLUTION / SQL –
SQL :-
alter table employee01
add column grade char(5) ;

select * from employee01 ;

update employee01 set grade ='A' where designation ='Manager' ;
update employee01 set grade ='B' where designation ='officer' ;
update employee01 set grade ='C' where designation ='analyst' ;
update employee01 set grade ='D' where designation ='clerk' ;

select emp_name , grade from employee01 ;

OUTPUT : -
 




                                              -- Practice -  03 --

use lab ;

/* 1. Find out how long an employee has worked in the organization in terms of
number of Days, Months &Year. */
SQL :-
select datediff(sysdate() , doj )/365 as experience from programmer order by experience desc ;

OUTPUT : -
 

/* 2.  Display the total salaries department wise. */ 
SQL :-
select dept_name ,  sum(salary)as total_salary from employee01 as e
right join department as d 
on e.dept_no = d.dept_no
group by dept_name ;

OUTPUT : -
 

/* 3. Display the maximum salaries in each department along with the name ofdepartment. 
The column heading should be like this: Dept_Name Max(Sum)  */
SQL :-
select dept_name , max(salary) as max_sum from employee01 as e
right join department as d 
on e.dept_no = d.dept_no 
group by dept_name ;

OUTPUT : -
 

/* 4. Display the total salary( Salary+Sp_allowance_Conveyance) of each employee in the order of total salary. */
SQL :-
select e.designation , sum(salary + sp_allow + conveyance) as total_salary from allowance as a left join employee01 as e 
on a.designation = e.designation 
group by  e.designation ;

OUTPUT : -
 

/* 5. List the no. of Employees along with their department numbers in each department. */
SQL :-
select d.dept_name , emp_no , d.dept_no   from employee01 as e
right join  department as d 
on e.dept_no = d.dept_no 
group by d.dept_name  ;

OUTPUT : -
 

/* 6. List the department wise total salary. */ 
SQL :-
select d.dept_name , sum(e.salary) from employee01 as e 
right join department as d 
on e.dept_no = d.dept_no 
group by d.dept_name ;

OUTPUT : -
 

/* 7. List the number of employees in each designation in the descending order. */ 
SQL :-
select  designation , count(*) as no_of_employee from employee01 as e
group by designation 
order by no_of_employee desc ;

OUTPUT : -
 

/*8. List the total salary, maximum and minimum along with the average salary of each employee designation wise. */
SQL :-
select  designation , sum(salary) as total_salary , min(salary) as min_salary , max(salary) as max_salary , avg(salary) as av_salary
from employee01 group by designation ;

OUTPUT : -
 

/* 9. List the total salary, maximum and minimum along with the average salary of each employee designation wise for department no.30. */
SQL :-
select  designation , sum(salary) as total_salary , min(salary) as min_salary , max(salary) as max_salary , avg(salary) as av_salary
from employee01  where dept_no = 30 
group by designation ;

OUTPUT : -
 

/* 10. List the total salary, maximum and minimum along with the average salary ofeach employee designation wise for 
department no.30 and display only these rows that have their average salary greater than 1000. */
SQL :-
select  designation , sum(salary) as total_salary , min(salary) as min_salary , max(salary) as max_salary , avg(salary) as av_salary
from employee01  where dept_no = 30 
group by designation 
having avg(salary) > 1000 ;

OUTPUT : -
 

/* 11. List the total salary of the employees for each designation department wise. */
SQL :-
select dept_name , sum(salary) as total_salary_of_employee 
from employee01 as e , department as d , allowance as a
where   e.designation = a.designation
group by dept_name;

OUTPUT : -
 

/* 12. List the employee details such as his Employee no., Name, Date of Joining, Basic 
Salary and Designation of department=’Marketing’. */
SQL :-
 select * from employee01 as e , department as d
 where dept_name = 'marketing'
 and  e.dept_no = d.dept_no ;

OUTPUT : -
  

/* 13. List the employee details such as his Employee no., Name, Date of Joining, Basic
Salary and Designation for the employee working in location = ‘AMERICA’. */
SQL :-
select *  from employee01 
where  dept_no in ( select dept_no from department where dept_locn = 'AMERICA') ;

OUTPUT : -
 

/* 14. List the departments where there are no employee functioning */
SQL :-
select * from department 
where dept_no not in  ( select dept_no  from employee01 ) ;

OUTPUT : -__
 
                            
        -- Practice - 04  --

/* 
Create the tables described below :

a. Table Name : Programmer(Used to store information about programmers)
Name         Type             Remark

NAME         Varchar2(8)      Name
DOB          Date             Date of Birth
DOJ          Date             Date of Joining
SEX          Varchar2(1)      Male/Female
PROF1        Varchar2(8)      Known Language 1
PROF2        Varchar2(8)      Known Language2
SALARY       Number(8)        Salary

b. Table Name: Software(Used to store information about Softwares)
Name         Type             Remark

NAME         Varchar2(8)      Name
TITLE        Varchar2(20)     Developed Project Name
DEV_IN       Varchar2(8)      Language Developed
SCOST        Number(7,2)      Software Cost
DCOST        Number(5)        Development Cost
SOLD         Number(3)        Number of Software Sold

c. Table Name: Studies(Used to store information about programmer Studies)
Name         Type             Remark

NAME         Varchar2(8)      Name
SPLACE       Varchar2(9)      Studied Place
COURSE       Varchar2(5)      Course Studied
CCOST        Number(5)        Course Cost 
*/ 

create table programmer ( 
 pname varchar(100) ,
 dob date ,
 doj date ,
 sex varchar(10) ,
 prof1 varchar(80),
 prof2 varchar(80),
 salary numeric (8) 
);
select * from programmer ;

create table software (
sname varchar(80) ,
title varchar(200),
dev_in varchar (80)  ,
scost numeric(7,2) ,
dcost numeric (5) ,
sold numeric (3) 
);

select * from software ;

create table studies (
pname varchar (80) ,
splace varchar(90) ,
course varchar(50) ,
ccost numeric (5) 
);
select * from studies ;
 

insert into programmer 
( pname , dob  , doj  , sex , prof1 , prof2 , salary )
values
('ram_kumar', '1966-04-21' ,'2000-04-21', 'M' , 'pascal' , 'basic' , 3200),
('altaf' , '1980-07-02' , '2001-11-13' , 'M' , 'clipper' ,'cobol',2800),
('jagdesh' , '1987-10-05', '1999-10-04', 'M' , 'oracle', 'java' ,4100),
('juliana' ,'1986-01-31','1998-04-21','F','cobol'   ,'dbase'   ,3000),
('kamala'  ,'1992-10-30','1999-06-02','F','c'       ,'dbase'   ,2900),
('mary'    ,'1989-10-30','2004-02-01','F','c'       ,'oracle'  ,4500),
('nelson'  ,'1990-09-11','2003-10-11','M','cobol'   ,'dbase'   ,2500),
('patrici' ,'1991-11-16','2002-04-21','M','pascal'  ,'clipper' ,2800),
( 'qadir'  ,'1987-08-31','2006-04-21','M','assembly','c'       ,3000),
('ramesh'  ,'1983-05-03','2005-02-28','M','pascal'  ,'dbase'   ,3200),
('rebecca' ,'1987-01-01','1990-12-01','F','basic'   ,'cobol'   ,2500),
('remitha' ,'1988-04-19','1993-04-20','F','c'       ,'assembly',3600),
('revathi' ,'1991-12-02','1992-01-02','F','pascal'  ,'basic'   ,3700),
('vijaya'  ,'1992-12-11','1992-05-02','F','foxpro'  , 'c'      ,3500) ;

select *from programmer ;
 

insert into software 
( sname , title , dev_in , scost , dcost , sold ) 
values 
( 'ANAND', 'PARACHUTES' , 'BASIC', 399.95 ,6000, 43),
('ANAND', 'VIDEO TITLING PACK', 'PASCAL', 7500.00 ,16000, 9),
('JAGADESH', 'SERIAL LINK UTILITY', 'JAVA', 800.00, 7500, 10 ),
('JAGADESH' ,'SARES MANAGEMENT' ,'ORACLE', 3000.00, 12000, 14),
('JULIANA' ,'INVENTORY CONTROL', 'COBOL' ,3000.00, 3500, 0 ),
('KAMAL' ,'PAYROLL PACKAGE', 'DBASE', 9000.00, 20000, 7),
('MARY','FINANCIAL ACC S/W','ORACLE', 18000.00, 85000, 4),
('MARY', 'CODE GENERATOR',' C', 4500.00, 20000, 23),
('MARY','READ ME' ,'C', 300.00, 1200, 84),
('PATRICK','GRAPHIC EDITOR', 'PASCAL', 750.00 ,5000, 11),
('QADIR','BOMBS AWAY', 'ASSEMBLY', 499.80, 530, 114),
('QADIR', 'VACCINES', 'C', 1900.00, 3400, 21),
('RAMESH','HOTEL MANAGEMENT' ,'DBASE', 12000.00, 35000, 4),
('RAMESH', 'DEAD LEE', 'PASCAL', 99.95, 4500, 73),
('REMITHA', 'PC UTILITES', 'C' ,725.00, 500, 51),
('REMITHA', 'TSR HELP PACKAGE', 'ASSEMBLY ',2500.00, 6000, 6),
('REVATHI', 'HOTEL MANAGEMENT', 'PASCAL' ,1100.00, 75000 ,2),
('REVATHI', 'QUIZ MASSTER', 'BASIC', 3200.00, 2100, 15),
('VIJAYA', 'ISK EDITOR', 'C', 900.00 ,700, 6)
;
select * from software ;
 

insert into studies 
(pname , splace , course , ccost )
values 
('ANAND', 'SABHARI', 'PGDCA', 4500),
('ALTAF', 'CCIT', 'DCA', 7200),
('JAGADESH', 'SSIL', 'DCA', 3500),
('JULIANA', 'BITS', 'DCA', 22000),
('KAMALA','PRAGATHI', 'DCP', 5000),
('MARY', 'SABHARI', 'PGDCA', 4500),
('NELSON' ,'PRAGATHI', 'DAP',5200),
('PATRICK', 'PRAGATHI', 'DCAP', 5200),
('QADIR', 'APPLE', 'HDCP', 14000),
('RAMESH', 'SABHARI', 'PGDCA', 4500),
('REBECCA', 'BRILLIANT', 'DCA', 11000),
('REMITHA', 'BDPS', 'DCA', 6000),
('REVATHI', 'SABHARI','DAP', 5000),
('VIJAYA', 'BDPS', 'DCA', 48000);
select * from studies ;
 

/* SQL QUERIES/ PROBLEMS */
/* 1. How many programmers have done the PGDCA course. */
SQL :-
select count(pname) from studies where course = 'PGDCA' ;

OUTPUT : -
 
/* 2. How much revenue has been earned through sales of packages in C */
SQL :-
select (scost*sold) as tcost  from software where dev_in ='c' ;

OUTPUT : -
 
/* 3. Display the details of SOFTWARE developed by Ramesh. */
SQL :-
select * from software where sname = 'Ramesh';

OUTPUT : -
 

/* 4. Display the details of Package who’s sales CROSSED the 20000 */
SQL :-
select * from  software where (scost*sold) > 20000 ;

OUTPUT : -
 

/* 5. Display the details of programmers knowing C */
SQL :-
select * from programmer where prof1 = 'c' or prof2 ='c' ;

OUTPUT : -
 

/* 6. How many programmers don’t know PASCAL & C. */
SQL :-
select count(pname)  as programmers from programmer 
where prof1 not in ('pascal', 'c')  and prof2 not in ( 'c', 'pascal') ;

OUTPUT : -
 

/* 7. What are the languages known by the male programmers. */
SQL :-
select prof1 , prof2 from programmer where sex like 'M' ;






OUTPUT : -
 

/* 8. Display the institute names from the STUDIES table without duplicates */
SQL :-
select distinct splace from studies ;

OUTPUT : -
 

/* 9.  Display the name of the programmers who’s name starts with ‘A’ and the third character is T. */
SQL :-
select pname from programmer where pname like 'A_t%' ;

OUTPUT : -
 

/* 10 Find out the selling cost average for package developed in Oracle */
SQL :-
select avg(scost) from software where dev_in = 'oracle' ;

OUTPUT : -
 

/* 11. Display the names, ages and experience of all programmers. */

SQL :-
select pname ,
datediff(current_date , dob )/365 AS age , 
datediff(current_date , doj )/365 AS  experience
from programmer  ;
                                              -- OR --       
SQL :-                              
select pname , 
DATEDIFF( SYSDATE() , dob)/365 as age , 
datediff( sysdate() , doj)/365 as experience 
FROM programmer;

OUTPUT : -
 
/* 12. Display the name of those who have done PGDCA course.*/
SQL :-
select pname from studies where  course = 'PGDCA' ;

OUTPUT : -
 

/* 13 What is the highest number of copies sold by a package? */
SQL :-
SELECT max(sold) from software ;


OUTPUT : -
 

/* 14. Display the names & date of birth of all programmers born in April. */
SQL :-
select pname , dob from programmer where dob like '%-04-%' ;

OUTPUT : -
 

/* 15 . Display the lowest course fee. */
SQL :-
select distinct course from studies where ccost in ( select min(ccost) from studies ) ;

OUTPUT : -
 
/* 16. How many programmers have done the DCA course. */ 
SQL :-
select count( DISTINCT Pname) from studies where course LIKE 'DCA';

OUTPUT : -
 

/* 17. How much revenue has been earned through the sale of packages developed in C. */
SQL :-
SELECT sum(scost*sold) as revenue from software where dev_in like 'c' ;

OUTPUT : -
 

/* 18. How many programmers studied at Pentafour. */
SQL :-
select count(distinct pname) from studies where splace like 'pentaflour' ;
 

/* 19. Find out the number of copies which should be sold in order to recover the
development cost of each package. */
SQL :-
select count(distinct sname ) from software where (sold * scost) > dcost ;

OUTPUT : -
 

/* 20. Display the details of packages for which the development cost has been
recovered. */
SQL :-
select * from software where (sold * scost) > dcost ;  

OUTPUT : -
  

/* 21. What is the price of costliest software developed in basic? */
SQL :-
select max(scost) from software where dev_in like 'basic' ;

OUTPUT : -
 

/* 22. How many packages were developed in Oracle? */
SQL :-
select count(distinct sname) from  software where dev_in like 'oracle' ;

OUTPUT : -
 

/* 23. How many programmers studied at PRAGATHI? */
SQL :-
select count(distinct pname) from studies where splace like 'pragathi' ;

OUTPUT : -
 

/* 24. How many programmers paid 10000 to 15000 for the course? */
SQL :-
select count(distinct ccost) from studies where ccost between 10000 and 15000 ;

OUTPUT : -
 

/* 25. What is the average course fee? */
SQL :-
select avg(ccost) from studies ;

OUTPUT : -
 

/* 26. How many programmers know either C or Pascal? */
SQL :-
select count(distinct pname) from programmer where prof1 in ('c' , 'pascal') or prof2 in ( 'c' , 'pascal') ;

OUTPUT : -
 

/* 27. How old is the oldest male programmer? */
SQL :-
select max( datediff(sysdate() ,dob)/365) as oldest_prpgrammer_age from programmer ;

OUTPUT : -
 


/* 28. What is the average age of female programmers? */
SQL :-
select avg(datediff(sysdate(),dob)/365) from programmer where sex like 'f' ;

OUTPUT : -
 

/* 29 . Calculate the experience in years for each programmer & display along with their names in descending order. */
SQL :-
select pname, datediff(sysdate(),doj)/365 as experience from programmer order by experience desc ; 

OUTPUT : -
 

/* 30 How many female programmers are there? */
SQL :-
select count(distinct pname ) from programmer where sex like 'f' ;

OUTPUT : -
 

/* 31. What is the average salary? */
SQL :-
select avg(distinct salary) from programmer ;

OUTPUT : -
 

/* 32. Display the details of those who don’t know C, C++ or Pascal. */
SQL :-
select * from programmer where prof1 not in ('c' , 'c++' ,'pascal') and prof2 not in ('c' , 'c++' ,'pascal') ;

OUTPUT : -
 

/* 33. How many people draw 2000 to 4000. */
SQL :-
select count(*) from programmer where salary between 2000 and 4000 ;

OUTPUT : -
 

/* 34. What is the price of costliest software developed in VB? */
SQL :-
select scost from software where dev_in = 'VB' ;


OUTPUT : -
 
  Null 

/* 35. Display the costliest package developed by each programmer. */
SQL :-
select sname , max(dcost) as costlier from  software  group by sname;

OUTPUT : -
 

/* 36. Who are the programmers who celebrate their birthdays during the current month? */
SQL :- 
select * from programmer where month(dob) = (select month(sysdate()) from dual);

OUTPUT : -
 
