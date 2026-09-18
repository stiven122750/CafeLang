# CafeLang

Lenguaje de programación basado en el contexto de una cafetería.

---

## Sintaxis general de las reglas

La siguiente gramática define la estructura básica que pueden tener
las reglas dentro de CafeLang.

```text
<programa> ::= { <sentencia> }


<sentencia> ::= <estructura_condicional>
              | <llamada_funcion>
              | <accion_cafe>


<estructura_condicional> ::= 
    "SI" "(" <expresion_logica> ")" 
    "{" <bloque> "}" 
    [ <bloque_sino> ]


<bloque_sino> ::= 
    "SINO" "{" <bloque> "}"
    |
    "SINO" "SI" "(" <expresion_logica> ")" 
    "{" <bloque> "}" 
    [ <bloque_sino> ]


<bloque> ::= { <sentencia> }


<llamada_funcion> ::= 
    "MOSTRAR" "(" <expresion> ")"


<accion_cafe> ::= 
    "PREPARAR"
    | "MOLER"
    | "TOSTAR"
    | "SERVIR"
    | "CANCELAR"


<expresion> ::= 
    <expresion_logica>
    | <valor_numerico>
    | <valor_booleano>
    | <cadena>


<expresion_logica> ::= 
    <termino_logico>
    { <operador_logico> <termino_logico> }


<termino_logico> ::= 
    <comparacion>
    | <valor_booleano>
    | "(" <expresion_logica> ")"


<comparacion> ::= 
    <valor> <operador_relacional> <valor>


<valor> ::= 
    <identificador>
    | <valor_numerico>
    | <valor_booleano>
    | <cadena>


<operador_logico> ::= 
    "Y"
    | "O"


<operador_relacional> ::= 
    "=="
    | "!="
    | ">"
    | "<"
    | ">="
    | "<="


<valor_booleano> ::= 
    "VERDADERO"
    | "FALSO"


<valor_numerico> ::= 
    <digito> { <digito> }
    [ "." <digito> { <digito> } ]


<cadena> ::= 
    '"' { <caracter> } '"'


<identificador> ::= 
    <letra> { <letra> | <digito> | "_" }


<digito> ::= 
    "0" | "1" | "2" | "3" | "4"
    | "5" | "6" | "7" | "8" | "9"


<letra> ::= 
    "a" | ... | "z"
    | "A" | ... | "Z"
```

---

## Palabras reservadas

Las palabras reservadas son aquellas que tienen un significado
específico dentro del lenguaje y que no deben utilizarse como
nombres de variables.

| Concepto    | Palabra reservada | Ejemplo                         |
| ----------- | ----------------- | ------------------------------- |
| Condición   | `SI`              | `SI (edad >= 18)`               |
| Alternativa | `SINO`            | `SINO { ... }`                  |
| Ciclo       | `MIENTRAS`        | `MIENTRAS (pedidoActivo)`       |
| AND         | `Y`               | `edad >= 18 Y pedidoActivo`     |
| OR          | `O`               | `tieneCupon O clienteFrecuente` |
| Verdadero   | `VERDADERO`       | `cafeDisponible == VERDADERO`   |
| Falso       | `FALSO`           | `cafeDisponible == FALSO`       |
| Mostrar     | `MOSTRAR`         | `MOSTRAR("Café listo")`         |
| Preparar    | `PREPARAR`        | `PREPARAR`                      |
| Moler       | `MOLER`           | `MOLER`                         |
| Tostar      | `TOSTAR`          | `TOSTAR`                        |
| Servir      | `SERVIR`          | `SERVIR`                        |
| Cancelar    | `CANCELAR`        | `CANCELAR`                      |

---

## Acciones propias del lenguaje

Las siguientes palabras están relacionadas directamente con el
tema del café:

```text
PREPARAR
MOLER
TOSTAR
SERVIR
CANCELAR
```

Estas acciones permiten que el lenguaje tenga una relación con el
contexto de una cafetería sin cambiar demasiado la estructura de
un lenguaje de programación tradicional.

