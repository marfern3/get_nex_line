# Get Next Line

`get_next_line` es un proyecto de la escuela 42 cuyo objetivo es implementar una función en C que lea una línea completa de un descriptor de archivo, independientemente de su tamaño. Es un ejercicio fundamental para aprender a gestionar memoria dinámica y trabajar con buffers en C.

---

## Descripción del proyecto

El proyecto consiste en crear una función que se pueda utilizar de la siguiente manera:

```c
char *get_next_line(int fd);
```

La función debe:
- Leer y devolver una línea completa, terminada en un salto de línea (`\n`) o el final del archivo (EOF).
- Gestionar eficientemente la memoria utilizando un buffer de tamaño definido por `BUFFER_SIZE`.
- Manejar múltiples descriptores de archivo simultáneamente.

---

## Requisitos

El programa debe cumplir con las siguientes especificaciones:
- Funcionar correctamente con cualquier tamaño de `BUFFER_SIZE`.
- Liberar toda la memoria asignada dinámicamente para evitar fugas.
- Ser compatible con el estándar C y seguir la norma de codificación de la escuela 42 (Norminette).

---

## Archivos

El proyecto contiene los siguientes archivos:

- **`get_next_line.c`**: Contiene la lógica principal para leer y devolver una línea.
- **`get_next_line_utils.c`**: Funciones auxiliares para gestionar cadenas y memoria.
- **`get_next_line.h`**: Cabecera que define las funciones y macros utilizadas.
- **`main.c`**: Programa de prueba para verificar el correcto funcionamiento de la función.

---

## Cómo usar

1. Clona este repositorio:

   ```bash
   git clone https://github.com/tuusuario/get_next_line.git
   cd get_next_line
   ```

2. Asegúrate de tener configurado el tamaño de `BUFFER_SIZE` antes de compilar. Puedes definirlo durante la compilación:

   ```bash
   gcc -D BUFFER_SIZE=42 -Wall -Wextra -Werror get_next_line.c get_next_line_utils.c main.c -o gnl
   ```

3. Ejecuta el programa:

   ```bash
   ./gnl
   ```

---

## Pruebas

El proyecto incluye un archivo `main.c` que te permite probar la función `get_next_line` con diferentes descriptores de archivo. Puedes modificar este archivo o usar herramientas como [Valgrind](https://valgrind.org/) para verificar fugas de memoria:

```bash
valgrind --leak-check=full ./gnl
```

---

## Ejemplo de uso

Supongamos que tenemos un archivo llamado `sample.txt` con el siguiente contenido:

```
Hola mundo
42 Madrid
get_next_line
```

Al ejecutar la función:

```c
int fd = open("sample.txt", O_RDONLY);
char *line;

while ((line = get_next_line(fd))) {
    printf("%s", line);
    free(line);
}
close(fd);
```

La salida será:

```
Hola mundo
42 Madrid
get_next_line
```

---

## Recursos

- [Manuales de sistema Linux](https://man7.org/linux/man-pages/): Referencia para funciones como `read`, `malloc` y `free`.
- [Norminette](https://github.com/42School/norminette): Herramienta para validar la norma de 42.
- [Valgrind](https://valgrind.org/): Para verificar la gestión de memoria dinámica.

---

## Contribuciones

Este proyecto forma parte de la formación en 42 y, como tal, las contribuciones externas no están permitidas. Sin embargo, cualquier sugerencia o mejora es bienvenida.

---

## Autor

Marco Fernandez Callejon

---

## Licencia

Este proyecto es parte del currículo de la escuela 42 y está sujeto a sus normas y regulaciones.

