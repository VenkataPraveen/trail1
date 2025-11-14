# Adapter Pattern

![](2024-11-11-14-25-20.png)

its like a wrapper class

adapter from old PS2 to PS4, 

- use the adaptee interface


## Adapter Pattern:

  The Adapter Pattern is a structural design pattern that allows objects with incompatible interfaces to work together. 
  It acts as a bridge between two incompatible interfaces by converting the interface of a class into another interface 
  that a client expects.
  
  Key Terms:
  
  - <span style="color: red;">Client</span>: The client is the object that interacts with the adapter. It expects to work with a target interface.
  
  - <span style="color: green;">Adapter</span>: The adapter is the object that implements the target interface and translates the requests from the client 
    to the adaptee. It allows the client to interact with the adaptee through the target interface.
  
  - <span style="color: red;">Target Interface</span>: The target interface is the interface that the client expects to work with. The adapter implements 
    this interface to make the adaptee compatible with the client.
  
  - <span style="color: red;">Adaptee</span>: The adaptee is the object that needs to be adapted. It has an incompatible interface that needs to be 
    converted by the adapter to match the target interface.
 
## Example in Java

Here is a simple example of the Adapter Pattern in Java:

```java
// Target Interface
interface Target {
    void request();
}

// Adaptee
class Adaptee {
    void specificRequest() {
        System.out.println("Called specificRequest()");
    }
}

// Adapter
class Adapter implements Target {
    private Adaptee adaptee;

    public Adapter(Adaptee adaptee) {
        this.adaptee = adaptee;
    }

    @Override
    public void request() {
        adaptee.specificRequest();
    }
}

// Client
public class Client {
    public static void main(String[] args) {
        Adaptee adaptee = new Adaptee();
        Target target = new Adapter(adaptee);
        target.request();
    }
}
```

In this example:
- The `Target` interface defines the domain-specific interface that the `Client` uses.
- The `Adaptee` class contains some useful behavior, but its interface is incompatible with the `Target` interface.
- The `Adapter` class implements the `Target` interface and translates the requests to the `Adaptee`.
- The `Client` uses the `Target` interface to interact with the `Adaptee` through the `Adapter`.


## Where to Use the Adapter Pattern

The Adapter Pattern is useful in the following scenarios:

- When you want to use an existing class, and its interface does not match the one you need.
- When you want to create a reusable class that cooperates with unrelated or unforeseen classes, that is, classes that don't necessarily have compatible interfaces.
- When you need to use several existing subclasses, but it's impractical to adapt their interface by subclassing every one. An object adapter can adapt the interface of its parent class.

## Example with Car

Here is an example of the Adapter Pattern with a car scenario in Java:

```java
// Target Interface
interface Car {
    void accelerate();
}

// Adaptee
class Bicycle {
    void pedal() {
        System.out.println("Pedaling the bicycle");
    }
}

// Adapter
class BicycleAdapter implements Car {
    private Bicycle bicycle;

    public BicycleAdapter(Bicycle bicycle) {
        this.bicycle = bicycle;
    }

    @Override
    public void accelerate() {
        bicycle.pedal();
    }
}

// Client
public class Driver {
    public static void main(String[] args) {
        Bicycle bicycle = new Bicycle();
        Car car = new BicycleAdapter(bicycle);
        car.accelerate();
    }
}
```

In this example:
- The `Car` interface defines the domain-specific interface that the `Driver` uses.
- The `Bicycle` class contains some useful behavior, but its interface is incompatible with the `Car` interface.
- The `BicycleAdapter` class implements the `Car` interface and translates the requests to the `Bicycle`.
- The `Driver` uses the `Car` interface to interact with the `Bicycle` through the `BicycleAdapter`.
