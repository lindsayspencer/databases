# Intro to Databases

1. What data types do each of these values represent?

1. "A Clockwork Orange" = string
2. 42 = integer
3. 09/02/1945 = date
4. 98.7 = float
5. $15.99 = smallmoney


2. Explain when a database would be used. Explain when a text file would be used.

A database would be used when there are multiple data pieces that need to be accessed and updated from within an application. A text file would be used if the data it contains just needs to be read and not updated.


3. Describe one difference between SQL and other programming languages?

Most other programming languages are procedural, meaning they tell a computer **how** to do something in addition to **what** to do. SQL is a declarative language, meaning that it will say what needs to be done without having to describe how to perform the procedure.


4. In your own words, explain how the pieces of a database system fit together at a high level.

The database pieces come together as a table, with columns containing data pieces with shared meaning and rows containing the entire data unit (such as all data for a single user).


5. Explain the meaning of table, row, column, and value.

1. table = the structure that contains all the data values organized into rows and columns (the FROM SQL clause)
2. row = contains all the data values for a single unit or object (the WHERE clause)
3. column = contains data values from different units that have shared meaning
4. value = a single piece of data in a row and column that is one part of the entire unit (such as the name from a unit of user data)


6. List three data types that can be used in a table.

1. string = 'Lindsay'
2. integer = 9
3. float = 9.7


7. Given this `payments` table, provide an English description of the following queries and include their results.

> What are all the values from the date and amount columns in the payments table?

> What are the amount values in the payments table from all items with amounts greater than 500?

> What are all the values in the payments table from the row where the payee is Mega Foods?


8. Given this `users` table, write SQL queries using the following criteria and include the output:

- The email and sign-up date for the user named DeAndre Data

```
SELECT email, signup
FROM users
WHERE name = 'DeAndre Data';
```

- The user ID for the user with email 'aleesia.algorithm@uw.edu'

```
SELECT userid
FROM users
WHERE email = 'aleesia.algorithm@uw.edu';
```

- All the columns for the user ID equal to 4

```
SELECT *
FROM users
WHERE userid = 4;
```
