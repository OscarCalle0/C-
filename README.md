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

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

GitHub

 1. Instalación de Git y Configuración Inicial
Antes de comenzar a usar GitHub con VS Code, asegúrate de tener Git instalado en tu sistema. Si no lo tienes, descárgalo e instálalo desde [git-scm.com](https://git-scm.com/).
 Configuración Inicial de Git
1. Configura tu nombre y correo electrónico (si es la primera vez que usas Git):
 sh
   git config --global user.name "Tu Nombre"
   git config --global user.email "tuemail@example.com"
 2. Integración de GitHub en Visual Studio Code
Visual Studio Code tiene integración incorporada con Git, y puedes realizar la mayoría de las operaciones de Git directamente desde la interfaz.
 1. Clonar un Repositorio Existente
1. Abre VS Code.
2. En la barra lateral izquierda, haz clic en el ícono de Source Control (Control de Código Fuente) o presiona `Ctrl+Shift+G`.
3. Haz clic en Clone Repository (Clonar Repositorio).
4. Ingresa la URL del repositorio GitHub y selecciona una carpeta local donde clonar el repositorio.

 2. Crear un Nuevo Repositorio
1. Abre VS Code y navega al proyecto que deseas convertir en un repositorio.
2. Abre la terminal integrada en VS Code (`Ctrl+` ` ` o Terminal > New Terminal).
3. Inicializa un nuevo repositorio Git:
 sh
   git init

4. Añade los archivos al área de preparación (staging area):
 sh
   git add .
 
5. Realiza el primer commit:
 sh
   git commit -m "Initial commit"
 
6. Crea un repositorio en GitHub a través de su interfaz web.
7. Conecta el repositorio local con GitHub:
 sh
   git remote add origin <URL-del-repositorio>
 
8. Sube tus cambios a GitHub:
 sh
   git push -u origin master
 
 3. Operaciones de Git: Commit, Push y Pull
 Desde la Interfaz Gráfica de VS Code
- Commit:
  1. Realiza cambios en tu proyecto.
  2. Ve a la vista de Source Control (`Ctrl+Shift+G`).
  3. Verás los archivos modificados. Escribe un mensaje de commit en el campo de texto en la parte superior.
  4. Haz clic en el ícono de check (confirmar) para hacer el commit.

- Push:
  1. Después de hacer un commit, ve a la vista de Source Control.
  2. Haz clic en los tres puntos (`...`) en la esquina superior derecha.
  3. Selecciona Push.

- Pull:
  1. Ve a la vista de Source Control.
  2. Haz clic en los tres puntos (`...`).
  3. Selecciona Pull para traer los cambios del repositorio remoto.
 Desde la Línea de Comandos
- Commit:
sh
  git add .
  git commit -m "Mensaje de commit"

- Push:
sh
  git push origin master

- Pull:
sh
  git pull origin master

 4. Manejo de Branches
Trabajar con ramas (branches) es común para gestionar diferentes características y versiones del proyecto.

- Crear una nueva rama:
sh
  git branch nombre-de-la-rama

- Cambiar a una rama:
sh
  git checkout nombre-de-la-rama


- Fusionar una rama:
  1. Cambia a la rama en la que deseas fusionar (generalmente `master` o `main`):
   sh
     git checkout master
   
  2. Fusiona la rama:
   sh
     git merge nombre-de-la-rama
   
- Eliminar una rama:
sh
  git branch -d nombre-de-la-rama

 5. Resolución de Conflictos
Si hay conflictos al hacer un `pull` o `merge`, VS Code te mostrará los archivos en conflicto. Puedes resolverlos directamente en el editor, luego agregar y hacer commit de los cambios.
1. Abre los archivos en conflicto.
2. Realiza las modificaciones necesarias para resolver el conflicto.
3. Añade los archivos modificados al área de preparación:
 sh
   git add archivo-en-conflicto
 
4. Haz un commit para completar la resolución del conflicto:
 sh
   git commit -m "Resolución de conflictos"

 6. Visualización de Cambios y Historial
- Ver cambios: En la vista de Source Control, puedes ver qué archivos han cambiado y qué líneas se han modificado.
- Historial de commits: Puedes usar la extensión GitLens en VS Code para una vista más detallada del historial de commits y otras funcionalidades avanzadas de Git.
 7. Configuración Adicional en VS Code
- Instalar la extensión de GitHub: Proporciona funcionalidades adicionales como la integración de GitHub Actions y pull requests.
- Configurar Git: Ajusta configuraciones específicas en el archivo `.gitconfig` para personalizar tu experiencia con Git.

 Resumen
- Clonar un repositorio desde GitHub.
- Inicializar un nuevo repositorio local y subirlo a GitHub.
- Realizar commits, push y pull desde la interfaz gráfica o línea de comandos.
- Manejar branches para diferentes versiones del proyecto.
- Resolver conflictos y ver el historial de commits.


-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 1. `echo "# C-" >> README.md`
Este comando agrega la línea `# C-` al archivo `README.md`. Si el archivo no existe, lo crea. El `#` en Markdown indica que es un encabezado de nivel 1.

 2. `git init`
Inicializa un nuevo repositorio de Git en el directorio actual. Crea un subdirectorio `.git` que contiene todos los archivos necesarios para el repositorio.
sh
git init

 3. `git add README.md`
Agrega el archivo `README.md` al área de preparación (staging area), lo que significa que está listo para ser incluido en el próximo commit.
sh
git add README.md

 4. `git commit -m "primer commit"`
Crea un commit con los cambios que están en el área de preparación y agrega un mensaje descriptivo "primer commit".
sh
git commit -m "primer commit"

 5. `git branch -M main`
Renombra la rama actual a `main`. Este comando se usa comúnmente para renombrar la rama principal por defecto de `master` a `main`.
sh
git branch -M main

 6. `git remote add origin https://github.com/OscarCalle0/C-.git`
Agrega un repositorio remoto llamado `origin` con la URL especificada. Este repositorio remoto es donde los cambios se empujarán (push) más adelante.
sh
git remote add origin https://github.com/OscarCalle0/C-.git

 7. `git push -u origin main`
Empuja los cambios a la rama `main` del repositorio remoto `origin` y establece `origin/main` como la rama por defecto para `push` y `pull`.
Sh
git push -u origin main

 8. `git remote add origin https://github.com/OscarCalle0/C-.git`
Este comando es redundante porque ya se ejecutó anteriormente, y simplemente establece el repositorio remoto otra vez.

 9. `git branch -M principal`
Renombra la rama actual a `principal`. Este es un intento de cambiar el nombre de la rama principal en español. Sin embargo, debes asegurarte de que este comando se ejecute en el contexto correcto, después de cambiar el nombre de la rama a `main`.
sh
git branch -M principal

 10. `git push -u origin principal`
Empuja los cambios a la rama `principal` del repositorio remoto `origin` y establece `origin/principal` como la rama por defecto para `push` y `pull`.
sh
git push -u origin principal

 Resumen del flujo de trabajo
1. Inicialización y Preparación Local:
- Crear un archivo `README.md` con contenido inicial.
- Inicializar un nuevo repositorio de Git.
- Agregar el archivo `README.md` al área de preparación.
- Realizar el primer commit con un mensaje.
2. Configuración del Repositorio Remoto:
- Renombrar la rama principal a `main`.
- Agregar un repositorio remoto llamado `origin`.
3. Empujar Cambios al Repositorio Remoto:
- Empujar los cambios a la rama `main` del repositorio remoto.
- (Opcional) Renombrar la rama principal a `principal` y empujar los cambios.



