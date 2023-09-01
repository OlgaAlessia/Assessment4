### Conceptual Exercise

Answer the following questions below:

- What is PostgreSQL? 

It is a open-source relational database management system (RDBMS) that uses SQL for querying and managing data.

- What is the difference between SQL and PostgreSQL?

SQL (Structured Query Language) is a programming language used to manage and manipulate relational databases. PostgreSQL is a powerful, open-source RDBMS that uses SQL as its query language.In terms of syntax, PostgreSQL is largely compatible with standard SQL, but it also includes additional features and functionality beyond what is available in standard SQL. Some of these features include support for advanced data types such as arrays and JSON, as well as support for full-text search and advanced indexing. One advantage of PostgreSQL over SQL is its ability to handle larger and more complex databases. PostgreSQL is known for its scalability and reliability, making it a good choice for businesses and organizations with large data sets or high-traffic websites. Another advantage of PostgreSQL is its open-source nature, which allows for a large and active community of developers who contribute to its development and maintenance. This can lead to more frequent updates and bug fixes, as well as a wider range of plugins and extensions to choose from.


- In `psql`, how do you connect to a database?

To connect to a database write ``` \c "db_name" ``` and it will appear the message: "You are now connect to database 'db_name' ".

- What is the difference between `HAVING` and `WHERE`?

The WHERE clause is used to filter the records from the tables or from the join tables and only those records that satisfying the condition in the clause, will be extract.
The HAVING clause is used to filter the record from only the condition in the "having" clause.

- What is the difference between an `INNER` and `OUTER` join?

INNER JOIN combines data from two tables based on the join condition and returns only the rows that match the condition from both tables

![img_innerjoin](https://intellipaat.com/mediaFiles/2019/04/A-Brief-Introduction-to-Inner-Join.png)


OUTER JOIN is when you trying to find rows in one table with no match in the other table.
There are 3 OUTER JOIN ( LEFT JOIN, RIGHT JOIN, FULL JOIN)


- What is the difference between a `LEFT OUTER` and `RIGHT OUTER` join?
LEFT OUTER JOIN returns all the rows from the left table and matching rows from the right table. 

![img_leftouterjoin](https://intellipaat.com/mediaFiles/2019/04/A-Brief-Introduction-to-Left-Join.png)

RIGHT OUTER JOIN returns all the rows from the right table and matching rows from the left table.

![img_rightouterjoin](https://intellipaat.com/mediaFiles/2019/04/A-Brief-Introduction-to-Right-Join.png)

- What is an ORM? What do they do?
One of the challenges of using object-oriented programming (OOP) languages and databases is the complexity of aligning the programming code with database structures. Object-relational mapping (ORM) is a technique that creates a layer between the language and the database, helping programmers work with data without the OOP paradigm.

- What are some differences between making HTTP requests using AJAX 
  and from the server side using a library like `requests`?

AJAX and HTTP requests are both methods for sending and receiving data on the web, but they operate in slightly different ways. 
An HTTP request is a standard protocol used for sending and receiving data on the web. It is the foundation of the web and allows for the transfer of information between a client (typically a web browser) and a server. HTTP requests can be made using a variety of methods, such as GET, POST, PUT, and DELETE, and the data is typically sent in the form of text or XML. 
AJAX, on the other hand, is a technique for creating fast and dynamic web pages. It allows for the creation of web pages that can update their content without the need for a full page reload. AJAX requests are made using JavaScript and the XMLHttpRequest object, and they are typically used to send and receive data in a more efficient and interactive way. In summary, an HTTP request is the foundation of web communication, while AJAX is a technique for creating more dynamic and interactive web pages.


- What is CSRF? What is the purpose of the CSRF token?

Cross-Site Request Forgery is an attack that tricks the victim into submitting a malicious request.
Flask-WTF includes a token, unique for each session, that is a mechanism in preventing CSRF attacks. A server-side application generates it in order to protect CSRF vulnerable resources. By validating the CSRF token on the server side, we can insure that the form submission comes form our own server and not a malicious source.


- What is the purpose of `form.hidden_tag()`?

The template generate a hidden field, used by Flask-WTF that includes a token to protect forms against CSRF attacks.
In our route, we can fetch the form data by checking if the form is validated when the user submits the data, then if it is, we can fetch the data.