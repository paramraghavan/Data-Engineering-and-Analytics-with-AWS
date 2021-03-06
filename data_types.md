Only 10% of all data collected or generated by businesses is structured data, another 10% of all data collected or generated by businesses is semistructured data, and the rest—the other 80%—is unstructured data.

- **Structured data**
relational or structured data. That data is commonly stored in relational databases, hence the name. It is highly structured by rules and constraints set within the database. 
This kind of data is the backbone for transactional applications. Structured data is organized and stored in the form of values that are grouped into rows and columns of a table.
- **Semi-structured data**
This data is often stored in non-relational (often called NoSQL) databases or even XML or JSON files. This data does not have a strict structure and is often more temporary 
in nature. Examples include the moves you make in an online video game, your internet browser cache, and even social apps that automatically delete your posts after a certain
amount of time. Semistructured data is often stored in a series of key-value pairs that are grouped into elements within a file.
- **Unstructured data**
This data often takes the form of files or objects, has no single structure, and represents everything else that a business collects and generates. This data is often considered
untouchable because it does not meet conventional norms. It requires tagging and cataloging in order to be analyzed, and this prevents many businesses from using it in their data
analysis solutions. Examples include images, email messages, text files, social media content, text messages, and videos. Unstructured data is not structured in a consistent way. Some data may have structure similar to semi-structured data but others may only contain metadata.

