# Reto número 12 repo
### Fecha:  01-11-2023
  
**1.** Consulte que hacen los siguientes métodos de strings en python: endswith, startswith, isalpha, isalnum, isdigit, isspace, istitle, islower, isupper.

| | Nombre del método | Estructura general | Uso |
|-|-------------------|--------------------|-----|
|1.|endswith|endswith(suffix[, start[, end]])| Este método verifica si la cadena termina con el sufijo especificado. Puedes proporcionar opcionalmente los argumentos start y end para limitar la búsqueda dentro de la cadena.|
|2.|startswith|startswith(prefix[, start[, end]])|Comprueba si la cadena comienza con el prefijo dado. Al igual que endswith, puedes especificar los argumentos opcionales start y end para restringir la búsqueda.|
|3.|isalpha|isalpha()|Devuelve True si todos los caracteres de la cadena son letras (alfabéticas) y la cadena no está vacía. De lo contrario, devuelve False.|
|4.|isalnum|isalnum()|Devuelve True si todos los caracteres de la cadena son letras (alfabéticas) o dígitos (numéricos) y la cadena no está vacía. De lo contrario, devuelve False.|
|5.|isdigit|isdigit()|Retorna True si todos los caracteres de la cadena son dígitos numéricos y la cadena no está vacía. En caso contrario, devuelve False.|
|6.|isspace|isspace()|Comprueba si la cadena contiene solo caracteres de espacio en blanco (espacios, tabuladores, saltos de línea, etc.). Retorna True si es así y False en caso contrario.|
|7.|istitle|istitle()|Comprueba si la cadena es un título, es decir, si la primera letra de cada palabra en la cadena está en mayúscula y las demás en minúscula. Devuelve True si la cadena sigue este formato y False en caso contrario.|
|8.|islower|islower()|Verifica si todos los caracteres de la cadena están en minúscula. Retorna True si todos los caracteres son minúsculas y la cadena no está vacía, de lo contrario, retorna False.|
|9.|isupper|isupper()|Comprueba si todos los caracteres de la cadena están en mayúscula. Retorna True si todos los caracteres son mayúsculas y la cadena no está vacía, de lo contrario, retorna False.|

**2.** Procesar el archivo y extraer: Cantidad de vocales, cantidad de consonantes, listado de las 50 palabras que más se repiten.
* Primero importe de counter para hallar el top de 50 palabras que más se repiten para contarlas. En la primera función se establecen en 0 los dos contadores de vocales y consonantes, se usa un for donde se va tomando cada letra del documento, usando lower() la ponemos en mínuscula para que en el siguiente condicional solo sea necesario colocar las vocales y consonantes en minúscula, si es vocal se suma 1 al contador de las vocales y si es consonante se le suma al contador de consontantes. Al final la función imprime los contadores de cada uno. La segunda función es para hallar las 50 más repetidas, primero usando split se separan las palabras, después, usando counter cuenta la cantidad de esa palabra que hay en el documento y usando most common filtramos solamante en nuestra lista las 50 que más se repetieron. La función imprime las 50 palabras que más se repetieron. En la función main, se importa el archivo, se lee el archivo y se llaman las dos funciones.
* Mirar archivo Punto_2.py
```pseudocode
from collections import Counter

def VocalesYConsonantes(doc_ok):
    c_vocales = 0 
    c_consonantes = 0 

    for letra in doc_ok:                                                       # Va mirando cada letra del archivo
      letra_min=letra.lower()                                                  # Para convertirlas todas a minuscula y hacer solo un condicional
      if letra_min in "aeiouáéíóú":                                            # Busca si es vocal
        c_vocales += 1                                                         
      elif letra_min in "bcdfghjklmnñpqrstvwxyz":                              # Busca si es consonante
        c_consonantes += 1 

    print("El número de vocales es: " +str(c_vocales)) 
    print("El número de consonantes es: " +str(c_consonantes)) 

def PalabrasMasRepetidas(doc_ok):
    doc_ok = doc_ok.split()                                                    # Para seprar las palabras
    p_repetidas = Counter(doc_ok).most_common(50)                              # Las que más aparecen se añaden a la variable con el top 50
    print("Las 50 palabras que más se repiten son: " + str(p_repetidas))

if __name__ == "__main__":
  with open("mbox-short.txt", "r") as doc:                                     # Para importar el archivo
    doc_ok = doc.read()                                                        # Lee el archivo
  VocalesYConsonantes(doc_ok)                                                  # Se llama la función para hallar número de vocales y consonantes
  PalabrasMasRepetidas(doc_ok)                                                 # Se llama la función para hallar las 50 palabras más repetidas
```
