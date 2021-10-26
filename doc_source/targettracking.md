# Target Tracking<a name="targettracking"></a>

Setting up target tracking so that endpoint capacity is automatically adjusted based on usage\. In this example, the provisioned capacity is automatically adjusted so that the utilized capacity is always 70% of the provisioned capacity\. This allows for temporary surges in use\. For more information, see [Target Tracking Scaling Policies for Application Auto Scaling](https://docs.aws.amazon.com/autoscaling/application/userguide/application-auto-scaling-target-tracking.html)\.

**Note**  
 All of the following examples are formatted for Unix, Linux, and macOS\. For Windows, replace the backslash \(\\\) Unix continuation character at the end of each line with a caret \(^\)\.

**To Set Up Target Tracking**

1. 

   ```
   aws application-autoscaling register-scalable-target \
       --service-namespace comprehend \
       --region region \
       --resource-id endpoint ARN \
       --scalable-dimension comprehend:document-classifier-endpoint:DesiredInferenceUnits \
       --min-capacity 1 \
       --max-capacity 1
   ```

1. 

   ```
   aws application-autoscaling describe-scalable-targets \
       --service-namespace comprehend \
       --region region \
       --resource-id endpoint ARN
   ```

1. PutScalingPolicy: Create a scaling policy to dynamically change the provisioned capacity based on the consumed capacity\. In this case, the provisioned capacity is adjusted such that consumed capacity is always 70% of provisioned capacity\. The scaling policy is stored in a text file called `config.json`

   ```
   aws application-autoscaling put-scaling-policy \
       --service-namespace comprehend \
       --region region \
       --scalable-dimension comprehend:document-classifier-endpoint:DesiredInferenceUnits \
       --resource-id endpoint ARN \
       --policy-name TestPolicy \
       --policy-type TargetTrackingScaling \
       --target-tracking-scaling-policy-configuration file://config.json
   ```

   The config\.json file should consist of the following code:

   ```
   cat config.json
     {
     "TargetValue": 70,
     "PredefinedMetricSpecification": 
     {
     "PredefinedMetricType": "ComprehendInferenceUtilization"
     }
     }
   ```

**To remove target tracking**

1. DeleteScalingPolicy: Removing a scaling policy\.

   ```
   aws application-autoscaling delete-scaling-policy \
       --service-namespace comprehend \
       --region region \
       --scalable-dimension comprehend:document-classifier-endpoint:DesiredInferenceUnits \
       --resource-id endpoint ARN \
       --service-namespace comprehend
   ```

1. DeregisterScalableTarget: Deregistering the scalable target so that autoscaling no longer applies to it\.

   ```
   aws application-autoscaling deregister-scalable-target \
       --service-namespace comprehend \
       --region region \
       --resource-id endpoint ARN \
       --scalable-dimension comprehend:document-classifier-endpoint:DesiredInferenceUnits
   ```