# CafeLang

Lenguaje de programación basado en el contexto de una cafetería.

CafeLang permite representar reglas de negocio mediante variables, condiciones, ciclos, funciones y acciones relacionadas con la preparación y venta de café.

---

# 1. Sintaxis general

    <programa> ::= { <declaracion> | <declaracion_funcion> | <sentencia> }

    <sentencia> ::= <condicional>
                  | <ciclo>
                  | <asignacion>
                  | <llamada_funcion>
                  | <entrada>
                  | <salida>
                  | <retorno>
                  | <accion_cafe>

    <condicional> ::= "SI" "(" <expresion_logica> ")" "{" <bloque> "}"
                      [ "SINO" "{" <bloque> "}" ]

    <ciclo> ::= "MIENTRAS" "(" <expresion_logica> ")" "{" <bloque> "}"
              | "PARA" "(" <asignacion> ";" <expresion_logica> ";" <asignacion> ")" "{" <bloque> "}"

    <declaracion> ::= <tipo> <identificador> [ "=" <expresion> ]

    <asignacion> ::= <identificador> "=" <expresion>

    <declaracion_funcion> ::= "FUNCION" <identificador> "(" [ <parametros> ] ")" "{" <bloque> "}"

    <parametros> ::= <parametro> { "," <parametro> }

    <parametro> ::= <tipo> <identificador>

    <llamada_funcion> ::= <identificador> "(" [ <argumentos> ] ")"

    <argumentos> ::= <expresion> { "," <expresion> }

    <entrada> ::= "LEER" "(" <identificador> ")"

    <salida> ::= "MOSTRAR" "(" <expresion> ")"

    <retorno> ::= "RETORNAR" <expresion>

    <accion_cafe> ::= "PREPARAR"
                    | "MOLER"
                    | "TOSTAR"
                    | "SERVIR"
                    | "CANCELAR"

    <bloque> ::= { <sentencia> }

---

# 2. Palabras reservadas

Las palabras reservadas forman parte del lenguaje y no pueden utilizarse como nombres de variables o funciones.

    SI
    SINO
    MIENTRAS
    PARA
    FUNCION
    RETORNAR

    ENTERO
    DECIMAL
    TEXTO
    BOOLEANO

    VERDADERO
    FALSO

    LEER
    MOSTRAR

    PREPARAR
    MOLER
    TOSTAR
    SERVIR
    CANCELAR

    Y
    O
    NO

---

# 3. Terminales

Los terminales son los elementos reconocidos directamente por el analizador léxico.

## 3.1 Palabras reservadas

    SI
    SINO
    MIENTRAS
    PARA
    FUNCION
    RETORNAR
    ENTERO
    DECIMAL
    TEXTO
    BOOLEANO
    VERDADERO
    FALSO
    LEER
    MOSTRAR
    PREPARAR
    MOLER
    TOSTAR
    SERVIR
    CANCELAR
    Y
    O
    NO

## 3.2 Operadores

    +
    -
    *
    /
    %
    ==
    !=
    >
    <
    >=
    <=
    =

## 3.3 Símbolos

    (
    )
    {
    }
    [
    ]
    ,
    ;

## 3.4 Tokens

    IDENTIFICADOR
    NUMERO_ENTERO
    NUMERO_DECIMAL
    CADENA

---

# 4. No terminales

Los no terminales representan las estructuras sintácticas de CafeLang.

    <programa>
    <sentencia>
    <condicional>
    <ciclo>
    <declaracion>
    <asignacion>
    <declaracion_funcion>
    <parametros>
    <parametro>
    <llamada_funcion>
    <argumentos>
    <entrada>
    <salida>
    <retorno>
    <accion_cafe>
    <bloque>
    <expresion>
    <expresion_aritmetica>
    <expresion_logica>
    <comparacion>
    <operador_logico>
    <operador_relacional>
    <operador_aritmetico>
    <tipo>
    <valor>
    <identificador>
    <cadena>
    <valor_numerico>

---

# 5. Tipos de datos

