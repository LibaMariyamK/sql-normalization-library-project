# SQL Part Project: Split the Flat Table

A library keeps all its records in **one big table**. Your job is to find out what is wrong with it and split it into proper related tables.

## What you will practice

`SHOW`, `CREATE`, `INSERT`, `DROP`, `SELECT`, choosing proper data types, constraints (primary key, foreign key, NOT NULL, UNIQUE and so on), and the basics of normalization.

## Files in this repo

| File | What it is |
|------|------------|
| `flat_table.sql` | Script that creates the flat table `library_flat` with data. Do not edit it. |
| `README.md` | These instructions. |

## Steps

### 1. Fork this repository
Click **Fork** (top right on GitHub) to get your own copy. All your work goes into **your fork**.

### 2. Create the flat table
Open `flat_table.sql` in MySQL Workbench and run it. Then look at the data:

```sql
SELECT * FROM library_flat;
```

### 3. Find the anomalies (problems)
Study the table before you change anything. Think about:

- What information is **repeated** again and again?
- If a member changes their phone number, **how many rows** must be edited?
- Can you store a new book that nobody has borrowed yet?
- What happens to a book's details if the only row that mentions it is deleted?
- Is every cell holding **one single value**? Look carefully at every column.

Write 3 to 5 anomalies you found in a file named **`anomalies.md`**. Be specific, using real values from the table. Example of the style:

> If Rahul changes his phone number, 3 rows (issue_id 3, 4, 14) must be updated. If one is missed, the data becomes inconsistent.

### 4. Split it into related tables
Design your own set of tables. You decide how many tables you need and what goes in each one.

- Pick proper **data types** for every column.
- Add the right **constraints**: primary keys, foreign keys, NOT NULL, UNIQUE and so on.
- Related tables must be linked with **foreign keys**.
- Create the tables in a **new database** (do not change `library_flat_db`), and use `SHOW` to display your database and tables.
- Be ready to explain why you split the tables the way you did.
### 5. Insert the data
Insert all the information from the flat table into your new tables, **without losing anything**. Remember that parent tables must be filled before child tables.

Then show the contents of every table with `SELECT`.

### 6. Generate the ER diagram
In MySQL Workbench:

1. Go to **Database → Reverse Engineer...**
2. Choose your connection and select **your new database** (not the flat one).
3. Continue through the wizard and click Execute.
4. Arrange the boxes neatly so the relationship lines are readable.
5. Export it with **File → Export → Export as PNG**.

Your diagram must show **lines between your tables**. If lines are missing, check that you declared the foreign keys.

### 7. Upload to your fork
Add these three files to your fork:

| File | Contents |
|------|----------|
| `solution.sql` | Your full script: create database and tables, insert data, and the `SHOW` and `SELECT` statements. It must run from top to bottom without errors. |
| `anomalies.md` | The anomalies you found (step 3). |
| `er_diagram.png` | The ER diagram of your **split** design (step 6). |
