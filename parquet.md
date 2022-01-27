# Parquet file Gzip vs Snappy
GZIP compression uses more CPU resources than Snappy or LZO, but provides a higher compression ratio. GZip is often a good choice for cold data, which is accessed infrequently. Snappy or LZO are a better choice for hot data, which is accessed frequently. Snappy often performs better than LZO. ref: google search
Use Snappy if you can handle higher disk usage for the performance benefits (lower CPU + Splittable).
> When Spark switched from GZIP to Snappy by default, this was the reasoning:

Based on our tests, gzip decompression is very slow (< 100MB/s), making queries decompression bound. Snappy can decompress at ~ 500MB/s on a single core.
- Snappy:
  - Storage Space: High
  - CPU Usage: Low
  - Splittable: Yes (1), If you need your compressed data to be splittable, then use BZip2, LZO, and Snappy formats which are splittable, but GZip is not.
  
- GZIP:
  - Storage Space: Medium
  - CPU Usage: Medium
  - Splittable: No
 
 ref: https://stackoverflow.com/questions/35789412/spark-sql-difference-between-gzip-vs-snappy-vs-lzo-compression-formats
 
 
# What is Parquet?
Parquet is an open source file format available to any project in the Hadoop ecosystem. Apache Parquet is designed for efficient as well as performant flat columnar storage format of data compared to row based files like CSV or TSV files.

Parquet uses the record shredding and assembly algorithm which is superior to simple flattening of nested namespaces. Parquet is optimized to work with complex data in bulk and features different ways for efficient data compression and encoding types.  This approach is best especially for those queries that need to read certain columns from a large table. Parquet can only read the needed columns therefore greatly minimizing the IO.

# Advantages of Storing Data in a Columnar Format:
- Columnar storage like Apache Parquet is designed to bring efficiency compared to row-based files like CSV. When querying, columnar storage you can skip over the non-relevant data very quickly. As a result, aggregation queries are less time consuming compared to row-oriented databases. This way of storage has translated into hardware savings and minimized latency for accessing data.
- Parquet is built to support flexible compression options and efficient encoding schemes. As the data type for each column is quite similar, the compression of each column is straightforward (which makes queries even faster). Data can be compressed by using one of the several codecs available; as a result, different data files can be compressed differently.
- Apache Parquet works best with interactive and serverless technologies like AWS Athena, Amazon Redshift Spectrum, Google BigQuery and Google Dataproc.

# Difference Between Parquet and CSV
CSV is a simple and widely spread format that is used by many tools such as Excel, Google Sheets, and numerous others can generate CSV files. Even though the CSV files are the default format for data processing pipelines it has some disadvantages:

- Amazon Athena and Spectrum will charge based on the amount of data scanned per query.
- Google and Amazon will charge you according to the amount of data stored on GS/S3.
- Google Dataproc charges are time-based.
Parquet has helped its users reduce storage requirements by at least one-third on large datasets, in addition, it greatly improved scan and deserialization time, hence the overall costs.

The following table compares the savings as well as the speedup obtained by converting data into Parquet from CSV.
![image](https://user-images.githubusercontent.com/52529498/151384560-5c3def77-2578-4b48-896d-927bdb4d9c6d.png)

- [Reference for above notes](https://databricks.com/glossary/what-is-parquet#:~:text=Parquet%20is%20an%20open%20source,like%20CSV%20or%20TSV%20files) 

 