CafeLang dispone de cuatro tipos de datos principales:

    ENTERO
    DECIMAL
    TEXTO
    BOOLEANO

Ejemplos:

    ENTERO cantidadTazas = 2
    DECIMAL precioCafe = 8500.0
    TEXTO nombreCliente = "Steven"
    BOOLEANO cafeDisponible = VERDADERO

---

# 6. Variables

Las variables utilizan nombres descriptivos y el formato camelCase.

Ejemplos:

    precioCafe
    cantidadTazas
    gramosCafe
    temperaturaAgua
    nivelAzucar
    calidadCafe
    saldoCliente
    puntosCliente
    cafeDisponible
    pedidoActivo
    clienteFrecuente
    cafeTostado
    cafeMolido
    aguaDisponible
    tieneLeche
    tieneCupon
    pedidoPreparado
    tipoCafe
    nombreCliente
    tazasServidas
    total
    precioFinal

## 6.1 Variables booleanas

Las variables booleanas representan estados.

    BOOLEANO cafeDisponible = VERDADERO
    BOOLEANO cafeMolido = FALSO
    BOOLEANO aguaDisponible = VERDADERO
    BOOLEANO tieneLeche = VERDADERO
    BOOLEANO tieneCupon = FALSO
    BOOLEANO pedidoPreparado = FALSO

---

# 7. Declaración y asignación

## 7.1 Declaración

    ENTERO cantidadTazas
    DECIMAL precioCafe
    TEXTO nombreCliente
    BOOLEANO cafeDisponible

## 7.2 Declaración con valor inicial

    ENTERO cantidadTazas = 2
    DECIMAL precioCafe = 8500.0
    TEXTO nombreCliente = "Steven"
    BOOLEANO cafeDisponible = VERDADERO

## 7.3 Asignación

    cantidadTazas = 3
    precioCafe = 9000.0
    nombreCliente = "Carlos"
    cafeDisponible = FALSO

---

# 8. Operadores

## 8.1 Operadores aritméticos

    +
    -
    *
    /
    %

Ejemplo:

    total = cantidadTazas * precioCafe

## 8.2 Operadores relacionales

    ==
    !=
    >
    <
    >=
    <=

Ejemplos:

    precioCafe > 5000
    puntosCliente >= 500
    cafeDisponible == VERDADERO

## 8.3 Operadores lógicos

    Y
    O
    NO

Ejemplo:

    SI (temperaturaAgua >= 85 Y temperaturaAgua <= 95) {
        MOSTRAR("Temperatura adecuada")
    }

Ejemplo con O:

    SI (tieneCupon == VERDADERO O puntosCliente >= 500) {
        MOSTRAR("Beneficio disponible")
    }

Ejemplo con NO:

    SI (NO cafeDisponible) {
        MOSTRAR("No hay café disponible")
    }

---

# 9. Expresiones

Las expresiones permiten realizar operaciones aritméticas, comparaciones y evaluaciones lógicas.

## 9.1 Expresiones aritméticas

    total = cantidadTazas * precioCafe

    precioFinal = precioCafe - descuento

    gramosCafe = cantidadTazas * 15

## 9.2 Expresiones relacionales

    cantidadTazas > 0

    temperaturaAgua >= 85

    puntosCliente >= 500

## 9.3 Expresiones lógicas

    cafeDisponible == VERDADERO Y aguaDisponible == VERDADERO

    tieneCupon == VERDADERO O puntosCliente >= 500

    NO pedidoPreparado

---

# 10. Precedencia de operadores

CafeLang utiliza la siguiente prioridad:

    1. Paréntesis
    2. NO
    3. * / %
    4. + -
    5. == != > < >= <=
    6. Y
    7. O
    8. =

Ejemplo:

    total = cantidadTazas * precioCafe + costoExtra

La multiplicación se realiza antes de la suma.

---

# 11. Condicionales

## 11.1 SI

    SI (cafeDisponible == VERDADERO) {
        MOSTRAR("El café está disponible")
    }

