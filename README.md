
---
title: MySQL with Python: A Beginner's Guide (Based on Tech With Tim's Video)
---
## Introduction

* **Topic:** Connecting and interacting with MySQL databases using Python.
* **Source:**  Tech With Tim's YouTube video: [https://www.youtube.com/watch?v=91iNR0eG8kE&ab_channel=TechWithTim](https://www.youtube.com/watch?v=91iNR0eG8kE&ab_channel=TechWithTim)
* **Why this is important:** Learn how to build dynamic applications that store and retrieve data.
* **What you'll learn:**
    * Setting up the necessary environment.
    * Connecting to a MySQL database from Python.
    * Executing SQL queries using Python.
    * Performing CRUD operations (Create, Read, Update, Delete).

---
title: Prerequisites

* **Python Installed:** Make sure you have Python installed on your system.
* **MySQL Server Installed:** You need a running MySQL server. This could be:
    * Locally installed MySQL Server.
    * A cloud-based MySQL service (e.g., AWS RDS, Google Cloud SQL).
* **MySQL Connector/Python:** This is the library that allows Python to communicate with MySQL.
    * Install using pip: `pip install mysql-connector-python`
* **Basic Python Knowledge:** Familiarity with Python syntax and basic programming concepts.
* **Basic SQL Knowledge (Optional but helpful):** Understanding of SQL commands like `SELECT`, `INSERT`, `UPDATE`, `DELETE`.

---
title: Setting up the Connection

* **Import the Connector:**
  ```python
  import mysql.connector
content_copy
download
Use code with caution.

Establish the Connection: Use mysql.connector.connect() to connect to your database.

Connection Parameters:

host: The hostname or IP address of your MySQL server.

user: Your MySQL username.

password: Your MySQL password.

database: The name of the database you want to connect to.

Example:

mydb = mysql.connector.connect(
    host="your_host",
    user="your_user",
    password="your_password",
    database="your_database"
)
content_copy
download
Use code with caution.
Python

Handle Potential Errors: Use try...except blocks to catch connection errors.

title: Creating a Cursor Object

What is a Cursor? A cursor allows you to execute SQL queries and fetch results.

Creating a Cursor: Use the cursor() method of the connection object.

mycursor = mydb.cursor()
content_copy
download
Use code with caution.
Python

Executing Queries: Use the execute() method of the cursor object.

mycursor.execute("SELECT * FROM customers")
content_copy
download
Use code with caution.
Python

title: Performing SELECT Queries (Reading Data)

Executing the SELECT Statement:

mycursor.execute("SELECT name, email FROM customers")
content_copy
download
Use code with caution.
Python

Fetching Results:

fetchone(): Fetches the next row as a tuple.

fetchall(): Fetches all rows as a list of tuples.

fetchmany(size): Fetches a specified number of rows.

Iterating Through Results:

myresult = mycursor.fetchall()
for row in myresult:
    print(row)
content_copy
download
Use code with caution.
Python

title: Performing INSERT Queries (Creating Data)

Writing the INSERT Statement:

sql = "INSERT INTO customers (name, address) VALUES (%s, %s)"
val = ("Amy", "Apple st 652")
content_copy
download
Use code with caution.
Python

Placeholders (%s): Used to safely insert values and prevent SQL injection.

Executing the INSERT Statement:

mycursor.execute(sql, val)
content_copy
download
Use code with caution.
Python

Committing Changes: Crucial to save the changes to the database.

mydb.commit()
print(mycursor.rowcount, "record inserted.")
content_copy
download
Use code with caution.
Python

title: Performing UPDATE Queries (Modifying Data)

Writing the UPDATE Statement:

sql = "UPDATE customers SET address = %s WHERE address = %s"
val = ("Valley 345", "Apple st 652")
content_copy
download
Use code with caution.
Python

Specifying the WHERE Clause: Important to target the correct rows.

Executing the UPDATE Statement:

mycursor.execute(sql, val)
content_copy
download
Use code with caution.
Python

Committing Changes:

mydb.commit()
print(mycursor.rowcount, "record(s) affected")
content_copy
download
Use code with caution.
Python

title: Performing DELETE Queries (Removing Data)

Writing the DELETE Statement:

sql = "DELETE FROM customers WHERE address = %s"
val = ("Mountain 21",)
content_copy
download
Use code with caution.
Python

Specifying the WHERE Clause: Be careful when deleting data!

Executing the DELETE Statement:

mycursor.execute(sql, val)
content_copy
download
Use code with caution.
Python

Committing Changes:

mydb.commit()
print(mycursor.rowcount, "record(s) deleted")
content_copy
download
Use code with caution.
Python

title: Preventing SQL Injection

The Danger of String Formatting: Directly inserting variables into SQL queries can lead to security vulnerabilities.

# Avoid this!
name = "Robert'); DROP TABLE students; --"
mycursor.execute("SELECT * FROM users WHERE name = '" + name + "'")
content_copy
download
Use code with caution.
Python

Using Placeholders: The %s syntax (or ? for some other database connectors) ensures that values are treated as data, not executable code.

sql = "SELECT * FROM users WHERE name = %s"
val = (name,)
mycursor.execute(sql, val)
content_copy
download
Use code with caution.
Python

title: Closing the Connection

Importance of Closing: Releases resources and ensures proper database operation.

Closing the Cursor:

mycursor.close()
content_copy
download
Use code with caution.
Python

Closing the Connection:

mydb.close()
content_copy
download
Use code with caution.
Python

Best Practice: Use try...finally to ensure the connection is closed even if errors occur.

try:
    mydb = mysql.connector.connect(...)
    mycursor = mydb.cursor()
    # ... your database operations ...
finally:
    if mydb.is_connected():
        mycursor.close()
        mydb.close()
        print("MySQL connection is closed")
content_copy
download
Use code with caution.
Python

title: Key Takeaways

MySQL Connector/Python: The bridge between your Python code and your MySQL database.

Connection Object: Represents the connection to the database.

Cursor Object: Used to execute queries and fetch results.

CRUD Operations: Essential for managing data in your database.

SQL Injection: A critical security concern to be aware of and prevent.

Connection Management: Opening and closing connections properly is important.

title: Further Exploration

Error Handling: Learn more about handling specific database errors.

Transactions: Understand how to group multiple operations into a single atomic unit.

Advanced SQL: Explore more complex SQL queries and database features.

Object-Relational Mappers (ORMs): Consider using libraries like SQLAlchemy or Django ORM for more abstract database interaction.

Tech With Tim's Channel: Explore other Python and programming tutorials on his channel.

title: Q & A (Refer to the Video for Detailed Explanations)

This presentation is a summary based on Tech With Tim's video.

For in-depth explanations and demonstrations, please watch the original video: https://www.youtube.com/watch?v=91iNR0eG8kE&ab_channel=TechWithTim

**How to Import into Google Slides:**

1. **Copy the entire output above.**
2. **Open Google Slides.**
3. **Create a new blank presentation.**
4. **In the top menu, click on "File" -> "Import slides...".**
5. **In the import dialog, select the "Upload" tab.**
6. **Drag and drop the text you copied into the upload area, OR click "Browse" and paste the text into a plain text file (.txt) and upload that file.**
7. **Google Slides will interpret the `---` as slide separators and the headings as titles and bullet points.**
8. **You may need to adjust the formatting and layout after importing.**

This output provides a structured outline of the video's content, suitable for a presentation format. Remember to refer to the original video for detailed explanations and code demonstrations.
content_copy
download
Use code with caution.
