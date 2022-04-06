# API Pandas Folium

- API
- Pandas
- Folium,mapas

## Instalar librerías

Lo primero que tenemos que hacer es instalar la librería Panda, que proporciona herramientas que permiten leer y escribir datos en diferentes formatos: CSV, Microsoft Excel, bases SQL y formato HDF5. Además esta herramienta nos permite seleccionar y filtrar de manera sencilla tablas de datos en función de la posición, el valor o las propias etiquetas, así como fusionar y unir datos.


```python
!pip install pandas folium
```

    Requirement already satisfied: pandas in c:\programdata\anaconda3\lib\site-packages (1.2.4)
    Requirement already satisfied: folium in c:\programdata\anaconda3\lib\site-packages (0.12.1.post1)
    Requirement already satisfied: jinja2>=2.9 in c:\programdata\anaconda3\lib\site-packages (from folium) (2.11.3)
    Requirement already satisfied: branca>=0.3.0 in c:\programdata\anaconda3\lib\site-packages (from folium) (0.4.2)
    Requirement already satisfied: numpy in c:\programdata\anaconda3\lib\site-packages (from folium) (1.20.1)
    Requirement already satisfied: requests in c:\programdata\anaconda3\lib\site-packages (from folium) (2.25.1)
    Requirement already satisfied: MarkupSafe>=0.23 in c:\programdata\anaconda3\lib\site-packages (from jinja2>=2.9->folium) (1.1.1)
    Requirement already satisfied: python-dateutil>=2.7.3 in c:\programdata\anaconda3\lib\site-packages (from pandas) (2.8.1)
    Requirement already satisfied: pytz>=2017.3 in c:\programdata\anaconda3\lib\site-packages (from pandas) (2021.1)
    Requirement already satisfied: six>=1.5 in c:\programdata\anaconda3\lib\site-packages (from python-dateutil>=2.7.3->pandas) (1.15.0)
    Requirement already satisfied: certifi>=2017.4.17 in c:\programdata\anaconda3\lib\site-packages (from requests->folium) (2020.12.5)
    Requirement already satisfied: idna<3,>=2.5 in c:\programdata\anaconda3\lib\site-packages (from requests->folium) (2.10)
    Requirement already satisfied: chardet<5,>=3.0.2 in c:\programdata\anaconda3\lib\site-packages (from requests->folium) (4.0.0)
    Requirement already satisfied: urllib3<1.27,>=1.21.1 in c:\programdata\anaconda3\lib\site-packages (from requests->folium) (1.26.4)
    

## Configurar librerías

La configuración de las librerías se basa en importarlas para usarlas en este cuaderno, lo hacemos con las siguientes funciones:


```python
import pandas as pd
import folium
```

## Variables

Vamos a usar:
- La URL
- Y las coordenadas de Zaragoza, que llamaremos `coords_zrgz` y cuyas coordenadas exactas son `[41.649693, -0.887712]`
- Mapa, aunque más que una variable es un objeto. Lo haremos haciendo una llamada a `folium`

La primera variable que vamos a usar es la URL de donde queremos exportar los datos, en este caso la accidentalidad en el tráfico en la ciudad de Zaragoza. 

Para hacer el mapa llamaremos a la libreria folium, a la que le pediremos la localización y cuyo valor serán las coordenadas de Zaragoza, aquí llamadas `coords_zrgz`


```python
url = 'https://www.zaragoza.es/sede/servicio/transporte/accidentalidad-trafico/accidente.csv?rows=20'
coords_zrgz = [41.649693,-0.887712]
mapa = folium.Map(location=coords_zrgz)
```

Ahora tenemos que invocar al mapa, y se hace sencillamente escribiendo la palabra `mapa`, ya que es la palabra a la que le hemos dado el valor de las coordenadas de Zaragoza.


```python
mapa
```




<div style="width:100%;"><div style="position:relative;width:100%;height:0;padding-bottom:60%;"><span style="color:#565656">Make this Notebook Trusted to load map: File -> Trust Notebook</span><iframe src="about:blank" style="position:absolute;width:100%;height:100%;left:0;top:0;border:none !important;" data-html=%3C%21DOCTYPE%20html%3E%0A%3Chead%3E%20%20%20%20%0A%20%20%20%20%3Cmeta%20http-equiv%3D%22content-type%22%20content%3D%22text/html%3B%20charset%3DUTF-8%22%20/%3E%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%3Cscript%3E%0A%20%20%20%20%20%20%20%20%20%20%20%20L_NO_TOUCH%20%3D%20false%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20L_DISABLE_3D%20%3D%20false%3B%0A%20%20%20%20%20%20%20%20%3C/script%3E%0A%20%20%20%20%0A%20%20%20%20%3Cstyle%3Ehtml%2C%20body%20%7Bwidth%3A%20100%25%3Bheight%3A%20100%25%3Bmargin%3A%200%3Bpadding%3A%200%3B%7D%3C/style%3E%0A%20%20%20%20%3Cstyle%3E%23map%20%7Bposition%3Aabsolute%3Btop%3A0%3Bbottom%3A0%3Bright%3A0%3Bleft%3A0%3B%7D%3C/style%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//cdn.jsdelivr.net/npm/leaflet%401.6.0/dist/leaflet.js%22%3E%3C/script%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//code.jquery.com/jquery-1.12.4.min.js%22%3E%3C/script%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/js/bootstrap.min.js%22%3E%3C/script%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//cdnjs.cloudflare.com/ajax/libs/Leaflet.awesome-markers/2.0.2/leaflet.awesome-markers.js%22%3E%3C/script%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//cdn.jsdelivr.net/npm/leaflet%401.6.0/dist/leaflet.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap.min.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap-theme.min.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//maxcdn.bootstrapcdn.com/font-awesome/4.6.3/css/font-awesome.min.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//cdnjs.cloudflare.com/ajax/libs/Leaflet.awesome-markers/2.0.2/leaflet.awesome-markers.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//cdn.jsdelivr.net/gh/python-visualization/folium/folium/templates/leaflet.awesome.rotate.min.css%22/%3E%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20%3Cmeta%20name%3D%22viewport%22%20content%3D%22width%3Ddevice-width%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20initial-scale%3D1.0%2C%20maximum-scale%3D1.0%2C%20user-scalable%3Dno%22%20/%3E%0A%20%20%20%20%20%20%20%20%20%20%20%20%3Cstyle%3E%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%23map_a113325c206e4c5e9cc0b298a04453e1%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20position%3A%20relative%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20width%3A%20100.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20height%3A%20100.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20left%3A%200.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20top%3A%200.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%3C/style%3E%0A%20%20%20%20%20%20%20%20%0A%3C/head%3E%0A%3Cbody%3E%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20%3Cdiv%20class%3D%22folium-map%22%20id%3D%22map_a113325c206e4c5e9cc0b298a04453e1%22%20%3E%3C/div%3E%0A%20%20%20%20%20%20%20%20%0A%3C/body%3E%0A%3Cscript%3E%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20map_a113325c206e4c5e9cc0b298a04453e1%20%3D%20L.map%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%22map_a113325c206e4c5e9cc0b298a04453e1%22%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20center%3A%20%5B41.649693%2C%20-0.887712%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20crs%3A%20L.CRS.EPSG3857%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20zoom%3A%2010%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20zoomControl%3A%20true%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20preferCanvas%3A%20false%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29%3B%0A%0A%20%20%20%20%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20tile_layer_7417ec98414e43a3a505a3a8d408b3ec%20%3D%20L.tileLayer%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%22https%3A//%7Bs%7D.tile.openstreetmap.org/%7Bz%7D/%7Bx%7D/%7By%7D.png%22%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%22attribution%22%3A%20%22Data%20by%20%5Cu0026copy%3B%20%5Cu003ca%20href%3D%5C%22http%3A//openstreetmap.org%5C%22%5Cu003eOpenStreetMap%5Cu003c/a%5Cu003e%2C%20under%20%5Cu003ca%20href%3D%5C%22http%3A//www.openstreetmap.org/copyright%5C%22%5Cu003eODbL%5Cu003c/a%5Cu003e.%22%2C%20%22detectRetina%22%3A%20false%2C%20%22maxNativeZoom%22%3A%2018%2C%20%22maxZoom%22%3A%2018%2C%20%22minZoom%22%3A%200%2C%20%22noWrap%22%3A%20false%2C%20%22opacity%22%3A%201%2C%20%22subdomains%22%3A%20%22abc%22%2C%20%22tms%22%3A%20false%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%3C/script%3E onload="this.contentDocument.open();this.contentDocument.write(    decodeURIComponent(this.getAttribute('data-html')));this.contentDocument.close();" allowfullscreen webkitallowfullscreen mozallowfullscreen></iframe></div></div>



El siguiente paso es crear un data frame `df`, que es como llama Python a las tablas. Pero en esta ocasión tenemos que delimitar la url con el código `delimiter`, que en este caso es el punto y coma `;`. Así le estamos diciendo a la librería que lea la función de Panda `read csv`, pero como no esta delimitado por comas `,`, sino por puntos y comas `;`, se lo tenemos que decir para que muestre bien los datos.


