# Scheduled scaling<a name="ScheduledScaling"></a>

With scheduled scaling, you can adjust endpoint provisioning to fit your capacity needs on a specified schedule\. Scheduled scaling automatically adjusts the number of inference units to accommodate surges of use at specific times\. You can use scheduled scaling for document classification endpoints and entity recognizer endpoints\. For additional information about scheduled scaling, see [Scheduled scaling for Application Auto Scaling](https://docs.aws.amazon.com/autoscaling/application/userguide/application-auto-scaling-scheduled-scaling.html)\.

**Note**  
The following examples are formatted for Unix, Linux, and macOS\. For Windows, replace the backslash \(\\\) Unix continuation character at the end of each line with a caret \(^\)\.

## Setting up scheduled scaling<a name="setup-scheduled-scaling"></a>

To set up scheduled scaling for an endpoint, you use AWS CLI commands to register a scalable target and then create a scheduled action\. The scalable target defines inference units as the resource used to adjust endpoint provisioning, and the scheduled action controls the auto scaling of the provisioned capacity at specific times\.

**To set up scheduled scaling**

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

1. Create a scheduled action\. The following examples create a scheduled action to automatically adjust the provisioned capacity every day at 12:00 UTC with a minimum of 2 inference units and a maximum of 5 inference units\. For more information about chronological expressions and scheduled scaling, see [Schedule expressions](https://docs.aws.amazon.com/AmazonCloudWatch/latest/events/ScheduledEvents.html)\. 

   For a document classification endpoint, use the following AWS CLI command:

   ```
   aws application-autoscaling put-scheduled-action \
       --service-namespace comprehend \
       --resource-id arn:aws:comprehend:region:account-id:document-classifier-endpoint/name \
       --scalable-dimension comprehend:document-classifier-endpoint:DesiredInferenceUnits \
       --scheduled-action-name TestScheduledAction \
       --schedule "cron(0 12 * * ? *)" \
       --scalable-target-action MinCapacity=2,MaxCapacity=5
   ```

   For an entity recognizer endpoint, use the following AWS CLI command:

   ```
   aws application-autoscaling put-scheduled-action \
       --service-namespace comprehend \
       --resource-id arn:aws:comprehend:region:account-id:entity-recognizer-endpoint/name \
       --scalable-dimension comprehend:entity-recognizer-endpoint:DesiredInferenceUnits \
       --scheduled-action-name TestScheduledAction \
       --schedule "cron(0 12 * * ? *)" \
       --scalable-target-action MinCapacity=2,MaxCapacity=5
   ```

## Removing scheduled scaling<a name="remove-scheduled-scaling"></a>

To remove scheduled scaling for an endpoint, you use AWS CLI commands to delete the scheduled action and then deregister the scalable target\.

**To remove scheduled scaling**

1. Delete the scheduled action\. The following examples delete a specified scheduled action\.

   For a document classification endpoint, use the following AWS CLI command:

   ```
   aws application-autoscaling delete-scheduled-action \
       --service-namespace comprehend \
       --resource-id arn:aws:comprehend:region:account-id:document-classifier-endpoint/name \
       --scalable-dimension comprehend:document-classifier-endpoint:DesiredInferenceUnits \
       --scheduled-action-name TestScheduledAction
   ```

   For an entity recognizer endpoint, use the following AWS CLI command:

   ```
   aws application-autoscaling delete-scheduled-action \
       --service-namespace comprehend \
       --resource-id arn:aws:comprehend:region:account-id:entity-recognizer-endpoint/name \
       --scalable-dimension comprehend:entity-recognizer-endpoint:DesiredInferenceUnits \
       --scheduled-action-name TestScheduledAction
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