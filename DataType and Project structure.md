**Directory structure** of  **Terraform project**, with accurate descriptions of each file:
projectname/
│
├── provider.tf         # Configures the provider block (e.g., AWS, Azure, GCP) and sets the region/profile/etc.
├── version.tf          # Specifies the required Terraform and provider versions to ensure compatibility.
├── backend.tf          # Configures the backend to manage the Terraform state (e.g., S3 for AWS, Azure Storage).
├── main.tf             # Main configuration file — defines resources like EC2 instances, VPCs, IAM roles, etc.
├── data.tf             # Declares data sources — used to fetch read-only information from existing infrastructure.
├── variables.tf        # Declares input variables with optional descriptions and types.
├── terraform.tfvars    # Provides concrete values for the input variables defined in variables.tf.
├── locals.tf           # Defines local variables (reusable expressions, concatenations, computed values).
├── outputs.tf          # Declares output values to display after execution (e.g., IP addresses, resource names).


✅ **Explanation of File Roles:**
  File	             Purpose
**provider.tf** -	Sets up the cloud provider (e.g., aws, azurerm) and authentication.
**version.tf**	Locks Terraform version and provider version for consistency.
**backend.tf**	Stores the state file remotely (S3, GCS, etc.) for collaboration and recovery.
**main.tf**	Central file to declare resources (like EC2, S3, etc.).
**data.tf**	Reads existing resources for use in your config (e.g., AMIs, VPCs).
**variables.tf**	Declares parameters for reuse and flexibility (region, instance_type).
**terraform.tfvars**	Supplies values to the variables declared in variables.tf.
**locals.tf**	Used for calculated values or clean code by avoiding repetitive logic.
**outputs.tf**	Prints key information post-deployment (IP addresses, ARNs, etc.).

------------------------------------------------------------------------------------------------------------------------- 

