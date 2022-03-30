# Reforcing Learning
Elementor comunes para tareas de control, como pueden ser el ajedees, un brazo mecanico o el pacman, pare realizar una tarea:  los elementos son:

## Estado
<img src="https://latex.codecogs.com/svg.image?S_t" /><br />
Toda informacion relevante que describe en que situacion esta<br />

## Acctiones
<img src="https://latex.codecogs.com/svg.image?A_t" /><br />
Acciones que son llevadas a cabo durante la tarea, las acciones se escojen en base al estado de la tarea

## Recompensa
<img src="https://latex.codecogs.com/svg.image?R_t" /><br />
UN valo numerico que el agente recibe luego de llevar a cabo una accion, determina el efecto inmediato de haber llevado a cabo esa accion

## Agente
La entidad que va a participar en la tarea, observando su **estado** y llevando a cabo **acciones** en cada momento del tiempo

## Entorno
Todos los aspectos de la tarea que el agente no conoce, 

# Procesos de desicion de Markov (MDP)
- Estados futuros dependen solo parcialmente de las acciones
- El proceso avanza en intervalos infinitos 
<br /><br />
El agente, interactua con el entorno, observa el estado y ejecuta una accion, esa accion modifica el estado y recibe una recompensa del entorno, que le da una devolucion para saber si la accion fue buena o no<br />
<p align="center" width="100%">
<img src="images/1.png" width="50%" a="center"/>
</p>
<img src="images/2.png" /><br />
<img src="images/3.png" /><br />

*Cuando esta en S1 el agente toma una accion, tiene el %10 de ir a la accion S0 y un %90 de volver a la S1*
<img src="images/4.png" /><br />

<br />

Hay 2 tipos de procesos:
- finitos: acciones, estados y recompensas son finitas
- infinitos: una o mas de estas 3 variables son infinitos
<br />
Los procesos pueden ser:
- Episodicos: Termina bajo unas ciertas condiciones
- Continuos: No tiene una condicion para terminar, su ejecucion es infinita
<br />

## Trayectoria
Rastro que se genera cuando un agente se mueve<br />
<img src="images/5.png" /><br />
<br />

## Episodio
Comienza en el estado inicial y termina en el estado final<br />
<img src="images/6.png" /><br />
<br />

## Recompensa
Resultado inmediato que produce nuestras acciones<br />


## Retorno
Suma de recompensa que el agente obtiene, en el ajedrez si comemos una ficha podemos dejar descubierto al rey<br />

## Factor de descuento
Podemos multiplicar las recompensas por u factor de descuento (gama elevada a un momento del tiempo en que se consigue), de esa forma vamos a buscar el camino lo antes posible<br />
cuando gama es mas cerca a cero el agente va a tratar de llegar lo mas rapido posible<br />
<img src="images/7.png" /><br />

## Politica de accion
Una funcion que decide que accion tomar<br />
<img src="images/8.png" /><br />
<img src="images/9.png" /><br />

- Determinista: siempre escoje la misma accion
- Estocastica: escoje una accion en base a unas determinadas probabilidades
<br />
Tenemos que hallar la politica optima, la vamos a llamar como pi*
<br />
<img src="images/10.png" /><br />
q-valor, es el retorno que esperamos obtener si partiendo de ese estado tomamos la accion especificada<br />
<img src="images/11.png" /><br />

## Ecuacion Bellman
Generamos una relacion recursiva entre su estado y los estados sucesores
<p align="center" width="100%"><img src="images/12.png" width="100%" a="center"/> </p>

# Librerias

## gym
nos proporciona una interface a las tareas de control que queremos resolver, tambien podemos realizar customizaciones como lo hicimos en el archivo *2022-03-Reinforcement-learning/beginner_master_rl/envs.py* (hicimos un laberinto)

# Programacion dinamica
Consiste en resolver los problemas mas pequeños para encontrar la politica mas oprima.<br />
La **solucion** optima a todos los **subproblemas** produce la solucion optima del problema **original**<br />
<p align="center" width="100%"><img src="images/13.png" width="100%" a="center"/> </p>
POdemos encontrar la politica optima para cada estado, cuando tengamos todas podemos combinarlas para optener la politica optima<br/>
<p align="center" width="100%"><img src="images/14.png" width="100%" a="center"/> </p>
Dependen mutuamente<br />
<p align="center" width="100%"><img src="images/15.png" width="100%" a="center"/> </p>
Vamos a tener una tabla con una entrada para cada una de las entradas de valores que va a ir mejorando.<br />
Estado a la derecha por ejemplo<br />
<p align="center" width="100%"><img src="images/16.png" width="100%" a="center"/> </p>
Funciona solo cuando tenemos un modelo perfecto a la tarea que nos enfrentamos, todo lo que esperamos.<br />
Con un auto es diferente (por ejemplo), pueden pasar muchas cosas que no nos esperamos<br />
Resuelve problemas mediante valores esperados, no a base de ensayo y error<br />
<p align="center" width="100%"><img src="images/17.png" width="100%" a="center"/> </p>
Por cada paso recibe una recompensa de -1, tiene que encontrar la salida mas corta
<p align="center" width="100%"><img src="images/18.png" width="100%" a="center"/> </p>
siguiente interacion, siguen acercandose a sus valores optimos<br />

- r + g*V(s')
- -1 + (0.99 * 0)
- -1 + (0.99 * -1)
- -1 + (0.99 * -1.99)

<p align="center" width="100%"><img src="images/19.png" width="100%" a="center"/> </p>
<p align="center" width="100%"><img src="images/20.png" width="100%" a="center"/> </p>
<p align="center" width="100%"><img src="images/21.png" width="100%" a="center"/> </p>
<p align="center" width="100%"><img src="images/22.png" width="100%" a="center"/> </p>


## Iteracion de politica
Tanto la funcion valor, como la politica, se iran acercando al valor optimo
<p align="center" width="100%"><img src="images/23.png" width="100%" a="center"/> </p>


