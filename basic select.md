**Weather Observation Station 9**

Query the list of CITY names from STATION that do not start with vowels. Your result cannot contain duplicates.

Input Format

The STATION table is described as follows:

![image](https://user-images.githubusercontent.com/94289230/200173060-2a2cfe49-a576-4682-80ba-34d0969509f3.png)

where LAT_N is the northern latitude and LONG_W is the western longitude.

SOLUTION
```SQL
SELECT DISTINCT CITY
FROM STATION
WHERE CITY NOT LIKE 'A%' AND CITY NOT LIKE 'E%' AND CITY NOT LIKE 'I%' AND CITY NOT LIKE 'O%' AND CITY NOT LIKE 'U%';
```
**Higher Than 75 Marks**

Query the Name of any student in STUDENTS who scored higher than  Marks. Order your output by the last three characters of each name. If two or more students both have names ending in the same last three characters (i.e.: Bobby, Robby, etc.), secondary sort them by ascending ID.

Input Format

The STUDENTS table is described as follows:

![image](https://user-images.githubusercontent.com/94289230/200174633-b34ab390-9671-4e53-9eea-d8bcb0463f44.png)

```SQL
SELECT NAME
FROM STUDENTS 
WHERE MARKS > 75
ORDER BY RIGHT(NAME, 3), ID;
```
