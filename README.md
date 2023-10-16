# OOP-4-Lab
import java.util.*;

class Animal {
    private String name;
    private int age;

    public Animal(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }
}

class Pet extends Animal {
    private String ownerName;
    private double price;

    public Pet(String name, int age, String ownerName, double price) {
        super(name, age);
        this.ownerName = ownerName;
        this.price = price;
    }

    public double getPrice() {
        return price;
    }
}

class Dog extends Pet {
    private String breed;
    private static final List<String> POPULAR_BREEDS = Arrays.asList("Labrador", "Bulldog", "German Shepherd", "Poodle", "Beagle");

    public Dog(String name, int age, String ownerName, String breed, double price) {
        super(name, age, ownerName, price);
        if (POPULAR_BREEDS.contains(breed)) {
            this.breed = breed;
        } else {
            throw new IllegalArgumentException(breed + " is not a top 5 breed");
        }
    }

    @Override
    public String toString() {
        return super.getName() + " the " + breed + " ($" + getPrice() + ")";
    }
}

class Cat extends Pet {
    private String breed;
    private static final List<String> POPULAR_BREEDS = Arrays.asList("Siamese", "Persian", "Maine Coon", "Ragdoll", "Bengal");

    public Cat(String name, int age, String ownerName, String breed, double price) {
        super(name, age, ownerName, price);
        if (POPULAR_BREEDS.contains(breed)) {
            this.breed = breed;
        } else {
            throw new IllegalArgumentException(breed + " is not a top 5 breed");
        }
    }

    @Override
    public String toString() {
        return super.getName() + " the " + breed + " ($" + getPrice() + ")";
    }
}

class Other extends Pet {
    private String species;

    public Other(String name, int age, String ownerName, String species, double price) {
        super(name, age, ownerName, price);
        this.species = species;
    }

    @Override
    public String toString() {
        return super.getName() + " the " + species + " ($" + getPrice() + ")";
    }
}

class Main {
    public static void main(String[] args) {
        // Creating instances of pets with predefined popular breeds
        List<Dog> dogs = Arrays.asList(
            new Dog("Buddy", 3, "John", "Labrador", 1200),
            new Dog("Max", 4, "Sarah", "Bulldog", 1000),
            new Dog("Rex", 5, "Smith", "German Shepherd", 1500),
            new Dog("Charlie", 3, "Tom", "Poodle", 1100),
            new Dog("Oscar", 2, "Olivia", "Beagle", 900)
        );

        List<Cat> cats = Arrays.asList(
            new Cat("Kitty", 2, "Linda", "Siamese", 600),
            new Cat("Simba", 1, "Mary", "Persian", 650),
            new Cat("Mittens", 3, "Nathan", "Maine Coon", 700),
            new Cat("Bella", 4, "Emily", "Ragdoll", 750),
            new Cat("Leo", 2, "Sophia", "Bengal", 800)
        );

        List<Other> others = Arrays.asList(
            new Other("Nemo", 2, "Alice", "Fish", 100),
            new Other("Iggy", 3, "Ella", "Iguana", 250),
            new Other("Bubbles", 1, "Hannah", "Rabbit", 80),
            new Other("Tweety", 2, "Zoe", "Bird", 120),
            new Other("Flash", 4, "Daniel", "Turtle", 150)
        );

        // Sort lists by price (from most to least expensive)
        dogs.sort(Comparator.comparingDouble(Pet::getPrice).reversed());
        cats.sort(Comparator.comparingDouble(Pet::getPrice).reversed());
        others.sort(Comparator.comparingDouble(Pet::getPrice).reversed());

        // Display the sorted pets
        System.out.println("Dogs from most expensive to least expensive:");
        dogs.forEach(System.out::println);

        System.out.println("\nCats from most expensive to least expensive:");
        cats.forEach(System.out::println);

        System.out.println("\nOther pets from most expensive to least expensive:");
        others.forEach(System.out::println);
    }
}
