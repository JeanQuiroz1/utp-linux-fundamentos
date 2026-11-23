# Fundamentos de Linux

**Autor de esta documentación:** Jean Alexis Quiroz Casas. Universidad Tecnológica de Panamá.

Este repositorio documenta operaciones iniciales de la terminal Linux: navegar, crear directorios, copiar y mover archivos, leer su contenido y consultar el sistema. Está relacionado con el Laboratorio 2 de Gestión de Sistemas Operativos II.

## Alcance y estado

El procedimiento está preparado para reproducirse en una carpeta de práctica de una cuenta sin privilegios administrativos. No se adjuntan aquí capturas nuevas ni se afirma que estos comandos se hayan ejecutado durante la preparación de este repositorio.

## Entorno y organización

Se necesita una distribución Linux y una terminal Bash. Puede usarse una máquina virtual. Para esta práctica local no se requiere topología de red: usuario → terminal → carpeta de trabajo. No deben utilizarse carpetas del sistema ni archivos personales como material de prueba.

## Procedimiento

### 1 Navegación

```bash
pwd
ls
mkdir -p "$HOME/practica_linux_utp"
cd "$HOME/practica_linux_utp"
```

`pwd` muestra la ubicación actual, `ls` lista el contenido y `cd` cambia de directorio. Los pasos siguientes se realizan dentro de `practica_linux_utp`. Si ya existe material de otra práctica, usar una carpeta nueva.

### 2 Creación y eliminación controlada

```bash
mkdir prueba_lab
cd prueba_lab
touch archivo1.txt archivo2.txt
ls -l
rm -i archivo2.txt
rm -i archivo1.txt
cd ..
rmdir prueba_lab
```

`rmdir` solo elimina carpetas vacías. Por eso es necesario retirar ambos archivos antes de borrar `prueba_lab`. La opción `-i` solicita confirmación al eliminar cada archivo.

### 3 Copiar mover y renombrar

```bash
touch nota.txt
cp -i nota.txt nota_copia.txt
mv -i nota_copia.txt nota_final.txt
mkdir backup
mv -i nota_final.txt backup/
ls -l backup
```

La copia conserva el archivo de origen. `mv` cambia el nombre o mueve el archivo según el destino indicado.

### 4 Contenido de archivos

```bash
printf '%s\n' 'Hola, este es mi primer archivo en Linux' > nota.txt
printf '%s\n' 'Estoy aprendiendo comandos básicos' >> nota.txt
cat nota.txt
head -n 1 nota.txt
tail -n 1 nota.txt
```

`>` escribe reemplazando el contenido y `>>` agrega al final. `head` y `tail` permiten consultar partes del archivo.

### 5 Usuario y sistema

```bash
whoami
date
uname -a
history
```

Estas consultas ayudan a reconocer el entorno. Antes de publicar sus salidas, se deben revisar nombres de usuario, rutas e historial para no exponer información privada.

### 6 Actividad de integración

```bash
mkdir mi_proyecto
cd mi_proyecto
touch doc1.txt doc2.txt doc3.txt
printf '%s\n' 'Este es mi primer proyecto' > doc1.txt
cp -i doc1.txt doc1_backup.txt
mkdir respaldo
mv -i doc2.txt respaldo/
ls -l
ls -l respaldo
cmp doc1.txt doc1_backup.txt
```

## Resultado esperado y comprobación

```text
mi_proyecto/
├── doc1.txt
├── doc1_backup.txt
├── doc3.txt
└── respaldo/
    └── doc2.txt
```

`doc1.txt` y `doc1_backup.txt` deben contener la misma frase. `cmp` no imprime diferencias cuando ambos son iguales. `doc2.txt` debe estar dentro de `respaldo` y `doc3.txt` debe seguir vacío. Estos son criterios de verificación, no resultados observados.

## Aprendizajes que desarrolla la práctica

La práctica permite distinguir una ruta de un archivo, comprender la diferencia entre copiar y mover y reconocer el efecto de la redirección. También introduce el cuidado necesario al eliminar datos y publicar evidencias técnicas.

## Referencia y licencia

Consigna de referencia: Laboratorio 2 de Gestión de Sistemas Operativos II, Mgtr. Elisleila González, UTP. El archivo de referencia identifica a Jean Quiroz y Herald Pimentel. Esta documentación nueva no atribuye su autoría a la docente ni al compañero.

La licencia MIT cubre únicamente la documentación original aportada a este repositorio. No extiende derechos sobre guías docentes ni materiales ajenos.
