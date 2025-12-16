using System;

class Kompleks
{
    // yopiq a'zolar
    private double real;
    private double imag;

    // a) Bo'sh konstruktor
    public Kompleks()
    {
        real = 0;
        imag = 0;
    }

    // b) Nusxalash konstruktori
    public Kompleks(Kompleks k)
    {
        real = k.real;
        imag = k.imag;
    }

    // c) Parametrli konstruktor
    public Kompleks(double r, double i)
    {
        real = r;
        imag = i;
    }

    // d) O'qish (get)
    public double GetReal()
    {
        return real;
    }

    public double GetImag()
    {
        return imag;
    }

    // e) Yozish (set)
    public void SetReal(double r)
    {
        real = r;
    }

    public void SetImag(double i)
    {
        imag = i;
    }

    // + operatori
    public static Kompleks operator +(Kompleks a, Kompleks b)
    {
        return new Kompleks(a.real + b.real, a.imag + b.imag);
    }

    // - operatori
    public static Kompleks operator -(Kompleks a, Kompleks b)
    {
        return new Kompleks(a.real - b.real, a.imag - b.imag);
    }

    // * operatori
    public static Kompleks operator *(Kompleks a, Kompleks b)
    {
        return new Kompleks(
            a.real * b.real - a.imag * b.imag,
            a.real * b.imag + a.imag * b.real
        );
    }

    // / operatori
    public static Kompleks operator /(Kompleks a, Kompleks b)
    {
        double denom = b.real * b.real + b.imag * b.imag;
        return new Kompleks(
            (a.real * b.real + a.imag * b.imag) / denom,
            (a.imag * b.real - a.real * b.imag) / denom
        );
    }

    // Chiqarish funksiyasi
    public void Print()
    {
        if (imag >= 0)
            Console.WriteLine($"{real} + {imag}i");
        else
            Console.WriteLine($"{real} - {-imag}i");
    }

    // f) Destruktor
    ~Kompleks()
    {
        // Garbage Collector ishlaydi
    }
}

class Program
{
    static void Main()
    {
        Kompleks a = new Kompleks(3, 4);
        Kompleks b = new Kompleks(1, 2);

        Kompleks c;

        c = a + b;
        Console.Write("a + b = ");
        c.Print();

        c = a - b;
        Console.Write("a - b = ");
        c.Print();

        c = a * b;
        Console.Write("a * b = ");
        c.Print();

        c = a / b;
        Console.Write("a / b = ");
        c.Print();
    }
}
