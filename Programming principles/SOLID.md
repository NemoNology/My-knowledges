# Расшифровка аббревиатуры
## S
Single responsibility principle - Принцип единственной ответственности.
Модуль (класс, метод/функция, структура и т.д.) должен отвечать за что-то одно.

### Пример

```csharp
// Нарушение принципа: класс Animal должен отвечать только за структуру (поля, методы) абстрактного животного, но не за добавление его в базу данных;
public class Animal(string name)
{
	public string Name { get; set; } = name;
	public void AddToDb(Db bd) { ... }
}
// Чтобы не нарушать принцип единственной ответственности, стоит переменести метод `AddToDB` в другой класс
public class DbController(Db db)
{
	public Db DB { get; set; } = db;
	public void AddObjectToDb(object obj) { ... }
}
```
## O
Open-closed principle - Принцип открытости/закрытости.
> Открыт к расширению, закрыт к модификации.

Программная сущность должна быть открыта к расширению, но не к модификации (изменению кода сущности).

### Пример

```csharp
// Нарушение принципа: если мы захотим добавить новый HtmlElementType, то придётся модифицировать `HtmlElementType` и свойства `Tag` `Icon` в HtmlElementExtension;
public enum HtmlElementType { ... }
public class HtmlElement
{
	public HtmnElementType Type { get; init; }
	...
}
public implicit extension HtmlElementExtension for HtmlElement
{
	public string Tag => this.Type switch 
	{
		Division => "div",
		...,
		_ => ""
	}
	public Icon Icon => this.Type switch
	{
		Division => Icons.Division,...,
		_ => Icons.Custom
	}
}
// Чтобы не нарушать принцип открытости/закрытости можно видоизменить класс `HtmlElement`, используя свойства `Tag` и `Icon`, вместо `Type`
public class HtmlElement
{
	public string Tag { get; init; }
	...
}
``` 
## L
Liskov substitution principle - Принцип подстановки Лисков.
> Функции, которые используют базовый тип, должны иметь возможность использовать подтипы базового типа не зная об этом.

### Пример
```csharp
var test = new();
```
## I
Interface segregation principle - Принцип разделения интерфейса.
> много интерфейсов, специально предназначенных для клиентов, лучше, чем один интерфейс общего назначения.

## D
Dependency inversion principle - Принцип инверсии зависимостей.
> Зависимость на Абстракциях. Нет зависимости на что-то конкретное


# Ссылки
- [Ru Wikipedia - SOLID (программирование)](https://ru.wikipedia.org/wiki/SOLID_(%D0%BF%D1%80%D0%BE%D0%B3%D1%80%D0%B0%D0%BC%D0%BC%D0%B8%D1%80%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5))
- [Habr - Принципы SOLID, о которых должен знать каждый разработчик](https://habr.com/ru/companies/ruvds/articles/426413/)