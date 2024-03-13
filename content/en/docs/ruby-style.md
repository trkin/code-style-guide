---
title: "Ruby style"
weight: 1
description: >-
     Tips for better Ruby code
---

## Ruby

### Do not use same variable name as method name

```
def tax(amount)
  amount * 0.20
end

tax = tax(100) # Don't do this since you will override the method
```
But is the method is from other classes you might use
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

