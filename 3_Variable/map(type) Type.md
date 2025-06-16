**Terraform Variable: map(type) Type**

The map(type) type represents a collection of key-value pairs, where all values must be of the specified type. Keys are always strings.

# 🟦 Block type keyword (declares an input variable)

variable "region_amis" {
#        ^^^^^^^^^^^
#        └───────▶ Label (the name of this map variable)

  description = "A map of AMIs, keyed by region."
  #           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  #           └────▶ Metadata (describes the variable's purpose)

  type        = map(string)
  #           ^^^^^^^^^^^
  #           └────▶ Data type (a map where values are strings)

  default = {
    us-east-1 = "ami-0abcdef1234567890"
    us-west-2 = "ami-0fedcba9876543210"
  }
  #           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  #           └────▶ Default value (a map with string keys and string values)
}

# Example Usage:
# You can reference this variable in your resources like:
# resource "aws_instance" "my_server" {
#   ami           = var.region_amis[var.aws_region] # Accessing map value by key
#   instance_type = "t2.micro"
#   # ...
# }

# 🟩 Output Block Example (exposes the variable's value)
output "configured_amis_map" {
#        ^^^^^^^^^^^^^^^^^^
#        └───────▶ Label (name of the output value)

  description = "The map of AMIs configured for different regions."
  #           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  #           └────▶ Metadata (describes the output's purpose)

  value       = var.region_amis
  #           ^^^^^^^^^^^^^
  #           └────▶ Actual value being output (the value of the 'region_amis' variable)
}
