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
	public Icon Icon { get; init; }
	...
}
``` 
## L
Liskov substitution principle - Принцип подстановки Барбары Лисков.
> Функции, которые используют базовый тип, должны иметь возможность использовать подтипы базового типа не зная об этом
> *Википедия*

> Цель этого принципа заключаются в том, чтобы классы-наследники могли бы использоваться вместо родительских классов, от которых они образованы, не нарушая работу программы. Если оказывается, что в коде проверяется тип класса, значит принцип подстановки нарушается.
> *Хабр*
## I
Interface segregation principle - Принцип разделения интерфейса.
> много интерфейсов, специально предназначенных для клиентов, лучше, чем один интерфейс общего назначения.
### Пример
```csharp
// Нарушение принципа: в случае реализации интерфейса `MegaPrinter`, реализующим классам придётся реализовывать все методы интерфейса, ключая неиспользуемые классом методы.
public interface MegaPrinter
{
    obj Scan();
    void Fax(FaxEndPoint endPoint, obj data);
    void Print(obj data);
}

// Using only `Scan` method
public class Scaner: MegaPrinter 
{
	obj Scan() { ... }
    void Fax(FaxEndPoint endPoint, obj data) { ... }
    void Print(obj data) { ... }
}

// Using only `Print` method
public class Printer: MegaPrinter 
{
	obj Scan() { ... }
    void Fax(FaxEndPoint endPoint, obj data) { ... }
    void Print(obj data) { ... }
}

// Чтобы не нарушать принцип разделения интерфейса, необходимо не перегружать интерфейсы и соблюдать принцип единственной ответственности и абстракцию.
public interface Scaner
{
	obj Scan();
}

public interface Faxer
{
	void Fax(FaxEndPoint endPoint, obj data);
}

public interface Printer
{
    void Print(obj data);
}

public class TextScaner: Scaner 
{
	obj Scan() { ... }
}

// Using only `Print` method
public class TextFaxer: Faxer 
{
	void Fax(FaxEndPoint endPoint, obj data) { ... }
}
```
## D
Dependency inversion principle - Принцип инверсии зависимостей.
> Зависимость на Абстракциях. Нет зависимости на что-то конкретное


# Ссылки
- [Википедия - SOLID (программирование)](https://ru.wikipedia.org/wiki/SOLID_(%D0%BF%D1%80%D0%BE%D0%B3%D1%80%D0%B0%D0%BC%D0%BC%D0%B8%D1%80%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5))
- [Хабр - Принципы SOLID, о которых должен знать каждый разработчик](https://habr.com/ru/companies/ruvds/articles/426413/)