## 11.2 SI / SINO

    SI (cafeDisponible == VERDADERO) {
        MOSTRAR("El café está disponible")
    }
    SINO {
        MOSTRAR("No hay café disponible")
    }

## 11.3 Condiciones anidadas

    SI (cafeDisponible == VERDADERO) {

        SI (temperaturaAgua >= 85 Y temperaturaAgua <= 95) {

            PREPARAR

        }
    }

---

# 12. Ciclos

CafeLang dispone de dos estructuras de repetición.

## 12.1 MIENTRAS

    ENTERO tazasServidas = 0

    MIENTRAS (tazasServidas < cantidadTazas) {

        SERVIR

        tazasServidas = tazasServidas + 1
    }

## 12.2 PARA

    ENTERO i = 1

    PARA (i = 1; i <= cantidadTazas; i = i + 1) {

        SERVIR
    }

---

# 13. Funciones

Las funciones permiten agrupar operaciones reutilizables.

Una función puede recibir parámetros y devolver valores mediante RETORNAR.

## 13.1 Función básica

    FUNCION calcularTotal(ENTERO cantidad, DECIMAL precio) {

        RETORNAR cantidad * precio

    }

## 13.2 Uso de una función

    DECIMAL total

    total = calcularTotal(cantidadTazas, precioCafe)

    MOSTRAR(total)

## 13.3 Función con condiciones

    FUNCION calcularDescuento(DECIMAL precio, ENTERO puntos) {

        SI (puntos >= 500) {

            RETORNAR precio * 0.90

        }

        RETORNAR precio
    }

---

# 14. Entrada de datos

LEER permite recibir información del usuario.

Ejemplo:

    ENTERO cantidadTazas

    LEER(cantidadTazas)

Otro ejemplo:

    TEXTO nombreCliente

    LEER(nombreCliente)

---

# 15. Salida de datos

MOSTRAR permite presentar información al usuario.

Ejemplos:

    MOSTRAR("Café listo")

    MOSTRAR(cantidadTazas)

    MOSTRAR(total)

    MOSTRAR(nombreCliente)

---

# 16. Acciones propias de CafeLang

CafeLang incorpora instrucciones relacionadas directamente con el contexto de una cafetería.

    PREPARAR
    MOLER
    TOSTAR
    SERVIR
    CANCELAR

## 16.1 PREPARAR

Representa el proceso de preparación del café.

    PREPARAR

## 16.2 MOLER

Representa el proceso de molienda.

    MOLER

## 16.3 TOSTAR

Representa el proceso de tostado.

    TOSTAR

## 16.4 SERVIR

Representa el servicio del café al cliente.

    SERVIR

## 16.5 CANCELAR

Cancela el proceso o pedido actual.

    CANCELAR

---

# 17. Reglas de negocio de la cafetería

CafeLang puede representar reglas específicas del dominio.

## 17.1 Café disponible

    SI (cafeDisponible == VERDADERO) {
        MOSTRAR("El café está disponible")
    }
    SINO {
        MOSTRAR("Café agotado")
    }

## 17.2 Cliente frecuente

    SI (puntosCliente >= 500) {

        clienteFrecuente = VERDADERO

        MOSTRAR("Cliente frecuente")
    }

## 17.3 Temperatura adecuada

    SI (temperaturaAgua >= 85 Y temperaturaAgua <= 95) {

        MOSTRAR("Temperatura adecuada")

    }
    SINO {

        MOSTRAR("Temperatura incorrecta")

    }

## 17.4 Preparación del café

    SI (cafeMolido == VERDADERO Y aguaDisponible == VERDADERO) {

        PREPARAR

        pedidoPreparado = VERDADERO

    }

## 17.5 Compra autorizada

    SI (saldoCliente >= precioCafe O tieneCupon == VERDADERO) {

        MOSTRAR("Compra autorizada")

    }
    SINO {

        MOSTRAR("Compra rechazada")

    }

## 17.6 Café con leche

    SI (tieneLeche == VERDADERO) {

        MOSTRAR("Preparando café con leche")

    }

