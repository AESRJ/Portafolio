---
title: "My Second Post"
date: 2025-08-29T10:51:21-07:00
tags: []
draft: false
featured_image: ""
description: "Portafolio de mis practicas de paradigmas d"
---

## Código analizado

```c
#include <stdio.h>

int global_var = 10;

void func() {
    int local_var = 20;          // variable local automática
    static int static_var = 30;  // variable estática
    local_var++;
    static_var++;
    printf("local_var: %d, static_var: %d\n", local_var, static_var);
}

int main() {
    func();
    func();
    return 0;
}

```

---

## Tipos de memoria usados

1. **`int global_var = 10;`**
    - Se almacena en el **segmento de datos (memoria estática)**.
    - Existe durante toda la ejecución del programa.
2. **`int local_var = 20;`**
    - Es una **variable automática (stack)**.
    - Se crea cada vez que se llama a `func()` y se destruye al salir de la función.
3. **`static int static_var = 30;`**
    - Se almacena en el **segmento de datos (memoria estática)**.
    - Se inicializa solo una vez (cuando el programa arranca).
    - Conserva su valor entre llamadas a la función.

---

## Ejecución paso a paso

### Primera llamada a `func()`

- `local_var = 20;` → luego `local_var++` → `21`
- `static_var = 30;` → luego `static_var++` → `31`
- **Salida:**
    
    ```
    local_var: 21, static_var: 31
    
    ```
    

### Segunda llamada a `func()`

- `local_var` se reinicia en `20;` → luego `local_var++` → `21`
- `static_var` conserva su valor anterior (`31`) → luego `static_var++` → `32`
- **Salida:**
    
    ```
    local_var: 21, static_var: 32
    
    ```
    

---

## Salida final del programa

```
local_var: 21, static_var: 31
local_var: 21, static_var: 32

```

---

**Conclusión:**

- `global_var` y `static_var` usan **memoria estática**.
- `local_var` usa **memoria automática (stack)**.
- No se usa memoria **dinámica (heap)** porque no hay `malloc`/`free`.

## Código Analizado:

```c
#include <stdio.h>
#include <stdlib.h>

void allocate_memory() {
    int *arr = (int *)malloc(5 * sizeof(int));
    for (int i = 0; i < 5; i++) {
        arr[i] = i * 2;
    }
    printf("arr[2]: %d\n", arr[2]);
}

int main() {
    allocate_memory();
    return 0;
}

```

---

## Problema de manejo de memoria

El error es que **la memoria dinámica reservada con `malloc` nunca se libera con `free`**.

Esto provoca una **fuga de memoria (memory leak)**:

- Cada vez que se llama a `allocate_memory()`, se reserva memoria en el heap.
- Al terminar la función, el puntero `arr` se destruye (por estar en el stack), pero la memoria que apunta sigue ocupada en el heap y queda inaccesible.

 Esto no se nota en programas pequeños, pero en programas largos o con muchas llamadas provoca **agotamiento de memoria**.

---

## Solución

Liberar la memoria al final de la función usando `free(arr)`:

```c
#include <stdio.h>
#include <stdlib.h>

void allocate_memory() {
    int *arr = (int *)malloc(5 * sizeof(int));
    if (arr == NULL) { // siempre es buena práctica verificar malloc
        printf("Error al asignar memoria\n");
        return;
    }

    for (int i = 0; i < 5; i++) {
        arr[i] = i * 2;
    }
    printf("arr[2]: %d\n", arr[2]);

    free(arr); // ✅ Se libera la memoria
}

int main() {
    allocate_memory();
    return 0;
}

```

---

**Conclusión:**

- El programa tenía una **fuga de memoria** por no usar `free`.
- La solución es llamar a `free(arr)` después de usar el arreglo.
- Además, siempre conviene verificar si `malloc` devolvió `NULL` (por falta de memoria).