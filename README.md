El presente proyecto tiene por objeto realizar una serie de pasos para poder obtener datos a partir de una fuente del gobierno y utilizarlo como dataset para operar sobre estos.

El pipeline consta de 3 etapas: la primera, el Extract (el cual no fue modificado por mí) trae los datos de la API del INDEC y los almacena para ser procesados; en segundo lugar, está el Transform, que es donde yo escribí el código de python para poder calcular y añadir información al dataset; en tercer lugar, está el Load que es donde yo escribí el código para poder validar la información generada y también generar un reporte con los metadatos del proceso.

Específicamente, en el archivo transform.py lo que hago es añadir las columnas de participación porcentual sobre el total de la provincia, variación porcentual interanual, la década a la cual correspondían las exportaciones de cada año, ranking de las exportaciones por provincia y año, el rubro que más aportó a esa cantidad de exportaciones, porcentaje de las exportaciones correspondientes a productos primarios, entre otros. Por ejemplo, para calcular la variación porcentual interanual para cada provincia y cada destino lo que hice es generar un diccionario donde a cada tupla (provincia, destino, año) les asigné el valor de las exportaciones en millones de dólares. Luego, 
haciendo uso del diccionario creado, recorrí fila por fila y calculé la variación interanual llamando a calcularla variación con los valores de exportación para el año actual y el anterior como parámetros.

Con referencia al archivo load.py se validaron los datos viendo que no existan valores absurdos, negativos o repetidos, y por último se escribe un informe en formato json donde se añade información general sobre la ejecución del pipeline.