## 17.7 Control de calidad

    SI (calidadCafe >= 80) {

        MOSTRAR("Café aprobado")

    }
    SINO {

        CANCELAR

    }

## 17.8 Preparación completa

    SI (cafeTostado == VERDADERO Y
        cafeMolido == VERDADERO Y
        pedidoPreparado == VERDADERO) {

        SERVIR

    }

---

# 18. Precio con beneficios

CafeLang permite crear reglas utilizando diferentes rangos.

    FUNCION precioConBeneficio(DECIMAL precio, ENTERO puntos) {

        SI (puntos >= 1000) {
            RETORNAR precio * 0.80
        }

        SI (puntos >= 500) {
            RETORNAR precio * 0.90
        }

        RETORNAR precio
    }

---

# 19. Validación de pedidos

Ejemplo de validación de cantidad:

    ENTERO cantidad

    LEER(cantidad)

    SI (cantidad >= 1 Y cantidad <= 10) {

        MOSTRAR("Cantidad válida")

    }
    SINO {

        MOSTRAR("Cantidad inválida")

    }

---

# 20. Comentarios

CafeLang permite comentarios de una línea y comentarios multilínea.

## 20.1 Comentario de una línea

    // Verificar disponibilidad

    SI (cafeDisponible == VERDADERO) {
        MOSTRAR("Disponible")
    }

## 20.2 Comentario multilínea

    /*
       Proceso de preparación
       del café
    */

    PREPARAR

Los comentarios son ignorados por el analizador léxico y no forman parte del AST.

---

# 21. Convenciones

- Las palabras reservadas se escriben en MAYÚSCULAS.
- Las variables utilizan camelCase.
- Las funciones utilizan camelCase.
- Las cadenas utilizan comillas dobles.
- Los valores booleanos utilizan VERDADERO y FALSO.
- Los bloques utilizan llaves `{ }`.
- La indentación recomendada es de 4 espacios.
- Los identificadores deben comenzar con una letra.
- Los identificadores pueden contener letras, números y `_`.
- Una palabra reservada no puede utilizarse como identificador.
- Los nombres de variables deben ser descriptivos.

Ejemplo correcto:

    precioCafe >= 5000

Ejemplo de estilo recomendado:

    temperaturaAgua >= 85 Y temperaturaAgua <= 95

---

# 22. Identificadores

Los identificadores representan nombres de variables y funciones.

Ejemplos válidos:

    precioCafe
    cantidadTazas
    total
    calcularTotal
    nombreCliente
    temperaturaAgua

Ejemplos inválidos:

    123precio
    500
    SI
    FUNCION

Los dos últimos son inválidos porque son palabras reservadas.

---

# 23. Literales

CafeLang reconoce diferentes tipos de valores.

## 23.1 Enteros

    0
    1
    10
    500
    8500

## 23.2 Decimales

    1.5
    0.90
    8500.0
    92.5

## 23.3 Cadenas

    "CafeLang"
    "Café listo"
    "Pedido realizado correctamente"

## 23.4 Booleanos

    VERDADERO
    FALSO

---

# 24. Tokens y análisis léxico

El lexer transforma el código fuente en una secuencia de tokens.

Ejemplo:

    SI (puntosCliente >= 500) {
        MOSTRAR("Cliente frecuente")
    }

El lexer reconoce:

    SI                  -> PALABRA_RESERVADA
    (                   -> PAREN_IZQ
    puntosCliente       -> IDENTIFICADOR
    >=                  -> OPERADOR_RELACIONAL
    500                 -> NUMERO_ENTERO
    )                   -> PAREN_DER
    {                   -> LLAVE_IZQ
    MOSTRAR             -> PALABRA_RESERVADA
    (                   -> PAREN_IZQ
    "Cliente frecuente" -> CADENA
    )                   -> PAREN_DER
    }                   -> LLAVE_DER

---

# 25. Análisis sintáctico

El parser recibe los tokens generados por el lexer y comprueba que respeten la gramática de CafeLang.

Ejemplo:

    SI (cafeDisponible == VERDADERO) {
        MOSTRAR("Disponible")
    }

