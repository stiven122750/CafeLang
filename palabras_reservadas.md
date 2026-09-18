# CafeLang

> **Lenguaje de programación orientado al contexto del café**

---

## 1. Sintaxis general de las reglas

La sintaxis de CafeLang se define mediante una gramática basada en
**BNF (Backus-Naur Form)**.

La gramática establece la estructura que deben cumplir los programas,
las sentencias, las condiciones, las expresiones y las acciones
propias del lenguaje.

### 1.1. Programa

```bnf
<programa> ::= { <sentencia> }
```

Un programa está compuesto por cero o más sentencias.

---

### 1.2. Sentencias

```bnf
<sentencia> ::= <estructura_condicional>
              | <llamada_funcion>
              | <accion_cafe>
```

Una sentencia puede ser una estructura condicional, una llamada a
`MOSTRAR` o una acción relacionada con el café.

---

### 1.3. Estructura condicional

```bnf
<estructura_condicional> ::= 
    "SI" "(" <expresion_logica> ")" 
    "{" <bloque> "}" 
    [ <bloque_sino> ]
```

Permite ejecutar un bloque de instrucciones cuando una condición
lógica se cumple.

Ejemplo:

```text
SI (cafeDisponible == VERDADERO) {
    MOSTRAR("El café está disponible")
}
```

---

### 1.4. Estructura alternativa

```bnf
<bloque_sino> ::= 
    "SINO" "{" <bloque> "}"
    |
    "SINO" "SI" "(" <expresion_logica> ")" 
    "{" <bloque> "}" 
    [ <bloque_sino> ]
```

Permite ejecutar instrucciones alternativas cuando la condición
principal no se cumple.

Ejemplo:

```text
SI (cafeDisponible == VERDADERO) {
    MOSTRAR("El café está disponible")
}
SINO {
    MOSTRAR("El café no está disponible")
}
```

También permite condiciones alternativas:

```text
SI (calidadCafe >= 90) {
    MOSTRAR("Café de excelente calidad")
}
SINO SI (calidadCafe >= 80) {
    MOSTRAR("Café de buena calidad")
}
SINO {
    MOSTRAR("La calidad del café es baja")
}
```

---

### 1.5. Bloque de instrucciones

```bnf
<bloque> ::= { <sentencia> }
```

Un bloque puede contener una o varias sentencias.

---

### 1.6. Llamada de función

```bnf
<llamada_funcion> ::= 
    "MOSTRAR" "(" <expresion> ")"
```

`MOSTRAR` permite presentar un mensaje o resultado.

Ejemplo:

```text
MOSTRAR("El pedido está listo")
```

---

### 1.7. Acciones relacionadas con el café

```bnf
<accion_cafe> ::=
    "PREPARAR"
    | "MOLER"
    | "TOSTAR"
    | "SERVIR"
    | "CANCELAR"
```

Estas acciones representan operaciones propias del dominio de
CafeLang.

Ejemplos:

```text
PREPARAR
MOLER
TOSTAR
SERVIR
CANCELAR
```

---

## 2. Expresiones

### 2.1. Expresión general

```bnf
<expresion> ::= 
    <expresion_logica>
    | <valor_numerico>
    | <valor_booleano>
    | <cadena>
```

Una expresión puede representar una condición lógica, un número,
un valor booleano o una cadena de texto.

---

### 2.2. Expresión lógica

```bnf
<expresion_logica> ::= 
    <termino_logico> 
    { <operador_logico> <termino_logico> }
```

Permite combinar una o más condiciones mediante operadores lógicos.

Ejemplo:

```text
gramosCafe >= 18 Y temperaturaAgua >= 90
```

---

### 2.3. Término lógico

```bnf
<termino_logico> ::= 
    <comparacion>
    | <valor_booleano>
    | "(" <expresion_logica> ")"
```

Un término lógico puede ser una comparación, un valor booleano
o una expresión lógica agrupada mediante paréntesis.

---

