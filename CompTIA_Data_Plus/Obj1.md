# CompTIA Data+ Exam: 1.0 Data Concepts and Environments

## 1.1 Identify basic concepts of data schemas and dimensions

### Databases

#### Relational Databases

Relational databases are based on the relational model, an intuitive, straightforward way of representing data in tables. In a relational database, each row in the table is a record with a unique ID called the primary key. Each column in the table represents a different field in the record, making it easy to establish relationships between different tables. For example, consider a university database with tables for Students, Courses, and Enrollment. The Students and Courses tables have a primary key for each student and course, respectively, while the Enrollment table uses foreign keys to represent enrollments in specific courses by specific students.

#### Non-relational Databases

Non-relational databases, or NoSQL databases, are designed for specific data models and have flexible schemas for building modern applications. Non-relational databases are capable of storing structured, semi-structured, and unstructured data. This flexibility is their main advantage over relational databases. For example, a MongoDB database storing Twitter posts would be a Non-relational database, as each post (document) can have different fields (user, message content, timestamp, etc.), and the order of fields can vary from post to post.

### Data mart/data warehousing/data lake

#### Online Transactional Processing (OLTP)

Online transaction processing (OLTP) is a class of systems that supports or facilitates high transaction-oriented applications. OLTP systems are designed to efficiently process transactions in real time. An example of an OLTP system could be a hotel reservation system. When you book a room, the system checks whether a room is available, reserves the room, deducts the cost from your credit card, and confirms your reservation, all in real time.

#### Online Analytical Processing (OLAP)

In contrast to OLTP, online analytical processing (OLAP) is a category of software tools that analyze data stored in databases and provide fast analysis of multidimensional data. OLAP systems allow users to analyze database information from multiple database systems at one time. An example of an OLAP operation could be an annual report of a company's product sales, which would draw data from different database systems, including sales, products, and time.

### Schema Concepts

#### Snowflake Schema

The snowflake schema is a variation of the star schema used in a data warehouse. The difference is that the tables, which describe the dimensions of the star schema, are normalized. This schema is called a snowflake because its diagram resembles a Snowflake. For example, if you have a Product Sales database, the product category, product, and supplier details are separated into different dimension tables in a snowflake schema.

#### Star Schema

The star schema is the simplest type of Data Warehouse schema. It is called a star schema because the entity-relationship diagram of this schema resembles a star, with points radiating from a center. The center of the star consists of a fact table, and the points of the star are the dimension tables. For instance, in a Sales data warehouse, a single Fact table could hold the core transactional data (like total sale amount), and the Dimension tables could contain descriptive attributes related to the Facts (like product, date, store, and customer details).

### Slowly Changing Dimensions

#### Keep Current Information

In a dimension table, when changes occur in the original data source, and you want to overwrite that information in the table, it's a "keep current information" approach. For example, if a customer changes their home address, the new address replaces the old address in the table.

#### Keep Historical and Current Information

On the other hand, there are cases where preserving historical data

 is necessary. In such cases, a new record is added to the table to represent the new information, without discarding the old record. This way, the table keeps both historical and current information. For instance, when a product's price changes, rather than simply overwriting the old price, a new record is created with the new price and the date of the change.

---

## 1.2 Compare and contrast different data types

### Date

The Date data type is used to store date values. A Date value typically includes the year, month, and day, and sometimes also the time. For example, an 'order_date' column in an 'orders' table in an e-commerce database would be a Date data type.

### Numeric

Numeric data types store numeric values. These values can be integers (without decimal points) or floating-point numbers (with decimal points). For example, a 'price' column in a 'products' table storing the prices of products would be a Numeric data type.

### Alphanumeric

An Alphanumeric data type can include letters, numbers, and other characters typically found on a keyboard. They're used when the data to be stored is a mix of letters and numbers. For instance, a product ID, such as 'A123', would be stored as an Alphanumeric data type.

## Currency

The Currency data type is used to store monetary values. It's a type of numeric data type that represents a currency value. This data type is commonly used in business databases. For example, the 'revenue' column in a 'sales' table storing the revenue from each sale would be a Currency data type.

### Text

The Text data type is used to store alphanumeric characters up to the max allowed length. They're used when the data to be stored is primarily composed of letters, as opposed to numbers. For instance, a 'description' column in a 'products' table storing a text description of each product would be a Text data type.

### Discrete vs. Continuous

Discrete data is countable and cannot be broken down into a smaller unit. It represents items that can be counted. For instance, the number of calls received by a call center per day is discrete data.

Continuous data, on the other hand, represents measurements and can be broken down into smaller parts and get more precise values. For example, the time a customer spends on a website is continuous data.

### Categorical/dimension

Categorical, or dimension, data types are used for data that can be divided into groups or categories. For example, a 'gender' column in a 'customers' table storing the gender of each customer is a categorical data type.

### Images

The Image data type is used to store image data, which can be a graphic, a drawing, or a photo. For example, a 'profile_picture' field in a 'users' table storing the profile picture of each user would be an Image data type.

### Audio

The Audio data type is used to store audio data, which can be music, speech, or any type of sound. For example, an 'audio_clip' field in a 'voicemails' table storing voicemail messages would be an Audio data type.

### Video

The Video data type is used to store video data. For example, a 'tutorial_video' field in a 'lessons' table storing video tutorials would be a Video data type.

---

## 1.3 Compare and contrast common data structures and file formats

### Structures

#### Structured

##### Defined rows/columns

Data is organized in tables with defined rows and columns. Each row represents a unique record, and each column represents a field in the record. For example, an Excel spreadsheet that tracks employee attendance would have each row represent a different employee, and columns

 would represent different dates.

##### Key-value pairs

Data is organized as a collection of key-value pairs. Each key is unique and maps to a specific value. For example, a dictionary in Python might store student grades, where each key is a student's name and each value is their grade.

#### Unstructured

##### Undefined fields

Unstructured data refers to information that either does not have a pre-defined data model or is not organized in a predefined manner. This type of data is often text-heavy but may contain data such as dates, numbers, and facts as well. For example, the body of an email has no set structure and can contain any number of fields in any order.

##### Machine Data

Machine data is information generated by machines without human intervention. Examples of machine data include logs generated by servers, GPS data from geo-location services, and sensor data from Internet of Things (IoT) devices.

### Data File Formats

#### Text/Flat file

##### Tab delimited

In a tab-delimited file, each data field is separated by a tab. For example, a .tsv file might contain a list of students, with fields for name, ID number, and grade level separated by tabs.

##### Comma delimited

In a comma-delimited file, each data field is separated by a comma. For example, a .csv file might contain a list of products sold by a company, with fields for product ID, product name, and price separated by commas.

#### JavaScript Object Notation (JSON)

JSON is a lightweight data interchange format that is easy for humans to read and write and easy for machines to parse and generate. JSON uses key-value pairs to store data, making it similar in some ways to a dictionary in Python. For example, a .json file might contain a list of students in a class, with each student represented by a JSON object with keys for name, ID number, and grade level.

#### Extensible Markup Language (XML)

XML is a markup language that defines a set of rules for encoding documents in a format that is both human-readable and machine-readable. XML data is stored in text format and is both human-readable and machine-readable. For example, an .xml file might store data about a collection of books in a library, with tags for title, author, and publication date for each book.

#### Hypertext Markup Language (HTML)

HTML is the standard markup language for documents designed to be displayed in a web browser. It can include text, images, and other types of content. For example, a .html file might display a webpage containing a news article, with tags for the article's title, the body of the article, and images to accompany the article.
