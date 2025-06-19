# Automatizacion-backup
Automatice la copia de seguridad con Python

![image](https://github.com/user-attachments/assets/a0ffac3d-da0c-47eb-add4-1efeffe93106)

En este artículo, vamos a ver cómo automatizar la copia de seguridad con un script de Python.

Las copias de seguridad de archivos son esenciales para preservar sus datos en el almacenamiento local. Usaremos los módulos shutil, os y sys. En este caso, el módulo shutil se utiliza para copiar datos de un archivo a otro, mientras que los módulos os y sys se utilizan para obtener la ruta del directorio, etc.

Implementación escalonada:
Paso 1: Importe los siguientes módulos:


import shutil
from datetime import date
import os
import sys



Paso 2: Obtengamos ahora la fecha de hoy usando el módulo datetime.


today = date.today()
date_format = today.strftime("%d_%b_%Y_")


Paso 3: Si el usuario especifica la ruta de acceso al archivo de origen, utilice la línea siguiente para concatenar la ruta de acceso al archivo de origen con el nombre del archivo de origen.


src_dir = src_dir+src_file_name
Si no es así, y el archivo se almacena en el mismo directorio que el script de Python actual, utilice el módulo os para determinar la ruta actual del archivo y cree el directorio de origen combinando la ruta proporcionada por el módulo os con el nombre del archivo de origen.


os.chdir(sys.path[0])


Paso 4: Si el usuario no especifica el nombre del archivo de origen, debemos devolver un error de archivo no existe.


if not src_file_name:
   print("Please give atleast the Source File Name")

   
Paso 5: Ahora, use los siguientes casos para probar las condiciones necesarias.

Si el usuario proporciona todas las entradas, como el nombre del archivo de origen, la ruta del archivo de origen, el nombre del archivo de destino y la ruta del archivo de destino.


if src_file_name and dst_file_name and src_dir and dst_dir:
     src_dir = src_dir+src_file_name
     dst_dir = dst_dir+dst_file_name
Si el nombre del archivo de destino es Ninguno, lo que indica que el usuario no especificó un nombre de archivo de destino, utilice las condiciones que se indican a continuación.


elif dst_file_name is None or not dst_file_name:
       dst_file_name = src_file_name
       dst_dir = dst_dir+date_format+dst_file_name
Si un usuario introduce una cadena vacía con uno o más espacios.


elif dst_file_name.isspace():
      dst_file_name = src_file_name
      dst_dir = dst_dir+date_format+dst_file_name
Si el usuario introduce el nombre de la copia de seguridad, simplemente concatene el directorio de destino, la fecha y el nombre del archivo de destino para crear el nombre del archivo de salida.


else:
      dst_dir = dst_dir+date_format+dst_file_name

      
Paso 6: Finalmente, simplemente necesitamos usar la función shutil para copiar el archivo al destino.


shutil.copy2(src_dir, dst_dir)
Nota: Si queremos hacer una copia de seguridad de toda la carpeta en lugar de archivos individuales, debemos usar el código a continuación.

shutil.copytree(src_file_name, dst_dir)





