# Polimorfismo y Casting POO

### Lo primero es pensar en objetos reales.
Antes de empezar a **programar** debes dejar de pensar en código. Analiza primero. Piensa en objetos y situaciones reales. Esto con el fin de que entiendas mejor la lógica de todo esto y te sea más sencillo entender.  
  
### Polimorfismo y Herencia
La palabra en sí es relativa a **transformar** algo. Y en programación no cambia mucho ese mismo significado. Para entender mejor vayamos a un ejemplo.  
Supongamos que tenemos una clase **PADRE** llamada Empleado:  

**Java**

```java
public class Empleado {
  int sueldo = 0;  
}
```
**Dart**
```dart
class Empleado {
  int sueldo = 0;
}
```
Esta clase tiene solamente un atributo: un entero llamado **sueldo** en el cual, obviamente, guardaremos más adelante el sueldo de los empleados que vayamos creando. La llamamos clase **PADRE** porque de esta clase se van a **EXTENDER** todas las clases a las que le deseemos indexar el polimorfismo.  
  
A continuación crearemos dos clases más. Estas clases serás las **HIJAS** de la clase **Empleado**:  
  
**Java**
```java
public class Vigilante extends Empleado{
}
```
```java
public class Jefe extends Empleado{
}
```
**Dart**
```dart
class Vigilante extends Empleado{
}
```
```dart 
class Jefe extends Empleado{
}
```
Estas clases **heredan** y traen consigo todos los atributos y métodos de su clase **padre** **Empleado**. En este caso, ambas clases heredan todos los atributos y métodos de la clase Empleado. Y como la clase padre solo consta de un atributo, únicamente se hereda este mismo: la variable de tipo entero llamada *sueldo*.  
  
Saliéndonos un poco de la programación. En la vida real, en una empresa, existen un conjunto de personas que trabajan en dicho lugar. Dichas personas hacen parte de un conjunto al cual llaman **empleados** y estos mismos tienen una característica en común: Reciben una paga cada mes. Un *sueldo*  
  
Tomando esto como referencia, podemos decir entonces que todas las personas que trabajan para la empresa son una instancia de un Empleado y todas y cada una recibe un *sueldo*.  

Pero **no todos los empleados reciben la misma cantidad de paga**. Es importante saber cuánto gana cada empleado con respecto a su ocupación. Pero, ¿cómo lo sabremos?   

Para esto se usa el polimorfismo.  

Primero que todo debemos saber realizar la instancia. Para poder instanciar los objetos debemos estar dentro del método **principal** o *main*:  

*En Java tendremos que crear una nueva clase que contenga este método, en cambio, en Dart podremos ponerlo en un mismo archivo de código*
  
**Java**
```java
public class ClasePrincipal {
  public static void main(String args[]) {
    Empleado eJefe = new Jefe();
    Empleado eVigilante = new Vigilante();
    
  }
}
```
**Dart**
```dart
void main(){
  Empleado eJefe = Jefe();
  Empleado eVigilante = Vigilante();
}
```
Estamos haciendo algo simple de entender si lo enfocamos en la realidad. En este código le estamos diciendo al programa "Oye, quiero que crees un Empleado que se llame *eJefe* y dale las características que tiene un Jefe. También crea otro que se llame *eVigilante* y a este darle todas las características de un Vigilante". Básicamente, estamos, por así decirlo, clasificando a cada uno por su ocupación, pero sin sacarlo de su clasificación general: Ambos son *empleados*.  
  
Ya tenemos lo más importante, ahora viene la lógica.  
Nosotros queremos indicar cuál es el sueldo de cada empleado usando su ocupación como referencia. Para esto podríamos codificar lo siguiente:  
**Java**
```java
public class MetodoPagar {
  public void pagar(Empleado e) {
    if(e instanceof Jefe) {
      System.out.println("JEFE: Usted recibe $100");
    } else if(e instanceof Vigilante) {
      System.out.println("Vigilante: Usted recibe $50");
    }
  }
} 
```
**Dart**
```dart
void pagar(Empleado e) {
  if(e is Vigilante) {
    print('JEFE: Usted recibe: \$100');
  } else if(e is Jefe) {
    print("VIGILANTE: Usted recibe: \$50");
  }
}
```

Lo que hacemos aquí es simple. Primero estamos creando un método llamado ***pagar*** y le decimos que reciba como parámetro un empleado y lo guarde en una variable ***e***. Después, en la funcionalidad, le estamos pidiendo por medio de un *if* que verifique si el empleado *e* es un Jefe o, en otras palabras, que verifique si *e* es un **OBJETO EMPLEADO** que guarda los atributos de la **CLASE JEFE**. De ser verdadero, entonces que imprima en consola: "JEFE: Usted recibe: \$100". De ser falso, por otra parte, que verifique si el empleado es un vigilante o si el **OBJETO EMPLEADO** *e* es una instancia de la **CLASE VIGILANTE**. Ya con todo esto podemos ejecutar el programa y ver su resultado.  

**Código completo Java**
```java
public class Empleado {
  int sueldo = 0;  
}

public class Vigilante extends Empleado{
}

public class Jefe extends Empleado{
}

public class MetodoPagar {
  public void pagar(Empleado e) {
    if(e instanceof Jefe) {
      System.out.printl("JEFE: Usted recibe $100");
    } else if(e instanceof Vigilante) {
      System.out.printl("Vigilante: Usted recibe $50");
    }
  }
} 

public class ClasePrincipal {
  public static void main(String args[]) {
    Empleado eJefe = new Jefe();
    Empleado eVigilante = new Vigilante();
    
      //Creamos una instancia de la clase MetodoPagar. Llamamos y ejecutamos el método pagar de la clase y pasamos como parámetros el objeto 'eJefe' y el objeto 'eVigilante'

    MetodoPagar mpg = new MetodoPagar();
    mpg.pagar(eJefe);
    mpg.pagar(eVigilante);
  }
}
```
**Código completo Dart**

```dart
class Empleado {
  int sueldo = 0;
}

class Vigilante extends Empleado{
}

class Jefe extends Empleado{
}

void pagar(Empleado e) {
  if(e is Vigilante) {
    print('JEFE: Usted recibe: \$100');
  } else if(e is Jefe) {
    print("VIGILANTE: Usted recibe: \$50");
  }
}

void main(){
  Empleado eJefe = Jefe();
  Empleado eVigilante = Vigilante();
  
  //Llamamos y ejecutamos el método pagar de la clase pasando como parámetros los objetos que creamos anteriormente

  pagar(eJefe);
  pagar(eVigilante);
}
```

Consola:
```console
VIGILANTE: Usted recibe: $50
JEFE: Usted recibe: $100
```
