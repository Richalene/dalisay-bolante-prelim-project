DataOps Report
Project 10: Digital Media Streaming & Content Engagement Pipeline

By: Shekinah D. Bolante  &  Mary Richalene P. Dalisay

Database
shop_oltp_p10.db

1. ------ Project Overview ------

    The Digital Media Streaming & Content Engagement Pipeline is a fault-tolerant data engineering pipeline designed to extract transactional streaming data from a simulated SQLite OLTP database, validate and clean the incoming records, anonymize user account identifiers, isolate invalid records, and transform the validated data into an analytical Data Lake format.
    
    The project simulates a video-on-demand streaming service that monitors movie viewing activity and user accounts. The source database contains intentionally corrupted and inconsistent records, including missing user account identifiers, malformed genre values, and negative playback durations.
    
    The pipeline processes these operational records without allowing invalid data to interrupt the overall execution. Valid records are transformed into an analytical dataset containing daily streaming engagement summarized by video genre.

The pipeline therefore applies Data Engineering Lifecycle and System Reliability principles to ensure that:

  1. Operational data is extracted safely from the OLTP system.
  2. Invalid records are identified before analytical processing.
  3. Corrupted records are quarantined instead of stopping the pipeline.
  4. User account identifiers are anonymized using SHA-256.
  5. Valid records are transformed into an analytical representation.
  6. Aggregated results are stored as Apache Parquet.
  7. Execution activity is captured through structured logging.

2. ------ The Python pipeline performs: ------

  1. Database connection
  2. Data extraction
  3. Validation
  4. Error isolation
  5. Data cleaning
  6. SHA-256 anonymization
  7. Aggregation

3. ------ Source ------
    shop_oltp_p10.db → orders
    Processing
    media_streaming_dag.py
    Invalid Data
    quarantine/invalid_playback_lengths.csv
    Analytical Data
    data/analytics/genre_engagement_rankings.parquet
    Execution Trace
    logs/content_engagement.log

4. ------ How to Run the Pipeline: ------

  Make sure the following files and directories are available in the project directory:
  
  shop_oltp_p10.db
  media_streaming_dag.py
  
  From the project directory, execute:
  
  python media_streaming_dag.py

The script should then perform the complete pipeline:

  1. Connect to SQLite database
  2. Extract orders
  3. Validate records
  4. Quarantine invalid records
  5. Normalize valid data
  6. Apply SHA-256 anonymization
  7. Aggregate streaming engagement
  8. Write Parquet analytical output
  9. Record execution details in the log

5. ------ Requirements:  ------

  The pipeline requires:
  
  Python v3
  pandas v
  pyarrow v
  
  The following modules are part of the Python Standard Library and do not require separate installation:
  
  sqlite3
  logging
  hashlib
  os / pathlib, if used by the implementation
  
  Dependencies are listed in:
  
  requirements.txt
