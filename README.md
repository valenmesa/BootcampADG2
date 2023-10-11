# Proyecto final Ingresos de los tours de Taylor Switf
- Google Slides
- Descripción del proyecto.
- Queries, scripts de Python y otros recursos empleados.
  
# [Scripts de Python](https://github.com/valenmesa/BootcampADG2/blob/main/Limpieza_Datos.ipynb)


* Importar libreria requerida  <br>
```import pandas as pd 
import matplotlib.pyplot as plt
import seaborn as sns 
import numpy as np 
```
* Leer datos desde archivo CSV <br>
```
csv_path = "https://docs.google.com/spreadsheets/d/e/2PACX-1vSN0fumSGBSA38-eFMqdcWvUsdJHEstjyAGRbqp5ncsU8LCL7y9oL4caapxkhk5mqOZheFpOmJAhSRx/pub?gid=438317318&single=true&output=csv" 
```
* Definir una lista llamada "missing_values" <br>
```
missing_values = ["?","—"] 
df = pd.read_csv(csv_path, sep=",", na_values = missing_values) 
```
* Verificar número de filas <br>
```
num_filas = df.shape[0] 
print("Número de filas:", num_filas) 
```
* Imprimir las primeras cinco filas de un dataframe para probar que todo ok <br>
```
df.head() 
```
* Renombrar las columnas <br>
```
new_col = { 
    'City':'Ciudad', 
    'Country':'Pais', 
    'Venue':'Lugar', 
    'Opening act(s)':'Acto_apertura', 
    'Attendance (tickets sold / available)':'Entradas_vendidas/disponibles', 
    'Revenue':'Ingresos', 
    'Tour':'Tour'} 
df = df.rename(columns=new_col) 
```
* Imprimiendo la cantidad de valores nulos en cada columna del DataFrame df <br>
```
print(df.isnull().sum()) 
```
* Eliminar todas las filas que contienen valores nulos <br>
```
df = df.dropna() 
```
* Imprimiendo la cantidad de valores nulos en cada columna del DataFrame df <br>
```
print(df.isnull().sum()) 
```
* Reemplazar lo caracteres especiales en las cadenas de texto <br>
```
df["Tour"] = df["Tour"].str.replace("_"," ") 
df["Acto_apertura"] = df["Acto_apertura"].str.replace("\n"," - ") 
```
* Imprimir las primeras cinco filas de un dataframe para probar que todo ok <br>
```
df.head() 
```
* Pasar las cadenas de texto a minuscula <br>
```
df["Acto_apertura"] = df["Acto_apertura"].str.lower() 
df["Ciudad"] = df["Ciudad"].str.lower() 
df["Pais"] = df["Pais"].str.lower() 
df["Lugar"] = df["Lugar"].str.lower() 
df["Tour"] = df["Tour"].str.lower() 
```
* Imprimir las primeras cinco filas de un dataframe para probar que todo ok <br>
```
df.head() 
```
* Eliminar los espacios en blanco al principio y al final de cada valor en la columna <br>
```
df["Acto_apertura"] = df["Acto_apertura"].apply(lambda x: x.strip()) 
df["Ciudad"] = df["Ciudad"].apply(lambda x: x.strip()) 
df["Pais"] = df["Pais"].apply(lambda x: x.strip()) 
df["Lugar"] = df["Lugar"].apply(lambda x: x.strip()) 
df["Tour"] = df["Tour"].apply(lambda x: x.strip()) 
```
* Dividir la columna Entradas_vendidas/disponibles en Entradas_vendidas y Entradas_disponibles <br>
```
df[['Entradas_vendidas', 'Entradas_disponibles']] = df['Entradas_vendidas/disponibles'].str.split('/', expand=True)  
```
* Eliminar la columna Entradas_vendidas/disponibles <br>
```
df = df.drop("Entradas_vendidas/disponibles",axis=1) 
```
* Imprimir las primeras cinco filas de un dataframe para probar que todo ok <br>
```
df.head() 
```
* Quitar caracteres especiales a la columna Ingresos, Entradas_vendidas y Entradas_available <br>
```
df["Ingresos"] = df["Ingresos"].str.replace('$','').str.replace(',','')
df["Entradas_vendidas"] = df["Entradas_vendidas"].str.replace(",","")
df["Entradas_disponibles"] = df["Entradas_disponibles"].str.replace(",","")
```
* Imprimir las primeras cinco filas de un dataframe para probar que todo ok
```
df.head() 
```
* Verificar numero de filas <br>
```
num_filas = df.shape[0] 
print("Número de filas:", num_filas) 
```
* Borrar duplicados con columna clave <br>
```
columnas_clave = ['Ciudad', 'Pais', 'Lugar', 'Tour'] 
df = df.drop_duplicates(subset=columnas_clave) 
```
* Verificar numero de filas <br>
```
num_filas = df.shape[0] 
print("Número de filas:", num_filas) 
```
* Generamos una tabla con el tipo de dato de cada columna <br>
```
df.dtypes 
```
* Cambiar los datos a tipo numerico <br>
```
df["Ingresos"] = pd.to_numeric(df["Ingresos"],errors='coerce') 
df["Entradas_vendidas"] = pd.to_numeric(df["Entradas_vendidas"],errors='coerce') 
df["Entradas_disponibles"] = pd.to_numeric(df["Entradas_disponibles"],errors='coerce') 
df.dtypes 
```
* Descargamos nuestro dataset  <br>
```
df.to_csv('Tours_Taylor.csv', index=False) 
```
- Enlace o referencia al dataset elegido.
- Documentación del desarrollo de su proyecto (tecnologías utilizadas y cualquier información relevante), aprendizajes obtenidos y futuras oportunidades de investigación. 
