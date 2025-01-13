## Hibernate

[1. Что такое ORM?](#1-что-такое-orm)

[2. Опиши, как конфигурируется Hibernate. Рассказать про hibernate.cfg.xml и про mapping.](#2-опиши-как-конфигурируется-hibernate-рассказать-про-hibernatecfgxml-и-про-mapping)

[3. Жизненный цикл Entiity.](#3-жизненный-цикл-entiity)

[4. Зачем нужен класс SessionFactory? Является ли он потокобезопасным?](#4-зачем-нужен-класс-sessionfactory-является-ли-он-потоко-безопасным)

[5. Зачем нужен класс Session? Является ли он потокобезопасным?](#5-зачем-нужен-класс-session-является-ли-он-поток-обезопасным)

[6. В чем отличие методов Session.get Session.load?](#6-в-чем-отличие-методов-sessionget-sessionload)

[7. Расскажите про методы flush close.](#7-расскажите-про-методы-flush-close)

[8. В чем отличие методы save от saveOrUpdate и merge?](#8-в-чем-отличие-методы-save-от-saveorupdate-и-merge)

[9. Расскажите процесс создания, редактирования, чтения и удаления данных через Hibernate.](#9-расскажите-процесс-создания-редактирования-чтения-и-удаления-данных-через-hibernate)

[10. Как осуществляется иерархия наследования в Hibernate? Рассказать про три стратегии наследования.](#10-как-осуществляется-иерархия-наследования-в-hibernate-рассказать-про-три-стратегии-наследования)

[11. Можно ли создать собственный тип данных?](#11-можно-ли-создать-собственный-тип-данных)

[12. Какие коллекции поддерживаются на уровне mapping?](#12-какие-коллекции-поддерживаются-на-уровне-mapping)

[13. Зачем нужен класс Transactional?](#13-зачем-нужен-класс-transactional)

[14. Расскажите про уровни изоляции? Какие уровни поддерживаются в hibernate? Как их устанавливать?](#14-расскажите-про-уровни-изоляции-какие-уровни-поддерживаются-в-hibernate-как-их-устанавливать)

[15. Что такое OplimisticLock? Расскажите стратегии создания через version, timestamp.](#15-что-такое-oplimisticlock-расскажите-стратегии-создания-через-version-timestamp)

[16. Расскажите про стратегии извлечения данных eager, lazy?](#16-расскажите-про-стратегии-извлечения-данных-eager-lazy)

[17. Что такое объект Proxy? С чем связана ошибка LazyInitializationException? Как ее избежать?](#17-что-такое-объект-proxy-с-чем-связана-ошибка-lazyinitializationexception-как-ее-избежать)

[18. HQL. Расскажи основные элементы синтаксиса HQL? Простой запрос, запрос join? Создания объекта через конструктор.](#18-hql-расскажи-основные-элементы-синтаксиса-hql-простой-запрос-запрос-join-создания-объекта-через-конструктор)

[19. Расскажите про уровни кешей в Hibernate?](#19-расскажите-про-уровни-кешей-в-hibernate)

[20. Что такое StatelessSessionFactory? Зачем он нужен, где он используется?](#20-что-такое-statelesssessionfactory-зачем-он-нужен-где-он-используется)

[21. Зачем нужен режим read-only?](#21-зачем-нужен-режим-read-only)

[22. Расскажите, какие шаблоны проектирования используется в Hibernate (factory, proxy, strategy)](#22-расскажите-какие-шаблоны-проектирования-используется-в-hibernate-factory-proxy-strategy)

# 1. Что такое ORM?

ORM (Object-Relational Mapping) — это техника программирования, которая позволяет преобразовывать данные между
объектно-ориентированным программированием и реляционной базой данных.

Грубо говоря, ORM — это мост между вашим Java-кодом и таблицами базы данных. Он позволяет работать с базой данных так,
как если бы вы работали с объектами Java, вместо того чтобы писать SQL-запросы вручную.

[К оглавлению](#Hibernate)

# 2. Опиши, как конфигурируется Hibernate. Рассказать про hibernate.cfg.xml и про mapping.

Чтобы использовать Hibernate в приложении, нужно настроить его. Настройка включает указание подключения к базе данных,
параметры сессий и маппинг объектов на таблицы.

1. `hibernate.cfg.xml`

Это основной конфигурационный файл, который содержит настройки Hibernate и подключения к базе данных. Обычно его кладут
в папку src/main/resources.

```java
Пример hibernate.cfg.xml:

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE hibernate-configuration PUBLIC 
    "-//Hibernate/Hibernate Configuration DTD 3.0//EN" 
    "http://hibernate.sourceforge.net/hibernate-configuration-3.0.dtd">
<hibernate-configuration>
    <session-factory>
        <!-- JDBC Properties -->
        <property name="hibernate.connection.driver_class">org.postgresql.Driver</property>
        <property name="hibernate.connection.url">jdbc:postgresql://localhost:5432/mydb</property>
        <property name="hibernate.connection.username">user</property>
        <property name="hibernate.connection.password">password</property>

        <!-- Dialect -->
        <property name="hibernate.dialect">org.hibernate.dialect.PostgreSQLDialect</property>

        <!-- Show SQL -->
        <property name="hibernate.show_sql">true</property>
        <property name="hibernate.format_sql">true</property>

        <!-- HBM2DDL AUTO -->
        <property name="hibernate.hbm2ddl.auto">update</property>

        <!-- Mapping -->
        <mapping class="com.example.model.User"/>
    </session-factory>
</hibernate-configuration>
```

#### Ключевые элементы:

+ hibernate.connection.driver_class: JDBC-драйвер для подключения к БД.
+ hibernate.connection.url: URL для подключения.
+ hibernate.connection.username и password: Учетные данные.
+ hibernate.dialect: Указывает, какая база данных используется (PostgreSQL, MySQL и т.д.).
+ hibernate.show_sql: Логировать SQL-запросы в консоль.
+ hibernate.hbm2ddl.auto: Автоматическое создание или обновление схемы БД (update, create, create-drop, validate, none).

2. `Маппинг (Mapping)`

Маппинг связывает классы Java с таблицами базы данных. Hibernate использует два подхода:

+ Аннотации (рекомендуется)
+ Файлы .hbm.xml (устарело)

#### Маппинг с помощью аннотаций

Классы модели отмечаются аннотациями из пакета javax.persistence и org.hibernate.

```java
import jakarta.persistence.*;

@Entity
@Table(name = "users")
public class User {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @Column(name = "username", nullable = false, unique = true)
    private String username;

    @Column(name = "email", nullable = false)
    private String email;

    // Геттеры и сеттеры
}
```

#### Ключевые аннотации:

+ `@Entity`: Класс является сущностью, маппится на таблицу.
+ `@Table(name = "table_name")`: Указывает имя таблицы.
+ `@Id`: Указывает первичный ключ.
+ `@GeneratedValue`: Настройка генерации ключа (например, автоинкремент).
+ `@Column`: Настраивает имя столбца, ограничения и др.

[К оглавлению](#Hibernate)

# 3. Жизненный цикл Entiity.

В Hibernate сущность (Entity) может находиться в одном из четырех состояний в течение своего жизненного цикла. Эти
состояния определяют, как объект взаимодействует с контекстом persistence и базой данных.

1. `Transient` (Переходное состояние)

Сущность создается как обычный объект Java, но Hibernate о ней ничего не знает. Она не связана с базой данных и не
управляется Hibernate.

Характеристики:

+ Объект создан с помощью конструктора, но не сохранен в базе.
+ У объекта нет идентификатора (или идентификатор не соответствует записи в БД).
+ Hibernate не управляет этим объектом.

```java
User user = new User(); // Transient
user.setUsername("John");
```
#### Как перейти из Transient:

Вызвать метод save(), persist(), или saveOrUpdate().

2. `Persistent` (Состояние управления)

Сущность управляется Hibernate и связана с контекстом persistence (например, сессией). Все изменения объекта
автоматически синхронизируются с базой данных.

Характеристики:

+ Hibernate отслеживает изменения сущности.
+ Изменения автоматически записываются в базу данных при закрытии сессии или вызове метода flush().
```java


Session session = sessionFactory.openSession();
Transaction tx = session.beginTransaction();

User user = new User(); // Transient
user.setUsername("John");

// Сохраняем объект
session.save(user); // Persistent

tx.commit();
session.close();
```
После вызова session.save(user) объект становится Persistent.

3. `Detached` (Отключенное состояние)

Сущность была связана с контекстом persistence, но связь разорвана, например, из-за закрытия сессии. Hibernate больше не
управляет этим объектом.

Характеристики:

+ Изменения объекта после разрыва связи больше не синхронизируются с базой.
+ Объект все еще существует в памяти и может быть связан обратно с Hibernate.
```java
Session session = sessionFactory.openSession();
Transaction tx = session.beginTransaction();

User user = session.get(User.class, 1); // Persistent
tx.commit();
session.close(); // Detached
```
#### Как снова сделать Persistent:

+ Использовать метод update() или merge().
```java
Session newSession = sessionFactory.openSession();
Transaction newTx = newSession.beginTransaction();

newSession.update(user); // Снова Persistent
newTx.commit();
newSession.close();
```
4. `Removed` (Удаленное состояние)

Сущность помечена для удаления из базы данных, но еще не удалена.

Характеристики:

+ Hibernate управляет сущностью, но при выполнении flush() или commit() она будет удалена из базы.
```java
Session session = sessionFactory.openSession();
Transaction tx = session.beginTransaction();

User user = session.get(User.class, 1); // Persistent
session.delete(user); // Removed

tx.commit(); // Удаление из базы данных
session.close();
```
Визуализация переходов:

+ Transient → Persistent: save(), persist().
+ Persistent → Detached: close(), evict(), или завершение сессии.
+ Detached → Persistent: update(), merge().
+ Persistent → Removed: delete().

Таким образом, Hibernate контролирует объект только в состоянии Persistent или Removed, а в других состояниях объект
существует независимо.

[К оглавлению](#Hibernate)

# 4. Зачем нужен класс SessionFactory? Является ли он потоко безопасным?

Именно из объекта SessionFactory мы получаем объекты типа Session. Он
служит фабрикой для сессий и является основным способом взаимодействия с базой данных через Hibernate. На все приложение
существует только одна
SessionFactory и она инициализируеться вместе со стартом приложения. SessionFactory кэширует мета-дату и SQL запросы
которые часто используются приложением во время работы. Так же оно кэширует информацию, которая была получена в одной из
транзакций и может быть использована и в других транзакциях.

Класс SessionFactory является потокобезопасным, что позволяет использовать один объект SessionFactory в приложении для
обработки запросов от разных потоков.

```java
Пример создания SessionFactory
Обычно объект SessionFactory создается с помощью класса Configuration.

import org.hibernate.SessionFactory;
import org.hibernate.cfg.Configuration;

public class HibernateUtil {
    private static final SessionFactory sessionFactory;

    static {
        try {
            // Создание SessionFactory из конфигурации
            sessionFactory = new Configuration().configure().buildSessionFactory();
        } catch (Throwable ex) {
            throw new ExceptionInInitializerError(ex);
        }
    }

    public static SessionFactory getSessionFactory() {
        return sessionFactory;
    }
}

Затем SessionFactory можно использовать в любом месте 
приложения для создания Session:
Session session = HibernateUtil.getSessionFactory().openSession();
```

[К оглавлению](#Hibernate)

# 5. Зачем нужен класс Session? Является ли он поток обезопасным?

Session — это основной интерфейс, который отвечает за связь с базой данных. Так же, он помогает создавать объекты
запросов, для получения - персистентных объектов. (Персистентный объект — объект, который уже находится в базе данных;
объект запроса — объект, который получается когда мы получаем результат запроса в базу данных, именно с ним работает
приложение). Объект Session можно получить из SessionFactory:
```java

Session session = sessionFactory.openSession();
```
Роль интерфейса Session:

+ является оберткой для jdbc подключения к базе данных; 
+ является фабрикой для транзакций (согласно официальной документации transaction — аllows the application to define units
of work, что по сути, означает что транзакция определяет границы операций связанных с базой данных).
+ является хранителем обязательного кэша первого уровня.

Жизненный цикл объекта session связан с началом и окончанием транзакции. Этот объект предоставляет методы для CRUD (
create, read, update, delete) операций для объекта персистентности. С помощью этого экземпляра можно выполнять HQL, SQL
запросы и задавать критерии выборки.

Объект Hibernate Session не является потокобезопасным. Каждый поток должен иметь свой собственный объект Session и
закрывать его по окончанию.

[К оглавлению](#Hibernate)

# 6. В чем отличие методов Session.get Session.load?

Наиболее часто используемые методы для загрузки данных из базы данных — get() и load().

+ `get()` загружает данные сразу при вызове, в то время как load() использует прокси объект и загружает данные только
  тогда,
  когда это требуется на самом деле. В этом плане load() имеет преимущество в плане ленивой загрузки данных.
+ `load()` бросает исключение, когда данные не найдены. Поэтому его нужно использовать только при уверенности в
  существовании данных.
  Нужно использовать метод get(), если необходимо удостовериться в наличии данных в БД.
  В случае обращение к несуществующему объекту, метод get(); вернет null. В случае нахождения объект, метод get();
  вернет
  сам объект и запрос в базу данных будет произведен немедленно.

Используйте get(), если:
Вы не уверены, существует ли объект.
Вам нужно сразу загрузить все данные объекта.

Используйте load(), если:
Вы уверены, что объект существует.
Хотите отложить выполнение запроса для оптимизации.
Работаете с большими объемами данных и не хотите
загружать объект до необходимости.

[К оглавлению](#Hibernate)

# 7. Расскажите про методы flush close.

1. Метод flush

Метод flush используется для синхронизации состояния объектов в контексте сессии с базой данных, но при этом транзакция
еще не фиксируется. То есть flush отправляет изменения в базу данных, но не выполняет commit.

```java
Пример использования:

Session session = sessionFactory.openSession();
Transaction tx = session.beginTransaction();

User user = new User("JohnDoe");
session.save(user);

// Данные записываются в базу, но транзакция еще не завершена
session.flush();

tx.commit();
session.close();
```

2. Метод close

Метод close используется для закрытия сессии и освобождения всех связанных с ней ресурсов. После вызова этого метода
Session больше нельзя использовать.

```java
Session session = sessionFactory.openSession();
Transaction tx = session.beginTransaction();

User user = session.get(User.class, 1);
System.out.println(user.getUsername());

// Завершаем транзакцию
tx.commit();

// Закрываем сессию
session.close();
```

#### Ошибки, связанные с использованием

+ Пропуск flush:
        Если изменения не синхронизированы с базой перед 
        выполнением HQL-запроса, может возникнуть неожиданное поведение.

+ Пропуск close:
        Если не закрывать сессию, это приведет к утечке ресурсов 
        (слишком большое количество открытых соединений с базой).

[К оглавлению](#Hibernate)

# 8. В чем отличие методы save от saveOrUpdate и merge?

+ Hibernate save() используется для сохранения сущности в базу данных. Проблема с использованием метода save() заключается
в том, что он может быть вызван без транзакции. А следовательно если у нас имеется отображение нескольких объектов, то
только первичный объект будет сохранен и мы получим несогласованные данные. Также save() немедленно возвращает
сгенерированный идентификатор.

+ Hibernate persist() аналогичен save() с транзакцией. persist() не возвращает сгенерированный идентификатор сразу.

+ Hibernate saveOrUpdate() использует запрос для вставки или обновления, основываясь на предоставленных данных. Если
данные уже присутствуют в базе данных, то будет выполнен запрос обновления. Метод saveOrUpdate() можно применять без
транзакции, но это может привести к аналогичным проблемам, как и в случае с методом save().

+ Hibernate merge() может быть использован для обновления существующих значений, однако этот метод создает копию из
переданного объекта сущности и возвращает его. Возвращаемый объект является частью контекста персистентности и
отслеживает любые изменения, а переданный объект не отслеживается.

| Характеристика           | save	                        | saveOrUpdate                        | merge                                 |
|--------------------------|------------------------------|-------------------------------------|---------------------------------------|
| Операция                 | Всегда INSERT                | INSERT или UPDATE                   | INSERT или UPDATE                     |
| Работа с идентификатором | Требует нового объекта       | Проверяет идентификатор             | Не зависит от идентификатора          |
| Контекст объекта         | Объект становится Persistent | Объект становится Persistent        | Оригинальный объект остается Detached |
| SQL-запрос               | Только INSERT                | INSERT или UPDATE                   | INSERT или UPDATE                     |
| Возвращаемое значение    | Serializable 	               | Ничего не возвращает                | Новый Persistent объект               |
| Использование            | Для новых объектов           | Для новых или существующих объектов | Для работы с Detached объектами       |

[К оглавлению](#Hibernate)

# 9. Расскажите процесс создания, редактирования, чтения и удаления данных через Hibernate.

Процесс работы с данными через Hibernate включает стандартные CRUD-операции: создание, чтение, редактирование и удаление
данных. Hibernate использует объекты для работы с таблицами базы данных, обеспечивая удобное взаимодействие через API.

+ Создание: Используйте save для новых объектов.
+ Чтение: Используйте get, load или HQL-запросы.
+ Обновление: Используйте update для объектов в базе или измените Persistent объект напрямую.
+ Удаление: Используйте delete для удаления объекта.

Все операции выполняются через сессию, в рамках транзакции.
```java
Session session = sessionFactory.openSession();
Transaction tx = session.beginTransaction();

// Создание
User newUser = new User("JaneDoe", "jane.doe@example.com");
session.save(newUser);

// Чтение
User user = session.get(User.class, newUser.getId());
System.out.println("Email before update: " + user.getEmail());

// Обновление
user.setEmail("updated.email@example.com");
session.update(user);

// Удаление
session.delete(user);

tx.commit();
session.close();

```

[К оглавлению](#Hibernate)

# 10. Как осуществляется иерархия наследования в Hibernate? Рассказать про три стратегии наследования.

Hibernate поддерживает объектно-реляционное отображение наследования (inheritance mapping), предоставляя три стратегии
для представления иерархии наследования в базе данных:

+ Одна таблица на иерархию классов
+ Одна таблица на подкласс
+ Одна таблица на каждый конкретный класс

1. Table per Class Hierarchy (Одна таблица на иерархию классов)

Описание:
Вся иерархия наследования отображается в одну таблицу. Hibernate добавляет специальный дискриминаторный столбец (@DiscriminatorColumn) для идентификации типа объекта.

Аннотации:

    @Inheritance(strategy = InheritanceType.SINGLE_TABLE)
    @DiscriminatorColumn — указывает столбец для определения типа.

2. Table per Subclass (Одна таблица на подкласс)

Описание:
Для каждого класса в иерархии создается отдельная таблица. Таблицы подклассов ссылаются на таблицу базового класса через внешний ключ.

Аннотации:

    @Inheritance(strategy = InheritanceType.JOINED)

3. Table per Concrete Class (Одна таблица на каждый конкретный класс)

Описание:
Для каждого конкретного класса (не абстрактного) создается своя таблица, содержащая все поля класса, включая наследуемые от базового.

Аннотации:

    @Inheritance(strategy = InheritanceType.TABLE_PER_CLASS)

#### Рекомендации по выбору стратегии

+    SINGLE_TABLE:
    Подходит для небольших иерархий с минимальными специфичными полями у подклассов.
+    JOINED:
    Используйте, если требуется высокая степень нормализации и связь данных между таблицами.
+    TABLE_PER_CLASS:
    Подходит для случаев, когда объекты подклассов хранятся отдельно и нет необходимости в запросах всей иерархии.

[К оглавлению](#Hibernate)

# 11. Можно ли создать собственный тип данных?

Да, в Hibernate можно создать собственный тип данных. Это делается с помощью пользовательских типов (UserType или AttributeConverter),
что позволяет отображать нестандартные типы Java на реляционные типы базы данных.

+ Реализация UserType
Интерфейс UserType предоставляет полный контроль над преобразованием данных между Java и SQL.
Пример: отображение LocalDate в SQL-тип DATE.

+ Использование AttributeConverter
Более простой подход для создания типов, появившийся в JPA 2.1.
Пример: отображение Boolean как Y/N.

[К оглавлению](#Hibernate)

# 12. Какие коллекции поддерживаются на уровне mapping?

[К оглавлению](#Hibernate)

# 13. Зачем нужен класс Transactional?

[К оглавлению](#Hibernate)

# 14. Расскажите про уровни изоляции? Какие уровни поддерживаются в hibernate? Как их устанавливать?

[К оглавлению](#Hibernate)

# 15. Что такое OplimisticLock? Расскажите стратегии создания через version, timestamp.

[К оглавлению](#Hibernate)

# 16. Расскажите про стратегии извлечения данных eager, lazy?

[К оглавлению](#Hibernate)

# 17. Что такое объект Proxy? С чем связана ошибка LazyInitializationException? Как ее избежать?

[К оглавлению](#Hibernate)

# 18. HQL. Расскажи основные элементы синтаксиса HQL? Простой запрос, запрос join? Создания объекта через конструктор.

[К оглавлению](#Hibernate)

# 19. Расскажите про уровни кешей в Hibernate?

[К оглавлению](#Hibernate)

# 20. Что такое StatelessSessionFactory? Зачем он нужен, где он используется?

[К оглавлению](#Hibernate)

# 21. Зачем нужен режим read-only?

[К оглавлению](#Hibernate)

# 22. Расскажите, какие шаблоны проектирования используется в Hibernate (factory, proxy, strategy)

[К оглавлению](#Hibernate)