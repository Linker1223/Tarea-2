# Tarea 2
## 2.1 Declaración de clases: atributos, métodos, encapsulamiento.
*Básicamente las clases son una estructura de datos que encapsula un cumulo de datos y  comportamientos que forman un conjunto como una unidad lógica. Los datos y comportamientos son los miembros de la clase o estructura, e incluyen sus métodos, propiedades y eventos, entre otros elementos, como se muestra más adelante en este tema.*


*Una declaración de clase o estructura es como un plano que se utiliza para crear instancias u objetos en tiempo de ejecución. Si define una clase o estructura llamada Person, Person es el nombre del tipo. Si declara e inicializa una variable **p** de tipo Person, se dice que p es un objeto o instancia de Person. Se pueden crear varias instancias del mismo tipo Person, y cada instancia tiene diferentes valores en sus propiedades y campos.*

*Una clase es un tipo de referencia. Cuando se crea un objeto de la clase, la variable a la que se asigna el objeto contiene solo una referencia a esa memoria. Cuando la referencia de objeto se asigna a una nueva variable, la nueva variable hace referencia al objeto original.*

*Una estructura es un tipo de valor. Cuando se crea una estructura, la variable a la que se asigna la estructura contiene los datos reales de ella. Cuando la estructura se asigna a una nueva variable, se copia.*

*En general, las clases se utilizan para modelar comportamientos más complejos, o datos que se prevén modificar después de haber creado un objeto de clase. Las estructuras son más adecuadas para las estructuras de datos pequeñas que contienen principalmente datos que no se prevén modificar después de haber creado la estructura.*

### Encapsulacion
*A veces se hace referencia a la encapsulación como el primer pilar o principio de la programación orientada a objetos. Según el principio de encapsulación, una clase o una estructura pueden especificar hasta qué punto se puede acceder a sus miembros para codificar fuera de la clase o la estructura. No se prevé el uso de los métodos y las variables fuera de la clase.*
  - Modelado:
*Todos los métodos, campos, constantes, propiedades y eventos deben declararse dentro de un tipo; se les denomina miembros del tipo.*
- Accesibilidad: 
*Algunos métodos y propiedades están diseñados para ser invocables y accesibles desde el código fuera de la clase o la estructura, lo que se conoce como código de cliente. Otros métodos y propiedades pueden estar indicados exclusivamente para utilizarse en la propia clase o estructura. Puede usar los modificadores de acceso public, protected, internal, protected internal, private y private protected para especificar hasta qué punto los tipos y sus miembros son accesibles para el código de cliente.*
- Herencia:
*Las clases (pero no las estructuras) admiten el concepto de herencia. Una clase que deriva de otra clase (la clase base) contiene automáticamente todos los miembros públicos, protegidos e internos de la clase base, salvo sus constructores y finalizadores.*
- Tipos genericos: 
*Las clases y estructuras pueden definirse con uno o varios parámetros de tipo. El código de cliente proporciona el tipo cuando crea una instancia del tipo. Por ejemplo, la clase List < T > del espacio de nombres System.Collections.Generic se define con un parámetro de tipo.*
- Tipos estaticos:
*Las clases (pero no las estructuras) pueden declararse como static. Una clase estática puede contener solo miembros estáticos y no se puede crear una instancia de ellos con la palabra clave new.*

Y hay mas pero eso es para otro dia.

## 2.2 Instanciación de una clase.
*Es usado para crear objetos o invocar constructores.*
- *El operador new también se usa para invocar el constructor predeterminado para tipos de valor. Por ejemplo: int i = new int();*

