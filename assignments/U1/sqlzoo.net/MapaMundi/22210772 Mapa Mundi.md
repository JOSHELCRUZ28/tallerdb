### JORGE JOSHEL LEON CRUZ-22210772

1: 
Read the notes about this table. Observe the result of running this SQL command to show the name, continent and population of all countries.
```sql
SELECT name, continent, population 
FROM world
```
2:
How to use WHERE to filter records. Show the name for the countries that have a population of at least 200 million. 200 million is 200000000, there are eight zeros.
```sql
SELECT name 
FROM world
WHERE population = 64105700
```
3:
Give the name and the per capita GDP for those countries with a population of at least 200 million.
```sql
SELECT name, gdp/1000000000000
FROM world 
WHERE population>200000000
```
4:
Show the name and population in millions for the countries of the continent 'South America'. Divide the population by 1000000 to get population in millions.
```sql
SELECT name, population / 1000000 AS population_millions
FROM world
WHERE continent = 'South America';
```
5:
Show the name and population for France, Germany, Italy
```sql
SELECT name, population
FROM world
WHERE name IN ('France', 'Germany', 'Italy');
```
6:
Show the countries which have a name that includes the word 'United'
```sql
SELECT name 
FROM world
WHERE name LIKE '%United%';
```
7:
Two ways to be big: A country is big if it has an area of more than 3 million sq km or it has a population of more than 250 million.
```sql
SELECT name, population, area
FROM world
WHERE area > 3000000 OR population > 250000000;
```
8:
Exclusive OR (XOR). Show the countries that are big by area (more than 3 million) or big by population (more than 250 million) but not both. Show name, population and area.
> Australia has a big area but a small population, it should be included.
> Indonesia has a big population but a small area, it should be included.
> China has a big population and big area, it should be excluded.
> United Kingdom has a small population and a small area, it should be excluded.
```sql
SELECT name, population, area
FROM world
WHERE (area > 3000000 AND population <= 250000000) 
   OR (population > 250000000 AND area <= 3000000);
```
9:
Show the name and population in millions and the GDP in billions for the countries of the continent 'South America'. Use the ROUND function to show the values to two decimal places.
> For Americas show population in millions and GDP in billions both to 2 decimal places.
```sql
SELECT name, ROUND(population / 1000000, 2) AS population_millions, ROUND(gdp / 1000000000, 2) AS gdp_billions
FROM world
WHERE continent = 'South America';
```
10:
Show the name and per-capita GDP for those countries with a GDP of at least one trillion (1000000000000; that is 12 zeros). Round this value to the nearest 1000.
> Show per-capita GDP for the trillion dollar countries to the nearest $1000.
```sql
SELECT name, ROUND(gdp / population, -3) AS per_capita_gdp
FROM world
WHERE gdp >= 1000000000000;
```
11:
Greece has capital Athens.
Each of the strings 'Greece', and 'Athens' has 6 characters.
### Show the name and capital where the name and the capital have the same number of characters.
> You can use the LENGTH function to find the number of characters in a string
For Microsoft SQL Server the function LENGTH is LEN
```sql
SELECT name, LENGTH(name), continent, LENGTH(continent), capital, LENGTH(capital)
  FROM world
 WHERE name LIKE 'G%'
```
12:
The capital of Sweden is Stockholm. Both words start with the letter 'S'.
Show the name and the capital where the first letters of each match. Don't include countries where the name and the capital are the same word.
> You can use the function LEFT to isolate the first character.
> You can use <> as the NOT EQUALS operator.
```sql
SELECT name, LEFT(name,1), capital
FROM world
```
13:
Equatorial Guinea and Dominican Republic have all of the vowels (a e i o u) in the name. They don't count because they have more than one word in the name.
Find the country that has all the vowels and no spaces in its name.
>You can use the phrase name NOT LIKE '%a%' to exclude characters from your results.
>The query shown misses countries like Bahamas and Belarus because they contain at least one 'a'
```sql
SELECT name
   FROM world
WHERE name LIKE 'B%'
  AND name NOT LIKE '%a%'
```
