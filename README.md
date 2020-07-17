# CorrectorDeExamenesDDS

### Perdon por lo incompleto, hice lo que pude con el tiempo que tuve.

Diagrama de clases:
<br>
<img src = "diagramaDeClasesCorrectorDeExamenes.png">

```java
Class Parcial{
int aprobacion; // Nota minima de aprobacion

List<Pregunta> preguntas; 
//Asumo que por constructor se me dan las preguntas del examen, o puedo tener un setter de preguntas.

int calcularNota(){
return this.puntajetotal() - aprobacion;
}

int puntajeTotal(){
return this.preguntas().sum(unaPregunta -> unaPregunta.puntajeObtenido());
}
}

Class Pregunta{
int peso;
int puntajeObtenido;
TipoPregunta tipo;
int puntajeObteido(){
return puntajeObtenido;
}
}

Enum TipoPregunta{
MultipleChoise, VoF ,PreguntaConcreta
}

```

Para agregar los cambios siguientes:
* las preguntas mal contestadas no suman, 
* restan la mitad de su valor, o bien 
* descuenta 1 punto del total.

Debería agregar un campo a las preguntas para saber si están bien o mal, ya que mi solución contempla si una pregunta concreta está "mal pero no tan mal".

* Las preguntas mal contestadas no suman:

```java
Class Pregunta{
bool estaBien;

  bool estaBienRespondida(){
  return estaBien;
  }
}

int puntajeObtenido(){
return this.preguntas().filter(unaPregunta -> unaPregunta.estaBienRespondida()).sum(unaPregunta ->unaPregunta.puntajeObtenido);
}
```
* restan la mitad de su valor
```java
Class Pregunta{
int puntajeObtenido(){
if(estaBien)
return puntajeObtenido;
else
return -(peso/2);
}
}
```

* descuenta 1 punto del total
```java
Class Pregunta{
int puntajeObtenido(){
if(estaBien)
return puntajeObtenido;
else
return -peso;
}
}
