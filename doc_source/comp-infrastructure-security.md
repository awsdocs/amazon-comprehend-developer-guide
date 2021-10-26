# Infrastructure Security in Amazon Comprehend<a name="comp-infrastructure-security"></a>

As a managed service, Amazon Comprehend adheres to the [AWS Best Practices for Security, Identity, and Compliance](http://aws.amazon.com/architecture/security-identity-compliance/)\.

To access Amazon Comprehend through the network, you use AWS published API calls\. Clients must support Transport Layer Security \(TLS\) 1\.0 or later\. We recommend TLS 1\.2 or later\. Clients must also support cipher suites with perfect forward secrecy \(PFS\), such as Ephemeral Diffie\-Hellman \(DHE\) or Elliptic Curve Ephemeral Diffie\-Hellman \(ECDHE\)\. Most modern systems, such as Java 7 and later, support these modes\.

Additionally, requests must be signed by using an access key ID and a secret access key that is associated with an AWS Identity and Access Management \(IAM\) principal\. Or you can use the [AWS Security Token Service](https://docs.aws.amazon.com/STS/latest/APIReference/Welcome.html) \(AWS STS\) to generate temporary security credentials to sign requests\.