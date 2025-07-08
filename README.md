**Online Bookshop - Core Java JDBC Project**
_______________________________________________________________________________________________________________________________
***This is a console-based menu-driven Online Bookshop application written in Core Java using JDBC and PostgreSQL.***

**💻 Technologies Used:**
- Java (JDK 8+)
- PostgreSQL
- JDBC
_____________________________________________________________________________________________________________________________
 **📦 Features:**
- Add authors and categories
- Add books with category and author
- Register users
- View available books
- Place orders with multiple items
- Uses PostgreSQL relationships and constraints
____________________________________________________________________________________________________________________________
**Dependancies:**

<dependencies>

    <dependency>
   
    <groupId>org.postgresql</groupId>
    
    <artifactId>postgresql</artifactId>
    
    <version>42.7.7</version>

</dependency>

</dependencies>
_______________________________________________________________________________________________________________________

**Prerequisites:**

**Before running the project, ensure you have the following installed:**

**1]Java Development Kit (JDK) 17 or higher.**

**2]PostgreSQL 15 or higher.**

**3]create PostgreSQL database with the following table:**
  
***-- Run in pgAdmin or psql***


CREATE TABLE Authors (
   
    author_id SERIAL PRIMARY KEY,
   
    name VARCHAR(100) NOT NULL
);


CREATE TABLE Categories (
  
    category_id SERIAL PRIMARY KEY,
  
    name VARCHAR(100) NOT NULL
);


CREATE TABLE Users (
   
    user_id SERIAL PRIMARY KEY,
   
    name VARCHAR(100),
   
    email VARCHAR(100),
   
    password VARCHAR(50)
);


CREATE TABLE Books (
    
    book_id SERIAL PRIMARY KEY,
   
    title VARCHAR(150),
   
    price DECIMAL(10,2),
    
    author_id INT REFERENCES Authors(author_id),
   
    category_id INT REFERENCES Categories(category_id)
);


CREATE TABLE Orders (
   
    order_id SERIAL PRIMARY KEY,
   
    user_id INT REFERENCES Users(user_id),
   
    order_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);


CREATE TABLE Order_Items (
   
    item_id SERIAL PRIMARY KEY,
   
    order_id INT REFERENCES Orders(order_id),
   
    book_id INT REFERENCES Books(book_id),
    
    quantity INT
);
_______________________________________________________________________________________________________________________________ 
**Contact:**

***For any questions or feedback, feel free to reach out:***

**Your Name :** Shruti Bapu Thorat

**Email:** shrutithorat767@gmail.com

**GitHub:** https://github.com/shruti-thorat0715/JavaFullStack/edit/main/README.md
_______________________________________________________________________________________________________________________________

**Enjoy using the Online Bookshop ! 🚀**


 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
  
