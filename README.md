# C#
Apuntes c#


 1. Conceptos Fundamentales de POO
Programación Orientada a Objetos (POO) es un paradigma de programación basado en el concepto de "objetos", que pueden contener datos en forma de campos (a menudo conocidos como atributos o propiedades) y código en forma de métodos. Los conceptos clave de POO incluyen:
- Abstracción
- Encapsulamiento
- Herencia
- Polimorfismo
 2. Palabras Reservadas en C# Relacionadas con POO
Aquí están las palabras reservadas más relevantes para la POO en C#:
- `class`: Define una clase.
- `interface`: Define una interfaz.
- `abstract`: Declara una clase o método abstracto.
- `virtual`: Permite que un método sea sobrescrito en una clase derivada.
- `override`: Permite que un método en una clase derivada reemplace una implementación base.
- `new`: Define un nuevo miembro en una clase derivada que oculta un miembro de la clase base.
- `public`, `private`, `protected`, `internal`, `protected internal`: Modificadores de acceso que controlan la visibilidad de clases, métodos y atributos.
 3. Abstracción
Abstracción es el proceso de ocultar los detalles complejos y mostrar solo la funcionalidad necesaria. En C#, se utiliza principalmente a través de clases abstractas y métodos abstractos.
- Clase Abstracta: No se puede instanciar directamente. Sirve como base para otras clases. Contiene métodos abstractos y no abstractos.
public abstract class Animal
  {
      public abstract void MakeSound(); // Método abstracto
  }

- Método Abstracto: Se declara en una clase abstracta y debe ser implementado por cualquier clase derivada.
 public class Dog : Animal
  {
      public override void MakeSound()
      {
          Console.WriteLine("Bark");
      }
  }
 4. Encapsulamiento
Encapsulamiento es el proceso de envolver datos y métodos que operan en esos datos en una sola unidad, o clase. Esto asegura que los datos internos de un objeto estén ocultos y solo accesibles a través de métodos públicos.
- Propiedades: Permiten el acceso controlado a los campos de una clase.
  public class Person
  {
      private string name; // Campo privado
      public string Name // Propiedad pública
      {
          get { return name; }
          set { name = value; }
      }
  }

- Métodos Públicos: Permiten realizar operaciones en los datos encapsulados.
  public class BankAccount
  {
      private decimal balance;
      public void Deposit(decimal amount)
      {
          if (amount > 0)
          {
              balance += amount;
          }
      }

      public decimal GetBalance()
      {
          return balance;
      }
  }
 5. Herencia
Herencia es un mecanismo que permite crear una nueva clase basada en una clase existente. La nueva clase hereda los miembros (métodos y propiedades) de la clase base y puede añadir nuevos miembros o sobrescribir los existentes.
- Clase Base: La clase que es heredada por otras clases.
  public class Animal
  {
      public void Eat()
      {
          Console.WriteLine("Eating...");
      }
  }

- Clase Derivada: La clase que hereda de la clase base.
  public class Dog : Animal
  {
      public void Bark()
      {
          Console.WriteLine("Bark");
     }
  }
- Sobrescritura de Métodos: Se usa el modificador `virtual` en la clase base y `override` en la clase derivada.
  public class Animal
  {
      public virtual void MakeSound()
      {
          Console.WriteLine("Some sound");
      }
  }

  public class Dog : Animal
  {
      public override void MakeSound()
      {
          Console.WriteLine("Bark");
      }
  }
 6. Polimorfismo
Polimorfismo permite que un método tenga diferentes comportamientos en función del objeto que lo invoca. Hay dos tipos principales:
- Polimorfismo de Tiempo de Ejecución: Implementado mediante herencia y sobrescritura de métodos.
  Animal myAnimal = new Dog();
  myAnimal.MakeSound(); // Imprime "Bark"
- Polimorfismo de Tiempo de Compilación: Logrado a través de sobrecarga de métodos y operadores.
  public class MathOperations
  {
      public int Add(int a, int b)
      {
          return a + b;
      }

      public double Add(double a, double b)
      {
          return a + b;
      }
  }

 7. Interfaces
Las interfaces definen un contrato que las clases deben implementar. Las interfaces no pueden contener implementación de métodos.
- Definición de Interfaz:
  public interface IShape
  {
      double GetArea();
  }
- Implementación de Interfaz:
  public class Circle : IShape
  {
      public double Radius { get; set; }

      public double GetArea()
      {
          return Math.PI * Radius * Radius;
      }
  }
 8. Uso de Tipos de Datos
En C#, los tipos de datos se dividen en dos categorías principales:
- Tipos de Valor: Incluyen tipos básicos como `int`, `float`, `double`, `bool`, y `structs`. Estos se almacenan en la pila (stack) y tienen una copia propia de los datos.
  int number = 5;
- Tipos de Referencia: Incluyen tipos como `string`, `class`, `array`, y `interface`. Estos se almacenan en el montón (heap) y las variables contienen una referencia al objeto en la memoria.
  string name = "John";
 9. Constructores y Destructores
- Constructores: Métodos especiales que se llaman al crear una instancia de una clase. Se usan para inicializar los campos de la clase.
  public class Person
  {
      public string Name { get; set; }

      public Person(string name)
      {
          Name = name;
      }
  }
- Destructores: Métodos especiales que se llaman al destruir una instancia de una clase. En C#, los destructores se usan menos debido al recolector de basura.
  public class Person
  {
      ~Person()
      {
          // Código de limpieza
      }
  }

 10. Ejemplos Prácticos
Aquí hay un ejemplo de una clase completa que muestra cómo se integran estos conceptos:
using System;
namespace PooExample
{
    public abstract class Animal
    {
        public abstract void MakeSound();

        public void Sleep()
        {
            Console.WriteLine("Sleeping...");
        }
    }

    public class Dog : Animal
    {
        public override void MakeSound()
        {
            Console.WriteLine("Bark");
        }
    }

    public interface IShape
    {
        double GetArea();
    }

    public class Circle : IShape
    {
        public double Radius { get; set; }

        public double GetArea()
        {
            return Math.PI * Radius * Radius;
        }
    }

    class Program
    {
        static void Main()
        {
            Animal myDog = new Dog();
            myDog.MakeSound();
            myDog.Sleep();

            IShape myCircle = new Circle { Radius = 5 };
            Console.WriteLine($"Area of the circle: {myCircle.GetArea()}");
        }
    }
}
 Resumen
- Abstracción: Oculta los detalles internos y muestra solo la funcionalidad necesaria.
- Encapsulamiento: Envuelve datos y métodos en una clase, protegiendo el acceso a los datos internos.
- Herencia: Permite que una clase derive de otra y herede sus miembros.
- Polimorfismo: Permite que un método tenga diferentes comportamientos según el contexto.


