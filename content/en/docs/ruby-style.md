---
title: "Ruby style"
weight: 1
description: >-
     Tips for better Ruby code
---

### Do not mix ternary operator and if statement
```
if a == true
  b == true ? "Yes" : "No" # Don't mix both "if" and "? : "
end

a == true ? "Yes" : "No" if b == true # Don't. This is event more complicated since output is "Yes" "No" and nil

a == true && b == true ? "Yes" : "No" # OK to use only ternary

if a == true && b == true # OK, this is much more readable
  "Yes"
else
  "No"
end
```

### After return or raise always add empty line

```
# bad, it if hard to see places for return
def name_upcase
  raise "NoName" if @name.blank
  return "ADMIN" if @name == "admin"
  @name.uppcase
end
```

```
# good, it is easier to see early return from block
def name_upcase
  raise "NoName" if @name.blank
  return "ADMIN" if @name == "admin"

  @name.uppcase
end
```

### Rubocop styles

```
# .rubocop.yml
# put comma after each line [1,]
Style/TrailingCommaInArrayLiteral:
  Enabled: false

# put comma after each line {a:1,}
Style/TrailingCommaInHashLiteral:
  Enabled: false

# also in arguments
Style/TrailingCommaInArguments:
  Enabled: false
```

### Do not use same variable name as method name

```
def tax(amount)
  amount * 0.20
end

tax = tax(100) # Don't do this since you will override the method
```
Also do not use the same name with local variable
```
def tax(amount)
  amount * 0.20
end

def add(tax) # Don't use the same name for argument since you will override the existing method
  tax + 1
end
```
But if the method is from other class, in this case you can use same name
```
class Calculate
  def initialize(percentage)
    @percentage = percentage
  end
  def tax(amount)
    amount * @percentage
  end
end

tax = Calculate.new(0.20).tax(100) # This is OK since we do not override the method
```

### Do not compare with string and number, use Constants

Instead of
```
dog = "Daki"

if dog == "Daki" # Don't compare with string
  puts "Dog is Daki"
end
```
better is to use CONST
```
DAKI = "Daki

if dog == DAKI # OK to compare with const
```
If you have a lot of constants you can create another class for it
```
class Const
  def self.daki
    "Daki"
  end
end

if dog == Const.daki  # OK
```
Using constants and methods, you do not need to think about case (if it is "Daki" or "daki")
and any syntax error will be visible (`Const.daik` will raise an error)

### Use bang method when you do not check the result

Instead of
```
user.save
```
use
```
user.save!
```
or
```
if user.save
  # do something
else
  # do something
end
```

### In ERB do not use data: { param: value } attribute, use "data-param": value

To generate
```
<button name="button" type="submit" data-some-param="123">name</button>
```
Instead of using `data:` attributes
```
<%= button_tag :name, data: { some_param: "123" } %>
```
use
```
<%= button_tag :name, "data-some-param": "123" %>
```
because it is easer to find when we search `data-some-param` in the code

### Naming is important, use snake_case of class CamelCase

Instead
```
# wrong
form = RegisterForm.new
user = LocationUser.last
```
use full name
```
register_form = RegisterForm.new
location_user = LocationUser.last
```

### Do not use Active Record Callbacks for external API calls or other complex logic

Instead of
```
# app/models/user.rb
class User < ApplicationRecord
  validate :check_api
  before_save :check_api

  def check_api
    HTTP
  end
end

# in controller
user.save
```
we should avoud callbacks and other complex logic and use method to explicity call when needed
```
# app/models/user.rb
class User < ApplicationRecord
  def save_and_check_api
    return unless save
    check_api
  end

  def check_api
    HTTP
  end
end

# in controller
user.save_and_check_api
```
since in this case we can use `user.save!` without fear that we will break because of invalid objects

### Order in Rails model

Since a lot of code is in models, we should agree for the following order

1. `include` and `extend` other modules, or methods from gems like: `devise`, `has_paper_trail`, `acts_as_list scope:`
1. `FIELDS = %i[name].freeze` and other constants
1. `enum status: %i[draft accepted]` enums
1. `attr_accessor` or `serialize :col, Hash`
1. `belongs_to :workflow` 
1.  `has_many :users` or `has_one :attached` associations
1. validations `validates :name, presence: true`
1. validate declarations `validate :_check_nested_resource`
1. callbacks declarations `before_validation :_default_values_on_create, on: :create`
1. scopes `scope :by_status_param, ->(status_argument) { where status: status_argument }`
1. class methods `def self.find_first_unpublished` (move to e.g. `app/queries/posts_query.rb`)
1. validate definitions `def _check_nested_resource`
1. callbacks definitions `def _default_values_on_create`
1. instance methods `def full_name`


### Separate pull request for indent and other syntax changes

It is hard to see changed lines if commit contains a lot of syntax corrections (indent, rename var names...).
It is better to use separate PR for those simple changes, and continue with original PR based on that.

