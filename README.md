# DiagramaEstado6.3.2

***Código Diagrama Estados***
```
@startuml
[*] --> StandBy
StandBy --> ValidandoTarjeta: Tarjeta introducida
ValidandoTarjeta --> StandBy: Tarjeta inválida
ValidandoTarjeta --> IngresoPIN: Tarjeta válida

IngresoPIN --> IngresoPIN: PIN incorrecto (Intentos < 3)
IngresoPIN --> TarjetaObstruida: Usuario inválido (Intentos = 3)
IngresoPIN --> SeleccionTransaccion: Usuario validado
IngresoPIN --> StandBy: Cancelar autenticación

TarjetaObstruida --> [*]

SeleccionTransaccion --> EjecutandoTransaccion: Seleccionar transacción
SeleccionTransaccion --> StandBy: Cancelar interacción

EjecutandoTransaccion --> SeleccionTransaccion: Transacción finalizada

@enduml
```
***Explicación diagrama***

El diagrama refleja un sistema de un cajero en donde se inserta una tarjeta la cuál tiene que ser validada y a continuación, tras ser aceptada junto al PIN correcto, se permite realizar una transacción o acabar la sesión.

El programa empieza en estado Stand-By, en donde no hay ninguna tarjeta insertada. Seguidamente, se introduce una tarjeta y se valida para ver si es real. Si no lo es, esta se expulsa. Si al contrario, sí que es real, se pide el PIN de la misma para comprobar si se puede acceder a su cuenta. Si en tres intentos el usuario introduce un PIN incorrecto, la tarjeta será retenida dentro del cajero por motivos de seguridad. Sin embargo, si el PIN es correcto en menos de 3 intentos, se accederá al apartado de realizar una transacción. Se selecciona una transacción y esta se ejecutará y finalizará. Tras la finalización, el cajero vuelve al apartado de realizar una transacción. Cuando el usuario decida terminar la sesión, tan solo debe cancelar la interacción y la tarjeta saldrá del cajero a la vez que este vuelve al estado de Stand-By.
