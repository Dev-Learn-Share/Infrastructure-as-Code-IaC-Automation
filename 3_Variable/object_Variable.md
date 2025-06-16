**Terraform Variable: object({...}) Type**

The object({...}) type represents a structured object with named attributes, where each attribute can have its own distinct type. This allows for complex, structured data.

# 🟦 Block type keyword (declares an input variable)
variable "server_config" {
#        ^^^^^^^^^^^^^^
#        └───────▶ Label (the name of this object variable)

  description = "Configuration details for a server instance."
  #           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  #           └────▶ Metadata (describes the variable's purpose)

  type = object({
    instance_type = string
    ami           = string
    disk_size_gb  = number
    tags          = map(string)
    #             └────▶ Defines the structure: each attribute has a specific type
  })
  #           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  #           └────▶ Data type (an object with specific string, number, and map attributes)

  default = {
    instance_type = "t3.medium"
    ami           = "ami-0abcdef1234567890"
    disk_size_gb  = 50
    tags = {
      Environment = "development"
      Owner       = "ops-team"
    }
  }
  #           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  #           └────▶ Default value (a structured object matching the defined type)
}

# Example Usage:
# You can reference this variable's attributes like:
# resource "aws_instance" "my_server" {
#   instance_type = var.server_config.instance_type
#   ami           = var.server_config.ami
#   volume_size   = var.server_config.disk_size_gb
#   tags          = var.server_config.tags
# }

# 🟩 Output Block Example (exposes attributes of the object variable)
output "server_details_output" {
#        ^^^^^^^^^^^^^^^^^^^^
#        └───────▶ Label (name of the output value)

  description = "Selected details of the configured server."
  #           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  #           └────▶ Metadata (describes the output's purpose)

  value = {
    instance_type = var.server_config.instance_type
    ami_id        = var.server_config.ami
    #             └────▶ Outputting specific attributes from the object
  }
  #           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  #           └────▶ Actual value being output (a map created from object attributes)
}
