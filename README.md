# hibernate-tutorial1
Hibernate Basic configuration

[![contributions welcome](https://img.shields.io/badge/contributions-welcome-orange.svg?style=flat)](https://github.com/nfriaa/hibernate-tutorial1/issues) [![Travis](https://img.shields.io/travis/rust-lang/rust.svg)](https://github.com/nfriaa/hibernate-tutorial1) [![license](https://img.shields.io/github/license/mashape/apistatus.svg)](https://github.com/nfriaa/hibernate-tutorial1/blob/master/LICENSE)

## Description
A sample code to configure maven project and test connection to MySQL database and execute some queries using Hibernate.
* JavaSE 8
* Hibernate 5
* Maven 4
* MySQL 5

## 1. Create database
```sql
CREATE DATABASE `persist_db` /*!40100 DEFAULT CHARACTER SET utf8 */
```

## 2. Create tables
```sql
CREATE TABLE `persist_db`.`product` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `name` varchar(255) DEFAULT NULL,
  `price` int(11) DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

CREATE TABLE `persist_db`.`test` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```

## 3. Create maven project and add dependencies
```xml
<!-- MySQL connector -->
<dependency>
    <groupId>mysql</groupId>
    <artifactId>mysql-connector-java</artifactId>
    <version>6.0.6</version>
</dependency>
<!-- Hibernate -->
<dependency>
    <groupId>org.hibernate</groupId>
    <artifactId>hibernate-core</artifactId>
    <version>5.2.11.Final</version>
</dependency>
```

## 4. Create the hibernate config file 'hibernate.cfg.xml'
```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE hibernate-configuration PUBLIC "-//Hibernate/Hibernate Configuration DTD 3.0//EN" "http://hibernate.sourceforge.net/hibernate-configuration-3.0.dtd">
<hibernate-configuration>
    <session-factory>
        <property name="hibernate.dialect">org.hibernate.dialect.MySQLDialect</property>
        <property name="hibernate.connection.url">jdbc:mysql://localhost:3306/persist_db?useTimezone=true&amp;serverTimezone=UTC</property>
        <property name="hibernate.connection.username">root</property>
        <property name="hibernate.connection.password">root</property>
    </session-factory>
</hibernate-configuration>
```

## 5. Create HibernateUtil.java 
Hibernate Utility class with a convenient method to get Session Factory.

## 6. Create main Application class
* a class whith main method to test connection
* execute some queries in SQL mode (NativeQuery) : session.createNativeQuery() method
* select, insert... and read results