![image](https://user-images.githubusercontent.com/52529498/141729500-b1b91c1b-dee5-49b6-aeb4-455c04c89d90.png)

ref: https://www.datamation.com/big-data/structured-vs-unstructured-data.html

## Datasets from everyday life
![image](https://user-images.githubusercontent.com/52529498/141729744-a1a748fa-3c4a-4793-9834-8ffa72d0f500.png)


## discuss semistructured and unstructured data stores
Semistructured and unstructured data can be stored in NoSQL databases, which is very common for semistructured data. These types of data stores can also be stored on file servers or in data lakes, which are both common for unstructured data. NoSQL databases store data that has no need for relationships. A better term might be Not Only SQL. NoSQL databases were created at a time when the rapid ingestion of data from websites and online games could no longer be handled by relational database systems effectively. For example  think about the times you have started to order something and then decided to wait until later. That abandoned data in the shopping cart has to be dealt with. In a relational database, there could be dozens of records across numerous tables that would have to be deleted. But with NoSQL databases, there is a single record for your entire shopping cart. When you abandon it, only that one record needs to be removed. This is the superpower of NoSQL databases.

When a customer first adds a product to the shopping cart, it is stored in a NoSQL database. Once the customer begins the checkout process, the data from the NoSQL database can be passed to a relational database for permanent storage. With data safely stored in the relational database, the customer completes their order, and the record in the NoSQL database can be deleted. This partnership between databases types is one way that massive ecommerce sites can meet the needs of thousands of customers every minute. In a NoSQL database, all of the information for each product, including the associated supplier, would be stored in a single item within the database table,so  we will have redundant data.

NoSQL databases are built to store semistructured and unstructured data in a way that provides for rapid collection and retrieval. There are several broad categories of NoSQL databases, like document stores, which store semistructured data in the form of files. These files range in form but can include JSON and XML. You can navigate the files using many languages, including Python and Node.js. Semistructured files contain data stored as a series of elements. Each element or item is an instance of a person, place, thing, or event. For instance, the document store may hold a series of log files from a set of servers. Every server is a little different and can generate log files specific to the way it is configured. There is no need for every server’s log files to contain the same attributes. The greatest strength of document stores is their flexibility. Users do not need to plan for a specific type of data when the document store is created, and they are easy to scale because of the lack of strict schemas.

Document stores sacrifice ACID(atomicity, consistency, isolation, durability) compliance to gain this flexibility. Remember that ACID compliance is how we can guarantee the quality of the data within a relational database.

![image](https://user-images.githubusercontent.com/52529498/149370474-e371893a-c096-40b2-96a8-214230af7bac.png)
ref: https://www.bmc.com/blogs/acid-atomic-consistent-isolated-durable/

Key-value databases, like dynamo db, are another type of NoSQL database. They store semistructured data in the form of key-value pairs. Logically, data is stored in a single table. This table contains items, and each item contains one or more attributes. Each item must contain a unique identifier or primary key.
An important distinction to make between key-value tables and relational tables is that key-value tables are schemaless. This means that you do not have to specify what each attribute is before you use it. You also have the advantage of creating nested attributes. These are attributes that have their own attributes. For instance, you could have an Address attribute with Street, City, State, and Postal Code attributes nested inside. A relational database would likely move this nested information into a different table.

### Document stores
Document stores are a type of non-relational database that store semistructured and unstructured data in the form of files. These files range in form but include JSON, BSON, and XML. The files can be navigated using numerous languages including Python and Node.js. BSON - BSON is a serialization format encoding format for JSON mainly used for storing and accessing the documents, whereas JSON is a human-readable standard file format mainly used for transmission of data in the form of key-value attribute pairs

Logically, files contain data stored as a series of elements. Each element is an instance of a person, place, thing, or event. For instance, the document store may hold a series of log files from a set of servers. These log files can each contain the specifics for that system without concern for what the log files in other systems contain.

- Strengths:
  - Flexibility
  - No need to plan for a specific type of data when creating one
  - Easy to scale
- Weaknesses:
  - Sacrifice ACID compliance for flexibility
  - Cannot query across files

### Key-value stores
Key-value databases are a type of non-relational database that store unstructured data in the form of key-value pairs.

Logically, data is stored in a single table. Within the table, the values are associated with a specific key. The values are stored in the form of blob objects and do not require a predefined schema. The values can be of nearly any type.

- Strengths: 
  - Very flexible
  - Able to handle a wide variety of data types
  - Keys are linked directly to their values with no need for indexing or complex join operations
  - Content of a key can easily be copied to other systems without reprogramming the data
- Weaknesses: 
 - Impossible to query values because they are stored as a single blob
 - Updating or editing the content of a value is quite difficult
 - Not all objects are easily modeled as key-value pairs

### Schema changes in a relational database vs non relational database

#### Schema changes in a relational database
The needs of the business have changed. You need to add a new column to track each product's rating. Not all products have a rating yet, so you need to allow the column to accept NULL values.

To add a new column to the table, you must:
- Execute a SQL command to add the column.
- The table now contains an empty column.
- Populate the new column with a value for each existing record.

![image](https://user-images.githubusercontent.com/52529498/141931571-e27a5712-e36f-473a-ae66-979374e0d731.png)

#### Schema changes in a non-relational database
When the same requirement is placed on data in a non-relational database, the remedy is quite different. You simply add the data for that record.
With a non-relational database, each record can have its own set of attributes. This flexibility is one of the greatest benefits of non-relational databases.

![image](https://user-images.githubusercontent.com/52529498/141931722-c0c69fdc-5dc6-484c-b2df-5daedebfb6ba.png)

### Graph database


### Comparing relational and non-relational databases
<table style="width:506.05pt;border-collapse:collapse;border:none;"><tbody><tr><td style="width:107.75pt;border:solid #ED7D31 1.0pt;border-right:none;background:#ED7D31;padding:0in 5.4pt 0in 5.4pt;height:22.0pt;"><p style="text-align:center;"><strong><span style="color:rgb(255, 255, 255);font-size:17px;">Characteristic</span></strong></p></td><td style="width:121.25pt;border-top:solid #ED7D31 1.0pt;border-left:none;border-bottom:solid #ED7D31 1.0pt;border-right:none;background:#ED7D31;padding:0in 5.4pt 0in 5.4pt;height:22.0pt;"><p style="text-align:center;"><span style="font-size:17px;"><span style="color:rgb(255, 255, 255);"><strong>Relational</strong></span></span></p></td><td style="width:148.5pt;border-top:solid #ED7D31 1.0pt;border-left:none;border-bottom:solid #ED7D31 1.0pt;border-right:none;background:#ED7D31;padding:0in 5.4pt 0in 5.4pt;height:22.0pt;"><p style="text-align:center;"><span style="font-size:17px;"><span style="color:rgb(255, 255, 255);"><strong>Non-relational</strong></span></span></p></td><td style="width:128.55pt;border:solid #ED7D31 1.0pt;border-left:none;background:#ED7D31;padding:0in 5.4pt 0in 5.4pt;height:22.0pt;"><p style="text-align:center;"><strong><span style="color:rgb(255, 255, 255);font-size:17px;">Graph</span></strong></p></td></tr><tr><td style="width:107.75pt;border:solid #F4B083 1.0pt;border-top:none;background:#FBE4D5;padding:0in 5.4pt 0in 5.4pt;height:.2in;"><p><strong>Representation</strong></p></td><td style="width:121.25pt;border-top:none;border-left:none;border-bottom:solid #F4B083 1.0pt;border-right:solid #F4B083 1.0pt;padding:0in 5.4pt 0in 5.4pt;height:.2in;"><p>Multiple tables, each containing columns and rows</p></td><td style="width:148.5pt;border-top:none;border-left:none;border-bottom:solid #F4B083 1.0pt;border-right:solid #F4B083 1.0pt;padding:0in 5.4pt 0in 5.4pt;height:.2in;"><p>Collection of documents<br>Single table with keys and values</p></td><td style="width:128.55pt;border-top:none;border-left:none;border-bottom:solid #F4B083 1.0pt;border-right:solid #F4B083 1.0pt;padding:0in 5.4pt 0in 5.4pt;height:.2in;"><p>Collections of nodes and relationships</p></td></tr><tr><td style="width:107.75pt;border:solid #F4B083 1.0pt;border-top:none;background:#FBE4D5;padding:0in 5.4pt 0in 5.4pt;height:.2in;"><p><strong>Data&nbsp;</strong><strong>design</strong></p></td><td style="width:121.25pt;border-top:none;border-left:none;border-bottom:solid #F4B083 1.0pt;border-right:solid #F4B083 1.0pt;padding:0in 5.4pt 0in 5.4pt;height:.2in;"><p>Normalized relational or dimensional data warehouse.</p></td><td style="width:148.5pt;border-top:none;border-left:none;border-bottom:solid #F4B083 1.0pt;border-right:solid #F4B083 1.0pt;padding:0in 5.4pt 0in 5.4pt;height:.2in;"><p>Denormalized document, wide column or key value</p></td><td style="width:128.55pt;border-top:none;border-left:none;border-bottom:solid #F4B083 1.0pt;border-right:solid #F4B083 1.0pt;padding:0in 5.4pt 0in 5.4pt;height:.2in;"><p>Denormalized entity relationship</p></td></tr><tr><td style="width:107.75pt;border:solid #F4B083 1.0pt;border-top:none;background:#FBE4D5;padding:0in 5.4pt 0in 5.4pt;height:.2in;"><p><strong>Optimized</strong></p></td><td style="width:121.25pt;border-top:none;border-left:none;border-bottom:solid #F4B083 1.0pt;border-right:solid #F4B083 1.0pt;padding:0in 5.4pt 0in 5.4pt;height:.2in;"><p>Optimized for storage</p></td><td style="width:148.5pt;border-top:none;border-left:none;border-bottom:solid #F4B083 1.0pt;border-right:solid #F4B083 1.0pt;padding:0in 5.4pt 0in 5.4pt;height:.2in;"><p>Optimized for compute</p></td><td style="width:128.55pt;border-top:none;border-left:none;border-bottom:solid #F4B083 1.0pt;border-right:solid #F4B083 1.0pt;padding:0in 5.4pt 0in 5.4pt;height:.2in;"><p>Optimized for relationships</p></td></tr><tr><td style="width:107.75pt;border:solid #F4B083 1.0pt;border-top:none;background:#FBE4D5;padding:0in 5.4pt 0in 5.4pt;height:.2in;"><p><strong>Query&nbsp;</strong><strong>style</strong></p></td><td style="width:121.25pt;border-top:none;border-left:none;border-bottom:solid #F4B083 1.0pt;border-right:solid #F4B083 1.0pt;padding:0in 5.4pt 0in 5.4pt;height:.2in;"><p>Language: SQL</p></td><td style="width:148.5pt;border-top:none;border-left:none;border-bottom:solid #F4B083 1.0pt;border-right:solid #F4B083 1.0pt;padding:0in 5.4pt 0in 5.4pt;height:.2in;"><p>Language: many<br>Uses object querying</p></td><td style="width:128.55pt;border-top:none;border-left:none;border-bottom:solid #F4B083 1.0pt;border-right:solid #F4B083 1.0pt;padding:0in 5.4pt 0in 5.4pt;height:.2in;"><p>Language: many<br>Uses object querying</p></td></tr><tr><td style="width:107.75pt;border:solid #F4B083 1.0pt;border-top:none;background:#FBE4D5;padding:0in 5.4pt 0in 5.4pt;height:.2in;"><p><strong>Scaling</strong></p></td><td style="width:121.25pt;border-top:none;border-left:none;border-bottom:solid #F4B083 1.0pt;border-right:solid #F4B083 1.0pt;padding:0in 5.4pt 0in 5.4pt;height:.2in;"><p>Scale vertically</p></td><td style="width:148.5pt;border-top:none;border-left:none;border-bottom:solid #F4B083 1.0pt;border-right:solid #F4B083 1.0pt;padding:0in 5.4pt 0in 5.4pt;height:.2in;"><p>Scale horizontally</p></td><td style="width:128.55pt;border-top:none;border-left:none;border-bottom:solid #F4B083 1.0pt;border-right:solid #F4B083 1.0pt;padding:0in 5.4pt 0in 5.4pt;height:.2in;"><p>Hybrid</p></td></tr><tr><td style="width:107.75pt;border:solid #F4B083 1.0pt;border-top:none;background:#FBE4D5;padding:0in 5.4pt 0in 5.4pt;height:.2in;"><p><strong>Implementation</strong></p></td><td style="width:121.25pt;border-top:none;border-left:none;border-bottom:solid #F4B083 1.0pt;border-right:solid #F4B083 1.0pt;padding:0in 5.4pt 0in 5.4pt;height:.2in;"><p>OLTP business systems, OLAP data warehouse</p></td><td style="width:148.5pt;border-top:none;border-left:none;border-bottom:solid #F4B083 1.0pt;border-right:solid #F4B083 1.0pt;padding:0in 5.4pt 0in 5.4pt;height:.2in;"><p>OLTP web/mobile apps</p></td><td style="width:128.55pt;border-top:none;border-left:none;border-bottom:solid #F4B083 1.0pt;border-right:solid #F4B083 1.0pt;padding:0in 5.4pt 0in 5.4pt;height:.2in;"><p>OLTP web/mobile apps</p></td></tr></tbody></table>









