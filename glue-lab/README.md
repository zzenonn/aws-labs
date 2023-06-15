# Data Transformation and ETL

## Lab Steps

### Crawl the Dataset
1. On the AWS Glue menu, select Crawlers on theleft side under **Data Catalog**.
2. Click Add crawler.
3. Enter ***amazon-glueetl-lab*** as the crawler name for initial data load.
4. Optionally, enter the description. This should also be descriptive and easily recognized and Click **Next**.
5. Click **Next** to move on to **Choose data sources and classifiers**
6. For Choose a data store, click the drop-down box and select S3.
7. For Location of S3 data, select **In a different account**.
8. For S3 path, type `s3://amazon-reviews-pds/parquet`.
9. Click **Next** to enter Configure security settings.
10. Click **Create new IAM Role**. 
11. Enter `AWSGlueServiceRole-Default` as the name of the role.
12. Click **Next** to enter Set output and scheduling.
13. Click **Add a database**.
14. Name the database `amazon-reviews`
15. Click **Next**.
16. Click **Create**.
17. Click **Run crawler**.

### Query the Dataset

1. From the Management Console, search for the **Athena** service and click it.
2. On the left side, ensure that `AwsDataCatalog` and `amazon-reviews` is selected.
3. In the query editor, run the following query:

```sql
SELECT AVG(star_rating) as rating, product_category FROM "amazon-reviews"."parquet" GROUP BY product_category ORDER BY rating DESC;
```

You should be able to see the result of a query reading from S3.