# Clean Code

Most code will someday change and you've begun to craft it in anticipation of that day. Pre-mature?

You should not reach for abstraction, but instead, you should resist them until they absolutely insist upon being created. Let the abstraction come naturally to you.

Duplication of logic suggests there are concepts hidden in the code which has not been isolated and named.

## Abstraction and Indirection and Ignorant

By abstracting out into more level of indirection, you are willingly becoming ignorant of the details as long as the abstracted behavior is what you expected.

Depend on abstract role rather than concrete class.

It is better and cheaper to manage temporary duplication than to recover from incorrect abstractions.

## Checklist

First, have you check your **patience**? Don't go through this checklist if you've insufficient patience.

1. Is your name intentional? Have you name your concepts?
2. Does your function do one thing only?
3. Does the code openly exposes the problem's domain?
4. Are you able to answer domain questions easily with the code?
5. Is your code too DRY and thus expensive to change?
6. Are you on the wrong level of abstraction?
7. Are you representing your concept in the wrong abstraction?
8. Have a list of difficult design decisions or design decisions which are likely to change

## Single Responsibility

* [SRP is about People (who request changes) and thus the reason for that module to change](https://8thlight.com/blog/uncle-bob/2014/05/08/SingleReponsibilityPrinciple.html)

```ruby
class Employee
  # Responsibility of Payroll module
  # CFO will request changes to the calculatePay()
  def calculatePay
  end
  
  # Responsibility of Persistent module
  # CTO will request changes to the save()
  def save
  end
  
  # Responsibility of Timesheet module
  # COO will request changes to the reportHours()
  def reportHours
  end
end
```