#SQL
# Определение
Structured Query Language - Язык структурированных запросов
# Основные типы данных
## Строка
### char(n)
n - количество символов в строке. `char` заполняет все пустые символы пробелами.
```sql
char([n])
char(5) от 'Ухо'      -> 'Ухо  '
char(5) от 'Ушки'     -> 'Ушки '
char(5) от 'Охота'    -> 'Охота'
char(5) от 'Охотился' ->  Ошибка
```
### varchar(n)
Не заполняет пробелами пустые символы.
```sql
varchar([n]) var_name
varchar(5) от 'Ухо'      -> 'Ухо'
varchar(5) от 'Ушки'     -> 'Ушки'
varchar(5) от 'Охота'    -> 'Охота'
varchar(5) от 'Охотился' ->  Ошибка
```
## Число
### Integer
### Float
### Double
### Decimal
```sql
int
float
double
decimal
```
## Дата
### Date
```sql
Date
('01.01.2024', 'dd.mm.yyyy')
```
# Запросы
## Create
Позволяет создавать объекты
```sql
CREATE [тип_объекта: TABLE, DATABASE, INDEX, VIEW, PROCEDURE, TRIGGER и т.д.] [имя_объекта] [парамеры];
```
### Table
```sql
CREATE TABLE имя_таблицы (
	[столбцы таблицы: имя_столбца тип_данных]
);

# Пример
create table Humans (
	Age int,
	Name varchar(255)
);
```
## Drop
Позволяет удалять объекты;
```sql
DROP [тип_объекта: TABLE, DATABASE, INDEX, PROCEDURE и т.д.] [имя_объекта];
```
## Insert
Позволяет добавлять данные в таблицы.
```sql
INSERT INTO [имя_таблицы] [(имена_столбцов - опционально)]
VALUES (
	([значения])
)

# Пример 1
INSERT INTO Humans
VALUES (
	(),
);
```
## Select
```sql
SELECT [набор полей для выборки. Например student_id, register_date и т.п]
FROM [имя_таблицы];

# Пример
SELECT * --| '*' - спец. символ, подразумеващющий все варианты. В данном случае - показать все данные из таблицы.
FROM Humans;
```
### Where
Ключевое слово, используемое для фильтрации выборки (SELECT).
Принимает логические выражения
```sql
SELECT ...
FROM ...
WHERE [логическое_выражение];
-- Логическое выражение может быть как простым..
WHERE Age = 21;
-- .. так и сложным
(MOD(Age, 2) = 0 OR Age in (15, 19, 21)) AND Name NOT LIKE '%III'

# Пример
SELECT *
FROM Humans
WHERE Age = 30; # Также: Age > 20; Age <= 10; Name = 'Саша' и т.п.
```
# Ссылки
- [YouTube - Максим Кухарь - Базовый курс по SQL для аналитиков и менеджеров](https://youtube.com/playlist?list=PLKl9v2TQvIkq4i_hZwZ1PmobxJSkIGwBf&si=isj-N83hn2N_WH4a)
- [Хабр - # Памятка/шпаргалка по SQL](https://habr.com/ru/articles/564390/)