### 2.4. Comparación

```bnf
<comparacion> ::= 
    <valor> <operador_relacional> <valor>
```

Las comparaciones permiten establecer relaciones entre valores.

Ejemplos:

```text
precioCafe >= 5000
gramosCafe > 18
temperaturaAgua <= 95
cafeDisponible == VERDADERO
```

---

### 2.5. Valores

```bnf
<valor> ::= 
    <valor_numerico>
    | <valor_booleano>
```

Los valores utilizados en una comparación pueden ser numéricos
o booleanos.

---

## 3. Operadores

### 3.1. Operadores lógicos

```bnf
<operador_logico> ::= 
    "Y"
    | "O"
```

| Operador | Función                                |
| -------- | -------------------------------------- |
| `Y`      | Ambas condiciones deben cumplirse.     |
| `O`      | Al menos una condición debe cumplirse. |

Ejemplo:

```text
SI (gramosCafe >= 18 Y temperaturaAgua >= 90) {
    MOSTRAR("El café puede prepararse")
}
```

---

### 3.2. Operadores relacionales

```bnf
<operador_relacional> ::= 
    "==" 
    | "!=" 
    | ">"
    | "<"
    | ">="
    | "<="
```

| Operador | Significado       |
| -------- | ----------------- |
| `==`     | Igual que         |
| `!=`     | Diferente de      |
| `>`      | Mayor que         |
| `<`      | Menor que         |
| `>=`     | Mayor o igual que |
| `<=`     | Menor o igual que |

---

## 4. Valores booleanos

```bnf
<valor_booleano> ::= 
    "VERDADERO"
    | "FALSO"
```

Los valores booleanos representan estados de verdadero o falso.

Ejemplo:

```text
cafeDisponible == VERDADERO
```

```text
pedidoActivo == FALSO
```

---

## 5. Valores numéricos

```bnf
<valor_numerico> ::= 
    <digito> { <digito> } 
    [ "." <digito> { <digito> } ]
```

Los valores numéricos pueden representar números enteros o
decimales.

Ejemplos:

```text
20
18
8500
92.5
3.14
```

---

## 6. Cadenas de texto

```bnf
<cadena> ::= 
    '"' { <caracter> } '"'
```

Las cadenas de texto deben estar delimitadas mediante comillas
dobles.

Ejemplos:

```text
"El café está disponible"

"Pedido listo"

"Temperatura adecuada"
```

---

## 7. Dígitos y letras

### 7.1. Dígitos

```bnf
<digito> ::= 
    "0" | "1" | "2" | "3" | "4"
    | "5" | "6" | "7" | "8" | "9"
```

### 7.2. Letras

```bnf
<letra> ::= 
    "a" | ... | "z"
    | "A" | ... | "Z"
```

---

# 8. Palabras reservadas

Las palabras reservadas son elementos que poseen un significado
especial dentro del lenguaje y no pueden utilizarse como nombres
de variables.

| Concepto    | Palabra reservada | Ejemplo                         |
| ----------- | ----------------- | ------------------------------- |
| Condicional | `SI`              | `SI (edad >= 18)`               |
| Alternativa | `SINO`            | `SINO { ... }`                  |
| Ciclo       | `MIENTRAS`        | `MIENTRAS (pedidoActivo)`       |
| AND         | `Y`               | `edad >= 18 Y activo`           |
| OR          | `O`               | `tieneCupon O clienteFrecuente` |
| True        | `VERDADERO`       | `activo == VERDADERO`           |
| False       | `FALSO`           | `activo == FALSO`               |
| Print       | `MOSTRAR`         | `MOSTRAR("Café listo")`         |
| Preparar    | `PREPARAR`        | `PREPARAR`                      |
| Moler       | `MOLER`           | `MOLER`                         |
| Tostar      | `TOSTAR`          | `TOSTAR`                        |
| Servir      | `SERVIR`          | `SERVIR`                        |
| Cancelar    | `CANCELAR`        | `CANCELAR`                      |

