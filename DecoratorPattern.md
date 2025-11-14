# Decorator Design Pattern

## Principles Used
The Decorator Design Pattern is based on the following principles:
- **Open/Closed Principle**: Classes should be open for extension but closed for modification.
- **Single Responsibility Principle**: A class should have only one reason to change.

![](2024-11-25-10-04-35.png)

Explain in detail:

![](2024-11-25-10-07-30.png)


## Explanation of Aggregation in Software Architecture
Aggregation is a relationship where one class is a part of another class. It represents a "has-a" relationship. In aggregation, the lifetime of the part is not managed by the whole. For example, a library has books, but if the library is destroyed, the books still exist.

## When to Use
- When you want to add responsibilities to individual objects dynamically and transparently.
- When extending functionality by subclassing is impractical.
- When you need to add responsibilities to an object without affecting other objects.
![](2024-11-25-09-52-13.png)

## Advantages
- More flexible than static inheritance.
- Avoids feature-laden classes high up in the hierarchy.
- Allows for the extension of functionality without modifying existing code.

## Disadvantages
- Can result in a large number of small objects in the design.
- Complexity increases as the number of decorators increases.

## Example in Java

```java
// Component Interface
public interface Coffee {
    String getDescription();
    double getCost();
}

// Concrete Component
public class SimpleCoffee implements Coffee {
    @Override
    public String getDescription() {
        return "Simple Coffee";
    }

    @Override
    public double getCost() {
        return 5.0;
    }
}

// Decorator Class
public abstract class CoffeeDecorator implements Coffee {
    protected Coffee decoratedCoffee;

    public CoffeeDecorator(Coffee coffee) {
        this.decoratedCoffee = coffee;
    }

    @Override
    public String getDescription() {
        return decoratedCoffee.getDescription();
    }

    @Override
    public double getCost() {
        return decoratedCoffee.getCost();
    }
}

// Concrete Decorators
public class MilkDecorator extends CoffeeDecorator {
    public MilkDecorator(Coffee coffee) {
        super(coffee);
    }

    @Override
    public String getDescription() {
        return decoratedCoffee.getDescription() + ", Milk";
    }

    @Override
    public double getCost() {
        return decoratedCoffee.getCost() + 1.5;
    }
}

public class SugarDecorator extends CoffeeDecorator {
    public SugarDecorator(Coffee coffee) {
        super(coffee);
    }

    @Override
    public String getDescription() {
        return decoratedCoffee.getDescription() + ", Sugar";
    }

    @Override
    public double getCost() {
        return decoratedCoffee.getCost() + 0.5;
    }
}

// Usage
public class Main {
    public static void main(String[] args) {
        Coffee coffee = new SimpleCoffee();
        System.out.println(coffee.getDescription() + " $" + coffee.getCost());

        coffee = new MilkDecorator(coffee);
        System.out.println(coffee.getDescription() + " $" + coffee.getCost());

        coffee = new SugarDecorator(coffee);
        System.out.println(coffee.getDescription() + " $" + coffee.getCost());
    }
}
```

