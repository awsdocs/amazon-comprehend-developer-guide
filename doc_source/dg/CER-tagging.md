# Tagging Custom Entity Recognizers<a name="CER-tagging"></a>

A tag is a key\-value pair which can be added to a Amazon Comprehend resource as metadata\. 

Tags can be used for organizing your resources as well as helping you to search and filter by tag\. Using tag\-based access control can allow for finer control than API\-level control as well as more dynamic control than resource\-based access control\. IAM policies can be created that allow or disallow an operation based on tags provided in the request \(request\-tags\) or tags on the resource that is being operated on \(resource\-tags\)\. For more information on using IAM roles for this, [Controlling Access Using Tags](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_tags.html) in the *IAM User Guide*

For instance, you could add tags such as ‘Sales’ or ‘Legal' to different custom entity recognizers to break down documents into dynamic categories for your company\. 

Multiple tags can be added to an Amazon Comprehend resource, either when you create it, or later\. Up to 50 tags can be associated with each resource\.

Each tag key must be unique for a specific resource\. However, the same key can be used for different resources\. The tag value can be used to make the tag more specific, but is optional\.

The following options are available when using tags with Amazon Comprehend: 
+  [Tagging a resource when you originally create it](#tag-original-2) 
+ [Tagging a resource after it’s been created](#tag-existing-2) 
+ [Modifying an existing tag](#modify-tag-2) 
+ [Removing tags from a resource](#remove-tag-2) 
+ [Viewing all tags associated with a resource](#viewing-tags-2) 
+ [Tagging restrictions](#tag-restrictions-2) 

## Tagging a resource when you originally create it<a name="tag-original-2"></a>

When you want to add one or more tags to a custom entity recognizer when you originally create it, you can do this when training the recognizer\. 

**To tag a resource when creating it**

1. In the optional **Tags** section, enter the key\-value pair for your tag\. 
**Note**  
Remember the key must be unique for the given resource\. The value is optional\.  
![\[The optional Tags section.\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/tag-image-10.png)

1. Choose **Add tag** to associate the tag with your recognizer\. You can do this multiple times to add more than one tag\.

   Once you’ve added a tag, you can remove it before training the recognizer by choosing **Remove tag**\.

When using the APIs, you can do this using the CreateEntityRecognizer operation\. 

## Tagging a resource after it’s been created<a name="tag-existing-2"></a>

You can also easily add a tag to an existing custom entity recognizer using the resource list or the detail page for a specific recognizer\. 

**To add a tag to an existing custom entity recognizer**

1. On the Custom Entity Recognizer resource list, select the recognizer to which you want to add the tag, and then choose **Manage tags**\.  
![\[The Custom Entity Recognizer resource list.\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/tag-image-25-CER.png)

   Alternatively, choose **Manage tags** in the **Tags** section of a specific recognizer’s details page\.  
![\[The detail page.\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/tag-image-28.png)

1. Under **Tags**, enter the key\-value pair for your tag\. 
**Note**  
Remember the key must be unique for the given resource\. The value is optional\.  
![\[The Tag section.\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/tag-image-30.png)

1. Choose **Add tag** to associate your tag with the recognizer\. You can do this multiple times to add more than one tag\.

   Once you’ve added a tag, you can remove it before training the recognizer by choosing **Remove tag**\.

1. Choose **Save**\.

## Modifying an existing tag<a name="modify-tag-2"></a>

You can remove an existing using the resource list or the detail page for a specific resource\. 

**To modify an existing tag**

1. Under **Tags**, choose the tag you want to change and choose the X for the key or value box\. Enter the new key or value\.   
![\[Existing tags for a resource.\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/tag-image-31.png)

1. Make any additional changes desired to the tags\. 

1. Choose **Save**\.

## Removing tags from a resource<a name="remove-tag-2"></a>

You can remove a tag from an existing custom entity recognizer using the resource list or the detail pagefor a specific recognizer\. 

**To remove a tag from an existing custom entity recognizer**

1. On the Custom Entity Recognizer resource list, select the recognizer from which you want to remove the tag, and then choose **Manage tags**\.  
![\[The Custom Entity Recognizer resource list.\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/tag-image-25-CER.png)

   Alternatively, choose **Manage tags** in the **Tags** section of a specific recognizer’s details page\.   
![\[The detail page.\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/tag-image-28.png)

1. Next to the tag that you want to remove, choose **Remove tag**\.  
![\[Existing tags for a resource.\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/tag-image-31.png)

1. Choose **Save**\.

## Viewing all tags associated with a resource<a name="viewing-tags-2"></a>

**To view all tags associated with a specific resource**
+ On the Custom Entity Recognizer resource list, select the recognizer for which you want to view the tags, and then choose **Manage tags**\.

## Tagging restrictions<a name="tag-restrictions-2"></a>

The following basic restrictions apply to Custom Entity Recognizer tags:
+ The maximum number of tags per recognizer is 50\.
+ The maximum length of a tag key is 127 characters\.
+ The maximum length of a tag value is 255 characters\.
+ Tag keys and values are case sensitive\.
+ The `aws:` prefix is reserved for AWS use; you cannot add, edit, or delete tags whose key begins with `aws:`\. Tags that begin with `aws:` do not count against your tags\-per\-resource limit\.
+ If you plan to use your tagging schema across multiple services and resources, remember that other services may have different restrictions for allowed characters\. Refer to the documentation for that service\.