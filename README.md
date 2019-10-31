In this repository will be described main questions from interviews for C# and Angular.

# The interview questions C#.

Вопросы:
1. ### ООП
Парадигма программирования, в которой основными концепциями являются понятия объектов и классов. 
Объект - экземляр класса, Класс - шаблон для объекта. 

Полиморфизм - это свойство системы использовать объекты с одинаковым интерфейсом без информации о типе и внутренней структуре объекта. К примеру у нас есть класс Shape. И есть классы наследуемые от него - Circle and Rectangle. Оба реализуют метод GetSquare (описанный в Shape) по-разному. В классе наследуемом - virtual. В классе наследнике - override. 

Наследование - это возможностьописать новый класс на основе уже существующего, с частичной или полностью позаимствованой функциональностью. Класс, от которого производится наследование - базовый, родительский. Новый класс - производный класс, потомок или наследник. Множественное наследование производится только с помощью интерфейсов. 

Инкапсуляция - это механизм программирования, объединяющий вместе код и данные, которыми он манипулирует, исключая как вмешательство извне, так и неправильное манипулирование данными.  

___
2. ### Что такое CLR? Что такое IL? Что такое CLS?
**CLR** - common language runtime. Существуют компиляторы, которые были специально созданы для данной платформы. CLR - все равно на каком языке был написан исходный код. Результатом компилятора является **managed module (управляемый модуль)**, который и требует CLR. 

**IL** - intermediate language. Код создаваемый компилятором при компиляции исходного кода. Далее CLR компилирует его в машинные команды. 

**CLS** - common language specification. Набор правил, следуя которым, разработчик может избежать кофликтов в работе со всеми языками .net.

___
3. ### Что такое managed code? Unmanaged code?

manged code - управляемый код. Служит для выполнения в среде CLR. В связи с этим на него накладываются некоторые ограничения. Основные приемущества - управление памятью, возможность программировать на различных языках, повышение безопасности, поддержка уравления версиями, четкая организация управления программных компонентов. 

unmanaged code - неуправляемый код. Не используется для выполенния в CLR. Может взаимодействовать с управляемым кодом, а значит на него не накладываются ограничения. 

___
4. ### Что такое assembly?
Наиментьшая единица многократного использовния, безопасности и управления версиями. 
Обеспечивает логическую группировку одного или нескольких управляемых модулей или файлов ресурсов. 
Способ объединения нескольких файлов в единую сущность. 

ПРОДОЛЖИТЬ....

___
5. ### Что такое assembly manifest?
Манифест сборки -    это внутренняя часть сборки, которая позволяет ей быть самоописанной.

Каждая сборка, статическая или динамическая, содержит набор данных, который описывает, как элементы в сборке связаны друг с другом. Манифест сборки содержит эти метаданные сборки. Манифест сборки содержит все метаданные, необходимые для указания требований к версии сборки и идентификатора безопасности, а также все метаданные, необходимые для определения области сборки и разрешения ссылок на ресурсы и классы. Манифест сборки может храниться либо в PE-файле (.exe или .dll) с кодом промежуточного языка Microsoft (MSIL), либо в отдельном PE-файле, который содержит только информацию о манифесте сборки.

![Assembly types diagram](/img/assembly-types-diagram.gif)

Для сборки с одним связанным файлом манифест включается в PE-файл для формирования сборки из одного файла. Вы можете создать многофайловую сборку с помощью отдельного файла манифеста или с помощью манифеста, включенного в один из файлов PE в сборке.

Каждый манифест сборки выполняет следующие функции:  
 - перечисляет файлы, из которых состоит сборка;
 - сопоставление ссылок на типы и ресурсы сборки с файлами, содержащими объявления и реализации этих типов и ресурсов;
 - перечисление других сборок, от которых зависит эта сборка;
 - обеспечение косвенного обращения пользователей сборки к подробностям ее реализации;
 - предоставление собственного описания сборки

 ### Что включает в себя манифест сборки

 Таблица внизу показывает всю информацию, которая включена в файл манифеста сборки. Первые четыре элемента: assembly name, version number, culture, and strong name information формируют идентификатор сборки. 

![Assembly manifest table](/img/assembly-manifest.png)

С помощью задания атрибутов сборки в коде можно добавить или изменить некоторые данные в манифесте сборки. Можно изменить данные о версии и информационные атрибуты, включая сведения о товарном знаке, авторском праве, продукте, компании и информационной версии. 

___
6. ### Что такое приватные и совместные сборки?

