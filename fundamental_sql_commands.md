Fundamental SQL Commands

1. List the commands for adding, updating, and deleting data.

- Adding: `INSERT INTO`
- Updating values: `UPDATE`
- Deleting values: `DELETE`
- `ALTER` is also used to update a table, and `DROP` is used to delete a table.


2. Explain the structure for each type of command.

- Adding
When adding a data value, the proper syntax is:
`INSERT INTO <table-name> VALUES (<col1-value>, <col2-value>, <col3-value>);`
Initiate the command with the `INSERT INTO` keyword. Declare what table you are targeting using the table name. Use the keyword `VALUES` to indicate that you are adding values to the table. In parentheses, include the new values, separated by commas. They must be provided in the same order as the columns in the table for two reasons. First, because the columns are restricted by data type, so you will get an error if it looks like you're string to add a string to an integer column. Second, because you could end up swapping values of the same data type into the incorrect columns.

- Updating
When updating a data value, the proper syntax is:
`UPDATE <table-name> SET <col-name>=<new-value> WHERE <identify-row>;`
Initiate the command with the `UPDATE` keyword. Declare what table you are targeting using the table name. Use the `SET` keyword to provide the updated value and identify which column it should be placed at. Use the `WHERE` keyword to identify which row(s) the updated value will be placed at, such as the row with an id of 17789. Multiple `SET` and `WHERE` clauses can be provided using the keyword `AND`.

- Deleting
When deleting a data value, the proper syntax is:
`DELETE FROM <table-name> WHERE <identify-row>;`
Initiate the command with the `DELETE` keyword. Declare what table you are targeting using the `FROM` keyword + the table name. Use the `WHERE` keyword to identify which row(s) you want to delete. It is best to provide multiple criteria in this clause, or at least to include a unique value as the identifier. This is important in order to ensure you are targeting the correct data for deletion as this is irreversible.
Side note: The syntax does not seem include the ability to delete a single value, but instead an entire row (data unit) will be deleted with this method. I would assume it is to ensure that there are no empty value spots in a row, and it would be best to update that value to a default value, such as 'None' or '0'.


3. What are some of the data types that can be used in tables? Give a real-world example of each data type.

Imagine a pet groomers has a data table containing pet names, next appointment date, appointment intervals, and whether or not they are up to date on their vaccinations. The table would contain the following data types, which are possible to use in tables:
- text: pet names would be saved as a `text` data type, such as `'Daisy'`
- date: next appointment date would be saved as a `date` data type, such as `1/15/2019`
- interval: next appointment dates would be chosen based on the info provided using the `interval` data type, such as `3 weeks`
- boolean: vaccination information would be saved as a `boolean` data type, such as `TRUE`


4. Table to hold a list of people invited to a wedding dinner.

Needs:
- first and last names (text)
- whether they RSVP'd (boolean)
- the number of guests they are bringing (integer)
- the number of meals (numeric(3, 1))

Create the table:
```
CREATE TABLE wedding(
  first-name text,
  last-name text,
  rsvp boolean,
  guests integer,
  meals numeric(3, 1)
  );
```

Add a column to track thank you cards:
```
ALTER TABLE wedding ADD COLUMN thank-you boolean SET DEFAULT FALSE;
```

Remove the column storing number of meals:
```
ALTER TABLE wedding DROP COLUMN thank-you;
```

Add a column for table number (integer data type):
```
ALTER TABLE wedding ADD COLUMN table-number integer SET DEFAULT 0;
```

Delete the column for table numbers:
```
ALTER TABLE wedding DROP COLUMN table-number;
```


5. Write a command to create a new table to hold the books in a library.

Needs:
- ISBN
- title
- author
- genre
- publishing date
- number of copies
- available copies

Create table:
```
CREATE TABLE library(
  isbn integer,
  title text,
  author text,
  genre text,
  publishing-date date,
  total-copies integer,
  available-copies integer
  );
```

Add 3 books to the table:
```
INSERT INTO library(isbn, title, author, genre, publishing-date, total-copies, available-copies)
  VALUES
  (9780765326379, 'Oathbringer', 'Brandon Sanderson', 'Fantasy', 11/14/2017, 2, 1),
  (9783896676351, 'Calypso', 'David Sedaris', 'Nonfiction', 05/29/2018, 4, 2),
  (9780385351393, 'The Circle', 'Dave Eggers', 'Science Fiction', 10/03/2013, 5, 3);
```

A book got checked out - change available copies:
```
UPDATE library SET available-copies=2 WHERE isbn=9780385351393;
```

Remove banned book from the table:
```
DELETE FROM library WHERE isbn=9780765326379 AND title='Oathbringer';
```


6. Write a command to make a new table to hold spacecrafts.

Needs:
- id (integer)
- name (text)
- year launched (integer)
- country of origin (text)
- mission description (text)
- orbiting body (text)
- currently operating (boolean)
- approx. miles from Earth (float)

Create table:
```
CREATE TABLE spacecrafts(
  id integer,
  name text,
  launch-year integer,
  origin-country text,
  mission text,
  orbiting text,
  operating boolean,
  distance float
  );
```

Add 3 non-earth-orbiting satellites to the table:
```
INSERT INTO spacecrafts(id, name, launch-year, origin-country, mission, orbiting, operating, distance)
VALUES
(134, 'Delorean', 2063, 'United States', 'Recording the number of rings left on Saturn', 'Saturn', TRUE, 120000000),
(135, 'Millennium Falcon', 2065, 'Japan', 'Travelling to planet Kessel in under 14 parsecs', 'Kessel', TRUE, 13500000000.6),
(136, 'Heart of Gold', 2069, 'Australia', 'To discover the meaning of the universe', 'Planet 42', TRUE, 85000000000.5);
```

Remove one satellite from table:
```
DELETE FROM spacecrafts WHERE id<=134 AND launch-year<2065;
```

Edit satellite to be no longer operating:
```
UPDATE spacecrafts SET operating=FALSE WHERE id=135;
```


7. Write a command to create a new table to hold the emails in your inbox.

Needs:
- id of email chain (integer)
- id (float)
- subject line (text)
- sender (text)
- additional recipients (text)
- body of email (text)
- timestamp (timestamp
- read or unread (boolean)

Create table:
```
CREATE TABLE emails(
  chain-id integer,
  id float,
  subject text,
  sender text,
  recipients text,
  body text,
  timestamp timestamp,
  read boolean
  );
```

Add three new emails to the inbox:
```
INSERT INTO emails
VALUES
(100, 100.01, 'Christmas', 'maryclaus@northpole.com', 'imsanta@northpole.com', 'Hello, Santa would like sugar cookies and chocolate milk this year. Thank you!', '2018-06-22 18:09:25-07', FALSE),
(101, 101.01, 'Friday Brunch', 'myfriend@gmail.com', 'None', 'Are you free for brunch this Friday?', '2019-01-02 07:10:25-07', FALSE),
(100, 100.02, 'RE: Christmas', 'imsanta@northpole.com', 'maryclaus@northpole.com', 'Also, red and green sprinkles, please.', '2018-12-22 19:10:25-07', FALSE);
```

Remove one email from the inbox table (I decided to delete 2):
```
DELETE FROM emails WHERE chain-id=100;
```

Mark an email as read...then unread after the crash:
```
UPDATE emails SET read=TRUE WHERE id=101.01;
```
CRASH!
```
UPDATE emails SET read=FALSE WHERE id=101.01;
```
