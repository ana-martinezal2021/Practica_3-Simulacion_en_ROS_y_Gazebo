# Practica_3-Simulacion_en_ROS_y_Gazebo
* **Autora** : Ana Martínez Albendea
* **Asignatura** : Modelado y Simulación de robots

## **Análisis de las gráficas**

En primer lugar realizamos un análisis de las gráficas obtenidas tras lanzar nuestro robot en los dos mundos de gazebo.

En el caso del mundo "/floor.world", podemos ver la siguiente gráfica:

![floor](https://github.com/ana-martinezal2021/Practica_3-Simulacion_en_ROS_y_Gazebo/assets/92941166/81f1aa93-52e1-432b-a308-b20cda38785b)

Como podemos ver en la parte donde el robot va subiendo la velocidad progresivamente, la velocidad de las ruedas sufre alguna fluctuación debido a que el robot se choca con los cubos principalmente con las ruedas delanteras debido a que sufren el primer contacto directo con los cubos. Además, debido a las irregularidades que presenta el terreno podemos ver pequeñas vibraciones en las velocidades de las ruedas que aumentan y disminuyen según la zona por la que pase el robot.
En cuanto a la velocidad que se publica en Odom y la que marca que llevan las ruedas, podemos apreciar la notable diferencia. Esto se debe a que estamos publicando en Odom de manera que asciende gradualmente de 0 a 5, se mantiene y luego desciente hasta pararse, pero esta publicación no se está realizando en las ruedas directamente. Esto quiere decir que aunque nosotros publiquemos por ejemplo una velocidad de 5 en Odom, el controlador se encarga de transformar la velocidad publicada al cuerpo a la velocidad equivalente que se debe publicar en los joint de las ruedas. Esto se ve también en las fluctuaciones que hay presentes en las velocidades de las ruedas pero no en Odom, ya que son estas las que sufren las consecuencias del choque con los cubos o el terreno irregular.

Por otro lado en el caso del mundo "/sand.world", tenemos esta gráfica:

![sand](https://github.com/ana-martinezal2021/Practica_3-Simulacion_en_ROS_y_Gazebo/assets/92941166/98006f4c-b4f4-4d1a-987b-7d9bd2367306)

En esta situación podemos ver también las fluctuaciones nombradas anteriormente donde las velocidades de las ruedas disminuyen o aumentan de golpe debido al choque con los cubos. En este caso algo notable es que al ser arena cuando las velocidades de las ruedas van subiendo para llegar a 5, no sufren esa complicación que se nota en la anterior. Se ve que el ascenso es más lineal y continuo y desde mi punto de vista se puede deber al terreno y como ha reaccionado el robot ante el choque con los cubos, ya que como se podrá ver en los vídeos no es igual en los dos.

Además, añadir que algo que llama la atención de las gráficas es que las velocidades no son todas positivas. Esto se debe a que para cumplir el REP-103, los ejes z sobre los que giran las ruedas deben estar todos mirando hacia afuera como en la realidad. Debido a ello para que el movimiento de las ruedas sea igual en las 4 se deben publicar multiplicadas por un factor negativos las ruedas de la parte izda del robot y con un factor positivo las ruedas de la parte derecha del robot. En la siguiente imagen se podrá ver como están dispuestos los ejes de las ruedas vistos desde la parte frontal del coche para que vea visualmente la razón:

![tf_ruedas](https://github.com/ana-martinezal2021/Practica_3-Simulacion_en_ROS_y_Gazebo/assets/92941166/438c7a94-bc92-4332-8f51-6fabaac18513)



## **Vídeos de las simulaciones**

Simulación en el mundo "/floor.world":

https://github.com/ana-martinezal2021/Practica_3-Simulacion_en_ROS_y_Gazebo/assets/92941166/a95484fa-8f71-4cae-9690-d3a31da02419

Simulación en el mundo "/sand.world":

https://github.com/ana-martinezal2021/Practica_3-Simulacion_en_ROS_y_Gazebo/assets/92941166/72b2606c-49b0-4b36-8c57-f26dc40789f7


## **Rosbags**

Rosbag del mundo "/floor.world":

https://urjc-my.sharepoint.com/:f:/g/personal/a_martinezal_2021_alumnos_urjc_es/En8VfD4FsYRKmyYvxUttxewBF5kxwwDxc11f54BSSReh1g?e=qkrj4E

Rosbag del mundo "/sand.world":

https://urjc-my.sharepoint.com/:f:/g/personal/a_martinezal_2021_alumnos_urjc_es/EuyFzSuowyBPi_xy61xXjgAB5Lk47JB2E8E3SCQc3REgpA?e=mdMYtF