Сборки бывают 2х типов: приватные (те, которые используют само приложение) и совместные (использующие набор приложений).

При приватных сборках приложение изолируется от внешнего воздействия операционной системы и програм. Так же уже не необходимо париться на счёт уникальности имён в глобальном пространстве.

Что б сделать сборку совместной - нужно её собрать и присвоить ей строгое шифрованное имя.

___
7. ### В чем различие между Value Type и Reference Type?
**Value Type(byte, sbyte, short, ushort, int, uint, long, ulong, float, double, decimal, bool, char, enum, struct)**:  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*Сохраняет некоторые значения, а не адреса памяти.*  
**Место хранения:**  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Типы значений сохраняются там, где они объявлены. Например: значение int внутри функции как локальной переменной будет храниться в стеке, тогда как значение int объявленное как член в классе, будет храниться в куче с классом, в котором он объявлен. Тип значения в классе имеет тип lifetype, который точно такой же, как класс, в котором он объявлен, требуя почти никакой работы сборщиком мусора.  
  
**Преимущества:**  
  - Тип значения не требует дополнительной сборки мусора. Он получает мусор, собранный вместе с экземпляром, в котором он живет. Локальные переменные в методах очищаются при отпускании метода.  
  
**Недостатки:**  
  - Когда большой набор значений передается методу, принимающая переменная фактически копируется, поэтому в памяти есть два избыточных значения.  

