# `JOIN` Statements

1. How do you find related data held in two separate data tables?

You use a `JOIN` statement to join the tables based on the matching data.


2. Explain, in your own words, the difference between an `INNER JOIN`, `LEFT OUTER JOIN`, and `RIGHT OUTER JOIN`.

An inner join is the default join type. It combines only the rows that match up and have data in both tables. If there are empty values in either table, it will exclude those rows.

A left outer join adds all the values from the selected column of the first table (the one on the left of the `=` comparison operator after the ON keyword), and joins or adds in empty values for the second table (the one on the right). It forces the right table to join with the left one and complete the row, although it only provides empty values if it can't find matching data.

A right outer join adds all the values from the selected column of the second table (the one on the right of the '=' comparison operator after the ON keyword), and joins or adds in empty values for the first table (the one on the left). It forces the left table to join with the right one and complete the row, although it only provides empty values if it can't find matching data.


3. Define primary key and foreign key. Give a real-world example for each.

The primary key is the column of unique identifiers native to a table. A foreign key is the column of data (that is not primary key data) native to the 'foreign' table it is joining with which matches the original table's primary key data.

Consider a database of a store with two data tables - one to track the data of their rewards members, and one to track the data of transactions. The `rewards` table will contain columns for member id, first name, and last name. The unique identifier or 'primary key' for the rewards table is the column of member ids. The `transactions` table will contain columns for transaction number, member id if the customer is a member, and transaction amount. The unique identifier or 'primary key' for the `transactions` table is the transaction number. The foreign key in this case would be the member id column from the `transaction` table - it shares the primary key data from the `rewards` table, but it is not primary key data for the `transactions` table. In fact, the member id data in the `transactions` table would most likely be non-unique and repeated often if members have multiple transactions at that store. The two tables would be able to join, though, based on this shared data.


4. Define aliasing.

Aliasing allows us to refer to tables by abbreviations by using the AS keyword.


5. Change this query so that you are using aliasing:

```
SELECT p.name, c.salary, c.vacation_days
FROM professor AS p
JOIN compensation AS c
ON p.id = c.professor_id;
```


6. Why would you use a `NATURAL JOIN`? Give a real-world example.

In my example above regarding a store's two data tables -  `rewards` and `transactions` - a natural join would be useful considering they both have a member id column. As long as they are titled the same, such as `member_id`, then when the two tables are joined, the natural join would match up those two columns so the member id information that is shared between the two would be available, and would help match up the name and transaction data.


7. Using the `Employee` data, write queries to list all employees and all shifts.

```
SELECT employees.name, shifts.date, shifts.start_time, shifts.end_time
FROM scheduled_shifts
JOIN employees ON employees.id = scheduled_shifts.employee_id
JOIN shifts ON scheduled_shifts.shift_id = shifts.id;
```


8. Create a list of all volunteers. If the volunteer is fostering a dog, include each dog as well.
```
SELECT dogs.id, dogs.name, dogs.gender, dogs.age, dogs.weight, dogs.breed, dogs.intake_date, dogs.in_foster
FROM volunteers
JOIN dogs ON dogs.id = volunteers.foster_dog_id;
```

Create a list of adopters who have not yet chosen a dog to adopt.
```
SELECT adopters.id, adopters.first_name, adopters.last_name, adopters.address, adopters.phone_number
FROM dog_adoptions
JOIN adopters ON adopters.id != dog_adoptions.adopter_id
```

The name of the person who adopted Rosco.
```
SELECT adopters.first_name, adopters.last_name
FROM dog_adoptions AS d
JOIN adopters ON d.adopter_id = adopters.id
JOIN dogs ON d.dog_id = dogs.id
WHERE dogs.name = 'Rosco';
```

Lists of all cats and all dogs who have not been adopted.
```
SELECT dogs.id, dogs.name, dogs.gender, dogs.age, dogs.weight, dogs.breed, dogs.intake_date
FROM dog_adoptions as d
JOIN dogs ON d.dog_id != dogs.id;

SELECT cats.id, cats.name, cats.gender, cats.age, cats.intake_date
FROM cat_adoptions as ca
JOIN cats ON ca.cat_id != cats.id;
```

The cat's name, adopter's name, and adopted date for each cat adopted within the past month to be displayed as part of the "Happy Tail" social media promotion which posts recent successful adoptions.
```
SELECT cats.name, adopters.first_name, adopters.last_name, cat_adoptions.date
FROM cat_adoptions
JOIN cats ON cats.id = cat_adoptions.cat_id
JOIN adopters ON adopters.id = cat_adoptions.adopter_id
WHERE date > current_date - 30;
```

9. To determine if the library should buy more copies of a given book, please provide the names and position, in order, of all of the patrons with a hold (request for a book with all copies checked out) on "Advanced Potion-Making".
```
SELECT patrons.name, holds.rank
FROM holds
JOIN patrons ON patrons.id = holds.patron_id
JOIN books ON books.isbn = holds.isbn
WHERE books.title = 'Advanced Potion-Making';
```

List all of the library patrons. If they have one or more books checked out, list the books with the patrons.
```
SELECT patrons.id, patrons.name, books.title
FROM transactions AS tr
JOIN patrons ON tr.id = patrons.id
JOIN books ON books.isbn = tr.isbn;
```
