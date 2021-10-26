# Autoscaling with Endpoints<a name="comprehend-autoscaling"></a>

Besides manually adjusting the number of inference units with which you provision your endpoints, you can also use use autoscaling to automatically set your endpoint provisioning to fit your capacity needs\. 

Autoscaling is only available using the AWS CLI\.

There are two ways of setting autoscaling:
+ [Target Tracking](targettracking.md): setting autoscaling so that it will adjust endpoint capacity \(thenumber of inference units\) based on utilization of the endpoint\. 
+ [Scheduled Scaling](ScheduledScaling.md): setting autoscaling so that it will adjust endpoint capacity based on a specified schedule\.