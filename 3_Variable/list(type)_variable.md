**Terraform Variable: list(type) Type**

The list(type) type represents an ordered collection of elements, where all elements must be of the specified type.# 🟦 Block type keyword (declares an input variable)

variable "allowed_cidrs" {
#        ^^^^^^^^^^^^^^
#        └───────▶ Label (the name of this list variable)

  description = "A list of CIDR blocks allowed to access the security group."
  #           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  #           └────▶ Metadata (describes the variable's purpose)

  type        = list(string)
  #           ^^^^^^^^^^^^
  #           └────▶ Data type (a list where each element is a string)

  default     = ["10.0.0.0/16", "192.168.1.0/24"]
  #           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  #           └────▶ Default value (a list of string CIDR blocks)
}

# Example Usage:
# You can reference this variable in your resources like:
# resource "aws_security_group_rule" "ingress_ssh" {
#   type        = "ingress"
#   from_port   = 22
#   to_port     = 22
#   protocol    = "tcp"
#   cidr_blocks = var.allowed_cidrs # Uses the list of strings
# }

# 🟩 Output Block Example (exposes the variable's value)
output "security_group_cidrs" {
#        ^^^^^^^^^^^^^^^^^^^^
#        └───────▶ Label (name of the output value)

  description = "The list of CIDR blocks configured for access."
  #           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  #           └────▶ Metadata (describes the output's purpose)

  value       = var.allowed_cidrs
  #           ^^^^^^^^^^^^^^^
  #           └────▶ Actual value being output (the value of the 'allowed_cidrs' variable)
}
