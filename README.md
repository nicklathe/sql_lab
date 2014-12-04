#SQL Lab


##Getting Started

To get started we'll need to import the booktown.sql file.

1. open terminal
2. use the command `psql -f booktown.sql`
3. type `sql` to open your psql console
4. type \list to ensure the booktown database was successfully completed

##Instructions
Provide the follow sql statements below each question.

##Order
1. Find all subjects sorted by subject

	SELECT * FROM subjects ORDER BY subjects;

2. Find all subjects sorted by location

	SELECT * FROM subjects ORDER BY location;



##Where
1. Find the book "Little Women"

	SELECT * FROM books WHERE title = 'Little Women';

2. Find all books containing the word "Python"

	SELECT * FROM books WHERE title LIKE '%Python%';

3. Find all subjects with the location "Main St" sort them by subject

	SELECT * FROM subjects WHERE location LIKE 'Main St' ORDER BY subject ASC;

##Joins

1. Find all books about Computers list ONLY book title

	SELECT books.title FROM books JOIN subjects ON subjects.id = books.subject_id WHERE subjects.id = 4;

* Find all books and display ONLY
	* Book title
	* Author's first name
	* Author's last name
	* Book subject

	SELECT books.title, authors.first_name, authors.last_name, subject FROM authors JOIN books ON authors.id = books.author_id JOIN subjects ON subjects.id = books.subject_id;

* Find all books that are listed in the stock table 
	* Sort them by retail price (most expensive first
	* Display ONLY: title and price
	
	SELECT books.title, stock.retail FROM editions JOIN stock ON editions.isbn = stock.isbn JOIN books ON editions.book_id = books.id ORDER BY retail DESC;

* Find the book "Dune" and display ONLY
	* Book title
	* ISBN number
	* Publisher name
	* Retail price

	SELECT books.title, editions.isbn, publishers.name, stock.retail FROM editions JOIN stock ON editions.isbn = stock.isbn JOIN books ON editions.book_id = books.id JOIN publishers ON editions.publisher_id = publishers.id WHERE title LIKE 'Dune';

* Find all shipments sorted by ship date display ONLY:
	* Customer first name
	* Customer last name
	* ship date
	* book title

	SELECT customers.last_name, customers.first_name, shipments.ship_date, books.title FROM books JOIN editions ON books.id = editions.book_id JOIN shipments ON editions.isbn = shipments.isbn JOIN customers ON shipments.customer_id = customers.id;



* Find all books that have either a 2nd or 3rd edition associated to it display ONLY:
	* Book title
	* Book Author
	* Edition Number

	SELECT books.title, authors.first_name, authors.last_name, editions.edition FROM books JOIN editions ON books.id = editions.book_id JOIN authors ON authors.id = books.author_id WHERE editions.edition IN (2,3); 


