<style>
    .correct_code {
        border-left: 4px solid #4CAF50; /* Green color for left border */
        background-color: #E8F5E9; /* Light green background color */
        padding: 10px; /* Add padding for better appearance */
        margin-bottom: 20px; /* Add margin for spacing */
    }
    .wrong_code {
        border-left: 4px solid #FF5722; /* Red color for left border */
        background-color: #FFEBEE; /* Light red background color */
        padding: 10px; /* Add padding for better appearance */
        margin-bottom: 20px; /* Add margin for spacing */
    }
</style>

## PEP 8 - normas para códigos en Python

> :memo: **Note:** Guia rápida de PEP 8 basada en el ensayo de Guido van Rossum. 
    https://peps.python.org/pep-0008/
    
---
## Parte 1 - Diseño del código
### Indentación
*Usa 4 espacios por nivel de sangría.*

Cuando se usa la ¨sangría colgante¨, se debe considerar lo siguiente: 
- No debe haber argumentos en la primera línea y se debe usar una sangría adicional en la siguiente linea para distinguirla claramente como una línea de continuación.

<div class="correct_code">
    <strong>Correct:</strong>

```bash 
    # Alineado con el delimitador de apertura.
    foo = nombre_de_funcion_larga(var_uno, var_dos,
                                  var_tres, var_cuatro)

    # Añadir 4 espacios (un nivel extra de sangría) para distinguir los argumentos del resto.
    def nombre_de_funcion_larga(
                var_uno, var_dos, var_tres,
                var_cuatro):
        print(var_uno)

    # Las sangrías colgantes deben agregar un tab.
    foo = nombre_de_funcion_larga(
        var_uno, var_dos,
        var_tres, var_cuatro)
```
</div>


<div class="wrong_code">
    <strong>Warning:</strong> 


```bash 
    # Argumentos en la primera línea prohibidos cuando no se utiliza alineación vertical.
    foo = long_function_name(var_one, var_two,
        var_three, var_four)
    # Se requiere una sangría adicional ya que la sangría no es distinguible.
    def long_function_name(
        var_one, var_two, var_three,
        var_four):
        print(var_one)
```
</div>

### Que pasa cuando la condicion del <ins>"if"</ins> es muy larga? 
Debemos usar el mismo concepto de 4 espacios por nivel de sangria. Algunos dejemplos de usos son 

<div class="correct_code">
    <strong>Correct:</strong>

```bash 
    # Sin sangría adicional.
    if (esto_es_una_cosa and
        eso_es_otra_cosa):
        hacer_algo()

    # Agrega un comentario, que proporcionará cierta distinción en editores
    # que admiten resaltado de sintaxis.
    if (esto_es_una_cosa and
        eso_es_otra_cosa):
        # Dado que ambas condiciones son verdaderas, podemos hacer algo.
        hacer_algo()

    # Agrega algo de sangría adicional en la línea de continuación condicional.
    if (esto_es_una_cosa
            and eso_es_otra_cosa):
        hacer_algo()
```
</div>

> :eyes: **tip:** Podemos colocar el <ins> parentesis ()</ins> de cualquier forma. 
```bash 
    my_list = [
        1, 2, 3,
        4, 5, 6,
        ]
    result = some_function_that_takes_arguments(
        'a', 'b', 'c',
        'd', 'e', 'f',
    )
```
---
## Recomendations
### *Limite máximo de lineas

- Usar limite máximo de **79 caracteres**. 
- Para textos largos como <ins>comentarios o docstrings</ins> se recomienda usar maximo 72 caracteres
- Ajustar el acho de tu editor de texto a máximo 80 caracteres por practicidad. O simplemente tener
    un archivo a lado de otro como guia. 
- Existen algunos casos especiales donde dentro de equipos de trabajo se determina como limite **99 caracteres** por mantenimiento. 
- Se puede realizar esta separación usando paréntesis, llaves y corchetes.

> :eyes: **tip:** Comunmente se usan barras invertidas ( \ ) para realizar el salto de linea. 
```bash 
    with open('/path') as file_1, \
     open('/path', 'w') as file_2:
    file_2.write(file_1.read())
```

### ¿Qué hacer en caso de operadores binarios?
*¿El quiebre de línea debería ser antes o después?*

<div class="wrong_code">
    <strong>Warning: Salto de línea despues del operador</strong> 

```bash 
    income = (gross_wages +
              taxable_interest +
              (dividends - qualified_dividends) -
              ira_deduction -
              student_loan_interest)
```
</div>

<div class="correct_code">
    <strong>Correct: Salto de línea antes del operador</strong>

```bash 
    # easy to match operators with operands
    income = (gross_wages
              + taxable_interest
              + (dividends - qualified_dividends)
              - ira_deduction
              - student_loan_interest)
```
</div>

### ¿Qué hacer en caso de operadores binarios?
| Tipo                                  | 3 lineas en blanco    |
|-----------                            |--------------------   |
| Definicion de Funcioness              |        2              |
| Definicion Clases                     |        2              |
| Método de una Clase                   |        1              |
| Grupos de Funciones Relacionadas      | ------------          |
| Secciones Logicas Dentro de Funciones |       1-3             |

### Usar identificadores UTF-8 (ASCII)

### Importar 
- Importar siempre cada bilbioteca en lineas separadas
- Siempre debe estar ubicado en el header del programa. Siguiendo el siguiente orden:
    1. importar biblioteca estandar.
    2. Importar bliotecas externas (third party).
    3. Importar biblioteca/aplicación local.
    **(Linea en blanco entre cada categoria)**
- Cuando se quiera importar clases de modulo contenedor-clase importar directamente el modulo 
```bash 
    import myclass
    import foo.bar.yourclass
```
>❗❗❗ **Atención:** Importar de esta forma``` [from <module> import *]``` debe ser <ins>evitado</ins>. Comunmente se usa para coger importar todo. Pero a largo plazo resulta confuso para el lector y es dificil identificar que y para que se esta usando esa biblioteca en el codigo. 

