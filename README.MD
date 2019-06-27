# TFM - Máster en Inteligencia Artificial

Este repositorio lo he creado para llevar el seguimiento de lo realizado con respecto a las tareas que se requieren llevar a cabo para lograr el objetivo del TFM. Fué creado el día 7/Jun/2019.

El título de mi TFM es:
<B>"Aprendizaje profundo aplicado a física de partículas: estimación de trazas de partículas detectadas por el telescopio de neutrinos en el fondo marino."</B>

Para lo anterior, he pensado guiarme con la metodología CRISP-DM que requiere los siguientes pasos:
* 1. Entendimiento del Negocio (o del Problema en este caso)
* 2. Entendimiento de los Datos
* 3. Preparación de los Datos
* 4. Modelado
* 5. Evaluación
* 6. Despliegue-Implementación del modelo en producción

## CONTROL DE CAMBIOS

<B>7/Jun</B>

Existen por el momento 2 archivos (me falta subir 1, pero primero le quitare cosas que no aportan nada.)

TFMv_0 - Este archivo contiene el esfuerzo inicial de comprensión del problema y de limpieza de datos, sin embargo está erróneo debido a una falta de comprensión del problema, se hizo una limpieza inicial "importante", pero solo se extrajeron de cada archivo los datos del muón que son las salidas, faltó el tratamiento en general de los hits y de la data bbfit y afit.


TFMv_0.1 - En este archivo se pretende corregir los errores anteriores y hacer una limpieza correcta, ya que se cuenta con nueva información proporcionada por mi director de TFM, así como una mayor comprensión del problema. (De todos modos debo leer y comprender mejor el rol de bbfit y aafit).

Algo muy rescatable, es el tratamiento que pude hacer de los 2554 archivos proporcionados y que seguramente me servirá para el siguiente intento.

<B>8/Jun</B>

Importante comentar que como collaboratory se me ha colgado varias veces debido a falta de memoria en otros proyectos, decidí adquirir hace poco (20 días aprox), una tarjeta de vídeo NVIDA RTX 2070 (que tuve que cambiar con el proveedor la primerz vez porque resultó que estaba dañanda); el objetivo es ver que sea de ayuda con el tema del entrenamiento para el TFM. Adicional ya puede configurar el ambiente Anaconda para que haga uso de esta, lo hice generando un ambiente virtual para que use tensorflow. Veremos si puede apoyar para este trabajo del TFM (espero que sí).

<B>25/Jun</B>

Una vez terminadas por fin todas las materias y el último examen del Master, me enfocaré de lleno al TFM.
Lo primero que haré es el tratamiento de los hits que según lo que entendí son la data que necesito para el modelado.

<B>26/Jun</B>

He estado trabajando en el tratamiento de un solo archivo para obtener la data de aafit y bbfit, adicionalmente también he estado trabajando en obtener la data de los best hits y los raw hits.
Ha sido un poco arduo.
La idea que se me ocurrio para poder localizar la información fué generar indices tipo punteros, y al parecer ha funcionado.
