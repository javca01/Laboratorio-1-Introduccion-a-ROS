# Laboratorio-1-Introduccion-a-ROS
En esta práctica se mostrará el proceso de conexión de Matlab con ROS empleando el paquete Hello Turtle, también se mencionará el procedimiento para crear un Script en Python para manipular el movimiento de la tortuga por medio de un conjunto de teclas determinado.

Conexión de Matlab con ROS

Empezaremos iniciando 2 terminales, en la primera lanzaremos el nodos maestro con el comando roscore y en la segunda colocaremos el comando rosrun turtlesim turtlesim_node para inicializar un nodo del paquete.

En la primera terminal colocamos el comando roscore.

XXXXXXXXXX

En la segunda terminal colocamos el comando rosrun turtlesim turtlesim_node.

XXXXXXXX

Vemos como emerge una tortuga en un canvas de fondo azul.

XXXXXXX

Posteriormente desde Matlab, lanzaremos una instancia para linux, a través de la ejecución de las siguiente sentencias.

XXXXXXX


Al ejecutar las sentencias anteriores realizamos la conexión con el nodo maestro de ROS, creamos un publicador y un objeto de mensaje vinculado a dicho publicados, a través del objeto mensaje, podemos manipular los atributos posicionales de la tortuga, en este caso la posición en X, a la que le atribuiremos el valor de 1,con esto conseguiremos que la tortuga, en este caso, se desplace horizontalmente, esta orden será enviada por medio del comando send, pasando como parámetros el publicador y el objeto de mensaje.

XXXXXXX

Ahora crearemos una subsección en nuestro script que nos permita suscribirnos al tópico pose de la simulación de turtle1.

XXXXXXX

Luego crearemos otra sección que nos permita enviar los valores de los parámetros asociados a pose vinculados al objeto turtle1.

XXXXXXX

La siguiente sentencia nos permitirá detener la ejecución del nodo maestro de ROS desde Matlab.

XXXXXXX

Manipulando la posición de la Tortuga con Python

Empezaremos creando el Script myTeleopKey.py dentro del paquete Hello_turtle, para ello podemos desde Visual Studio Code (VSC) abrir la carpeta en nuestro espacio de trabajo donde se encuentra nuestro paquete Hello_turtle y en el interior de esta abriremos la carpeta Scripts, allí guardaremos nuestro archivo.

Ahora en nuestro Script, importaremos las librerías que nos permitirán manipular el influjo de eventos de entrada, por ejemplo, el modulo termios, la librería cliente para ROS, rospy, así como aquellas vinculadas a servicios que nos permitirán manipular la posición de la tortuga, ofrecidos en el paquete Hello turtle, por ejemplo, los módulos TeleportAbsolute, TeleportRelative y Twist.

 XXXXXXXXXX
 
 Luego, escribiremos una función que nos permita obtener el valor de los eventos de entrada, asociados al hecho de oprimir alguna tecla.
 
 XXXXXXX
 
 Ahora definiremos las funciones que nos permiten hacer el vínculo con los servicios asociados al objeto turtle1 y modificar los atributos de posición.
 
 XXXXXXXX
 
 Finalmente definimos la función que le atribuye a cada evento del teclado de nuestro interés el conjunto de acciones que permiten modificar la posición del objeto turtle1.
 
 XXXXXXXXX
 
 Finalmente definimos el main.
 
 XXXXXXXXXX
 
 Ahora incluiremos nuestro Script myTeleopKey.py en el apartado de catkin_install_python del archivo Cmakelist.txt.
 
 XXXXXXXXX
 
 Luego, en una nueva terminal iremos al directorio del workspace de catkiny ejecutaremos el comando catkin_make para reconstruir el paquete modificado.

 XXXXXXXXXXX
 
 Posteriormente en usaremos tres terminales, en la primera reiniciaremos el nodo maestro de ROS con el comando roscore, en la segunda escribiremos el comando rosrun turtlesim turtlesim_node y en la tercera escribiremos el comando source devel/setup.bash y luego el comando rosrun hello turtle myTeleopKey.py y probamos el funcionamiento del script desarrollado.
 
 1ra terminal:
 XXXXXXXXX
 
 2da terminal:
 XXXXXXX
 
 3ra terminal:
 XXXXXXXXX
 
 

