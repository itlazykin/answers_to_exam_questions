## Gof

[1. Что такое паттерны проектирования?](#1-что-такое-паттерны-проектирования)

[2. Какие типы паттернов существуют?](#2-какие-типы-паттернов-существуют)

[3. Как работает паттерн Singleton? Приведите пример, когда его стоит использовать.](#3-как-работает-паттерн-singleton-приведите-пример-когда-его-стоит-использовать)

[4. Что такое Factory Method и чем он отличается от Abstract Factory?](#4-что-такое-factory-method-и-чем-он-отличается-от-abstract-factory)

[5. Чем отличаются паттерны Builder и Factory?](#5-чем-отличаются-паттерны-builder-и-factory)

[6. Как работает паттерн Adapter? Приведите пример.](#6-как-работает-паттерн-adapter-приведите-пример)

[7. Что делает паттерн Decorator? Чем он отличается от наследования?](#7-что-делает-паттерн-decorator-чем-он-отличается-от-наследования)

[8. Как работает паттерн Observer? Где его можно применить?](#8-как-работает-паттерн-observer-где-его-можно-применить)

[9. Что делает паттерн Strategy?](#9-что-делает-паттерн-strategy)

[10. Как работает паттерн Command? Где он может быть полезен?](#10-как-работает-паттерн-command-где-он-может-быть-полезен)

[11. Когда применение паттерна проектирования может усложнить систему?](#11-когда-применение-паттерна-проектирования-может-усложнить-систему)

# 1. Что такое паттерны проектирования?

Паттерны проектирования — это проверенные временем способы решения распространённых задач при проектировании
программного кода. Они помогают сделать код более гибким, поддерживаемым и удобочитаемым, но при этом не являются
готовыми кусками кода, а скорее набором рекомендаций.

[К оглавлению](#Gof)

# 2. Какие типы паттернов существуют?

Паттерны проектирования делятся на три группы:

+ порождающие — отвечают за создание объектов.
  Singleton, Factory Method, Abstract Factory, Builder, Prototype.
+ Структурные — определяют, как классы и объекты могут быть связаны между собой.
  Adapter, Decorator, Composite, Proxy, Bridge, Facade, Flyweight.
+ Поведенческие — описывают взаимодействие объектов.
  Strategy, Observer, Command, State, Chain of Responsibility, Template Method.

[К оглавлению](#Gof)

# 3. Как работает паттерн Singleton? Приведите пример, когда его стоит использовать.

Паттерн Singleton гарантирует, что в программе будет существовать только один экземпляр определённого класса и
предоставляет глобальную точку доступа к нему.

Пример реализации (ленивая инициализация, потокобезопасность):

```java
public class Singleton {
    private static volatile Singleton instance;

    private Singleton() {
    }

    public static Singleton getInstance() {
        if (instance == null) {
            synchronized (Singleton.class) {
                if (instance == null) {
                    instance = new Singleton();
                }
            }
        }
        return instance;
    }
}
```

Используется, например, для логирования, работы с конфигурацией приложения и управления соединением с базой данных.

#### Когда не стоит использовать Singleton?

+ Когда вам нужно создать несколько экземпляров класса, каждый из которых будет работать независимо (например, в случае
  с объектами, связанными с пользователем, сессиями или данными).
+ Когда вам нужно тестировать класс, так как Singleton может затруднить юнит-тестирование (из-за жесткой привязки ко
  всем частям приложения).

[К оглавлению](#Gof)

# 4. Что такое Factory Method и чем он отличается от Abstract Factory?

Factory Method — паттерн, который определяет интерфейс для создания объектов, но оставляет выбор того, какой именно
класс инстанцировать, подклассам.

```java
interface Product {
    void use();
}

class ConcreteProductA implements Product {
    public void use() {
        System.out.println("Используется продукт A");
    }
}

class Creator {
    public Product factoryMethod() {
        return new ConcreteProductA();
    }
}

```

Factory Method подходит, когда требуется делегировать создание объектов подклассам.

Abstract Factory — расширяет Factory Method и предоставляет интерфейс для создания семейств взаимосвязанных объектов, а
не одного типа.
Используется, когда нужно создавать сразу несколько объектов, работающих вместе.

[К оглавлению](#Gof)

# 5. Чем отличаются паттерны Builder и Factory?

+ Factory создаёт объекты целиком и сразу, скрывая процесс их создания.
+ Builder применяется, когда объект сложный, и его нужно собирать по шагам.

```java
class Car {
    private String engine;
    private int wheels;

    private Car(Builder builder) {
        this.engine = builder.engine;
        this.wheels = builder.wheels;
    }

    public static class Builder {
        private String engine;
        private int wheels;

        public Builder setEngine(String engine) {
            this.engine = engine;
            return this;
        }

        public Builder setWheels(int wheels) {
            this.wheels = wheels;
            return this;
        }

        public Car build() {
            return new Car(this);
        }
    }
}
```

[К оглавлению](#Gof)

# 6. Как работает паттерн Adapter? Приведите пример.

Adapter используется, когда необходимо сделать совместимыми два интерфейса, которые изначально не могут работать вместе.

Пример:
Допустим, у нас есть старый интерфейс OldPrinter, а новый код требует NewPrinter. Мы создаём адаптер:

```java
class OldPrinter {
    void printOld() { System.out.println("Старый принтер печатает"); }
}

interface NewPrinter {
    void print();
}

class PrinterAdapter implements NewPrinter {
    private OldPrinter oldPrinter;

    public PrinterAdapter(OldPrinter oldPrinter) {
        this.oldPrinter = oldPrinter;
    }

    public void print() {
        oldPrinter.printOld();
    }
}
Теперь новый код может работать с NewPrinter, не меняя старый класс.
```

[К оглавлению](#Gof)

# 7. Что делает паттерн Decorator? Чем он отличается от наследования?

Decorator позволяет динамически добавлять объектам новые свойства без изменения их кода.
В отличие от наследования, декораторы позволяют изменять поведение объекта на лету, а не на этапе компиляции.
"На лету" означает, что программа может адаптироваться к новым условиям или требованиям без остановки и перезапуска.

```java
interface Coffee {
    String getDescription();
    double getCost();
}

class SimpleCoffee implements Coffee {
    public String getDescription() { return "Обычный кофе"; }
    public double getCost() { return 5; }
}

class MilkDecorator implements Coffee {
    private Coffee coffee;

    public MilkDecorator(Coffee coffee) {
        this.coffee = coffee;
    }

    public String getDescription() { return coffee.getDescription() + ", с молоком"; }
    public double getCost() { return coffee.getCost() + 2; }
}
```

[К оглавлению](#Gof)

# 8. Как работает паттерн Observer? Где его можно применить?

Observer реализует механизм подписки: один объект (наблюдаемый) уведомляет подписчиков (наблюдателей) об изменениях.
Используется, например, в подписках на события, в системах уведомлений, UI-событиях.

```java
interface Observer {
    void update(String message);
}

class Subscriber implements Observer {
    private String name;
    public Subscriber(String name) { this.name = name; }

    public void update(String message) {
        System.out.println(name + " получил уведомление: " + message);
    }
}

class Publisher {
    private List<Observer> observers = new ArrayList<>();

    public void subscribe(Observer observer) { observers.add(observer); }
    public void notifyObservers(String message) {
        for (Observer observer : observers) {
            observer.update(message);
        }
    }
}

```

[К оглавлению](#Gof)

# 9. Что делает паттерн Strategy?

Strategy позволяет менять алгоритм работы объекта на лету.
"На лету" означает, что программа может адаптироваться к новым условиям или требованиям без остановки и перезапуска.

```java
interface PaymentStrategy {
    void pay(int amount);
}

class CreditCardPayment implements PaymentStrategy {
    public void pay(int amount) { System.out.println("Оплата кредитной картой: " + amount); }
}

class PayPalPayment implements PaymentStrategy {
    public void pay(int amount) { System.out.println("Оплата через PayPal: " + amount); }
}

class ShoppingCart {
    private PaymentStrategy paymentStrategy;

    public void setPaymentStrategy(PaymentStrategy paymentStrategy) {
        this.paymentStrategy = paymentStrategy;
    }

    public void checkout(int amount) {
        paymentStrategy.pay(amount);
    }
}

```

[К оглавлению](#Gof)

# 10. Как работает паттерн Command? Где он может быть полезен?

Command инкапсулирует запрос как объект, позволяя передавать его и выполнять позже.
Полезен в системах отложенного выполнения, меню действий.

```java
interface Command {
    void execute();
}

class Light {
    void turnOn() { System.out.println("Свет включен"); }
}

class TurnOnLightCommand implements Command {
    private Light light;

    public TurnOnLightCommand(Light light) { this.light = light; }

    public void execute() { light.turnOn(); }
}

```

[К оглавлению](#Gof)

# 11. Когда применение паттерна проектирования может усложнить систему?

+ Когда задача простая и не требует сложной структуры: Если вы решаете простую задачу, то добавление паттерна
  проектирования может быть излишним и только увеличит сложность системы. Например, если вы пишете маленькое приложение
  для личных нужд, использование паттернов вроде "Фабрика" или "Стратегия" может только утяжелить код, который и так
  будет легко читаем и поддерживаем.

+ Когда система уже работает, и добавление паттерна не решает реальных проблем: Применение паттерна может быть
  оправдано, если система имеет проблемы с расширяемостью, поддерживаемостью или изменчивостью. Но если система уже
  достаточно стабильна, то применение нового паттерна может просто добавить ненужный слой абстракции, который усложнит
  восприятие и поддержку кода.

+ Когда паттерн приводит к избыточности кода: Некоторые паттерны, такие как "Мост" или "Цепочка ответственности", могут
  требовать дополнительных классов или объектов, что увеличивает количество кода без значительного улучшения
  функционала. В этом случае дополнительная абстракция может только запутать систему, а не улучшить её.

[К оглавлению](#Gof)

