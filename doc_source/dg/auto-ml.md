# Comprehend Custom<a name="auto-ml"></a>

Comprehend custom helps you meet your specific needs even if you don't have the skillset to build machine learning\-based NLP solutions\. Using automatic machine learning, or AutoML, Comprehend Custom builds customized NLP models on your behalf, using data you already have\. Training and calling custom comprehend models are both async \(batch\) operations\. 

Amazon Comprehend uses a proprietary, state\-of\-the\-art sequence tagging deep neural network model that powers the same Amazon Comprehend detect entities service to train your custom entity recognizer models\. In addition, we understand that acquiring training data could be costly\. To help customers build a highly accurate model with limited amount of data, Amazon Comprehend uses a technique called *transfer learning* to train your custom models based on an sophisticated general\-purpose entities recognition model that was pre\-trained with a large amount of data we collected from multiple domains\. Offline experiments have shown that transfer learning significantly improves custom entity recognizer model accuracy, especially when the amount of training data is small\.

**Topics**
+ [Custom Classification](how-document-classification.md)
+ [Custom Entity Recognition](custom-entity-recognition.md)