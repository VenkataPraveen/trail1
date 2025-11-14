# FACADE PATTERN

## Explanation

The Facade Pattern provides a simplified interface to a complex subsystem. It defines a higher-level interface that makes the subsystem easier to use.

## Example

Consider a home theater system. It has various components like a DVD player, projector, lights, and screen. To watch a movie, you need to interact with each component individually, which can be complex. The Facade Pattern can simplify this by providing a single interface to control all the components.

### Code Example



In this example, the `HomeTheaterFacade` class provides a simple interface to control the home theater system. Instead of interacting with each component individually, you can use the `watch_movie` method to perform all the necessary actions.
### Java Code Example

```java
class DVDPlayer {
    public void on() {
        System.out.println("DVD Player on");
    }
    public void play(String movie) {
        System.out.println("Playing " + movie);
    }
}

class Projector {
    public void on() {
        System.out.println("Projector on");
    }
    public void wideScreenMode() {
        System.out.println("Projector in widescreen mode");
    }
}

class Screen {
    public void down() {
        System.out.println("Screen down");
    }
}

class TheaterLights {
    public void dim(int level) {
        System.out.println("Theater lights dimming to " + level + "%");
    }
}

class HomeTheaterFacade {

    // access patterns are private
    private DVDPlayer dvdPlayer;
    private Projector projector;
    private Screen screen;
    private TheaterLights lights;

    public HomeTheaterFacade(DVDPlayer dvdPlayer, Projector projector, Screen screen, TheaterLights lights) {
        this.dvdPlayer = dvdPlayer;
        this.projector = projector;
        this.screen = screen;
        this.lights = lights;
    }

    public void watchMovie(String movie) {
        System.out.println("Get ready to watch a movie...");
        screen.down();
        projector.on();
        projector.wideScreenMode();
        lights.dim(10);
        dvdPlayer.on();
        dvdPlayer.play(movie);
    }
}

// Usage
public class FacadePatternDemo {
    public static void main(String[] args) {
        DVDPlayer dvdPlayer = new DVDPlayer();
        Projector projector = new Projector();
        Screen screen = new Screen();
        TheaterLights lights = new TheaterLights();

        HomeTheaterFacade homeTheater = new HomeTheaterFacade(dvdPlayer, projector, screen, lights);
        homeTheater.watchMovie("Inception");
    }
}
```

## When to Use the Facade Design Pattern

| Scenario | Description |
|----------|-------------|
| Simplify complex systems | When you have a complex system with many interdependent classes, a facade can provide a simpler interface to interact with the system. |
| Decouple subsystems | When you want to decouple a subsystem from its clients and other subsystems, a facade can provide a unified interface to the subsystem. |
| Improve readability | When you want to improve the readability and usability of a complex system, a facade can hide the complexities and provide a more readable interface. |
| Layered architecture | When you are working with a layered architecture, a facade can be used to define entry points to each layer, making it easier to manage dependencies between layers. |


## Key Design Principles

1. **Encapsulation**: The Facade Pattern encapsulates the complexities of the subsystem by providing a simplified interface. This hides the intricate details and interactions of the subsystem from the client.

2. **Abstraction**: By defining a higher-level interface, the Facade Pattern abstracts the underlying components and their interactions. This makes it easier for clients to use the subsystem without needing to understand its internal workings.

3. **Single Responsibility Principle**: The Facade class has the single responsibility of providing a simplified interface to the subsystem. It does not add any additional functionality but merely delegates tasks to the appropriate components.

4. **Loose Coupling**: The Facade Pattern promotes loose coupling between the client and the subsystem. Clients interact with the facade rather than the subsystem directly, reducing dependencies and making the system more modular and easier to maintain.

5. **Separation of Concerns**: The pattern separates the concerns of the client and the subsystem. The client is concerned with performing high-level operations, while the subsystem handles the low-level details. The facade bridges this gap by providing a clear separation between the two.
