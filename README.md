import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        Circle circle1 = new Circle();
        circle1.setRadius(sc.nextInt());
        System.out.println(circle1);


        Cylinder cylinder1 = new Cylinder();
        System.out.println(cylinder1);


    }
}

import java.util.Scanner;

public class Cylinder {
    private int height;
    private int radius;
    private double surfaceArea;
    private double volume;

    public Cylinder() {
        Scanner sc = new Scanner(System.in);
        System.out.print("Cylinder radius : " );
        this.radius = sc.nextInt();

        System.out.print("Cylinder height : " );
        this.height = sc.nextInt();
    }

    public Cylinder(int radius, int height) {
        this.radius = radius;
        this.height = height;
    }

    public double getSurfaceArea() {
        this.surfaceArea = 2 * Math.PI * radius * radius + 2 * Math.PI * radius * height;
        return this.surfaceArea;
    }

    public double getVolume() {
        this.volume = Math.PI * radius * radius * height;
        return this.volume;
    }

    @Override
    public String toString() {
        return "Cylinder radius: " + radius +
                ", Cylinder height: " + height +
                ", Cylinder surface area: " + getSurfaceArea() +
                ", Cylinder volume: " + getVolume();
    }
}

public class Circle {
    private int radius;
    private double perimeter;
    private double area;

    public Circle() {
        System.out.print("Circle radius : ");

    }

    public void setRadius(int radius) {
        this.radius = radius;
    }

    public int getRadius() {
        return radius;
    }

    public void setPerimeter() {
        this.perimeter = getRadius() * 2 * Math.PI;
    }

    public double getPerimeter() {
        return perimeter;
    }

    public void setArea() {
        this.area = getRadius() * getRadius() * Math.PI;
    }

    public double getArea() {
        return area;
    }

    public String toString() {
        setPerimeter();
        setArea();
        return "Circle: radius = " + radius + ", perimeter = " + getPerimeter() + ", area = " + getArea();
    }
}