---

# 9. Convenciones de escritura

## 9.1. Palabras reservadas

Las palabras reservadas se escriben siempre en **MAYÚSCULAS**.

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

---

## 9.2. Nombres de variables

Los nombres de variables utilizan **camelCase** y deben representar
claramente el concepto almacenado.

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

---

## 9.3. Variables booleanas

Las variables booleanas deben utilizar nombres que permitan
identificar fácilmente que representan una condición de verdadero
o falso.

Se recomienda utilizar nombres como:

```text
cafeDisponible
pedidoActivo
clienteFrecuente
tieneLeche
tieneCupon
cafeTostado
cafeMolido
aguaDisponible
```

---

## 9.4. Variables numéricas

Las variables numéricas utilizan nombres relacionados directamente
con el concepto que representan.

Ejemplos:

```text
precioCafe
cantidadTazas
gramosCafe
temperaturaAgua
calidadCafe
saldoCliente
puntosCliente
```

---

## 9.5. Variables de texto

Las variables de texto utilizan camelCase.

Ejemplos:

```text
nombreCliente
tipoCafe
nombrePedido
```

---

## 9.6. Cadenas de texto

Las cadenas siempre deben escribirse entre comillas dobles.

Correcto:

```text
MOSTRAR("El café está disponible")
```

Incorrecto:

```text
MOSTRAR(El café está disponible)
```

---

## 9.7. Indentación y llaves

Se utilizan **4 espacios por nivel de indentación**.

La llave de apertura se escribe en la misma línea de la condición.

Ejemplo:

```text
SI (cafeDisponible == VERDADERO) {
    MOSTRAR("El café está disponible")
}
```

Para estructuras anidadas:

```text
SI (cafeDisponible == VERDADERO) {
    SI (temperaturaAgua >= 90) {
        MOSTRAR("El café puede prepararse")
    }
}
```

---

## 9.8. Operadores relacionales

Los operadores relacionales deben tener un espacio antes y después.

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

---

## 9.9. Operadores lógicos

Los operadores lógicos también deben estar separados por espacios.

Correcto:

```text
gramosCafe >= 18 Y temperaturaAgua >= 90
```

```text
tieneCupon == VERDADERO O clienteFrecuente == VERDADERO
```

Incorrecto:

```text
gramosCafe >= 18YtemperaturaAgua >= 90
```

---

# 10. Ejemplo completo

El siguiente ejemplo combina condiciones, operadores lógicos,
valores booleanos, salida de información y acciones propias
de CafeLang.

```text
SI (cafeDisponible == VERDADERO) {

    SI (gramosCafe >= 18 Y temperaturaAgua >= 90) {

        PREPARAR

        MOSTRAR("El café puede prepararse")

    } SINO {

        MOSTRAR("Las condiciones de preparación no son adecuadas")

    }

} SINO {

    MOSTRAR("El café no está disponible")
}
```

---

# 11. Resumen de palabras reservadas

```text
SI
SINO
MIENTRAS
Y
O
VERDADERO
FALSO
MOSTRAR
PREPARAR
MOLER
TOSTAR
SERVIR
CANCELAR
```

---

## 12. Identidad del lenguaje

CafeLang mantiene una estructura de programación convencional,
pero incorpora acciones relacionadas con el contexto del café.

La intención es que la sintaxis sea:

* Sencilla de leer.
* Fácil de implementar.
* Fácil de analizar mediante un lexer.
* Compatible con un parser basado en reglas gramaticales.
* Clara para la construcción del AST.
* Coherente con las 15 reglas definidas para el proyecto.

La personalización del lenguaje se concentra principalmente en
las acciones del dominio:

```text
PREPARAR
MOLER
TOSTAR
SERVIR
CANCELAR
```

Mientras que las estructuras fundamentales mantienen una sintaxis
simple:

```text
SI
SINO
MIENTRAS
Y
O
MOSTRAR
```
