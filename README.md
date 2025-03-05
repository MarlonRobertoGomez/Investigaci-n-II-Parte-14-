Open/Closed Principle (OCP) - Principio Abierto/Cerrado
// Incorrecto: Modificar la clase cada vez que se agrega un nuevo tipo de cálculo.
public class AreaCalculator
{
    public double CalculateArea(string shape, double size)
    {
        if (shape == "circle") return Math.PI * size * size;
        else if (shape == "square") return size * size;
        return 0;
    }
}

// Correcto: Usar polimorfismo para permitir la extensión sin modificar la clase existente.
public abstract class Shape
{
    public abstract double CalculateArea();
}

public class Circle : Shape
{
    public double Radius { get; set; }
    public Circle(double radius) => Radius = radius;
    public override double CalculateArea() => Math.PI * Radius * Radius;
}

public class Square : Shape
{
    public double Side { get; set; }
    public Square(double side) => Side = side;
    public override double CalculateArea() => Side * Side;
}
