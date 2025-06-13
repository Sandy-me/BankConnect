#  BankConnect

A simple Java desktop application that connects to a MySQL database using JDBC. This system provides a Swing-based GUI to manage customer records and a command-line interface to execute basic SQL queries. It is ideal for learning JDBC, database interaction, and Java Swing fundamentals.


##  Project Structure


BankConnect/
├── src/
│   ├── bankGUI.java          # GUI-based customer management
│   └── bank.java             # Console-based query tool
├── lib/
│   └── mysql-connector-java-8.0.xx.jar  # MySQL JDBC driver
├── sql/
│   └── bank.sql              # SQL script to create the schema (optional)
├── .gitignore                # Ignores compiled files and system configs
└── README.md



## Features

### GUI App (`bankGUI.java`)
- Add new customers with name, street, and city.
- View existing customers.
- Modify customer records.
- Built using Java Swing.
- Connects to MySQL via JDBC.

### Query Console (`bank.java`)
- Runs 5 predefined SQL queries:
  1. All customer names.
  2. Distinct branch names.
  3. All branch details.
  4. Accounts with balance > 700.
  5. Accounts in ‘Brighton’ branch with balance > 800.


## Technologies Used

- Java (JDK 8+)
- JDBC (MySQL Connector/J)
- MySQL Database
- Java Swing (GUI)
- Visual Studio Code (IDE)



## Setup Instructions

### Database Setup

1. Install MySQL and create a database named `bank`.
2. You can use a schema like this:

   sql
CREATE DATABASE bank;
USE bank;

CREATE TABLE customer (
    customer_name VARCHAR(100) PRIMARY KEY,
    customer_street VARCHAR(100),
    customer_city VARCHAR(100)
);

CREATE TABLE branch (
    branch_name VARCHAR(100) PRIMARY KEY,
    branch_city VARCHAR(100),
    assets DECIMAL(15,2)
);

CREATE TABLE account (
    account_number VARCHAR(20) PRIMARY KEY,
    branch_name VARCHAR(100),
    balance DECIMAL(10,2),
    FOREIGN KEY (branch_name) REFERENCES branch(branch_name)
);


3. Add some sample data to test.

###  Compile and Run

Ensure you have the MySQL Connector JAR in the `lib/` folder.

####  Compile

   bash
javac -cp "lib/*" src/bankGUI.java src/bank.java


#### Run the GUI

   bash
java -cp "lib/*:src" bankGUI


#### Run the Console App

   bash
java -cp "lib/*:src" bank


> Note: On **Windows**, use `;` instead of `:` in the classpath.


## Notes

* Make sure to **replace database credentials** in your Java files with placeholders before uploading publicly.
* You can extend this project to include branch and account management in the GUI.
* Consider using `PreparedStatement` instead of string concatenation to avoid SQL injection risks.


## License

This project is open for educational and personal use. Feel free to modify and enhance it.


## Author

Sandra Meroka
GitHub: https://github.com/Sandy-me

