# FCC_universe.sql

This is my solution for the [**Celestial Bodies Database**](https://www.freecodecamp.org/learn/relational-database/build-a-celestial-bodies-database-project/build-a-celestial-bodies-database) 
required project for the [**freeCodeCamp's Relational Databases Certification**](https://www.freecodecamp.org/learn/relational-database/) using PostgreSQL. <br />

## Contents
- Tables
    - Galaxy
    - Star
    - Planet
    - Moon
    - Constellation
- Project tasks

## Tables
The database can be rebuilt by entering `psql -U postgres < universe.sql` in a terminal where the .sql file is.\
Rebuilding the database using this file will result in the following tables: <br />

### Galaxy

|galaxy_id <sup>1</sup>|	name <sup>2</sup>|	seen_by_naked_eye <sup>3</sup>|	constellation_id <sup>4</sup>|	type <sup>5</sup>|
|:-:|:-------------:|:--:|:-:|:--------:|	
|1	|Milky Way	    |yes |9	 |spiral    |
|2	|Andromeda	    |yes |1	 |spiral    |
|3	|Centaurus A	  |yes |3	 |elliptical|
|4	|Eye of Sauron	|no	 |2	 |spiral    |
|5	|Fireworks	    |no	 |5	 |spiral    |
|6	|Butterfly	    |no	 |6	 |spiral    |

<sup>1</sup> serial, primary key, not null\
<sup>2</sup> varchar(30), unique, not null\
<sup>3</sup> boolean\
<sup>4</sup> int, foreign key REFERENCES constellation(constellation_id)\
<sup>5</sup> text

### Star
|star_id <sup>6</sup>	|name	<sup>7</sup>|galaxy_id	<sup>8</sup>|constellation_id	<sup>9</sup>|distance_earth_in_light_years <sup>10</sup>|
|:-:|:---------:|:-:|:-:|:---------:|		
|1	|Sun	      |1	|   |0,000016067|
|2	|Betelgeuse	|1	|7	|642,5      |
|3	|Antares	  |1	|8	|554,5      |
|4	|Alpheratz	|2	|1	|96,87      |
|5	|Spica	    |1	|6	|260,9      |
|6	|Mira	      |1	|4	|424        |

<sup>6</sup> serial, primary key, not null\
<sup>7</sup> varchar(30), unique, not null\
<sup>8</sup> int, foreign key REFERENCES galaxy(galaxy_id)\
<sup>9</sup> int, foreign key REFERENCES constellation(constellation_id)\
<sup>10</sup> num(4,1)

### Planet
|planet_id	<sup>11</sup>|name	<sup>12</sup>|star_id	<sup>13</sup>|moon_quantity	<sup>14</sup>|distance_from_Earth_in_million_km<sup>15</sup>|
|:-:|:-:|:-:|:-:|:-:|
|1	|Mercury	|1	|0	|77|
|2	|Venus	|1	|0	|61|
|3	|Earth	|1	|1||	
|4	|Mars	|1	|2	|54,6|
|5	|Jupiter	|1	|80	|588|
|6	|Saturn	|1	|145	|1200000|
|7	|Uranus	|1	|27	|2600000|
|8	|Neptune	|1	|14	|4300000|
|9	|Pluto	|1	|5	|4280000|
|10	|Ceres	|1	|0	|413|
|11	|Haumea	|1	|2	|7416|
|12	|Eris	|1	|1	|10125|

<sup>11</sup> serial, primary key, not null\
<sup>12</sup> varchar(30), unique, not null\
<sup>13</sup> int, foreign key REFERENCES star(star_id)\
<sup>14</sup> int\
<sup>15</sup> num

### Moon
|moon_id	<sup>16</sup>|name	<sup>17</sup>|planet_id<sup>18</sup>|	water	<sup>19</sup>|diameter_in_km<sup>20</sup>|		
|:-:|:-:|:-:|:-:|:-:|
|1	|Moon	|3	|no	|3.474,80|
|2	|Fobos	|4	|no	|22,533|
|3	|Deimos	|4	|no	|12,4|
|4	|Io	|5 |no		|3.643,20|
|5	|Europa	|5	|yes	|3.121,60|
|6	|Ganymede	|5	|yes	|5.268,20|
|7	|Callisto	|5	|yes	|4.820,60|
|8	|Dione	|6	|yes	|1.122,80|
|9	|Enceladus	|6	|yes	|504,20|
|10	|Epimetheus	|6	|no	|116,20|
|11	|Prometheus	|6	|no	|86,20|
|12	|Mimas	|6	|yes	|396,40|
|13	|Rhea	|6	|no	|1.527,60|
|14	|Thalassa	|8	|no	|82,00|
|15	|Despina	|8	|no	|150,00|
|16	|Galatea	|8	|no	|174,80|
|17	|Proteus	|8	|no	|420,00|
|18	|Unbriel	|7	|no	|1.169,40|
|19	|Titania	|7	|no	|1.576,80|
|20	|Oberon	|7	|no	|1.522,80|

<sup>16</sup> serial, primary key, not null\
<sup>17</sup> varchar(30), unique, not null\
<sup>18</sup> int, foreign key REFERENCES planet(planet_id)\
<sup>19</sup> boolean\
<sup>20</sup> num(5,1)

### Constellation
|constellation_id	<sup>21</sup>|name	<sup>22</sup>|stars_with_known_planets<sup>23</sup>|shape<sup>24</sup>|
|:-:|:-:|:-:|:-:|
|1	|Andromeda	|0|maiden with chains|
|2	|Canes Venatici	|4|hunting dog|
|3	|Centaurus	|11|centaur|
|4	|Cetus	|14|whale-like monster|
|5	|Cygnus	|97|swan|
|6	|Virgo	|29|maiden|
|7	|Orion	|10|hunter|
|8	|Scorpius	|13|scorpion|
|9	|Sagittarius	|32|centaur with bow and arrow|

<sup>21</sup> serial, primary key, not null\
<sup>22</sup> varchar(30), unique, not null\
<sup>23</sup> int\
<sup>24</sup> varchar(30)


## Project Tasks
The goal was to create a database in PostgreSQL that passed the following tests \(more details available on [**freeCodeCamp - Celestial Bodies Database**](https://www.freecodecamp.org/learn/relational-database/build-a-celestial-bodies-database-project/build-a-celestial-bodies-database)\):
- You should create a database named `universe`
- Be sure to connect to your database with `\c universe`. Then, you should add tables named `galaxy`, `star`, `planet`, and `moon`
- Each table should have a primary key
- Each primary key should automatically increment
- Each table should have a `name` column
- You should use the `INT` data type for at least two columns that are not a primary or foreign key
- You should use the `NUMERIC` data type at least once
- You should use the `TEXT` data type at least once
- You should use the `BOOLEAN` data type on at least two columns
- Each "star" should have a foreign key that references one of the rows in `galaxy`
- Each "planet" should have a foreign key that references one of the rows in `star`
- Each "moon" should have a foreign key that references one of the rows in `planet`
- Your database should have at least five tables
- Each table should have at least three rows
- The `galaxy` and `star` tables should each have at least six rows
- The `planet` table should have at least 12 rows
- The `moon` table should have at least 20 rows
- Each table should have at least three columns
- The `galaxy`, `star`, `planet`, and `moon` tables should each have at least five columns
- At least two columns per table should not accept `NULL` values
- At least one column from each table should be required to be `UNIQUE`
- All columns named `name` should be of type `VARCHAR`
- Each primary key column should follow the naming convention `table_name_id`. For example, the `moon` table should have a primary key column named `moon_id`
- Each foreign key column should have the same name as the column it is referencing