El parser debe reconocer la estructura:

    SI
    (
    expresion_logica
    )
    {
    bloque
    }

Si la estructura no cumple la gramática, se genera un error sintáctico.

Ejemplo incorrecto:

    SI cafeDisponible == VERDADERO {
        MOSTRAR("Disponible")
    }

El error se produce porque falta la estructura:

    SI (condicion)

---

# 26. AST

El AST, o Árbol de Sintaxis Abstracta, representa la estructura lógica del programa.

Ejemplo:

    SI (cafeDisponible == VERDADERO) {
        MOSTRAR("Café disponible")
    }

Conceptualmente:

    CONDICIONAL
    |
    +-- CONDICION
    |   |
    |   +-- COMPARACION
    |       |
    |       +-- cafeDisponible
    |       +-- ==
    |       +-- VERDADERO
    |
    +-- ENTONCES
        |
        +-- MOSTRAR
            |
            +-- "Café disponible"

---

# 27. Validación semántica

Después del análisis sintáctico se realiza la validación semántica.

La validación semántica comprueba:

- Que las variables hayan sido declaradas.
- Que las variables se utilicen con tipos compatibles.
- Que las funciones existan.
- Que los parámetros tengan tipos correctos.
- Que las funciones reciban la cantidad correcta de argumentos.
- Que RETORNAR sea utilizado dentro de una función.
- Que las operaciones sean compatibles con los tipos.
- Que no se utilicen palabras reservadas como identificadores.

Ejemplo incorrecto:

    ENTERO cantidad = "cafe"

El valor `"cafe"` es TEXTO y la variable espera un ENTERO.

---

# 28. Tabla de símbolos

La tabla de símbolos almacena información sobre los identificadores encontrados durante el análisis.

Ejemplo:

    | Nombre           | Tipo       | Categoría |
    |------------------|------------|-----------|
    | cantidadTazas    | ENTERO     | Variable  |
    | precioCafe       | DECIMAL    | Variable  |
    | nombreCliente    | TEXTO      | Variable  |
    | cafeDisponible   | BOOLEANO   | Variable  |
    | calcularTotal    | DECIMAL    | Función   |

La tabla de símbolos permite controlar declaraciones, tipos, funciones y ámbitos.

---

# 29. Proceso completo del lenguaje

El procesamiento de CafeLang sigue el siguiente flujo:

    Código fuente
          |
          v
        Lexer
          |
          v
        Tokens
          |
          v
        Parser
          |
          v
         AST
          |
          v
    Tabla de símbolos
          |
          v
    Análisis semántico
          |
          v
       Ejecución

## 29.1 Lexer

Reconoce:

- Palabras reservadas.
- Identificadores.
- Números.
- Cadenas.
- Operadores.
- Símbolos.
- Comentarios.

## 29.2 Parser

Comprueba que los tokens respeten la gramática.

## 29.3 AST

Representa la estructura del programa.

## 29.4 Análisis semántico

Comprueba la coherencia del programa.

## 29.5 Ejecución

Interpreta el AST y ejecuta las instrucciones.

---

# 30. Ejemplo completo

    ENTERO cantidadTazas
    DECIMAL precioCafe
    DECIMAL total
    BOOLEANO cafeDisponible
    BOOLEANO cafeMolido
    BOOLEANO aguaDisponible
    ENTERO puntosCliente
    DECIMAL saldoCliente

    cantidadTazas = 2
    precioCafe = 8500.0
    cafeDisponible = VERDADERO
    cafeMolido = VERDADERO
    aguaDisponible = VERDADERO
    puntosCliente = 650
    saldoCliente = 20000.0

    SI (cafeDisponible == VERDADERO Y cantidadTazas > 0) {

        total = calcularTotal(cantidadTazas, precioCafe)

        SI (saldoCliente >= total) {

            SI (cafeMolido == VERDADERO Y aguaDisponible == VERDADERO) {

                PREPARAR

                SERVIR

                pedidoPreparado = VERDADERO

                MOSTRAR("Pedido realizado correctamente")
                MOSTRAR(total)

            }
            SINO {

                MOSTRAR("No se puede preparar el pedido")

            }

        }
        SINO {

            MOSTRAR("Saldo insuficiente")

        }

    }
    SINO {

        MOSTRAR("No es posible realizar el pedido")

    }

