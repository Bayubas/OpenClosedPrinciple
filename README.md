# OpenClosedPrinciple
Open / Closed Principle artinya sebuah class harus bisa di-extend, tapi harus juga tertutup untuk modifikasi.

# AboutProgram
- Source code ini memilike 2 program, yaitu Coupon With OCP dan Coupon Without OCP
- Pada bagian Coupon With OCP, kita menggunakan Abstraction, jadi kita dapat mengubah object menjadi object lain tanpa harus meninggalkan fungsi sesungguhnya.
- Sedangkan pada bagian CouponWithoutOCP, jika kalian mengubah salah satu fungsi maka akan memengaruhi fungsi lain.
- Program ini berjalan pada console, sehingga bisa dijalankan dengan run without debug.

# Coupon With OCP
- class Coupon.cs
 ```csharp
 public abstract class Coupon
  {
      public abstract double calculate(double originPrice);
  }
  ```
  - class Coupon with nominal.cs
  
  ```csharp
  class CouponWithNominal 
    {
        public double discNominal;

        public CouponWithNominal(double discNominal)
        {
            this.discNominal = discNominal;
        }

        public override double calculate(double originPrice)
        {
            return originPrice - discNominal;
        }
    }
  ```
- class Program.cs
  
  ```csharp
  {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
            Coupon coupon1 = new CouponWithNominal(2000);
            Console.WriteLine(coupon1.calculate(10000));
        }
    }
    ```

# Class Without OCP

- class Coupon.cs

```csharp
public abstract class Coupon
  {
      public abstract double calculate(double originPrice);
  }
  ```

- class Coupon

```csharp
    {
        public double discNominal = 0;
        public double priceNett(double originPrice)
        {
            double net = 0;
            net = (100 - discPercentage) * originPrice / 100;
            return net;
        }
    }
    ```
    
 - class Program
 
 ```csharp
 class Program
  {
      static void Main(string[] args)
      {


          Coupon coupon1 = new Coupon();
          coupon1.discNominal = 2000;
          Console.WriteLine(coupon1.priceNett(10000));
      }
  }
  ```

  
  
