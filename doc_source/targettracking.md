# Target tracking<a name="targettracking"></a>

With target tracking, you can adjust endpoint provisioning to fit your capacity needs based on usage\. The number of inference units automatically adjust so that the utilized capacity is within a target percentage of the provisioned capacity\. You can use target tracking to accommodate temporary surges of use for your document classification endpoints and entity recognizer endpoints\. For more information, see [Target tracking scaling policies for Application Auto Scaling](https://docs.aws.amazon.com/autoscaling/application/userguide/application-auto-scaling-target-tracking.html)\.

**Note**  
The following examples are formatted for Unix, Linux, and macOS\. For Windows, replace the backslash \(\\\) Unix continuation character at the end of each line with a caret \(^\)\.

## Setting up target tracking<a name="setup-target-tracking"></a>

To set up target tracking for an endpoint, you use AWS CLI commands to register a scalable target and then create a scaling policy\. The scalable target defines inference units as the resource used to adjust endpoint provisioning, and the scaling policy defines the metrics that control the auto scaling of the provisioned capacity\. 

**To set up target tracking**

1. Register a scalable target\. The following examples register a scalable target to adjust endpoint provisioning with a minimum capacity of 1 inference unit and a maximum capacity of 2 inference units\.

   For a document classification endpoint, use the following AWS CLI command:

   ```
   aws application-autoscaling register-scalable-target \
       --service-namespace comprehend \
       --resource-id arn:aws:comprehend:region:account-id:document-classifier-endpoint/name \
       --scalable-dimension comprehend:document-classifier-endpoint:DesiredInferenceUnits \
       --min-capacity 1 \
       --max-capacity 2
   ```

   For an entity recognizer endpoint, use the following AWS CLI command:

   ```
   aws application-autoscaling register-scalable-target \
       --service-namespace comprehend \
       --resource-id arn:aws:comprehend:region:account-id:entity-recognizer-endpoint/name \
       --scalable-dimension comprehend:entity-recognizer-endpoint:DesiredInferenceUnits \
       --min-capacity 1 \
       --max-capacity 2
   ```

1. To verify the registration of the scalable target, use the following AWS CLI command:

   ```
   aws application-autoscaling describe-scalable-targets \
       --service-namespace comprehend \
       --resource-id endpoint ARN
   ```

1. Create a target tracking configuration for the scaling policy and save the configuration in a file called `config.json`\. The following is an example of a target tracking configuration that automatically adjusts the number of inference units so that utilized capacity is always 70% of the provisioned capacity\.

   ```
   {
     "TargetValue": 70,
     "PredefinedMetricSpecification": 
     {
     "PredefinedMetricType": "ComprehendInferenceUtilization"
     }
   }
   ```

1. Create a scaling policy\. The following examples create a scaling policy based on the target tracking configuration defined in the `config.json` file\. 

   For a document classification endpoint, use the following AWS CLI command:

   ```
   aws application-autoscaling put-scaling-policy \
       --service-namespace comprehend \
       --resource-id arn:aws:comprehend:region:account-id:document-classifier-endpoint/name \
       --scalable-dimension comprehend:document-classifier-endpoint:DesiredInferenceUnits \
       --policy-name TestPolicy \
       --policy-type TargetTrackingScaling \
       --target-tracking-scaling-policy-configuration file://config.json
   ```

   For an entity recognizer endpoint, use the following AWS CLI command:

   ```
   aws application-autoscaling put-scaling-policy \
       --service-namespace comprehend \
       --resource-id arn:aws:comprehend:region:account-id:entity-recognizer-endpoint/name \
       --scalable-dimension comprehend:entity-recognizer-endpoint:DesiredInferenceUnits \
       --policy-name TestPolicy \
       --policy-type TargetTrackingScaling \
       --target-tracking-scaling-policy-configuration file://config.json
   ```

## Removing target tracking<a name="remove-target-tracking"></a>

To remove target tracking for an endpoint, you use AWS CLI commands to delete the scaling policy and then deregister the scalable target\.

**To remove target tracking**

1. Delete the scaling policy\. The following examples delete a specified scaling policy\.

   For a document classification endpoint, use the following AWS CLI command:

   ```
   aws application-autoscaling delete-scaling-policy \
       --service-namespace comprehend \
       --resource-id arn:aws:comprehend:region:account-id:document-classifier-endpoint/name \
       --scalable-dimension comprehend:document-classifier-endpoint:DesiredInferenceUnits \
       --policy-name TestPolicy \
   ```

   For an entity recognizer endpoint, use the following AWS CLI command:

   ```
   aws application-autoscaling delete-scaling-policy \
       --service-namespace comprehend \
       --resource-id arn:aws:comprehend:region:account-id:entity-recognizer-endpoint/name \
       --scalable-dimension comprehend:entity-recognizer-endpoint:DesiredInferenceUnits \
       --policy-name TestPolicy
   ```

1. Deregister the scalable target\. The following examples deregister a specified scalable target\.

   For a document classification endpoint, use the following AWS CLI command:

   ```
   aws application-autoscaling deregister-scalable-target \
       --service-namespace comprehend \
       --resource-id arn:aws:comprehend:region:account-id:document-classifier-endpoint/name \
       --scalable-dimension comprehend:document-classifier-endpoint:DesiredInferenceUnits
   ```

   For an entity recognizer endpoint, use the following AWS CLI command:

   ```
   aws application-autoscaling deregister-scalable-target \
       --service-namespace comprehend \
       --resource-id arn:aws:comprehend:region:account-id:entity-recognizer-endpoint/name \
       --scalable-dimension comprehend:entity-recognizer-endpoint:DesiredInferenceUnits
   ```