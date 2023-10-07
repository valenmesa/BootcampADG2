# BootcampADG2
- Google Slides
- Descripción del proyecto.
- Queries, scripts de Python y otros recursos empleados.
  
# [Scripts de Python](https://github.com/valenmesa/BootcampADG2/blob/main/Limpieza_Datos.ipynb)


* Importar libreria requerida  <br>
import pandas as pd <br>
import matplotlib.pyplot as plt <br>
import seaborn as sns <br>
import numpy as np <br>

* Leer datos desde archivo CSV <br>
csv_path = "https://docs.google.com/spreadsheets/d/e/2PACX-1vSN0fumSGBSA38-eFMqdcWvUsdJHEstjyAGRbqp5ncsU8LCL7y9oL4caapxkhk5mqOZheFpOmJAhSRx/pub?gid=438317318&single=true&output=csv" <br>
* Definir una lista llamada "missing_values" <br>
missing_values = ["?","—"] <br>
df = pd.read_csv(csv_path, sep=",", na_values = missing_values) <br>

* Verificar número de filas <br>
num_filas = df.shape[0] <br>
print("Número de filas:", num_filas) <br>

* Imprimir las primeras cinco filas de un dataframe para probar que todo ok <br>
df.head() <br>

* Renombrar las columnas <br>
new_col = { <br>
    'City':'Ciudad', <br>
    'Country':'Pais', <br>
    'Venue':'Lugar', <br>
    'Opening act(s)':'Acto_apertura', <br>
    'Attendance (tickets sold / available)':'Entradas_vendidas/disponibles', <br>
    'Revenue':'Ingresos', <br>
    'Tour':'Tour'} <br>
df = df.rename(columns=new_col) <br>

* Imprimiendo la cantidad de valores nulos en cada columna del DataFrame df <br>
print(df.isnull().sum()) <br>

* Eliminar todas las filas que contienen valores nulos <br>
df = df.dropna() <br>

* Imprimiendo la cantidad de valores nulos en cada columna del DataFrame df <br>
print(df.isnull().sum()) <br>

* Reemplazar lo caracteres especiales en las cadenas de texto <br>
df["Tour"] = df["Tour"].str.replace("_"," ") <br>
df["Acto_apertura"] = df["Acto_apertura"].str.replace("\n"," - ") <br>

* Imprimir las primeras cinco filas de un dataframe para probar que todo ok <br>
df.head() <br>

* Pasar las cadenas de texto a minuscula <br>
df["Acto_apertura"] = df["Acto_apertura"].str.lower() <br>
df["Ciudad"] = df["Ciudad"].str.lower() <br>
df["Pais"] = df["Pais"].str.lower() <br>
df["Lugar"] = df["Lugar"].str.lower() <br>
df["Tour"] = df["Tour"].str.lower() <br>

* Imprimir las primeras cinco filas de un dataframe para probar que todo ok <br>
df.head() <br>

* Eliminar los espacios en blanco al principio y al final de cada valor en la columna <br>
df["Acto_apertura"] = df["Acto_apertura"].apply(lambda x: x.strip()) <br>
df["Ciudad"] = df["Ciudad"].apply(lambda x: x.strip()) <br>
df["Pais"] = df["Pais"].apply(lambda x: x.strip()) <br>
df["Lugar"] = df["Lugar"].apply(lambda x: x.strip()) <br>
df["Tour"] = df["Tour"].apply(lambda x: x.strip()) <br>

* Dividir la columna Entradas_vendidas/disponibles en Entradas_vendidas y Entradas_disponibles <br>
df[['Entradas_vendidas', 'Entradas_disponibles']] = df['Entradas_vendidas/disponibles'].str.split('/', expand=True)  <br>

* Eliminar la columna Entradas_vendidas/disponibles <br>
df = df.drop("Entradas_vendidas/disponibles",axis=1) <br>

* Imprimir las primeras cinco filas de un dataframe para probar que todo ok <br>
df.head() <br>

* Quitar caracteres especiales a la columna Ingresos, Entradas_vendidas y Entradas_available <br>
df["Ingresos"] = df["Ingresos"].str.replace('$','').str.replace(',','') <br>
df["Entradas_vendidas"] = df["Entradas_vendidas"].str.replace(",","") <br>
df["Entradas_disponibles"] = df["Entradas_disponibles"].str.replace(",","") <br>

* Imprimir las primeras cinco filas de un dataframe para probar que todo ok <br>
df.head() <br>

* Verificar numero de filas <br>
num_filas = df.shape[0] <br>
print("Número de filas:", num_filas) <br>

* Borrar duplicados con columna clave <br>
columnas_clave = ['Ciudad', 'Pais', 'Lugar', 'Tour'] <br>
df = df.drop_duplicates(subset=columnas_clave) <br>

* Verificar numero de filas <br>
num_filas = df.shape[0] <br>
print("Número de filas:", num_filas) <br>

* Generamos una tabla con el tipo de dato de cada columna <br>
df.dtypes <br>

* Cambiar los datos a tipo numerico <br>
df["Ingresos"] = pd.to_numeric(df["Ingresos"],errors='coerce') <br>
df["Entradas_vendidas"] = pd.to_numeric(df["Entradas_vendidas"],errors='coerce') <br>
df["Entradas_disponibles"] = pd.to_numeric(df["Entradas_disponibles"],errors='coerce') <br>
df.dtypes <br>

* Descargamos nuestro dataset  <br>
df.to_csv('Tours_Taylor.csv', index=False) <br>

- Enlace o referencia al dataset elegido.
- Documentación del desarrollo de su proyecto (tecnologías utilizadas y cualquier información relevante), aprendizajes obtenidos y futuras oportunidades de investigación. 
