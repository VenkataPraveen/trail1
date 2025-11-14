# Creational Pattern
## What is the problem?

In software development, creating objects can become complex and may lead to tight coupling between classes. This can make the code difficult to maintain and extend.
- Tight Coupling
- adding new types of objects can require changes across the entire codebase
- duplicated object <span style="color: red;">instantiation</span>
    - Objects are created multiple times leading to duplicated code

## How is Creational Pattern beneficial?

<span style="color: green;">Solution:</span>
Objects are created without specifying the exact class

Creational Patterns provide <span style="color: red;">abstraction</span> to instantiate objects in a manner suitable to the situation. 
-   Instantiate objects as needed without depending on concrete classes.
-   Delegate instantiation to subclasses or external objects to reduce coupling.


## What is Creational Pattern?

Creational Patterns are design patterns that deal with object creation mechanisms. They aim to create objects in a manner suitable to the situation, which can help in managing the complexity of the code.

## Types of Creational Patterns
    1.  Factory Method Pattern
    2.  Abstract Factory Pattern
    3.  Builder Pattern
    4.  Prototype Pattern
    5.  Singleton Pattern

## Example

### Factory Method Pattern

The Factory Method defines an interface for creating an object but allows subclasses to alter the type of object created.


```java
// Car interface
interface Car {
    void drive();
}

// SUV implementation
class SUV implements Car {
    @Override
    public void drive() {
        System.out.println("Driving an SUV");
    }
}

// Sedan implementation
class Sedan implements Car {
    @Override
    public void drive() {
        System.out.println("Driving a Sedan");
    }
}

// CarFactory
abstract class CarFactory {
    abstract Car createCar();
}

class SUVFactory extends CarFactory {
    @Override
    Car createCar() {
        return new SUV();
    }
}

class SedanFactory extends CarFactory {
    @Override
    Car createCar() {
        return new Sedan();
    }
}

// Client code
public class Main {
    public static void main(String[] args) {
        CarFactory suvFactory = new SUVFactory();
        Car suv = suvFactory.createCar();
        suv.drive();

        CarFactory sedanFactory = new SedanFactory();
        Car sedan = sedanFactory.createCar();
        sedan.drive();
    }
}
```

## Abstract Factory Pattern


#### Example
We can extend the car example by adding related objects like `Tyre` and `Engine` to each car type.

```java
// Tyre interface
interface Tyre {
    void design();
}

// Engine interface
interface Engine {
    void manufacture();
}

// SUV Tyre implementation
class SUVTyre implements Tyre {
    @Override
    public void design() {
        System.out.println("Designing SUV Tyre");
    }
}

// SUV Engine implementation
class SUVEngine implements Engine {
    @Override
    public void manufacture() {
        System.out.println("Manufacturing SUV Engine");
    }
}

// Sedan Tyre implementation
class SedanTyre implements Tyre {
    @Override
    public void design() {
        System.out.println("Designing Sedan Tyre");
    }
}

// Sedan Engine implementation
class SedanEngine implements Engine {
    @Override
    public void manufacture() {
        System.out.println("Manufacturing Sedan Engine");
    }
}

// Abstract Factory
interface CarFactory {
    Car createCar();
    Tyre createTyre();
    Engine createEngine();
}

// SUV Factory
class SUVFactory implements CarFactory {
    @Override
    public Car createCar() {
        return new SUV();
    }

    @Override
    public Tyre createTyre() {
        return new SUVTyre();
    }

    @Override
    public Engine createEngine() {
        return new SUVEngine();
    }
}

// Sedan Factory
class SedanFactory implements CarFactory {
    @Override
    public Car createCar() {
        return new Sedan();
    }

    @Override
    public Tyre createTyre() {
        return new SedanTyre();
    }

    @Override
    public Engine createEngine() {
        return new SedanEngine();
    }
}

// Client code
public class Main {
    public static void main(String[] args) {
        CarFactory suvFactory = new SUVFactory();
        Car suv = suvFactory.createCar();
        Tyre suvTyre = suvFactory.createTyre();
        Engine suvEngine = suvFactory.createEngine();
        suv.drive();
        suvTyre.design();
        suvEngine.manufacture();

        CarFactory sedanFactory = new SedanFactory();
        Car sedan = sedanFactory.createCar();
        Tyre sedanTyre = sedanFactory.createTyre();
        Engine sedanEngine = sedanFactory.createEngine();
        sedan.drive();
        sedanTyre.design();
        sedanEngine.manufacture();
    }
}
```



### 3. **Builder Pattern**

The Builder Pattern separates the construction of a complex object from its representation, allowing the same construction process to create different representations.

#### Example
We can have a `CarBuilder` that builds cars with optional features like sunroofs or sports kits.
```java
// Car class with optional features
class Car {
    private String type;
    private boolean sunroof;
    private boolean sportsKit;

    private Car(CarBuilder builder) {
        this.type = builder.type;
        this.sunroof = builder.sunroof;
        this.sportsKit = builder.sportsKit;
    }

    public void showSpecifications() {
        System.out.println("Car Type: " + type);
        System.out.println("Sunroof: " + (sunroof ? "Yes" : "No"));
        System.out.println("Sports Kit: " + (sportsKit ? "Yes" : "No"));
    }

    // Builder Class
    public static class CarBuilder {
        private String type;
        private boolean sunroof;
        private boolean sportsKit;

        public CarBuilder(String type) {
            this.type = type;
        }

        public CarBuilder addSunroof(boolean sunroof) {
            this.sunroof = sunroof;
            return this;
        }

        public CarBuilder addSportsKit(boolean sportsKit) {
            this.sportsKit = sportsKit;
            return this;
        }

        public Car build() {
            return new Car(this);
        }
    }
}

// Client code
public class Main {
    public static void main(String[] args) {
        Car suv = new Car.CarBuilder("SUV")
                .addSunroof(true)
                .addSportsKit(false)
                .build();
        suv.showSpecifications();

        Car sedan = new Car.CarBuilder("Sedan")
                .addSunroof(false)
                .addSportsKit(true)
                .build();
        sedan.showSpecifications();
    }
}
```

### 4. **Prototype Pattern**

Prototype allows for creating duplicate objects while keeping performance high. It uses cloning to copy an existing instance rather than creating a new one from scratch.

---
example:

```java
// Car Prototype interface
interface CarPrototype {
    CarPrototype clone();
}

// Concrete Car class implementing CarPrototype
class Car implements CarPrototype {
    private String model;

    public Car(String model) {
        this.model = model;
    }

    @Override
    public CarPrototype clone() {
        return new Car(this.model);
    }

    public void showModel() {
        System.out.println("Car Model: " + model);
    }
}

// Client code
public class Main {
    public static void main(String[] args) {
        Car car1 = new Car("SUV");
        Car car2 = (Car) car1.clone();

        car1.showModel();
        car2.showModel();
    }
}
```

