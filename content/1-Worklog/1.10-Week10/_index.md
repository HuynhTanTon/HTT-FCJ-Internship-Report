---
title: "Week 10 Worklog"
date: 2024-01-01
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---

**Period:** 22/06/2026 – 28/06/2026

### Week 10 Objectives:

* Build a data lake on AWS: S3 + Glue + Athena + QuickSight.
* Query large datasets on S3 without a traditional database server.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | ---- | ---------- | --------------- | ------------------ |
| Mon | Study data lake architecture: S3 (storage), Glue (ETL), Athena (query), QuickSight (BI). | 22/06/2026 | 22/06/2026 | <https://000070.awsstudygroup.com/><br><https://000035.awsstudygroup.com/> |
| Tue | Lab 1: Upload a ~100,000-row CSV to S3; create an Athena table and run SQL directly on S3. | 23/06/2026 | 24/06/2026 | <https://000106.awsstudygroup.com/><br><https://000040.awsstudygroup.com/> |
| Wed | Practice AWS Glue Crawler / ETL; fix DynamicFrame API issues (convert with `toDF()` to Spark DataFrame). | 25/06/2026 | 25/06/2026 | <https://000040.awsstudygroup.com/><br><https://000105.awsstudygroup.com/> |
| Thu | Optimize Athena cost with Parquet + daily partitions; visualize with QuickSight. | 26/06/2026 | 26/06/2026 | <https://000073.awsstudygroup.com/><br><https://000106.awsstudygroup.com/> |
| Fri | Summarize the S3 → Glue → Athena → QuickSight pipeline and cost best practices. | 27/06/2026 | 27/06/2026 | <https://000070.awsstudygroup.com/><br><https://cloudjourney.awsstudygroup.com/> |

### Week 10 Achievements:

* Queried large S3 datasets with Athena without a database server.
* Used Glue for ETL and optimized Athena with Parquet + partitions.
* Visualized results with QuickSight.

### Challenges & Solutions:

* Glue Job failed due to incorrect DynamicFrame API usage → followed the Glue guide and converted with `toDF()` to a Spark DataFrame.

### Next Week Plan:

* Explore AI/ML Services: SageMaker, Rekognition and Amazon Bedrock.