```python
df = pd.read_csv(url,delimiter=';')
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>id</th>
      <th>year</th>
      <th>type</th>
      <th>accidentType</th>
      <th>firstAddress</th>
      <th>secondAddress</th>
      <th>geometry</th>
      <th>reason</th>
      <th>area</th>
      <th>creationDate</th>
      <th>daniosMateriales</th>
      <th>falloMecanico</th>
      <th>estadoPavimento</th>
      <th>tipoEstadoPavimento</th>
      <th>estadoAtmosfera</th>
      <th>tipoEstadoAtmosfera</th>
      <th>afectado</th>
      <th>vehiculo</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>SALIDA CALZADA</td>
      <td>NaN</td>
      <td>COSTA, JOAQUIN</td>
      <td>PERAL, ISAAC</td>
      <td>-0.8818527060979306,41.649027473051156</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>NaN</td>
      <td>2014-10-09T00:00:00Z</td>
      <td>True</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>COLISIÓN ALCANCE</td>
      <td>NaN</td>
      <td>CADENA(MARQUES DE LA)</td>
      <td>NaN</td>
      <td>-0.8645810716721081,41.661585829868585</td>
      <td>DISTANCIA DE SEGURIDAD, no mantener</td>
      <td>2560.0</td>
      <td>2014-10-23T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>COLISIÓN ALCANCE</td>
      <td>NaN</td>
      <td>GOMEZ AVELLANEDA, G.</td>
      <td>CASTRO, R. (POETA)</td>
      <td>-0.887776415002892,41.666992622958105</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>2598.0</td>
      <td>2014-10-23T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>COLIS FRONTOLATERAL</td>
      <td>NaN</td>
      <td>MONZON</td>
      <td>GARCIA CONDOY, H.</td>
      <td>-0.8825260453930127,41.62957498750602</td>
      <td>CEDA EL PASO, no respetar prioridad de paso</td>
      <td>2555.0</td>
      <td>2014-10-23T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>SALIDA CALZADA</td>
      <td>NaN</td>
      <td>RIOJA</td>
      <td>NAVARRA, AVENIDA DE</td>
      <td>-0.908314757720389,41.6562121210704</td>
      <td>PERDIDA del control por VELOCIDAD INADECUADA</td>
      <td>2554.0</td>
      <td>2014-10-24T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>5</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>OTRAS</td>
      <td>NaN</td>
      <td>MUEL</td>
      <td>NaN</td>
      <td>-0.8691088511672924,41.65949772773082</td>
      <td>Caída de ocupante en Transporte Público</td>
      <td>2578.0</td>
      <td>2014-10-24T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>6</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>ATROPELLO</td>
      <td>NaN</td>
      <td>PIGNATELLI, RAMON VIA</td>
      <td>NaN</td>
      <td>-0.8880337913721866,41.633353667694024</td>
      <td>PEATÓN cruza calz SIN PREFER. fuera de paso</td>
      <td>2606.0</td>
      <td>2014-10-24T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>7</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>CAIDA SOBRE CALZADA</td>
      <td>NaN</td>
      <td>ALIERTA, AV. CESAREO</td>
      <td>AULA, LUIS</td>
      <td>-0.8708838775078237,41.6390382112928</td>
      <td>INVADIR otro carril en el mismo sentido de cir...</td>
      <td>2583.0</td>
      <td>2014-10-24T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>8</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>COLIS. MARCHA ATRÁS</td>
      <td>NaN</td>
      <td>CERBUNA, PEDRO</td>
      <td>NaN</td>
      <td>-0.8970649943808023,41.64083344974765</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>2556.0</td>
      <td>2014-10-24T00:00:00Z</td>
      <td>True</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>9</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>COLISIÓN LATERAL</td>
      <td>NaN</td>
      <td>ASALTO</td>
      <td>COCCI, JORGE</td>
      <td>-0.8718525605769747,41.64904657717317</td>
      <td>INVADIR otro carril en el mismo sentido de cir...</td>
      <td>4657.0</td>
      <td>2013-12-20T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>10</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>OTRAS</td>
      <td>NaN</td>
      <td>ARAGON (CORONA DE)</td>
      <td>SAN ANTONIO M CLARET</td>
      <td>-0.8964627561577849,41.64322365075108</td>
      <td>Caída de ocupante en Transporte Público</td>
      <td>63.0</td>
      <td>2013-12-21T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>11</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>COLISIÓN ALCANCE</td>
      <td>NaN</td>
      <td>FRAGUA, LA</td>
      <td>GASSIER, PIERRE</td>
      <td>-0.8778095796207178,41.68753087470739</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>4780.0</td>
      <td>2013-12-22T00:00:00Z</td>
      <td>True</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>12</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>SALIDA CALZADA</td>
      <td>NaN</td>
      <td>PIRINEOS, AV. DE LOS</td>
      <td>NaN</td>
      <td>-0.8812157329722801,41.661646612715046</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>4661.0</td>
      <td>2013-12-22T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>13</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>COLISIÓN ALCANCE</td>
      <td>NaN</td>
      <td>TORRES, CAMINO DE LAS</td>
      <td>NaN</td>
      <td>-0.8762000299022707,41.6454384961757</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>4667.0</td>
      <td>2013-12-22T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>14</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>ATROPELLO</td>
      <td>NaN</td>
      <td>RIOJA</td>
      <td>NAVARRA, AVENIDA DE</td>
      <td>-0.9089013552408617,41.65543768899759</td>
      <td>PEATÓN cruza calz SIN PREFER. en PASO CON semá...</td>
      <td>4664.0</td>
      <td>2013-12-22T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>15</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>COLISIÓN ALCANCE</td>
      <td>NaN</td>
      <td>ITALIA</td>
      <td>NaN</td>
      <td>-0.9004729973337304,41.65180346604993</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>4671.0</td>
      <td>2013-12-22T00:00:00Z</td>
      <td>True</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>16</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>COLISIÓN ALCANCE</td>
      <td>NaN</td>
      <td>AGUSTIN, PASEO MARIA</td>
      <td>MAYANDIA (GENERAL)</td>
      <td>-0.8917562993466011,41.65233828238132</td>
      <td>DISTANCIA DE SEGURIDAD, no mantener</td>
      <td>18.0</td>
      <td>2013-12-20T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>17</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>COLISIÓN ALCANCE</td>
      <td>NaN</td>
      <td>AGUSTIN, PASEO MARIA</td>
      <td>SANTA ANA</td>
      <td>-0.888856043735591,41.65040494617356</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>4718.0</td>
      <td>2013-12-23T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>18</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>COLISIÓN ALCANCE</td>
      <td>NaN</td>
      <td>CASPE, AV.COMPROMISO</td>
      <td>NaN</td>
      <td>-0.8629911318784169,41.645335650478316</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>4723.0</td>
      <td>2013-12-23T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>19</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>COLISIÓN ALCANCE</td>
      <td>NaN</td>
      <td>MURANO, ISLA DE AV.</td>
      <td>NaN</td>
      <td>-0.8870207060655807,41.609992514227066</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>NaN</td>
      <td>2013-12-23T00:00:00Z</td>
      <td>True</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
  </tbody>
</table>
</div>



## Exploración de la tabla

Ahora vamos a ver cuales son los nombres de las columnas, lo hacemos de la siguiente forma:


```python
df.columns
```




    Index(['id', 'year', 'type', 'accidentType', 'firstAddress', 'secondAddress',
           'geometry', 'reason', 'area', 'creationDate', 'daniosMateriales',
           'falloMecanico', 'estadoPavimento', 'tipoEstadoPavimento',
           'estadoAtmosfera', 'tipoEstadoAtmosfera', 'afectado', 'vehiculo'],
          dtype='object')



Queremos que nos muestre la geometría, lo hacemos con la siguiente función ya que hemos visto arriba cuáles son las categorías a las que podemos acceder. También podemos accedewr a otras como `year`, `creationDate` o `tipoEstadoAtmosfera`, entre otros.


```python
df['geometry']
```




    0     -0.8818527060979306,41.649027473051156
    1     -0.8645810716721081,41.661585829868585
    2      -0.887776415002892,41.666992622958105
    3      -0.8825260453930127,41.62957498750602
    4        -0.908314757720389,41.6562121210704
    5      -0.8691088511672924,41.65949772773082
    6     -0.8880337913721866,41.633353667694024
    7       -0.8708838775078237,41.6390382112928
    8      -0.8970649943808023,41.64083344974765
    9      -0.8718525605769747,41.64904657717317
    10     -0.8964627561577849,41.64322365075108
    11     -0.8778095796207178,41.68753087470739
    12    -0.8812157329722801,41.661646612715046
    13      -0.8762000299022707,41.6454384961757
    14     -0.9089013552408617,41.65543768899759
    15     -0.9004729973337304,41.65180346604993
    16     -0.8917562993466011,41.65233828238132
    17      -0.888856043735591,41.65040494617356
    18    -0.8629911318784169,41.645335650478316
    19    -0.8870207060655807,41.609992514227066
    Name: geometry, dtype: object



La siguiente fórmula nos sirve para ver los tipos de datos que tiene el data frame. Hay `id`, `años`,`tipos`,`tipos de accidentes` y muchos otros que podemos ver a continuación:


```python
df.info ()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 20 entries, 0 to 19
    Data columns (total 18 columns):
     #   Column               Non-Null Count  Dtype  
    ---  ------               --------------  -----  
     0   id                   20 non-null     object 
     1   year                 20 non-null     int64  
     2   type                 20 non-null     object 
     3   accidentType         0 non-null      float64
     4   firstAddress         20 non-null     object 
     5   secondAddress        11 non-null     object 
     6   geometry             20 non-null     object 
     7   reason               20 non-null     object 
     8   area                 18 non-null     float64
     9   creationDate         20 non-null     object 
     10  daniosMateriales     20 non-null     bool   
     11  falloMecanico        20 non-null     bool   
     12  estadoPavimento      20 non-null     object 
     13  tipoEstadoPavimento  0 non-null      float64
     14  estadoAtmosfera      20 non-null     object 
     15  tipoEstadoAtmosfera  0 non-null      float64
     16  afectado             15 non-null     object 
     17  vehiculo             20 non-null     object 
    dtypes: bool(2), float64(4), int64(1), object(11)
    memory usage: 2.7+ KB
    

La siguiente función nos sirve para conocer la información numérica, que realmente no nos aporta nada. A pesar de ello, es para conocer que existen y que podemos obtener estos datos.


```python
df.describe ()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>year</th>
      <th>accidentType</th>
      <th>area</th>
      <th>tipoEstadoPavimento</th>
      <th>tipoEstadoAtmosfera</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>20.000000</td>
      <td>0.0</td>
      <td>18.000000</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>2013.450000</td>
      <td>NaN</td>
      <td>3234.000000</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>std</th>
      <td>0.510418</td>
      <td>NaN</td>
      <td>1551.515843</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>min</th>
      <td>2013.000000</td>
      <td>NaN</td>
      <td>18.000000</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>2013.000000</td>
      <td>NaN</td>
      <td>2557.000000</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>2013.000000</td>
      <td>NaN</td>
      <td>2602.000000</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>2014.000000</td>
      <td>NaN</td>
      <td>4666.250000</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>max</th>
      <td>2014.000000</td>
      <td>NaN</td>
      <td>4780.000000</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



Ahora vamos a ver los datos de la columna `type`. Y a esta columna le vamos a decir, encadenar, que haga una descripción de los valores únicos.


```python
df['type'].unique()
```




    array(['SALIDA CALZADA', 'COLISIÓN ALCANCE', 'COLIS FRONTOLATERAL',
           'OTRAS', 'ATROPELLO', 'CAIDA SOBRE CALZADA', 'COLIS. MARCHA ATRÁS',
           'COLISIÓN LATERAL'], dtype=object)



Las coordenadas deberían estar en la columna geometry, que nos da las coordenadas de las cosas que queremos después visualizar en un mapa interactivo en el que se muestren los accidentes en diversos puntos en el mapa.


```python
df['geometry']
```




    0     -0.8818527060979306,41.649027473051156
    1     -0.8645810716721081,41.661585829868585
    2      -0.887776415002892,41.666992622958105
    3      -0.8825260453930127,41.62957498750602
    4        -0.908314757720389,41.6562121210704
    5      -0.8691088511672924,41.65949772773082
    6     -0.8880337913721866,41.633353667694024
    7       -0.8708838775078237,41.6390382112928
    8      -0.8970649943808023,41.64083344974765
    9      -0.8718525605769747,41.64904657717317
    10     -0.8964627561577849,41.64322365075108
    11     -0.8778095796207178,41.68753087470739
    12    -0.8812157329722801,41.661646612715046
    13      -0.8762000299022707,41.6454384961757
    14     -0.9089013552408617,41.65543768899759
    15     -0.9004729973337304,41.65180346604993
    16     -0.8917562993466011,41.65233828238132
    17      -0.888856043735591,41.65040494617356
    18    -0.8629911318784169,41.645335650478316
    19    -0.8870207060655807,41.609992514227066
    Name: geometry, dtype: object



La siguiente función type te dice que tipos de datos son, en este caso, la columna `geometry`


```python
type(df['geometry'][0])
```




    str



El resultado es un string `str`, una cadena de caracteres. Posteriormente deberemos separar esta cadena de caracteres por la coma `,`. ¿Cómo hacemos que se separe? Con la función `split`, como vemos a continuación, en la que le decimos a `geometry` que se separe por la coma `,`


```python
df['geometry'][0].split(',')
```




    ['-0.8818527060979306', '41.649027473051156']



Ya tenemos algo que podemos empezar a manipular. De momento lo que vamos a hacer es crear un punto que se llamará `point`, y que va a tener los dos valores que hemos visto anteriormente. Si antes solo veiamos los datos, ahora estamos creando un punto geográfico, que nosotros hemos llamado `point`


```python
point = df['geometry'][0].split(',')
point
```




    ['-0.8818527060979306', '41.649027473051156']



Ahora ya hemos creado un objeto nuevo, que toma los datos de esa columna y hace la división de los caracteres a partir de la coma. Lo que hacemos es haberle puesto un nombre a estos datos para poder llamarlos posteriormente con la palabra `point`


```python
type(point)
```




    list



Ahora, mediante esta fórmula, podemos saber que point es una lista, ya no es un string como habíamos visto al principio.

Ahora vamos a crear una serie, que es donde vamos a guardar uno de los elementos de cada una de las filas, en este caso longitud y latitud.


```python
longitudes = []
latitudes = []
```


```python
longitudes
```




    []




```python
type(longitudes)
```




    list



Ahora, para cada una de las filas le voy a crear un objeto que se llama longitud, que lo que hace es en esa fila hacer la separación que he hecho antes. La `i` es de input, que es cada uno de los elementos de la columna `geometry`. Con esto ya hemos hecho una acción para cada uno de los elementos dentro de la tabla de datos. Luego hemos llamado a `punto_coord` como la separación de cada una de las celdas de la columna `geometry`. Más tarde le damos un valor a las `longitudes` y le pedimos que nos muestre cuáles son.


```python
for i in df ['geometry']:
    punto_coord = i.split(',')
    longitudes += [float(punto_coord[1])]
longitudes
```




    [41.649027473051156,
     41.661585829868585,
     41.666992622958105,
     41.62957498750602,
     41.6562121210704,
     41.65949772773082,
     41.633353667694024,
     41.6390382112928,
     41.64083344974765,
     41.64904657717317,
     41.64322365075108,
     41.68753087470739,
     41.661646612715046,
     41.6454384961757,
     41.65543768899759,
     41.65180346604993,
     41.65233828238132,
     41.65040494617356,
     41.645335650478316,
     41.609992514227066]




```python
for i in df ['geometry']:
    punto_coord = i.split(',')
    latitudes += [float(punto_coord[0])]
