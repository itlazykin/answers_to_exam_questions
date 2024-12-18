## Hibernate

[1. Что такое ORM?](#1-что-такое-orm)

[2. Опиши, как конфигурируется Hibernate. Рассказать про hibernate.cfg.xml и про mapping.](#2-опиши-как-конфигурируется-hibernate-рассказать-про-hibernatecfgxml-и-про-mapping)

[3. Жизненный цикл Entiity.](#3-жизненный-цикл-entiity)

[4. Зачем нужен класс SessionFactory? Является ли он потокобезопасным?](#4-зачем-нужен-класс-sessionfactory-является-ли-он-потокобезопасным)

[5. Зачем нужен класс Session? Является ли он потокобезопасным?](#5-зачем-нужен-класс-session-является-ли-он-потокобезопасным)

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

Это основной конфигурационный файл, который содержит настройки Hibernate и подключения к базе данных. Обычно его кладут в папку src/main/resources.

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

#### Маппинг через .hbm.xml (устарело)

Файлы .hbm.xml описывают связь между классами и таблицами.

```java
<?xml version="1.0"?>
<!DOCTYPE hibernate-mapping PUBLIC 
    "-//Hibernate/Hibernate Mapping DTD 3.0//EN" 
    "http://hibernate.sourceforge.net/hibernate-mapping-3.0.dtd">
<hibernate-mapping>
    <class name="com.example.model.User" table="users">
        <id name="id" column="id" type="long">
            <generator class="identity"/>
        </id>
        <property name="username" column="username" not-null="true" unique="true"/>
        <property name="email" column="email" not-null="true"/>
    </class>
</hibernate-mapping>

Этот файл указывается в hibernate.cfg.xml:
<mapping resource="com/example/model/User.hbm.xml"/>
```

[К оглавлению](#Hibernate)

# 3. Жизненный цикл Entiity.

1. `Transient` (Переходное состояние)

Сущность создается как обычный объект Java, но Hibernate о ней ничего не знает. Она не связана с базой данных и не управляется Hibernate.

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

Сущность управляется Hibernate и связана с контекстом persistence (например, сессией). Все изменения объекта автоматически синхронизируются с базой данных.

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

Сущность была связана с контекстом persistence, но связь разорвана, например, из-за закрытия сессии. Hibernate больше не управляет этим объектом.

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

Таким образом, Hibernate контролирует объект только в состоянии Persistent или Removed, а в других состояниях объект существует независимо.

[К оглавлению](#Hibernate)

# 4. Зачем нужен класс SessionFactory? Является ли он потокобезопасным?

[К оглавлению](#Hibernate)

# 5. Зачем нужен класс Session? Является ли он потокобезопасным?

[К оглавлению](#Hibernate)

# 6. В чем отличие методов Session.get Session.load?

[К оглавлению](#Hibernate)

# 7. Расскажите про методы flush close.

[К оглавлению](#Hibernate)

# 8. В чем отличие методы save от saveOrUpdate и merge?

[К оглавлению](#Hibernate)

# 9. Расскажите процесс создания, редактирования, чтения и удаления данных через Hibernate.

[К оглавлению](#Hibernate)

# 10. Как осуществляется иерархия наследования в Hibernate? Рассказать про три стратегии наследования.

[К оглавлению](#Hibernate)

# 11. Можно ли создать собственный тип данных?

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