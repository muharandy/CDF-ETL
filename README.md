# CDF-ETL

Exploring NiFi for Batch ETL

- Staging Table creation using Hive via Hue
- Initial load with NiFi with QueryDatabaseTable, ConvertRecord with AvroReader and CSVRecordSetWriter, followed by PutHDFS
- Data Profiling and Exploration with CDSW
- Data transformation or aggregation using PySpark invoked via ExecuteSparkInteractive through Livy
