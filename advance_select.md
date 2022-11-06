**1. Type of Triangle**

Write a query identifying the type of each record in the TRIANGLES table using its three side lengths. Output one of the following statements for each record in the table:

Equilateral: It's a triangle with  sides of equal length.
Isosceles: It's a triangle with  sides of equal length.
Scalene: It's a triangle with  sides of differing lengths.
Not A Triangle: The given values of A, B, and C don't form a triangle.

Input Format

The TRIANGLES table is described as follows:

![image](https://user-images.githubusercontent.com/94289230/200175386-5a647e28-5eed-4d24-9d96-8b710827937f.png)

Sample Input

![image](https://user-images.githubusercontent.com/94289230/200175419-52cc3567-1176-41df-abad-b643fb0e2566.png)

Explanation

![image](https://user-images.githubusercontent.com/94289230/200175933-452881c0-4685-4669-a75b-42838831e9bf.png)

MISTAKE
```SQL
SELECT CASE 
    WHEN A=B=C THEN 'Equilateral',  --DON'T NEED THE COMMA
    WHEN A=B!=C THEN 'Isosceles' ,
    WHEN A!=B!=C THEN 'Scalene' ,
    ELSE 'Not A Triangle'
    END
FROM TRIANGLES;
```

SOLUTION
```SQL
SELECT CASE 
    WHEN A=B AND B=C THEN 'Equilateral'
    WHEN (A=B OR B=C OR A=C) AND A+B>C THEN 'Isosceles' 
    WHEN A!=B AND B!=C AND A!=C AND A+B>C  THEN 'Scalene' 
    ELSE 'Not A Triangle'
    END
FROM TRIANGLES;
```
OR

```SQL
SELECT CASE
WHEN A + B <= C OR A + C <= B OR B + C <= A THEN 'Not A Triangle'
WHEN A = B AND B = C THEN 'Equilateral'
WHEN A = B OR B = C OR A = C THEN 'Isosceles'
ELSE 'Scalene'
END
FROM TRIANGLES;
```

**2. The PADS**

![image](https://user-images.githubusercontent.com/94289230/200178658-a800ca47-266a-471f-811c-94994dc9950b.png)

![image](https://user-images.githubusercontent.com/94289230/200178671-94974607-a926-450a-947d-962320818d82.png)

![image](https://user-images.githubusercontent.com/94289230/200178693-1ec4e237-4eb5-4afe-a4c3-b138440baa12.png)

![image](https://user-images.githubusercontent.com/94289230/200178709-98c587da-6a9d-442c-abaf-4058824e7860.png)

MISTAKE (AT 2ND QUERY)
```SQL
WITH NEW_OCCUPATIONS AS(
    SELECT 
        NAME,
        LEFT(OCCUPATION,1) AS INITIAL
    FROM OCCUPATIONS
    )

SELECT CONCAT(NAME,'(', INITIAL,')') AS NEW_NAME
FROM NEW_OCCUPATIONS
ORDER BY NEW_NAME;

--cannot use alias in CONCAT
SELECT CONCAT('There are a total of',' ', COUNT(OCCUPATION) AS OCCUPATION_COUNT,' ',LOWER(OCCUPATION), 's.' ) --CONCAT cannot put ALIAS
FROM OCCUPATIONS
GROUP BY OCCUPATION
ORDER BY OCCUPATION_COUNT, OCCUPATION;
```

SOLUTION
```SQL
WITH NEW_OCCUPATIONS AS(
    SELECT 
        NAME,
        LEFT(OCCUPATION,1) AS INITIAL
    FROM OCCUPATIONS
    )

SELECT CONCAT(NAME,'(', INITIAL,')') AS NEW_NAME
FROM NEW_OCCUPATIONS
ORDER BY NEW_NAME;

SELECT CONCAT('There are a total of',' ', COUNT(OCCUPATION),' ',LOWER(OCCUPATION), 's.' ) AS PROFESSION
FROM OCCUPATIONS
GROUP BY OCCUPATION
ORDER BY PROFESSION;
```

SOLUTION ONLINE
```SQL
SELECT (name || '(' || SUBSTR(occupation,1,1) || ')') FROM occupations ORDER BY name;
SELECT ('There are a total of ' || COUNT(occupation) || ' ' || LOWER(occupation) || 's' || '.') FROM occupations GROUP BY occupation ORDER BY COUNT(occupation), occupation ASC;
```
