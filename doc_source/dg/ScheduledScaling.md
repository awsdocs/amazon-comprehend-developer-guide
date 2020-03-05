# Scheduled Scaling<a name="ScheduledScaling"></a>

Setting up scheduled scaling so that the endpoint capacity is adjusted on a given schedule to accommodate heavier or lighter usage of the endpoint\. For additional information on scheduled scaling, see [Scheduled Scaling for Application Auto Scaling](https://docs.aws.amazon.com/autoscaling/application/userguide/application-auto-scaling-scheduled-scaling.html)\.

**Note**  
 All of the following examples are formatted for Unix, Linux, and macOS\. For Windows, replace the backslash \(\\\) Unix continuation character at the end of each line with a caret \(^\)\.

**To set up scheduled scaling**

1. RegisterScalableTarget: Register Amazon Comprehend as a scalable target for AWS Auto Scaling\.

   ```
   aws application-autoscaling register-scalable-target \
       --service-namespace comprehend \
       --region region \
       --resource-id endpoint ARN \
       --scalable-dimension comprehend:document-classifier-endpoint:DesiredInferenceUnits \
       --min-capacity 1 \
       --max-capacity 3
   ```

1. PutScheduledAction: A scheduled action controls the min and max provisioned capacity within which the provisioned capacity can be scaled at a specific schedule\. In this case, we put a scheduled action to change the min and max capacity every day at 12:00 UTC to a min of 2 and a max of 5\. For more information on chronological expressions and scheduled scaling, see [Schedule Expressions](https://docs.aws.amazon.com/AmazonCloudWatch/latest/events/ScheduledEvents.html)\. 

   ```
   aws application-autoscaling put-scheduled-action \
       --service-namespace comprehend \
       --region region \
       --scheduled-action-name TestScheduledAction \
       --resource-id endpoint ARN \
       --scalable-dimension comprehend:document-classifier-endpoint:DesiredInferenceUnits \
       --schedule "cron(0 12 * * ? *)" \
       --scalable-target-action MinCapacity=2,MaxCapacity=5
   ```

**To remove an autoscaling scheduled action**

1. DeleteScheduledAction: Deleting the scheduled action\.

   ```
   aws application-autoscaling delete-scheduled-action \
       --service-namespace comprehend \
       --region region \
       --scheduled-action-name RemoveScheduledAction \
       --resource-id endpoint ARN \
       --scalable-dimension comprehend:document-classifier-endpoint:DesiredInferenceUnits
   ```

1. DeregisterScalableTarget: Deregistering the scalable target so that autoscaling no longer applies to it\.

   ```
   aws application-autoscaling deregister-scalable-target \
       --service-namespace comprehend \
       --region region \
       --resource-id endpoint ARN \
       --scalable-dimension comprehend:document-classifier-endpoint:DesiredInferenceUnits
   ```