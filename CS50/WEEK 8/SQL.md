# SQL

https://www.youtube.com/watch?v=AywtnUjQ6X4&feature=youtu.be

Ofter times, in order for us to build the most functional website we can, we depend on a **database** to store information.

If you've ever used Microsoft Excel or Google Spreadsheets (among others), odds are you're familiar with the notion of a database: a hierarchically organized set of tables, each of which contains a set of rows and columns.

SQL (the *Structured Query Language*) is a programming language whose purpose is to **query** a database 

**MySQL** is one open-source platform on which you can establish the type of relational database that SQL is most adept at working with.

- **SQLite** is another, which we've actually use in CS50 since 2016.

Many installations of SQL come witha GUI tool called **phpMyAdmin** which can be used to execute database queries in a more user-friendly way.

After you create a database, the next thing you'll most likely want to do is create a **table**.

- The syntax for doing this is actually a bit awkward to do programmatically, at least at the outset, and so this is where phpMyAdmin will come in handy.

As part of the process of creating a table, you'll be asked to specify all of the **columns** in that table.

Thereafter, all your queries will refer to **rows** of the table.

Each column of your SQL table is capable of holding data fo a particular data type.

Unlike in C, the CHAR data type in SQL does not refer to a single character. Rather, it is a fixed-length string.

- In most relational databases, including MySQL, you actually specify the fixed-length as part of the type definition, e.g. CHAR(10).

A VARCHAR refers to a variable-length string.

- VARCHARs also require you to specify the **maximum** possible length of a string that could be stored in that column, e.g. VARCHAR(99).

SQLite has these data types as well, but affiliates each with a "type affinity" to simplify things. (8:21)

 

| NULL | INTEGER | REAL | TEXT | BLOB |
| :--: | :-----: | :--: | :--: | :--: |
|      |         |      |      |      |

One other important consideration when contstructing a table in SQL is to choose one column to be your 