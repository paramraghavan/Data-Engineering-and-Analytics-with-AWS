# Data-Engineering-and-Analytics-with-AWS
This is based on my experience working with AWS, resources available in AWS and my curious web searches.

## Architecting on AWS
When architecting our system we should separate *Compute* and *Storage*. We should use
- the open data formats like apache parquet, Avro, ORC. etc. I have mostly use [parquet](https://github.com/paramraghavan/Data-Engineering-and-Analysis-with-AWS/blob/main/parquet.md), but in some cses used csv as that was the consumers requirement.
- The data should not be replicated but shared across team, such that the same data is used by marketing team for sql query and s used by data scientist to run their model

## Lifecycle of data
![image](https://user-images.githubusercontent.com/52529498/140820594-4f8775e2-7506-4b1f-a98e-c3e547dc9e73.png)



References:
- http://diagramo.com/editor/editor.php