latitudes
```




    [-0.8818527060979306,
     -0.8645810716721081,
     -0.887776415002892,
     -0.8825260453930127,
     -0.908314757720389,
     -0.8691088511672924,
     -0.8880337913721866,
     -0.8708838775078237,
     -0.8970649943808023,
     -0.8718525605769747,
     -0.8964627561577849,
     -0.8778095796207178,
     -0.8812157329722801,
     -0.8762000299022707,
     -0.9089013552408617,
     -0.9004729973337304,
     -0.8917562993466011,
     -0.888856043735591,
     -0.8629911318784169,
     -0.8870207060655807]



Ahora vamos a crear un data frame de las coordenadas, que unen los puntos de latitud y los de longitud. Nos dará como resultado una tabla, que veremos a continuación.


```python
df_coord = pd.DataFrame({'long':longitudes,'lat':latitudes})
df_coord
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>long</th>
      <th>lat</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>41.649027</td>
      <td>-0.881853</td>
    </tr>
    <tr>
      <th>1</th>
      <td>41.661586</td>
      <td>-0.864581</td>
    </tr>
    <tr>
      <th>2</th>
      <td>41.666993</td>
      <td>-0.887776</td>
    </tr>
    <tr>
      <th>3</th>
      <td>41.629575</td>
      <td>-0.882526</td>
    </tr>
    <tr>
      <th>4</th>
      <td>41.656212</td>
      <td>-0.908315</td>
    </tr>
    <tr>
      <th>5</th>
      <td>41.659498</td>
      <td>-0.869109</td>
    </tr>
    <tr>
      <th>6</th>
      <td>41.633354</td>
      <td>-0.888034</td>
    </tr>
    <tr>
      <th>7</th>
      <td>41.639038</td>
      <td>-0.870884</td>
    </tr>
    <tr>
      <th>8</th>
      <td>41.640833</td>
      <td>-0.897065</td>
    </tr>
    <tr>
      <th>9</th>
      <td>41.649047</td>
      <td>-0.871853</td>
    </tr>
    <tr>
      <th>10</th>
      <td>41.643224</td>
      <td>-0.896463</td>
    </tr>
    <tr>
      <th>11</th>
      <td>41.687531</td>
      <td>-0.877810</td>
    </tr>
    <tr>
      <th>12</th>
      <td>41.661647</td>
      <td>-0.881216</td>
    </tr>
    <tr>
      <th>13</th>
      <td>41.645438</td>
      <td>-0.876200</td>
    </tr>
    <tr>
      <th>14</th>
      <td>41.655438</td>
      <td>-0.908901</td>
    </tr>
    <tr>
      <th>15</th>
      <td>41.651803</td>
      <td>-0.900473</td>
    </tr>
    <tr>
      <th>16</th>
      <td>41.652338</td>
      <td>-0.891756</td>
    </tr>
    <tr>
      <th>17</th>
      <td>41.650405</td>
      <td>-0.888856</td>
    </tr>
    <tr>
      <th>18</th>
      <td>41.645336</td>
      <td>-0.862991</td>
    </tr>
    <tr>
      <th>19</th>
      <td>41.609993</td>
      <td>-0.887021</td>
    </tr>
  </tbody>
</table>
</div>



Vamos a crear otro data frame que lo que va a hacer es, con la función de pandas de `concat`, concatenar la columna type del data frame original con el que hemos creado de coordenadas. Porque lo que queremos es una tabla que, además de la longitud y la latitud, nos muestre el tipo de accidente que ha ocurrido en cada coordenada.


```python
df_accidentes = pd.concat([df['type'],df_coord],axis=1)
df_accidentes
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>type</th>
      <th>long</th>
      <th>lat</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>SALIDA CALZADA</td>
      <td>41.649027</td>
      <td>-0.881853</td>
    </tr>
    <tr>
      <th>1</th>
      <td>COLISIÓN ALCANCE</td>
      <td>41.661586</td>
      <td>-0.864581</td>
    </tr>
    <tr>
      <th>2</th>
      <td>COLISIÓN ALCANCE</td>
      <td>41.666993</td>
      <td>-0.887776</td>
    </tr>
    <tr>
      <th>3</th>
      <td>COLIS FRONTOLATERAL</td>
      <td>41.629575</td>
      <td>-0.882526</td>
    </tr>
    <tr>
      <th>4</th>
      <td>SALIDA CALZADA</td>
      <td>41.656212</td>
      <td>-0.908315</td>
    </tr>
    <tr>
      <th>5</th>
      <td>OTRAS</td>
      <td>41.659498</td>
      <td>-0.869109</td>
    </tr>
    <tr>
      <th>6</th>
      <td>ATROPELLO</td>
      <td>41.633354</td>
      <td>-0.888034</td>
    </tr>
    <tr>
      <th>7</th>
      <td>CAIDA SOBRE CALZADA</td>
      <td>41.639038</td>
      <td>-0.870884</td>
    </tr>
    <tr>
      <th>8</th>
      <td>COLIS. MARCHA ATRÁS</td>
      <td>41.640833</td>
      <td>-0.897065</td>
    </tr>
    <tr>
      <th>9</th>
      <td>COLISIÓN LATERAL</td>
      <td>41.649047</td>
      <td>-0.871853</td>
    </tr>
    <tr>
      <th>10</th>
      <td>OTRAS</td>
      <td>41.643224</td>
      <td>-0.896463</td>
    </tr>
    <tr>
      <th>11</th>
      <td>COLISIÓN ALCANCE</td>
      <td>41.687531</td>
      <td>-0.877810</td>
    </tr>
    <tr>
      <th>12</th>
      <td>SALIDA CALZADA</td>
      <td>41.661647</td>
      <td>-0.881216</td>
    </tr>
    <tr>
      <th>13</th>
      <td>COLISIÓN ALCANCE</td>
      <td>41.645438</td>
      <td>-0.876200</td>
    </tr>
    <tr>
      <th>14</th>
      <td>ATROPELLO</td>
      <td>41.655438</td>
      <td>-0.908901</td>
    </tr>
    <tr>
      <th>15</th>
      <td>COLISIÓN ALCANCE</td>
      <td>41.651803</td>
      <td>-0.900473</td>
    </tr>
    <tr>
      <th>16</th>
      <td>COLISIÓN ALCANCE</td>
      <td>41.652338</td>
      <td>-0.891756</td>
    </tr>
    <tr>
      <th>17</th>
      <td>COLISIÓN ALCANCE</td>
      <td>41.650405</td>
      <td>-0.888856</td>
    </tr>
    <tr>
      <th>18</th>
      <td>COLISIÓN ALCANCE</td>
      <td>41.645336</td>
      <td>-0.862991</td>
    </tr>
    <tr>
      <th>19</th>
      <td>COLISIÓN ALCANCE</td>
      <td>41.609993</td>
      <td>-0.887021</td>
    </tr>
  </tbody>
</table>
</div>



Vamos a crear un marcador, para que salgan los puntos en el mapa. Lo creamos con la función de folium que se llama `marker`. Esta funcion va a tener las coordenadas de Zaragoza y la información que queremos que se vea cuando se pase por ella el ratón. Luego le vamos a decir que datos queremos que muestre el objeto mapa, que añade como hijo el marcador.


```python
marcador = folium.Marker(coords_zrgz, popup="¡Hola, Zaragoza!")
mapa = mapa.add_child(marcador)
mapa 
```




<div style="width:100%;"><div style="position:relative;width:100%;height:0;padding-bottom:60%;"><span style="color:#565656">Make this Notebook Trusted to load map: File -> Trust Notebook</span><iframe src="about:blank" style="position:absolute;width:100%;height:100%;left:0;top:0;border:none !important;" data-html=%3C%21DOCTYPE%20html%3E%0A%3Chead%3E%20%20%20%20%0A%20%20%20%20%3Cmeta%20http-equiv%3D%22content-type%22%20content%3D%22text/html%3B%20charset%3DUTF-8%22%20/%3E%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%3Cscript%3E%0A%20%20%20%20%20%20%20%20%20%20%20%20L_NO_TOUCH%20%3D%20false%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20L_DISABLE_3D%20%3D%20false%3B%0A%20%20%20%20%20%20%20%20%3C/script%3E%0A%20%20%20%20%0A%20%20%20%20%3Cstyle%3Ehtml%2C%20body%20%7Bwidth%3A%20100%25%3Bheight%3A%20100%25%3Bmargin%3A%200%3Bpadding%3A%200%3B%7D%3C/style%3E%0A%20%20%20%20%3Cstyle%3E%23map%20%7Bposition%3Aabsolute%3Btop%3A0%3Bbottom%3A0%3Bright%3A0%3Bleft%3A0%3B%7D%3C/style%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//cdn.jsdelivr.net/npm/leaflet%401.6.0/dist/leaflet.js%22%3E%3C/script%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//code.jquery.com/jquery-1.12.4.min.js%22%3E%3C/script%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/js/bootstrap.min.js%22%3E%3C/script%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//cdnjs.cloudflare.com/ajax/libs/Leaflet.awesome-markers/2.0.2/leaflet.awesome-markers.js%22%3E%3C/script%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//cdn.jsdelivr.net/npm/leaflet%401.6.0/dist/leaflet.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap.min.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap-theme.min.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//maxcdn.bootstrapcdn.com/font-awesome/4.6.3/css/font-awesome.min.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//cdnjs.cloudflare.com/ajax/libs/Leaflet.awesome-markers/2.0.2/leaflet.awesome-markers.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//cdn.jsdelivr.net/gh/python-visualization/folium/folium/templates/leaflet.awesome.rotate.min.css%22/%3E%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20%3Cmeta%20name%3D%22viewport%22%20content%3D%22width%3Ddevice-width%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20initial-scale%3D1.0%2C%20maximum-scale%3D1.0%2C%20user-scalable%3Dno%22%20/%3E%0A%20%20%20%20%20%20%20%20%20%20%20%20%3Cstyle%3E%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%23map_a113325c206e4c5e9cc0b298a04453e1%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20position%3A%20relative%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20width%3A%20100.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20height%3A%20100.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20left%3A%200.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20top%3A%200.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%3C/style%3E%0A%20%20%20%20%20%20%20%20%0A%3C/head%3E%0A%3Cbody%3E%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20%3Cdiv%20class%3D%22folium-map%22%20id%3D%22map_a113325c206e4c5e9cc0b298a04453e1%22%20%3E%3C/div%3E%0A%20%20%20%20%20%20%20%20%0A%3C/body%3E%0A%3Cscript%3E%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20map_a113325c206e4c5e9cc0b298a04453e1%20%3D%20L.map%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%22map_a113325c206e4c5e9cc0b298a04453e1%22%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20center%3A%20%5B41.649693%2C%20-0.887712%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20crs%3A%20L.CRS.EPSG3857%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20zoom%3A%2010%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20zoomControl%3A%20true%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20preferCanvas%3A%20false%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29%3B%0A%0A%20%20%20%20%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20tile_layer_7417ec98414e43a3a505a3a8d408b3ec%20%3D%20L.tileLayer%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%22https%3A//%7Bs%7D.tile.openstreetmap.org/%7Bz%7D/%7Bx%7D/%7By%7D.png%22%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%22attribution%22%3A%20%22Data%20by%20%5Cu0026copy%3B%20%5Cu003ca%20href%3D%5C%22http%3A//openstreetmap.org%5C%22%5Cu003eOpenStreetMap%5Cu003c/a%5Cu003e%2C%20under%20%5Cu003ca%20href%3D%5C%22http%3A//www.openstreetmap.org/copyright%5C%22%5Cu003eODbL%5Cu003c/a%5Cu003e.%22%2C%20%22detectRetina%22%3A%20false%2C%20%22maxNativeZoom%22%3A%2018%2C%20%22maxZoom%22%3A%2018%2C%20%22minZoom%22%3A%200%2C%20%22noWrap%22%3A%20false%2C%20%22opacity%22%3A%201%2C%20%22subdomains%22%3A%20%22abc%22%2C%20%22tms%22%3A%20false%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_e5123a0f1e9540f2b4ad028328c87e6a%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.649693%2C%20-0.887712%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_f09092b946ed42d9982237b57f11a45f%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_dc3a4bf00b884381843a32276a147875%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_dc3a4bf00b884381843a32276a147875%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3E%C2%A1Hola%2C%20Zaragoza%21%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_f09092b946ed42d9982237b57f11a45f.setContent%28html_dc3a4bf00b884381843a32276a147875%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_e5123a0f1e9540f2b4ad028328c87e6a.bindPopup%28popup_f09092b946ed42d9982237b57f11a45f%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%3C/script%3E onload="this.contentDocument.open();this.contentDocument.write(    decodeURIComponent(this.getAttribute('data-html')));this.contentDocument.close();" allowfullscreen webkitallowfullscreen mozallowfullscreen></iframe></div></div>



Ahora vamos a hacer un mapa con cada uno de los puntos que tiene nuestra tabla, previamente creada. Lo vamos a hacer con la función interrows, que significa que haga lo mismo para cada fila. Además de que lo hará también con los data frame creados anteriormente.


```python
for index, fila in df_accidentes.iterrows():
    marcador = folium.Marker([fila['lat'],fila['long']],popup=fila['type'])
    mapa.add_child(marcador)