## 2.3 Referencia al objeto actual.   

        class Rectangulo
        
    {
    //le puse vase por que no funcionaba base xd
    
        private int vase;
        private int altura;
        public Rectangulo(int vase, int altura)
        {
            this.vase = vase;
            this.altura = altura;
        }

        public int Vase
        {
            get{return vase;}
            set{vase = value;}
        }
        public int Altura
        {
            get{return altura;}
            set{altura = value;}
        }
        public void Imprimir()
        {
        //Aqui esta el "this." como parametro
            Console.WriteLine(Perimetro.CalcularPerimetro(this));
        }
    }
    class Perimetro
    {   
        public static double CalcularPerimetro(Rectangulo x)
        {
            return x.Vase*2 + x.Altura*2;
        }
    }
    class Program
    {
        static void Main(string[] args)
        {
        Rectangulo x = new Rectangulo(5,6);
        x.Imprimir(); 
        }
    }

## 2.4 Métodos: declaración, mensajes, paso de parámetros, retorno de valores.
1. *Los parámetros declarados para un método sin in, ref o out se pasan al método llamado por valor. Ese valor se puede cambiar en el método, pero el cambio se perderá cuando se devuelva el control al procedimiento que ha realizado la llamada. Si usa palabras clave de parámetros de método en la declaración del parámetro, puede modificar este comportamiento.*
*Estas son las palabras clave que puede usar para declarar parámetros de métodos:*
- **params**: *Especifica que este parámetro puede tomar un número variable de argumentos.
in especifica que este parámetro se pasa por referencia, pero solo se lee mediante el método llamado.*
- **ref**: *Especifica que este parámetro se pasa por referencia y puede ser leído o escrito por el método llamado.*
- **out**: *Especifica que este parámetro se pasa por referencia y se escribe mediante el método llamado.*

//(No creo que esto se pueda resumir mas en realidad)

2. *Mediante el uso de la palabra clave **params**, puede especificar un parámetro de método que toma un número variable de argumentos. Puede enviar una lista separada por comas de argumentos del tipo especificado en la declaración de parámetro o una matriz de argumentos del tipo especificado. También puede no enviar ningún argumento. El tipo declarado del parámetro **params** debe ser una matriz unidimensional, como se muestra en el ejemplo siguiente.*

3. *Puede usar la palabra clave out en dos contextos:*
- *Como un modificador de parámetro, que le permite pasar un argumento a un método mediante una referencia en lugar de mediante un valor.*
- *En declaraciones de parámetro de tipo genérico para interfaces y delegados, que especifica que un parámetro de tipo es covariante.*

4. *La palabra clave ref indica un valor que se ha pasado mediante referencia. Se usa en cuatro contextos diferentes:*
- *En una firma del método y en una llamada al método, para pasar un argumento a un método mediante referencia.*
- *En una firma del método, para devolver un valor al autor de la llamada mediante referencia.*
- *En un cuerpo de miembro, para indicar que un valor devuelto de referencia se almacena localmente como una referencia que el autor de la llamada pretende modificar o, en general, que una variable local accede a otro valor por referencia.*
- *En una declaración **struct** para declarar **ref struct** o **ref readonly struct.***

## 2.5 Constructores y destructores: declaración, uso y aplicaciones.
*Los constructores son métodos de clase que se ejecutan cuando se crea un objeto de un tipo determinado. Los constructores tienen el mismo nombre que la clase y, normalmente, inicializan los miembros de datos del nuevo objeto.*
*Esta clase crea instancias con el operador **new.***

    public class Taxi

    {

        public bool isInitialized;
        public Taxi()
        {
            isInitialized = true;
        }
    }

    class TestTaxi
    {
        static void Main()
        {
            Taxi t = new Taxi();
            Console.WriteLine(t.isInitialized);
        }
    }

*El operador **new** invoca el constructor **Taxi** inmediatamente después de asignar la memoria al nuevo objeto.*
*Los constructores predeterminados se invocan cada vez que se crea una instancia de un objeto mediante el operador **new** y no se proporciona ningún argumento a **new**.*

## 2.6 y 2.7
No supe como hacerlo, soy una desgracia </3

Eso es toda mi tarea por mi parte.
