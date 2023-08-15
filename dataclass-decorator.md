## Simplifying code with Data Class decorator

When writing a class, normally you will have to write __eq__ method to compare the value in the two instances.

For example:

```python
class Money:
    def __init__(self, value: float, currency: str) -> None:
        self.value = value
        self.currency = currency

    def __eq__(self, other: Money):
        if isinstance(other, Money):
            return (self._value == other._value) and \
                (self._currency.lower() == other._currency.lower())
        return False


a = Money(20, 'Baht')
b = Money(20, 'Baht')
print(a == b)
# True
```

We can simplify this code using **@dataclass** decorator.

```python
from dataclasses import dataclass

@dataclass
class Money:
    value: float
    currency: str


a = Money(20, 'Baht')
b = Money(20, 'Baht')
print(a == b)
# True
```

You can even add other comparing methods with a really short code.

```python
from dataclasses import dataclass

@dataclass(order=True)
class Money:
    value: float
    currency: str


a = Money(20, 'Baht')
b = Money(30, 'Baht')
print(a > b)
# False
```