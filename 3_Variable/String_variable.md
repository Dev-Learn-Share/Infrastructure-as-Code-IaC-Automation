# Defining a String Variable in Terraform

Let's take an example for defining a string variable.

This is a block type keyword that tells Terraform you're declaring an input variable:

```terraform
# BLOCK
# <–––--------------------->
variable " " { }

This is the label or name of the variable:
Terraform

#        label or name
#       <–––----------------->
variable "environment_name" {
  // ... configuration for the variable ...
}

Understanding a Terraform Variable Block

Here's a detailed breakdown of the components within a Terraform variable block:
Terraform

# 🟦 Block type keyword (tells Terraform this is a variable)
variable "environment_name" {
#        ^^^^^^^^^^^^^^^^^^
#        └───────▶ Label (the name of the variable)

  description = "A string that represents the name of the environment"
  #           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  #           └────▶ Metadata (human-readable info about the variable)

  type        = string
  #           ^^^^^^
  #           └────▶ Data type (this must be a string)

  default     = "dev"
  #           ^^^^^
  #           └────▶ Default value (used if not overridden by tfvars or CLI)
}

Understanding a Terraform Output Block

Terraform output blocks are used to return values from your configuration, making them accessible to other configurations, modules, or for display after terraform apply.
Terraform

# 🟦 Block type keyword (declares an output value in Terraform)
output "selected_environment" {
#        ^^^^^^^^^^^^^^^^^^^^^
#        └──────▶ Label (name of the output variable)

  description = "The environment selected by the user"
  #           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  #           └────▶ Meta argument (helps document the output)

  value       = var.environment_name
  #           ^^^^^^^^^^^^^^^^^^^^
  #           └────▶ Actual value being output (in this case, the string variable)
}