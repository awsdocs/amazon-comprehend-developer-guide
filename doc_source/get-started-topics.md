# Topic Modeling<a name="get-started-topics"></a>

 To determine the topics in a document set, use the [StartTopicsDetectionJob](API_StartTopicsDetectionJob.md) to start an asynchronous job\. You can monitor topics in documents written in English or Spanish\.

**Topics**
+ [Before You Start](#topics-before)
+ [Topic Modeling Using the AWS Command Line Interface](#topics-cli)
+ [Topic Modeling Using the AWS SDK for Java](#topic-java)
+ [Topic Modeling Using the AWS SDK for Python \(Boto\)](#topic-python)
+ [Topic Modeling Using the AWS SDK for \.NET](#topic-csharp)

## Before You Start<a name="topics-before"></a>

Before you start, make sure that you have:
+ **Input and output buckets**—Identify the Amazon S3 buckets that you want to use for input and output\. The buckets must be in the same region as the API that you are calling\.
+ **IAM service role**—You must have an IAM service role with permission to access your input and output buckets\. For more information, see [Role\-Based Permissions Required for Asynchronous Operations](access-control-managing-permissions.md#auth-role-permissions)\.

## Topic Modeling Using the AWS Command Line Interface<a name="topics-cli"></a>

The following example demonstrates using the `StartTopicsDetectionJob` operation with the AWS CLI

The example is formatted for Unix, Linux, and macOS\. For Windows, replace the backslash \(\\\) Unix continuation character at the end of each line with a caret \(^\)\.

```
aws comprehend start-topics-detection-job \
                --number-of-topics topics to return \
                --job-name "job name" \
                --region region \
                --cli-input-json file://path to JSON input file
```

For the `cli-input-json` parameter you supply the path to a JSON file that contains the request data, as shown in the following example\.

```
{
    "InputDataConfig": {
        "S3Uri": "s3://input bucket/input path",
        "InputFormat": "ONE_DOC_PER_FILE"
    },
    "OutputDataConfig": {
        "S3Uri": "s3://output bucket/output path"
    },
    "DataAccessRoleArn": "arn:aws:iam::account ID:role/data access role"
}
```

If the request to start the topic detection job was successful, you will receive the following response:

```
{
    "JobStatus": "SUBMITTED",
    "JobId": "job ID"
}
```

Use the [ListTopicsDetectionJobs](API_ListTopicsDetectionJobs.md) operation to see a list of the topic detection jobs that you have submitted\. The list includes information about the input and output locations that you used and the status of each of the detection jobs\. The example is formatted for Unix, Linux, and macOS\. For Windows, replace the backslash \(\\\) Unix continuation character at the end of each line with a caret \(^\)\.

```
aws comprehend list-topics-detection-jobs \-- region
```

You will get JSON similar to the following in response:

```
{
    "TopicsDetectionJobPropertiesList": [
        {
            "InputDataConfig": {
                "S3Uri": "s3://input bucket/input path", 
                "InputFormat": "ONE_DOC_PER_LINE"
            }, 
            "NumberOfTopics": topics to return, 
            "JobId": "job ID", 
            "JobStatus": "COMPLETED", 
            "JobName": "job name", 
            "SubmitTime": timestamp, 
            "OutputDataConfig": {
                "S3Uri": "s3://output bucket/output path"
            }, 
            "EndTime": timestamp
        },
        {
            "InputDataConfig": {
                "S3Uri": "s3://input bucket/input path", 
                "InputFormat": "ONE_DOC_PER_LINE"
            }, 
            "NumberOfTopics": topics to return, 
            "JobId": "job ID", 
            "JobStatus": "RUNNING", 
            "JobName": "job name", 
            "SubmitTime": timestamp, 
            "OutputDataConfig": {
                "S3Uri": "s3://output bucket/output path"
            }
        }        
    ]
}
```

You can use the [DescribeTopicsDetectionJob](API_DescribeTopicsDetectionJob.md) operation to get the status of an existing job\. The example is formatted for Unix, Linux, and macOS\. For Windows, replace the backslash \(\\\) Unix continuation character at the end of each line with a caret \(^\)\.

```
aws comprehend describe-topics-detection-job --job-id job ID 
```

You will get the following JSON in response:

```
{
    "TopicsDetectionJobProperties": {
        "InputDataConfig": {
            "S3Uri": "s3://input bucket/input path", 
            "InputFormat": "ONE_DOC_PER_LINE"
        }, 
        "NumberOfTopics": topics to return, 
        "JobId": "job ID", 
        "JobStatus": "COMPLETED", 
        "JobName": "job name", 
        "SubmitTime": timestamp, 
        "OutputDataConfig": {
            "S3Uri": "s3://output bucket/ouput path"
        }, 
        "EndTime": timestamp
    }
}
```

## Topic Modeling Using the AWS SDK for Java<a name="topic-java"></a>

The following Java program detects the topics in a document collection\. It uses the [StartTopicsDetectionJob](API_StartTopicsDetectionJob.md) operation to start detecting topics\. Next, it uses the [DescribeTopicsDetectionJob](API_DescribeTopicsDetectionJob.md) operation to check the status of the topic detection\. Finally, it calls [ListTopicsDetectionJobs](API_ListTopicsDetectionJobs.md) to show a list of all jobs submitted for the account\.

```
import com.amazonaws.auth.AWSCredentialsProvider;
import com.amazonaws.auth.DefaultAWSCredentialsProviderChain;                
import com.amazonaws.client.builder.AwsClientBuilder;
import com.amazonaws.services.comprehend.AmazonComprehend;
import com.amazonaws.services.comprehend.AmazonComprehendClientBuilder;
import com.amazonaws.services.comprehend.model.DescribeTopicsDetectionJobRequest;
import com.amazonaws.services.comprehend.model.DescribeTopicsDetectionJobResult;
import com.amazonaws.services.comprehend.model.InputDataConfig;
import com.amazonaws.services.comprehend.model.InputFormat;
import com.amazonaws.services.comprehend.model.ListTopicsDetectionJobsRequest;
import com.amazonaws.services.comprehend.model.ListTopicsDetectionJobsResult;
import com.amazonaws.services.comprehend.model.StartTopicsDetectionJobRequest;
import com.amazonaws.services.comprehend.model.StartTopicsDetectionJobResult;
 
public class App 
{
    public static void main( String[] args )
    {
        // Create credentials using a provider chain. For more information, see
        // https://docs.aws.amazon.com/sdk-for-java/v1/developer-guide/credentials.html
         AWSCredentialsProvider awsCreds = DefaultAWSCredentialsProviderChain.getInstance();
 
        AmazonComprehend comprehendClient =
            AmazonComprehendClientBuilder.standard()
                                         .withCredentials(awsCreds)
                                         .withRegion("region")
                                         .build();
                                         
        final String inputS3Uri = "s3://input bucket/input path";
        final InputFormat inputDocFormat = InputFormat.ONE_DOC_PER_FILE;
        final String outputS3Uri = "s3://output bucket/output path";
        final String dataAccessRoleArn = "arn:aws:iam::account ID:role/data access role";
        final int numberOfTopics = 10;
 
        final StartTopicsDetectionJobRequest startTopicsDetectionJobRequest = new StartTopicsDetectionJobRequest()
                .withInputDataConfig(new InputDataConfig()
                        .withS3Uri(inputS3Uri)
                        .withInputFormat(inputDocFormat))
                .withOutputDataConfig(new OutputDataConfig()
                        .withS3Uri(outputS3Uri))
                .withDataAccessRoleArn(dataAccessRoleArn)
                .withNumberOfTopics(numberOfTopics);
 
        final StartTopicsDetectionJobResult startTopicsDetectionJobResult = comprehendClient.startTopicsDetectionJob(startTopicsDetectionJobRequest);
 
        final String jobId = startTopicsDetectionJobResult.getJobId();
        System.out.println("JobId: " + jobId);
 
        final DescribeTopicsDetectionJobRequest describeTopicsDetectionJobRequest = new DescribeTopicsDetectionJobRequest()
                .withJobId(jobId);
 
        final DescribeTopicsDetectionJobResult describeTopicsDetectionJobResult = comprehendClient.describeTopicsDetectionJob(describeTopicsDetectionJobRequest);
        System.out.println("describeTopicsDetectionJobResult: " + describeTopicsDetectionJobResult);
 
        ListTopicsDetectionJobsResult listTopicsDetectionJobsResult = comprehendClient.listTopicsDetectionJobs(new ListTopicsDetectionJobsRequest());
        System.out.println("listTopicsDetectionJobsResult: " + listTopicsDetectionJobsResult);
 
    }
}
```

## Topic Modeling Using the AWS SDK for Python \(Boto\)<a name="topic-python"></a>

The following Python program detects the topics in a document collection\. It uses the [StartTopicsDetectionJob](API_StartTopicsDetectionJob.md) operation to start detecting topics\. Next, it uses the [DescribeTopicsDetectionJob](API_DescribeTopicsDetectionJob.md) operation to check the status of the topic detection\. Finally, it calls [ListTopicsDetectionJobs](API_ListTopicsDetectionJobs.md) to show a list of all jobs submitted for the account\.

```
import boto3
import json
from bson import json_util
 
comprehend = boto3.client(service_name='comprehend', region_name='region')
                
input_s3_url = "s3://input bucket/input path"
input_doc_format = "ONE_DOC_PER_FILE"
output_s3_url = "s3://output bucket/output path"
data_access_role_arn = "arn:aws:iam::account ID:role/data access role"
number_of_topics = 10
 
input_data_config = {"S3Uri": input_s3_url, "InputFormat": input_doc_format}
output_data_config = {"S3Uri": output_s3_url}
 
start_topics_detection_job_result = comprehend.start_topics_detection_job(NumberOfTopics=number_of_topics,
                                                                              InputDataConfig=input_data_config,
                                                                              OutputDataConfig=output_data_config,
                                                                              DataAccessRoleArn=data_access_role_arn)
 
print('start_topics_detection_job_result: ' + json.dumps(start_topics_detection_job_result))
 
job_id = start_topics_detection_job_result["JobId"]
 
print('job_id: ' + job_id)
 
describe_topics_detection_job_result = comprehend.describe_topics_detection_job(JobId=job_id)
 
print('describe_topics_detection_job_result: ' + json.dumps(describe_topics_detection_job_result, default=json_util.default))
 
list_topics_detection_jobs_result = comprehend.list_topics_detection_jobs()
 
print('list_topics_detection_jobs_result: ' + json.dumps(list_topics_detection_jobs_result, default=json_util.default))
```

## Topic Modeling Using the AWS SDK for \.NET<a name="topic-csharp"></a>

The following C\# program detects the topics in a document collection\. It uses the [StartTopicsDetectionJob](API_StartTopicsDetectionJob.md) operation to start detecting topics\. Next, it uses the [DescribeTopicsDetectionJob](API_DescribeTopicsDetectionJob.md) operation to check the status of the topic detection\. Finally, it calls [ListTopicsDetectionJobs](API_ListTopicsDetectionJobs.md) to show a list of all jobs submitted for the account\.

The \.NET example in this section uses the [AWS SDK for \.NET](https://docs.aws.amazon.com/sdk-for-net/latest/developer-guide/welcome.html)\. You can use the [AWS Toolkit for Visual Studio](https://docs.aws.amazon.com/AWSToolkitVS/latest/UserGuide/welcome.html) to develop AWS applications using \.NET\. It includes helpful templates and the AWS Explorer for deploying applications and managing services\. For a \.NET developer perspective of AWS, see the [AWS Guide for \.NET Developers](https://docs.aws.amazon.com/sdk-for-net/latest/developer-guide/welcome.html)\. 

```
using System;
using Amazon.Comprehend;
using Amazon.Comprehend.Model;

namespace Comprehend
{
    class Program
    {
        // Helper method for printing properties
        static private void PrintJobProperties(TopicsDetectionJobProperties props)
        {
            Console.WriteLine("JobId: {0}, JobName: {1}, JobStatus: {2}, NumberOfTopics: {3}\nInputS3Uri: {4}, InputFormat: {5}, OutputS3Uri: {6}",
                props.JobId, props.JobName, props.JobStatus, props.NumberOfTopics,
                props.InputDataConfig.S3Uri, props.InputDataConfig.InputFormat, props.OutputDataConfig.S3Uri);
        }

        static void Main(string[] args)
        {
            String text = "It is raining today in Seattle";

            AmazonComprehendClient comprehendClient = new AmazonComprehendClient(Amazon.RegionEndpoint.USWest2);

            String inputS3Uri = "s3://input bucket/input path";
            InputFormat inputDocFormat = InputFormat.ONE_DOC_PER_FILE;
            String outputS3Uri = "s3://output bucket/output path";
            String dataAccessRoleArn = "arn:aws:iam::account ID:role/data access role";
            int numberOfTopics = 10;

            StartTopicsDetectionJobRequest startTopicsDetectionJobRequest = new StartTopicsDetectionJobRequest()
            {
                InputDataConfig = new InputDataConfig()
                {
                    S3Uri = inputS3Uri,
                    InputFormat = inputDocFormat
                },
                OutputDataConfig = new OutputDataConfig()
                {
                    S3Uri = outputS3Uri
                },
                DataAccessRoleArn = dataAccessRoleArn,
                NumberOfTopics = numberOfTopics
            };

            StartTopicsDetectionJobResponse startTopicsDetectionJobResponse = comprehendClient.StartTopicsDetectionJob(startTopicsDetectionJobRequest);

            String jobId = startTopicsDetectionJobResponse.JobId;
            Console.WriteLine("JobId: " + jobId);

            DescribeTopicsDetectionJobRequest describeTopicsDetectionJobRequest = new DescribeTopicsDetectionJobRequest()
            {
                JobId = jobId
            };

            DescribeTopicsDetectionJobResponse describeTopicsDetectionJobResponse = comprehendClient.DescribeTopicsDetectionJob(describeTopicsDetectionJobRequest);
            PrintJobProperties(describeTopicsDetectionJobResponse.TopicsDetectionJobProperties);

            ListTopicsDetectionJobsResponse listTopicsDetectionJobsResponse = comprehendClient.ListTopicsDetectionJobs(new ListTopicsDetectionJobsRequest());
            foreach (TopicsDetectionJobProperties props in listTopicsDetectionJobsResponse.TopicsDetectionJobPropertiesList)
                PrintJobProperties(props);
        }
    }
}
```