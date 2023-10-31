**Instrucciones tarea1:**

1. **Consulta el Archivo de Referencia:**
   - El alumnado deberá consultar el archivo *Manual_de_comandos_ubunthu.pdf*.

2. **Identifica la Combinación de Cifras:**
   - Según la fecha de nacimiento de cada estudiante, identificarán una combinación específica de cifras.

3. **Modificación del Archivo "1.md":**
   - En el archivo PDF, cada cifra corresponde a un punto específico. Por ejemplo, si la combinación es "14", deberás añadir al archivo *1.md* los puntos correspondientes a "1" y "4" desde el archivo PDF.

4. **Evaluación de Habilidades:**
   - Esta tarea evaluará la habilidad de los estudiantes para clonar un repositorio a través de fork en GitHub, así como para crear y modificar archivos.

# Hola Andrei, he nacido el 29/04, te he puesto el punto 2 y el 9.5 (porque no hay 9) :smile:


2. NOCIONES BÁSICAS
En una terminal:

Las aplicaciones con nombres compuestos se escriben con guión entre las palabras
(ej. compizconfig-settings-manager).

Para los nombres de archivos y directorios que contienen espacios en blanco hay que envolverlos en
comillas dobles (ej. "nombre archivo") o simples (ej. 'nombre archivo').
Un consejo: Para no haceros un lío, nunca uséis espacios en blanco en los nombres de carpetas y archivos y
sustituirlo por un guión bajo (mis_imágenes) o un guión medio (mis-imágenes)

Los espacios en blanco se utilizan únicamente para separar ordenes (ej. para instalar varios
paquetes: sudo apt-get install avidemux k3b kde-i18n-es k3b-i18n, vemos que dichos
paquetes están separados por espacios en blanco entre ellos).

La ruta "/home/tu_usuario" se puede cambiar por el símbolo "~" (para escribirlo, pulsar la
combinación de teclas Alt Gr + Ñ ), que viene a sustituirlo en la línea de ordenes, sea cual sea el nombre del
usuario
Cuando tecleamos una orden, el intérprete de comandos sigue una serie de pasos:
1. Busca el nombre de la orden y comprueba si es una orden interna.
2. Comprueba si la orden es un alias, es decir, un nombre sustitutorio de otra orden.
3. Si no se cumple ninguno de los casos anteriores, busca el programa correspondiente y lo ejecuta.
4. Si el intérprete de comandos no puede encontrar la orden que hemos tecleado, muestra un mensaje de error.
El formato general de una orden en Linux es:
comando [-opciones] [argumentos]
A la hora de introducir los comandos hay que tener en cuenta las siguientes características:
• Los comandos hay que teclearlos exactamente.
• Las letras mayúsculas y minúsculas se consideran como diferentes.• En su forma más habitual, el sistema operativo utiliza un signo de $ como prompt para indicar que está
preparado para aceptar comandos, aunque este carácter puede ser fácilmente sustituido por otro u otros
elegidos por el usuario. En el caso de que el usuario acceda como administrador este signo se sustituye por #.
• Cuando sea necesario introducir el nombre de un fichero o directorio como argumento a un comando, Linux,
permite escribir las primeras letras del mismo y realiza un autorrellenado al presionar la tecla del tabulador. Si
no puede distinguir entre diversos casos rellenará hasta el punto en el que se diferencien.
La Terminal guarda un HISTORIAL y podéis ver cómo funciona en:
http://ubuntu-guia.blogspot.com/2010/08/historial-terminal-consola-ubuntu.html



9.5. Agrupación y compresión de ficheros: Comandos tar y gzip/gunzip
Tanto el comando tar como gzip son ampliamente empleados para la difusión de programas
y ficheros en Linux.
tar Este comando agrupa varios ficheros en uno solo o ―archivo‖, mientras que el segundoos comprime. En conjunto estos dos programas actúan de forma muy similar a programas
como Winzip. Su sintaxis es:
tar [opciones][ficheros]
El modo en el que se escriben las opciones de tar es un poco especial. El guión inicial, por
ejemplo, no es necesario.
Las opciones más comunes para tar son:
-c creación de archivadores nuevos.
-x extracción de archivos de un archivador existente.
-v muestra los archivos mientras se agregan o se extraen.
-t muestra el contenido de un archivo tar.
-f el siguiente argumento es el archivador a crear, del que queremos extraer archivos o
mostrar un listado.
Para crear un nuevo archivo se emplea:
tar –cvf nombre_archivo.tar fichero1 fichero2 ...
donde fichero1, fichero2 etc. son los ficheros que se van a añadir al archivo tar. Si se desea
extraer los ficheros se emplea:
tar –xpvf nombre_archivo.tar fichero1 ...
Veamos algunos ejemplos:
# tar cvf escritorio.tar Desktop
empaqueta el contenido de Desktop en un archivador nuevo escritorio.tar
#tar xvf escritorio.tar Desktop/Floppy.desktop
extrae del archivo escritorio.tar el fichero indicado
#tar xvf escritorio.tar
extrae todo el contenido del archivo escritorio.tar
#tar tvf escritorio.tar
muestra un listado largo del contenido del archivo escritorio.tar
Hay que tener en cuenta, a la hora de extraer el contenido de un archivador (al fichero tar
resultante se le suele llamar así), si el archivador se creó conservando el nombre del
directorio de origen. Es posible que se sobrescriba el contenido de los ficheros originales.
Ejemplo: Nos situamos en el directorio raíz como root. Si archivamos los ficheros /
etc/group y /etc/passwd:
#tar cvf backup.tar /etc/group /etc/passwdestamos conservando los nombres del directorio al que pertenecen. Por lo tanto, para
extraer estos ficheros nos tendremos que situar en el directorio raíz:
#cd /
#tar xvf backup.tar /etc/group /etc/passwd
Sin embargo, si archivamos los ficheros group y passwd estando en /etc:
#tar cvf /backup.tar group passwd
no guardamos la ruta, por lo que para extraer los ficheros tendremos que situarnos en ella:
#cd /
#cd /etc
#tar xvf /backup.tar group passwd
gzip/gunzip Al contrario que tar que agrupa varios ficheros en uno, gzip comprime un
único fichero con lo que la información se mantiene pero se reduce el tamaño del mismo.
El uso de gzip es muy sencillo:
gzip [opciones] fichero
con lo que se comprime fichero (que es borrado) y se crea un fichero con nombre
fichero.gz.
La opción más común es:
-1 a –9 grado de compresión, mínimo y máximo respectivamente.
-d descomprimir el fichero .gz
Si lo que se desea es descomprimir un fichero se emplea entonces:
gzip –d fichero.gz
recuperando el fichero inicial.
Otra posibilidad sería utilizar el comando gunzip para la descompresión, de la siguiente
forma:
gunzip fichero.gz
Como se ha comentado al principio es típico emplear tar y gzip de forma consecutiva, para
obtener ficheros con extensión tar.gz o tgz que contienen varios ficheros de forma
comprimida (similar a un fichero zip). El comando tar incluye la opción z para estos
ficheros de forma que para extraer los ficheros que contiene:
tar –zxf fichero.tar.gz