Ejemplo:

```text
PREPARAR
```

```text
SERVIR
```

---

## Convención de escritura

### 1. Palabras reservadas

Las palabras reservadas se escriben en mayúsculas.

Ejemplos:

```text
SI
SINO
MIENTRAS
MOSTRAR
PREPARAR
MOLER
TOSTAR
SERVIR
CANCELAR
```

### 2. Variables

Los nombres de las variables se escriben utilizando camelCase.

Ejemplos:

```text
precioCafe
cantidadTazas
gramosCafe
temperaturaAgua
saldoCliente
puntosCliente
tipoCafe
nombreCliente
```

### 3. Variables booleanas

Para las variables booleanas se utilizan nombres que permitan
identificar fácilmente si representan una condición.

Ejemplos:

```text
cafeDisponible
pedidoActivo
clienteFrecuente
cafeTostado
cafeMolido
aguaDisponible
tieneLeche
tieneCupon
pedidoPreparado
```

### 4. Variables numéricas

Las variables numéricas utilizan nombres relacionados con el
dato que almacenan.

Ejemplos:

```text
precioCafe
cantidadTazas
gramosCafe
temperaturaAgua
nivelAzucar
calidadCafe
saldoCliente
puntosCliente
```

### 5. Variables de texto

Las variables que almacenan texto también utilizan camelCase.

Ejemplos:

```text
nombreCliente
tipoCafe
nombrePedido
```

### 6. Cadenas de texto

Los textos se escriben entre comillas dobles.

Ejemplo:

```text
MOSTRAR("El café está disponible")
```

### 7. Indentación

Se utilizan 4 espacios para cada nivel de indentación.

Ejemplo:

```text
SI (cafeDisponible == VERDADERO) {
    MOSTRAR("El café está disponible")
}
```

En condiciones anidadas:

```text
SI (cafeDisponible == VERDADERO) {
    SI (temperaturaAgua >= 90) {
        MOSTRAR("El café puede prepararse")
    }
}
```

### 8. Operadores relacionales

Los operadores deben tener un espacio antes y después.

Correcto:

```text
precioCafe >= 5000
gramosCafe > 18
temperaturaAgua <= 95
```

Incorrecto:

```text
precioCafe>=5000
gramosCafe>18
temperaturaAgua<=95
```

### 9. Operadores lógicos

Los operadores lógicos también se escriben separados por espacios.

Ejemplo:

```text
gramosCafe >= 18 Y temperaturaAgua >= 90
```

Otro ejemplo:

```text
tieneCupon == VERDADERO O clienteFrecuente == VERDADERO
```

---

## Ejemplos de reglas

### Regla con una condición

```text
SI (cafeDisponible == VERDADERO) {
    MOSTRAR("El café está disponible")
}
```

### Regla con dos condiciones

```text
SI (gramosCafe >= 18 Y temperaturaAgua >= 90) {
    MOSTRAR("El café puede prepararse")
}
```

### Regla utilizando OR

```text
SI (saldoCliente >= precioCafe O tieneCupon == VERDADERO) {
    MOSTRAR("Compra autorizada")
}
```

### Regla con alternativa

```text
SI (cafeDisponible == VERDADERO) {
    MOSTRAR("El café está disponible")
}
SINO {
    MOSTRAR("El café no está disponible")
}
```

### Regla con una acción

```text
SI (pedidoPreparado == VERDADERO) {
    SERVIR
}
```

---

## Resumen

CafeLang utiliza una estructura sencilla para representar las reglas
del proyecto.

Las estructuras principales son:

```text
SI
SINO
MIENTRAS
```

Los operadores lógicos son:

```text
Y
O
```

Los valores booleanos son:

```text
VERDADERO
FALSO
```

Y las acciones relacionadas con el contexto del café son:

```text
PREPARAR
MOLER
TOSTAR
SERVIR
CANCELAR
```

La idea es mantener una sintaxis fácil de leer y al mismo tiempo
contar con las estructuras necesarias para realizar el análisis
léxico y sintáctico del lenguaje.
