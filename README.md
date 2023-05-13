# Polimorfismo y Casting POO

### Lo primero es pensar en objetos reales.
Antes de empezar a **programar** debes dejar de pensar en código. Analiza primero. Piensa en objetos y situaciones reales. Esto con el fin de que entiendas mejor la lógica de todo esto y te sea más sencillo entender.  
  
### Polimorfismo y Herencia
La palabra en sí es relativa a **tranformar** algo. Y en programación no cambia mucho ese mismo significado. Para entender mejor vayamos a un ejemplo.  
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
}
```
Esta clase tiene solamente un atributo: un entero llamado **sueldo** en el cual, obviamente, guardaremos mas adelante el sueldo de los empleados que vayamos creando. La llamamos clase **PADRE** porque de esta clase se van a **EXTENDER** todas las clases a las que le deseemos indexar el polimorfismo.  
  
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
class Vigilante {
}
```
```dart 
class Jefe{
}
```
Estas clases **heredan** y traen consigo todos los atributos y metodos de su clase **padre** **Empleado**. En este caso ambas clases heredan todos los atributos y métodos de la clase Empleado. Y como la clase padre solo consta de un atributo, únicamente se hereda este mismo: la variable de tipo entero llamada *sueldo*.  
  
Saliéndonos un poco de la programación. En la vida real, en una empresa, existen un conjunto de personas que trabajan en dicho lugar. Dichas personas hacen parte de un conjunto al cual llaman **empleados** y estos mismos tienen una caracteristica en común: Reciben una paga cada mes. Un *sueldo*  
  
Tomando esto como referencia, podemos decir entonces que todas las personas que trabajan para la empresa son una instancia de un Empleado y todas y cada una recibe un *sueldo*.  

Pero **no todos los empleados reciben la misma cantidad de paga**. Es importante saber cuánto gana cada empleado con respecto a su ocupación. Pero, ¿como lo sabremos?   

Para esto se usa el polimorfismo.  

Primero que todo debemos saber realizar la instancia. Para poder instanciar los objetos debemos estar dentro del método **principal** o *main*:  

*En Java tendremos que crear una nueva clase que contenga este método, en cambio en Dart podremos ponerlo en una mismo archivo de código*
  
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
public main(){
  Empleado eJefe = Jefe();
  Empleado eVigilante = Vigilante();
}
```
Estamos haciendo algo simple de entender si lo enfocamos en la realidad. En este código le estamos diciendo al programa "Oye, quiero que crees un Empleado que se llame *eJefe* y dale las caracteristicas que tiene un Jefe. También crea otro que se llame *eVigilante* y a este dale todas las caracteristicas de un Vigilante". Básicamente estamos, por así decirlo, clasificando a cada uno por su ocupación, pero sin sacarlo de su clasificación general: Ambos son *empleados*.  
  
Ya tenemos lo mas importante, ahora viene la lógica.  
Nosotros queremos indicar cual es el sueldo de cada empleado usando su ocupación como referencia. Para esto podríamos codificar lo siguente:
  
**JAVA**
```java
public class MetodoPagar {
  public void pagar(Empleado e) {
    if(e instanceof Jefe) {
      System.out.printl("JEFE: Usted recibe $100");
    } else if(e instanceof Vigilante) {
      System.out.printl("Vigilante: Usted recibe $50");
    }
  }
} 
```

Un ejemplo más sencillo de comprender es decir que tenemos un conjunto camisetas. Este conjunto de camisetas las clasificamos por colores claros y colores oscuros. Al separarlas por el tipo de color ya estariamos creando las clases hijas (podríamos llamarlas ColorClaro y ColorOscuro) con sus propias caracteristicas. Sin embargo, al ser todas camisetas, todas pertenecen a su clase padre (a la cual podemos darle el nombre de Camiseta), por lo cual **TODAS** son camisetas.  
Bueno ya las tenemos clasificadas y sabemos a dónde pertenecen. Pero falta algo. En un caso super hipotetico (digo así porque ¿quién no va a saber hacer eso?) en el que queremos saber cuales camisas se pueden lavar con clorox y cuales no, es necesario consultar primero si la camisa soporta el clorox o no. 
