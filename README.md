package sectiona.furnituremanagementsystem;



import java.util.ArrayList;

import java.util.List;



public class FurnitureManagementSystem {

    

    private List<Furniture> furnitureList;

    

    public FurnitureManagementSystem() {

        furnitureList = new ArrayList<>();

    }

    

    public void addFurniture(Furniture furniture) {

        furnitureList.add(furniture);

    }

    

    public void removeFurniture(String name) {

        furnitureList.removeIf(furniture -> furniture.getName().equalsIgnoreCase(name));

    }

    

    public Furniture findFurniture(String name) {

        for (Furniture furniture : furnitureList) {

            if (furniture.getName().equalsIgnoreCase(name)) {

                return furniture;

            }

        }

        return null;

    }

    

    public List<Furniture> getAllFurniture() {

        return furnitureList;

    }

    

    public void displayAllFurniture() {

        System.out.println("Furniture List:");

        for (Furniture furniture : furnitureList) {

            System.out.println(furniture);

        }

    }

    

    public static void main(String[] args) {

        FurnitureManagementSystem system = new FurnitureManagementSystem();

        FurnitureFactory factory = new FurnitureFactory();

        

        Furniture chair = factory.createFurniture("Chair", "Chair", 50, "Wood", 10, 4, null, 0, null);

        Furniture table = factory.createFurniture("Table", "Table", 100, "Metal", 25, 0, "Round", 0, null);

        Furniture sofa = factory.createFurniture("Sofa", "Sofa", 300, "Leather", 50, 0, null, 3, null);

        Furniture cupboard = factory.createFurniture("Cupboard", "Cupboard", 200, "Wood", 75, 0, null, 5, null);

        Furniture bed = factory.createFurniture("Bed", "Bed", 400, "Wood", 100, 0, null, 0, "Queen");

        

        system.addFurniture(chair);

        system.addFurniture(table);

        system.addFurniture(sofa);

        system.addFurniture(cupboard);

        system.addFurniture(bed);

        

        System.out.println("After adding furniture:");

        system.displayAllFurniture();

        

        system.removeFurniture("Chair");

        

        System.out.println("\nAfter removing 'Chair':");

        system.displayAllFurniture();

        

        Furniture found = system.findFurniture("Table");

        if (found != null) {

            System.out.println("\nFound furniture: " + found);

        } else {

            System.out.println("\nFurniture not found.");

        }

    }

}



class Furniture {

    

    private String name;

    private double price;

    private String material;

    private double weight;

    

    public Furniture(String name, double price, String material, double weight) {

        this.name = name;

        this.price = price;

        this.material = material;

        this.weight = weight;

    }

    

    public String getName() {

        return name;

    }

    

    public double getPrice() {

        return price;

    }

    

    public String getMaterial() {

        return material;

    }

    

    public double getWeight() {

        return weight;

    }

    

    @Override

    public String toString() {

        return "Furniture{" +

               "name='" + name + '\'' +

               ", price=" + price +

               ", material='" + material + '\'' +

               ", weight=" + weight +

               '}';

    }

}



class Chair extends Furniture {

    private int numberOfLegs;

    

    public Chair(String name, double price, String material, double weight, int numberOfLegs) {

        super(name, price, material, weight);

        this.numberOfLegs = numberOfLegs;

    }

    

    public int getNumberOfLegs() {

        return numberOfLegs;

    }

    

    @Override

    public String toString() {

        return "Chair{" +

               "name='" + getName() + '\'' +

               ", price=" + getPrice() +

               ", material='" + getMaterial() + '\'' +

               ", weight=" + getWeight() +

               ", numberOfLegs=" + numberOfLegs +

               '}';

    }

}



class Table extends Furniture {

    private String shape;

    

    public Table(String name, double price, String material, double weight, String shape) {

        super(name, price, material, weight);

        this.shape = shape;

    }

    

    public String getShape() {

        return shape;

    }

    

    @Override

    public String toString() {

        return "Table{" +

               "name='" + getName() + '\'' +

               ", price=" + getPrice() +

               ", material='" + getMaterial() + '\'' +

               ", weight=" + getWeight() +

               ", shape='" + shape + '\'' +

               '}';

    }

}



class Sofa extends Furniture {

    private int numberOfSeats;

    

    public Sofa(String name, double price, String material, double weight, int numberOfSeats) {

        super(name, price, material, weight);

        this.numberOfSeats = numberOfSeats;

    }

    

    public int getNumberOfSeats() {

        return numberOfSeats;

    }

    

    @Override

    public String toString() {

        return "Sofa{" +

               "name='" + getName() + '\'' +

               ", price=" + getPrice() +

               ", material='" + getMaterial() + '\'' +

               ", weight=" + getWeight() +

               ", numberOfSeats=" + numberOfSeats +

               '}';

    }

}



class Cupboard extends Furniture {

    private int numberOfShelves;

    

    public Cupboard(String name, double price, String material, double weight, int numberOfShelves) {

        super(name, price, material, weight);

        this.numberOfShelves = numberOfShelves;

    }

    

    public int getNumberOfShelves() {

        return numberOfShelves;

    }

    

    @Override

    public String toString() {

        return "Cupboard{" +

               "name='" + getName() + '\'' +

               ", price=" + getPrice() +

               ", material='" + getMaterial() + '\'' +

               ", weight=" + getWeight() +

               ", numberOfShelves=" + numberOfShelves +

               '}';

    }

}



class Bed extends Furniture {

    private String size;

    

    public Bed(String name, double price, String material, double weight, String size) {

        super(name, price, material, weight);

        this.size = size;

    }

    

    public String getSize() {

        return size;

    }

    

    @Override

    public String toString() {

        return "Bed{" +

               "name='" + getName() + '\'' +

               ", price=" + getPrice() +

               ", material='" + getMaterial() + '\'' +

               ", weight=" + getWeight() +

               ", size='" + size + '\'' +

               '}';

    }

}



class FurnitureFactory {

    public Furniture createFurniture(String type, String name, double price, String material, double weight, int numberOfLegs, String shape, int numberOfSeatsOrShelves, String size) {

        switch (type) {

            case "Chair":

                return new Chair(name, price, material, weight, numberOfLegs);

            case "Table":

                return new Table(name, price, material, weight, shape);

            case "Sofa":

                return new Sofa(name, price, material, weight, numberOfSeatsOrShelves);

            case "Cupboard":

                return new Cupboard(name, price, material, weight, numberOfSeatsOrShelves);

            case "Bed":

                return new Bed(name, price, material, weight, size);

            default:

                throw new IllegalArgumentException("Unknown furniture type: " + type);

        }

    }

}
