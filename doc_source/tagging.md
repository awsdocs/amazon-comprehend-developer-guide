# Tagging your resources<a name="tagging"></a>

A tag is a key\-value pair that you can add to an Amazon Comprehend resource as metadata\. You can use tags on **Analysis jobs**, **Custom classification** models, **Custom entity recognition** models, and **endpoints**\. Tags have two major functions: organizing your resources and providing tag\-based access control\.

To organize your resources with tags, you could add the tag key 'Department' and tag values ‘Sales’ or ‘Legal'\. You can then search and filter for resources that are pertinent to your company's legal department\.

To provide tag\-based access control, create IAM policies with permissions based on tags\. A policy can allow or disallow an operation based on the tags provided in your request \(request\-tags\) or tags associated with the resource you're calling \(resource\-tags\)\. For more information on using tags with IAM, see [Controlling access using tags](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_tags.html) in the *IAM User Guide*\.

Considerations for using tags with Amazon Comprehend:
+ You can add up to 50 tags per resource, and tags can be added at the time you create the resource, or retroactively\.
+  A tag *key* is a required field but a tag *value* is optional\.
+ Tags do not have to be unique between resources, but a given resource cannot have duplicate tag keys\.
+ Tag keys and values are case sensitive\.
+ A tag key can have a maximum of 127 characters; a tag value can have a maximum of 255 characters\.
+ The '`aws:`' prefix is reserved for AWS use; you cannot add, edit, or delete tags whose key begins with `aws:`\. These tags don't count against your tags\-per\-resource limit of 50\.

**Note**  
If you plan to use your tagging schema across multiple AWS services and resources, remember that other services may have different requirements for allowed characters\.

**Topics**
+ [Tagging a new resource](tagging-newtags.md)
+ [Viewing, editing, and deleting tags associated with a resource](tagging-existingtags.md)