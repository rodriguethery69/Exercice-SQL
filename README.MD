
![tableau](/img/tableau.png)
```
mysql> USE dbmovie_utopia;
Database changed
mysql> CREATE TABLE movies;
ERROR 4028 (HY000): A table must have at least one visible column.
mysql> CREATE table movies (
    -> id int primary key auto_increment not null,
    -> title varchar(250) NOT NULL,
    -> rating float not null,
    -> year_released int NOT NULL,
    -> box_office BIGINT NOT NULL,
    -> budget BIGINT NOT NULL,
    -> duration INT NOT NULL,
    -> distribution_company_id INT NOT NULL,
    -> genreID int NOT NULL,
    -> directorID int NOT NULL);
Query OK, 0 rows affected (0.01 sec)
```


```
mysql> CREATE TABLE movie_language(
    -> movieID int NOT NULL,
    -> languageID int NOT NULL
    -> );
Query OK, 0 rows affected (0.00 sec)
```

```
mysql> ALTER TABLE movie_language ADD FOREIGN KEY (movieID) REFERENCES movies(id);;
Query OK, 0 rows affected (0.01 sec)
Enregistrements: 0  Doublons: 0  Avertissements: 0
```

```
mysql> CREATE TABLE languages(
    -> id INT PRIMARY KEY NOT NULL AUTO_INCREMENT,
    -> name VARCHAR(250)
    -> );
Query OK, 0 rows affected (0.00 sec)

mysql> ALTER TABLE movie_language ADD FOREIGN KEY(languageID) REFERENCES languages(id);
Query OK, 0 rows affected (0.01 sec)
Enregistrements: 0  Doublons: 0  Avertissements: 0

mysql> ALTER TABLE languages
    -> MODIFY COLUMN name VARCHAR(250) NOT NULL;
Query OK, 0 rows affected (0.01 sec)
Enregistrements: 0  Doublons: 0  Avertissements: 0
```

```
mysql> INSERT INTO languages (name) VALUES ('English'), ('Sicilian'), ('German'), ('Yddish'), ('Italian'), ('Spanish'), ('French');
Query OK, 7 rows affected (0.00 sec)
Enregistrements: 7  Doublons: 0  Avertissements: 0
```

```
mysql> ALTER TABLE movie_language
    -> MODIFY COLUMN languageID INT NOT NULL DEFAULT 1;
Query OK, 0 rows affected (0.01 sec)
Enregistrements: 0  Doublons: 0  Avertissements: 0
```

```
mysql> CREATE TABLE distribution_compagny(
    -> id INT PRIMARY KEY AUTO_INCREMENT NOT NULL,
    -> name VARCHAR(110)
    -> );
Query OK, 0 rows affected (0.00 sec)
```

```
mysql> ALTER TABLE movies ADD FOREIGN KEY (distribution_company_id) REFERENCES distribution_compagny(id);
Query OK, 0 rows affected (0.01 sec)
Enregistrements: 0  Doublons: 0  Avertissements: 0
```

```
mysql> CREATE TABLE genre(
    -> id INT PRIMARY KEY AUTO_INCREMENT NOT NULL,
    -> name VARCHAR(250) NOT NULL
    -> );
Query OK, 0 rows affected (0.00 sec)
```

```
mysql> ALTER TABLE movies ADD FOREIGN KEY (genreID) REFERENCES genre(id);
Query OK, 0 rows affected (0.01 sec)
Enregistrements: 0  Doublons: 0  Avertissements: 0
```