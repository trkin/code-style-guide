---
title: "Ruby style"
weight: 1
description: >-
     Tips for better Ruby code
---

### Do not mix ternary operator and if statement
```
if a == true
  b == true ? "Yes" : "No" # Don't mix both
end

a == true ? "Yes" : "No" if b == true # Don't. This is event more complicated since output is "Yes" "No" and nil

a == true && b == true ? "Yes" : "No" # OK to use only ternary

if a == true && b == true # OK, this is much more readable
  "Yes"
else
  "No"
end
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

### Do not compare with string

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

