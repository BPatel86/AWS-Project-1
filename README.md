# AWS-Project-1

# Serverless Architecture for Scalable Cleaning Supplies E-commerce Platform

This project demonstrates a **serverless architecture** built on AWS for a customer who sells cleaning supplies. The business experiences frequent **spikes in website traffic**, so the solution is designed to **automatically scale in and out** based on demand. Additionally, the application components are **fully decoupled**, ensuring flexibility, scalability, and maintainability.

---

## 🏗️ Architecture Overview

The solution leverages the following AWS services:

- **API Gateway** – Provides a RESTful API endpoint to initiate the process.
- **Amazon SQS** – Queues incoming API requests for decoupled processing.
- **AWS Lambda (1st Function)** – Consumes SQS messages and writes entries to DynamoDB.
- **Amazon DynamoDB** – Stores data with millisecond latency and supports DynamoDB Streams.
- **AWS Lambda (2nd Function)** – Triggered by DynamoDB Streams to process new records.
- **Amazon SNS** – Sends email notifications based on new database records.

---

## 🔁 Flow Description

1. A client sends a POST request to the **API Gateway**.
2. API Gateway places the request message into the **Amazon SQS** queue.
3. The **first Lambda function** (triggered by SQS) processes the message and writes a new entry to **DynamoDB**.
4. **DynamoDB Streams** detects the new item and triggers the **second Lambda function**.
5. The second function forwards the data to **Amazon SNS**.
6. **Amazon SNS** sends an **email notification** to a subscribed address.
   
---

## 🧠 Key Learnings

Through building this architecture, the following AWS concepts and best practices were applied:

- Creating and assigning **IAM policies and roles** to secure AWS resources.
- Building a **DynamoDB table** to persist application data.
- Using **Amazon SQS** to decouple services and handle varying workloads.
- Writing **Lambda functions** to handle logic between services.
- Enabling **DynamoDB Streams** to capture data changes in near real time.
- Using **Amazon SNS** for email-based alerting and notifications.
- Creating a **REST API** with API Gateway for frontend/backend communication.
  
---
## 🖼️ Architecture Diagram (Optional)
 ![image](https://github.com/user-attachments/assets/237f9a28-1bfe-4ff8-ad57-20bbe9adc87d)

 ---

## 📌 Conclusion

This serverless architecture demonstrates how to build **resilient, scalable, and decoupled applications** using AWS services. It is ideal for businesses with **fluctuating demand** and a need for **rapid deployment without server management**.

---

