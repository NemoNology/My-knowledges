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
char(5) от 'Ушки'     -> 'Ушки  '
char(5) от 'Охота'    -> 'Охота'
char(5) от 'Охотился' -> Ошибка
```
### varchar(n)
Не заполняет пробелами пустые символы.
```sql
varchar([n]) var_name
varchar(5) от 'Ухо'      -> 'Ухо'
varchar(5) от 'Ушки'     -> 'Ушки'
varchar(5) от 'Охота'    -> 'Охота'
varchar(5) от 'Охотился' -> Ошибка
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
('01.01.2024', '')
```
# Ссылки
- [YouTube - Максим Кухарь - Базовый курс по SQL для аналитиков и менеджеров](https://youtube.com/playlist?list=PLKl9v2TQvIkq4i_hZwZ1PmobxJSkIGwBf&si=isj-N83hn2N_WH4a)