---

# 31. Ejemplo completo con funciones

    FUNCION calcularTotal(ENTERO cantidad, DECIMAL precio) {

        RETORNAR cantidad * precio

    }

    FUNCION calcularDescuento(DECIMAL precio, ENTERO puntos) {

        SI (puntos >= 500) {

            RETORNAR precio * 0.90

        }

        RETORNAR precio
    }

    ENTERO cantidadTazas = 3
    DECIMAL precioCafe = 8500.0
    ENTERO puntosCliente = 600

    DECIMAL total
    DECIMAL precioFinal

    total = calcularTotal(cantidadTazas, precioCafe)

    precioFinal = calcularDescuento(total, puntosCliente)

    MOSTRAR("Total:")
    MOSTRAR(total)

    MOSTRAR("Precio final:")
    MOSTRAR(precioFinal)

---

# 32. Ejemplo de proceso de preparación

    BOOLEANO cafeTostado = FALSO
    BOOLEANO cafeMolido = FALSO
    BOOLEANO aguaDisponible = VERDADERO
    BOOLEANO pedidoPreparado = FALSO

    TOSTAR

    cafeTostado = VERDADERO

    SI (cafeTostado == VERDADERO) {

        MOLER

        cafeMolido = VERDADERO
    }

    SI (cafeMolido == VERDADERO Y aguaDisponible == VERDADERO) {

        PREPARAR

        pedidoPreparado = VERDADERO
    }

    SI (pedidoPreparado == VERDADERO) {

        SERVIR

        MOSTRAR("Café servido")

    }

---

# 33. Ejemplo con ciclo

    ENTERO cantidadTazas = 5
    ENTERO tazasServidas = 0

    MIENTRAS (tazasServidas < cantidadTazas) {

        SERVIR

        tazasServidas = tazasServidas + 1

    }

    MOSTRAR("Todas las tazas fueron servidas")

---

# 34. Ejemplo con entrada del usuario

    ENTERO cantidadTazas

    MOSTRAR("Ingrese la cantidad de tazas:")

    LEER(cantidadTazas)

    SI (cantidadTazas >= 1 Y cantidadTazas <= 10) {

        MOSTRAR("Cantidad válida")

        MIENTRAS (cantidadTazas > 0) {

            SERVIR

            cantidadTazas = cantidadTazas - 1

        }

    }
    SINO {

        MOSTRAR("La cantidad debe estar entre 1 y 10")

    }

---

# 35. Ejemplo de reglas combinadas

    ENTERO cantidadTazas
    DECIMAL precioCafe
    DECIMAL total
    DECIMAL precioFinal
    ENTERO puntosCliente
    DECIMAL saldoCliente

    BOOLEANO cafeDisponible
    BOOLEANO cafeTostado
    BOOLEANO cafeMolido
    BOOLEANO aguaDisponible
    BOOLEANO tieneCupon
    BOOLEANO pedidoPreparado

    cantidadTazas = 2
    precioCafe = 8500.0
    puntosCliente = 700
    saldoCliente = 20000.0

    cafeDisponible = VERDADERO
    cafeTostado = VERDADERO
    cafeMolido = VERDADERO
    aguaDisponible = VERDADERO
    tieneCupon = FALSO
    pedidoPreparado = FALSO

    SI (cafeDisponible == VERDADERO) {

        total = calcularTotal(cantidadTazas, precioCafe)

        precioFinal = calcularDescuento(total, puntosCliente)

        SI (saldoCliente >= precioFinal O tieneCupon == VERDADERO) {

            SI (cafeTostado == VERDADERO Y
                cafeMolido == VERDADERO Y
                aguaDisponible == VERDADERO) {

                PREPARAR

                pedidoPreparado = VERDADERO

                SERVIR

                MOSTRAR("Pedido completado")
                MOSTRAR(precioFinal)

            }
            SINO {

                MOSTRAR("El café no está listo para preparar")

            }

        }
        SINO {

            MOSTRAR("No hay saldo suficiente")

        }

    }
    SINO {

        MOSTRAR("El café no está disponible")

    }