mapa
```




<div style="width:100%;"><div style="position:relative;width:100%;height:0;padding-bottom:60%;"><span style="color:#565656">Make this Notebook Trusted to load map: File -> Trust Notebook</span><iframe src="about:blank" style="position:absolute;width:100%;height:100%;left:0;top:0;border:none !important;" data-html=%3C%21DOCTYPE%20html%3E%0A%3Chead%3E%20%20%20%20%0A%20%20%20%20%3Cmeta%20http-equiv%3D%22content-type%22%20content%3D%22text/html%3B%20charset%3DUTF-8%22%20/%3E%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%3Cscript%3E%0A%20%20%20%20%20%20%20%20%20%20%20%20L_NO_TOUCH%20%3D%20false%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20L_DISABLE_3D%20%3D%20false%3B%0A%20%20%20%20%20%20%20%20%3C/script%3E%0A%20%20%20%20%0A%20%20%20%20%3Cstyle%3Ehtml%2C%20body%20%7Bwidth%3A%20100%25%3Bheight%3A%20100%25%3Bmargin%3A%200%3Bpadding%3A%200%3B%7D%3C/style%3E%0A%20%20%20%20%3Cstyle%3E%23map%20%7Bposition%3Aabsolute%3Btop%3A0%3Bbottom%3A0%3Bright%3A0%3Bleft%3A0%3B%7D%3C/style%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//cdn.jsdelivr.net/npm/leaflet%401.6.0/dist/leaflet.js%22%3E%3C/script%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//code.jquery.com/jquery-1.12.4.min.js%22%3E%3C/script%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/js/bootstrap.min.js%22%3E%3C/script%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//cdnjs.cloudflare.com/ajax/libs/Leaflet.awesome-markers/2.0.2/leaflet.awesome-markers.js%22%3E%3C/script%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//cdn.jsdelivr.net/npm/leaflet%401.6.0/dist/leaflet.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap.min.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap-theme.min.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//maxcdn.bootstrapcdn.com/font-awesome/4.6.3/css/font-awesome.min.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//cdnjs.cloudflare.com/ajax/libs/Leaflet.awesome-markers/2.0.2/leaflet.awesome-markers.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//cdn.jsdelivr.net/gh/python-visualization/folium/folium/templates/leaflet.awesome.rotate.min.css%22/%3E%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20%3Cmeta%20name%3D%22viewport%22%20content%3D%22width%3Ddevice-width%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20initial-scale%3D1.0%2C%20maximum-scale%3D1.0%2C%20user-scalable%3Dno%22%20/%3E%0A%20%20%20%20%20%20%20%20%20%20%20%20%3Cstyle%3E%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%23map_a113325c206e4c5e9cc0b298a04453e1%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20position%3A%20relative%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20width%3A%20100.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20height%3A%20100.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20left%3A%200.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20top%3A%200.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%3C/style%3E%0A%20%20%20%20%20%20%20%20%0A%3C/head%3E%0A%3Cbody%3E%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20%3Cdiv%20class%3D%22folium-map%22%20id%3D%22map_a113325c206e4c5e9cc0b298a04453e1%22%20%3E%3C/div%3E%0A%20%20%20%20%20%20%20%20%0A%3C/body%3E%0A%3Cscript%3E%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20map_a113325c206e4c5e9cc0b298a04453e1%20%3D%20L.map%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%22map_a113325c206e4c5e9cc0b298a04453e1%22%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20center%3A%20%5B41.649693%2C%20-0.887712%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20crs%3A%20L.CRS.EPSG3857%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20zoom%3A%2010%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20zoomControl%3A%20true%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20preferCanvas%3A%20false%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29%3B%0A%0A%20%20%20%20%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20tile_layer_7417ec98414e43a3a505a3a8d408b3ec%20%3D%20L.tileLayer%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%22https%3A//%7Bs%7D.tile.openstreetmap.org/%7Bz%7D/%7Bx%7D/%7By%7D.png%22%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%22attribution%22%3A%20%22Data%20by%20%5Cu0026copy%3B%20%5Cu003ca%20href%3D%5C%22http%3A//openstreetmap.org%5C%22%5Cu003eOpenStreetMap%5Cu003c/a%5Cu003e%2C%20under%20%5Cu003ca%20href%3D%5C%22http%3A//www.openstreetmap.org/copyright%5C%22%5Cu003eODbL%5Cu003c/a%5Cu003e.%22%2C%20%22detectRetina%22%3A%20false%2C%20%22maxNativeZoom%22%3A%2018%2C%20%22maxZoom%22%3A%2018%2C%20%22minZoom%22%3A%200%2C%20%22noWrap%22%3A%20false%2C%20%22opacity%22%3A%201%2C%20%22subdomains%22%3A%20%22abc%22%2C%20%22tms%22%3A%20false%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_e5123a0f1e9540f2b4ad028328c87e6a%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.649693%2C%20-0.887712%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_f09092b946ed42d9982237b57f11a45f%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_dc3a4bf00b884381843a32276a147875%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_dc3a4bf00b884381843a32276a147875%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3E%C2%A1Hola%2C%20Zaragoza%21%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_f09092b946ed42d9982237b57f11a45f.setContent%28html_dc3a4bf00b884381843a32276a147875%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_e5123a0f1e9540f2b4ad028328c87e6a.bindPopup%28popup_f09092b946ed42d9982237b57f11a45f%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_f070fd117eca48958a0b64b7d3cbf923%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8818527060979306%2C%2041.649027473051156%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_f1a7236ca5794bd283b78b93168b8ed5%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_a2e3124934404c8d99fbe36a8a2cad64%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_a2e3124934404c8d99fbe36a8a2cad64%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ESALIDA%20CALZADA%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_f1a7236ca5794bd283b78b93168b8ed5.setContent%28html_a2e3124934404c8d99fbe36a8a2cad64%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_f070fd117eca48958a0b64b7d3cbf923.bindPopup%28popup_f1a7236ca5794bd283b78b93168b8ed5%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_665eea19b75e4fb0bdd12a258653119d%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8645810716721081%2C%2041.661585829868585%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_123fbec29e794a25b5fb6a01a21081fa%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_6d334881b9ef41eca36a5d821d69d936%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_6d334881b9ef41eca36a5d821d69d936%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_123fbec29e794a25b5fb6a01a21081fa.setContent%28html_6d334881b9ef41eca36a5d821d69d936%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_665eea19b75e4fb0bdd12a258653119d.bindPopup%28popup_123fbec29e794a25b5fb6a01a21081fa%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_1731063bc3b744d8937ce344092e5f33%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.887776415002892%2C%2041.666992622958105%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_98cb69532b664b90890914d2b6ac6aa5%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_7a7d46672754464fa30df3361cccf793%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_7a7d46672754464fa30df3361cccf793%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_98cb69532b664b90890914d2b6ac6aa5.setContent%28html_7a7d46672754464fa30df3361cccf793%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_1731063bc3b744d8937ce344092e5f33.bindPopup%28popup_98cb69532b664b90890914d2b6ac6aa5%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_4d2b8bef7c4043eab8285a7a8d67f574%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8825260453930127%2C%2041.62957498750602%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_44627a4203de4d99a17f4a88a93b317b%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_aef831443a2643bcbd92dc29ce825133%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_aef831443a2643bcbd92dc29ce825133%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLIS%20FRONTOLATERAL%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_44627a4203de4d99a17f4a88a93b317b.setContent%28html_aef831443a2643bcbd92dc29ce825133%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_4d2b8bef7c4043eab8285a7a8d67f574.bindPopup%28popup_44627a4203de4d99a17f4a88a93b317b%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_dc5d99400ac24fe7a366ab5929270d1e%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.908314757720389%2C%2041.6562121210704%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_e5af535814624763a9e15d247a2466da%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_5f05bfdb886745b2a38b857350f6df55%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_5f05bfdb886745b2a38b857350f6df55%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ESALIDA%20CALZADA%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_e5af535814624763a9e15d247a2466da.setContent%28html_5f05bfdb886745b2a38b857350f6df55%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_dc5d99400ac24fe7a366ab5929270d1e.bindPopup%28popup_e5af535814624763a9e15d247a2466da%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_5ac2d44d331948359f0c2c7f21ba03dd%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8691088511672924%2C%2041.65949772773082%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_2c29456244074717a0346df6567e6fcc%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_8ba019594481458b8a1aa4b079f4c0ca%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_8ba019594481458b8a1aa4b079f4c0ca%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3EOTRAS%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_2c29456244074717a0346df6567e6fcc.setContent%28html_8ba019594481458b8a1aa4b079f4c0ca%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_5ac2d44d331948359f0c2c7f21ba03dd.bindPopup%28popup_2c29456244074717a0346df6567e6fcc%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_c8a507ec30d843ff85badbe0d65aac9a%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8880337913721866%2C%2041.633353667694024%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_264cdc4e4d244de6a75a8bf057e8280a%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_c47c7a37938b41c9a1662116996159f0%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_c47c7a37938b41c9a1662116996159f0%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3EATROPELLO%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_264cdc4e4d244de6a75a8bf057e8280a.setContent%28html_c47c7a37938b41c9a1662116996159f0%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_c8a507ec30d843ff85badbe0d65aac9a.bindPopup%28popup_264cdc4e4d244de6a75a8bf057e8280a%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_54d12b9bc4ab490cbba5443bdb174f02%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8708838775078237%2C%2041.6390382112928%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_d62d664689bb4468b569a7bccab46d32%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_deecb0c5dcaf4ddd9ceb1986891573db%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_deecb0c5dcaf4ddd9ceb1986891573db%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECAIDA%20SOBRE%20CALZADA%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_d62d664689bb4468b569a7bccab46d32.setContent%28html_deecb0c5dcaf4ddd9ceb1986891573db%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_54d12b9bc4ab490cbba5443bdb174f02.bindPopup%28popup_d62d664689bb4468b569a7bccab46d32%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_b41e7399045e401c835b4a712f30778c%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8970649943808023%2C%2041.64083344974765%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_f56437c38c014bb8973d2c695da78748%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_a7ed1bcc86f0460b97b79f52f207bd65%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_a7ed1bcc86f0460b97b79f52f207bd65%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLIS.%20MARCHA%20ATR%C3%81S%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_f56437c38c014bb8973d2c695da78748.setContent%28html_a7ed1bcc86f0460b97b79f52f207bd65%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_b41e7399045e401c835b4a712f30778c.bindPopup%28popup_f56437c38c014bb8973d2c695da78748%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_d4edc636fefc4c9d9d50da2971fa653b%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8718525605769747%2C%2041.64904657717317%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_2763cac4e4f94f0f99cb29ed26a34264%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_1f8400ca7f7e4b4cb17c1448d7e2cab6%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_1f8400ca7f7e4b4cb17c1448d7e2cab6%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20LATERAL%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_2763cac4e4f94f0f99cb29ed26a34264.setContent%28html_1f8400ca7f7e4b4cb17c1448d7e2cab6%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_d4edc636fefc4c9d9d50da2971fa653b.bindPopup%28popup_2763cac4e4f94f0f99cb29ed26a34264%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_faff2f4a287a41d698c92a7e138c3d07%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8964627561577849%2C%2041.64322365075108%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_fecdaf98bcbc43efa366a5decf32cb83%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_304b4fbff6db469a999fc7fe94c9bc36%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_304b4fbff6db469a999fc7fe94c9bc36%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3EOTRAS%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_fecdaf98bcbc43efa366a5decf32cb83.setContent%28html_304b4fbff6db469a999fc7fe94c9bc36%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_faff2f4a287a41d698c92a7e138c3d07.bindPopup%28popup_fecdaf98bcbc43efa366a5decf32cb83%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_f3867ae43536407884c5f0c4907d8678%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8778095796207178%2C%2041.68753087470739%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_8c428a6937d647c1aa3bff1b946e15b7%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_624f4dc308f14156b11c3ae7476d8a83%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_624f4dc308f14156b11c3ae7476d8a83%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_8c428a6937d647c1aa3bff1b946e15b7.setContent%28html_624f4dc308f14156b11c3ae7476d8a83%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_f3867ae43536407884c5f0c4907d8678.bindPopup%28popup_8c428a6937d647c1aa3bff1b946e15b7%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_a8fa2c22e8514703adbe20e8db3ddcf5%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8812157329722801%2C%2041.661646612715046%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_e24cdc3565744b009a873e779ef2ca17%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_0339ab44e3dc4d3e86e6093ef9524e5e%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_0339ab44e3dc4d3e86e6093ef9524e5e%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ESALIDA%20CALZADA%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_e24cdc3565744b009a873e779ef2ca17.setContent%28html_0339ab44e3dc4d3e86e6093ef9524e5e%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_a8fa2c22e8514703adbe20e8db3ddcf5.bindPopup%28popup_e24cdc3565744b009a873e779ef2ca17%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_dd58cf6867f342249f84ca6664791505%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8762000299022707%2C%2041.6454384961757%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_679b1a27be0244f28fbe6702f0759d93%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_ec9671733ce5406b8885a3a5b530587f%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_ec9671733ce5406b8885a3a5b530587f%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_679b1a27be0244f28fbe6702f0759d93.setContent%28html_ec9671733ce5406b8885a3a5b530587f%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_dd58cf6867f342249f84ca6664791505.bindPopup%28popup_679b1a27be0244f28fbe6702f0759d93%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_3946615425474cb9a27702410d1efe8f%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.9089013552408617%2C%2041.65543768899759%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_a910fee7b2134de59350f369802ee236%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_96d08d5279254b7eb572eae5efcc77c7%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_96d08d5279254b7eb572eae5efcc77c7%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3EATROPELLO%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_a910fee7b2134de59350f369802ee236.setContent%28html_96d08d5279254b7eb572eae5efcc77c7%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_3946615425474cb9a27702410d1efe8f.bindPopup%28popup_a910fee7b2134de59350f369802ee236%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_3c6f9aba79cd476d86f8c8b9693246e0%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.9004729973337304%2C%2041.65180346604993%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_f18fcb542243411eabc20ce22126e509%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_fb3f39efc5fc43deb006a8ef6ca091f7%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_fb3f39efc5fc43deb006a8ef6ca091f7%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_f18fcb542243411eabc20ce22126e509.setContent%28html_fb3f39efc5fc43deb006a8ef6ca091f7%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_3c6f9aba79cd476d86f8c8b9693246e0.bindPopup%28popup_f18fcb542243411eabc20ce22126e509%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_3b6bb3a0a3624e3eb22a645a4df3cb1d%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8917562993466011%2C%2041.65233828238132%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_09c9d0a58c3a46339d66c507e9ab02ec%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_a92cb19dc099491298e0bd4acde75807%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_a92cb19dc099491298e0bd4acde75807%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_09c9d0a58c3a46339d66c507e9ab02ec.setContent%28html_a92cb19dc099491298e0bd4acde75807%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_3b6bb3a0a3624e3eb22a645a4df3cb1d.bindPopup%28popup_09c9d0a58c3a46339d66c507e9ab02ec%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_caf967e297de4af9a4ca3fb395281d69%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.888856043735591%2C%2041.65040494617356%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_ed6c299d092843d48d78406c55685638%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_8552b88b76a3496e935c78f63171bd70%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_8552b88b76a3496e935c78f63171bd70%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_ed6c299d092843d48d78406c55685638.setContent%28html_8552b88b76a3496e935c78f63171bd70%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_caf967e297de4af9a4ca3fb395281d69.bindPopup%28popup_ed6c299d092843d48d78406c55685638%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_6a5f8d48f6be4e09a3142eb019142e3a%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8629911318784169%2C%2041.645335650478316%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_355dbb8c245047229054b694937367e0%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_a429bab4f74e493c9ecc85dcca4ebd16%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_a429bab4f74e493c9ecc85dcca4ebd16%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_355dbb8c245047229054b694937367e0.setContent%28html_a429bab4f74e493c9ecc85dcca4ebd16%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_6a5f8d48f6be4e09a3142eb019142e3a.bindPopup%28popup_355dbb8c245047229054b694937367e0%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_1780ad31aaca4f5592a993f3778b1ed8%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8870207060655807%2C%2041.609992514227066%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_b5ba603077184a9b97edc6bfb80e1fad%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_b0c034f7d5904ae5adbecac6f358b9dd%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_b0c034f7d5904ae5adbecac6f358b9dd%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_b5ba603077184a9b97edc6bfb80e1fad.setContent%28html_b0c034f7d5904ae5adbecac6f358b9dd%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_1780ad31aaca4f5592a993f3778b1ed8.bindPopup%28popup_b5ba603077184a9b97edc6bfb80e1fad%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_bff425a118c640479ebfeef3b0cd9b6e%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8818527060979306%2C%2041.649027473051156%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_968d041aba054bb7a1dc2e74a0c7f6f5%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_a989334a1dac4a7a886ff2163a04353a%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_a989334a1dac4a7a886ff2163a04353a%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ESALIDA%20CALZADA%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_968d041aba054bb7a1dc2e74a0c7f6f5.setContent%28html_a989334a1dac4a7a886ff2163a04353a%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_bff425a118c640479ebfeef3b0cd9b6e.bindPopup%28popup_968d041aba054bb7a1dc2e74a0c7f6f5%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_4f90fcda8ba74d8c942719881f10023d%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8645810716721081%2C%2041.661585829868585%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_ae881fbfab1346c88b68158fc9570d18%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_b45a9208f5d544cd80585a7e4f9a584a%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_b45a9208f5d544cd80585a7e4f9a584a%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_ae881fbfab1346c88b68158fc9570d18.setContent%28html_b45a9208f5d544cd80585a7e4f9a584a%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_4f90fcda8ba74d8c942719881f10023d.bindPopup%28popup_ae881fbfab1346c88b68158fc9570d18%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_9e46455f28864e3db555fc0e43d26388%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.887776415002892%2C%2041.666992622958105%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_b6f0d76a358d4642a12b8596edcac849%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_556b5353f36b4238b83cd67c88148af5%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_556b5353f36b4238b83cd67c88148af5%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_b6f0d76a358d4642a12b8596edcac849.setContent%28html_556b5353f36b4238b83cd67c88148af5%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_9e46455f28864e3db555fc0e43d26388.bindPopup%28popup_b6f0d76a358d4642a12b8596edcac849%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_2dc9d1de3ade4282b890dbb00116b934%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8825260453930127%2C%2041.62957498750602%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_72315566812f41339d4e0947a7f9c0b5%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_2643b73b6f504527b45d0bbf51e46591%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_2643b73b6f504527b45d0bbf51e46591%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLIS%20FRONTOLATERAL%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_72315566812f41339d4e0947a7f9c0b5.setContent%28html_2643b73b6f504527b45d0bbf51e46591%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_2dc9d1de3ade4282b890dbb00116b934.bindPopup%28popup_72315566812f41339d4e0947a7f9c0b5%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_dd2582716d6a4f75a5ff87631d429b71%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.908314757720389%2C%2041.6562121210704%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_05d0ad499bf04874b6ee0b0cb8dc02be%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_b3a799f03f404583acf2c73a73216d93%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_b3a799f03f404583acf2c73a73216d93%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ESALIDA%20CALZADA%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_05d0ad499bf04874b6ee0b0cb8dc02be.setContent%28html_b3a799f03f404583acf2c73a73216d93%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_dd2582716d6a4f75a5ff87631d429b71.bindPopup%28popup_05d0ad499bf04874b6ee0b0cb8dc02be%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_03206880a59c47509b2bb23c4c25d072%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8691088511672924%2C%2041.65949772773082%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_fc0521422d0f40c6833e5a52aed32288%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_b78bec5273f745498a8a01f6b7de95a4%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_b78bec5273f745498a8a01f6b7de95a4%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3EOTRAS%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_fc0521422d0f40c6833e5a52aed32288.setContent%28html_b78bec5273f745498a8a01f6b7de95a4%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_03206880a59c47509b2bb23c4c25d072.bindPopup%28popup_fc0521422d0f40c6833e5a52aed32288%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_8fb7a6c8f2714fb58b4756ecd2c4412d%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8880337913721866%2C%2041.633353667694024%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_b36edb2148a84b5996b500916ba9ef4f%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_8315c5cd621145a2b8a196467842f66a%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_8315c5cd621145a2b8a196467842f66a%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3EATROPELLO%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_b36edb2148a84b5996b500916ba9ef4f.setContent%28html_8315c5cd621145a2b8a196467842f66a%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_8fb7a6c8f2714fb58b4756ecd2c4412d.bindPopup%28popup_b36edb2148a84b5996b500916ba9ef4f%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_2253d1d90edc46c5a96ee2cb48a202ab%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8708838775078237%2C%2041.6390382112928%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_d039258909fe4f6fa1dda0129e4ef9b0%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_62c2771e2d8340949664417cb2398661%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_62c2771e2d8340949664417cb2398661%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECAIDA%20SOBRE%20CALZADA%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_d039258909fe4f6fa1dda0129e4ef9b0.setContent%28html_62c2771e2d8340949664417cb2398661%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_2253d1d90edc46c5a96ee2cb48a202ab.bindPopup%28popup_d039258909fe4f6fa1dda0129e4ef9b0%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_88b4f8d435274d99bc45f44342bbf0cb%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8970649943808023%2C%2041.64083344974765%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_580636bb59774e45b0f1c7745b425873%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_05e4147d1d394e91a11439792a925af6%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_05e4147d1d394e91a11439792a925af6%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLIS.%20MARCHA%20ATR%C3%81S%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_580636bb59774e45b0f1c7745b425873.setContent%28html_05e4147d1d394e91a11439792a925af6%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_88b4f8d435274d99bc45f44342bbf0cb.bindPopup%28popup_580636bb59774e45b0f1c7745b425873%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_4a568e82951242cba0ab70e4f3523f20%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8718525605769747%2C%2041.64904657717317%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_4163a8775e6f432eaf6c77a22aed2cbc%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_33ab0ee0958c4d26ad38947ae5392b01%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_33ab0ee0958c4d26ad38947ae5392b01%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20LATERAL%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_4163a8775e6f432eaf6c77a22aed2cbc.setContent%28html_33ab0ee0958c4d26ad38947ae5392b01%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_4a568e82951242cba0ab70e4f3523f20.bindPopup%28popup_4163a8775e6f432eaf6c77a22aed2cbc%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_34164585f52b44d9ad02da253a491d69%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8964627561577849%2C%2041.64322365075108%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_4670ccf2fcfe42fe8658288960a618e1%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_6a3d79e038e14a1ea228e716420e4f69%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_6a3d79e038e14a1ea228e716420e4f69%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3EOTRAS%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_4670ccf2fcfe42fe8658288960a618e1.setContent%28html_6a3d79e038e14a1ea228e716420e4f69%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_34164585f52b44d9ad02da253a491d69.bindPopup%28popup_4670ccf2fcfe42fe8658288960a618e1%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_6ee9a9568770459d8992fa80df7d9cdc%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8778095796207178%2C%2041.68753087470739%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_da5ca0de0f2e497c9f97b248ae49ade1%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_d813e0098166470f9925c6451fea489d%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_d813e0098166470f9925c6451fea489d%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_da5ca0de0f2e497c9f97b248ae49ade1.setContent%28html_d813e0098166470f9925c6451fea489d%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_6ee9a9568770459d8992fa80df7d9cdc.bindPopup%28popup_da5ca0de0f2e497c9f97b248ae49ade1%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_f61a21fc2fd34aef966a701e818264d3%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8812157329722801%2C%2041.661646612715046%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_01d35fa41aec411fbc341c0269a644f2%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_3cf1714d50f4428396392f6b7c836fa8%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_3cf1714d50f4428396392f6b7c836fa8%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ESALIDA%20CALZADA%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_01d35fa41aec411fbc341c0269a644f2.setContent%28html_3cf1714d50f4428396392f6b7c836fa8%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_f61a21fc2fd34aef966a701e818264d3.bindPopup%28popup_01d35fa41aec411fbc341c0269a644f2%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_aa0d85392c164e7bb32fdd69adf10fdf%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8762000299022707%2C%2041.6454384961757%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_f3a3106ca0974cd68c716301b63f7170%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_fc0cc551ff9846ac851cd4e3032f65fe%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_fc0cc551ff9846ac851cd4e3032f65fe%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_f3a3106ca0974cd68c716301b63f7170.setContent%28html_fc0cc551ff9846ac851cd4e3032f65fe%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_aa0d85392c164e7bb32fdd69adf10fdf.bindPopup%28popup_f3a3106ca0974cd68c716301b63f7170%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_ea5b8784d34f444d83348a8a279a52e8%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.9089013552408617%2C%2041.65543768899759%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_3aaeb245e5844e718bfab85f9494f82a%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_1deeb89e11794509b59ea38d25c02ff1%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_1deeb89e11794509b59ea38d25c02ff1%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3EATROPELLO%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_3aaeb245e5844e718bfab85f9494f82a.setContent%28html_1deeb89e11794509b59ea38d25c02ff1%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_ea5b8784d34f444d83348a8a279a52e8.bindPopup%28popup_3aaeb245e5844e718bfab85f9494f82a%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_250cc2350be140fb9396dc1512bc43dd%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.9004729973337304%2C%2041.65180346604993%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_cf27b962b65d4a17996c9028bcf617d4%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_6a9519a67d7f45f69def1d87e78e8b59%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_6a9519a67d7f45f69def1d87e78e8b59%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_cf27b962b65d4a17996c9028bcf617d4.setContent%28html_6a9519a67d7f45f69def1d87e78e8b59%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_250cc2350be140fb9396dc1512bc43dd.bindPopup%28popup_cf27b962b65d4a17996c9028bcf617d4%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_83ce093b3b074e6a871a744f257925fd%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8917562993466011%2C%2041.65233828238132%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_2a257bf6f1f3444ca818c14c10242b89%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_f67b021e9d9941e08d0d70841f0b786d%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_f67b021e9d9941e08d0d70841f0b786d%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_2a257bf6f1f3444ca818c14c10242b89.setContent%28html_f67b021e9d9941e08d0d70841f0b786d%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_83ce093b3b074e6a871a744f257925fd.bindPopup%28popup_2a257bf6f1f3444ca818c14c10242b89%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_a1af5c451207477d97acc056ed481316%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.888856043735591%2C%2041.65040494617356%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_e3ce186fba4b45f3aedf384ea74d0807%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_34d1d4f38eb64f9a948037bcc6f955ab%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_34d1d4f38eb64f9a948037bcc6f955ab%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_e3ce186fba4b45f3aedf384ea74d0807.setContent%28html_34d1d4f38eb64f9a948037bcc6f955ab%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_a1af5c451207477d97acc056ed481316.bindPopup%28popup_e3ce186fba4b45f3aedf384ea74d0807%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_d3c730a7b9c44fcdaaf20119d72183ea%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8629911318784169%2C%2041.645335650478316%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_9ab5c98c085d41bcab7b15f79b382516%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_469df4b883194fbab4414c59be1bbfb1%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_469df4b883194fbab4414c59be1bbfb1%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_9ab5c98c085d41bcab7b15f79b382516.setContent%28html_469df4b883194fbab4414c59be1bbfb1%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_d3c730a7b9c44fcdaaf20119d72183ea.bindPopup%28popup_9ab5c98c085d41bcab7b15f79b382516%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_03fe74c57e014a909e1888604c70e7d5%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8870207060655807%2C%2041.609992514227066%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_80d5f4ab90c6449f909cd1fe15e838fd%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_5fc37e1fae13482b9119d9308132c8c2%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_5fc37e1fae13482b9119d9308132c8c2%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_80d5f4ab90c6449f909cd1fe15e838fd.setContent%28html_5fc37e1fae13482b9119d9308132c8c2%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_03fe74c57e014a909e1888604c70e7d5.bindPopup%28popup_80d5f4ab90c6449f909cd1fe15e838fd%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_abc1d418d44a4f6093b167031e89a82b%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8818527060979306%2C%2041.649027473051156%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_c3650c7d7b5e4d219851fa96245fbb4a%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_53491e91e30d46c4b66caa612f373a85%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_53491e91e30d46c4b66caa612f373a85%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ESALIDA%20CALZADA%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_c3650c7d7b5e4d219851fa96245fbb4a.setContent%28html_53491e91e30d46c4b66caa612f373a85%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_abc1d418d44a4f6093b167031e89a82b.bindPopup%28popup_c3650c7d7b5e4d219851fa96245fbb4a%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_20ceae4b238248aba9169ae9ac746189%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8645810716721081%2C%2041.661585829868585%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_1b22ebc3b91045889190ba5615bc8245%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_664bd6bf17fa4f51946a130c6200a5a3%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_664bd6bf17fa4f51946a130c6200a5a3%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_1b22ebc3b91045889190ba5615bc8245.setContent%28html_664bd6bf17fa4f51946a130c6200a5a3%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_20ceae4b238248aba9169ae9ac746189.bindPopup%28popup_1b22ebc3b91045889190ba5615bc8245%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_cc3ff38ede1c4c508de07ed5590e05e8%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.887776415002892%2C%2041.666992622958105%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_07d1692218794db6bbbf61b1f875c64a%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_d238527f0e0a48d09dd7b44f71c12167%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_d238527f0e0a48d09dd7b44f71c12167%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_07d1692218794db6bbbf61b1f875c64a.setContent%28html_d238527f0e0a48d09dd7b44f71c12167%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_cc3ff38ede1c4c508de07ed5590e05e8.bindPopup%28popup_07d1692218794db6bbbf61b1f875c64a%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_3e1341d098af42f6a3eb365168f10480%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8825260453930127%2C%2041.62957498750602%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_d9f26deb7df74a95aabc51ebaf3223bf%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_552bd1adf8e941639d08506d0a07ee79%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_552bd1adf8e941639d08506d0a07ee79%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLIS%20FRONTOLATERAL%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_d9f26deb7df74a95aabc51ebaf3223bf.setContent%28html_552bd1adf8e941639d08506d0a07ee79%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_3e1341d098af42f6a3eb365168f10480.bindPopup%28popup_d9f26deb7df74a95aabc51ebaf3223bf%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_52987e19e84045839264d3c00d3c8953%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.908314757720389%2C%2041.6562121210704%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_eb3b19d6ed6c48208964d4104ba471c2%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_bdd5c7586b3348f7ade96721ff60ceb5%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_bdd5c7586b3348f7ade96721ff60ceb5%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ESALIDA%20CALZADA%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_eb3b19d6ed6c48208964d4104ba471c2.setContent%28html_bdd5c7586b3348f7ade96721ff60ceb5%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_52987e19e84045839264d3c00d3c8953.bindPopup%28popup_eb3b19d6ed6c48208964d4104ba471c2%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_16c1b774b7eb4362a8d548c4cf61f3c7%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8691088511672924%2C%2041.65949772773082%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_b45bc0cfb7c844c1916463c6b7b7da76%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_80b7dfc86ca048d5be59f8092ead7ac1%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_80b7dfc86ca048d5be59f8092ead7ac1%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3EOTRAS%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_b45bc0cfb7c844c1916463c6b7b7da76.setContent%28html_80b7dfc86ca048d5be59f8092ead7ac1%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_16c1b774b7eb4362a8d548c4cf61f3c7.bindPopup%28popup_b45bc0cfb7c844c1916463c6b7b7da76%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_32ae1b05fec5436ab3ee5fb7fede85a9%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8880337913721866%2C%2041.633353667694024%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_fc33ed964cc24e459d828539ce144d44%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_94d3a5a08bf441b59f2013aa217c5888%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_94d3a5a08bf441b59f2013aa217c5888%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3EATROPELLO%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_fc33ed964cc24e459d828539ce144d44.setContent%28html_94d3a5a08bf441b59f2013aa217c5888%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_32ae1b05fec5436ab3ee5fb7fede85a9.bindPopup%28popup_fc33ed964cc24e459d828539ce144d44%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_59370ae4b0ff4d0db5a220b4e021faa6%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8708838775078237%2C%2041.6390382112928%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_78b8518dcf6d4957aa5b2beda1245ae5%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_61bed660e0974bcbb038d7bf6b51e97d%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_61bed660e0974bcbb038d7bf6b51e97d%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECAIDA%20SOBRE%20CALZADA%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_78b8518dcf6d4957aa5b2beda1245ae5.setContent%28html_61bed660e0974bcbb038d7bf6b51e97d%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_59370ae4b0ff4d0db5a220b4e021faa6.bindPopup%28popup_78b8518dcf6d4957aa5b2beda1245ae5%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_5d1c0eb3db2545f2ac992e69d10e089e%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8970649943808023%2C%2041.64083344974765%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_7c33d969c7b840c692787246095b5d63%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_e53a36de1c2441d586324097c0339f5f%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_e53a36de1c2441d586324097c0339f5f%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLIS.%20MARCHA%20ATR%C3%81S%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_7c33d969c7b840c692787246095b5d63.setContent%28html_e53a36de1c2441d586324097c0339f5f%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_5d1c0eb3db2545f2ac992e69d10e089e.bindPopup%28popup_7c33d969c7b840c692787246095b5d63%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_ba72144443e44713a03a0f37fe45dc00%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8718525605769747%2C%2041.64904657717317%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_e491df549266473bb171a29be471286d%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_56d1da71a03743af932beaa109dadc8e%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_56d1da71a03743af932beaa109dadc8e%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20LATERAL%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_e491df549266473bb171a29be471286d.setContent%28html_56d1da71a03743af932beaa109dadc8e%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_ba72144443e44713a03a0f37fe45dc00.bindPopup%28popup_e491df549266473bb171a29be471286d%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_faeb55c659ee4ae6938265b5cb3ab386%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8964627561577849%2C%2041.64322365075108%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_1815c8a1d66d4e9da8f3a76ee0f364fb%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_7a8eeed9f796440a8bdcc406ad18d6a1%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_7a8eeed9f796440a8bdcc406ad18d6a1%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3EOTRAS%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_1815c8a1d66d4e9da8f3a76ee0f364fb.setContent%28html_7a8eeed9f796440a8bdcc406ad18d6a1%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_faeb55c659ee4ae6938265b5cb3ab386.bindPopup%28popup_1815c8a1d66d4e9da8f3a76ee0f364fb%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_db6380154d4648c3a9338289fdfe9e2f%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8778095796207178%2C%2041.68753087470739%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_1ef85821754c44c2a1fa61b10e2c0e87%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_d4fdabbc52fe49a8b16eae8e5cd6ec8c%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_d4fdabbc52fe49a8b16eae8e5cd6ec8c%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_1ef85821754c44c2a1fa61b10e2c0e87.setContent%28html_d4fdabbc52fe49a8b16eae8e5cd6ec8c%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_db6380154d4648c3a9338289fdfe9e2f.bindPopup%28popup_1ef85821754c44c2a1fa61b10e2c0e87%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_83627abb1eea41a989ec613c32ac76b3%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8812157329722801%2C%2041.661646612715046%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_dff69e70e417429f96e3727503383deb%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_3e93664e4aae4da981ec7174094c7e45%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_3e93664e4aae4da981ec7174094c7e45%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ESALIDA%20CALZADA%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_dff69e70e417429f96e3727503383deb.setContent%28html_3e93664e4aae4da981ec7174094c7e45%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_83627abb1eea41a989ec613c32ac76b3.bindPopup%28popup_dff69e70e417429f96e3727503383deb%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_98e35d677a4c4f298fe8dfac7507382c%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8762000299022707%2C%2041.6454384961757%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_0ab65c614a9c40a9a684375a4c5634d2%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_e2715c55116a4af58d8a34e0ec303bff%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_e2715c55116a4af58d8a34e0ec303bff%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_0ab65c614a9c40a9a684375a4c5634d2.setContent%28html_e2715c55116a4af58d8a34e0ec303bff%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_98e35d677a4c4f298fe8dfac7507382c.bindPopup%28popup_0ab65c614a9c40a9a684375a4c5634d2%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_a5e987c12616445a9086aaa7f39efce0%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.9089013552408617%2C%2041.65543768899759%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_0d2b13322755431b8a62d716b1b4aef9%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_15a0332d9e2e43c78f92a0171275d173%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_15a0332d9e2e43c78f92a0171275d173%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3EATROPELLO%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_0d2b13322755431b8a62d716b1b4aef9.setContent%28html_15a0332d9e2e43c78f92a0171275d173%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_a5e987c12616445a9086aaa7f39efce0.bindPopup%28popup_0d2b13322755431b8a62d716b1b4aef9%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_55e424fdccb2468b8729958232184d4b%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.9004729973337304%2C%2041.65180346604993%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_81d7fc737c7047d793796a33a06963cb%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_36f8d3d0e76a4a44b81a6014a3c9fd9d%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_36f8d3d0e76a4a44b81a6014a3c9fd9d%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_81d7fc737c7047d793796a33a06963cb.setContent%28html_36f8d3d0e76a4a44b81a6014a3c9fd9d%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_55e424fdccb2468b8729958232184d4b.bindPopup%28popup_81d7fc737c7047d793796a33a06963cb%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_31dda6606ba248369deb666a4fcc3fa5%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8917562993466011%2C%2041.65233828238132%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_c3febdc9b5d64c79b22ae1aa1c35cc83%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_ce8aacc8f37a46d2a26d6bd6ebd0cd02%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_ce8aacc8f37a46d2a26d6bd6ebd0cd02%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_c3febdc9b5d64c79b22ae1aa1c35cc83.setContent%28html_ce8aacc8f37a46d2a26d6bd6ebd0cd02%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_31dda6606ba248369deb666a4fcc3fa5.bindPopup%28popup_c3febdc9b5d64c79b22ae1aa1c35cc83%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_3deef009412647ad9a24dc1a2b30a9d1%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.888856043735591%2C%2041.65040494617356%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_079e06e991a740be85b905b6254b0df4%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_5e37383a683a48b2995b688e4e0c3b64%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_5e37383a683a48b2995b688e4e0c3b64%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_079e06e991a740be85b905b6254b0df4.setContent%28html_5e37383a683a48b2995b688e4e0c3b64%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_3deef009412647ad9a24dc1a2b30a9d1.bindPopup%28popup_079e06e991a740be85b905b6254b0df4%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_4487e3e558bf4c8b81ca0d8c2dca9061%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8629911318784169%2C%2041.645335650478316%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_cddedb6c67d942ed8b64e2a25ef3f5e1%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_c91e6003ac2243aba0cb6dd2707e8f8c%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_c91e6003ac2243aba0cb6dd2707e8f8c%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_cddedb6c67d942ed8b64e2a25ef3f5e1.setContent%28html_c91e6003ac2243aba0cb6dd2707e8f8c%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_4487e3e558bf4c8b81ca0d8c2dca9061.bindPopup%28popup_cddedb6c67d942ed8b64e2a25ef3f5e1%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_34e8cd9fee30466dbc87038a8feab315%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8870207060655807%2C%2041.609992514227066%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_8bff7c94981b44a08c91b4e2503a94e2%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_1fd065db586c4aeeb7926ee15d6af81c%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_1fd065db586c4aeeb7926ee15d6af81c%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_8bff7c94981b44a08c91b4e2503a94e2.setContent%28html_1fd065db586c4aeeb7926ee15d6af81c%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_34e8cd9fee30466dbc87038a8feab315.bindPopup%28popup_8bff7c94981b44a08c91b4e2503a94e2%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_a2448a3e71d14d28b8ccbf7c2ca80ea1%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8818527060979306%2C%2041.649027473051156%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_b72b9907afee44d2b63905479bbb5be2%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_fa74600ce93c4cea8fa36f6d0854ed58%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_fa74600ce93c4cea8fa36f6d0854ed58%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ESALIDA%20CALZADA%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_b72b9907afee44d2b63905479bbb5be2.setContent%28html_fa74600ce93c4cea8fa36f6d0854ed58%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_a2448a3e71d14d28b8ccbf7c2ca80ea1.bindPopup%28popup_b72b9907afee44d2b63905479bbb5be2%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_81405831f78f417ebf48b762410c2d45%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8645810716721081%2C%2041.661585829868585%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_069dd5937ddf42a087c5a77929d430cf%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_b504bf97267d4092bf1e5f2e734ba784%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_b504bf97267d4092bf1e5f2e734ba784%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_069dd5937ddf42a087c5a77929d430cf.setContent%28html_b504bf97267d4092bf1e5f2e734ba784%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_81405831f78f417ebf48b762410c2d45.bindPopup%28popup_069dd5937ddf42a087c5a77929d430cf%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_1b8fb3d72986418c98b73120a3cd93f0%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.887776415002892%2C%2041.666992622958105%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_48784fcba549496fa3df1d4b9e15d273%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_1d3ff9a6640946bb8468ef1996425f2f%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_1d3ff9a6640946bb8468ef1996425f2f%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_48784fcba549496fa3df1d4b9e15d273.setContent%28html_1d3ff9a6640946bb8468ef1996425f2f%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_1b8fb3d72986418c98b73120a3cd93f0.bindPopup%28popup_48784fcba549496fa3df1d4b9e15d273%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_97c7d61242db462c90b28e0e54c87a77%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8825260453930127%2C%2041.62957498750602%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_2a3f9de291a04f05952252c8dd376300%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_1b2612954df1448f9ae60015a0cdd3d6%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_1b2612954df1448f9ae60015a0cdd3d6%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLIS%20FRONTOLATERAL%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_2a3f9de291a04f05952252c8dd376300.setContent%28html_1b2612954df1448f9ae60015a0cdd3d6%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_97c7d61242db462c90b28e0e54c87a77.bindPopup%28popup_2a3f9de291a04f05952252c8dd376300%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_9ff06d1f457248d6a8b7869368a8ccb4%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.908314757720389%2C%2041.6562121210704%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_46d735369c214ec8bfb66b6ebe257fa3%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_e69cc79dca1f42239dbe88ea569e3003%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_e69cc79dca1f42239dbe88ea569e3003%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ESALIDA%20CALZADA%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_46d735369c214ec8bfb66b6ebe257fa3.setContent%28html_e69cc79dca1f42239dbe88ea569e3003%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_9ff06d1f457248d6a8b7869368a8ccb4.bindPopup%28popup_46d735369c214ec8bfb66b6ebe257fa3%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_a42aa65f7e61458c8d3d9f6bc8a97d62%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8691088511672924%2C%2041.65949772773082%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_030914b5da3f49e68a859b8be3080489%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_63b04e9673b94e1abfa39723a56d0420%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_63b04e9673b94e1abfa39723a56d0420%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3EOTRAS%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_030914b5da3f49e68a859b8be3080489.setContent%28html_63b04e9673b94e1abfa39723a56d0420%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_a42aa65f7e61458c8d3d9f6bc8a97d62.bindPopup%28popup_030914b5da3f49e68a859b8be3080489%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_85dba60cf7c2444cad3a494c3edf7f5e%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8880337913721866%2C%2041.633353667694024%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_0e4d5320d46e4289bba3722953bc968e%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_5d76a5d27ec04dc99d648655e3b6f476%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_5d76a5d27ec04dc99d648655e3b6f476%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3EATROPELLO%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_0e4d5320d46e4289bba3722953bc968e.setContent%28html_5d76a5d27ec04dc99d648655e3b6f476%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_85dba60cf7c2444cad3a494c3edf7f5e.bindPopup%28popup_0e4d5320d46e4289bba3722953bc968e%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_cb321b9fdd854a9bb0abb74580c7fb36%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8708838775078237%2C%2041.6390382112928%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_5d2a0431c52149ffbd0fceae3ea17eef%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_7119e0773a15482d8ebf0c3c03347918%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_7119e0773a15482d8ebf0c3c03347918%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECAIDA%20SOBRE%20CALZADA%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_5d2a0431c52149ffbd0fceae3ea17eef.setContent%28html_7119e0773a15482d8ebf0c3c03347918%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_cb321b9fdd854a9bb0abb74580c7fb36.bindPopup%28popup_5d2a0431c52149ffbd0fceae3ea17eef%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_3c28d166a9a24babb28f6c8e640bf6ed%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8970649943808023%2C%2041.64083344974765%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_12db79ad3a8e4c8492dea2b49d9d401c%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_5ed81bd0922149f5b4fff56d2cac8620%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_5ed81bd0922149f5b4fff56d2cac8620%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLIS.%20MARCHA%20ATR%C3%81S%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_12db79ad3a8e4c8492dea2b49d9d401c.setContent%28html_5ed81bd0922149f5b4fff56d2cac8620%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_3c28d166a9a24babb28f6c8e640bf6ed.bindPopup%28popup_12db79ad3a8e4c8492dea2b49d9d401c%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_fd13f139bafb493da0ffb4b515bf2692%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8718525605769747%2C%2041.64904657717317%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_757e4e35dcc442b6996d33b6d0e62c98%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_466adfaaa5f84c2fb9d5d2c8acc863e4%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_466adfaaa5f84c2fb9d5d2c8acc863e4%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20LATERAL%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_757e4e35dcc442b6996d33b6d0e62c98.setContent%28html_466adfaaa5f84c2fb9d5d2c8acc863e4%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_fd13f139bafb493da0ffb4b515bf2692.bindPopup%28popup_757e4e35dcc442b6996d33b6d0e62c98%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_8120f4a198b146cb9004d0be31503819%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8964627561577849%2C%2041.64322365075108%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_7812180906dd49069ca9822295ef9749%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_a80177355e3640edb1b57bcdeb40e9d5%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_a80177355e3640edb1b57bcdeb40e9d5%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3EOTRAS%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_7812180906dd49069ca9822295ef9749.setContent%28html_a80177355e3640edb1b57bcdeb40e9d5%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_8120f4a198b146cb9004d0be31503819.bindPopup%28popup_7812180906dd49069ca9822295ef9749%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_5cde4d6799134c2fb2cc0da2ea05f5f6%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8778095796207178%2C%2041.68753087470739%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_dcbf9c73c0b24a77a151ff5bd48ead68%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_e607e6491d324c5bb92f15c126621ede%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_e607e6491d324c5bb92f15c126621ede%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_dcbf9c73c0b24a77a151ff5bd48ead68.setContent%28html_e607e6491d324c5bb92f15c126621ede%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_5cde4d6799134c2fb2cc0da2ea05f5f6.bindPopup%28popup_dcbf9c73c0b24a77a151ff5bd48ead68%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_a36cd47a42f04186a68df483b9c496f7%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8812157329722801%2C%2041.661646612715046%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_04bed782e1b84ee69f464616463abd01%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_30ede9c05e954735a0f6cee4de691f66%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_30ede9c05e954735a0f6cee4de691f66%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ESALIDA%20CALZADA%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_04bed782e1b84ee69f464616463abd01.setContent%28html_30ede9c05e954735a0f6cee4de691f66%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_a36cd47a42f04186a68df483b9c496f7.bindPopup%28popup_04bed782e1b84ee69f464616463abd01%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_547cf2635e9f47c49ec711ca79c2bf4a%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8762000299022707%2C%2041.6454384961757%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_8e852c28a4464f6fb503f185722631db%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_3fe08c8f697947cf86d93d6b004faec0%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_3fe08c8f697947cf86d93d6b004faec0%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_8e852c28a4464f6fb503f185722631db.setContent%28html_3fe08c8f697947cf86d93d6b004faec0%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_547cf2635e9f47c49ec711ca79c2bf4a.bindPopup%28popup_8e852c28a4464f6fb503f185722631db%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_2850db69ecfd4ef5a7522bae5ba2bff0%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.9089013552408617%2C%2041.65543768899759%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_04fe6a6248c44a9e8755d1fcafaab1d9%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_230ab6d394c947019f7f1c7442785280%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_230ab6d394c947019f7f1c7442785280%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3EATROPELLO%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_04fe6a6248c44a9e8755d1fcafaab1d9.setContent%28html_230ab6d394c947019f7f1c7442785280%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_2850db69ecfd4ef5a7522bae5ba2bff0.bindPopup%28popup_04fe6a6248c44a9e8755d1fcafaab1d9%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_e19a9dabe4ab48628c25b27e560583ee%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.9004729973337304%2C%2041.65180346604993%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_812a3a2a26ba4b089ea5514301241bb7%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_28893bef37a54a0aa636a911aa29e3bb%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_28893bef37a54a0aa636a911aa29e3bb%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_812a3a2a26ba4b089ea5514301241bb7.setContent%28html_28893bef37a54a0aa636a911aa29e3bb%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_e19a9dabe4ab48628c25b27e560583ee.bindPopup%28popup_812a3a2a26ba4b089ea5514301241bb7%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_9fc0cf3c8e0f4ebea7a41573873e34eb%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8917562993466011%2C%2041.65233828238132%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_c4de8323a1b546f4a1c38c61448d1c2c%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_d054531302144ce1aaffd1d0aed33e18%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_d054531302144ce1aaffd1d0aed33e18%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_c4de8323a1b546f4a1c38c61448d1c2c.setContent%28html_d054531302144ce1aaffd1d0aed33e18%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_9fc0cf3c8e0f4ebea7a41573873e34eb.bindPopup%28popup_c4de8323a1b546f4a1c38c61448d1c2c%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_05e8ce5b18fc4ff8910e1da531959689%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.888856043735591%2C%2041.65040494617356%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_ee3ee588890940e888f0c59d63fb36ef%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_6e5499e04cf948e79d939f8a524899d1%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_6e5499e04cf948e79d939f8a524899d1%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_ee3ee588890940e888f0c59d63fb36ef.setContent%28html_6e5499e04cf948e79d939f8a524899d1%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_05e8ce5b18fc4ff8910e1da531959689.bindPopup%28popup_ee3ee588890940e888f0c59d63fb36ef%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_82d69b6f005b41e8b0022c69e61b1f60%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8629911318784169%2C%2041.645335650478316%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_6e380ab3530240d2903625f1a874b263%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_506aaf9de82c404e8a3dced6d680a49e%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_506aaf9de82c404e8a3dced6d680a49e%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_6e380ab3530240d2903625f1a874b263.setContent%28html_506aaf9de82c404e8a3dced6d680a49e%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_82d69b6f005b41e8b0022c69e61b1f60.bindPopup%28popup_6e380ab3530240d2903625f1a874b263%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_34ac0e0fe10e4d29b280350df01b3b6c%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8870207060655807%2C%2041.609992514227066%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_3fbbac6ee94c453fa097945b36a0bb78%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_7b50c4dc792d41e3bf6507e6ce44d49c%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_7b50c4dc792d41e3bf6507e6ce44d49c%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_3fbbac6ee94c453fa097945b36a0bb78.setContent%28html_7b50c4dc792d41e3bf6507e6ce44d49c%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_34ac0e0fe10e4d29b280350df01b3b6c.bindPopup%28popup_3fbbac6ee94c453fa097945b36a0bb78%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_7424ab4e1f5a44eebb932b1b25a0d036%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8818527060979306%2C%2041.649027473051156%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_284626cb97df4caeb0ebe280cc2cc6bc%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_addf8343314c4d3cb40e4afb885f3465%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_addf8343314c4d3cb40e4afb885f3465%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ESALIDA%20CALZADA%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_284626cb97df4caeb0ebe280cc2cc6bc.setContent%28html_addf8343314c4d3cb40e4afb885f3465%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_7424ab4e1f5a44eebb932b1b25a0d036.bindPopup%28popup_284626cb97df4caeb0ebe280cc2cc6bc%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_dbf475c955484c5aa221bea273302480%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8645810716721081%2C%2041.661585829868585%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_a85c24dff19242c9bdd6b6027da5ccc8%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_be1d527f9171466fbd11e311a31c0a5c%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_be1d527f9171466fbd11e311a31c0a5c%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_a85c24dff19242c9bdd6b6027da5ccc8.setContent%28html_be1d527f9171466fbd11e311a31c0a5c%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_dbf475c955484c5aa221bea273302480.bindPopup%28popup_a85c24dff19242c9bdd6b6027da5ccc8%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_b39595ebbc594b54a2b12c0fc6ef8a3f%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.887776415002892%2C%2041.666992622958105%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_2f33e8cb5d284d83b4665a415d0c04c5%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_34fa0380f23944d1a67ce00141749dfd%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_34fa0380f23944d1a67ce00141749dfd%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_2f33e8cb5d284d83b4665a415d0c04c5.setContent%28html_34fa0380f23944d1a67ce00141749dfd%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_b39595ebbc594b54a2b12c0fc6ef8a3f.bindPopup%28popup_2f33e8cb5d284d83b4665a415d0c04c5%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_9f4b390b5b8e47f48d994c6390d758fe%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8825260453930127%2C%2041.62957498750602%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_0c9079fc9031450c8dfe5d4a95c31b13%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_84ace393d28449f496a611e2b921f0e5%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_84ace393d28449f496a611e2b921f0e5%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLIS%20FRONTOLATERAL%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_0c9079fc9031450c8dfe5d4a95c31b13.setContent%28html_84ace393d28449f496a611e2b921f0e5%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_9f4b390b5b8e47f48d994c6390d758fe.bindPopup%28popup_0c9079fc9031450c8dfe5d4a95c31b13%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_c8c54a5d39094323a7da3b5145d88437%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.908314757720389%2C%2041.6562121210704%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_49a7982aa92c4e11963c58591bd56c8c%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_ff0f0d2be26a42dcb93be94237be591d%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_ff0f0d2be26a42dcb93be94237be591d%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ESALIDA%20CALZADA%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_49a7982aa92c4e11963c58591bd56c8c.setContent%28html_ff0f0d2be26a42dcb93be94237be591d%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_c8c54a5d39094323a7da3b5145d88437.bindPopup%28popup_49a7982aa92c4e11963c58591bd56c8c%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_cce406e07e784a25892cf35c730f1dbb%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8691088511672924%2C%2041.65949772773082%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_3d21c00a5b5546769665f5142e3202a1%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_c74fca5e372a4625941fc9d9ccbdca91%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_c74fca5e372a4625941fc9d9ccbdca91%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3EOTRAS%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_3d21c00a5b5546769665f5142e3202a1.setContent%28html_c74fca5e372a4625941fc9d9ccbdca91%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_cce406e07e784a25892cf35c730f1dbb.bindPopup%28popup_3d21c00a5b5546769665f5142e3202a1%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_f9c3a6a6c1ae473c8e2606fd9a56dd1a%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8880337913721866%2C%2041.633353667694024%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_7dd5b036a6904fa2ac752aa08c8cc213%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_f33c9e1a1bbf4ce8b383c415b81aaabe%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_f33c9e1a1bbf4ce8b383c415b81aaabe%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3EATROPELLO%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_7dd5b036a6904fa2ac752aa08c8cc213.setContent%28html_f33c9e1a1bbf4ce8b383c415b81aaabe%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_f9c3a6a6c1ae473c8e2606fd9a56dd1a.bindPopup%28popup_7dd5b036a6904fa2ac752aa08c8cc213%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_b915143ae3d44661888e4a0964d3ba8b%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8708838775078237%2C%2041.6390382112928%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_9247887c67914495a5cbcdc96e168c01%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_0a17158d962f4bd8a0f82da4c81ff866%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_0a17158d962f4bd8a0f82da4c81ff866%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECAIDA%20SOBRE%20CALZADA%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_9247887c67914495a5cbcdc96e168c01.setContent%28html_0a17158d962f4bd8a0f82da4c81ff866%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_b915143ae3d44661888e4a0964d3ba8b.bindPopup%28popup_9247887c67914495a5cbcdc96e168c01%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_f588631c9ef846d692f347553ebe3eab%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8970649943808023%2C%2041.64083344974765%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_2c1e8970262d47b9b0b74d23765118c7%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_60f5e4f78e8545238b50205f5a3be515%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_60f5e4f78e8545238b50205f5a3be515%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLIS.%20MARCHA%20ATR%C3%81S%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_2c1e8970262d47b9b0b74d23765118c7.setContent%28html_60f5e4f78e8545238b50205f5a3be515%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_f588631c9ef846d692f347553ebe3eab.bindPopup%28popup_2c1e8970262d47b9b0b74d23765118c7%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_a73fbd1188fe4ed6b0eebf2cae092cf6%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8718525605769747%2C%2041.64904657717317%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_eaa910b52b804372bd33f7f31a35cdc6%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_41765dbd3d8b47a0b73316e6fdb927e9%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_41765dbd3d8b47a0b73316e6fdb927e9%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20LATERAL%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_eaa910b52b804372bd33f7f31a35cdc6.setContent%28html_41765dbd3d8b47a0b73316e6fdb927e9%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_a73fbd1188fe4ed6b0eebf2cae092cf6.bindPopup%28popup_eaa910b52b804372bd33f7f31a35cdc6%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_d806add28d47459385d9b9929a1555e0%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8964627561577849%2C%2041.64322365075108%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_74c0f224d6a3456d886634acd482fc98%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_0acd93f357d048e0bc710e44abc076cf%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_0acd93f357d048e0bc710e44abc076cf%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3EOTRAS%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_74c0f224d6a3456d886634acd482fc98.setContent%28html_0acd93f357d048e0bc710e44abc076cf%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_d806add28d47459385d9b9929a1555e0.bindPopup%28popup_74c0f224d6a3456d886634acd482fc98%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_d2e6e5299bda4482a761c7eb9e95a3e9%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8778095796207178%2C%2041.68753087470739%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_22b5c30cf7064d0e8f02387a8fb25a6c%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_9c4aa20296ef4c00bcda6fed5a2696ae%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_9c4aa20296ef4c00bcda6fed5a2696ae%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_22b5c30cf7064d0e8f02387a8fb25a6c.setContent%28html_9c4aa20296ef4c00bcda6fed5a2696ae%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_d2e6e5299bda4482a761c7eb9e95a3e9.bindPopup%28popup_22b5c30cf7064d0e8f02387a8fb25a6c%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_c80870b753ae44a5a297de98f3f55a23%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8812157329722801%2C%2041.661646612715046%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_d29b8baa951a464492341891b5f6785e%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_ae305dd9d9bb457b8a68f6321d3ae9ba%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_ae305dd9d9bb457b8a68f6321d3ae9ba%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ESALIDA%20CALZADA%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_d29b8baa951a464492341891b5f6785e.setContent%28html_ae305dd9d9bb457b8a68f6321d3ae9ba%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_c80870b753ae44a5a297de98f3f55a23.bindPopup%28popup_d29b8baa951a464492341891b5f6785e%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_f61e851b733748809cf0ccfc45d4f133%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8762000299022707%2C%2041.6454384961757%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_86a8f5c135a84814b4868d31e66e0321%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_8b28785f9aec4e56a2649948d7bf7273%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_8b28785f9aec4e56a2649948d7bf7273%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_86a8f5c135a84814b4868d31e66e0321.setContent%28html_8b28785f9aec4e56a2649948d7bf7273%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_f61e851b733748809cf0ccfc45d4f133.bindPopup%28popup_86a8f5c135a84814b4868d31e66e0321%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_cf326bec9c07404bbb327b2d99f42f38%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.9089013552408617%2C%2041.65543768899759%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_ddee52a1eb614e9993f211ce443a1733%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_0e87c82d290d4db4a898dd1dcf39ddba%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_0e87c82d290d4db4a898dd1dcf39ddba%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3EATROPELLO%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_ddee52a1eb614e9993f211ce443a1733.setContent%28html_0e87c82d290d4db4a898dd1dcf39ddba%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_cf326bec9c07404bbb327b2d99f42f38.bindPopup%28popup_ddee52a1eb614e9993f211ce443a1733%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_04aaa227e919489f9a3666a96cbb1cf3%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.9004729973337304%2C%2041.65180346604993%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_6b0507ee59064135950b086d01af3b44%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_e8970ad363e3422387af14690a29b875%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_e8970ad363e3422387af14690a29b875%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_6b0507ee59064135950b086d01af3b44.setContent%28html_e8970ad363e3422387af14690a29b875%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_04aaa227e919489f9a3666a96cbb1cf3.bindPopup%28popup_6b0507ee59064135950b086d01af3b44%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_0a28fc3466a94e57aae2862aa9335190%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8917562993466011%2C%2041.65233828238132%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_c975d1f45fea4dfc8de798f46ee29578%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_c7540f7dc9e74c369b7d30db04eb9fd5%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_c7540f7dc9e74c369b7d30db04eb9fd5%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_c975d1f45fea4dfc8de798f46ee29578.setContent%28html_c7540f7dc9e74c369b7d30db04eb9fd5%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_0a28fc3466a94e57aae2862aa9335190.bindPopup%28popup_c975d1f45fea4dfc8de798f46ee29578%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_1e55290ab329459d800098fd0a51c411%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.888856043735591%2C%2041.65040494617356%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_a90c8399d41240f5a31dc763763ca4ba%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_b23e9dd4b0dd4240a43895a9b0ac11fa%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_b23e9dd4b0dd4240a43895a9b0ac11fa%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_a90c8399d41240f5a31dc763763ca4ba.setContent%28html_b23e9dd4b0dd4240a43895a9b0ac11fa%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_1e55290ab329459d800098fd0a51c411.bindPopup%28popup_a90c8399d41240f5a31dc763763ca4ba%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_16a51000ba734fb7a6bd4805540b191c%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8629911318784169%2C%2041.645335650478316%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_7a6aec3844a2427c970b650dc75649a3%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_a7a83b4ed68a4a628e089819fe5a2de1%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_a7a83b4ed68a4a628e089819fe5a2de1%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_7a6aec3844a2427c970b650dc75649a3.setContent%28html_a7a83b4ed68a4a628e089819fe5a2de1%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_16a51000ba734fb7a6bd4805540b191c.bindPopup%28popup_7a6aec3844a2427c970b650dc75649a3%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_8ba290accfb14ca78029ab50ab05278c%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8870207060655807%2C%2041.609992514227066%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a113325c206e4c5e9cc0b298a04453e1%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_19e6f408d070470a8db8eace09ec7899%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_4e0c9010cfec453085a8eee0b51089fe%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_4e0c9010cfec453085a8eee0b51089fe%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_19e6f408d070470a8db8eace09ec7899.setContent%28html_4e0c9010cfec453085a8eee0b51089fe%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_8ba290accfb14ca78029ab50ab05278c.bindPopup%28popup_19e6f408d070470a8db8eace09ec7899%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%3C/script%3E onload="this.contentDocument.open();this.contentDocument.write(    decodeURIComponent(this.getAttribute('data-html')));this.contentDocument.close();" allowfullscreen webkitallowfullscreen mozallowfullscreen></iframe></div></div>




```python

```
