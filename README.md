# Database Challenge - Support Engineer
The objective of this repository is to upload my Database Challenge for a Support Engineer position at Lexart labs.

## Intro
The challenge was to create a table called 'AverageLifeExpectancy' with the information from the 'World' database (https://dev.mysql.com/doc/index-other.html). The new table created should have the average life expectancy from three regions (South America, North America and Asia).

## Methodology
After downloading the 'World' database and importing it to use. I used the 'MySQL Workbench' tool, to analyze all the data and to create the table requested in the challenge.

First I found the 'Life Expectancy' and 'Continent' columns at the country table with the query: 
```sql
SELECT * FROM world.country;
```

And then create the following query: 
```sql
CREATE TABLE AverageLifeExpectancy AS
SELECT ROUND(AVG(LifeExpectancy)) AS LifeProm, Continent AS Region
FROM world.country
WHERE Continent IN ('South America', 'North America', 'Asia')
GROUP BY Continent
ORDER BY Continent DESC;
```
#### Explaing by parts:

+ Used ```SELECT``` for selecting 'LifeExpanctancy' and 'Continent' columns, renaming respectively to 'LifeProm' an 'Region'. I also needed to used an ```AVG()``` function inside a ```ROUND()``` function, to get the average value, with no decimal places of 'LifeExpanctancy':
     ```sql
    SELECT ROUND(AVG(LifeExpectancy)) AS LifeProm, Continent AS Region
    ```
+ Chose the table from world database:
     ```sql
    FROM world.country
    ```
+ Used ```WHERE``` clause to specifed the conditions that I needed on 'Continent' column:
     ```sql
    WHERE Continent IN ('South America', 'North America', 'Asia')
    ```
+ Used ```GROUP BY``` clause to group my rows for each 'Continent':
     ```sql
    GROUP BY Continent
    ```
+ Ordered the results to be descending with ```ORDER BY``` clause:
     ```sql
    GROUP BY Continent
    ```
+ To finish, after I checked the informations, I used ```CREATE TABLE``` arguments for create the new table with the correct data with the name of 'AverageLifeExpectancy':
     ```sql
    CREATE TABLE AverageLifeExpectancy AS
    ```
## Results Analysis
Of a total of 239 countries, 102 where inside ```WHERE``` clause of 3 specific continents and of those, 101 had a valid value (not null) for 'LifeExpanctancy' column.

The resulting table is:
| LifeProm |     Region    |
|----------|---------------|
|    71    | South America |
|    73    | North America |
|    67    |      Asia     |

## Conclusion
The continent with the highest life expectancy was North America with 74 of value, followed by South America with 73 of value and Asia with the lowest value of 67.



