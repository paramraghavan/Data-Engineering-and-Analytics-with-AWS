# What is Immutable Data?

Immutable data is a piece of information in a database that cannot be (or shouldn’t be) deleted or modified. Most traditional databases store data in a mutable format,
meaning the database overwrites the older data when new data is available. For example, in an employee database, the address information is over-written when an employee
changes their residence.

In contrast, the databases that store immutable data will not overwrite an old item when new information is available. They use various techniques 
to preserve the historical and current values of the data. Immutable data is highly useful for auditing and debugging.

A real-life example of **immutable data is someone’s medical records.** Over the years, a person might have sought treatment for different ailments. 
The medical record consists of various prescriptions, procedures, and test reports. These data files are immutable. For example, when a person receives a
new medical prescription, their old prescription should not be overwritten. Instead, the database should append the new data to the existing one. Historical
medical data is a classic example of immutable data.

# Why Do Organizations Need Immutable Data?
With the advent of cloud data and the Internet of Things (IoT), organizations receive a huge volume of transaction data. This data needs to be quickly stored in 
a database. Immutable files are a suitable solution for storing high-speed transaction logs. Organizations also need to consider the need for historical data. 
With data privacy regulations getting stricter, many organizations choose to preserve their historical data. It will help them be compliant if a customer 
or government requests past data. A database that stores data in the immutable format is best suited for this use case.

Organizations often need to compare their current data to a historical one to understand user trends or measure growth. In such cases, overwriting 
the historical data is not a good idea. Immutable data also helps organizations to keep track of the changes they went through over the years; it is especially
helpful in software systems.


# What Are the Uses of an Immutable Database?

## Storing Stream Data
With the information explosion and the advent of the IoT, organizations receive a massive amount of data every second. They cannot afford delays in
storing data. Most of the traditional databases that use a mutable file have a certain latency because they erase the previous data, write the new one, 
and check for integrity. But in the case of stream data—for example, from IoT sensors—the database should quickly store the data. When the database uses 
immutable data files, it simply appends the new data. This makes immutable databases much faster at storing data—and therefore more suitable for storing 
stream data.

## Preserving Historical Context
Personal data, such as a person’s medical history, needs to be stored permanently to provide a context for the new data. For example, when a person is 
treated for an ailment, all their old medications and treatments need to be taken into account. While traditional databases can provide historical
context, they don’t guarantee data preservation. Immutable databases, by their very nature, ensure that no data will be ever deleted.

## Auditing and Debugging
Systems that frequently change, such as websites or software, need to preserve the major snapshots of the system to track changes. Most version control systems
store data in immutable files so that there is no risk of overwriting them. Financial institutions also need an immutable database to preserve all their historical 
transactions. Other organizations that need to present data for frequent auditing can also benefit from an immutable database.

# How Does an Immutable Database Work?
In contrast to the traditional relational databases (mutable databases) that are record-based, *the immutable databases are log-based*. When a new data item is available, 
the mutable database rewrites a particular cell in a data table. *The immutable database stores data in logs and creates a new log for every new piece of data.*

To understand the way an immutable database works, look at a simple database that stores details of a blog article. A classic relational database would store 
this data in a mutable format, with the details of the **blog post being stored in a table. Assume that permalink, title, and content are the three columns of 
this table.** In a mutable database, when the title or the content changes, the database performs an update operation. The new data overwrites the previous entry. 
The older title(s) and content are lost forever. A standard, immutable database stores this same information as logs.

**The mutable database only stores the current state of the blog. The immutable database stores the history of the blog along with the current state.
An immutable database only performs insert operations and never does an update of an existing data field.**

# What Are the Advantages of Immutable Data?
## Faster Operations
When data is stored as immutable, new data is appended to the previous one, along with a timestamp. This means the database can simply insert data without blocking the 
system to perform integrity checks. This quality of immutable data is crucial in the case of stream and sensor data. In these cases, data arrives continuously and 
needs to be stored with minimum latency.

## Historical Context
Many organizations need to compare historical data with the latest version for better, more contextual analytics. Immutable databases preserve all historical data. It helps to 
create checkpoints in the past to which a system can be restored.

## Auditability
Many industries, especially healthcare and financial, might face random audits. It is crucial for them to preserve all the data so they have the historical data handy
if it’s required for an audit.

## Compliance
Across the globe, data privacy rules are quite stringent. Users have the right to demand a copy of all the data an organization has collected from them. Storing data as
immutable helps the organizations to comply with such requests.


# What Are the Disadvantages of Immutable Data?
## Higher Storage Requirements
Storing immutable data has higher storage requirements compared to traditional mutable databases. Every update is stored as a different log, 
which increases the size of the database.

## Data Compliance
By design, an immutable database never deletes any data. However, most of the data regulations mandate that the system should delete the data if a user requests it. 
This is a significant challenge for immutable databases built on the assumption that no data is ever deleted.

# How do Immutable Databases Offer a Deletion Function?

Inherently, the immutable databases do not provide a deletion function because the database itself is designed on the principle that the data is never deleted. 
However, as we saw in the previous section, data privacy regulations give users the right to be “forgotten.” This requires that the data be deleted/overwritten.

** Crypto-shredding is a solution that can be used to “overwrite” the immutable data. In a database with a crypto-shredding facility, the immutable data is stored in an encrypted format. 
An encryption key is required to decrypt the personal data stored in the database. All such keys are stored in a mutable database. When there is a request to overwrite the data, the
data isn’t deleted. Instead, the associated encryption key is overwritten. With the encryption key gone, the data is no longer useful. It is as good as deleting the data associated 
with the encryption key. This is an acceptable solution for the European Union’s data privacy rules.**

Ref: https://www.tibco.com/reference-center/what-is-immutable-data