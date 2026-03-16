![logo_ironhack_blue 7](https://user-images.githubusercontent.com/23629340/40541063-a07a0a8a-601a-11e8-91b5-2f13e4e6b441.png)

# Answers

SELECT * FROM technologies;

CREATE DATABASE library;

CREATE TABLE authors (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    nationality VARCHAR(50),
    birth_year DATE
);

CREATE TABLE publishers (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    location VARCHAR(100),
    founded_year INT
);

CREATE TABLE books (
    id SERIAL PRIMARY KEY,
    title VARCHAR(255) NOT NULL,
    author_id INT REFERENCES authors(id),
    publisher_id INT REFERENCES publishers(id),
    publish_date DATE
);

-- Insert authors
INSERT INTO authors (name, nationality, birth_year) VALUES
('J.K. Rowling', 'British', '1965-07-31'),
('George Orwell', 'British', '1903-06-25'),
('Mark Twain', 'American', '1835-11-30'),
('Agatha Christie', 'British', '1890-09-15'),
('Stephen King', 'American', '1947-09-21'),
('Charles Dickens', 'British', '1812-02-07'),
('Leo Tolstoy', 'Russian', '1828-09-09'),
('Virginia Woolf', 'British', '1882-01-25'),
('F. Scott Fitzgerald', 'American', '1896-09-24'),
('Harper Lee', 'American', '1926-04-28');

-- Insert publishers
INSERT INTO publishers (name, location, founded_year) VALUES
('Bloomsbury', 'London', 1986),
('Secker & Warburg', 'London', 1935),
('Chatto & Windus', 'London', 1855),
('Penguin Books', 'London', 1935),
('HarperCollins', 'New York', 1989),
('Simon & Schuster', 'New York', 1924),
('Random House', 'New York', 1927),
('Macmillan Publishers', 'London', 1843),
('Scholastic Inc.', 'New York', 1920),
('Hachette Book Group', 'New York', 2006);

-- Insert books
INSERT INTO books (title, author_id, publisher_id, publish_date) VALUES
('Harry Potter and the Chamber of Secrets', 1, 1, '1998-07-02'),
('Harry Potter and the Goblet of Fire', 1, 1, '2000-07-08'),
('1984', 2, 2, '1949-06-08'),
('Animal Farm', 2, 2, '1945-08-17'),
('Adventures of Huckleberry Finn', 3, 3, '1884-12-10'),
('The Adventures of Tom Sawyer', 3, 3, '1876-06-09'),
('Murder on the Orient Express', 4, 4, '1934-01-01'),
('Oliver Twist', 6, 6, '1837-02-01'),
('To Kill a Mockingbird', 10, 8, '1960-07-11'),
('The Mysterious Manuscript', NULL, NULL, '2019-11-05'),
('Echoes in the Void', NULL, NULL, '2020-07-13');

## Iteration 2 - Joins

1. Using an **INNER JOIN**, list all books (left table) that have an assigned author (right table). The result should include only books with assigned authors.

```sql
-- Your Query Goes Here
```
select * from books inner join authors on books.author_id = authors.id

<br>

2. Using a **LEFT JOIN**, list all authors (left table) and their corresponding books on the (right table). The result should include all authors, including those who don't have any books assigned.

```sql
-- Your Query Goes Here
```
select * from authors left join books on books.author_id = authors.id

<br>

3. Using a **RIGHT JOIN**, list all books (right table) and their corresponding authors on the (left table). The result should include books without assigned authors.

```sql
-- Your Query Goes Here
```
select * from authors right join books on books.author_id = authors.id

<br>

4. Using a **FULL JOIN**, list all records from the `books` and `authors` tables. The result should include all details from both tables, even if there are no match.

```sql
-- Your Query Goes Here
```
select * from authors full join books on books.author_id = authors.id

<br>

## BONUS: Iteration 3 - Joins (continued)

1. Using an **INNER JOIN**, list all books (left table) and their corresponding publishers on the (right table). The result should include the book's title, publisher's name, and location.

```sql
-- Your Query Goes Here
```
select books.title, publishers.name, publishers.location from books inner join publishers on books.publisher_id = publishers.id

<br>

2. Using a **LEFT JOIN**, list all publishers (left table) and any books they have published on the (right table). The result should include all publishers, including those who haven't published any books.

```sql
-- Your Query Goes Here
```
select * from publishers left join books on books.publisher_id = publishers.id

<br>

3. Using a **RIGHT JOIN**, list all books (right table) and their corresponding publishers on the (left table). The result should include all books, even those without a linked publisher.

```sql
-- Your Query Goes Here
```
select * from publishers right join books on books.publisher_id = publishers.id

<br>

4. Using a **FULL JOIN**, list all records from the `authors`, `books`, and `publishers` tables. The result should include all records from the three tables, even if there are no matches between them.

```sql
-- Your Query Goes Here
```
SELECT * FROM authors a
FULL JOIN books b
    ON a.id = b.author_id
FULL JOIN publishers p
    ON b.publisher_id = p.id;

<br>
