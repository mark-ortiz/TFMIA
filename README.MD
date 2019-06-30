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

## CONTROL DE CAMBIOS / DIARIO DE ACTIVIDADES

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

Subí el código del siguiente intento que es el archivo TFMv0.1

También subí el código del archivo en progreso que es el archivo TFMv0.2

<B>27/Jun</B>

Hice algunos progresos en la generación de los archivos CSV, estos archivos pretendo que sean data más limpia para comenzar a extraer las entradas requeridas (runID, frameID, trigger_counter, interactionID, aafit_azimut, aafit_zenit, aafit_lambda, aafit_beta, bbfit_azimut, bbfit_zenit, bbfit_quality)

Logré realizar un algoritmo para obtener un dataframe con toda la data requerida a partir del archivo CSV.

Unicamente lo he probado para el primer archivo.

He calculado que la obtención de los archivos CSV, tardará alrededor de 5 días con una sola computadora... por lo que puse a trabajar también a la PC de mi trabajo y espero terminar en máximo 3 días y ya contar con los 2542 archivos CSV ya mas limpios para su tratamiento.


<B>28/Jun</B>

Hoy tratando de hacer que el algoritmo que genera la data funcione para todos los archivos, me he encontrado que algunos archivos, en algunos eventos, <B>no contienen data de aafit!!!!.</B>

Por ejemplo investigando en el archivo orignal TXT con nombre MC_076810_numu_CC_a_reco.i3.gz.txt, en el evento 773, no existe la linea con la data relativa a aafit.

Necesito pensar una forma de resolver lo anterior, ya que la idea era recorrer todos los archivos y obtener la data... pero si no existe como tal la línea de aafit en absoluto en algunos archivos, pues el algoritmo falla y da error de índices. Es un problema como siempre de data incompleta.!!!

Una posible idea que se me ocurre, es volver a analizar todos los archivos CSV que se generen, mediante un algoritmo que revise cada uno y en caso de que haga falta una data lo descarte... la idea seria generar un nuevo directorio que contenga solo archivos con data completa... pero necesito tener ya todos los archivos CSV... y para eso falta al menos 1 día más.

<B>29 Jun</B>

Después de probar muchas opciones y desechar algunas ideas locas (y tontas) como menciono en el Notebook que hice expreso para esto (GENERA_DF_AAFIT_BBFIT.ipynb), finalmente pude generar un algoritmo para obtener la data de bbfit, aafit, del muon y demas relevantes y poner toda la data en un solo dataframe para el tratamiento posterior que es el modelado.

Me falta todavía hacer lo mismo y obtener la data para los hits, pero como dicen... un problema a la vez. Espero que la experiencia ganada me ayude, ya que los hits requieren una comparación que no he pensado a profundidad y creo que me puede dar un poco de problema...

Otra cosa que hice fué poner a trabajar en paralelo en la generación de archivos CSV a 3 equipos (2 PC y 1 laptop), ya que iba muy lento e iba a tardar según mis cálculos más de 1 semana un solo equipo. Con lo anterior logré reducir el tiempo a sólo 3 días.

Ahora ya tengo un conjunto de archivos CSV, que pueden ser tratados más fácilmente con pandas de python, solo para la data de aafit y bbfit, como dije todavía falta generar el algoritmo para los hits y por supuesto la data.

Estoy también trabajando la sig. versión del Notebook TFM_v0.3, en el cual he hecho algo de limpieza de los anteriores y ya he eliminado algunas cosas que no servían o estaban de más y repetidas, y pondré el algoritmo completo de generación de data de aafit,bbfit y el muon.

<B>30 Jun</B>

Este dia Domingo he verificado que no se haya colgado nada de la extracción de CSVs, ya que en México es común la falta de energía eléctrica y pues eso da al traste con el trabajo, sin embargo todo bien, los 3 equipos terminaron satisfactoriamente y tengo todos los archivos que se requieren en CSV para hacer la extracción de data.

Hoy pondré a trabajar el algoritmo para generar la data de aafit, bbfit y el muon. Después de algunos pruebas, estimo que esto tardará alrededor de 3 o 4 horas máximo y con un solo equipo PC.
