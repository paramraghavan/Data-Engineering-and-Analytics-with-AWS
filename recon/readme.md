# Recon process for entire ingestion pipeline
200+ pipelines performing ingestions, some of them are incremental, some of them are full load, some of the small loads are sometimes incremental other times full load
identify the  recon processes that be applied 
* to make sure we ingest what we get.
* Data quality check.

Here's a systematic approach:

1. Source-to-Landing Reconciliation
   - Record count comparison between source and landing area
   - File size/byte count comparison for file-based ingestion
   - Checksum verification of loaded files
   - Timestamp tracking of last successful load
   - For incremental loads: tracking of watermark/high-water mark values

2. Data Quality Checks at Landing
   - Null checks for critical fields
   - Data type validation
   - Date format consistency
   - Range checks for numeric fields
   - Pattern matching for standardized fields (e.g., email, phone)
   - Duplicate record detection

3. Load Pattern Analysis
   - Monitor volume patterns (e.g., expected daily/weekly/monthly volumes)
   - Track historical patterns of full vs incremental loads
   - Set up anomaly detection for unexpected volume changes
   - Maintain metrics on load duration and resource utilization

4. End-to-End Reconciliation
   - For full loads: source-to-target record count matching
   - For incremental loads: 
     - Delta record validation
     - Comparison of changed records against source
     - Verification of unchanged records remaining intact
   - Running totals/aggregates comparison for key metrics


## Explain watermark

In the context of **incremental data loads**, tracking **watermark** or **high-watermark** values is crucial for identifying and processing only the data that has changed or been added since the last load. Here's an explanation:

---

### **What is a Watermark?**
A **watermark** represents a point up to which data has been successfully processed. For example:
- A **low-watermark** indicates the earliest point in data history to consider (rarely used in incremental loads).
- A **high-watermark** represents the latest point up to which the data has been processed during the last load.

---

### **High-Watermark for Incremental Loads**
The high-watermark is used to:
1. **Identify New/Updated Data**: By comparing the current data values (e.g., timestamps or sequence numbers) with the stored high-watermark, you can identify records that are new or updated since the last load.
2. **Resume Interrupted Loads**: If a load process fails, the high-watermark ensures that only unprocessed data is retried.
3. **Reconciliation**: Provides a reference for reconciling source and target data to confirm all relevant records have been loaded.

---

### **How is it Implemented?**
1. **Tracking Mechanism**:
   - The high-watermark is typically a column in the source data that monotonically increases, such as:
     - A **timestamp** column (e.g., `last_updated`, `modified_date`).
     - A **sequence number** column (e.g., `id` or version control).
   - The most recent value of this column is stored (persisted) after each incremental load.

2. **Process Flow**:
   - **Step 1**: Retrieve the last high-watermark from storage (e.g., a database, file, or metadata repository).
   - **Step 2**: Query the source data for rows where the column value is greater than the stored high-watermark.
   - **Step 3**: Load the new/updated records into the target system.
   - **Step 4**: Update the high-watermark value to the latest value processed.

---

### **Reconciliation in Incremental Loads**
Reconciliation ensures data accuracy and completeness during incremental loading. Key steps:
1. **Source-Target Comparison**:
   - Compare the high-watermark in the target system with the current maximum value in the source system to ensure all data up to the watermark is loaded.
   
2. **Record Counts**:
   - Confirm that the count of records processed matches the count of records available in the source for the specified watermark range.
   
3. **Error Handling**:
   - Identify and address discrepancies, such as missing records or duplicates.

---

### **Example Use Case**
#### Scenario:
You have a source database with a table `transactions` containing a column `last_modified`. The target system needs to load only new or updated transactions incrementally.

#### Workflow:
1. Retrieve the last high-watermark value (`2025-01-05 10:00:00`).
2. Query the source database:
   ```sql
   SELECT * 
   FROM transactions 
   WHERE last_modified > '2025-01-05 10:00:00';
   ```
3. Load the results into the target.
4. Update the high-watermark to the most recent `last_modified` value in the loaded data.
