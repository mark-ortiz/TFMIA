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

Empecé a trabajar en un notebook para el filtrado de los hits, logré filtrar los raw hits y los selected pulses del mismo evento, sin embargo he llegado al punto que no sé decidir cual es el criterio para seleccionar los "mejores hits".

<B>1 Jul</B>

Revisando como va la generación del dataframe, al parecer estime mal el tiempo de generación del primer dataframe con la data, relativo al punto 3.1 de las instrucciones dadas por mi director de TFM.

Analizando, solo estime con archivos pequeños de 5 MB y no los "grandes" de más de 40 MB y hasta 90 MB, por lo que el tiempo para la generación de este primer dataframe puede que tarde hasta 3 días con un solo equipo PC, por lo que puse a trabajar 2 equipos para tratar de que solo sean 2 días y al final uniré los 2 dataframes para que quede solo 1. (Solo espero que no se corte la energía eléctrica :/ ).

Mientras seguiré trabajando en obtener los hits relevantes a partir de los raw y los selected pulses, como mencioné antes, ya tengo un algoritmo que me permite obtenerlos. Me falta la definición del criterio para poder continuar y terminar de generar el algoritmo que recorra todos los archivos y genere el dataframe deseado.

Algo muy importante que me parece faltó mencionar respecto al punto 3.1 y el dataframe que generará, es que hay ciertos eventos (muy pocos) dentro de cada archivo en los cuales no existe como tal el renglón de aafit. Para estos casos hice algo similar al tratamiento de los nan de bbfit, asigne valores fuera de rango como -3pi y -1 y 1.

También es necesario mencionar que he dividido en diversos notebooks el trabajo, ya que me estaba costando mucho ir hacia arriba y abajo. Los más importantes son los llamados GENERA_CSVs y GENERA_DF_AAFIT_BBFIT, también he pasado por 2 iteraciones más del principal que se llama TFMvX.X, el actual es el TFMv0.3 el cual ya logré estructurar mejor y contiene comentarios según yo más acertados y precisos, por supuesto esto es después de haber comprendido mucho mejor los datos.

<B>2 Jul</B>

Hoy fué dia duro en el trabajo. Solo he logrado generar un algoritmo que selecciona de un primer evento del primer archivo los hits de acuerdo al criterio en donde si X',Y',Z',X,Y y Z son iguales que el selected pulse entonces se debe guardar ese raw hit.

Falta generar un dataframe con la estructura correcta para sacarlo a un archivo.

<B>3 Jul</B>

Mi PC de casa se reinició debido a las actualizaciones de Windows y se perdieron 3 días de trabajo de procesamiento de datos para obtener la data de aafit, bbfit, muon y otras.

Intentaré generar un algoritmo que sólo trabaje con listas y genere un dataframe por cada archivo CSV, así si llega a pasar algo, no se perderá todo el trabajo realizado.

Hoy también intentaré obtener la data de los hits a partir de filtrar por Z' como indico Salva.

Logré bajar el tiempo radicalmente para generar el dataframe respecto al punto 3.1 del correo de Salva del 17 de Junio.

<B>4 Jul</B>

Logré terminar un algoritmo y programa para extraer la data relevante de los raw hits de acuerdo a lo indicado de cada uno de los archivos CSV (primera limpieza de los TXTs), es decir, seleccionar de cada evento los raw_hits que correspondan con linea y piso detector.

Dejé corriendo el notebook en 2 PCs para dividir la carga, ya que calculo que tardaran ambas computadoras alrededor de 4 horas o menos cada una.

Se generaran 2 dataframes que unire para tener la data ya completa junto con la metadata (runID, frameID, trigger_counter e interactionID).

En este caso y a diferencia del punto 3.1 (donde obtuve la data del muón, aafit y bbfit), todavía falta hacer la transformación azimut y zenit, pero lo haré una vez que ya tenga el dataframe completo.

Los archivos que he utilizado para trabajar son DATA_HITSv2_Laptop y DATA_HITS_v2. Ambos notebooks ya los coloqué en el repositorio, así como el inicial.

Solo espero que no haga crash mi laptop por falta de memoria... mañana me enteraré. Plan B... si lo hace, correré de nuevo el programa en la PC del trabajo que tiene 32GB de RAM (mi laptop "solo" tiene 16GB).

<B>5 Jul</B>

Lamentablemente se cumplió lo que me esperaba... :(, mi laptop hizo crash por falta de memoria, no se apagó como tal, pero el kernel de python del notebook marcó error. Lo que haré ahora es por la tarde llevar mi PC de mi trabajo a casa, copiar los archivos para tener completos los CSV en ambos lugares, es decir, tanto en mi PC del trabajo como en la laptop de casa.

Regresando del trabajo, ya he conectado la PC a mi red y he copiado los archivos para tener todo el dataset de CSVs en ambos equipos.

Puse a trabajar nuevamente el algoritmo para extraer los hits, pero en el equipo de mi trabajo, el cual tiene 32GB de RAM, espero que este si aguante y no haga crash (no debería). Ahora a esperar a que termine la extracción.

<B>6 Jul</B>

Terminó exitosamente la extracción de la data de TODOS los archivos CSV (2542). Obtuve un dataframe de 63,520,301 filas y de 7.4GB de tamaño.

Todavía falta hacer la transformación a azimut y zenit, pero espero que sea mucho más fácil, aunque seguramente también tardará considerablmente, hoy trabajaré en el algoritmo y dejaré trabajando el equipo.

Si logro terminar hoy, mañana ya veré o preguntaré acerca de la correlación de ambos archivos que obtuve, el relativo al punto 3.1 y el relativo al 3.2.

Algo que olvidaba es el tema de la selección de hits usando el "cutoff"... no sé si esto seá facil o inclusive necesario, pero lo platicaré con Salva vía correo una vez que tenga la data y le pueda mandar un ejemplo de lo que obtuve.

<B>7 Jul</B>

Generé un nuevo notebook con un algoritmo para calcular azimut y zenit y agregar las columnas correspondientes al dataframe a partir del que ya tengo de los hits. 

Dejé corriendo el notebook con el algoritmo que generé para agregar las columnas azimut y zenit al dataframe de los hits, sin embargo hizo crash debido a falta de memoria, aunque esto pudo haberse debido no al dataframe en sí o a la generación de las listas para después agregarlas al dataframe, sino más bien a que por tratar de monitorear como iba avanzando en los renglones, deje imprimiendo la variable del bucle principal y que son mas de 60M de renglones. 

<B>8 Jul</B>

Hoy deje corriendo el algoritmo que generé y pude agregar al dataframe de los hits las columnas azimut y zenit, el archivo resultante es de aprox. 11GB.

Lo que hice de diferente es crear un monitoreo de avance de los renglones más "suave" y que no consume tanta memoria, ya que solo imprimía el avance cada que pasaba 1 millón de filas. Pude comprobar que esto fue lo que causó el crash de ayer.

Debo mandar esta información a Salva para que le eche un vistazo y me diga que pasa con el tema de los "cutoff" o si seguimos así adelante.

Algo muy interesante que me di cuenta es que Z de los hits en todos los eventos es -0.707106. No sé si esto afecte algo posteriormente para el modelado, pero el azimut de los hits siempre sale igual 2.356193.
