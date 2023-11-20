# Introduction Pitch :
- Iguazu : `E-GUA-ZU`
- Problems : 
	- ad-hoc pipelines no platform 
	- lag in data -> business decisions were being made on old data 
	- streaming data -> reporting adverse event  
	- heterogeneous data sources 

<!------------------------------------------------------------------------------------------>
# Research Work 

- Spark : Distributed in-memory big-data processing 
- Kafka : Messaging Queue (Kinesis)
- Snowflake : Data Warehouse 
- Flink : 
- S3 : Data Lake 

## Workflow Design 

- **Apache Airflow**: Apache Airflow is an open-source platform for orchestrating and scheduling workflows. It provides a rich set of features for managing dependencies, retrying failed tasks, and monitoring job execution. Airflow uses Python for defining workflows and offers a web-based UI for configuration and monitoring.

- You can use **Amazon Lambda** to schedule and execute batch processing tasks. 
	- Amazon Lambda is a serverless compute service provided by Amazon Web Services (AWS), which allows you to run code without provisioning or managing servers.
	- Here's how you can utilize Amazon Lambda for scheduling batch processing:
		1. Create Lambda Functions: Write the code for your batch processing tasks as individual Lambda functions. Each Lambda function should represent a specific task or job that needs to be executed.
		2. Define Scheduling Logic: Determine the scheduling logic for your batch processing tasks. This can be based on a fixed schedule (e.g., every hour, daily, weekly) or triggered by specific events or external triggers.
		3. Set up Event Sources: Configure event sources for your Lambda functions to trigger them based on the desired schedule. AWS provides various event sources such as Amazon CloudWatch Events, AWS Step Functions, Amazon S3 events, or custom event sources using AWS SDKs or APIs.
		4. Configure Lambda Triggers: Connect the event sources to the Lambda functions by configuring the appropriate triggers. This ensures that your batch processing tasks are automatically triggered based on the defined schedule or events.
		5. Handle Dependencies: If your batch processing tasks have dependencies or need to be executed in a specific order, you can implement the logic within your Lambda functions or use AWS Step Functions to orchestrate the workflow.
		6. Monitoring and Error Handling: Implement appropriate logging and error handling mechanisms within your Lambda functions to track the execution status, handle failures, and retry failed tasks if necessary. You can leverage AWS CloudWatch logs and metrics for monitoring and troubleshooting.
	- Using Amazon Lambda for batch processing scheduling offers several benefits, such as automatic scaling, pay-as-you-go pricing, and reduced operational overhead. It allows you to focus on writing the task logic while AWS takes care of managing the infrastructure and scaling resources as needed.
	- Remember to consider the execution time limits and resource constraints imposed by Lambda functions when designing your batch processing tasks.

- Miscs : 
	- [Database vs Data Warehouse vs Data Lake | What is the Difference?](https://www.youtube.com/@AlexTheAnalyst)


