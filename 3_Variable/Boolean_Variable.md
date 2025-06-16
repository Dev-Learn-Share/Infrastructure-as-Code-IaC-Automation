**Terraform Variable: bool Type**
The bool (boolean) type is used for true or false values, often for flags or toggles.

# 🟦 Block type keyword (declares an input variable)
variable "enable_public_ip" {
#        ^^^^^^^^^^^^^^^^^
#        └───────▶ Label (the name of this boolean variable)

  description = "Whether to assign a public IP address to the instance."
  #           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  #           └────▶ Metadata (describes the variable's purpose)

  type        = bool
  #           ^^^^
  #           └────▶ Data type (explicitly set to bool)

  default     = false
  #           ^^^^^
  #           └────▶ Default value (if no value is provided, this will be used)
}

# Example Usage:
# You can reference this variable in your resources like:
# resource "aws_instance" "web_server" {
#   associate_public_ip_address = var.enable_public_ip
#   # ...
# }

# 🟩 Output Block Example (exposes the variable's value)
output "public_ip_enabled_status" {
#        ^^^^^^^^^^^^^^^^^^^^^^^^
#        └───────▶ Label (name of the output value)

  description = "Boolean status indicating if public IP is enabled."
  #           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  #           └────▶ Metadata (describes the output's purpose)

  value       = var.enable_public_ip
  #           ^^^^^^^^^^^^^^^^
  #           └────▶ Actual value being output (the value of the 'enable_public_ip' variable)
}
