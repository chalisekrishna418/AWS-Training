# Application Integration

## Simple Notification Service (SNS)
- SNS provides message delivery from publishers to subscribers (also known as producers and consumers).
- Publishers communicate asynchronously with subscribers by sending messages to a topic, which is a logical access point and communication channel.
- You can consume the message by setting up subscriber endpoints such as Amazon Kinesis Data Firehose, Amazon SQS, AWS Lambda, HTTP, email, mobile push notifications, and mobile text messages (SMS).

## Simple Queue Service (SQS)
- It is a managed queueing service from AWS that can be useful to build decoupled distributed applications.
- Amazon SQS also offers dead-letter queues (DLQ).
- SQS Supports **standard and FIFO queues.**

**1. Standard Queues**
- Standard queues supports a nearly unlimited number of API calls per second, per API action. 
- Occasionally, messages are delivered in an order different from which they were sent.

**2. FIFO Queues**
- FIFO queues support up to 3,000 messages per second, each with a batch of 10 messages. This limit can be increased from AWS Quota service.
- The order in which messages are sent and received is strictly preserved.

## Reading Materials
- [AWSDocs- SNS](https://docs.aws.amazon.com/sns/latest/dg/welcome.html)
- [AWSDocs - SQS](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/welcome.html)
