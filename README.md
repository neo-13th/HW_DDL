# «Работа с данными (DDL/DML)»
## Задание 1  
1.1. Поднимите чистый инстанс MySQL версии 8.0+. Можно использовать локальный сервер или контейнер Docker.  

sudo apt update  
sudo apt install mysql-server  

![msql](https://github.com/user-attachments/assets/c8bac979-9b9b-4466-926e-073178d5f8fd)  
 

1.2. Создайте учётную запись  

mysql -u root -p  
CREATE USER 'sys_temp'@'localhost' IDENTIFIED BY 'password' 

1.3. Выполните запрос на получение списка пользователей в базе данных. (скриншот)  

mysql> SELECT User,Host FROM mysql.user;
![DDL1](https://github.com/user-attachments/assets/40d845ff-633d-4996-9f32-60627a17d96b)  

1.4. Дайте все права для пользователя sys_temp.  

GRANT ALL PRIVILEGES ON *.* TO 'sys_temp'@'localhost';  

1.5. Выполните запрос на получение списка прав для пользователя sys_temp. (скриншот)  

![DDL2](https://github.com/user-attachments/assets/91ec4028-b784-497d-94d2-74c00421f0ac)


1.6. Переподключитесь к базе данных от имени sys_temp.  

Для смены типа аутентификации с sha2 используйте запрос:  

ALTER USER 'sys_temp'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';  
SET PASSWORD FOR 'sys_temp'@'localhost' = '123';  

![DDL3](https://github.com/user-attachments/assets/a99eae72-6ff4-499a-9825-9549ab67810e)


1.6. По ссылке https://downloads.mysql.com/docs/sakila-db.zip скачайте дамп базы данных. 

wget https://downloads.mysql.com/docs/sakila-db.zip  

1.7. Восстановите дамп в базу данных.  

mysql -u root  
create database sakila;  

mysql < sakila-schema.sql  
mysql < sakila-data.sql  
mysqldump -u root -p sakila > sakila-data.sql  

![DDL4](https://github.com/user-attachments/assets/79f84b68-ca72-45a6-a981-00e177dc94e0)  


1.8. При работе в IDE сформируйте ER-диаграмму получившейся базы данных. При работе в командной строке используйте команду для получения всех таблиц базы данных. (скриншот)  
![DDL5](https://github.com/user-attachments/assets/5d31b026-4c80-4a8a-a703-0c144987851b)  

## Задание 2  
Составьте таблицу, используя любой текстовый редактор или Excel, в которой должно быть два столбца: в первом должны быть названия таблиц восстановленной базы, во втором названия первичных ключей этих таблиц. Пример: (скриншот/текст)  

Название таблицы           | Название первичного ключа
---------------------------|---------------------------
actor                      | actor_id
actor_info                 | -
address                    | address_id
category                   | category_id
city                       | city_id
country                    | country_id
customer                   | customer_id
customer_list              | -
film                       | film_id
film_actor                 | actor_id, film_id
film_category              | category_id, film_id
film_list                  | -
film_text                  | film_id
inventory                  | inventory_id
language                   | language_id
nicer_but_slower_film_list | -
payment                    | payment_id
rental                     | rental_id
sales_by_film_category     | -
sales_by_store             | -
staff                      | staff_id 
staff_list                 | -
store                      | store_id 

![DDL6](https://github.com/user-attachments/assets/ca264033-bfc4-416a-be37-89ead0aea2a9)  


  
