# 🛒 Order Processing Project - AWS Step Function

## Overview
A lightweight, serverless order workflow using API Gateway, Lambda, Step Functions, SES and DynamoDB. It receives order data via an API, processes the request in sequence (create, pay, confirm), and logs everything efficiently.

## Architecture

The system follows a serverless event-driven architecture using AWS managed services.

### Workflow Overview
1. Client/API Gateway triggers the `stateMachine` Lambda with order details using a RESTful API.
2. This Lambda initiates the Step Function, passing the payload.

  ![img](Assignment_images_3/start_step_func.png)
  ![img](Assignment_images_3/start_step_func_2.png)

### Step Function Orchestration
The Step Function (`OrderProcessorStateMachine`) coordinates the following steps:

- `ValidateOrder` → Validates order inputs.
  
  ![img](Assignment_images_3/valid_order.png)

- `UpdateInventory` → Updates product stock in DynamoDB.
 
  ![img](Assignment_images_3/update_inv.png)

- `CreateOrder` → Persists the order data in DynamoDB.

  ![img](Assignment_images_3/create_order.png)

- `ProcessPayment` → Simulates payment logic.

  ![img](Assignment_images_3/process_payment.png)

- `SendConfirmation` → Sends email via AWS SES.
 
  ![img](Assignment_images_3/send_email.png)

- `handleFailure` → Handles any failure across the steps.

  ![img](Assignment_images_3/handle_error.png)
  ![img](Assignment_images_3/handle_error_2.png)

### AWS Services Involved
**API Gateway (REST API)** Entry point for HTTP requests using RESTful endpoints.

  ![img](Assignment_images_3/api_gateway.png)

**Lambda:** Handles each functional unit.

**Step Function:** Orchestrates workflow.

**DynamoDB:** Stores order and inventory data.

   ![img](Assignment_images_3/dynamo_db.png)
   ![img](Assignment_images_3/dynamo_db2.png)

**SES:** Sends confirmation emails.

   ![img](Assignment_images_3/SES.png)

### Postman URL Test

  ![img](Assignment_images_3/result_postman.png)

### Result

  ![img](Assignment_images_3/step_func.png)

### Benefits
- Modular microservices design

- Clear separation of concerns

- Easy debugging and monitoring with Step Function console

- Scalable and extensible architecture

## Conclusion
This serverless order processing system uses AWS Step Functions and Lambda for a scalable, event-driven architecture. By breaking the workflow into modular Lambda functions for tasks like order creation, payment processing, and failure handling, it ensures better maintainability and reusability. Step Functions orchestrate tasks with minimal effort, handling retries, failures, and transitions. This design enhances reliability, performance, and reduces operational complexity, making it a solid foundation for further extensions like notifications or analytics.


