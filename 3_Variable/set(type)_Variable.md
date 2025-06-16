**Terraform Variable: set(type) Type**

The set(type) type represents an unordered collection of unique elements, where all elements must be of the specified type. Duplicate elements are automatically removed.

# 🟦 Block type keyword (declares an input variable)

variable "unique_tags" {
#        ^^^^^^^^^^^
#        └───────▶ Label (the name of this set variable)

  description = "A set of unique tags to apply to resources (duplicates will be removed)."
  #           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  #           └────▶ Metadata (describes the variable's purpose)

  type        = set(string)
  #           ^^^^^^^^^^^
  #           └────▶ Data type (a set where each element is a string)

  default     = ["production", "web", "frontend", "web"] # "web" will appear only once
  #           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  #           └────▶ Default value (a set of strings; duplicates like "web" are ignored)
}

# Example Usage:
# You can reference this variable in your resources like:
# resource "aws_instance" "example" {
#   # ...
#   tags = {
#     for tag in var.unique_tags : tag => "true"
#   }
# }

# 🟩 Output Block Example (exposes the variable's value)
output "applied_unique_tags" {
#        ^^^^^^^^^^^^^^^^^^
#        └───────▶ Label (name of the output value)

  description = "The set of unique tags applied to resources."
  #           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  #           └────▶ Metadata (describes the output's purpose)

  value       = var.unique_tags
  #           ^^^^^^^^^^^
  #           └────▶ Actual value being output (the value of the 'unique_tags' variable)
}
