# Operators in `SELECT` Statements

1. Write out a generic `SELECT` statement.

My `SELECT` statement asks for the publishing year of the book 'Fox in Socks' from the table `books`.
```
SELECT year
FROM books
WHERE title='Fox in Socks';
```


2. Create a fun way to remember the order of operations in a `SELECT` statement.

A mnemonic way to remember the order of operations could be the question "So Find What?" This works well because a `SELECT` statement is used to find certain information from a table, and it reflects the **S**, **F**, **W** (SELECT, FIND, WHERE) order.


3. Given the `dogs` table, write the following queries...
```
SELECT name, age, gender
FROM dogs
WHERE breed LIKE 'labrador%';

SELECT id
FROM dogs
WHERE age < 1;

SELECT name, age
FROM dogs
WHERE gender='F' AND weight > 35;

SELECT *
FROM dogs
WHERE breed <> '%shepherd';

SELECT id, age, weight, breed
FROM dogs
WHERE weight > 60 OR breed='great dane';
```

4. Given the `cats` table, what records are returned from these queries?

`SELECT name, adoption_date FROM cats;`
Will return the name and adoption_data column data from the `cats` table for all entries.

`SELECT name, age FROM cats;`
Will return the name and age column data from the `cats` table for all entries.


5. From the `cats` table, write the following queries...

```
SELECT *
FROM cats;

SELECT name, gender
FROM cats
WHERE age=7;

SELECT name
FROM cats;
```


6. List each comparison operator and explain when you would use it. Include a real world example for each.

- `=` : used to target based on a strict value (meaning in the case of strings, capitalization must be an exact match), like asking for a patient with a particular name (name='Susan Smith')
- `>` : used to return values greater than a given value, like asking for the data of patients that are more than 50 years old 
- `<` : used to return values lesser than a given value, like asking for the data of patients that are less than 30 years old
- `>=` : used to return values greater or equal to a given value, like asking for names of dogs that weigh more or at 50lbs
- `<=` : used to return values lesser or equal to a given value, like asking for names of cats that weight less than or at 30lbs
- `<>` : used to exclude a value, like not including dogs with the breed equal to great dane
- `!=` : used to exclude a value, like not including books published in the year 1980
- `LIKE` : used to find partial matches, like all authors with the last name 'Martin'


7. From the `cats` table, what data is returned from these queries?

`SELECT name FROM cats WHERE gender = ‘F’;`
Will return the name value for all female cats.

`SELECT name FROM cats WHERE age <> 3;`
Will return the name value for all cats that are not 3 years old.

`SELECT ID FROM cats WHERE name != ‘Mushi’ AND gender = ‘M’;`
Will return the id value for all male cats that are not named 'Mushi'.
