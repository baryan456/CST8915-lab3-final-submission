# CST8915 Lab 3 – Full-Stack Cloud-Native Development

## Student Information

- **Name:** Aryan Banoth
- **Student ID:** 041293006
- **Course:** CST8915 – Full-stack Cloud-native Development

## YouTube Demo Video

[Watch the Lab 3 Demo Video](https://youtu.be/OTgnC7xk5DU)

## Lab overview
The goal of this lab was to deploy the Algonquin Pet Store microservices on Azure and demonstrate communication between the Store Front, Product Service, Order Service, and RabbitMQ.

The Product Service was rewritten from Rust to Python and deployed to Azure Web App Service. The Order Service was deployed to Azure Web App Service and connected to RabbitMQ running on an Azure Virtual Machine.

Due to the regional limitation on the Azure Student account, Azure Static Web Apps could not be used for the Store Front.


## 4. Application Architecture

```text
                         Internet
                            |
                            v
              +---------------------------+
              |     Store Front VM        |
              |      Vue.js + Nginx       |
              |       |
              +-------------+-------------+
                            |
                 +----------+----------+
                 |                     |
                 v                     v
      +--------------------+   +--------------------+
      |  Product Service   |   |   Order Service    |
      |  Azure Web App     |   |   Azure Web App     |
      |    |   |  |
      +--------------------+   +---------+----------+
                                         |
                                         v
                              +----------------------+
                              |     RabbitMQ VM      |
                              |      order_queue     |
                              +----------------------+
```                        

## Reflection Questions

### 1. What challenges did you encounter when configuring environment variables in the GitHub Actions workflow?

One challenge was configuring the Store Front to use the deployed Azure service URLs instead of the local development URLs. The environment variables need to point to the Azure Web App URLs so that the Store Front can communicate with the deployed Product Service and Order Service. In this lab, Azure Static Web Apps was unavailable because of the regional limitation on my Azure Student account, so the Store Front was deployed on an Azure VM instead.

### 2. How does deploying microservices on Azure Web App Service differ from running them locally?

When running locally, the microservices use localhost addresses and local ports, and they are started directly from the development environment. With Azure Web App Service, the microservices are deployed as cloud applications and require configuration such as environment variables, startup commands, dependencies, networking, and deployment settings. Azure also provides public URLs for accessing the deployed services.

### 3. Why is it important to use environment variables for configurations in a cloud environment?

Environment variables keep configuration separate from the application source code. Cloud applications can have different URLs, connection strings, ports, and other configuration values between development and production. Using environment variables makes the application easier to configure and deploy without changing the source code and helps avoid hard-coding configuration values.

## Service Repositories

### Order Service

https://github.com/baryan456/CST8915-lab3-orderservice

### Product Service

https://github.com/baryan456/CST8915-Lab-3---Product-Service

### Store Front

https://github.com/baryan456/CST8915-lab3-storefront

## Note

Azure Static Web Apps was unavailable due to the regional limitation on my Azure Student account.
