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
