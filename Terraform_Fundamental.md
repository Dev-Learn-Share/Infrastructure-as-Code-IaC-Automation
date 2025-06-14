
**Terraform**

Terraform is an open-source Infrastructure as Code (IaC) tool developed by HashiCorp. 
It is an IAC tool that allows you to build, change and version infrastructure safely and efficitently.

It allows users to define and provision infrastructure resources in a **consistent, repeatable manner using a high-level configuration** language known as HashiCorp Configuration Language (HCL)

**Terraform Structure ** widely-used and highly recommended structure for organizing a Terraform project. While Terraform technically combines all .tf files in a directory into a single configuration, splitting them by function makes the code much easier to read, manage, and scale.

Here’s a breakdown of that standard three-file structure:

-----------------------------------------------------------------------------------------------------

**main.tf 🏗️**
This file is the heart of your configuration. It contains the primary set of resources you intend to create, manage, or data sources you need to query. Think of it as the main execution file where you define what infrastructure will be built.

**Providers**: Configuration for the cloud or service provider (e.g., AWS, Azure, Google Cloud).
**Resources**: The core infrastructure components like virtual machines, databases, networks, etc.
**Data Sources**: Lookups to fetch information from the provider (e.g., finding the latest machine image AMI).

-----------------------------------------------------------------------------------------------------

**variables.tf 📝**

This file acts as a central place to declare all the input variables for your project. Declaring variables here makes your configuration flexible and reusable without hard-coding values.

**Purpose** : To define the "parameters" or "inputs" your configuration accepts, like an instance type, a region, or a list of port numbers.

**Best Practice** : Every variable should have a type and a description. Adding a default value makes it optional.

-----------------------------------------------------------------------------------------------------

**outputs.tf 📤** 

This file defines the output values of your infrastructure. After Terraform creates your resources, outputs are used to display useful or important information to the user or to pass data to other Terraform workspaces.

**Purpose**: To extract and display valuable information from your resources once they are created.
Examples: The public IP address of a web server, the connection string for a database, or the ARN of an S3 bucket.

-----------------------------------------------------------------------------------------------------