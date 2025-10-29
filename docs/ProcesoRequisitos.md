<div align=center>

|Observar||Conceptualizar||Decidir||Construir||Ejecutar|
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
|[Modelo del dominio](/docs/modeloDelDominio.md)|>>|[***Requisitos***](/docs/ProcesoRequisitos.md)|>>|[Análisis](/docs/ProcesoAnalisis.md)|>>|[Decisiones tecnológicas](/docs/DecisionesTecnologicas.md)|>>|[Diseño](/docs/ProcesoDiseño.md)|>>|[Código](/src/)

</div>

# Proceso de Requisitos: Tetris

Los requisitos especifican QUÉ debe hacer el sistema desde la perspectiva del usuario, sin contaminación de decisiones de implementación. Transforman los conceptos del dominio en comportamientos concretos del software.

## Metodología

### Punto de partida: modelo del dominio

Los requisitos parten del modelo del dominio que identificó conceptos del mundo real:

- Juego, Tablero, Pieza, TipoPieza
- Celda, Línea, Movimiento, Turno

**Pregunta central**: ¿Qué solicitudes puede realizar un actor externo al sistema utilizando estos conceptos?

### Actores

**Técnica**: Análisis de entidades externas que interactúan con el sistema

<div align=center>

|Actor|Descripción|Justificación|
|-|-|-|
|Jugador|Persona que controla el juego|Solicita manipulación de piezas y gestión de partida|
|Tiempo|Disparador temporal|Solicita descenso automático de piezas según intervalo configurado|

</div>

### Casos de Uso

**Técnica**: Análisis de objetivos que cada actor busca alcanzar

Del modelo del dominio surge:

<div align=center>

|Comportamiento identificado|¿Quién lo solicita?
|-|:-:|
|arrancarSistema()|Jugador |
|iniciarPartida()|Jugador |
|cancelarPartida()|Jugador |
|moverPieza()|Jugador
|rotarPieza()|Jugador
|alternarVelocidadCaida()|Jugador
|descenderPieza()|Tiempo


|![](/images/modelosUML/DiagramaCasosUso.svg)
|:-:
|[Código plantUML](/modelosUML/DiagramaCasosUso.puml)

</div>

### Presentar el modelo de casos de uso como un todo

#### Estados del sistema

<div align=center>

|![](/images/modelosUML/DiagramaDeContexto000.svg)
|:-:
|[Código plantUML](/modelosUML/DiagramaDeContexto000.puml)

</div>

#### Diagramas de contexto

<div align=center>

|Jugador<br>![](/images/modelosUML/DiagramaDeContexto001-ActorJugador.svg)
|:-:
|[Código plantUML](/modelosUML/DiagramaDeContexto001-ActorJugador.puml)


|Tiempo<br>![](/images/modelosUML/DiagramaDeContexto001-ActorTiempo.svg)
|:-:
|[Código plantUML](/modelosUML/DiagramaDeContexto001-ActorTiempo.puml)


</div>

### Detallar casos de uso

#### descenderPieza()

<div align=center>

|![](/images/modelosUML/detalleCasosUso/descenderPieza.svg)
|:-:
|[Código plantUML](/modelosUML/detalleCasosUso/descenderPieza.puml)

</div>

#### iniciarPartida()

<div align=center>

|![](/images/modelosUML/detalleCasosUso/iniciarPartida.svg)
|:-:
|[Código plantUML](/modelosUML/detalleCasosUso/iniciarPartida.puml)

</div>

#### moverPieza()

<div align=center>

|![](/images/modelosUML/detalleCasosUso/moverPieza.svg)
|:-:
|[Código plantUML](/modelosUML/detalleCasosUso/moverPieza.puml)

</div>

#### cancelarPartida()

<div align=center>

|![](/images/modelosUML/detalleCasosUso/cancelarPartida.svg)
|:-:
|[Código plantUML](/modelosUML/detalleCasosUso/cancelarPartida.puml)

</div>

#### rotarPieza()

<div align=center>

|![](/images/modelosUML/detalleCasosUso/rotarPieza.svg)
|:-:
|[Código plantUML](/modelosUML/detalleCasosUso/rotarPieza.puml)

</div>

#### alternarVelocidadCaida()

<div align=center>

|![](/images/modelosUML/detalleCasosUso/alternarVelocidadCaida.svg)
|:-:
|[Código plantUML](/modelosUML/detalleCasosUso/alternarVelocidadCaida.puml)

</div>

#### arrancarSistema()

<div align=center>

|![](/images/modelosUML/detalleCasosUso/arrancarSistema.svg)
|:-:
|[Código plantUML](/modelosUML/detalleCasosUso/arrancarSistema.puml)

</div>

### Prototipar casos de uso

<div align=center>

|![](/images/tetris.png)
|:-:
|

</div>

No se trata de documentar por documentar. La imagen del README, visible desde el principio, nos deja claro:

- Cómo se ve el juego (estado EN_CURSO)
- Cómo interactúa el usuario (teclas 4, 6, 7, 9)
- Qué información presenta el sistema (tablero, score)

Para los demás casos de uso:

- iniciarPartida(): arranca el juego → se ve el tablero
- descenderPieza(): automático, se ve la pieza bajando
- alternarVelocidadCaida(): la pieza cae más rápido (observable en velocidad)
- cancelarPartida(): vuelve al inicio

Todo está implícito y claro con esa única imagen: agregar más sería redundante.
