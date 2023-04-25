# SQL_Lecture_2
# More SQL

## Get certain information out only

Get the number of rows in a table

```SQL
SELECT COUNT(*) FROM table_name
```

Search for a row

```SQL
SELECT * FROM table_name WHERE column_name LIKE "%some value%" --Here some value refers to the content of the rows
```

## Create today's database

```SQL
CREATE TABLE bands (
    id          INTEGER PRIMARY KEY AUTOINCREMENT
                        UNIQUE
                        NOT NULL,
    band_name   TEXT    NOT NULL,
    formed_year INTEGER NOT NULL,
    genre       TEXT    NOT NULL
);
```

```SQL
INSERT INTO bands (id, band_name, formed_year, genre)
VALUES
    (1, 'Metallica', 1981, 'metal'),
    (2, 'Black Sabbath', 1968, 'metal'),
    (3, 'Led Zeppelin', 1968, 'rock'),
    (4, 'Iron Maiden', 1975, 'metal');
```

```SQL
CREATE TABLE albums (
    album_id      INTEGER PRIMARY KEY AUTOINCREMENT
                          UNIQUE
                          NOT NULL,
    album_name    TEXT    NOT NULL,
    released_year INTEGER NOT NULL,
    band_id       INTEGER REFERENCES bands (id) 
                          NOT NULL
);
```

```SQL
INSERT INTO albums (album_id, album_name, released_year, band_id)
VALUES 
    (1, 'Kill ''Em All', 1983, 1),
    (2, 'Ride the Lightning', 1984, 1),
    (3, 'Master of Puppets', 1986, 1),
    (4, '...And Justice for All', 1988, 1),
    (5, 'Metallica', 1991, 1),
    (6, 'Load', 1996, 1),
    (7, 'Reload', 1997, 1),
    (8, 'St. Anger', 2003, 1),
    (9, 'Death Magnetic', 2008, 1),
    (10, 'Hardwired... to Self-Destruct', 2016, 1),
    (11, '72 Seasons', 2023, 1),
    (12, 'Black Sabbath', 1970, 2),
    (13, 'Paranoid', 1970, 2),
    (14, 'Master of Reality', 1971, 2),
    (15, 'Vol. 4', 1972, 2),
    (16, 'Sabbath Bloody Sabbath', 1973, 2),
    (17, 'Sabotage', 1975, 2),
    (18, 'Led Zeppelin', 1969, 3),
    (19, 'Led Zeppelin II', 1969, 3),
    (20, 'Led Zeppelin III', 1970, 3),
    (21, 'Led Zeppelin IV', 1971, 3),
    (22, 'Houses of the Holy', 1973, 3),
    (23, 'Iron Maiden', 1980, 4),
    (24, 'Killers', 1981, 4),
    (25, 'The Number of the Beast', 1982, 4),
    (26, 'Piece of Mind', 1983, 4),
    (27, 'Powerslave', 1984, 4),
    (28, 'Somewhere in Time', 1986, 4),
    (29, 'Seventh Son of a Seventh Son', 1988, 4),
    (30, 'No Prayer for the Dying', 1990, 4);
```

```SQL
CREATE TABLE members (
    member_id  INTEGER PRIMARY KEY AUTOINCREMENT
                       NOT NULL
                       UNIQUE,
    first_name TEXT    NOT NULL,
    last_name  TEXT    NOT NULL,
    instrument TEXT    NOT NULL,
    band_id    INTEGER REFERENCES bands (id) 
                       NOT NULL
);
```

```SQL
INSERT INTO members (
                        member_id,
                        first_name,
                        last_name,
                        instrument,
                        band_id
                    )
VALUES 
    (1, 'James', 'Hetfield', 'Guitar, Vocals', 1),
    (2, 'Lars', 'Ulrich', 'Drums', 1),
    (3, 'Kirk', 'Hammet', 'Guitar', 1),
    (4, 'Robert', 'Trujillo', 'Bass', 1),
    (5, 'Ozzy', 'Osbourne', 'Vocals', 2),
    (6, 'Bill', 'Ward', 'Drums', 2),
    (7, 'Geezer', 'Butler', 'Bass', 2),
    (8, 'Tony', 'Iommi', 'Guitar', 2),
    (9, 'Robert', 'Plant', 'Vocals', 3),
    (10, 'John', 'Bonham', 'Drums', 3),
    (11, 'John Paul', 'Jones', 'Bass', 3),
    (12, 'Jimmy', 'Page', 'Guitar', 3),
    (13, 'Steve', 'Harris', 'Bass', 4),
    (14, 'Dave', 'Murray', 'Guitar', 4),
    (15, 'Adrian', 'Smith', 'Guitar', 4),
    (16, 'Bruce', 'Dickinson', 'Vocals', 4),
    (17, 'Nicko', 'McBrain', 'Drums', 4),
    (18, 'Janick', 'Gers', 'Guitar', 4);
```