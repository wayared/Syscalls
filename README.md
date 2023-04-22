
# Theory
## Remember use this commands to view the documentation "man 2 open" "man 2 write" "man 2 lseek" "man 2 read" "man 2 close"

Una aplicación notifica al kernel que tiene la intención de
acceder a un archivo con la llamada de sistema open.

int open(char *filename, int flags, mode_t mode);

open usa bitmasks para configurar los modos de acceso a
los archivos.

O_RDONLY: solo lectura
O_WRONLY: solo escritura
O_RDWR: lectura y escritura
O_CREAT: si el archivo no existe, crea uno nuevo
O_TRUNC: si el archivo existe, lo trunca
O_APPEND: antes de cada escritura, mueve el puntero de
posición al final.

El tercer argumento en open utiliza bitmasks para
especificar los permisos de acceso de un archivo nuevo.

S_IRUSR: usuario dueño puede leer archivo
S_IWUSR: usuario dueño puede escribir archivo
S_IXUSR: usuario dueño puede ejecutar archivo
S_IRGRP: grupo dueño puede leer archivo

open("foo.txt", O_WRONLY | O_CREAT, S_IRUSR | S_IWUSR);

Cuando una aplicación no va a acceder más a un archivo
debe notificar al kernel con la llamada de sistema close.

int close(int fd);

Las llamadas read y write copian n bytes entre memoria y
el archivo (o viceversa) retornando el número de bytes
copiados.

include <unistd.h>

Retorna: número de bytes leidos, 0 si EOF, -1 si hubo error 
ssize_t read(int fd, void *buf, size_t n);
 Retorna: número de bytes escritos, -1 si hubo error 
ssize_t write(int fd, const void *buf, size_t n);

lseek reposiciona el puntero de posición de archivo.
off_t lseek(int fd, off_t offset, int whence);