**Reference Type(object, string, class, interface, delegate**:  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*Удерживает адрес памяти значения не value.*  
**Место хранения:**  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Сохранено в куче.  

**Преимущества:**  
 - Когда вы передаете ссылочную переменную методу и он меняет, он действительно изменяет исходное значение, тогда как в типах значений берется копия данной переменной и это значение изменяется.
 - Когда размер переменной больше ссылочного типа, это хорошо.
 - Поскольку классы относятся к переменным ссылочного типа, они дают возможность повторного использования, что приносит пользу объектно-ориентированному программированию.  
 
**Недостатки:**  
 - Больше ссылок на работу при распределении и разыменованиях при чтении значения. Дополнительная перегрузка для сборщика мусора

___
8. ### Про сборщик мусора. Когда объект удаляется сборщиком мусора?  
+  

___
9. ### Что такое Code Access Security (CAS)?  

___
10. ### Что такое attribute?  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Атрибуты в .NET представляют специальные инструменты, которые позволяют встраивать в сборку дополнительные метаданные. Атрибуты могут применяться как ко всему типу (классу, интерфейсу и т.д.), так и к отдельным его частям (методу, свойству и т.д.). Основу атрибутов составляет класс System.Attribute, от которого образованы все остальные классы атрибутов.  

Пример класса атдибута:  

```  c#
 public class AgeValidationAttribute : System.Attribute
{
    public int Age { get; set; }
     
    public AgeValidationAttribute()
    { }
     
    public AgeValidationAttribute(int age)
    {
        Age = age;
    }
}
```
С помощью атрибута AttributeUsage можно ограничить типы, к которым будет применяться атрибут.  
```c#
[AttributeUsage(AttributeTargets.Class)]
public class RoleInfoAttribute : System.Attribute
{
//....................................
}
```  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Ряд ограничений: All, Assembly, Constructor, Delegate, Enum, Event, Field, Interface, Method, Property, Struct. Их можно комбиноровать с помощью опретора или(|). 
```c# 
[AttributeUsage(AttributeTargets.Class | AttributeTargets.Struct)]
```

___
11. ### Как обеспечить использование именованных параметров в конструкторе атрибута?  
При описании конструктора/ов атрибута нужно указать его параметры. 

___
12. ### В чем различие между Finalize и Dispose?  
+  

___
13. ### Что такое Boxing и Unboxing?  
+

___
14. ### Что такое GAC?  
+  

___
15. ### Какие типы можно использовать в предложении foreach?  
+  

___
16. ### В чем различие между классом и структурой?  
+  

___
17. ### Что означает модификатор virtual?  
+  

___
18. ### Чем отличается event от delegate?  
+  

___
19. ### Может ли класс реализовать два интерфейса, у которых объявлены одинаковые методы? Каким образом?  
+  

___
20. ### Поддерживает ли C# множественное наследование?  
no  

___
21. ### Кому доступны переменные с модификатором protected на уровне класса?  

___
22. ### Наследуются ли переменные с модификатором private?  

___
23. ### Опишите модификатор “protected internal”  

___
24. ### Назовите класс .NET, от которого наследуются все классы?  
system.object  

___
25. ### Что обозначает термин immutable (неизменяемый)?  

___
26. ### Какая разница между классами System.String и System.Text.StringBuilder?  
+  

___
27. ### Какое преимущество использования класса System.Text.StringBuilder перед System.String?  

___
28. ### Можно ли хранить разные типы данных в объекте класса System.Array?  

___
29. ### Объясните разницу между System.Array.CopyTo() и System.Array.Clone()?  
+  

___
30. ### Как отсортировать элементы массива в убывающем порядке?  
+  

___
31. ### As, is – что это, как применяется?  
+  

___
32. ### Какой синтаксис используется для указания класса родителя в C#?  

___
33. ### Можно ли запретить наследование от своего собственного класса?  

___
34. ### Можно ли разрешить наследование класса, но запретить перекрытие метода?  

___
35. ### Что такое абстрактный класс?  
+  

___
36. ### В каком случае вы обязаны объявить класс абстрактным?   

___
37. ### Что такое интерфейс класса?  
апи доступа(его паблик методы)  

___
38. ### Почему нельзя указать модификатор видимости для методов интерфейса?  
потому что он публичный лол  

___
39. ### Можно ли наследовать от нескольких интерфейсов?  
Да   

___
40. ### Назовите отличия между интерфейсом и абстрактным классом?  
+  

___
41. ### Назовите различия между структурами и классами.  
+  

___
42. ### В чем разница между абстрактными и виртуальными классами? Между виртуальными и абстрактными методами?  
+  

___
43. ### Dispose(), Finalize() – что это за методы, как используются в .NET?  
+  

___
44. ### Для чего в .NET используется конструкция using(…){…}? Причем тут IDisposable?  
+  

___
45. ### Назовите явное имя параметра, передаваемого в метод set свойства класса?  

___
46. ### Что обозначает ключевое слово “virtual” для метода или свойства?  

___
47. ### Чем перекрытый метод отличается от перегруженного метода?  

___
48. ### Можно ли объявить перекрытый метод статическим, если перекрываемый метод не является статическим?  

___
49. ### Что такое «сопутствующая сборка» (satellite assembly)?  

___
50. ### Какая наименьшая исполнимая единица в .NET?  
Сборка - наименьшая единица развертывания.
___
51. ### Что происходит в памяти при упаковке и распаковке значимого типа?  
+  

___
52. ### Рефлексия в C#  

___
53. ### ref and out 
Использубтся для параметров метода. 

ref используется когда уже у нас инициализированна переменная за пределами метода и мы ее передаем по ссылке в нужный метод. Out - можно передавать переменную даже если она не инициализирована за пределами метода, но должна быть обязательно нициализирована в методе. 
54. ### Метаданные  

Результатом компилятора является **управляемый модуль**. Каждый управляемый модуль имеет таблицы метаданных. Есть два типа таблиц. 1 - описывающие типы данных и их члены, определнные в исзодном коде. 2 - описывающие типы данных и их члены, нак оторые имеются ссылки в исходном коде. 

Одни из немногих применений метаданным:
    **1.** Служит для облегчения написания и понимания кода. IntelliSense - анализирует метаданные что предпочтительно (методы, события, свойства) в каждом конкретном случае и какие параметры требуются конерктному методу. 
    **2.** В процессе верификации кода CLR считывает метаданные, чтобы убедиться, что код совершает только безопасные по отношению к типам действия. 
    **3.** Метаданные повзволяют сериализовать поля объекта. В случае передачи **сериализованных** данных на другой компьютер по сети, там можно произвести процесс **десериализации** и восстановить объект и его состояние уже на другой машине. 
    **4.** Позволяют сборщику мусора отслеживать жизненный цикл объектов, узнать типы объектов и определить какие поля ссылаются на другие объекты. 


55. ### 
56. ### 
57. ### 
58. ### 
59. ### 
60. ### 
61. ### 
62. ### 
63. ### 
64. ### 


Описание паттернов проектирования. 
Ссылки на репозитории реализации. 

### Паттерн наблюдатель. 

Паттерн наблюдаетель или "Observer"
Главная цель наблюдателя - уведомление всех заинтересованных объектов о событии или изменении состояния. 
Реализуется связь один ко многим между объектами таким образом, что при изменнии одного объекта, все зависящие от него, будут уведомлены об этом. По другому этот паттерн может быть описан как "Издатель - подписчик". 







Паттерн стратегия. 
Паттерн абстрактная фабрика. 



# pure JS

1. callbacks

Иными словами функция обратного вызова. Функция обратного вызова - это та функция, которая передается как параметр в другую функцию и выполняется после выполнения определенного условия. 

Пример синхронного вызова функции обратного вызова. 
```javascript

    function greeting(name) {
    alert('Hello ' + name);
    }

    function processUserInput(callback) {
    var name = prompt('Please enter your name.');
    callback(name);
    }

    processUserInput(greeting);

```

Пример асинхронного вызова 
```javascript
    async function pageLoader(callback) {
        const data = await fetch('/ru/docs/Словарь/функция_обратного_вызова')
        callback(data)
    }

    function onPageLoadingFinished(pageData) {
        console.log('Page was sucessfully loaded!')
        console.log('Response:')
        console.log(pageData)
    }

    pageLoader(onPageLoadingFinished)
```

Мы заранее не знаем, в какой момент времени произойдет выполнение функции fetch(). Но точно можем сказать, что результат выполнения будет выведет после ее завершения. 


2. promises
3. var let const
4. arrow functions
5. Prototypes

**Прототипы** - это механизм, с помощью которого объекты JavaScript наследуют свойства друг от друга. 




6. modules
7. async await
8.
9.
10.


# The interview questions Angular.

1. Dependency Injection

Внедрение зависимостей. Это способ создания объектов, которые зависят от других объектов. Система внедрения зависимостей предоставляет зависимые объекты, когда создает экземпляр класса.


2. 
3.
4.
5.
6.
7.
8.
9.
10.

# Тестирование

# Методологии 

1. ### Agile

    Agile - набор подходов по "гибкой" разработке ПО. 

    **Люди и взаимодействие** важнее процессов и инструментов
    **Работающий продукт** важнее исчерпывающей документации
    **Сотрудничество с заказчиком** важнее согласования условий контракта
    **Готовность к изменениям** важнее следования первоначальному плану

    То есть, не отрицая важности того, что справа,
    мы всё-таки больше ценим то, что слева.

    **Принципы Agile:**
    - Наивысшим приоритетом для нас является удовлетворение потребностей
    заказчика, благодаря регулярной и ранней поставке ценного программного
    обеспечения.

    - Изменение требований приветствуется, даже на поздних стадиях разработки.
    Agile-процессы позволяют использовать изменения для обеспечения заказчику
    конкурентного преимущества.

    - Работающий продукт следует выпускать как можно чаще, с периодичностью
    от пары недель до пары месяцев.

    - На протяжении всего проекта разработчики и представители бизнеса должны
    ежедневно работать вместе.

    - Над проектом должны работать мотивированные профессионалы. Чтобы
    работа была сделана, создайте условия, обеспечьте поддержку и полностью
    доверьтесь им.

    - Непосредственное общение является наиболее практичным и эффективным
    способом обмена информацией как с самой командой, так и внутри команды.

    - Работающий продукт — основной показатель прогресса.

    - Инвесторы, разработчики и пользователи должны иметь возможность
    поддерживать постоянный ритм бесконечно. Agile помогает наладить такой
    устойчивый процесс разработки.

    - Постоянное внимание к техническому совершенству и качеству
    проектирования повышает гибкость проекта.

    - Простота — искусство минимизации лишней работы — крайне необходима.

    - Самые лучшие требования, архитектурные и технические решения рождаются
    у самоорганизующихся команд.

    - Команда должна систематически анализировать возможные способы
    улучшения эффективности и соответственно корректировать
    стиль своей работы.


2. ### Scrum 

    Это уже конкретное направление Agile.  

    **Scrum – это «подход структуры»**. Над каждым проектом работает универсальная команда специалистов, к которой присоединяется еще два человека: владелец продукта и scrum-мастер. Первый соединяет команду с заказчиком и следит за развитием проекта; это не формальный руководитель команды, а скорее куратор. Второй помогает первому организовать бизнес-процесс: проводит общие собрания, решает бытовые проблемы, мотивирует команду и следит за соблюдением scrum-подхода.

    Scrum-подход делит рабочий процесс на равные спринты – обычно это периоды от недели до месяца, в зависимости от проекта и команды. Перед спринтом формулируются задачи на данный спринт, в конце – обсуждаются  результаты, а команда начинает новый спринт. Спринты очень удобно сравнивать между собой, что позволяет управлять эффективностью работы.
