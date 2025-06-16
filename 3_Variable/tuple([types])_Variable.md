**Terraform Variable: tuple([types]) Type**

The tuple([types]) type represents a fixed-length, ordered sequence of elements, where each element can have a different type. This is similar to a list but with a rigid structure.

# 🟦 Block type keyword (declares an input variable)

variable "user_details" {
#        ^^^^^^^^^^^^
#        └───────▶ Label (the name of this tuple variable)

  description = "A tuple containing user ID (string), age (number), and active status (boolean)."
  #           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  #           └────▶ Metadata (describes the variable's purpose)

  type        = tuple([string, number, bool])
  #           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  #           └────▶ Data type (a tuple with specific types at each position)

  default     = ["user-123", 30, true]
  #           ^^^^^^^^^^^^^^^^^^^^^^
  #           └────▶ Default value (a tuple matching the defined structure)
}

# Example Usage:
# You can reference this variable's elements by their position (index):
# local {
#   user_id      = var.user_details[0]
#   user_age     = var.user_details[1]
#   user_is_active = var.user_details[2]
# }
#
# output "first_user_id" {
#   value = local.user_id
# }

# 🟩 Output Block Example (exposes elements of the tuple variable)
output "tuple_user_id_and_status" {
#        ^^^^^^^^^^^^^^^^^^^^^^^^
#        └───────▶ Label (name of the output value)

  description = "The user ID and active status from the tuple."
  #           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  #           └────▶ Metadata (describes the output's purpose)

  value = {
    id     = var.user_details[0]
    active = var.user_details[2]
    #      └────▶ Outputting specific elements from the tuple
  }
  #           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  #           └────▶ Actual value being output (a map created from tuple elements)
}
