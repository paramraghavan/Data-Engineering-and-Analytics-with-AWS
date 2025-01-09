1. Sender-to-Ingestion Verification:
- File/Record Level Controls:
  - Get control totals from sender (usually in a control file or manifest)
    - Total number of files
    - Total number of records per file
    - File checksums
    - Batch totals (e.g., total amount, total quantity)
  - Compare these against what you received

**The key differences between general reconciliation and sender verification are:**
1. Verification Focus:
- Sender Verification: 
  - Focuses on matching what sender claims they sent vs what you received
  - Usually involves pre-defined control totals
  - Happens at the point of ingestion
  - Primary goal is to ensure complete data receipt

- Reconciliation:
  - Broader scope covering entire data pipeline
  - Includes transformations and business rules
  - Happens at multiple points in the pipeline
  - Focuses on data quality and consistency

2. Implementation Approach:
- Sender Verification:
  - Requires control file/manifest from sender
  - Immediate verification upon receipt
  - Binary pass/fail based on exact matches
  - Focus on file integrity and completeness

- Reconciliation:
  - Can include business rules
  - May allow for acceptable variances
  - Includes quality checks
  - Tracks data lineage through transformations

3. Timing:
- Sender Verification:
  - Real-time or near real-time
  - Must happen before data processing
  - Blocks further processing if verification fails

- Reconciliation:
  - Can be done after processing
  - May include historical comparisons
  - Can be scheduled independently
