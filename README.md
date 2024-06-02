# TestTaskMindbox
тестовое задание на позицию C# Cтажер-разработчик

# Задание 3
В базе данных MS SQL Server есть продукты и категории. Одному продукту может соответствовать много категорий, в одной категории может быть много продуктов. Напишите SQL запрос для выбора всех пар «Имя продукта – Имя категории». Если у продукта нет категорий, то его имя все равно должно выводиться.

CREATE TABLE Products(
id INT PRIMARY KEY , 
name VARCHAR(255));

CREATE TABLE Category(
id INT PRIMARY KEY ,
name VARCHAR(255));

CREATE TABLE ProdCat(
products_id INT ,
category_id INT ,
FOREIGN KEY(products_id) REFERENCES Products(id) ON DELETE CASCADE,
FOREIGN KEY(category_id) REFERENCES Category(id) ON DELETE CASCADE);

INSERT INTO Products VALUES(1,'Бумага'), (2,'Ножницы'), (3,'Ложка'), (4,'Яблоко');
INSERT INTO Category VALUES(1,'Канцелярия'), (2,'Столовые приборы');
INSERT INTO ProdCat VALUES(1, 1), (2, 1), (3, 2), (4,null);

SELECT p.name AS product, c.name AS category FROM Products AS p
LEFT JOIN ProdCat AS pc ON p.id = pc.products_id
LEFT JOIN Category AS c ON c.id = pc.category_id
ORDER BY product;

![image](https://github.com/reEcho0/TestTaskMindbox/assets/135825784/d448dad7-25ba-41b0-81ce-cbeb6db328c9)
