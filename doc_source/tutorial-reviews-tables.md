# Step 4: Preparing the Amazon Comprehend output for data visualization<a name="tutorial-reviews-tables"></a>

To prepare the results of the sentiment and entities analysis jobs for creating data visualizations, you use AWS Glue and Amazon Athena\. In this step, you extract the Amazon Comprehend results files\. Then, you create an AWS Glue *crawler* that explores your data and automatically catalogs it in tables in the AWS Glue Data Catalog\. After that, you access and transform these tables using Amazon Athena, a serverless and interactive query service\. When you have finished this step, your Amazon Comprehend results are clean and ready for visualization\.

For a PII entity detection job, the output file is plaintext, not a compressed archive\. The output file name is the same as the input file, with `.out` appended at the end\. You don't need the step of extracting the output file\. Skip to [ Load the Data into an AWS Glue Data Catalog](#tutorial-reviews-tables-crawler)\.



**Topics**
+ [Prerequisites](#tutorial-reviews-tables-prereqs)
+ [Download the Output](#tutorial-reviews-tables-download)
+ [Extract the output files](#tutorial-reviews-tables-extract)
+ [Upload the extracted files](#tutorial-reviews-tables-upload)
+ [Load the data into an AWS Glue Data Catalog](#tutorial-reviews-tables-crawler)
+ [Prepare the data for analysis](#tutorial-reviews-tables-prep)

## Prerequisites<a name="tutorial-reviews-tables-prereqs"></a>

Before you begin, complete [Step 3: Running analysis jobs on documents in Amazon S3](tutorial-reviews-analysis.md)\.

## Download the Output<a name="tutorial-reviews-tables-download"></a>

The Amazon Comprehend uses Gzip compression to compress output files and save them as a tar archive\. The simplest way to extract the output files is to download the `output.tar.gz` archives locally\. 

In this step, you download the sentiment and entities output archives\.

### Download the Output Files \(Console\)<a name="tutorial-reviews-tables-download-console"></a>

To find the output files for each job, return to the analysis job in the Amazon Comprehend console\. The analysis job provides the S3 location for the output, where you can download the output file\.

**To download the output files \(console\)**

1. In the [Amazon Comprehend console](https://console.aws.amazon.com/comprehend/), in the navigation pane, return to **Analysis jobs**\.

1. Choose your sentiment analysis job `reviews-sentiment-analysis`\.

1. Under **Output**, choose the link displayed next to **Output data location**\. This redirects you to the `output.tar.gz` archive in your S3 bucket\.

1. In the **Overview** tab, choose **Download**\.

1. On your computer, rename the archive as `sentiment-output.tar.gz`\. Since all of the output files have the same name, this helps you keep track of the sentiment and entities files\.

1. Repeat steps 1\-4 to find and download the output from your `reviews-entities-analysis` job\. On your computer, rename the archive as `entities-output.tar.gz`\.

### Download the output files \(AWS CLI\)<a name="tutorial-reviews-tables-download-cli"></a>

To find the output files for each job, use the `JobId` from the analysis job to find the output's S3 location\. Then, use the `cp` command to download the output file to your computer\.

**To download the output files \(AWS CLI\)**

1. To list details about your sentiment analysis job, run the following command\. Replace `sentiment-job-id` with the sentiment `JobId` that you saved\.

   ```
   aws comprehend describe-sentiment-detection-job --job-id sentiment-job-id
   ```

   If you lost track of your `JobId`, you can run the following command to list all of your sentiment jobs and filter for your job by name\.

   ```
   aws comprehend list-sentiment-detection-jobs 
   --filter JobName="reviews-sentiment-analysis"
   ```

1. In the `OutputDataConfig` object, find the `S3Uri` value\. The `S3Uri` value should be similar to the following format: `s3://DOC-EXAMPLE-BUCKET/.../output/output.tar.gz`\. Copy this value to a text editor\.

1. To download the sentiment output archive to your local directory, run the following command\. Replace the S3 bucket path with the `S3Uri` you copied in the previous step\. Replace `path/` with the folder path to your local directory\. The name `sentiment-output.tar.gz` replaces the original archive name to help you keep track of the sentiment and entities files\.

   ```
   aws s3 cp s3://DOC-EXAMPLE-BUCKET/.../output/output.tar.gz 
   path/sentiment-output.tar.gz
   ```

1. To list details about your entities analysis job, run the following command\.

   ```
   aws comprehend describe-entities-detection-job
   --job-id entities-job-id
   ```

   If you don't know your `JobId`, run the following command to list all of your entities jobs and filter for your job by name\.

   ```
   aws comprehend list-entities-detection-jobs
   --filter JobName="reviews-entities-analysis"
   ```

1. From the `OutputDataConfig` object in your entities job description, copy the `S3Uri` value\.

1. To download the entities output archive to your local directory, run the following command\. Replace the S3 bucket path with the `S3Uri` you copied in the previous step\. Replace `path/` with the folder path to your local directory\. The name `entities-output.tar.gz` replaces the original archive name\.

   ```
   aws s3 cp s3://DOC-EXAMPLE-BUCKET/.../output/output.tar.gz 
   path/entities-output.tar.gz
   ```

## Extract the output files<a name="tutorial-reviews-tables-extract"></a>

Before you can access the Amazon Comprehend results, unpack the sentiment and entities archives\. You can use either your local file system or a terminal to unpack the archives\. 

### Extract the output files \(GUI file system\)<a name="tutorial-reviews-tables-extract-gui"></a>

If you use macOS, double\-click the archive in your GUI file system to extract the output file from the archive\.

If you use Windows, you can use a third\-party tool such as 7\-Zip to extract the output files in your GUI file system\. In Windows, you must perform two steps to access the output file in the archive\. First decompress the archive, and then extract the archive\.

Rename the sentiment file as `sentiment-output` and the entities file as `entities-output` to distinguish between the output files\.

### Extract the output files \(terminal\)<a name="tutorial-reviews-tables-extract-terminal"></a>

If you use Linux or macOS, you can use your standard terminal\. If you use Windows, you must have access to a Unix\-style environment, such as Cygwin, to run tar commands\.

To extract the sentiment output file from the sentiment archive, run the following command in your local terminal\.

```
tar -xvf sentiment-output.tar.gz --transform 's,^,sentiment-,'
```

Note that the `--transform` parameter adds the prefix `sentiment-` to the output file inside of the archive, renaming the file as `sentiment-output`\. This allows you to distinguish between the sentiment and entities output files and prevent overwriting\.

To extract the entities output file from the entities archive, run the following command in your local terminal\.

```
tar -xvf entities-output.tar.gz --transform 's,^,entities-,'
```

The `--transform` parameter adds the prefix `entities-` to the output file name\.

**Tip**  
To save storage costs in Amazon S3, you can compress the files again with Gzip before uploading them\. It's important to decompress and unpack the original archives because AWS Glue can’t automatically read data from a tar archive\. However, AWS Glue can read from files in Gzip format\.

## Upload the extracted files<a name="tutorial-reviews-tables-upload"></a>

After extracting the files, upload them to your bucket\. You must store the sentiment and entities output files in separate folders in order for AWS Glue to read the data properly\. In your bucket, create a folder for the extracted sentiment results and a second folder for the extracted entities results\. You can create folders either with the Amazon S3 console or the AWS CLI\. 

### Upload the extracted files to Amazon S3 \(console\)<a name="tutorial-reviews-tables-upload-console"></a>

In your S3 bucket, create one folder for the extracted sentiment results file and one folder for the entities results file\. Then, upload the extracted results files to their respective folders\.

**To upload the extracted files to Amazon S3 \(console\)**

1. Open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In **Buckets**, choose your bucket and then choose **Create folder**\.

1. For the new folder name, enter `sentiment-results` and choose **Save**\. This folder will contain the extracted sentiment output file\.

1. In your bucket's **Overview** tab, from the list of bucket contents, choose the new folder `sentiment-results`\. Choose **Upload**\.

1. Choose **Add files**, choose the `sentiment-output` file from your local computer, and then choose **Next**\.

1. Leave the options for **Manage users**, **Access for other AWS account**, and **Manage public permissions** as the defaults\. Choose **Next**\.

1. For **Storage class**, choose **Standard**\. Leave the options for **Encryption**, **Metadata**, and **Tag** as the defaults\. Choose **Next**\.

1. Review the upload options and then choose **Upload**\.

1. Repeat steps 1\-8 to create a folder called `entities-results`, and upload the `entities-output` file to it\.

### Upload the extracted files to Amazon S3 \(AWS CLI\)<a name="tutorial-reviews-tables-upload-cli"></a>

You can create a folder in your S3 bucket while uploading a file with the `cp` command\. 

**To upload the extracted files to Amazon S3 \(AWS CLI\)**

1. Create a sentiment folder and upload your sentiment file to it by running the following command\. Replace `path/` with the local path to your extracted sentiment output file\.

   ```
   aws s3 cp path/sentiment-output s3://DOC-EXAMPLE-BUCKET/sentiment-results/
   ```

1. Create an entities output folder and upload your entities file to it by running the following command\. Replace `path/` with the local path to your extracted entities output file\.

   ```
   aws s3 cp path/entities-output s3://DOC-EXAMPLE-BUCKET/entities-results/
   ```

## Load the data into an AWS Glue Data Catalog<a name="tutorial-reviews-tables-crawler"></a>

To get the results into a database, you can use an AWS Glue *crawler*\. An AWS Glue *crawler* scans files and discovers the schema of the data\. It then arranges the data in tables in an AWS Glue Data Catalog \(a serverless database\)\. You can create a crawler with the AWS Glue console or the AWS CLI\.

### Load the data into an AWS Glue Data Catalog \(console\)<a name="tutorial-reviews-tables-crawler-console"></a>

Create an AWS Glue crawler that scans your `sentiment-results` and `entities-results` folders separately\. A new IAM role for AWS Glue gives the crawler permission to access your S3 bucket\. You create this IAM role while setting up the crawler\.

**To load the data into an AWS Glue Data Catalog \(console\)**

1. Ensure that you're in a Region which supports AWS Glue\. If you're in another Region, in the navigation bar, choose a supported Region from the **Region selector**\. For a list of Regions that support AWS Glue, see the [Region Table](http://aws.amazon.com/about-aws/global-infrastructure/regional-product-services/) in the *Global Infrastructure Guide*\.

1. Open the AWS Glue console at [https://console\.aws\.amazon\.com/glue/](https://console.aws.amazon.com/glue/)\.

1. In the navigation pane, choose **Crawlers** and then choose **Add crawler**\.

1. For **Crawler name**, enter `comprehend-analysis-crawler` and then choose **Next**\.

1. For **Crawler source type**, choose **Data stores** and then choose **Next**\.

1. For **Add a data store**, do the following:

   1. For **Choose a data store**, choose **S3**\.

   1. Leave **Connection** blank\.

   1. For **Crawl data in**, choose **Specified path in my account**\.

   1. For **Include path**, enter the full S3 path of the sentiment output folder: `s3://DOC-EXAMPLE-BUCKET/sentiment-results`\.

   1. Choose **Next**\.

1. For **Add another data store**, choose **Yes** and then choose **Next**\. Repeat Step 6, but enter the full S3 path of the entities output folder: `s3://DOC-EXAMPLE-BUCKET/entities-results`\.

1. For **Add another data store**, choose **No** and then choose **Next**\.

1. For **Choose an IAM role**, do the following:

   1. Choose **Create an IAM role**\.

   1. For **IAM role**, enter `glue-access-role` and then choose **Next**\.

1. For **Create a schedule for this crawler**, choose **Run on demand** and choose **Next**\.

1. For **Configure the crawler's output**, do the following:

   1. For **Database**, choose **Add database**\.

   1. For **Database name**, enter `comprehend-results`\. This database will store your Amazon Comprehend output tables\.

   1. Leave the other options on their default settings and choose **Next**\.

1. Review the crawler information and then choose **Finish**\.

1. In the Glue console, in **Crawlers**, choose `comprehend-analysis-crawler` and choose **Run crawler**\. It can take a few minutes for the crawler to finish\.

### Load the data into an AWS Glue Data Catalog \(AWS CLI\)<a name="tutorial-reviews-tables-crawler-cli"></a>

Create an IAM role for AWS Glue that provides permission to access your S3 bucket\. Then, create a database in the AWS Glue Data Catalog\. Finally, create and run a crawler that loads your data into tables in the database\.

**To load the data into an AWS Glue Data Catalog \(AWS CLI\)**

1. To create an IAM role for AWS Glue, do the following:

   1. Save the following trust policy as a JSON document called `glue-trust-policy.json` on your computer\.

      ```
      {
        "Version": "2012-10-17",
        "Statement": [
          {
            "Effect": "Allow",
            "Principal": {
              "Service": "glue.amazonaws.com"
            },
            "Action": "sts:AssumeRole"
          }
        ]
      }
      ```

   1. To create an IAM role, run the following command\. Replace `path/` with your local computer's path to the JSON document\.

      ```
      aws iam create-role --role-name glue-access-role
      --assume-role-policy-document file://path/glue-trust-policy.json
      ```

   1. When the AWS CLI lists the Amazon Resource Number \(ARN\) for the new role, copy and save it to a text editor\.

   1. Save the following IAM policy as a JSON document called `glue-access-policy.json` on your computer\. The policy grants AWS Glue permission to crawl your results folders\.

      ```
      {
          "Version": "2012-10-17",
          "Statement": [
              {
                  "Effect": "Allow",
                  "Action": [
                      "s3:GetObject",
                      "s3:PutObject"
                  ],
                  "Resource": [
                      "arn:aws:s3:::DOC-EXAMPLE-BUCKET/sentiment-results*",
                      "arn:aws:s3:::DOC-EXAMPLE-BUCKET/entities-results*"
                  ]
              }
          ]
      }
      ```

   1. To create the IAM policy, run the following command\. Replace `path/` with your local computer's path to the JSON document\.

      ```
      aws iam create-policy --policy-name glue-access-policy
      --policy-document file://path/glue-access-policy.json
      ```

   1. When the AWS CLI lists the access policy's ARN, copy and save it to a text editor\.

   1. Attach the new policy to the IAM role by running the following command\. Replace `policy-arn` with the IAM policy ARN you copied in the previous step\.

      ```
      aws iam attach-role-policy --policy-arn policy-arn
      --role-name glue-access-role
      ```

   1. Attach the AWS managed policy `AWSGlueServiceRole` to your IAM role by running the following command\.

      ```
      aws iam attach-role-policy --policy-arn
      arn:aws:iam::aws:policy/service-role/AWSGlueServiceRole
      --role-name glue-access-role
      ```

1. Create an AWS Glue database by running the following command\.

   ```
   aws glue create-database 
   --database-input Name="comprehend-results"
   ```

1. Create a new AWS Glue crawler by running the following command\. Replace `glue-iam-role-arn` with the ARN of your AWS Glue IAM role\.

   ```
   aws glue create-crawler 
   --name comprehend-analysis-crawler
   --role glue-iam-role-arn 
   --targets S3Targets=[
   {Path="s3://DOC-EXAMPLE-BUCKET/sentiment-results"},
   {Path="s3://DOC-EXAMPLE-BUCKET/entities-results"}] 
   --database-name comprehend-results
   ```

1. Start the crawler by running the following command\.

   ```
   aws glue start-crawler --name comprehend-analysis-crawler
   ```

   It can take a few minutes for the crawler to finish\.

## Prepare the data for analysis<a name="tutorial-reviews-tables-prep"></a>

Now you have a database populated with the Amazon Comprehend results\. However, the results are nested\. To unnest them, you run a few SQL statements in Amazon Athena\. Amazon Athena is an interactive query service that makes it easy to analyze data in Amazon S3 using standard SQL\. Athena is serverless, so there is no infrastructure to manage and it has a pay\-per\-query pricing model\. In this step, you create new tables of cleaned data that you can use for analysis and visualization\. You use the Athena console to prepare the data\.

**To prepare the data**

1. Open the Athena console at [https://console\.aws\.amazon\.com/athena/](https://console.aws.amazon.com/athena/home)\.

1. In the query editor, choose **Settings**, then choose **Manage**\.

1. For **Location of query results**, enter `s3://DOC-EXAMPLE-BUCKET/query-results/`\. This creates a new folder called `query-results` in your bucket that stores the output of the Amazon Athena queries you run\. Choose **Save**\.

1. In the query editor, choose **Editor**\.

1. For **Database**, choose the AWS Glue database `comprehend-results` that you created\.

1. In the **Tables** section, you should have two tables called `sentiment_results` and `entities_results`\. Preview the tables to make sure that the crawler loaded the data\. In each table’s options \(the three dots next to the table name\), choose **Preview table**\. A short query runs automatically\. Check the **Results** pane to ensure that the tables contain data\.
**Tip**  
If the tables don’t have any data, try checking the folders in your S3 bucket\. Make sure that there is one folder for entities results and one folder for sentiment results\. Then, try running a new AWS Glue crawler\.

1. To unnest the `sentiment_results` table, enter the following query in the **Query editor** and choose **Run**\.

   ```
   CREATE TABLE sentiment_results_final AS
   SELECT file, line, sentiment,
   sentimentscore.mixed AS mixed,
   sentimentscore.negative AS negative,
   sentimentscore.neutral AS neutral,
   sentimentscore.positive AS positive
   FROM sentiment_results
   ```

1. To begin unnesting the entities table, enter the following query in the **Query editor** and choose **Run**\.

   ```
   CREATE TABLE entities_results_1 AS
   SELECT file, line, nested FROM entities_results
   CROSS JOIN UNNEST(entities) as t(nested)
   ```

1. To finish unnesting the entities table, enter the following query in the **Query editor** and choose **Run query**\.

   ```
   CREATE TABLE entities_results_final AS
   SELECT file, line,
   nested.beginoffset AS beginoffset,
   nested.endoffset AS endoffset,
   nested.score AS score,
   nested.text AS entity,
   nested.type AS category
   FROM entities_results_1
   ```

Your `sentiment_results_final` table should look like the following, with columns named **file**, **line**, **sentiment**, **mixed**, **negative**, **neutral**, and **positive**\. The table should have one value per cell\. The **sentiment** column describes the most likely overall sentiment of a particular review\. The **mixed**, **negative**, **neutral**, and **positive** columns give scores for each type of sentiment\.

![\[Screenshot of the sentiment output table in Athena.\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/tutorial-reviews-sentiment-table.png)

Your `entities_results_final` table should look like the following, with columns named **file**, **line**, **beginoffset**, **endoffset**, **score**, **entity**, and **category**\. The table should have one value per cell\. The **score** column indicates Amazon Comprehend's confidence in the **entity** it detected\. The **category** indicates what kind of entity Comprehend detected\.

![\[Screenshot of the entities output table in Athena.\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/tutorial-reviews-entities-table.png)

Now that you have the Amazon Comprehend results loaded into tables, you can visualize and extract meaningful insights from the data\.