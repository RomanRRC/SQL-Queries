![Header](https://github.com/RomanRRC/SQL-Queries/blob/main/sql-server-icon-png-11364.png)

# SQL-Queries
Этот репозиторий содержит SQL-запросы которые были мной выполнены в рамках прохожждения курса и подготовки домашнего задания
<br>С данными запросами Вы можете ознакомиться ниже</br>

## Задание № 1

### Выведите имя, фамилию, патронуса всех персонажей, у которых есть patronus или он известен
<br>Select fname, lname, patronus</br>
<br>FROM `111`.characters</br>
<br>Where not patronus='Unknown' AND patronus Is not NULL;</br>

### Выведите фамилию персонажей, у которых последняя буква в фамилии ‘e’
<br>Select Lname</br>
<br>FROM `111`.characters</br>
<br>WHERE Lname Like '%e';</br>

### Посчитайте общий возраст всех персонажей и выведите это на экран
<br>Select SUM(age)</br>
<br>FROM `111`.characters;</br>

### Выведите имя, фамилию и возраст персонажей по убыванию их возраста
<br>Select Fname, lname, age </br>
<br>FROM `111`.characters</br>
<br>Order BY age DESC;</br>

### Выведите имя персонажа и возраст, у которых последний находится в диапазоне от 50 до 100 лет
<br>Select Fname,age</br>
<br>FROM `111`.characters</br>
<br>Where AGe between 50 and 100;</br>

### Выведите возраст всех персонажей так, чтобы среди них не было тех, у кого он одинаковый
<br>Select distinct Age</br>
<br>FROM `111`.characters;</br>

### Выведите всю информацию о персонажах, у которых faculty = Gryffindor и чей возраст больше 30 лет
<br>select *</br>
<br>FROM `111`.characters</br>
<br>where age> 30 and faculty = 'Gryffindor';</br>

### Выведите имена первых трех факультетов из таблицы, так чтобы факультеты не повторялись
<br>Select distinct faculty</br>
<br>FROM `111`.characters</<br>
<br>limit 3;</br>

### Выведите имена всех персонажей, у которых имя начинается с ‘H’ и состоит из 5 букв, или чье имя начинается с ‘L’
select fname FROM `111`.characters where fname like 'H____' OR fname like 'L%' ;

### Посчитайте средний возраст всех персонажей 
<br>select AVG(age)</br>
<br>FROM `111`.characters;</br>

### Удалите персонажа с ID = 11
<br>delete FROM `111`.characters</br>
<br>where char_id=11;</br>

### Выведите фамилию всех персонажей, которые содержат в ней букву ‘a’
<br>select lname</br>
<br>FROM `111`.characters</br>
<br>where lname like "%a";</br>

### Используйте псевдоним для того, чтобы временно замените название столбца fname на Half-Blood Prince для реального принца-полукровки
<br>select fname as Half_Blood_Prince</br>
<br>FROM `111`.characters</br>
<br>where fname = 'Severus';</br>

### Выведите id и имена всех патронусов в алфавитном порядки, при условии что они есть или известны
<br>select char_id, patronus</br>
<br>FROM `111`.characters</br>
<br>Where not patronus= 'Unknown' and patronus is not null</br>
<br>Order BY patronus asc;</br>

### Используя оператор IN, выведите имя и фамилию тех персонажей, у которых фамилия Crabbe, Granger или Diggory
<br>select fname, lname</br>
<br>FROM `111`.characters</br>
<br>where lname in ("Crabbe", "Granger", "Diggory");</br>

### Выведите минимальный возраст персонажа
<br>Select Min(age)</br>
<br>FROM `111`.characters;</br>

### Используя оператор UNION выберите имена из таблицы characters и названия книг из таблицы library
<br>Select fname FROM `111`.characters</br>
<br>Union</br>
<br>select book_name FROM `111`.library;</br>

### Используя оператор HAVING посчитайте количество персонажей на каждом факультете, оставив только те факультеты, где количество студентов больше 1
<br>select count(Char_id), faculty</br>
<br>FROM `111`.characters</br>
<br>Group By faculty</br>
<br>Having count(char_id)>1;</br>

### Используя оператор CASE опишите следующую логику: Выведите имя и фамилию персонажа, а также следующий текстовое сообщение:
#### Если факультет Gryffindor, то в консоли должно вывестись Godric
#### Если факультет Slytherin, то в консоли должно вывестись Salazar
#### Если факультет Ravenclaw, то в консоли должно вывестись Rowena
#### Если факультет Hufflepuff, то в консоли должно вывестись Helga
#### Если другая информация, то выводится Muggle
#### Для сообщения используйте псевдоним Founders

<br>Select fname, lname,</br>
<br>Case</br>
<br>When faculty = 'Gryffindor' Then 'Godric'</br>
<br>When faculty = 'Slytherin' Then 'Salazar'</br>
<br>When faculty = 'Ravenclaw' Then 'Rowena'</br>
<br>When faculty = 'Hufflepuff' Then 'Helga'</br>
<br>Else 'Muggle'</br>
<br>End As Founders</br>
<br>FROM `111`.characters;</br>

### Используя регулярное выражение найдите фамилии персонажей, которые не начинаются с букв H, L или S и выведите их
<br>select lname</br>
<br>FROM `111`.characters</br>
<br>Where not lname regexp '^[HLS]';</br>