---

# 36. Errores del lenguaje

CafeLang puede clasificar los errores en diferentes categorías.

## 36.1 Error léxico

Se produce cuando aparece un símbolo o token no reconocido.

Ejemplo:

    precioCafe = 8500 @

El carácter `@` no pertenece al alfabeto definido para CafeLang.

## 36.2 Error sintáctico

Se produce cuando los tokens no respetan la gramática.

Ejemplo:

    SI cafeDisponible == VERDADERO {

        MOSTRAR("Disponible")

    }

Faltan los paréntesis de la condición.

## 36.3 Error semántico

Se produce cuando la estructura es sintácticamente correcta pero no tiene sentido según las reglas del lenguaje.

Ejemplo:

    ENTERO cantidad = "dos"

La variable es ENTERO pero se intenta asignar una cadena.

---

# 37. Alfabeto de CafeLang

El alfabeto representa el conjunto de símbolos que pueden formar parte del lenguaje.

Conceptualmente:

    Σ = {
        letras,
        dígitos,
        operadores,
        delimitadores,
        comillas,
        espacios,
        saltos de línea
    }

CafeLang utiliza estos símbolos para construir tokens, expresiones y estructuras sintácticas.

---

# 38. Cadenas

Una cadena es una secuencia finita de símbolos pertenecientes al alfabeto.

Ejemplos:

    "CafeLang"

    "Café listo"

    "Pedido realizado correctamente"

Las cadenas se representan mediante comillas dobles.

---

# 39. Lenguaje formal

CafeLang puede definirse formalmente como un conjunto de cadenas válidas que cumplen las reglas de su gramática.

Una cadena pertenece al lenguaje si:

1. Sus caracteres pertenecen al alfabeto permitido.
2. Puede ser dividida correctamente en tokens.
3. Los tokens cumplen la gramática.
4. Las estructuras son semánticamente válidas.

Por lo tanto:

    L(CafeLang) = { cadenas válidas según la gramática de CafeLang }

---

# 40. Objetivo del proyecto

CafeLang busca ser un lenguaje pequeño pero suficientemente completo para demostrar los principales conceptos de Lenguajes Formales y Compiladores:

    Alfabeto
    Cadenas
    Lenguaje formal
    Tokens
    Análisis léxico
    Gramática
    Análisis sintáctico
    AST
    Tabla de símbolos
    Análisis semántico
    Ejecución

El contexto de cafetería permite representar reglas reales mediante instrucciones como:

    PREPARAR
    MOLER
    TOSTAR
    SERVIR
    CANCELAR

Además, CafeLang incorpora características generales de un lenguaje de programación:

    Variables
    Tipos de datos
    Operadores
    Condicionales
    Ciclos
    Funciones
    Parámetros
    Retorno de valores
    Entrada de datos
    Salida de datos
    Comentarios
    Validación semántica

---

# 41. Resumen de CafeLang

CafeLang es un lenguaje de programación de propósito educativo orientado al dominio de una cafetería.

Su estructura permite pasar desde los conceptos fundamentales de lenguajes formales hasta la ejecución de programas.

El flujo principal es:

    ALFABETO
       |
       v
    CADENAS
       |
       v
    TOKENS
       |
       v
    GRAMÁTICA
       |
       v
    PARSER
       |
       v
      AST
       |
       v
    TABLA DE SÍMBOLOS
       |
       v
    ANÁLISIS SEMÁNTICO
       |
       v
    EJECUCIÓN

De esta manera, CafeLang no se limita a imprimir mensajes, sino que permite construir programas con lógica, operaciones matemáticas, variables, funciones, condiciones, ciclos y reglas propias del dominio de una cafetería.
