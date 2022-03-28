# Actividad dirigida 2

En esta parte de la Actividad Dirigida 2 es donde vamos a poner el código en bruto completo para poder llegar a entender bien lo que hemos hecho en el notebook de 'Jupyter'. También es vital para poder contrastar con el otro ejercicio como es un código en bruto y como es editado con `Jupyter`: dos maneras muy diferentes de visualizar los datos

## Librerías
En este caso, lo primero que realizamos es importar la librería requests. Un paso vital e importante que nos permite obtener la página web a la que queremos hacer scrapping.

Por otra parte, la librería beautiful soup es la que nos sirve para extraer información de contenido en formato HTML o XML. Es un paso vital para luego poder analizar la información.

## Variables
Es el momento en el que vamos a definir lo que queremos obtener. Para ello lo más importante es poner la URL de donde queremos sacar los datos ("https://resultados.elpais.com/deportivos/juegos-olimpicos/medallero/"). Es a esta misma URL a la que le haremos la peticion request.get, que nos va a servir para obtener los datos.

También es importante darle la instrucción a la página de que si el estatus code no nos permite hacer scrapping, que nos informe mediante el código (req.status_code != 200).

Es importante tambien que para que se pueda leer el HTML de la web es vital que pasemos los datos por `BeautifulSoup` que, como hemos explicado es la que nos permite extraer la información en formato HTML o XML

## Datos
Una de las cosas más importantes es tener claro cuales son las variables que queremos conseguir. En nuestro caso son los `oros`, `platas`, `bronces` y el `total de medallas` que tiene cada país que aparece en la tabla de los datos que queremos extraer. Por ello es importante identificarlas en el HTML de la URL y aplicar en el código la función `find_all()` para que las busque y las seleccione para, más tarde, mostrárnoslas.

Esto se consigue mediante un bucle que mediante el código `print` imprimirá los datos/números que le hemos pedido y nos haga una buena visualización de datos rápida y cómoda.

## Pregunta
La pregunta es, más que nada, para conseguir que el usuario o la persona que utiliza nuestro código tenga cierto tipo de interacción. En este caso se pregunta `¿Quieres conocer los 20 países que han obtenido más medallas en 2020?`. Entonces si la persona teclea `s` significará que es un sí y procederá a seguir con el scrapping. Si el usuario no pulsa esa letra, no continuará.

## Código en bruto
```
from bs4 import BeautifulSoup
import requests
#Datos sobre los Juegos Olímpicos en 2020

respuesta=input('¿QUIERES CONOCER LOS 20 PAÍSES QUE HAN OBTENIDO MÁS MEDALLAS EN 2020?\n \n Si tu respuesta es Sí, presiona "s" \n')
if(respuesta == 's'):
  print('\nRESULTADOS DE LOS DATOS DE LOS JUEGOS OLÍMPICOS 2020\n')
  print ('PAÍSES')
  URL = "https://resultados.elpais.com/deportivos/juegos-olimpicos/medallero/"
  # Realizamos la petición a la web
  req = requests.get(URL)
  # Si el estatus code no es 200 no se puede leer la página
  if (req.status_code != 200):
    raise Exception("No se puede hacer Web Scraping en"+ URL)
  # Pasamos el contenido HTML de la web a un objeto BeautifulSoup()
  html = BeautifulSoup(req.text, "html.parser")
  # Obtenemos todos los divs donde están las entradas
  paises = html.find_all("th",{"class":"pais"})
  oros = html.find_all("td",{"class":"m_oro"})
  platas = html.find_all("td",{"class":"m_plata"})
  bronces = html.find_all("td",{"class":"m_bronce"})
  totales = html.find_all("td",{"class":"m_total"})
  for i in range (20):
    # Con el método "getText()" no nos devuelve el HTML
    print("%d. %s \nOro: %s Plata: %s Bronce: %s \n Total: %s \n " % (i+1, paises[i+1].text.strip(),oros[i].text.strip(),platas[i].text.strip(),bronces[i].text.strip(), totales[i].text.strip()))

else:
  print('Qué lástima, y...')

```
 
