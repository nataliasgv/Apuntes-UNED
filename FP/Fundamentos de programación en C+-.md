  # Tema 1 Introducción

Desde el punto de vista del control de su funcionamiento, podemos clasificar las máquinas en diferentes tipos.

Las _máquinas no automáticas_, o de control manual, son gobernadas por un operador o agente externo que desencadena unas determinadas operaciones en cada momento. Por ejemplo, una máquina de escribir imprime las letras o mueve el papel de acuerdo con las teclas pulsadas por el mecanógrafo.

Las _máquinas automáticas_ actúan por sí solas, sin necesidad de operador, aunque pueden responder a estímulos externos. Por ejemplo, un ascensor automático gobierna por sí mismo los movimientos de subida y bajada incluyendo cambios de velocidad, apertura y cierre de puertas, etc., de forma coordinada, respondiendo a los estímulos de los botones de llamada o envío a un piso dado. En este caso el comportamiento de la máquina será fijo , en el sentido de que a unos determinados estímulos externos responderá siempre de la misma manera.

Otras máquinas automáticas se denominan programables, y su comportamiento no es siempre el mismo. Una máquina programable se puede concebir como una máquina base, de comportamiento fijo, que se completa con una parte modificable que describe el funcionamiento de la máquina base. Esta parte modificable se denomina _programa_.

Una máquina programable se comporta, por tanto, como diferentes máquinas particulares, en función del programa utilizado.

Cuando una máquina programable opera bajo control de un programa determinado, se dice que el programa se ejecuta en dicha máquina.
## **1.1.2 Concepto de cómputo**

La palabra cómputo es sinónimo de cuenta o cálculo. En informática y de una forma general puede identificarse el concepto de cómputo con el de tratamiento de la información.
## **1.1.3 Concepto de computador**

La máquina programable por excelencia es el computador. Un computador se define como una máquina programable para tratamiento de la información, es decir, un computador es una máquina para realizar cómputos. 

Un computador, pose unos elementos fijos (máquina base) y otros modificables (programa). De forma simplificada podemos asociar los elementos fijos a los dispositivos físicos del computador, que constituyen el hardware, y los elementos modificables a las representaciones de los programas en sentido amplio, que constituyen el software.

Los computadores actuales corresponden a un tipo particular de máquinas programables que se denominan _máquinas de programa almacenado_. En estas máquinas la modificación del programa no implica un cambio de componentes físicos de la máquina, sino que estas máquinas poseen una memoria en la cual se puede almacenar información de cualquier tipo.
![[Pasted image 20241129191832.png]]
## **1.2 Programación e ingeniería de software**

Para realizar un determinado tratamiento de información con ayuda de un computador habrá sido necesario:

 (a) Construir el computador (hardware).

 (b) Idear y desarrollar el programa (software;).

(c) Ejecutar dicho programa en el computador. Sólo la última fase (c) es habitualmente realizada por el usuario. Las dos primeras corresponden a los profesionales de la informática

### **1.2.2 Objetivos de la programación**

Entre los objetivos particulares de la programación podemos reconocer los siguientes:

 • CORRECCIÓN: Es evidente que un programa debe realizar el tratamiento esperado, y no producir resultados erróneos. Esto tiene una consecuencia inmediata que no siempre se considera evidente: antes de desarrollar un programa debe especificarse con toda claridad cuál es el funcionamiento esperado. Sin dicha especificación es inútil hablar de funcionamiento correcto.

• CLARIDAD: Prácticamente todos los programas han de ser modificados después de haber sido desarrollados inicialmente. Por esta razón es fundamental que sus descripciones sean claras y fácilmente inteligibles por otras personas distintas de su autor, o incluso por el mismo autor al cabo de un cierto tiempo, cuando ya ha olvidado los detalles del programa.

• EFICIENCIA: Una tarea de tratamiento de información puede ser programada de muy diferentes maneras sobre un computador determinado, es decir, habrá muchos programas distintos que producirán los resultados deseados. Algunos de estos programas serán más eficientes que otros. Los programas eficientes aprovecharán mejor los recursos disponibles y, por tanto, su empico será más económico en algún sentido.

Si se trata de establecer una importancia relativa entre los distintos objetivos, habría que considerar como prioritaria la corrección, a continuación, debe perseguirse la claridad y finalmente ha de atenderse a la eficiencia.

## **1.3 Lenguajes de programación**

La forma de codificar programas de una máquina en particular se dice que es su código de máquina o lenguaje de máquina.

s. En particular los lenguajes de programación sirven precisamente para representar programas de manera simbólica, en forma de un texto que puede ser leído con relativa facilidad por una persona. Además, los lenguajes de programación son formas de representación prácticamente independientes de las máquinas particulares que se vayan a usar.

## **1.4 Compiladores e Intérpretes**

Existen diferentes estrategias para conseguir ejecutar en una máquina determinada un programa escrito en un lenguaje de programación simbólico. Normalmente se basan en el uso de programas especiales que realizan un tratamiento de la información en forma de texto que representa el programa en el lenguaje de programación simbólico. Estos programas para manipular representaciones de programas los denominaremos _procesadores de lenguajes_.

==Un _compilador_ es un programa que traduce programas de un lenguaje de programación simbólico a código de máquina. A la representación del programa en lenguaje simbólico se le llama _programa fuente_, y en su representación en código de maquina se le llama _programa objeto_. Análogamente al lenguaje simbólico y al lenguaje máquina se les llama también _lenguaje fuente_ y _lenguaje objeto_, respectivamente.==

La ejecución del programa mediante compilador exige al menos dos etapas separadas, tal como se indica en la figura L8. En la primera de ellas se traduce el programa simbólico a código de máquina. En la segunda etapa se ejecuta ya directamente el programa en código de máquina y se procesan los datos y resultados particulares.

==Un _intérprete_ es un programa que analiza directamente la descripción simbólica del programa fuente y realiza las operaciones oportunas. Puede decirse que el intérprete es (o simula) una máquina virtual cuyo lenguaje de máquina coincide con el lenguaje fuente. El proceso de un programa mediante intérprete se limita a ejecutar directamente el programa en la máquina virtual, es decir, sobre el intérprete.==

El proceso mediante intérprete es más sencillo, en conjunto, que, mediante compilador, ya que no hay que realizar dos fases separadas. Su principal inconveniente es que la velocidad de ejecución es más lenta, ya que al tiempo Que se van tratando los datos de la aplicación hay que ir haciendo el análisis e interpretación de las operaciones descritas en el programa fuente.

## **1.5 Modelos abstractos de cómputo**

Si de un conjunto de lenguajes de programación basados en elementos computacionales similares extraemos los conceptos comunes, obtendremos un modelo abstracto de cómputo. Este modelo abstracto recoge los elementos básicos y formas de combinación de una manera abstracta, prescindiendo de la notación concreta usada en cada lenguaje de programación para representarlos.

Existen diversos modelos abstractos de cómputo, o modelos de programación, que subyacen en los lenguajes de programación actuales. Entre ellos están la programación funcional, programación lógica, programación imperativa, modelo de flujo de datos, programación orientada a objetos, etc. Todos estos modelos son modelos universales, en el sentido de que pueden utilizarse para describir cualquier cómputo intuitivamente posible.

### **1.5.1 Modelo funcional**

El modelo de _programación funcional_ se basa casi exclusivamente en el empleo de funciones. Una función es una aplicación, que hace corresponder un elemento de un conjunto de destino (resultado) a cada elemento de un conjunto de partida (argumento) para el que la función esté definida.

Por ejemplo, la operación de suma de números enteros es una función en que el conjunto de partida es el de las parejas de números enteros y el de destino es el conjunto de los números enteros. A cada pareja de enteros se le hace corresponder un entero, que es su suma.

El proceso de cómputo llamado reducción, se basa en reemplazar progresivamente cada función por el resultado de la misma. Este sistema de evaluación por sustitución es la base del llamado cálculo-λ.

Cuando en un cómputo intervienen funciones definidas, la evaluación se sigue haciendo por sustitución. El proceso, llamado reescritura, consiste en reemplazar una función por su definición, sustituyendo los argumentos simbólicos en la definición por los argumentos reales en el cómputo.
![[Pasted image 20241203154602.png]]
### **1.5.2 Modelo de flujo de datos**

En este modelo de cómputo, un programa corresponde a una red de operadores interconectados entre sí. Cada operador lo representaremos gráficamente mediante un cuadrado con entradas y salidas, y dentro de él el símbolo de la operación que realiza. Un operador espera hasta tener valores presentes en sus entradas, y entonces se activa él solo, consume los valores en las entradas, calcula el resultado, y lo envía a la salida. Después de esto vuelve a esperar que le lleguen nuevos valores por las entradas.
![[Pasted image 20241203154624.png]]
Una red de flujo de datos puede organizarse de manera que opere de forma iterativa, obteniendo no ya un resultado sino una serie de ellos. Por ejemplo, la red de la figura 1.13 produce la serie de números naturales, a base de reciclar sobre sí mismo un operador de incremento.
![[Pasted image 20241203154632.png]]
### **1.5.3 Modelo de programación lógica**

Este modelo abstracto de cómputo corresponde plenamente a lo que se denomina programación declarativa. Un programa consiste en plantear de manera formal un problema a base de declarar una serie de elementos conocidos, y luego preguntar por un resultado, dejando que sea la propia máquina la que decida cómo obtenerlo. En programación lógica los elementos conocidos que pueden declararse son hechos y reglas. Un hecho es una relación entre objetos concretos. Una regla es una relación general entre objetos que cumplen ciertas propiedades. Una relación entre objetos la escribiremos poniendo el nombre de dicha relación y luego los objetos relacionados entre paréntesis. Por ejemplo: Hijo( Juan, Luis) significaría que Juan es hijo de Luis.

Para realizar una consulta escribiremos el esquema de un hecho en que alguno de los elementos sea desconocido. Esto lo indicaremos usando nombres de incógnitas en minúscula, para distinguirlos de los nombres de elementos conocidos, que en este caso se habían escrito en mayúsculas (en lenguaje Prolog se usa el convenio contrario). La consulta será respondida indicando todos los valores posibles que puedan tomar las incógnitas.

| Consulta       | Respuesta                                      |
| -------------- | ---------------------------------------------- |
| Hijo( x, Ana ) |  x = Felipe<br><br> x = Juan<br><br> x = Sonia |

La verdadera potencia de la programación lógica aparece cuando declaramos reglas. Al realizar consultas basadas en reglas la máquina realiza automáticamente las inferencias (deducciones) necesarias para responderla. Por ejemplo, usando el símbolo ":-" para definir una regla, escribiremos:

Reglas

 Padre ( x, y ) :- Hijo( y, x )

Hermano( x, y ) :- Hijo( x, z ), Hijo( y, z )

La primera regla se limita a nombrar la relación inversa de "hijo". La segunda expresa que dos personas son hermanas si son hijas de un mismo padre o madre.

### **1.5.4 Modelo imperativo**

==El modelo de programación imperativa responde a la estructura interna habitual de un computador, que se denomina arquitectura Von Neumann. Un programa en lenguaje de máquina aparece como una lista de instrucciones u órdenes elementales que han de ejecutarse una tras otra, en el orden en que aparecen en el programa. El orden de ejecución puede alterarse en caso necesario mediante el uso de instrucciones de control.==

==Las instrucciones de un programa imperativo utilizan datos almacenados en la memoria del computador. Esta capacidad de almacenamiento de valores se representa en los programas imperativos mediante el uso de 1luriables. Una variable no tiene aquí el mismo significado que en matemáticas, sino que representa un dato almacenado bajo un nombre dado.==

==Un programa imperativo se plantea como el cálculo o modificación de sucesivos valores intermedios hasta obtener el resultado final. Las instrucciones típicas de un programa imperativo son las de asignación, que consisten en obtener un resultado parcial mediante un cálculo elemental que puede ser realizado por la máquina, y que se almacena en una variable para ser utilizado posteriormente. En los lenguajes de programación simbólicos las instrucciones y órdenes se denominan sentencias. En C± y otros lenguajes similares la sentencia de asignación se representa de la forma variable = expresión==

## **1.6 Elementos de la programación imperativa**

### **1.6.1 Procesador, entorno, acciones**

La idea abstracta correspondiente al concepto físico de máquina es el procesador. Definiremos como procesador a todo agente capaz de entender las órdenes del problema y ejecutarlas. El procesador es esencialmente un elemento de control. Para ejecutar las instrucciones empleará los recursos necesarios, que formarán parte del sistema en el cual se ejecute el programa. Por ejemplo, se necesitarán dispositivos de almacenamiento para guardar datos que habrán de ser utilizados posteriormente, o dispositivos de entrada-salida que permitirán tomar datos de partida del exterior y presentar los resultados del programa. Todos estos elementos disponibles para ser utilizados por el procesador constituyen el entorno.

### **1.6.2 Acciones primitivas. Acciones compuestas**

Las acciones que son directamente realizables por el procesador se denominan acciones primitivas. El planteamiento razonable de un programa complejo debe pasar por usar la idea de abstracción para limitar la complejidad de detalles al estudiar el programa en su conjunto. Es muy útil usar la idea de acción compuesta corno abstracción equivalente a un fragmento de programa más o menos largo que realiza una operación bien definida.

La descripción de un programa en términos de acciones compuestas puede facilitar su comprensión. Por supuesto, al desarrollar el programa habrá sido preciso describir o descomponer las acciones compuestas en otras más sencillas, hasta llegar finalmente a acciones primitivas, que son las que realmente podrá ejecutar el procesador.

### **1.6.3 Esquemas de acciones**

En particular, la llamada programación estructurada sugiere el uso de tres esquemas generales denominados secuencia, selección e iteración, con los cuales (junto con la definición de operaciones abstractas) se puede llegar a desarrollar de forma comprensible un programa tan complicado como sea necesario.

## **1. 7 Evolución de la programación**

### **1.7.1 Evolución comparativa Hardware/ Software**

Los primeros computadores eran máquinas extraordinariamente costosas, y con una capacidad que hoy día consideraríamos ridículamente limitada, como consecuencia de ello la finalidad principal de la programación era obtener el máximo rendimiento de los computadores. Los programas se escribían directamente en el lenguaje de la máquina, o a lo sumo en un lenguaje ensamblador en que cada instrucción de máquina se representaba simbólicamente mediante un código nemotécnico para facilitar la lectura del programa. Simplemente se consideraba que el mejor programa era el que realizaba el trabajo en menos tiempo y usando el mínimo de recursos de la máquina.

Ya no tiene sentido dedicar un gran esfuerzo a conseguir programas eficientes. Es más barato desarrollar programas relativamente más simples, aunque no aprovechen muy bien los recursos de la máquina, y comprar un computador de mayor potencia de proceso que compense esa posible falta de eficiencia. Los lenguajes de programación simbólicos han facilitado extraordinariamente las tarcas de programación, al poder invocar en un programa operaciones cada vez más complejas como acciones primitivas. De esta manera se reduce el volumen total del programa medido en número de instrucciones, que ahora pasan a ser sentencias del lenguaje simbólico.

# Tema 2 Elementos básicos de programación

## **2.2 Notación BNF**

Notación BNF (Backus-Naur Form) basada en la descripción de cada elemento gramatical en función de otros más sencillos, según determinados esquemas o construcciones. Cada uno de estos esquemas se define mediante una regla de producción.

Estas reglas sobre cómo han de escribirse los elementos del lenguaje en forma de símbolos utilizan a su vez otros símbolos, que se denominan metasímbolos. Son los siguientes:

 ==**: : =** Metasímbolo de definición. Indica que el elemento a su izquierda puede desarrollarse según el esquema de la derecha.==

==|  Metasímbolo de alternativa. Indica que puede elegirse uno y sólo uno de los elementos separados por este metasímbolo.==

==**{ }** Metasímbolos de repetición. Indican que los elementos incluidos dentro de ellos se pueden repetir cero o más veces.==

==**[ ]** Metasímbolos de opción. Indican que los elementos incluidos dentro de ellos pueden ser utilizados o no.==

==**( )** Metasímbolos de agrupación. Agrupan los elementos incluidos en su interior.==

También se emplearán distintos estilos de letra para distinguir los elementos simbólicos siguientes:

 ==_Elemento_no_terminal_ Este estilo se emplea para escribir el nombre de un elemento gramatical que habrá de ser definido por alguna regla. Cualquier elemento a la izquierda del metasímbolo **:: =** será no terminal y aparecerá con este estilo.==

==_Elemento_terminal_ Este estilo se emplea para representar los elementos que forman parte del lenguaje C±, es decir, que constituyen el texto de un programa. Si aparecen en una regla deberán escribirse exactamente como se indica.==

## **2.3 Valores y tipos**

Un _dato_ es un elemento de información que puede tomar un _valor_ entre varios posibles. Si un dato tiene siempre necesariamente un valor fijo, diremos que es una _constante._

En programación a las distintas clases de valores se les denomina _tipos_. Un dato tiene asociado un tipo, que representa la clase de valores que puede tomar. Por ejemplo, son tipos diferentes los números enteros, los días de la semana, etc.

Es importante destacar que el concepto de tipo es algo _abstracto_, e independiente de los símbolos concretos que se empleen para representar los valores. Por ejemplo, aunque podemos representar los meses del año mediante números enteros de 1 a 12, los meses no son números enteros, pues no tiene sentido, por ejemplo, sumar Enero (l) y Marzo (3) para obtener Abril (4). Con más precisión se habla de tipos abstractos de datos, que identifican tanto el conjunto de valores que pueden tomar los datos de ese tipo como las operaciones significativas que pueden hacerse con dichos valores.

## **2.4 Representación de valores constantes**

### **2.4.1 Valores numéricos enteros**

Los valores enteros representan un número exacto de unidades, y no pueden tener parte fraccionaria. Un _valor entero_ se escribe mediante una secuencia de uno o más dígitos del 0 al 9 sin separadores de ninguna clase entre ellos y precedidos opcionalmente de los símbolos más (+) o menos (- ).

Usando la notación BNF podernos representar de manera precisa las reglas para escribir estos valores:

 `Valor_entero :: = [ +׀-]Secuencia_ dígitos`

`Secuencia_ dígitos:: = Dígito{Dígito}`

`Dígito::= 0| 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 `

• NOTA: El lenguaje C± como derivado de C/ C+- considera que cuando el valor entero comienza. por un primer dígito 0 se está escribiendo en base 8 (octal) en lugar de en base 10 (decimal). Así, el valor número 020 es un número octal que equivale a 16 en decimal. En este curso no se hace uso de los valores octales y carece de sentido poner ceros a la izquierda de un valor numérico. En cualquier caso, el compilador de C/C+- da un error si al escribir un valor octal se utilizan los dígitos 8 ó 9.

### **2.4.2 Valores numéricos reales**

Los valores numéricos reales permiten expresar cualquier cantidad, incluyendo fracciones de unidad. Se pueden representar de dos maneras distintas: en la notación decimal habitual, o en la. notación científica. En la notación decimal habitual un _valor real_ se escribe con una parte entera terminada siempre por un punto (.), y seguida opcionalmente por una secuencia de dígitos que constituyen la parte fraccionaria decimal.

En la notación científica un número real se escribe como una _mantisa_, que es un número real en la notación decimal habitual, seguida de un factor de escala que se escribe como la letra E seguida del exponente entero de una potencia de 10 por la que se multiplica la mantisa. Son valores reales válidos en notación científica:

 - 23.2E+12 equivalente a -23.2x

A diferencia de los valores enteros, un mismo valor real puede tener muy diversas representaciones válidas. Por ejemplo, todas las representaciones siguientes corresponden al mismo valor:

 45.6         456.E-1       4.56E+l       45.60E+0       456000.00E-4

Las reglas anteriores, expresadas en notación BNF son:

`Valor_ real:: = Valor_ entero_ . [Secuencia_dígitos] [Escala]

`Escala:: = E _Valor_entero_`

### **2.4.3 Caracteres**

Dentro del texto de un problema en C± el valor de un carácter concreto se escribe poniendo dicho carácter entre apóstrofos ( ' ). Ejemplos de valores de caracteres Ron los siguientes:

 'a' 'A' 'Ñ' 'ñ' '7 ' '5 ' '?'

Es interesante hacer las siguientes observaciones: :

 • el espacio en blanco (' ') es un carácter válido como los demás

• hay que distinguir entre un valor entero de un dígito (p.ej. 7) y el carácter correspondiente a dicho dígito (p.ej. '7 ')

La colección o juego de caracteres (_charset_) que pueden manipularse en un programa depende de la máquina que se esté usando. Sólo se pueden representar de la forma indicada (escribiéndolos entre apóstrofos) aquellos caracteres que tengan asociado un símbolo gráfico (letra, dígito, signo de puntuación, etc.) que pueda introducirse en el texto del programa. Otros caracteres definidos, tales como los caracteres de control, que no tienen símbolo gráfico, se representan mediante una secuencia de escape con la siguiente notación:

'\n' Salto al comienzo de una nueva línea de escritura

'\r' Retorno al comienzo de la misma línea de escritura

'\ t ' Tabulación

'\ ' '  Apóstrofo

' \ \ ' Barra inclinada

'\f' Salto a una nueva página o borrado de pantalla

### **2.4.4 Cadenas de caracteres (_strings_)**

Una cadena de caracteres (en inglés string) se escribe como una secuencia de caracteres incluidos entre comillas ("). Por ejemplo: "Este texto es una cadena de caracteres "

Conviene observar que:

• si una cadena incluye comillas en su interior se escribirá mediante \ "

• no hay que confundir un valor de tipo carácter ( ' x ' ) con una cadena del mismo único carácter ("x" ). La distinción se produce por el delimitador utilizando comillas (") para una cadena y apóstrofo ( ' ) para un carácter

• es posible definir una cadena vacía que no contengan ningún carácter.

## **2.5 Tipos predefinidos**

Dentro de una misma clase de valores pueden distinguirse varios tipos diferentes, tanto a nivel de _tipos predefinidos en el lenguaje_, como de tipos definidos por el programador.

Recordaremos que un tipo de datos define:

1. Una colección de valores posibles

2. Las operaciones significativas sobre ellos

En el lenguaje C± hay cuatro tipos de datos predefinidos, que se designan con los nombres _int, float , char, bool_, así como mecanismos para definir nuevos tipos a partir de ellos. En los lenguajes e y C+ + hay tipos predefinidos adicionales.

### **2.5.1 El tipo entero (_int_)**

Los valores de este tipo son los valores numéricos enteros positivos y negativos. Como tipo abstracto su definición coincide con el concepto matemático de los números enteros. Sin embargo, dado el carácter físico de los computadores, el rango de valores nunca podrá ser infinito como se establece en el concepto matemático. En cada caso el rango de valores del tipo int depende de la plataforma (combinación de: procesador, sistema operativo y compilador) que se esté utilizando. En general se corresponde con el rango de valores que pueden manipularse con instrucciones básicas del lenguaje de máquina y viene a ser simétrico en torno al valor cero. Dentro de dicho rango la representación de cualquier valor es exacta. Son rangos comunes los siguientes:
![[Pasted image 20241203154848.png]]
Estos rangos obedecen a que los computadores suelen emplear la codificación en base 2 de los valores enteros. Para el signo del número se utiliza un bit, quedando, por tanto, 15, 31 ó 63 para el valor absoluto:

2^15= 32.768

2^31= 2.147.483.648

2^63= 9.223.372.036.854.775.808

• NOTA: Para facilitar la escritura de programas que tengan en cuenta la limitación particular de rango existente en cada caso, C y C++ permiten hacer referencia al valor mínimo mediante el nombre simbólico INT_MIN, y al valor máximo mediante INT_MAX. El rango admisible será, por tanlto: INT_MIN ... O ... INT_MAX. Estos nombres están definidos en el módulo limits de la librería estándar de C (cabecera <limits.h>)

Asociadas al tipo int están las operaciones que se pueden realizar con los valores de este tipo.

+ Suma de enteros a+b

 - Resta de enteros a -b

 * Multiplicación de enteros a * b

/ División de enteros a / b

% Resto de la división a % b

+ Identidad de un entero +a

- Cambio de signo de un entero – a

### **2.5.2 El tipo real (_float_)**

Con el tipo float se trata de representar en el computador los valores numéricos reales positivos y negativos. Sin embargo, al contrario que en caso del tipo int, esta representación puede no ser exacta. Además, dado que la capacidad de los computadores es limitada, la representación sólo se puede considerar válida dentro de un rango, de forma semejante a como sucede con los enteros.
![[Pasted image 20241203155105.png]]
Asociadas al tipo float están las operaciones que se pueden realizar con él. Las operaciones entre valores reales son las operaciones aritméticas básicas que se realizan entre reales y devuelven como resultado valores reales.

### **2.5.3 El tipo carácter (char)**

Para comprender bien el manejo de valores de tipo carácter en un computador es necesario conocer cómo se definen y representan esos valores de caracteres. Cada carácter no se representa internamente como un dibujo (el glifo del carácter), sino como un valor numérico entero que es su código. La colección concreta de caracteres y sus códigos numéricos se establecen en una tabla (charset) que asocia a cada carácter el código numérico (codepoint) que le corresponde. Dependiendo del número de bits reservado para representar el código de cada carácter podremos tener tablas más o menos amplias. Algunas tablas de caracteres de amplio uso son:
![[Pasted image 20241203155119.png]]
Las tablas mencionadas son compatibles entre sí en el sentido de que cada una de ellas incluye la anterior, manteniendo los códigos numéricos de los caracteres. Lamentablemente la compatibilidad no se extiende a otras muchas labias de caracteres de amplio uso.

En C+- (como en C/ C++) los valores del tipo char ocupan 8 bits e incluyen el repertorio ASCII. Además incluyen otros caracteres no-ASCII que dependen de la tabla de caracteres establecida . En los ejemplos de este libro asumiremos que se dispone de los caracteres comunes a Latin-l y Windows-1252. Por lo tanto, la colección de valores del tipo char incluye caracteres alfabéticos, numéricos, de puntuación y caracteres de control.

Como ya se ha dicho, en el texto de un programa se pueden escribir los valores de los caracteres, bien directamente, o mediante una secuencia de escape, p.ej. para los caracteres de control. También se puede representar cualquier carácter mediante la notación char(x) siendo x eL código del carácter. Por ejemplo, en ASCIL

 char(10) Salto al comienzo de una nueva línea. Posición 10ª

char(13) Retorno al comienzo de la misma línea. Posición 13ª

char(65) Letra A mayúscula. Posición 65ª.

En sentido inverso, el código numérico de un determinado carácter e se expresa como int(c). Por ejemplo:

int('A') 65 (65ª posición de la tabla ASCII)

De forma inmediata se puede decir que, para cualquier carácter c, cuyo código sea x, se cumplirá que:

char(int(c)) = c

int(char(x)) = x

Además, conviene saber que la tabla ASCII posee las siguientes características:

• Los caracteres correspondientes a las letras mayúsculas de la 'A' a la 'Z' están ordenados en posiciones consecutivas y crecientes según el orden alfabético.

• Los caracteres correspondientes a las letras minúsculas de la 'a' a la 'z' están ordenados en posiciones consecutivas y crecientes según el orden alfabético.

• Los caracteres correspondientes a los dígitos del 'O' al '9' están ordenados en posiciones consecutivas y crecientes.

En C (y en C±) se puede usar también el módulo de librería ctype (cabecera «ctype .h» , que facilita el manejo de diferentes clases de caracteres. Este módulo incluye funciones tales como:
![[Pasted image 20241203155200.png]]
## **2.6 Expresiones aritméticas**

Una expresión aritmética representa un cálculo a realizar con valores numéricos (más adelante se verán expresiones que utilizan también valores de otros tipos). Una expresión aritmética es una combinación de operandos y operadores.

Para indicar el orden en que se quieren realizar las operaciones parciales se pueden utilizar paréntesis. Si no se utilizan paréntesis el orden de las operaciones depende de una jerarquía entre los operadores empleados, que para los operadores numéricos es la siguiente:

1º Operadores multiplicativos: * / %

2° Operadores aditivos: + -

Dentro del mismo nivel las operaciones se ejecutan en el orden en que están escritas en la expresión aritmética de izquierda a derecha.

Si se mezclan en una misma expresión valores de tipos diferentes, las expresiones aritméticas son completamente ambiguas.

Evidentemente, los resultados serán diferentes según el tipo de operación que se realice. Además, no queda claro si el resultado que se pretende obtener es un valor entero o real. Para poder realizar estas operaciones es necesario que se realice una conversión de la representación de los datos al tipo adecuado.

float(45) Representa el valor numérico 45.0 con tipo float

int (34 .7) Representa el valor numérico 34 con tipo int

## **2.7 Operaciones de escritura simples**

El objetivo de un programa es obtener unos resultados. Estos resultados deben ser emitidos al exterior del computador a través de un dispositivo de salida de datos: impresora, pantalla, trazador (plotter), línea de comunicaciones, etc. Las acciones que envían resultados al exterior se llaman, en general, operaciones de escritura, con independencia de que se trate de una impresión en papel, o la simple visualización en pantalla, o la grabación de los datos en un soporte donde queden registrados, o su envío a otro equipo remoto.

### **2.7.1 El procedimiento printf**

Este procedimiento pertenece al módulo stdio (cabecera <stdio.h>). La forma más sencilla de invocarlo es escribir:

Printf (cadena-de-caracteres);

NOTA: Esta forma sencilla sólo es válida si la cadena de caracteres a escribir no contiene el carácter %.

Si lo que se quiere escribir es la representación como texto de una serie de valores de cualquier tipo de los vistos hasta el momento habrá que usar la forma general de la orden printf:

printf( cadena-con-formatos, valor1, valor2, …, valorN );

Una cadena de caracteres con formatos deberá incluir en su interior una especificación de formato por cada valor que se quiera insertar. La forma más simple de especificar un formato es mediante %x, es decir, usando el carácter fijo % seguido de una letra de código que indica el tipo de formato a aplicar.
![[Pasted image 20241203155220.png]]
Como se puede apreciar en los ejemplos estos formatos simples usan sólo el número de caracteres estrictamente necesarios para escribir el valor de cada dato, sin añadir espacios en blanco. Si se quiere separar con espacios unos valores de otros, entonces hay que incluirlos en el formato.

Otra forma de conseguir espacios en los resultados es indicar explícitamente cuántos caracteres debe ocupar el valor de cada dato escrito. Esto se hace poniendo el número de caracteres entre el símbolo de % y el código del formato.
![[Pasted image 20241203155232.png]]
Cuando el número de caracteres indicado es insuficiente para representar completamente el valor, como ocurre en el último ejemplo, se utilizan tantos caracteres como sean necesarios para que el resultado aparezca completo. Además, cuando se utiliza un formato f , e ó g se puede especificar también el número de cifras decimales que se deben escribir después del punto decimal.
![[Pasted image 20241203155242.png]]
## **2.8 Estructura de un programa completo**

Un programa en C± se engloba dentro de una estructura principal o main().

Podemos observar que en el texto del programa aparece una línea precedida del símbolo #. Con este símbolo comienzan lo que se llaman _directivas para el compilador_. En concreto con la directiva #include se indica al compilador que utilice el módulo de librería stdio (cabecera <stdio.h>) para las operaciones de escritura que se realizaran en el programa. De hecho, la directiva #include será la única que se usará en C+-.

El cuerpo del programa contiene las sentencias ejecutables correspondientes a las acciones a realizar, escritas entre los símbolos { de comienzo y } final. Cada sentencia del programa termina con un punto y coma (;).

Es conveniente recordar que todos los programas en C± se deben guardar en el fichero con el nombre del programa y la extensión . cpp. Así, el nombre del fichero fuente de este programa deberá ser: hola.cpp.

### **2.8.1 Uso de comentarios**

En C± los comentarios se incluyen dentro de los símbolos /* y * / . Por ejemplo:

`` /* ¡Ojo! Esto es un comentario */``

### **2.8.2 Descripción formal de la estructura de un programa**

La descripción formal de la estructura (simplificada) de un programa es la siguiente:

`Programa :: = {Include} int main() Bloque`

 `Include:: = #include <Nombre_modulo.h>`

Cada directiva debe ocupar una línea del programa ella sola. En los lenguajes C y C++ hay una gran variedad de directivas, pero en C± se utilizará casi exclusivamente la directiva #include , que sirve para indicar que el programa utilizará un determinado módulo de librería. El parámetro _Nombre_ módulo_ corresponde en realidad al nombre del fichero de cabecera (header) del módulo. El resto del código del programa se podría repartir en líneas de código como se desee, aunque en el Manual de Estilo de C± se exigirá un estilo de presentación uniforme, tal como se irá indicando a medida que se introduzcan los elementos del lenguaje.

Por ahora diremos que un bloque puede contener una secuencia de sentencias:

`Bloque:: = {Parte_ejecutiva}`

`Parte_ejecutiva:: = {Sentencia}`

# Tema 3 Constantes y Variables

## **3.1 Identificadores**

En programación se llaman identificadores a los nombres usados para identificar cada elemento del programa. En C± los identificadores son una palabra formada con caracteres alfabéticos o numéricos seguidos, sin espacios en blanco ni signos de puntuación intercalados, y que debe comenzar por una letra. Es importante resaltar que las letras ñ o Ñ o las vocales acentuadas no están incluidas en el alfabeto de la mayoría de los lenguajes de programación, y por supuesto tampoco en C±, por lo que no pueden formar parte de ningún identificador. Sin embargo, estas letras sí pueden ser utilizadas como valores de tipo char o formando parte de una cadena.

A la hora de inventar nombres conviene seguir unas reglas de estilo uniformes que faciliten la lectura del programa. En el Manual de Estilo de C± se sugieren. entre otras, las siguientes:

• Por defecto, escribir todo en minúsculas: indice nombre apellidos area

• Escribir en mayúsculas o empezando por mayúsculas los nombres de constantes que sean globales o que sean parámetros generales del programa: Pi NULO MAXIMO

1.      Usar guiones o mayúsculas intermedias para los nombres compuestos: diaDelMes ANCHO_MAXIMO

## **3.2 El vocabulario de C±**

Además de los identificadores usados para nombrar diferentes elementos, en un programa podemos encontrar otras palabras que siguen las mismas reglas de formación que los identificadores, pero que realmente no son nombres. Se trata de las _palabras clave_, que sirven para delimitar determinadas construcciones del lenguaje de programación.

Las palabras clave son elementos fijos del lenguaje. También son elementos fijos del lenguaje los nombres de los tipos fundamentales y los de algunas funciones especiales incorporadas en el propio lenguaje. Este conjunto de elementos fijos se denominan _palabras reservadas_, y no pueden ser redefinidas por el programador para utilizarlas con otros fines. Las palabras reservadas en el subconjunto C± son las siguientes:

==bool break case catch char const default delete do else enum extern false float for if int new private return struct switch true try typedef union void while==

Además de las palabras de la lista anterior hay algunos identificadores que sin estar reservados en C++ tienen un significado preciso en cada programa en el que aparezcan. Por lo tanto, tampoco deberían ser redefinidos por el programador para otros fines. Por ejemplo:

main NULL std string …

En C± se considerarán también estos identificadores como palabras reservadas, y por lo tanto será un error redefinirlos.

## **3.3 Constantes**

### **3.3.1 Concepto de constante**

Una constante. es un valor fijo que se utiliza en un programa. El valor debe ser siempre el mismo para cualquier ejecución del programa, es decir, el valor no puede cambiar de una ejecución a otra.

### **3.3.2 Declaración de constantes con nombre**

La declaración de un valor constante con nombre consiste en asociar un identificador a dicho valor constante. La declaración de la constante especifica su nombre y tipo y el valor asociado. Si queremos declarar el valor de la constante asociado al nombre Pi escribiremos:

**const float** Pi = 3.14159265;

Las constantes con nombre han de ser declaradas en el programa antes de ser utilizadas. Una vez definida la constante se puede utilizar su nombre exactamente igual que si fuera su valor explícito.

Ej:

const char Pregunta[] = "¿Código postal?";

En el caso de la constante Pregunta su tipo es cadena de caracteres y la forma en que se declara es utilizando los símbolos [] a continuación del nombre de la constante.

==Una posibilidad interesante es poder declarar el valor de una constante en forma de expresión. En C+- sólo se permite hacer esto si la expresión puede ser evaluada por el compilador en el momento de traducir el programa fuente a programa objeto. Para ello es necesario que todos los operandos que intervengan en la expresión sean valores constantes, y que las operaciones entre ellos sean operadores fijos del lenguaje o funciones predefinidas (que tienen identificadores predefinidos). En este caso la expresión se denomina _expresión constante_. Los operandos constantes pueden ser valores explícitos o constantes con nombre declaradas en algún punto anterior del programa.==

Ej:

`const float diametro = 2 * radio;`

`const int constanteRara = (23 * 5) / ((7 - 4) % 2));`

`const int area = largo * ancho;`

`const int perimetro = 2*(largo + ancho) ;`

Las reglas precisas que han de seguir las declaraciones de constantes con nombre son las siguientes:  

`Declaración_ de_constante::= `

`const Tipo Nombre = Expresión_constante;`

`Tipo: : = Identificador`

`Nombre:: =Identificador`

## **3.4 Variables**

### **3.4.1 Concepto de variable**

Las variables algebraicas representan valores simbólicos, bien valores cualesquiera, o bien valores desconocidos, pero de manera que una vez asociada la variable a un valor determinado dicho valor no debe cambiarse.

En programación el concepto de variable es diferente, y está directamente asociado a la memoria del computador. Esta memoria permite almacenar información para ser usada posteriormente. La función de la memoria es mantener dicho valor todo el tiempo que sea necesario para usarlo tantas veces como se necesite.

Los valores almacenados en la memoria pueden ser modificados cuantas veces se desee. Al almacenar un valor en un elemento determinado de la memoria, dicho valor se mantiene de ahí en adelante, pero sólo hasta que se almacene en dicho elemento un nuevo valor diferente.

Las variables en los lenguajes de programación imperativos son el concepto abstracto equivalente a la memoria física de la máquina. Una variable representa un valor almacenado que se puede conservar indefinidamente para ser usado tantas veces como se desee. El valor de una variable se puede modificar en cualquier momento, y será el nuevo valor el que estará almacenado en ella a partir de entonces.

### **3.4.2 Declaración de variables**

Cada variable en un programa en C± debe tener asociado un tipo de valor determinado. Esto quiere decir que si una variable tiene asociado el tipo int, por ejemplo, sólo podrá almacenar valores de este tipo, pero no valores de tipo float u otro diferente.

Las variables han de ser declaradas en el programa antes de ser utilizadas. La declaración simple de una variable especifica su nombre y el tipo de valor asociado.

Ej:

int edad;

Si varias variables tienen el mismo tipo, se pueden declarar todas conjuntamente, escribiendo sus nombres seguidos, separados por el carácter coma (.) detrás del tipo común a todas ellas.

Ej:

int dia, mes, anno;         

La descripción BNF (simplificada) de una declaración de variables es la siguiente: `Declaración_de_variable:: =Tipo Nombre {, Nombre};`

`Tipo:: =Identificador`

`Nombre:: =Identificador`

### **3.4.3 Uso de variables. Inicialización**

El valor almacenado en una variable puede utilizarse usando la variable como operando en una expresión aritmética. El tipo declarado para cada una de las variables determina las operaciones que posteriormente se podrán realizar con ella, de la misma forma que sucedía para los valores literales según se explicó en el tema anterior.

Por ejemplo, si declaramos las variables:

`int base, altura;`

`int saldo , meses. dias;`

`float volumen, area, gastos;`

`char modelo, codigo;`

podremos escribir expresiones tales como:

`base * altura`

`dias + int( codigo )`

`volumen / area`

pero sería inapropiado escribir

`área / base`

`saldo + gastos`

`base + modelo`

 porque combinan operandos de tipos diferentes

Si se usan correctamente los tipos de operandos para cada operación, en una misma expresión pueden intervenir operandos de diferentes clases. Por ejemplo, pueden usarse a la vez variables, constantes con nombre y valores numéricos constantes.

Para usar una variable de manera correcta es necesario inicializarla antes de usar su valor en ningún cálculo. _Inicializar_ una variable es simplemente darle un valor determinado por primera vez.

Para evitar confusiones, en el Manual de Estilo de C± sólo está permitido especificar el valor inicial de una variable en una declaración individual para esa variable. Por tanto, no está permitido realizar inicializaciones de ninguna variable cuando se declaran como una lista de variables del mismo tipo. Para inicializar la variable, su nombre irá seguido del signo igual (=) y a continuación su valor inicial, de forma similar a una declaración de constante:

float gastos = 0.0;

char modelo = ‘?’ ;

Como no es obligatorio dar valor inicial a todas las variables, unas pueden llevar valor inicial y otras no.

La descripción BNF (corregida) de la declaración de variables, con valor inicial opcional, es la siguiente:

`Declaración_de_variable :: = Variable_simple | Lista_de_variables ;`

`Variable_simple :: = Tipo Nombre [ = Expresión]`

`Lista_ de_ variables :: = Tipo Nombre { , Nombre}`

`Tipo :: = Identificador`

`Nombre :: = Identificador`

Si no se especifica el valor inicial al declarar la variable, entonces deberá ser inicializada en el momento adecuado asignándole valor de alguna manera durante la ejecución del programa, antes de usar el valor almacenado para operar con él.

## **3.5 Sentencia de asignación**

Una forma de conseguir que una variable guarde un determinado valor es mediante una sentencia de _asignación_. Esta sentencia es característica. de la programación imperativa, y permite inicializar una variable o modificar el valor que tenía hasta el momento. Mediante asignaciones podremos dar valores iniciales a las variables, o guardar en ellas los resultados intermedios o finales de cualquier programa.

La estructura de una sentencia de asignación es la siguiente:

 _Asignación_ **: : =** _Variable_ **=** _Expresión ;_

 _Variable_ **: : =** _Identificador_

El signo igual (=) es el operador de asignación. Este operador indica que el resultado de la expresión a su derecha debe ser asignado a la variable cuyo identificador está a su izquierda. Por ejemplo, la secuencia de asignación siguiente:

base = 18;

area = 56 . 89;

codigo = ' z ';

sustituye los valores que tuvieran las variables base, area y codigo hasta ese momento por los nuevos valores 18, 56,89 y la letra “z", respectivamente.

Si intervienen variables en la expresión a la derecha de una sentencia de asignación, se usará el valor que tenga la variable en ese momento. Por ejemplo, la siguiente secuencia de asignaciones:

 meses = 2;

dias = meses;

meses = 7 ;

saldo = meses;

Un caso especial, que requiere cierta atención, es aquél en que a una variable se le asigna el valor de una expresión de la que forma parte la propia variable. Por ejemplo:

dias = días + 30;

Esta asignación recuerda a una ecuación, pero su significado es completamente diferente. Esta. sentencia es una orden de evaluar primero la expresión a la derecha usando el valor que tenía la varriable hasta ese momento, y luego modificar el valor de la variable almacenando en ella el **resultado de la expresión.**

### **3.5.1 Sentencias de autoincremento y autodecremento**

Resulta bastante frecuente la necesidad de incrementar en uno el valor de una variable. Para ello, empleando la sentencia de asignación se tiene que escribir:

variable = variable + 1;

Para simplificar y aumentar la claridad del programa, en C+- se dispone de una sentencia especial de autoincremento que utiliza el símbolo ++. Así, en lugar de la sentencia de asignación anterior se suele utilizar habitualmente la sentencia de autoincremento de la siguiente manera: variable++;

De forma semejante cuando se necesita decrementar una variable en una unidad, C+- dispone de la sentencia especial de autodecremento que utiliza el símbolo -- y que se escribe:

variable--;

Esta sentencia es equivalente a la sentencia de asignación:

variable : variable - 1;

### **3.5.2 Compatibilidad de tipos**

Una sentencia de asignación puede resultar confusa si el tipo de la variable y el del resultado de la expresión son diferentes, de manera similar a lo que ocurre con tilla operación aritmética entre operandos de tipos diferentes. El lenguaje C+- no es _fuertemente tipado_ y permite la ambigüedad que supone la asignación de un valor de un tipo a una variable de otro tipo. Para salvar la ambigüedad, C+- utiliza el convenio de C/ C++ de convertir previamente de manera automática el valor a asignar al tipo del valor de la variable. De todas maneras, para evitar confusiones, en el Manual de Estilo se establece que para la realización de programas en C± es obligatorio que se realice siempre una conversión explícita de tipos en estos casos. Ej:

int saldo;

float gastos;

saldo= int(gastos);

## **3.6 Operaciones de lectura simple**

En C+-, los datos leídos han de ser guardados inmediatamente en variables del programa. Por tanto, otra manera de asignar un valor a una variable es almacenar en ella un valor introducido desde el exterior del computador mediante el teclado u otro dispositivo de entrada de datos.

### **3.6.1 El procedimiento scanf**

El procedimiento scanf pertenece al módulo de librería stdio. Para leer datos de entrada y almacenarlos en determinadas variables se escribirá:

**scanf**  _(cadena-con-formatos, &variablel, &variable2. ... &variableN);_

Es importante observar que los nombres de las variables a leer van precedidos del carácter _ampersand_ (&).

Ej:

Declaración de variables int mes, dia; float saldo;

Datos de entrada 123 4.5 6

Orden de lectura scanf( "%d %f %d", &mes, &saldo, &dia );

Resultado mes = 123; saldo = 4.5; dia = 6;

La cadena de caracteres con los formatos sigue las mismas reglas que la del procedimiento printf del terna anterior. Debe contener un formato de conversión (%_x_) por cada variable a leer. Al ejecutarse el procedimiento scanf se van tomando caracteres del dispositivo de entrada, se ponen en correspondencia con los formatos indicados, y se extraen los valores correspondientes a cada formato de conversión para asignarlos a cada variable de la lista, respectivamente.

Al igual que en el procedimiento printf, la cadena con los formatos puede incluir también otros fragmentos de texto entremezclados con los formatos de conversión. La ejecución de scanf consiste en analizar uno a uno los elementos de la cadena con formatos, y actuar en consecuencia, avanzando en el texto de entrada:

1. ==Un formato numérico (%d, %f , %g, ... ) hace que se salten los siguientes caracteres de espacio en blanco en la entrada, si los hay. A continuación, se leen los caracteres no blancos que formen una representación válida de un valor numérico del tipo correspondiente al formato, y el valor numérico obtenido se asigna al siguiente argumento de la lista de variables a leer.==

2. ==Un formato %c hace que se lea exactamente el siguiente carácter de la entrada, sea o no espacio en blanco, y se asigne a la siguiente variable a leer.==

3. ==Un carácter de espacio en blanco en la cadena con formatos hace que se salten los siguientes caracteres de espacio en blanco en el texto de entrada, si los hay.==

4. ==Un carácter no blanco en la cadena con formatos hace que se lea (y se salte) el siguiente carácter de la entrada, que debe coincidir exactamente con el carácter del formato.==

==Si alguna de las acciones anteriores no puede realizarse, porque el texto de entrada no contiene los caracteres apropiados, la ejecución de scanf se interrumpe en ese momento, y no se lee más texto de entrada ni se asignan valores a las variables que falten por leer.== Los formatos de conversión numéricos pueden incluir la especificación del tamaño del dato, de forma similar a como se dijo para printf. ==Pero a diferencia de los formatos para printf, en que ese tamaño era el mínimo número de caracteres a escribir, en scanf significa el tamaño máximo del dato de entrada a leer.== Ej:
![[Pasted image 20241203160306.png]]
### **3.6.2 Lectura interactiva**

Cuando un programa se comunica con el usuario mediante un terminal de texto se suele programar cada operación de lectura inmediatamente después de una escritura en la que se indica qué dato es el que se solicita en cada momento. Por ejemplo:

float saldo printf( "¿Cantidad Pendiente? " );

scanf( "%fn , &saldo );

Tras ejecutar la escritura del texto de petición, en la pantalla se verá:

¿Cantidad Pendiente? **_**

En ese momento se inicia, la ejecución del procedimiento de lectura, El símbolo (**_**) se utiliza aquí para indicar la posición del cursor en la pantalla, en espera de la entrada del dato solicitado.

Si se quiere introducir más de un valor con la misma pregunta y en la misma se puede utilizar como separador de datos el espacio en blanco. Por ejemplo:

float saldo, gastos ;

…

printf( "¿Cantidad pendiente y Gastos? " );

scanf( "%f%f", &saldo, &gastos );

En la pantalla aparecerá el mensaje de petición, y luego se teclearán los datos separados por uno o varios blancos y acabados con un INTRO:

 ¿cantidad pendiente y Gastos? -45768 l0456.5 INTRO

## **3.7 Estructura de un programa con declaraciones**

Antes de realizar nuevos programas es necesario saber dónde se sitúan dentro del programa los nuevos elementos introducidos en este tema. Las declaraciones de valores constantes y de las variables forman parte del bloque del programa. Por tanto, ahora la estructura del bloque es la siguiente:

_Bloque_**:: = {** _Parte declarativa Parte_ ejecutiva_**}**

_Parte_declarativa_ **:: =** _{ Declaración_ **}**

_Parte_ ejecutiva_ **: : = {** _Sentencia_ **}**

_Declaración_ **: : =**

_Declaración_dc_constante_ **I** _Declaración_ de_variable_ **I**

_Sentencia_ **: : =** _Llamada_a_Procedimiento_ **I** _Asignación_ **I**

El contenido de un bloque se organizará en dos partes. La primera de ellas contendrá todas las declaraciones de constantes, variables, etc., y la segunda incluirá las sentencias ejecutables correspondientes a las acciones a realizar. Las declaraciones pueden hacerse en el orden que se quiera, con la limitación de que cada nombre debe ser declarado antes de ser usado. Las sentencias ejecutables deben escribirse exactamente en el orden en que han de ser ejecutadas.

# Tema 4 Metodología de Desarrollo de Programas (I)

## **4.1 La programación como resolución de problemas**

Resolver un problema consiste esencialmente en encontrar una estrategia a seguir para conseguir la solución. Una estrategia se expresará como una colección de reglas o recomendaciones que, si se siguen, conducirán a la solución.

Todo programa puede considerarse, de alguna forma, como la solución de un problema determinado, consistente en obtener una cierta información de salida a partir de unos determinados datos de entrada. La tarea de desarrollar dicho programa equivale, por tanto, a la de expresar la estrategia de resolución del problema en los términos del lenguaje de programación utilizado.

## **4.2 Descomposición en subproblemas**

Cualquier problema de cierta complejidad necesitará una labor de desarrollo para expresar la solución. ==El método más general de resolución de problemas no triviales consiste en descomponer el problema original en subproblemas más sencillos, continuando el proceso hasta llegar a subproblemas que puedan ser resueltos de forma directa.==

Lo que se busca aquí es una analogía con la labor de desarrollo de programas. Puesto que el proceso de ejecución de un programa imperativo consiste en la realización de las sucesivas acciones indicadas por las órdenes que constituyen el programa, analizaremos la resolución de problemas en que la estrategia de solución consiste en realizar acciones sucesivas.

Según esta idea, para desarrollar la estrategia de resolución, habrá que ir identificando subproblemas que se resolverán ejecutando acciones cada vez más simples.

==El proceso de descomposición en subproblemas debe continuar hasta que los subproblemas se puedan resolver mediante acciones consideradas directamente ejecutables por el agente que ha de proporcionar la solución.== La expresión final de la solución del problema debe tener en cuenta, por tanto, qué acciones particulares se consideran realizables de forma directa. Tenemos así una analogía con la tarea de programación, que exige redactar el programa con los elementos particulares del lenguaje de programación elegido

## **4.3 Desarrollo por refinamientos sucesivos**

La aplicación de las ideas anteriores a la construcción de programas conduce a la técnica de desarrollo mediante _refinamientos sucesivos_. Esta técnica es parte de las recomendaciones de una metodología general de desarrollo de programas denominada _programación estructurada_, que se estudiará con más detalle en el tema siguiente. ==La técnica de refinamientos consiste en expresar inicialmente el programa a desarrollar como una acción global, que si es necesario se irá descomponiendo en acciones más sencillas hasta llegar a acciones simples que puedan ser expresadas directamente como sentencias del lenguaje de programación.==

Cada paso de refinamiento consiste en descomponer cada acción compleja en otras más simples. Esta descomposición exige:

• Identificar las acciones componentes.

• Identificar la manera de combinar las acciones componentes para conseguir el efecto global.

==La forma en que varias acciones se combinan en una acción compuesta constituye el _esquema_ de la acción compuesta.==

Por el momento presentamos un primer esquema que denominaremos _esquema secuencial_, que consiste en realizar una acción compuesta a base de realizar una tras otra, en secuencia, dos o más acciones componentes.

### **4.3.1 Desarrollo de un esquema secuencial**

La metodología de refinamientos incluye el ir desarrollando a la vez las sentencias del programa que realizan las acciones de la parte ejecutable, y la definición de las variables necesarias para almacenar la información, manipulada por dichas acciones. Para desarrollar una acción compuesta según un esquema secuencial se necesitará:

a)      Identificar las acciones componentes de la secuencia. Identificar las variables necesarias para disponer de la información adecuada al comienzo de cada acción, y almacenar el resultado.

b)     Identificar el orden en que deben ejecutarse las acciones componentes.

Ej:

a)      Acciones componentes:

• Cálculos: obtener la suma

`suma = datol + dato2`

• Operaciones de entrada: leer datos

`printf( "Dar dos números: " ) ;`

`scanf( "%d", &datol ) ;`

`scanf( "%d", &dato2 ) ;`

`printf( "\ n" ) ;`

• Operaciones de salida: imprimir resultado

`printf( "La suma es%l0d\n", suma)`

Variables necesarias: datos y resultado

`int datol, dato2, suma;`

b)      Orden de ejecución:

1) Leer los datos

2) Calcular la suma

3) Imprimir el resultado

Si nos limitamos a describir la manera en que la acción global del programa se va descomponiendo en acciones cada vez más sencillas, podemos usar la siguiente notación de refinamiento:

Acción compuesta -->

Acción 1

Acción 2

... etc.

En esta notación se utiliza una flecha (-->) para indicar que una acción complicada se descompone o refina en otras más sencillas. Aplicando esta notación al ejemplo anterior, hasta llegar a sentencias de C±, tendremos:

Obtener la suma de dos números -->

Leer los datos

Calcular la suma

Imprimir el resultado

Leer los datos -->

`printf( "Dar dos números: " );`

`scanf( "%1:1". &datol );`

`scanf( "%d", &dato2 );`

`printf( "\ n" );`

Calcular la suma -->

`suma = dato! + dato2;`

imprimir el resultado -->

`printf( "La suma es%10d\ n", suma);`

Uniendo todos los fragmentos finales de código en el orden adecuado, y añadiendo las declaraciones de las variables necesarias, tendremos el programa completo.

## **4.4 Aspectos de estilo**

El estilo de redacción del programa en su forma final es algo fundamental para conseguir que sea claro y fácilmente comprensible por parte de quienes hayan de leerlo.

### **4.4.1 Encolumnado**

Un recurso de estilo de presentación es el _encolumnado_ o sangrado (_indent_). Ampliando el margen izquierdo para las partes internas del programa se puede conseguir que el texto de un elemento compuesto ocupe una zona aproximadamente rectangular, y que el texto que representa cada uno de sus componentes ocupe también una zona rectangular dentro de ella.
![[Pasted image 20241203160521.png]]
### **4.4.2 Comentarios. Documentación del refinamiento**

Aunque el lenguaje permite empicar comentarios con toda libertad, es aconsejable seguir ciertas pautas para facilitar la lectura del programa. Estas pautas corresponden a diferentes clases de comentarios, cada una con un propósito diferente. Entre ellas podemos mencionar:

• Cabeceras de programa

==La cabecera de programa tiene como finalidad documentar el programa como un todo.== Puede incluir datos de identificación, finalidad, descripción general, etc. Suele presentarse como una "caja" al comienzo del texto del programa, ocupando todo el ancho del listado.
![[Pasted image 20241203160539.png]]
• Cabeceras de sección

==Las cabeceras de sección sirven para documentar partes importantes de un programa relativamente largo.== Al igual que la cabecera del programa, se presentan en forma de "caja" al comienzo de la sección correspondientes, ocupando todo el ancho del listado.
![[Pasted image 20241203160610.png]]
• Comentarios-orden

Los comentarios-orden son un elemento metodológico fundamental, y sirven para documentar los refinamientos empleados en el desarrollo del programa.

Para incluir la información de los pasos de refinamiento en el texto del programa se puede introducir un comentario con la descripción de cada acción intermedia.
![[Pasted image 20241203160621.png]]
• Comentarios al margen

Estos comentarios sirven para aclarar el significado de ciertas sentencias del programa, que pueden ser difíciles de interpretar al leerlas tal como aparecen escritas en el lenguaje de programación empleado. Ulla recomendación de estilo es situar estos comentarios hacia la parte derecha del listado, en las mismas líneas que las sentencias que se comentan, y alineados todos a partir de una posición fija, hacia el comienzo del tercio final.
![[Pasted image 20241203160633.png]]
### **4.4.3 Elección de nombres**

Los nombres que tenga que inventar el programador deben ser elegidos con un criterio nemotécnico, de manera que recuerden fácilmente el significado de los elementos nombrados.

Para que los nombres o identificadores resulten significativas hay que procurar que tengan la categoría gramatical adecuada al elemento nombrado. En concreto:

- ==Los valores (constantes, variables, etc.) deben ser designados mediante sustantivos.==

- ==Las acciones (procedimientos, etc.) deben ser designadas con verbos==

- ==Los tipos deben ser designados mediante nombres genéricos.==

### **4.4.4 Uso de letras mayúsculas y minúsculas**

Los lenguajes de programación que permiten distinguir entre letras mayúsculas y minúsculas facilitan la construcción de nombres en programas largos, en que es preciso inventar un gran número de ellos.

### **4.4.5 Constantes con nombre**

En lugar de usar directamente valores numéricos con las expresiones de algunos cálculos, puede resultar ventajoso definir determinados coeficientes o factores de conversión con un nombre simbólico que tenga un buen significado nemotécnico, y usar la constante con ese nombre en los cálculos.

Otra forma ventajosa de usar el mecanismo de definición de constantes con nombre se da en el caso de que el comportamiento de un programa venga dado en función de ciertos valores generales, fijos, pero que quizá fuera interesante cambiarlos en el futuro. Este tipo de valores se denominan a veces parámetros del programa, y es conveniente que su valor aparezca escrito sólo una vez en un lugar destacado del programa

# Tema 5 Estructuras Básicas de la Programación Imperativa

## **5.1 Programación estructurada**

==La _programación estructurada_ es una metodología de programación que fundamentalmente trata de construir programas que sean fácilmente comprensibles.==

Esta metodología está basada en la técnica de desarrollo de programas por _refinamientos sucesivos_, tal como se ha expuesto en el tema anterior. Inicialmente, se plantea la operación global a realizar por el programa, y se descompone en otras más sencillas. A su vez, estas últimas vuelven a ser descompuestas nuevamente en otras todavía más elementales. Este proceso de descomposición continúa hasta que todo se puede escribir utilizando las estructuras básicas disponibles en el lenguaje de programación que se está empleando.

### **5.1.1 Representación de la estructura de un programa**

La estructura de los programas imperativos se representa tradicionalmente mediante _diagramas de flujo_, llamados en inglés "flow-chart". Estos diagramas contienen dos elementos básicos, correspondientes a acciones y condiciones. Las acciones se representan mediante rectángulos, y las condiciones mediante rombos. Las condiciones equivalen a preguntas a las que se puede responder “SÍ" o “No".
![[Pasted image 20241203160747.png]]
El flujo de control durante la ejecución del programa se refleja mediante líneas o vías que van de un elemento a otro. Durante la ejecución, cuando el flujo llega a la entrada de una acción, la acción se realiza y el flujo se dirige a su salida. Cuando se llega a la entrada de una condición, la condición se evalúa, y si resulta ser cierta se continúa por la salida "SÍ", mientras que si es falsa se continúa por la salida "No".

La parte de diagrama de flujo en el interior de una acción compuesta constituye la estructura o esquema de dicha acción. La programación estructurada recomienda descomponer las acciones usando las estructuras más sencillas posibles. Entre ellas se reconocen tres estructuras básicas, que son: _Secuencia, Selección e Iteración._
![[Pasted image 20241203160757.png]]
### **5.1.2 Secuencia**

La estructura más sencilla para emplear en la descomposición es utilizar una secuencia de acciones o partes que se ejecutan de forma sucesiva.
![[Pasted image 20241203160807.png]]
### **5.1.3 Selección**

La estructura de selección consiste en ejecutar una acción u otra, dependiendo de una determinada condición que se analiza a la entrada de la estructura.
![[Pasted image 20241203160816.png]]
### **5.1.4 Iteración**

La iteración es la repetición de una acción mientras que se cumpla una determinada condición. La estructura de iteración más general es aquella en que la condición se analiza a la entrada de la estructura y antes de iniciar cada nueva repetición. Puesto que el flujo de ejecución vuelve hacia atrás siguiendo un camino cerrado, la estructura de iteración se denomina también bucle.
![[Pasted image 20241203160825.png]]
### **5.1.5 Estructuras anidadas**

Mediante la técnica de refinamientos sucesivos se definen inicialmente las estructuras más externas del programa y en los pasos sucesivos se va detallando la. estructura de cada acción compuesta. Este proceso finalmente da lugar a que todo el programa quede escrito utilizando las estructuras básicas descritas en este apartado, anidadas unas dentro de otras.

## **5.2 Expresiones condicionales**

Una primera forma de construir expresiones condicionales es mediante el empleo de operadores de comparación en expresiones aritméticas. Estos operadores permiten realizar comparaciones entre dos valores del mismo tipo.
![[Pasted image 20241203160854.png]]
Las condiciones compuestas se construyen como expresiones lógicas. Cada término de una expresión lógica podrá ser una expresión condicional simple.
![[Pasted image 20241203160900.png]]
La operación de conjunción El && E2 da resultado cierto si tanto El como E2 son ciertos. En el lenguaje C± para evaluar la operación de conjunción && siempre se empieza por evaluar la expresión simple El del primer operando y si su resultado es falso ya no se evalúa la expresión E2 del segundo operando.

==Está claro que el resultado de la conjunción ya no depende del valor de E2 y será siempre falso. Por este motivo se dice que el operador && se evalúa en _cortocircuito_.

La operación de disyunción El I I E2 da resultado cierto si una de las dos, El o E2 , o ambas son ciertas. También el operador I I se evalúa en cortocircuito.

La complejidad de las expresiones puede ser tan grande como sea necesario; el número de términos lógicos que pueden combinarse es ilimitado. Además, cada valor numérico se puede obtener mediante una expresión aritmética.

Cada operador tiene una prioridad determinada. Si no se utilizan paréntesis, el orden de evaluación en el lenguaje C± es el siguiente:
![[Pasted image 20241203160933.png]]
Dentro del mismo nivel de prioridad las operaciones se evalúan en el orden en que están escritas en cada expresión concreta, de izquierda a derecha.

Para formalizar estos conceptos, las reglas BNF que definen cómo se pueden escribir expresiones aritméticas, condicionales y lógicas en el lenguaje C± son las siguientes:
![[Pasted image 20241203160945.png]]
RESUMEN:

==2.      Es aconsejable utilizar paréntesis adicionales para evitar cualquier ambigüedad o dificultad de interpretación de la expresión.

==3.      Es aconsejable utilizar paréntesis adicionales siempre que se mejore la claridad de la expresión.

==4.      No es aconsejable utilizar paréntesis adicionales en aquellas expresiones que, aprovechando los niveles de prioridad por defecto del lenguaje, estén ampliamente consensuadas y no planteen ninguna duda en su interpretación.

==5.      No están permitidas las comparaciones entre elementos de distintos tipos. ~

==6.      Los operadores lógicos ( && Y I I )sólo se pueden utilizar con elementos de tipo Sí(cierto) / No(falso)

## **5.3 Estructuras básicas en C±**

### **5.3.1 Secuencia**

Para programar una secuencia de acciones en C± se escriben las sentencias que forman la secuencia de acciones una tras otra.

Formalmente, según se vio en el tema 2, la sintaxis de la estructura secuencia es:
![[Pasted image 20241203161028.png]]
### **5.3.2 Sentencia IF**

La ejecución de la sentencia if consiste en evaluar la expresión de Condición, y a continuación ejecutar o bien la Acción A (si se cumple la condición), o bien la Acción B (si la condición no se cumple). Las palabras clave ir y else separan las distintas partes de la sentencia.
![[Pasted image 20241203161040.png]]
En ocasiones no es necesario ejecutar nada cuando la Condición no se cumple. En este caso se ejecuta la Acción cuando la expresión Condición se cumple y en caso contrario no se ejecuta nada.

Es bastante frecuente realizar selecciones que dan lugar a más de dos posibles. Tal como se indicó anteriormente, es posible anidar varias estructuras de selección unas dentro de otras.

Si la evaluación de las condiciones se hace en cascada, atendiendo a una de ellas sólo si todas las anteriores han sido falsas, se puede simplificar la escritura en C± de la sentencia IF eliminando las llaves { ... } de las ramas else para expresar directamente una cadena de selecciones.

El formato de la sentencia if para la selección en cascada es el siguiente:

`if ( Condición 1 ) {`

 `Acción A`

`} else if ( Condición 2 ) {`

`Acción B`

`} else if ( Condición N ) {`

`Acción J`

`} else {`

`Acción K }`

Todas las sentencias presentadas son variantes de una única sentencia IF de C+- cuya sintaxis es la siguiente:
![[Pasted image 20241203161056.png]]
### **5.3.3 Sentencia WHILE**

While ( Condición ) {

Acción }

El significado es que mientras la expresión Condición resulta cierta, se ejecuta la Acción de forma repetitiva. Cuando el resultado es falso finaliza la ejecución de la sentencia. Si la Condición resulta falsa en la primera evaluación, la Acción no se ejecuta nunca.

### **5.3.4 Sentencia FOR**

Existen muchas situaciones en las que las repeticiones del bucle se controlan mediante una variable que va contando las veces que se ejecuta. La cuenta puede ser en sentido creciente, o decreciente. La Condición de la iteración se limita a comprobar si se ha alcanzado el límite correspondiente al número de repeticiones previstas.

Debido a lo habitual de esta situación, en casi todos los lenguajes existen sentencias que simplifican s u construcción. En C± se dispone de la sentencia FOR, cuya forma para incremento creciente es la siguiente:

for (int Índice = Inicial ; Índice <= Final ; Índice ++) {

Acción }

El símbolo punto y coma (;) separa los distintos elementos de control de la sentencia. La actualización del índice se hace mediante la sentencia de _autoincremento_.

La variable Índice sirve de contador para controlar el número de iteraciones a realizar. Inicialmente la variable Índice toma el valor Inicial y se incrementa automáticamente en una unidad con cada nueva ejecución de Acción. La Acción se ejecuta repetidamente hasta que la variable Índice alcanza el valor Final.

La variable Índice se declara dentro del propio FOR, y sólo existe mientras se ejecuta. Al terminar la ejecución la variable Índice ya no es visible en las siguientes sentencias del programa.

la sintaxis completa de la sentencia FOR es, por tanto, la siguiente:
![[Pasted image 20241203161125.png]]
![[Pasted image 20241203161145.png]]
# Tema 6 Metodología de Desarrollo de Programas (II)

## **6.1 Desarrollo con esquemas de selección e iteración**

Se tienen tres posibilidades a la hora de refinar una acción compuesta:

•        Organizarla como secuencia de acciones.

•        Organizarla como selección entre acciones alternativas.

•        Organizarla como iteración de acciones.

### **6.1.1**     **Esquema de selección**

Un esquema de selección consiste en ==plantear una acción compuesta como la realización de una acción entre varias posibles==, dependiendo de ciertas condiciones. Es decir, se trata de elegir una sola entre varias posibles alternativas.

Para desarrollar un esquema de selección debemos identificar sus elementos componentes. Por tanto, habrá que:

==a)      Identificar cada una de las alternativas del esquema, y las acciones correspondientes.

b)     Identificar las condiciones para seleccionar una alternativa u otra.==

Ej:

(a)    Las alternativas son que tenga 28 días o que tenga 29. Las acciones serán asignar dicho valor a una. variable que almacene el número de días.

dias = 28

o bien

dias == 29

(b)   La condición para elegir una acción u otra es que el año sea bisiesto. De forma simplificada (pero válida para años entre 1901 y 2099) expresaremos la condición como equivalente a que el año sea múltiplo de cuatro.

Año % 4 == 0

Colocando cada elemento identificado en el lugar correspondiente del esquema, tendremos:

íf (anno % 4 == O) {

días = 29;

} else {

días = 28;

}
### **6.1.2 Esquema de iteración**

Para desarrollar un _esquema de iteración_ dentro de un programa deberemos identificar cada uno de sus elementos componentes. Al hacerlo hay que identificar simultáneamente las variables adecuadas para almacenar la información necesaria.

En líneas generales se podría proceder de la siguiente manera:

a)      Identificar las acciones útiles a repetir, y las variables necesarias. Precisar el significado de estas variables al comienzo y final de cada repetición.

b)     Identificar cómo actualizar la información al pasar de cada iteración a la siguiente. Puede ser necesario introducir nuevas variables.

c)      Identificar la condición de terminación. Puede ser necesario introducir nuevas variables e incluso acciones adicionales para mantenerlas actualizadas.

d)     Identificar los valores iniciales de las variables, y si es necesaria alguna acción para asignárselos antes de entrar en el bucle.

Ej:

(a) Acciones titiles a repetir: Imprimir un término.

printf("%10d\ n", termino);

_Variables necesarias_: El término a imprimir.

int termino;

_Valor al empezar la repetición_: Último término impreso hasta el momento.

(b) Actualizar las variables al pasar de una repetición a la siguiente: Antes de imprimir, calcular el término actual a partir de los dos anteriores (se necesita tener almacenado el penúltimo término).

aux = termino + anterior;

anterior = termino;

termino = aux;

Variables adicionales: El penúltimo término, y una variable temporal.

int anterior;

int aux;

(e) Condición de terminación: El término siguiente excedería del rango de los enteros. Hay que evaluar la condición sin calcular explícitamente el valor de dicho término, porque se produciría "overflow".

INT_MAX- termino < anterior

(Obsérvese que esta expresión equivale en teoría a INT_MAX < termino+anterior)

(d ) Valores iniciales de las variables: Los dos primeros términos, 0 y 1.

 anterior = 0;

termino = 1;

El bucle completo sería:

int termino;

int anterior;

int aux;

…

anterior = 0

termino= 1;

while (INT_MAX-termino >= anterior) {

aux = termino + anterior;

anterior = termino;

termino = aux;

printf("%10d\ n", termino);

}

## **6.3 Verificación de programas**

==En la práctica, la verificación de un programa se hace muchas veces mediante ensayos. Un _ensayo_ (en inglés, _testing_) consiste en ejecutar el programa con datos preparados de antemano y para los cuales se sabe cuál ha de ser resultado a obtener. Si al ejecutar el programa no se obtienen los resultados esperados, se sabrá que hay algún error, y el programa se examina para determinar la causa del error y eliminarla. Este proceso se llama _depuración_ (en inglés _debugging_).==

La única manera de verificar con seguridad la corrección de un programa es demostrar formalmente que el programa cumple con sus especificaciones. Para ello es necesario escribir esas especificaciones con toda precisión en forma de expresiones lógicas, y luego realizar una demostración lógico-matemática de que el programa las cumple.

### **6.3.1 Notación lógico-matemática**

### **6.3.2 Corrección parcial y total**

Usando las expresiones y reglas de la lógica, y conociendo la semántica (significado) de las acciones, es posible demostrar si un programa es o no correcto (respecto a una determinada especificación). Para programas que siguen el modelo imperativo el proceso de demostración se realiza en dos partes:

1.      Corrección parcial: si el programa termina el resultado es correcto.

2.      Corrección total: lo anterior, y además para todo dato de entrada válido el programa termina.

La base de la comprobación de corrección parcial es:

- Anotar el comienzo y final del programa con aserciones o asertos (afirmaciones, formalizadas como expresiones lógicas) correspondientes a las condiciones iniciales y al resultado deseado. ==La condición al comienzo se suele denominar precondición, y la del final postcondición. La precondición y la postcondición, conjuntamente, constituyen la especificación formal del programa.==

- Anotar los puntos intermedios del programa con aserciones similares respecto al estado del cómputo en ese punto.

- Demostrar que, si se cumple una aserción en un punto del programa y se siguen cada una de las líneas de ejecución posibles hasta llegar a otro punto con aserción, dicha aserción ha de cumplirse, según las reglas de la lógica y de acuerdo con las acciones realizadas.

En particular la corrección parcial se consigue al demostrar que al llegar al del programa ha de cumplirse la aserción correspondiente al resultado deseado.

La corrección total se consigue añadiendo la demostración de que todos los bucles del programa terminan tras un numero finitos de repeticiones. Para demostrar la terminación se puede:

- Asociar a cada bucle una función monótona (siempre estrictamente creciente o decreciente) llamada variante, y que debe tener un valor acotado para que le bucle se repita.

### **6.3.3 Razonamiento sobre sentencias de asignación**

Para analizar el comportamiento de un fragmento de programa correspondiente a una sentencia de asignación, comenzaremos por anotar delante de dicha sentencia todas las condiciones que sabemos que se cumplen inmediatamente antes de ejecutarla. A continuación, anotaremos detrás de la sentencia las condiciones que podamos demostrar que se cumplen después de su ejecución, y que serán las siguientes:

- Las condiciones anteriores en las que no intervenga la variable asignada.

- La condición de que la variable tiene el valor asignado.

### **6.3.4 Razonamiento sobre el esquema de selección**
![[Pasted image 20241203161525.png]]

### **6.3.5 Razonamiento sobre el esquema de iteración: invariante, terminación.**
![[Pasted image 20241203161543.png]]
## **6.4 Eficiencia de programas. Complejidad**

La eficiencia sólo debe tenerse en cuenta si es un factor decisivo o importante en cada caso.

### **6.4.1 Medidas de eficiencia**

==La eficiencia de un programa se define en función de la cantidad de recursos que consume durante su ejecución.

==Las principales medidas de recursos empleados son:

- ==El tiempo que tarda en ejecutarse un programa.
- ==La cantidad de memoria usada para almacenar datos====

En lo que sigue atenderemos exclusivamente a la primera de las dos medidas mencionadas. Un programa se considerará tanto más eficiente cuanto menos tiempo tarde en ejecutarse. Los programas poco eficientes tardarán mucho tiempo en dar los resultados. Hablaremos, por tanto, de la _eficiencia en tiempo_ de un programa.

El tamaño del problema se puede expresar bien por la cantidad de datos a tratar, o bien por los valores particulares de los datos. Por ejemplo, para un programa que obtenga el valor medio o la suma de una serie de datos, el número de datos a sumar o promediar es una buena medida del tamaño del problema. En cambio, para un programa que calcule una potencia de un número, el tamaño significativo puede ser el valor del exponente.

==La función que da el tiempo de ejecución según el tamaño del problema se dice que mide la _complejidad algorítmica_ del programa.==

### **6.4.2 Análisis de programas**

La determinación de la eficiencia (o complejidad) de un programa se hace analizando los siguientes elementos:

==1.      Cuánto tarda en ejecutarse cada instrucción básica del lenguaje utilizado.

2.      ==Cuántas instrucciones de cada clase se realizan durante una ejecución del programa==

Para simplificar, consideraremos que ==cada operación elemental del lenguaje de programación: suma , resta, lectura, escritura, asignación de valor, decisión según condición, etc ... , dura una unidad de tiempo==. Con esta simplificación, ==el análisis de la eficiencia de un programa se centra en establecer cuántas instrucciones se ejecutan en total==, dependiendo del tamaño o cantidad de los datos a procesar.

Al realizar el análisis mencionado nos encontraremos con que el número preciso de instrucciones ejecutadas depende de los valores particulares de los datos, incluso para un tamaño fijo del problema. En este caso se pueden adoptar al menos dos criterios diferentes para realizar el análisis de eficiencia:

• Analizar el comportamiento, en promedio.

• Analizar el comportamiento en el peor caso.

Utilizaremos el segundo criterio, por ser el más sencillo de aplicar, para analizar algunos ejemplos de programas. Con este criterio el análisis de complejidad (número de instrucciones ejecutadas) de los esquemas básicos de los programas se basa en las siguientes reglas:

1.      ==La complejidad de un esquema de secuencia es la suma de las complejidades de sus acciones componentes.==

2.      ==La complejidad de un esquema de selección equivale a la de la alternativa más compleja, es decir, de ejecución más larga, más la complejidad de la evaluación de la condición de selección.==

3.      ==La complejidad de un esquema de iteración se obtiene sumando la serie correspondiente al número de instrucciones en las repeticiones sucesivas.==

### **6.4.3 Crecimiento asintótico**

En los análisis de eficiencia (o complejidad) se considera muy importante la manera como la función de complejidad va aumentando con el tamaño del problema. Lo que interesa es la forma de crecimiento del tiempo de ejecución y no tanto el tiempo particular empleado.

La forma en que crece la función para tamaños grandes se dice que es su _comportamiento asintótico_, y se representa mediante la notación: O (f(n)) En dicha notación n indica el tamaño del problema, f la forma o función de crecimiento asintótico, y O (que se lee O-grande) significa orden de crecimiento.

Algunas formas de crecimiento típicas, y sus valoraciones habituales, son las siguientes:
![[Pasted image 20241203161922.png]]
Los problemas que sólo pueden resolverse con programas de complejidad exponencial se consideran _problemas intratables_ en la práctica para tamaños grandes.

# Tema 7 Funciones y Procedimientos

## **7.1 Concepto de subprograma**

Como mecanismo de programación, un subprograma es una parte de un programa que se desarrolla por separado y se utiliza invocándolo mediante un nombre simbólico.

El empleo de subprogramas, desarrollando por separado ciertas partes del programa, resulta especialmente ventajoso en los casos siguientes:

• En programas complejos

• Cuando se repiten operaciones análogas

La técnica de refinamientos sucesivos sugiere descomponer las operaciones complejas de un programa en otras más simples. En sucesivos pasos de refinamiento, cada operación se vuelve a descomponer hasta que todo el programa se puede escribir utilizando las sentencias disponibles en el lenguaje empleado.

## **7.2 Funciones**

Una función es un tipo de subprograma que calcula como resultado un valor único a partir de otros valores dados como argumentos.

### **7.2.1 Definición de funciones**

El primer paso en el manejo de una función es declarar su interfaz. Esta declaración incluye su nombre, los argumentos que necesita con el correspondiente tipo para cada uno de ellos, y el tipo de resultado que proporciona. En C+- esto se realiza escribiendo una cabecera de función de la siguiente forma:

_TipoResultado NombreFuncion( Tipo1 argumento1, Tipo2 argumento2 , ... )_

==Los argumentos que aparecen en la cabecera son los argumentos formales.== ==No son variables del programa, sino sólo nombres simbólicos que sirven para formalizar la definición posterior de la función, permitiendo hacer referencia a los argumentos en la definición de los cálculos.==

La definición completa de una función se compone de una cabecera seguida de un cuerpo de función que tiene la misma estructura que un Bloque de programa completo. Este bloque comienza con una _parte declarativa_ y continúa con una _parte ejecutiva_. En la parte declarativa se pueden declarar constantes y variables locales que sólo son visibles en el cuerpo de la función. La parte ejecutiva estará constituida por una secuencia de sentencias.

En las sentencias que constituyen el cuerpo de la función se puede (y se debe) hacer uso de los argumentos formales declarados en su interfaz, esto permite parametrizar los cálculos de la función para los valores particulares de los argumentos. Así, otra forma de ver las funciones es como expresiones parametrizadas.

Eu estos ejemplos se observa la existencia de una nueva sentencia de C+- iniciada con la palabr clave **return**. Esta sentencia sirve para devolver como valor de la función el resultado de los cálculos realizados. Esta sentencia. tiene la siguiente estructura:

_return expresión;_

y provoca la finalización inmediata de la ejecución de la función. ==El resultado de la expresión debe ser un valor del tipo indicado en la declaración de la función==. Dicho valor es el que se devuelve corno resultado de la función. ==La sentencia return se puede insertar en cualquier punto de la parte ejecutable de la función. Además, es posible utilizar más de una sentencia return en una misma función. La ejecución de la función acaba cuando se ejecuta cualquiera de las sentencias return.==

### **7.2.2 Uso de funciones**

Para usar una función en los cálculos de un programa se invoca dicha función escribiendo Sil nombre y a continuación, entre paréntesis, los valores concretos de los argumentos, separados por comas.

==Al invocar una función es obligatorio que los valores suministrados para los argumentos (los argumentos reales) correspondan en número y tipo con los argumentos en la definición (los argumentos formales).==

El efecto de la invocación de una función puede describirse de forma simplificada de la siguiente manera:

1. Se evalúan las expresiones de los valores de los argumentos.

2. Se asignan dichos valores a los correspondientes argumentos formales.
pre
3. Se ejecuta el código de la definición de la función, hasta alcanzar una sentencia de retorno.

4. El valor retornado se usa en el punto donde se invocó la función.

### **7.2.3 Funciones predefinidas**

Se consideran funciones predefinidas las que forman parte del propio lenguaje de programación.

Los lenguajes e y C++ disponen de pocas funciones predefinidas (a cambio ofrecen una gran variedad de operadores). Además, estas funciones predefinidas sólo resultan útiles en un uso avanzado del lenguaje. Las funciones predefinidas son, en general, pseudofunciones. Esto es particularmente cierto para las funciones que usan tipos como argumentos o en la" que el tipo del argumento no está totalmente determinado (por ejemplo, admiten cualquier tipo numérico).

### **7.2.4 Funciones estándar**

Al realizar programas en C± podremos utilizar funciones que estén definidas en módulos ya redactados de antemano. Algunos módulos constituyen librerías estándar y están disponibles en la mayoría de los compiladores de C/C++.

Las funciones definidas en módulos estándar se denominan funciones estándar y pueden ser utilizadas sin necesidad de escribir su definición, pero a diferencia de las funciones predefinidas hay que indicar expresamente que se van a utilizar dichos módulos de librería mediante la directiva **#include** del correspondiente módulo que las contenga.

En lo referente a funciones matemáticas, se dispone del módulo estándar **math**. Para utilizar sus funciones habrá que incluir la directiva #inc1ude<math.h>.

## **7. 3 Procedimientos**      

Un _procedimiento_ es un subprograma que realiza una determinada acción. A diferencia de las funciones, un procedimiento no tiene como objetivo, en general, devolver un valor obtenido por cálculo.

Un procedimiento es una forma de subprograma que agrupa una sentencia o grupo de sentencias que realizan una acción, y permite darles un nombre por el que se las pueden identificar posteriormente. Estas sentencias, al igual que las funciones, se pueden parametrizar mediante una serie de argumentos. Así otra forma de ver a los procedimientos es como _acciones parametrizadas._

### **7.3.1 Definición de procedimientos**

La definición en C± de un procedimiento es prácticamente igual a la de una función:

void NombreProcedimiento ( Tipo1 argum1 , Tipo2 argum2, ... ) Bloque

La diferencia principal es que no se declara el tipo de valor del resultado, ya que no existe dicho valor. La palabra reservada **void** es la que indica que no hay resultado de ningún tipo. Además, con cierta frecuencia interesa definir procedimientos sin argumentos. En estos casos sólo es necesario dar el nombre, y no habrá lista de argumentos entre los paréntesis.

Si se desea, en la definición de un procedimiento pueden usarse también sentencias de retorno, pero con un significado algo diferente que en el caso de las funciones. La sentencia **return**;

Se escribe ahora simplemente así, sin ninguna expresión que la acompañe, ya que no hay ningún valor que devolver. Esta sentencia sirve simplemente para terminar la ejecución del procedimiento en ese momento, y volver al punto siguiente a donde se invocó.  

### **7.3.2 Uso de procedimientos**

Para usar un procedimiento hay que invocarlo. Dicha invocación o llamada constituye por sí sola una sentencia de C+-, cuyo formato es:

NombreProcedimiento( argumento1 , argumento2, );

De forma simplificada, la invocación de un procedimiento produce un efecto análogo a la secuencia de acciones siguientes:

1. Se evalúan las expresiones de los valores de los argumentos.

2. Se asignan dichos valores a los correspondientes argumentos formales.

3. Se ejecuta el código de la definición del procedimiento, hasta alcanzar el final del bloque o una sentencia de retorno.

4. El programa que invocó al procedimiento continúa en el punto siguiente a la sentencia de llamada.

### **7.3.3 Procedimientos estándar**

Al igual que para las funciones, en los módulos estándar asociados a cada compilador de C;C++ se dispone de diversos procedimientos estándar que pueden utilizarse sin más que hacer uso de la directiva #include del correspondiente módulo. En particular ya se han mencionado y utilizado los procedimientos estándar de lectura de datos o escritura de resultados, que están disponibles tras incluir la cabecera <stdio.h> .

## **7.4 Paso de argumentos**

La manera fundamental de comunicar información entre las sentencias de un subprograma y el programa que lo utiliza es mediante los argumentos.

### **7.4.1 Paso de argumentos por valor**

Esta es la forma utilizarla en los ejemplos que se han mencionado hasta el momento. Los argumentos representan valores que se transmiten desde el programa que llama hacia el subprograma. En el caso de las funciones hay además un valor de retorno, que es el valor de la función que se transmite desde el subprograma hacia el programa que lo llamó. Los argumentos reales en la llamada al subprograma pueden darse en general en forma de expresiones, cuyos tipos de valor deben ser compatible en asignación con los tipos de los argumentos formales.

==El modo de paso por valor implica que los elementos usados como argumentos en la llamada al subprograma no pueden ser modificados por la ejecución de sentencias del subprograma.== Esto es cierto incluso en el caso de que en el subprograma se ejecuten asignaciones a los argumentos formales, considerados como variables locales dentro del subprograma.

El paso de argumentos por valor puede describirse de la siguiente manera:

1. Se evalúan las expresiones de los argumentos reales usados en la llamada.

2. Los valores obtenidos se copian en los argumentos formales.

3. Los argumentos formales se usan como variables dentro del subprograma. Si a estas variables se les asignan nuevos valores, no se estará modificando el argumento real, sino sólo la copia.

### **7.4.2 Paso de argumentos por referencia**

En ciertos casos es deseable que el subprograma pueda modificar las variables que se usen como argumentos. Esto permite producir simultáneamente varios resultados y no sólo uno.

==El paso de un argumento por referencia se indica en la cabecera del subprograma, anteponiendo el símbolo & al nombre del argumento formal:==

_TipoResultado Nombre( TipoArgumento & argumento. . . . )_

Si un argumento se pasa por referencia ya no será válido usar como argumento real una expresión. El argumento real usado en la llamada debe ser necesariamente una variable del mismo tipo. Esta variable será utilizada en el subprograma como si fuera suya, es decir, la asignación de nuevo valor al argumento modifica realmente la variable externa pasada como argumento. El paso de argumentos por referencia puede describirse de la siguiente manera:

1. Se seleccionan las variables usadas como argumentos reales.

2. Se asocia cada variable con el argumento formal correspondiente.

3. Se ejecutan las sentencias del subprograma como si los argumentos formales fuesen los argumentos reales.

## **7.5 Visibilidad. Estructura de bloques**

La definición de un subprograma está formada por una cabecera o interfaz y un bloque de código que es el cuerpo del subprograma. Ese bloque de código constituye una barrera de visibilidad que hace que los elementos declarados en el interior del cuerpo de un subprograma sean visibles desde el exterior.

Los elementos definidos en el ámbito más externo son _elementos globales_, mientras que los elementos definidos en el interior del bloque de un subprograma son _elementos locales_ a dicho subprograma. Los elementos locales de un bloque son invisibles desde el exterior del bloque y dejan existir al finalizar la ejecución del bloque.

El contenido lógico de la interfaz es Jo que se denomina signatura del subprograma, que es suficiente para comprobar si las invocaciones son consistentes con su definición:
![[Pasted image 20241203162329.png]]
Finalmente hay que mencionar el caso especial de la sentencia for de C±. En ella se declara la variable contador del bucle en la misma sentencia, y establece un ámbito local limitado en el cual es visible dicha variable contador. De hecho, al terminar la ejecución del bucle la variable contador desaparece.

## **7.6 Recursividad de subprogramas**

Un caso especial que no ha sido considerado hasta este momento es la posibilidad de que en un subprograma se haga uso de ese mismo subprograma. Cuando un subprograma hace una llamada a sí mismo se dice que es un _subprograma recursivo_.

## **7.7 Problemas en el uso de subprogramas**

### **7.7.1 Uso de variables globales. Efectos secundarios**

Ya se ha comentado que uno de los objetivos de la programación es la claridad código desarrollado, es decir, que sea fácil de entender. En el caso de los subprogramas una cualidad deseable para ello es lo que se denomina _transparencia referencial_, que consiste en que el efecto de una llamada al subprograma pueda predecirse simplemente con la información contenida en el código de la llamada. Dicho de otro modo, siempre que se invoque al subprograma con los mismos valores de los argumentos se debe obtener el mismo resultado.

==Cuando un programa modifica alguna variable externa, se dice que está produciendo _efectos secundarios_== o laterales (en inglés _side effects_). El uso de subprogramas con efectos secundarios debe con precaución.

==Una función que no produzca efectos laterales y todos sus argumentos se pasen por valor se dice que es una _función pura_.==

### **7.7.2 Redefinición de elementos**

Dentro de cada bloque se pueden definir elementos locales dándoles el nombre que se considere más adecuado en cada caso. Los nombres locales no afectan al código fuera del bloque, ya que no son visibles. Incluso es posible repetir el mismo nombre para elementos diferentes definidos en distintos bloques. Por ejemplo, es habitual utilizar las variables de nombres i , j , k, etc. para los índices de las sentencias de iteración. Si estos nombres repetidos están en distintos bloques no existe ningún problema pues en cada uno de ellos estas variables tienen un carácter local que no afecta a las definiciones de los otros bloques.

Sin embargo, cuando en el interior de un bloque se define un elemento local con el mismo nombre que otro elemento global la situación es algo distinta. De acuerdo con las reglas de visibilidad, cualquier bloque tiene acceso a todos elementos globales. Sin embargo, al dar un nombre ya utilizado como global a un nuevo elemento local del bloque se está redefiniendo dicho nombre, y automáticamente se pierde la posibilidad de acceso al elemento global del mismo nombre. Se dice que el nombre local oculta o "hace sombra" (en inglés shadow) al nombre global.

### **7.7.3 Doble referencia**

Se produce doble referencia (en inglés aliasing) cuando una misma variable se referencia con dos nombres distintos, cosa que puede ocurrir en la invocación de subprogramas con argumentos pasados por referencia. Fundamentalmente, esto puede ocurrir en dos situaciones muy concretas:

1. Cuando un subprograma utiliza una variable externa que también se le pasa como argumento. 2. Cuando para utilizar un subprograma se pasa la misma variable en dos o más argumentos.

Como conclusión se puede decir que no se debe utilizar la doble referencia, salvo que el subprograma se diseñe pensando en esa posibilidad.

# Tema 8 Metodología de Desarrollo de Programas (III)

## **8. 1 Operaciones abstractas**

Una abstracción es una visión simplificada de una cierta entidad, de la que sólo consideramos sus elementos esenciales, prescindiendo en lo posible de los detalles. Las entidades que podernos abstraer para materializarlas como subprogramas son, en general, operaciones. Con la palabra operación englobamos &anta la idea de acción como la de función.

## **8.1.1 Especificación y realización**

Al plantear operaciones abstractas habremos de definir dos posibles visiones. La visión abstracta o simplificada, y la visión detallada, completa. La visión abstracta es la que permite usar dicha operación sin más que conocer qué hace dicha operación. La visión detallada es la que define cómo se hace dicha operación, y permite que el procesador la ejecute. La primera visión representa el punto de vista de quienes han de utilizar la operación. Se dice que esa visión abstracta ~ la especificación o interfaz de la operación. La visión detallada representa el punto de vista de quien ha de ejecutar dicha acción, y se dice que expresa su realización o implementación.

==Especificación: Qué hace la operación (punto de vista de quien la invoca).

Realización: Cómo se hace la operación (punto de vista. de quien la ejecuta)==

En C± la especificación puede ser simplemente una cabecera de subprograma. Esa forma simplificada de especificación indica solamente cuál ha de ser la _sintaxis_ o forma de uso de la operación

La _especificación_ completa debe establecer también cuál es la _semántica_ o significado de la operación. Para ello podemos añadir un comentario en que se indique qué relación hay entre los argumentos y el resultado de la operación.

La _realización_, por su parte, debe suministrar toda la información necesaria para poder ejecutar la operación. En C± la realización o implementación será. la definición completa del subprograma, en forma de bloque de código.
![[Pasted image 20241203162509.png]]
Con ello se pone de manifiesto la idea de que la especificación es una visión abstracta de qué hace la función, con independencia de los detalles de cómo lo hace.

### **8.1.2 Funciones. Argumentos**

En programación la idea de función surge al aplicar el concepto de abstracción a las expresiones aritméticas. Una expresión representa un nuevo valor obtenido por cálculo a partir de ciertos valores ya conocidos que se usan como operandos.

Si buscamos que el concepto de función en programación se aproxime al concepto matemático de función, el paso de argumentos debería ser siempre por valor. El concepto matemático de función es una aplicación entre conjuntos, cuyo cómputo se limita a suministrar un resultado, sin modificar el valor de los argumentos.

Desde el punto de vista de claridad del programa, y con independencia de cuál sea el mecanismo de paso de argumentos empleado, la cualidad más deseable al utilizar funciones es conseguir su _transparencia referencial_. Tal como se mencionó anteriormente, ==la transparencia referencial significa que la función devolverá siempre el mismo resultado cada vez que se la invoque con los mismos argumentos.==

La transparencia referencial se garantiza si la realización de la función no utiliza datos exteriores a ella. Es decir, si no emplea:

- Variables externas al subprograma, a las que se accede directamente por su nombre, de acuerdo con las reglas de visibilidad de bloques.

- Datos procedentes del exterior, obtenidos con sentencias de lectura.

- Llamadas a otras funciones o procedimientos que no posean transparencia referencial. Las sentencias de lectura son en realidad un caso particular de éste.

### **8.1.3 Acciones abstractas. Procedimientos**

De manera similar a como las funciones pueden ser consideradas como expresiones abstractas, parametrizadas, los procedimientos pueden ser considerados como _acciones abstractas_, igualmente _parametrizadas_. ==Un procedimiento representa una acción, Que se define por separado, y que se invoca por su nombre.==

Como acciones abstractas, podemos tener dos visiones de un procedimiento. La primera es la visión abstracta o _especificación_, formada por la cabecera del procedimiento y una descripción de qué hace dicho procedimiento, y la segunda es la _realización_, en que se detalla, codificada en el lenguaje de programación elegido, cómo se hace la acción definida como procedimiento.

Al definir procedimientos no podemos limitarnos a usar sólo el paso de argumentos por valor. ==En programación imperativa las acciones consisten habitualmente en modificar los valores de determinadas variables. ==Por esta razón considera normal que los procedimientos usen argumentos pasados por referencia. De todas maneras, conviene seguir una cierta disciplina para que los programas resulten claros y fáciles de entender. Para ello podemos recomendar que los procedimientos se escriban siempre como procedimientos puros, entendiendo por ello que no produzcan efectos laterales o secundarios. Con esto se consigue que la acción que realiza un procedimiento se deduzca en forma inmediata de invocación de dicha acción. Se garantiza que un procedimiento cumple con esta. cualidad si su realización no utiliza:

- Variables externas al subprograma, a las que se accede directamente por su nombre, de acuerdo con las reglas de visibilidad de bloques.

- Llamadas a otros subprogramas que no sean procedimientos o funciones puras.

## **8.2 Desarrollo usando abstracciones**

### **8.2.1 Desarrollo descendente**

==La estrategia de desarrollo descendente (en inglés, Top-Down), es simplemente el desarrollo por refinamientos sucesivos, teniendo en cuenta además la posibilidad de definir operaciones abstractas. ==En cada etapa de refinamiento de una operación habrá que optar por una de las alternativas siguientes:

- Considerar la operación como operación terminal, y codificarla mediante sentencias del lenguaje de programación.

- Considerar la operación como operuci6n compleja, y descomponerla en otras más sencillas.

- Considerar la operación como operación abstracta, y especificarla, escribiendo más adelante el subprograma que la realiza

En general resultará ventajoso refinar una operación como operación abstracta, que se define en forma separada, si se consigue alguna de las ventajas siguientes:

- Evitar mezclar en un determinado fragmento de programa operaciones con un nivel de detalle muy diferente.

- Evitar escribir repetidamente fragmentos de código que realicen operaciones análogas.

El beneficio obtenido es, corno cabría esperar, una mejora en la claridad del programa. Hay que decir que esto i==mplica un costo ligeramente mayor en términos de eficiencia, ya que siempre se ejecuta más rápidamente una operación si se escriben directamente las sentencias que la realizan, que si se invoca ml subprograma que contiene dichas sentencias.== La. llamada al subprograma representa una acción adicional que consume un cierto tiempo de ejecución. ==Por el contrario, hay un aumento de eficiencia en ocupación de memoria si se codifica como subprograma una operación que se invoca varias veces en distintos puntos del programa.==

### **8.2.4 Reutilización**

La realización de ciertas operaciones como subprogramas independientes facilita lo que se llama _reutilización de software_. Si la operación identificada como operación abstracta tiene un cierto sentido en sí misma, es muy posible que resulte de utilidad en otros programas, además de en aquél para el cual se ha desarrollado.

### **8.2.6 Desarrollo para reutilización**

Para aplicar de manera eficaz las técnicas de reutilización de software es preciso pensar en las posibles aplicaciones de un cierto subprograma en el momento de especificarlo, con independencia de las necesidades particulares del programa que se está desarrollando en ese momento.

Esta estrategia de desarrollo tiene ventajas e inconvenientes. La principal ventaja es que se amplía el conjunto de aplicaciones en que se podrá reutilizar adelante el subprograma que se está desarrollando ahora. Su principal inconveniente es que será más costoso hacer el desarrollo del subprograma planteado como operación de uso general, que planteado como operación particular hecha a medida del programa que lo utiliza en este momento.

### **8.2.7 Desarrollo ascendente**

==La metodología de _desarrollo ascendente_ (en inglés _Bottom-Up_) consiste en ir creando subprogramas que realicen operaciones significativas de utilidad para el programa que se intenta construir, hasta que finalmente sea posible escribir el programa principal, de manera relativamente sencilla, apoyándose en los subprogramas desarrollados hasta ese momento.==

## **8.3 Programas robustos**

==Un programa se dice que es un programa robusto si su operación se mantiene en condiciones controladas aunque se le suministren datos erróneos.==

### **8.3.1 Programación a la defensiva**

La llamada _programación a la defensiva_ (en inglés, _defensive programming_(, consiste en que cada programa o subprograma esté escrito de manera que desconfíe sistemáticamente de los datos o argumentos con que se le invoca, y devuelva siempre como resultado:

a)      El resultado correcto, si los datos son admisibles

b)      Una indicación precisa de error, si los datos no son admisibles.

Lo que no debe hacer nunca el programa es devolver un resultado como si fuese normal, cuando en realidad es erróneo, ni "abortar".

### **8.3.2 Tratamiento de excepciones**

Ante la posibilidad de errores en los datos con que se opera, hay que considerar dos actividades diferentes:

1.      Detección de la situación de error.

2.      Corrección de la situación de error

Si una operación se ha escrito como subprograma, la programación a la defensiva recomienda que la primera actividad (detección del posible error) se haga dentro del subprograma, sin confiar en que quienes usen el subprograma lo invoquen siempre con datos correcto. Existen varios esquemas de programación posibles para tratamiento de errores. Un modelo recomendado es el _modelo de terminación_. En este modelo, si se detecta un error en una sección o bloque del programa, la acción de tratamiento del error reemplaza al resto de las acciones pendientes de dicha sección, con lo cual tras la acción correctora se da por terminado el bloque.

La sentencia throw provoca la terminación del subprograma de manera semejante a una sentencia return. Sin embargo, ambas terminaciones son distintas: con return se realiza una terminación normal y con throw se realiza una terminación por excepción. La sentencia throw puede devolver cualquier tipo de resultado en excepción. Además, la sentencia throw es la encargada de indicar que se ha detectado una situación de error y lanzar el mecanismo de tratamiento de excepciones.

Con las herramientas convencionales de un lenguaje de programación, el esquema típico para el tratamiento de excepciones sería el siguiente:

Algoriutmo del Problema (inicio);

OperaciónRobusta (argumentos ) ;

If (Excepción) {

            Tratamiento de la Excepción

}

Algoritmo del Problema (continuación)

Este esquema tiene el inconveniente de que hay que insertar el tratamiento la excepción en medio del código del algoritmo del problema que se está resolviendo. Esta mezcla del código normal y el código excepcional disminuye claridad del programa. Las sentencias disponibles en C± para el manejo de excepciones permiten separar ambos códigos siguiendo el siguiente esquema:

Try {

            Algoritmo del Problema (inicio);

OperaciónRobusta (argumentos);

Algoritmo del Problema (continuación);

}

Catch (Excepción){

Tratamiento de la Excepción

}

# Tema 9 Definición de tipos

## **9.1 Tipos definidos**

Mediante la definición de nuevos tipos de daos por el programador se consigue que cada información que maneja el computador tenga su sentido específico. ==El tipo establece los posibles valores que puede tomar ese dato, la definición de tipos supone crear un lluevo nivel de abstracción dentro del programa.==

En C± la declaración de los tipos se realiza, junto a la declaración de las constantes y variables, dentro de las _Declaraciones_ del programa principal o en cualquiera de sus procedimientos o funciones. Asimismo, en C± la declaración de cada nuevo tipo siempre se inicia con la palabra clave typedef. Por ejemplo:

typedef int TipoEdad;

En estas declaraciones se definen nuevos tipos dándoles un nombre o identificador y haciéndolos equivalentes o sinónimos de otros tipos ya definidos.

En algunos lenguajes de programación, tales como Pascal, Modula-2 o Ada, se puede acotar el rango de valores de un tipo de datos a partir de otro en el momento de la declaración. Lamentablemente, en C± sólo es posible acotar el rango de valores de un dato haciendo las correspondientes comprobaciones dentro del código del programa.

De manera formal, la sintaxis de la declaración de tipos es la siguiente:
![[Pasted image 20241203162921.png]]
El tipo sinónimo ya ha sido utilizado en los ejemplos anteriores para introducir el concepto de tipo de dato. Formalmente la declaración de un tipo sinónimo la siguiente:
![[Pasted image 20241203162927.png]]
El tipo sinónimo puede parecer trivial, sin embargo, tiene una utilidad bastante importante ==como mecanismo de parametrización del programa==. Al igual que sucedía con las constantes con nombre, en un programa pueden utilizar sólo tipos con nombres propios. Por ejemplo:

typedef int entero;

typedef char caracter;

typedef float real;

Estos nuevos tipos entero, caracter y real sustituyen a los predefinidos del lenguaje y son los únicos que se utilizarán en nuestro programa. Cuando se cambia de compilador para transportar el programa a otra plataforma o se quiere cambiar la precisión de los cálculos sólo es necesario modificar en estas sentencias de parametrización los tipos haciéndolos sinónimos de otros diferentes.

## **9.2 Tipo enumerado**

### **9.2.1 Definición de tipos enumerados**

Una manera sencilla de definir un nuevo tipo de dato es enumerar todos los posibles valores que puede tomar. En C± el nuevo tipo enumerado se define detrás de la palabra clave enum mediante un identificador del tipo y a continuación se detalla la lista con los valores separados por comas ( ,) y encerrados entre llaves {…}. Cada posible valor también se describe mediante un identificador. Estos identificadores al mismo tiempo quedan declarados como valores constantes.
![[Pasted image 20241203163002.png]]
==La enumeración implica un orden que se establece entre los valores enumerados. ==En C este orden se define de forma implícita e impone que el primer elemento de la lista ocupa la posición 0, el siguiente la 1, y así sucesivamente hasta el último, que ocupa la posición N-l, siendo N el número de elementos enumerados. Los tipos de datos enumerados forman parte de una clase de tipos de C+- denominados _tipos ordinales_, a la cual pertenecen también los tipos int y char, pero no el tipo fIoat.

La sintaxis exacta de la declaración de los tipos enumerados es la siguiente:
![[Pasted image 20241203163027.png]]
### **9.2.2 Uso de tipos enumerados**

Al igual que para el resto de los tipos ordinales, con los tipos enumerados se puede utilizar la notación int(e) para obtener la posición de un valor en la lista de valores del tipo.

La operación inversa, que permita conocer qué valor enumerado ocupa una determinada posición, se consigue mediante la notación inversa que hace uso del identificador del tipo enumerado y que se invoca de la siguiente forma: TipoEnumerado(_N_) que devuelve el valor que ocupa la posición _N_ en la colección de valores del cipo TipoEnumerado.

## **9.3 El tipo predefinido bool**

typedef enwn bool { false, true };

Esta definición no es necesario escribirla ya que está implícita en el lenguaje. El nombre bool es el identificador del tipo (abreviatura de booleano), y las constantes simbólicas _false_ y _true_ corresponden a los valores de verdad falso y cierto, respectivamente. Como tipo ordinal se cumple:

int(false) == 0

int(true) == 1

A partir del tipo predefinido bool, ahora es posible declarar variables de este tipo y utilizarlas, de forma similar al resto de variables, para guardar resultados de expresiones condicionales. Por ejemplo:

bool bisiesto;

bisiesto = (anno % 4) == 0;

Asimismo, es posible realizar operaciones entre ellas. En concreto, entre operandos booleanos (variables o no) es posible realizar las operaciones lógicas.
![[Pasted image 20241203163051.png]]
El tipo booleano, como cualquier otro tipo enumerado, se puede pasar como argumento de un procedimiento o función y puede ser devuelto como resultado de una función. ==De hecho, es frecuente definir funciones cuyo resultado es un valor booleano cuando se quiere realizar un test sobre los argumentos de la función. Este tipo de funciones se denominan _predicados_.==
![[Pasted image 20241203163105.png]]
Conviene recordar que para poder usar estas funciones predicado es necesario incluir la cabecera. de librería al comienzo del programa.

## **9.4 Tipos estructurados**

Todos los tipos de datos presentados hasta este momento se denominan ==_tipos escalares_ y son datos simples, en el sentido de que no se pueden descomponer.==

==Un _tipo estructurado_ de datos, o estructura de datos, es un tipo cuyos valores construyen agrupando datos de otros tipos más sencillos. ==Los elementos de información que integran un valor estructurado se denominan componentes. Todos los tipos estructurados se definen, en último término, a partir de tipos simples combinados.

## **9.5 Tipo formación y su necesidad**

Estas estructuras se denominan genéricamente _formaciones_ (en inglés _array_), y permiten la generalización de la declaración, referencia y manipulación de colecciones de datos todos del mismo tipo.

## **9.6 Tipo vector**

Un vector está constituido por una serie de valores, todos ellos del mismo tipo, a los que se les da un nombre común que identifica a toda la estructura globalmente. Cada valor concreto dentro de la estructura se distingue por su índice o número de orden que ocupa en la serie.
![[Pasted image 20241203163143.png]]
Esta estructura es análoga al concepto matemático de vector, en el que el vector completo se identifica por un nombre único y cada elemento particular mediante el correspondiente subíndice: V = (V0, V1, V2 , V3 .. .. , Vn- 2 , Vn-1)

### **9.6.1 Declaración de vectores**

En C±, una estructura de tipo vector se declara de la siguiente forma:
![[Pasted image 20241203163158.png]]
Donde _TipoVector_ es el nombre del nuevo tipo de vector que se declara y _NumeroElementos_ es un valor constante que indica el número de elementos que constituyen el vector. Por tanto, la variabilidad del índice de un vector siempre estará comprendida entre 0 y _NumeroElementos_ -1. Finalmente, _TipoElemento_ corresponde al tipo de dato de cada uno de los elementos del vector y puede ser cualquier tipo de dato predefinido del lenguaje o definido por el programador.

En muchos casos el tamaño del vector es un parámetro del programa que podría tener que cambiarse al adaptarlo a nuevas necesidades. Si es así, resulta aconsejable que la declaración del número de elementos se realice como una constante con nombre.

La sintaxis exacta de la declaración de los tipos formación es la siguiente:
![[Pasted image 20241203163206.png]]
### **9.6.2 Inicialización de un vector**

En el caso de un vector la inicialización afecta a todos sus elementos y por tanto la notación es algo especial y en ella se indica el valor inicial de todos los elementos agrupándolos entre llaves { ... } y separándolos por comas (,).

TipoAgenda agendaUno = {

Lunes, Viernes, Domingo, Martes, Martes, Martes, Sabado

};

### **9.6.3 Operaciones con elementos de vectores**

La mayoría de las operaciones interesantes con vectores hay que realizarlas operando con sus elementos uno por uno. La referencia a un elemento concreto de un vector se hace mediante el nombre del vector seguido, entre corchetes, del índice del elemento referenciado.

Es especialmente importante insistir en que al usar lenguajes como C, C++ o C± la comprobación de que el Índice para acceder a un elemento de vector está dentro del rango permitido es responsabilidad del programador. Muchos ataques informáticos aprovechan la falta de previsión de esta comprobación para alterar el funcionamiento normal de un programa suministrándole datos de mayor tamaño que el previsto y provocar lo que se denomina en inglés _buffer overrun_.

### **9.6.4 Operaciones globales con vectores**

En lenguajes tales como Pascal, Modula-2, Ada, etc. existe la posibilidad de realizar una asignación global de un vector a otro, siempre que estos sean compatibles entre sí.

Sin embargo, en C± no existe esta posibilidad y la asignación se tiene que programar explícitamente mediante un bucle que realice la copia elemento a elemento.
![[Pasted image 20241203163229.png]]
La sintaxis completa de esta sentencia es la siguiente:
![[Pasted image 20241203163243.png]]
### **9.6.5 Paso de argumentos de tipo vector**

Otra manera habitual de operar globalmente con los vectores es utilizarlos como argumentos de procedimientos o funciones.

Así, en C± el modo por defecto de paso de argumentos de tipo formación , y más concretamente de tipo vector, es el paso por referencia.

Cuando se invocan estos procedimientos, además de emplear en la llamada argumentos reales que deben ser compatibles con el correspondiente argumento formal, hay que tener en cuenta que el argumento real puede ser modificado.

Las variables vectorUno y estadoMotor podrán quedar modificadas después de ejecutar el correspondiente procedimiento.

==En C+-, cuando se utilizan argumentos de tipo formación y no se quiere que se modifiquen los parámetros reales en la llamada al procedimiento, los argumentos formales deben ir precedidos de la palabra clave _const_.==

Cuando declaramos argumento de tipo formación o vector precedido de la palabra clave const equivalente al paso de dicho argumento por valor.

## **9.7 Vector de caracteres: Cadena (string)**

En C± cualquier tipo vector cuya declaración sea de la forma:

typedef char Nombre[ N ]

Se considera una cadena o _string_, con independencia de su longitud particular, esto es, del valor de N. Por tanto, el tipo definido en el apartado anterior TipoCadena es una cadena. La característica peculiar de las cadenas es la siguiente:

==Una cadena de caracteres (en inglés string) es un vector en el que se pueden almacenar textos de diferentes longitudes (si caben). Para distinguir la longitud útil en cada momento se reserva siempre espacio para un carácter más, y se hace que toda cadena termine con un carácter `\0` situado al final. ==Por tanto, para declarar una cadena de un máximo de veinte caracteres se hacer de la siguiente forma:

typedef char Cadena20[21];

Como la utilización de cadenas de caracteres es bastante habitual, el lenguaje C (y C±) dispone de la librería string (cabecera <string.h>) que facilita el manejo de cadenas.
![[Pasted image 20241203163333.png]]
Al igual que con cualquier otro tipo de vector, no es posible realizar asign. dones globales entre cadenas.

Para realizar esta operación usando el procedimiento general se programaría un for que copie elemento a elemento tal como se ha explicado en el apartado anterior. ==Sin embargo, esta operación se puede realizar utilizando la función de librería st rcpy tal y como se muestra a continuación:==

`apellido = "González";` ERROR en C±

 `nombre = apellido;` ERROR en C±

``strcpy( apellido, "González" );

`strcpy( nombre, apellido ) :

Al igual que las constantes, también cualquier variable de tipo cadena se puede utilizar como argumento de procedimientos o funciones. Más concretamente, en el procedimiento de escritura printf se pueden utilizar constantes o variables de cadena empleando el formato de escritura %s para string o cadena. Por ejemplo:

 printf("Datos: %s - %s : %s %s\n", idioma, direccion, "José", apellido);

También es posible utilizar variables de tipo cadena con el procedimiento de lectura scanf utilizando también el formato de lectura %s para string o cadena. Por ejemplo, sea el siguiente fragmento de código:

printf("Nombre y Apellido? ");

scanf("%s%s", &nombre, &apellido);

Con ello se guardan en las variables nombre y apellido las cadenas "José" y "González" introducidas por teclado.

## **9.8 Tipo tupla y su necesidad**

Otra forma de construir un dato estructurado consiste en agrupar elementos de información usando el esquema de tupla o agregado. En este esquema el dato estructurado está formado por una colección de componentes, cada uno de los cuales puede ser de un tipo diferente.

==Tupla: Colección de elementos componentes, de diferentes tipos, cada uno de los cuales se identifica por un nombre.==

Un aspecto importante del empleo de datos estructurados corresponde al punto de vista de abstracción. Una tupla, como cualquier otro dato compuesto, puede verse de forma abstracta como un todo, prescindiendo del detalle de sus componentes. La posibilidad de hacer referencia a toda la colección de elementos mediante un nombre único correspondiente al dato compuesto simplifica al muchos casos la escritura del programa que lo maneja.

## **9.9 Tipo registro (_struct_)**

Los esquemas de tupla pueden usarse en programas en C± definiéndolos como estructuras del tipo _registro_ o struct. Un registro o struct es una estructura de datos formada por una colección de elementos de información llamados _campos_.

### **9.9.1 Definición de registros**

La declaración de un tipo registro en C± se hace utilizando la palabra clave struct de la siguiente la forma:
![[Pasted image 20241203163517.png]]
Cada una de las parejas Tipo- campo y nombre-campo, separadas por punto y coma (;), define un campo o elemento componente y su correspondiente tipo. Además, hay que tener en cuenta que la estructura acaba siempre con punto y coma (;)
![[Pasted image 20241203163525.png]]
La sintaxis de la declaración de los tipos registro es la siguiente:
![[Pasted image 20241203163534.png]]
### **9.9.2 Variables de tipo registro y su inicialización**

Como siempre, para declarar variables de tipo registro es necesario haber inicializado previamente la definición del tipo del registro. A continuación se detalla una declaración de variables:

TipoFecha ayer, hoy;

TipoPunto punto1, punto2;

También estas variables se pueden inicializar en la declaración de una manera semejante a las formaciones agrupando los valores iniciales entre llaves { . .. } . separándolos por una coma (,), pero teniendo en cuenta el tipo de dato de cada. campo. A continuación, se declaran nuevamente alguna de las variables anteriores incluyendo su inicialización.

TipoFecha hoy = { 12, Marzo, 2009 };

TipoPunto punto1 = { 12. 5, -76 .9 };

### **9.9.3 Uso de registros**

Al manejar datos estructurados de tipo registro se dispone de dos posibilidades: operar con el dato completo, o bien operar con cada campo por separado. Las posibilidades de operar con el dato completo son bastante limitadas. La única operación admisible es la de asignación. El valor de un dato de tipo registro asignarse directamente a una variable de su mismo tipo. Por ejemplo, las definiciones anteriores es posible escribir:

punto2 = punto1;

En estas asignaciones debe cumplirse la compatibilidad de tipos.

Las operaciones de tratamiento de estructuras registro consisten normalmente en operar con sus campos por separado. La forma de hacer referencia a un campo es mediante la notación:

 _registro. Campo_

Cada campo se puede usar como cualquier otro dato del correspondiente tipo.

# Tema 10 Ampliación de estructuras de control

## **10.1 Estructuras complementarias de iteración**

### **10.1.1 Repetición: Sentencia DO**

A veces resulta más natural comprobar la condición que controla las iteraciones al finalizar cada una de ellas, en lugar de hacerlo al comienzo de las mismas. En este caso, siempre se ejecuta al menos una primera iteración.
![[Pasted image 20241203163613.png]]
El formato de la estructura. de repetición en C± es el siguiente:
![[Pasted image 20241203163621.png]]
La Condición que controla las repeticiones es una expresión cuyo resultado un valor de tipo bool. Si el resultado es true se vuelve a ejecutar la Acción y cuando el resultado es false finaliza la ejecución de la estructura.

### **10.1.2 Sentencia CONTINUE**

La sentencia continue dentro de cualquier clase de bucle (while, for o do) finaliza la iteración en curso e inicia la siguiente iteración. A veces, dependiendo de la evolución de los cálculos realizados en una iteración, no tiene sentido completar la iteración que se está realizando y resulta más adecuado iniciar una nueva. Esto puede suceder cuando alguno de los datos suministrados para realizar un cálculo es erróneo y puede dar lugar a una operación imposible (división por cero, raíz de un número negativo, etc.). En este caso lo adecuado es detectar la situación y dar por finalizada la iteración e iniciar una nueva iteración con nuevos datos de partida.

## **10.2 Estructuras complementarias de selección**

### **10.2.1 Sentencia SWITCH**

Cuando la selección entre varios casos alternativos depende del valor que toma una determinada variable o del resultado final de una expresión, es necesario realizar comparaciones de esa misma variable o expresión con todos los valores puede tomar, uno por uno, para decidir el camino a elegir.

Si lo que se necesita es comparar el resultado de una expresión, dicha expresión se reevaluará tantas veces como comparaciones se deben realizar (a menos que disponga de un compilador optimizante).

Si el tipo de valor que determina la selección es un tipo ordinal: int, char o enumerado, se dispone en C± de la sentencia switch cuya estructura permite agrupar los casos que tienen el mismo tratamiento y en la que se evalúa solamente una vez la expresión x.
![[Pasted image 20241203163658.png]]
En la sentencia switch se deben incluir todos los posibles valores que tomar la variable o expresión. Cuando se obtiene un valor que no está asociado a ninguna vía (y no hay alternativa default), el programa finaliza por error. Si lo que sucede es que existen valores para los que no se debe realizar ninguna acción, entonces estos valores se deben declarar asociados a una acción.

Otra forma de conseguir esto mismo es mediante \lila alternativa default vacía utilizando sólo un punto y coma ( ;).

Para acabar este apartado se detalla la sintaxis formal de la sentencia switch do C+-:
![[Pasted image 20241203163711.png]]
# Tema 11 Estructuras de datos
## 11.1 Argumentos de tipo vector abierto
Si un subprograma debe operar con un vector recibido como argumento, necesita toda la información del tipo de dicho vector, es decir, el tipo y número de sus elementos.
En la práctica no tiene sentido tener que duplicar el código sólo porque cambia el valor de una constante. Más razonable es escribir un procedimiento general de escritura de vectores de números enteros, y pasar como parámetro el tamaño del vector. Para eso hace falta un mecanismo para expresar que un argumento de tipo vector puede tener un tamaño cualquiera, es decir, indefinido. Los vectores con un tamaño indefinido se denominan *vectores abiertos*.
En C:I: los argumentos de tipo vector abierto se especifican de manera similar a una declaración de tipo vector, omitiendo el tamaño explícito pero no los corchetes ([] ).
```
void EscribirVectorAbierto(const int v[], int numElementos) { 
for (int i = O; i < numElementos; i++) {
printf( "%1Od". v(i] ); 
} 
printf( "\n" ); 
}f
```
El precio que hay que pagar por disponer de esta facilidad es tener que pasar siempre la longitud concreta del vector como argumento, en cada llamada.
Por supuesto, hay otras alternativas al paso explícito de la longitud del vector. los subprogramas estándar para operar con cadenas de caracteres (strings) usan la técnica de almacenar un carácter nulo al final del valor efectivo de cada cadena. Esto exige disponer siempre de espacio para un carácter más, al menos, pero evitan tener que pasar la longitud como argumento.
## 11.2 Formaciones anidadas. Matrices
### 11.2.1 Declaración de matrices y uso de sus elementos
==Las matrices son estructuras de tipo formación (array) de dos o más dimensiones. Una forma sencilla de plantear la definición de estas estructuras es considerarlas como vectores cuyos elementos son a su vez vectores (o matrices).==
![[Pasted image 20241208222746.png]]
En la figura se presenta la matriz como un vector cuyos elementos son las filas de la matriz, que a su vez son vectores de elementos de la matriz. Usando directamente declaraciones de tipos vector podríamos escribir la declaración de una matriz de números enteros de la siguiente manera:
```
const int NumFilas = 10; 
const int NumColumnas = 15; 
typedef int TipoElemento; 
typedef TipoElemento TipoMatriz [NumFilas] [NumColumnas]; 
TipoMatriz matriz;
```
Para designar un elemento de la matriz se usará un doble subíndice: 
```
TipoMatriz matriz; 
matriz[3][5] = 27;
```
Las reglas sintácticas de la definición de formaciones de una o varias dimensiones.
![[Pasted image 20241208223317.png]]
### 11.2.2 Operaciones con matrices
Las operaciones con elementos individuales de una matriz pueden hacerse directamente, de forma análoga a la operación con variables simples de ese tipo. En cambio las operaciones globales con matrices han de plantearse de manera similar a las operaciones globales con vectores. En general habrá que operar elemento a elemento, o a lo sumo por filas completas.
Al comienzo de este tema se ha mencionado la posibilidad de definir argumentos de tipo vector como vectores abiertos, de tamaño indefinido. Podemos pensar en generalizar ese mecanismo y permitir el uso de argumentos de tipo matriz abierta. Lamentablemente los lenguajes e o C++, y por lo tanto C+-, no lo permiten.
==Si realmente se necesita definir operaciones genéricas con formaciones de dimensiones indefinidas hay que recurrir al uso explícito de punteros, tal como verá en el tema 13.==

## 11.3 El esquema unión
Hay aplicaciones en las que resultaría deseable que el tipo de un dato variase según las circunstancias. ==Si las posibilidades de variación son un conjunto finito de tipos, entonces se puede decir que el tipo del dato corresponde a un esquema que es la *unión* de los tipos particulares posibles.== Cada uno de los tipos particulares constituye una variante o alternativa del tipo unión. Representaremos simbólicamente este esquema de forma similar a las alternativas en las reglas de sintaxis BNF:
![[Pasted image 20241208223935.png]]
### 11.3.1 El tipo union
Un tipo union se define como una colección de campos alternativos, de tal manera que cada dato particular sólo usará uno de esos campos en un momento dado, dependiendo de la alternativa aplicable. La definición es similar a la de un agregado o struct.
```
typedef struct TipoFraccion {
int numerador; 
int denominador;
};
typedef union TipoNumero {
int valorEntero;
float valorReal; 
TipoFraccion valorRacional;
}; 
```

La referencia a los elementos componentes se hace también como en los tipos struct :
```
TipoNumero numero, otro, fraccionl, fraccion2;
numero.valorEntero = 33;
otro.valorReal= float (numero .valorEntero);
fraccion2 .valorRacional = fraccionl.valorRacional;
```
Si una variante de una unión es a su vez otra tupla o unión habrá que usar varios cualificadores para designar los campos anidados:
```
fraccionl.valorRaeional.numerador = 33; 
fraccion1.valorRaeional.denominador = 44;
```
Sólo una de las variantes puede estar vigente en un momento dado. Si asignamos valor a una de ellas será ésta la que exista a partir de ese momento, al tiempo que dejan de existir las demás:
```
fraeeionl.valorEntero = 22; 
printf( "%d", fraccionl.valorEntero );                /* Correcto */
printf( "%d", fraccionl.valorRacional.denominador );  /* ERROR */
```
### 11.3.2 Registros con variantes
El hecho de que un dato de tipo unión deba ir acompañado de información complementaria para saber cuál es la variante aplicable hace que los tipo unión aparezcan casi siempre formando parte de estructuras más complejas. ==Un ejemplo frecuente es lo que se denominan registros con *variantes*. Se trata de agregados o tuplas en los que hay una colección de campos fijos, aplicables en todos los casos, y campos variantes que se definen según el esquema unión. Además suele reservarse un campo fijo para indicar explícitamente cuál es la variante aplicable en cada momento. A dicho campo se le llama *discriminante*.==
```
typedef enum ClaseNumer  {Entero , Real, Fraccion};
typedef struct TipoFraccion {
	int numerador; 
	int denominador; 
};
typedef union TipoValor { 
	int valorEntero; 
	float valorReal; 
	TipoFraccion valorRacional;
};  
typedef struct TipoNumero {
	ClaseNumero clase;  /* discriminante*/ 
	 TipoValor valor;
};  
void EscribirNumero( TipoNumero n ) {
	switch (n.clase) {
	case Entero: 
		printf( "%d", n.valor.valorEntero ); 
		break; 
	case Real: 
		printf( "" f" I n.valor.valorReal ); 
		break; 
	case Fraccion: 
		printf( "%d/%d", n.valor.valorRacional.numerador,
						 n.valor.valorRacional.denominador );
		 break; 
	default: printf("????") ;
	}
```
## 11.4 Esquemas de datos y esquemas de acciones
Recordaremos que los esquemas básicos eran la *secuencia*, la *selección*, y la *iteración*, en el caso de acciones compuestas. 
Estos esquemas se corresponden, respectivamente, con los esquemas *tupla*, *unión* y *formación*, definidos para las estructuras de datos. La analogía se pone de manifiesto si describimos dichos esquemas de forma generalizada, común a los datos y acciones. 
- *Tupla - Secuencia*: Colección de elementos de tipos diferentes, combinados en un orden fijo. 
- *Unión - Selección:* Selección de un elemento entre varios posibles, de tipos diferentes.
- *Formación - Iteración*: Colección de elementos del mismo tipo.
## 11.5 Estructuras combinadas
Se pueden definir estructuras cuyas componentes son a su vez estructuras, sin límite de complejidad de los esquemas de datos resultantes.
### 11.5.1 Formas de combinación
```
typedef struct TipoPunto { 
float x, y; 
};
typedef TipoPunto TipoTriangulo[3];
const int MaxPuntos = 100;
typedef TipoPunto TipoPuntos[MaxPuntos];
typedef struct TipoListaPuntos {
int numeroPuntos; TipoPuntos puntos; 
};
typedef TipoListaPuntos Poligonal;       /* línea abierta */
typedef TipoListaPuntos Poligono;        /* linea cerrada */
```
### 11.5.2 Tablas
En otros contextos se le da también el nombre de *diccionario* o *relación*. Los esquemas de tabla son el fundamento de las bases de datos relacionales, aunque su implementación es muy diferente de las estructuras simplificadas que se presentan aquí.

Pueden construirse estructuras de datos bastante complejas combinándolas de manera que en algunas de ellas hagamos referencia a datos almacenadas en otras. Una forma de hacer referencia a los datos de una tabla es usando el índice correspondiente a la posición de cada registro.
```
typedef struct TipoPunto { 
float x, y; 
}; 
const int MaxPuntos = 1000; 
typedef int TipolndicePunto; 
typedef TipoPunto TipoTablaPuntos[MaxPuntos];

typedef TipolndicePunto TipoTriangulo[3];

typedef struct TipoCirculo {
	TipolndicePunto centro; 
	float radio; 
}; 

TipoTablaPuntos puntos;
```
En este ejemplo, la tabla puntos almacena las coordenadas de todos los puntas utilizados para definir cualquiera de las figuras geométricas que se manejan. Las figuras se definen almacenando referencias a los puntos de la tabla, en lugar de almacenar directamente las coordenadas de los puntos. Un triángulo T definido por tres puntos A, 13 Y e se podría registrar, por ejemplo, almacenando los puntos, arbitrariamente, en las posicione':> 10, 11 Y 12 de la tabla de puntos
# Tema 12 Esquemas típicos de operación con formaciones
Cuando se trabaja con colecciones de datos es habitual que las operaciones globales sobre la colección se realicen a base de operar con los elementos uno a uno. Esto exige el empleo de esquemas de programas en los que se recorren los elementos de la colección en un orden adecuado.
## 12.1 Esquema de recorrido
==El esquema de recorrido consiste en realizar cierta operación con todos y cada uno de los elementos de una formación (en algunos casos con parte de ellos).==
La forma más general del esquema de recorrido sería:
```
iniciar operación
while (quedan elementos isn tratar) {
	elegir uno de ellos y tratarlo 
}
completar operación
```
Si es aceptable tratar todos los elementos en el orden de sus índices, el esquema de recorrido se puede concretar como un bucle for, más sencillo de entender. Para el caso de un vector v (una dimensión) con un número N de elementos (los índices van de O a N-1):
```
const int N = ... ;
typedef ... T_Elemento ... ;
typedef T_Elemento T_Vector[N];
T_Vector v;
iniciar operación
for ( int i=O; i<N; i++){
	tratar v/i/
}
completar operación
```
### 12.1.1 Recorrido de matrices
==Si la formación es de tipo matriz, para hacer el recorrido se necesitan tantos for anidados como dimensiones tenga la formación.==
Ej (inicializar todos los elementos de una matriz z a cero):
```
const int N = ...;
typedef int T_Matriz[N][N];
T_Matriz z;
...
for (int i=O; i<N; i++){
	for (int j=0; j<N; j++){
		z[i][j]=0;
	}
}
```
### 12.1.2 Recorrido no lineal
En los ejemplos anteriores el índice usado para controlar el bucle nos señala directamente al elemento a procesar en cada iteración. En ciertos casos el  elemento a procesar debe elegirse realizando ciertos cálculos, y el contador de iteraciones sirve fundamentalmente para contabilizar el avance del recorrido detectar el final del bucle.

==Ejemplo: CUADRADO MÁGICO (lado impar)
Se puede construir rellenando las casillas números correlativos, empezando por el centro de la fila superior y avanzando en diagonal hacia arriba y a la derecha. Al salir del cuadro por un lado pasa a la casilla correspondiente del lado contrario. Si la siguiente casilla en avance diagonal ya está ocupada no se avanza, sino que se desciende a la casilla inmediatamente debajo para continuar el recorrido.==
![[Pasted image 20241213174330.png]]
```
const int N = ... ;
typedef int T_Matriz[N][N] ;
T_Matriz cuadro; 
int fil, col; 

fil = O; 
col = N/2; 

for (int k = 1; k <= N*N; k++) { 
	cuadro[fil][col] = k;
	fil = (fil+N-1) % N; 
	col = (col+1) % N; 
	if (cuadro[fil][col] ! == O) { 
		fil == (fil+2) % N;
		col == (col+N-1) % N; 
	}
}
```
## 12.2 Búsqueda secuencial

En las operaciones de búsqueda secuencial se examinan uno a uno los elementos de la colección para tratar de localizar los que cumplen una cierta condición, Si realmente queremos encontrar todos los que existan, entonces la búsqueda equivale a un recorrido como los mostrados en la sección anterior.
Si no necesitamos localizar todos los elementos que cumplen la condición sino sólo uno de ellos, si lo hay, entonces no necesitamos recorrer la colección en su totalidad. El recorrido se debe detener en cuanto se encuentre el elemento buscado, y por tanto sólo será un recorrido completo cuando no se encuentre el elemento buscado dentro de la colección. ==Este planteamiento del problema indica que no se puede utilizar directamente una sentencia *for* de C± para la operación de búsqueda.==
```
iniciar operación
while (quedan dementos sin tratar y no se ha encontrado ninguno aceptable) {
	elegir uno de ellos y ver si es aceptable 
} 
completar operación
```
## 12.3 Inserción
El problema que se plantea aquí es insertar un nuevo elemento en una colección de elementos ordenados, manteniendo el orden de la colección. Se supone que los elementos están almacenados en un vector, ocupando las posiciones desde el principio, y que queda algo de espacio libre al final del vector (si el vector estuviese lleno no se podrían insertar nuevos elementos).
![[Pasted image 20241213180951.png]]
```
typedef ... T_Elemento ... ;
void Insertar( T_Elemento v[], int N, T_Elemento elemento) {
PRE: V[0...n-1] está ordenado 
	int j=N ;
	INVARIANTE:Los elementos delante del hueco están ordenados entre sí, y los elementos detrás del hueco están ordenados entre sí y son mayores que el nuevo, y los elementos delante del hueco son menores o iguales que los de detrás del hueco, y la colección de valores delante y detrás del hueco coincide con el contenido inicial del vector
	while (j > O && elemento < v(j-l]) {
		v[j] = v[j-l]; 
		j --; 
	}	 
	v[ j ] = elemento;
POST : v´[0...n] está ordenado y contiene los valores v[0... N-1] más "elemento"
}
```
## 12.4 Ordenación por inserción directa
En este apartado se aborda una solución para la ordenación de datos almacenados en un vector. Por ejemplo, se trata de ordenar un vector v de diez elementos (índices de 0 a 9)
![[Pasted image 20241213182132.png]]
A continuación se muestra el código de una posible realización. La variable valor guarda el elemento extraído de la posición i. La ordenación total vector se consigue mediante el recorrido de todos sus elementos, desde el segundo, para buscarles su hueco e insertarlos en él.
```
typedef ... T_Elemento ...;
void Ordenar ( T_Elemento v[], intN){
	T_Elemento valor;
	int j;
	for (int i =1 ; i<N; i++){
		valor = v[i];
		j = i;
		while (j> 0 && valor < v[j-1]){
		v[j] = v[j-1];
		j--;
		}
		v[j] = valor	
	}
}
```
## 12.5 Búsqueda por dicotomía
Cuando los datos están ordenados la búsqueda resulta mucho mas rápida. Si comparamos el elemento a buscar con el que está justo en la mitad de los datos ordenados, podemos decidir si es ése el elemento que buscamos o debemos continuar buscando, pero sólo en la mitad derecha o sólo en la mitad izquierda.
El mismo proceso se puede repetir con la mitad elegida, comparando con el elemento que está en el centro de dicha mitad. En cada comparación, la búsqueda se reduce a comprobar si el dato buscado está entre la mitad de los anteriores. La búsqueda finaliza cuando el elemento se encuentra, o bien cuando la zona pendiente de examinar queda reducida a un sólo elemento (o ninguno) después de sucesivas divisiones en mitades. Esta búsqueda se denomina búsqueda por dicotomía.
```
typedef .... T_Elemento...;

int Indice(T_Elemento buscado, const T_Elementov[], int N){
	int izq, dc, mitad, pos;
	izq = 0; dc = N-1; pos = -1;
while (pos<0 && izq <= dch){
	mitad = (izq +dch) / 2;
	if (v[mitad] == buscado){
	pos = mitad;
	} else if (v[mitad] < buscado) {
	  dcg = mitad -1;
	} else {
	  izq = mitad +1;
	}
}
return pos;
}
```

## 12.6 Simplificación de las condiciones de contorno
A continuación veremos algunas técnicas particulares para evitar la necesidad de detectar de manera explícita si se ha llegado a un elemento del contorno (extremo) y/o realizar con él un tratamiento especial.
### 12.6.1 Técnica del centinela
Por ejemplo, en el procedimiento general de búsqueda es necesario comprobar en cada iteración una condición doble: si no se ha alcanzado todavía el final del vector, y si se encuentra el elemento buscado.

La doble condición del bucle de iteración complica el código y supone tiempo adicional en la ejecución de cada iteración. Si garantizamos que dato buscado está dentro de la zona de búsqueda, antes o después se terminara encontrándolo y ya no será necesario comprobar explícitamente si se alcanza el final del vector. 

La manera de asegurar esto es incluir el dato buscado en el vector antes comenzar la busqueda. El vector se amplía con un elemento más situado al final (si se hace la búsqueda hada adelante) o situado al principio (si la búsqueda se hace hacia atrás). En ese elemento adicional se copia el dato a buscar antes de iniciar la búsqueda para que actúe como *centinela* (C) y asegure que la búsqueda nunca acaba de forma infructuosa.

*iniciar operación (colocar el centinela)
**while** (no se ha encontrado un elemento aceptable) {
	elegir otro elemento a ver si es aceptable
}
completar operación ( si se ha encontrado el centinela , indicar fallo en la búsqueda)*

```
typedef ... T_Elemento...;

int Indice (T_Elemento buscado, const T_Elemento v[], int N) {
	int pos = 0;
	
	v[N] = buscado; /* centinela */
	while (v[pos] !=buscado) {
		pos++;
	}
	if (pos >= N) { /* lo que se encuentra es el centinela */
	pos = -1;
	}
	return pos;
}
```

###  12.6.2 Matrices orladas
Estas matrices se dimensionan con dos filas y dos columnas más de las necesarias. La matriz original la forman las filas 1 a M y las columnas 1 a N. Las filas y columnas extra garantizan que todos los elementos de la matriz original tienen elementos vecinos en todas las direcciones. Antes de operar con la matriz inicializan las filas y columnas extra con un valor de contorno (C) que permita simplificar la operación de modo que el tratamiento de los elementos del borde de la matriz original sea idéntico al de los demás.

Para ilustrar el uso de una matriz orlada supongamos que tenemos una imagen en blanco y negro (escala de grises) de Ancho x Alto pixeles almacenada en una matriz definida de la siguiente forma:
```
const int Ancho = 40; /* Anchura de la imagen */
const int Alto = 20; /* Altura de la imagen */ 
const int Borde = -1; /* Indicador de borde de la imagen */ 
const int Blanco = O; /* Nivel bajo de grises = blanco */
const int Negro = 5; /* Nivel alto de grises = negro*/
typedef int Imagen_t[Alto+2](Ancho+2]; 
Imagen_t imagen;
```
Supongamos ahora que queremos recortar la imagen, esto eliminar aquellos puntos externos de la imagen que están en blanco, pero dejando los puntos blancos que son interiores y están rodeados de puntos negros. El tratamiento de cada punto exige examinar al mismo tiempo puntos contiguos. El programa se simplifica si se garantiza que todo punto útil de la imagen tiene puntos contiguos en todas las direcciones, es decir, hay situaciones excepcionales en los bordes.

Para ello se aprovecha el contorno de la matriz, es decir, la orla, inicializándola con el valor que indicará los elementos del borde.
```
for(int i=0; i<=Alto; i++){
	imagen [i][0] = Borde;
	imagen [i][0] = Borde;
}
for (int i=0; i<= Ancho+1; i++){
	imagen [0][i] = Borde;
	imagen [Alto+1][i] = Borde;
}
```
Suponiendo que imagen está ya contrastada anteriormente y que su contorno está inicializado al valor de Borde, el recorte se realizaría mediante sucesivos recorridos de toda la matriz en los que los puntos blancos que tienen algún punto Borde alrededor deben pasar también a puntos Borde. El proceso de recorte se termina cuando en un recorrido completo de toda la imagen no hay ningún punto que cambie.
```
bool fin;

do{
	fin = true;
	for(int i=1; i<=Alto; i++) {
		for (int j=1; j<=Ancho; j++){
			if((imagen[i][j] == Blanco) &&
			   ((imagen[i-1][j] == Borde) ||
			    (imagen[i][j-1] == Borde) ||
			    (imagen[i][j+1] == Borde) ||
			    (imagen[i+1][j] == Borde))) {
			   imagen[i][j] = Borde;
			   fin = false; 
			}
		}
	}
} while (! fin);
```
Esta forma de operar se denomina de fuerza bruta, y puede ser poco eficiente, pero es muy sencilla de programar.

# Tema 13 Punteros y variables dinámicas
## 13.1 Estructuras de datos no acotadas

En los temas anteriores se han descrito las estructuras de datos que pueden definirse en C±. Todas ellas tienen una característica en común: la capacidad total se determina explícitamente al definirlas.==Una estructura podrá usarse de manera que el número de componentes que contengan información significativa sea variable, pero nunca mayor que el tamaño total de la estructura.==
La fijación del tamaño máximo representa una solución de compromiso entre la capacidad del programa y su eficiencia. Si el tamaño es relativamente pequeño el programa tendrá una capacidad de tratamiento limitada. Si el tamaño se fija a un valor muy grande, el programa será poco eficiente en el uso de la memoria.
Debe resultar evidente que sería útil disponer de estructuras de datos que no tuvieran un tamaño fijado de antemano, sino que pudieran ir creciendo o reduciendo su tamaño en función de los datos particulares que se estén manejando en carla ejecución del programa. ==Estas estructuras de datos se denominan *estructuras dinámicas*.==

## 13.2 La estructura secuencia
La estructura secuencia puede definirse como un esquema de datos del tipo iterativo, pero con un número variable de componentes. La estructura secuencia resulta parecida a una formación con número variable de elementos.
==Hay varias formas posibles de plantear las operaciones sobre secuencias. Para describir las distintas alternativas distinguiremos entre operaciones de *construcción* y de *acceso*. En las primeras podremos añadir o eliminar componentes de la secuencia, en las segundas podremos obtener o modificar el valor de los componentes que existen en un moment.o dado.==
Las operaciones de construcción pueden incluir: 
Añadir o retirar componentes al principio / final / mitad de la secuencia. 
Las operaciones de acceso pueden ser: 
Acceso secuencial:  Las componentes deben tratarse una por una, en el orden en que aparecen en la secuencia. 
Acceso directo: Se puede acceder a cualquier componente directamente indicando su posición, como en una formación o vector.
En muchos casos, y en particular cuando el acceso es secuencial, el tratamiento de una secuencia se realiza empleando un **cursor**. ==El cursor es una variable que señala a un elemento de la secuencia.== El acceso, inserción o eliminación de componentes de la secuencia se hace actuando sobre el elemento señalado por el cursor (↑). 
Para actuar sobre el cursor se suelen plantee las siguient.es operaciones:
- Iniciar: Pone el cursor señalando al primer elemento. 
- Avanzar: El cursor pasa a señalar al siguiente elemento. 
- Fin: Es una función que indica si el cursor ha llegado al final de la secuencia.
## 13.3 Variables dinámicas
Una variable dinámica no se declara como tal, sino que se crea en el momento necesario, y se destruye cuando ya no se necesita. Las variables dinámicas no tienen nombre, sino que se designan mediante otras variables llamadas punteros o referencias.

### 13.3.1 Punteros
En C± los punteros o referencias son variables simples cuyo contenido es precisamente una referencia a otra variable. El valor de un puntero no es representable como número o texto.
![[Pasted image 20241217201055.png]]
El tipo de un puntero especifica en realidad el tipo de variable a la que puede apuntar. La declaración es: 
```
typedef Tipo_de_variable* Tipo_puntero
```
Una vez declarado el tipo, se pueden declarar variables puntero de dicho tipo. Una variable puntero se puede usar para designar la variable apuntada mediante la notación:
```
*puntero
```
Ej:
```
typedef int* Tp_Entero;
Tp_Entero pe;

*pe = 33;
printf( "%d" , *pe ) ;
```
Estas sentencias asignan el valor 33 a la variable dinámica señalada por el puntero pe, y luego la imprimen. Para que estas sentencias funcionen correctamente es necesario que exista realmente la variable apuntada. Si el puntero no señala realmente a una variable dinámica, el resultado de usar * puntero será imprevisible.

Para poder detectar si un puntero señala realmente o no a otra variable, existe en C+- el valor especial NULL.
Este valor es compatible con cualquier tipo de puntero, e indica que el puntero no señala a ninguna parte. Por lo tanto debería ser asignado a cualquier puntero que sepamos que no señala a ninguna variable. Normalmente se usará para inicializar las variables de tipo puntero al comienzo del programa. La inicialización no es automática.
Ej:
```
if (pe != NULL) {
	*pe = 33;
	printf( "%d" , *pe ) ;
}
```
Esta sentencia garantizaría que sólo se usa la variable apuntada cuando realmente existe.

### 13.3.2 Uso de variables dinámicas
Las variables normales de un programa tienen esa zona de memoria reservada de antemano al empezar a ejecutarse el programa o subprograma en que se declaran, y por tanto pueden ser usadas en cualquier momento. Conviene recordar que las variables declaradas en un subprograma sólo existen mientras se ejecutan las sentencias de ese subprograma.

==Las variables dinámicas no tienen ese espacio de memoria reservado de antemano, sino que se crean a partir de punteros en el momento en que se indique. Además, una vez creadas siguen existiendo incluso después de que termine la ejecución del subprograma donde se crean.==
La forma más sencilla de crear una variable dinámica es mediante el operador **new**:
```
typedef Tipo_de_variable* Tipo_puntero;
Tipo_puntero puntero;

puntero = new Tipo_de_variable;
```
El operador new crea una variable dinámica del tipo indicado y devuelve una referencia que puede asignarse a un puntero de tipo compatible. Como en cualquier otra asignación, el valor anterior del puntero se pierde. Tal como se ha dicho antes, la variable dinámica no tiene nombre, y sólo se puede hacer referencia a ella a través del puntero.

La variable dinámica se crea a base de reservarle el espacio necesario en una zona general de memoria gestionada dinámicamente. En principio no se puede asumir que la variable recién creada tenga un valor concreto, igual que las variables normales que se declaran sin un valor inicial explícito.
La sentencia **delete** permite destruir variable dinámica a la que señala un puntero:
```
delete puntero;
```
==Esta sentencia destruye la variable apuntada pero no garantiza que el puntero quede con un valor determinado. En particular no garantiza que tome el valor NULL.==

==Una variable dinámica puede estar referenciada por más de un puntero. Esto ocurre cuando se copia un puntero en otro.==
```
typedef int* Tp:_Entero;
Tp_Entero p1, p2;

p1 = new int;
p2 = p1;
```
Tanto la variable p1 como p2 quedan señalando a la misma variable dinámica.
Un problema delicado al manejar variables dinámicas es que pueden quedar perdidas, sin posibilidad de hacer referencia a ellas.
```
typedef int* Tp_Entero;
Tp_Enero p1, p2;

p1 = new int;
p2 = new int;
p2 = p1;
```

![[Pasted image 20241217202703.png]]
==En este caso la variable creada mediante p2 = new int; queda perdida, sin posibilidad de ser usada, ya que las variables dinámicas no tienen nombre y el único puntero que la señalaba ha cambiado su valor, perdiendo el anterior. Además el espacio ocupado por la variable dinámica sigue reservarlo, lo es totalmente inútil y representa una pérdida de la capacidad de memoria disponible (en inglés se denomina memory leak).==

## 13.4 Realización de secuencias mediante punteros
C± no dispone de esquemas de datos de tamaño variable. Dichos esquemas pueden ser realizados indirectamente por el programador mediante el uso de punteros. 

Para definir una secuencia ilimitada tendremos que recurrir al empleo de variables dinámicas y punteros. Una manera de hacerlo es usar punteros para enlazar cada elemento de la secuencia con el siguiente.
![[Pasted image 20241217203324.png]]
==Cada elemento de la secuencia se materializa como un registro con dos campos: el primero contiene el valor de una componente, y el segundo es un puntero que señala al siguiente. El último elemento tendrá el puntero al siguiente con valor NULL. La secuencia completa es accesible a través de un puntero que señala al comienzo de la misma.==
```
typedef struct Tipo_nodo {
	Tipo_componente primero;
	Tipo_nodo * resto;
};

typedef Tipo_nodo * Tipo_secuencia;
```
Esta pareja de definiciones es válida en C±, aunque tiene una característica excepcional: se usa el identificador Tipo_ nodo antes de haber sido definido completamente. Esto sólo es posible hacerlo en declaraciones de punteros como la anterior. Gracias a esa posibilidad se puede realizar mediante punteros el equivalente a una definición recursiva de un esquema de datos. (Una definición recursiva es aquella en que se hace referencia a sí misma)

Una vez definidos los tipos de la secuencia y sm; componentes se podrán dedarar variables de dichos tipos y operar con ellos:
```
Tipo_componente valor;
Tipo_secuencia secuencia, siguiente;

if(secuencia != NULL) {
	(*secuancia).primero = valor;
	siguiente = (*secuencia).resto;
}
```
La combinación del operador de desreferenciación de puntero ( * ) y la selección de campo de registro ( . ) es incómoda de escribir, porque requiere paréntesis y difícil de leer. Por esta razón C± permite combinar ambos en un operador único con una grafía más amigable (->).
```
if (secuencia != NULL) {
	secuencia->primero = valor;
	siguiente 0 secuencia->resto;
}
```

### 13.4.1 Operaciones con secuencias enlazadas
Supondremos la existencia de un cursor que va señalando a las componentes una tras otra. El cursor será simplemente un puntero.

#### **DEFINICIÓN** 
La definición de la secuencia será:
```
typdef struct TipoNodo {
	int valor;
	TipoNodo * siguiente;
};
typedef TipoNodo * TipoSecuencia;
TipoSecuencia secuencia;
```
1.
- **`struct TipoNodo`**: Es una estructura que representa un **nodo** de una lista enlazada.
    
- **`int valor`**: Campo que almacena el valor del nodo.
    
- **`TipoNodo * siguiente`**: Es un puntero que apunta al siguiente nodo en la lista.  
    Esta autoreferencia permite **enlazar** varios nodos para formar una lista.
    
- Luego se define un alias para `struct TipoNodo` con el nombre **`TipoNodo`**.
2.
Con `typedef`, se crea un **alias** llamado `TipoSecuencia` para `TipoNodo *`.

- **`TipoNodo *`**: Es un puntero a un nodo de tipo `TipoNodo`.
- **`TipoSecuencia`**: Ahora es un nombre más simple para referirse a **punteros a nodos de tipo `TipoNodo`**.
3.
- **`TipoSecuencia`** es un alias para `TipoNodo *`.
- Por lo tanto, `secuencia` es una variable que almacena un **puntero al primer nodo** de la lista enlazada.

#### **RECORRIDO** 
El recorrido de toda la secuencia. se consigue mediante un bucle de acceso a elementos y avance del cursor. Puesto que la secuencia tiene un número indefinido de elementos, no se usará un bucle con contador. En este caso usaremos un esquema while.
```
typedef TipoNodo * TipoPuntNodo;
TipoPuntNodo cursor;

cursor = secuencia;
while (curosr != NULL) {
	printf( "%5d" , cursor->valor );
	cursor = cursor->siguiente;
}
```
1.
- **`TipoNodo`**: Es un tipo de dato que define un nodo de una lista enlazada.
- **`TipoNodo *`**: Es un **puntero a un TipoNodo**.
- **`TipoPuntNodo`**: Es un **alias** para `TipoNodo *`.
 A partir de aquí, escribir `TipoPuntNodo` es lo mismo que escribir `TipoNodo *`.

- **`TipoPuntNodo`** es un alias para `TipoNodo *`.
- Por lo tanto, `cursor` es una variable que representa **un puntero a un nodo** (`TipoNodo`)
2.
**`cursor = secuencia;`**

- El puntero `cursor` se inicializa con el valor de `secuencia`.
- Es decir, `cursor` ahora apunta al **primer nodo** de la lista enlazada.
3.
**`while (cursor != NULL)`**

- El bucle se ejecuta mientras `cursor` no sea `NULL`.
- Cuando `cursor` es `NULL`, significa que hemos llegado al **final de la lista**.
4.
**`printf("%5d", cursor->valor);`**

- `cursor->valor` accede al campo `valor` del nodo al que `cursor` está apuntando.
- Se imprime el valor con un ancho de 5 espacios.
5.
**`cursor = cursor->siguiente;`**

- El puntero `cursor` se actualiza para apuntar al **siguiente nodo** de la lista.
- `cursor->siguiente` contiene la dirección del siguiente nodo.

#### **BÚSQUEDA** 
La búsqueda en una secuencia enlazada ha de hacerse de manera secuencial. La búsqueda es parecida al recorrido, pero la condición de terminación cambiará. De hecho habrá una doble condición de terminación: que se localice el elemento buscado, y/o que se agote la secuencia. A continuación se presenta la búsqueda de la posición en que ha de insertarse un lluevo número en la secuencia ordenada. La posición será la que ocupe el primer valor igualo mayor que el que se quiere insertar.
```
int numero;
TipoPuntNodo cursor ¡, anterior;

cursor = secuencua;
anterior = NULL;
while (cursor != NULL && cursor->valor < numero) {
	anterior = cursor;
	cursor = cursor->siguiente;
}
```
1.
- **`int numero`**: Es una variable que  contiene un **número entero**.
    
    - Este número servirá como **criterio** para recorrer la lista enlazada y buscar una posición específica.
- **`TipoPuntNodo`**: Como vimos anteriormente, es un alias para `TipoNodo *` (puntero a un `TipoNodo`).
    
- **`cursor`**: Es un puntero que recorrerá la lista nodo por nodo.
    
- **`anterior`**: Es un puntero que apunta al **nodo anterior** al que está apuntando `cursor`.
2.
- **`cursor = secuencia`**:
    
    - Se inicializa el puntero `cursor` con el valor de `secuencia`.
    - Es decir, `cursor` **apunta al primer nodo** de la lista enlazada.
- **`anterior = NULL`**:
    
    - El puntero `anterior` se inicializa en `NULL`.
    - Al inicio, no hay un nodo "anterior" porque estamos en el primer nodo.

3.
 **Condición del bucle:**

- **`cursor != NULL`**:
    
    - El bucle se ejecuta mientras `cursor` no haya alcanzado el final de la lista (es decir, no sea `NULL`).
- **`cursor->valor < numero`**:
    
    - Además, el bucle se ejecuta mientras el campo `valor` del nodo actual (al que apunta `cursor`) sea **menor** que `numero`.
    - Esto implica que el bucle recorre la lista buscando la **primera posición** donde `cursor->valor` es **mayor o igual** que `numero`.
**Cuerpo del bucle:**

1. **`anterior = cursor`**:
    
    - El puntero `anterior` se actualiza para apuntar al **nodo actual** (antes de que `cursor` avance).
2. **`cursor = cursor->siguiente`**:
    
    - El puntero `cursor` avanza al **siguiente nodo** en la lista.
**Flujo del bucle:**

El bucle recorre la lista enlazada **nodo por nodo** hasta que:

1. **`cursor == NULL`**:
    
    - Esto significa que hemos llegado al final de la lista.
    - En este caso, no se encontró un nodo cuyo `valor` sea mayor o igual a `numero`.
2. **`cursor->valor >= numero`**:
    
    - El valor del nodo actual (`cursor->valor`) es mayor o igual a `numero`.
    - El bucle se detiene aquí porque hemos encontrado la **posible posición** donde `numero` podría insertarse o realizarse alguna operación.

Durante este recorrido, el puntero `anterior` siempre **se queda atrás**, apuntando al nodo previo al que está apuntando `cursor`. Al salir del bucle **cursor** queda señalando al punto en que deberá insertarse el nuevo elemento, y **anterior** señala al elemento que lo precede.

#### **INSERCIÓN**
La inserción de un nuevo elemento se consigue creando una variable dinámica para contenerlo, y modificando los punteros para enlazar dicha variable dentro de la secuencia. El caso más sencillo es el de insertar un nuevo elemento detrás de uno dado.
```
int numero;
TipoPuntNodo cursor, anterior, nuevo;

nuevo = new TipoNodo;                                /* 1º paso */
nuevo->valor = numero;
nuevo->siguiente = anterior = anterior->siguiente;   /* 2º paso */
anterior->siguiente = nuevo;                         /* 3º paso */

```
![[Pasted image 20241217212118.png]]
1.
- **`int numero`**: Es un número entero que queremos asignar al nuevo nodo.
- **`TipoPuntNodo`**: Es un alias para `TipoNodo *` (puntero a un nodo de tipo `TipoNodo`).
- **`cursor`**, **`anterior`** y **`nuevo`** son punteros que trabajarán con la lista enlazada.
2.
- Se crea un **nuevo nodo** dinámicamente utilizando `new`.
- La variable `nuevo` ahora apunta a un bloque de memoria que representa un nodo de tipo `TipoNodo`.
3.
- El campo `valor` del nuevo nodo (`nuevo->valor`) se asigna con el valor de la variable `numero`.
- Hasta ahora, `nuevo` tiene un valor asignado pero todavía no está enlazado a la lista.
4.
`nuevo->siguiente = anterior = anterior->siguiente;`
Esta línea hace **dos cosas simultáneamente**:

1. **`anterior = anterior->siguiente`**:
    
    - El puntero `anterior` se actualiza para apuntar al siguiente nodo después del que ya estaba apuntando.
    - Es decir, `anterior` ahora apunta a `anterior->siguiente`.
2. **`nuevo->siguiente = anterior`**:
    
    - El campo `siguiente` del nuevo nodo (`nuevo->siguiente`) se asigna con el valor de `anterior`.
    - Esto significa que `nuevo` **apunta al siguiente nodo** que originalmente era apuntado por `anterior`.
- El nuevo nodo `nuevo` ahora enlaza al nodo que seguía después de `anterior`.
5.
`anterior->siguiente = nuevo;`
- Aquí, el campo `siguiente` del nodo `anterior` se actualiza para que apunte al nodo **nuevo**.
- De esta manera, el nodo **anterior** ahora enlaza al nodo **nuevo**.
- Esto finaliza la inserción del nuevo nodo en la lista.

#### **BORRADO**
Para borrar un elemento hay que quitar el nodo que lo contiene, enlazando directamente el anterior con el siguiente. Es la operación inversa de la inserción. Si el nodo que contenía el elemento ya no es necesario hay que destruirlo explícitamente.
```
TipoPuntNodo cursor, anterior;

anterior->siguiente = cursor->siguiente;
delete cursor;
cursor = NULL;
```
![[Pasted image 20241217214431.png]]
1.
- **`TipoPuntNodo`** es un alias para `TipoNodo *`, es decir, un puntero a un nodo de tipo `TipoNodo`.
- `cursor` apunta al **nodo que queremos eliminar**.
- `anterior` apunta al **nodo previo** al que queremos eliminar.
2.
**`anterior->siguiente = cursor->siguiente;`**

- **Objetivo**: Ajustar los punteros para "saltar" el nodo al que apunta `cursor`.
    
- **`cursor->siguiente`**: Es el puntero al **siguiente nodo** después del nodo que queremos eliminar.
    
- **`anterior->siguiente = cursor->siguiente`**:
    
    - El puntero `siguiente` del nodo **anterior** ahora apunta al nodo que **sigue después del nodo actual** (`cursor`).
    - En otras palabras, se "desconecta" el nodo que apunta `cursor` de la lista enlazada.
3.
 **`delete cursor;`**

- Esta línea **libera la memoria** ocupada por el nodo al que apunta `cursor`.
    
- Como el nodo se ha desconectado en el paso anterior, ya no forma parte de la lista enlazada.
4.
 **`cursor = NULL;`**

- Aquí, el puntero `cursor` se asigna a `NULL`.
## 13.5 Punteros y paso de argumentos
### 13.5.1 Paso de punteros como argumentos
Como cualquier otro dato, un puntero puede pasarse como argumento a un subprograma.
```
vid ImprimirLista( TipoSecuencia lista ) {
	TipoPunt-nodo cursor = lista;
	while (cursor != NULL) {
		printf( "%5d" , cursor->valor );
		cursor = cursor->siguiente;
	}
	print( "\n" );
}

TipoSecuencia secuencia;

ImprimirLista( secuencia );
```
Por defecto, los datos de tipo puntero se pasan como argumentos por valor. Es lo que ocurre en el ejemplo anterior. Si se desea usar un subprograma para modificar datos de tipo puntero, entonces habrá que pasar el puntero por referencia. 
```
void Buscar( TipoSecuencia lista, int numero,
			 TipoPuntNodo & cursor, TipoPuntNodo & anterior ) {
	cursor = lista;
	anterior = NULL;
	while (cursor != NULL && cursor->valor != numero) {
		anterior = cursor;
		cursor = cursor->siguiente;	
	}
}

TipoSecuencia secuencia;
TipoPuntNodo encontrado, previo;
int dato;

Buscar( secuencia, dato, encontrado, previo );
```

1. **`cursor = lista;`**
    
    - El puntero `cursor` comienza apuntando al **primer nodo** de la lista.
2. **`anterior = NULL;`**
    
    - Como `cursor` está en el primer nodo, **no existe un nodo anterior** al inicio, por lo que `anterior` se inicializa en `NULL`.
3. **Bucle `while`**:
    
    - El bucle continúa mientras:
        
        - `cursor` **no sea NULL** (es decir, mientras no se llegue al final de la lista).
        - `cursor->valor` **no sea igual** al valor buscado (`numero`).
    - En cada iteración:
        
        - **`anterior`** se actualiza al nodo actual (`cursor`).
        - **`cursor`** se mueve al siguiente nodo (`cursor = cursor->siguiente`).
4. **Al salir del bucle**:
    
    - Si **`cursor == NULL`**, significa que no se encontró ningún nodo con el valor `numero`.
    - Si **`cursor->valor == numero`**, `cursor` apunta al nodo que contiene el valor buscado, y `anterior` apunta al nodo previo.
En la llamada a **Buscar** la variable **secuencia** no podrá ser modificada, ya que el argumento lista se pasa por valor. Por el contrario, las variables de tipo puntero **encontrado** y **previo** serán modificadas por el subprograma para reflejar el resultado de la búsqueda.

Dentro de la función `Buscar`, las variables **`encontrado`** y **`previo`** **no se actualizan explícitamente dentro de la función**, pero en su lugar, los punteros **`cursor`** y **`anterior`** se modifican. Entonces, después de ejecutar la función `Buscar`, las variables `encontrado` y `previo` deben **contener** los valores de `cursor` y `anterior` respectivamente. Es decir:

- Si el valor **`numero`** es encontrado en la lista, **`encontrado`** apuntará al nodo que contiene `numero`, y **`previo`** apuntará al nodo anterior a `encontrado`.
- Si no se encuentra el valor, **`encontrado`** será `NULL`, y **`previo`** será el último nodo de la lista (ya que el puntero `cursor` será `NULL` al final del bucle).
### 13.5.2 Paso de argumentos mediante punteros
Desde un punto de vista conceptual el paso de un puntero como argumento puede ser considerado equivalente a pasar como argumento la variable apuntada.
Por ejemplo, si queremos pasar como argumento una variable dinámica podemos recurrir a un puntero como elemento intermedio para designarla.
La dificultad reside en el hecho de fine pasar un puntero por valor no evita que el subprograma pueda modificar la variable apuntada.

Al establecer la analogía entre el paso como argumento del puntero y el paso como argumento de la variable apuntada, la distinción entre paso por valor y por referencia se pierde. ==El paso por valor de un puntero equivale al paso por referencia de la variable apuntada. Los punteros se usan implícitamente para pasar argumentos por referencia.==

Por supuesto, hace falta entonces un operador especial para obtener el valor de un puntero a una variable (estática) y usarlo en la llamada al subprograma. En lenguaje e ese operador corresponde también al símbolo &, como se muestra a continuación:
```
int numero;

Duplicar( &numero );
```

A lo largo de todo este libro han ido apareciendo sentencias de lectura como la siguiente:

```
scanf( "%d" , &numero );
```

==Lo que se está haciendo en esta llamada es pasar como argumento un puntero que señala a la variable numero, a través del cual se puede modificar su valor.== Hay que hacer notar que el puntero en sí se está pasando por valor, y eso es equivalente a pasar el dato apuntado por referencia.

## 13.6 Punteros y vectores en en C y C++
En las siguientes secciones se explica la analogía que existe en C/C++ entre los punteros y las formaciones, mostrando algunas de las posibilidades y consecuencias de este hecho. La razón de estas explicaciones es aclarar algunas de las irregularidades que presenta el lenguaje C± en el manejo de las formaciones.
**En estas siguientes secciones se muestran operaciones que están expresamente prohibidas y que no se deben utilizar en los programas.**
### 13.6.1 Nombres de vectores como punteros
Cuando se ha declarado una variable de tipo vector el nombre de dicha variable equivale en gran medida a un puntero que apunta al comienzo del vector.
```
typedef int* Tp_Entero;
typedef int Tv_Entero[5];

void Incrementar( Tp_Entero val ) {  /* paso por referencia */
    *val = *val + 1;
}

void ImprimirVector( const int v[], int nV ) {
    for (int k = 0; k < nV; k++) {
        printf("%10d", v[k]);
    }
    printf("\n");
}

Tp_Entero p1;
Tv_Entero v1 = {10, 20, 30, 40, 50};
pI = vI;                                 /* vector como puntero */

Incrementar(p1);                        
ImprimirVector(p1, 5);                   /* puntero como vector */

Incrementar(v1);                         /* vector como puntero */
ImprimirVector(v1, 5);

Incrementar( &v1[0] );
ImprimirVector( &v1[0], 5 );             /* puntero como vector */
```

El nombre del vector v1 equivale al valor de un puntero que señala al comienzo es decir, al primer elemento v1 [0]. Por lo tanto puede ser asignado a una variable puntero del tipo equivalente. En sentido contrario, un puntero de ese tipo puede ser usado como argumento al invocar un subprograma que requiera un vector. Tras la asignación `p1 =  v1` en el ejemplo, cada una de las parejas de sentencias `Incrementar(); ImprimirVector();` realizan la misma acción: incrementar el valor del primer elemento y luego imprimir los 5 elementos del vector. 
La analogía alcanza incluso a poder utilizar el puntero como base para indexar un elemento del vector. Tras ejecutar `p1 =  v1` las expresiones siguientes son equivalentes: 

`p[3]` equivale a `v[3]`

y aún más, en la declaración de un puntero se puede crear e inicializar un vector al que apunte: 
```
typedef char * TipoPalabra;

TipoPalabra nombre = "Juan Antonio" ;
``` 

A pesar de lo anterior una variable puntero es claramente distinta de una variable vector. La asignación de un puntero a un vector 
`v1 =  p1`
no es aceptada por el compilador y provoca un mensaje de error.

### 13.6.2 Paso de vectores como punteros
Tal como se ha dicho antes en este tema, el paso por valor de un puntero equivale al paso por referencia de la variable apuntada. El cualificador **const** delante de un argumento formal de tipo puntero indica al compilador que ese valor de tipo puntero no debe ser usado para modificar la variable a la que apunta.

### 13.6.3 Matrices y vectores de punteros
Si un puntero es análogo a un vector, entonces un vector de punteros es análogo a una matriz, es decir, a un vector de vectores.
Para que la analogía sea total es necesario crear dinámicamente cada fila de la matriz a partir de cada elemento del vector de punteros.
La figura muestra la diferencia entre una matriz propiamente dicha, es decir, un vector de filas, y su estructura análoga en forma de vector de punteros a filas. En ambos casos un elemento se designa como`` matriz[fila][columna]`` pero la organización de los datos en memoria es claramente diferente.
![[Pasted image 20241217223701.png]]
De hecho la segunda alternativa no exige que todas las filas tengan el mismo tamaño.

# Tema 14 Tipos abstractos de datos
## 14.1 Concepto de tipo abstracto de datos (TAD)
Si analizamos con cuidado qué necesita un programa para poder usar datos de un tipo, encontraremos que hace falta:
- Hacer referencia al tipo en sí, mediante un nombre, para poder definir variables, subprogramas, etc. 
- Hacer referencia a algunos valores particulares, generalmente como constantes con nombre. 
- Invocar operaciones de manipulación de los valores de ese tipo, bien usando operadores en expresiones aritméticas o bien mediante subprogramas.
El conjunto de todos estos elementos constituye el tipo abstracto de datos (TAD):

**Un *tipo abstracto de datos* (TAD) es una agrupación de una *colección de valores* y una *colección de operaciones de manipulación*.**

Es importante comprender que estas colecciones son cerradas, es decir sólo se deben poder usar los valores abstractos y las operaciones declaradas para ese tipo. Además los detalles de cómo se representan los valores y cómo se implementan las operaciones pueden estar ocultos para quien utiliza el tipo abstracto.

La programación orientada a objetos se basa esencialmente en el uso de tipos abstractos de datos, con algunas modificaciones. La terminología cambia bastante: se habla de clases y objetos en lugar de tipos y datos, y de métodos en lugar de operaciones. Por otra parte se añade el concepto de herencia para facilitar la definición de nuevas clases a partir de otras ya existentes, reutilizando elementos ya definidos.

## 14.2 Realización de tipos abstractos en C±
El subconjunto denominado C± que se usa en este libro no contempla la definición de clases como tales, sino que se limita a presentar una forma algo más limitada de programar tipos abstractos de datos. Para ello se aprovecha el hecho de que los tipos registro ``(struct)`` se tratan en C++ como equivalentes a clases.
### 14.2.1 Definición de tipos abstractos como tipos registro (struct)
Hasta ahora se ha visto que los tipos registro permiten definir estructuras con varios campos de datos con nombre y tipo individual. Ahora añadiremos la posibilidad de incluir también otros elementos, en particular subprogramas, y distinguir entre elementos públicos y privados. De esta manera se pueden definir tipos abstractos de datos, ya que:
- Los campos de datos sirven para almacenar el contenido de información del dato abstracto. 
- Los subprogramas permiten definir operaciones sobre esos datos.
- La posibilidad de declarar ciertos elementos como privados permite dar detalles de implementación, y dejar visible sólo la interfaz del abstracto.
 ![[Pasted image 20241218001425.png]]
**INTERFAZ DEL TIPO ABSTRACTO PUNTO
```
 typedef struct TipoPunto {
    float x;  /* Coordenada X */
    float y;  /* Coordenada Y */
    
		/** Leer un punto con formato "(x, y)" */
	void Leer();
	
		/** Escribir un punto con formato "(x, y)" */
	void Escribir();
	
		/** Calcular la distancia de un punto a otro */
	float Distancia(TipoPunto p);
}
```
Los subprogramas correspondientes a las operaciones sobre el tipo abstracto se declaran simplemente por su cabecera, porque lo que se declara aquí es sólo la interfaz del tipo. La notación para referirse a las operaciones es la misma que para los campos de datos, usando el punto (.) como operador de cualificación. El esquema de esta notación y un ejemplo de uso son:
variable.campo                                  Referencia a campo de datos
variable.operación( argumentos )     Referencia a operación
```
TipoPunto p, q;

p.x = 3.3;
p.y = 4.4;

p.Leer();  
p.Escribir();  
printf("%f", p.Distancia(q) );
```
Como complemento de la declaración de la interfaz se necesita además definir la implementación de las operaciones. Esta implementación se hace fuera de la declaración del tipo registro, usando la notación ***Tipo* : : *Operación*** como nombre del subprograma.
**IMPLEMENTACIÓN DEL TIPO ABSTRACTO PUNTO**
```
#include <stdio.h>
#include <math.h>
/* Excepción en lectura */
typedef enum TipoPuntoError { PuntoNoLeido } ;

/* Leer un punto con formato "(x,y)" */
void TipoPunto::Leer() {
	int campos;
	
	campos = scanf( "( %f , %f )", &x, &y );
	if (campos < 2) { /* comprobar que se han leido dos valores */
		throw PuntoNoLeido;
	}
}
/* Escribir un punto con formato "(x, y)" */
void TipoPunto::Escribir() {
    printf( "( %f , %f )", x, y);
}
/* Calcular la distancia de un punto a otro */
float TipoPunto::Distancia( TipoPunto p ) {
    float deltaX, deltaY;

	deltaX : X - p.x ;
	deltaY : y - p.y;
	return sqrt( deltaX*deltaX + deltaY*deltaY );
}
```
Como se ve, en el código de implementación se puede hacer referencia a los campos de la estructura directamente por su nombre, sin necesidad de cualificación. Se sobreentiende que se refieren a la propia variable sobre la que invoca la operación.

Una vez definido el tipo abstracto se puede escribir código que lo use:
**PROGRAMA PRINCIPAL
```
#include <stdio.h>

/* Definición del tipo abstracto PUNTO */
/* ... aqui se incluye el código anterior ... */

/** Programa principal */
int main() {
	
	TipoPunto a, b;
	bool seguir = true ;
	
	while (seguir) {
		
		try {
			a.Leer() ;
			b .Leer() ;
			printf( "Segmento: " );
			a. Escribir();
			printf( " " );
			b . Escribir();
			printf( " Longitud : %f\n", a.Distancia( b ) );
		} catch (TipoPuntoError e) {
			seguir = false;
		}
	}
}

```
### 14.2.2 Ocultación
Para. que un tipo sea realmente abstracto haría falta que los detalles de implementación no fueran visibles. Los subprogramas, como mecanismo de abstracción, ya ocultan los detalles de la realización de las operaciones. Sin embargo queda la cuestión de cómo ocultar la manera de representar los valores del tipo abstracto.
Para permitir esta ocultación los tipos ``struct`` admiten la posibilidad de declarar ciertos elementos componentes como privados, usando la palabra clave ``private`` para delimitar una zona de declaraciones privadas dentro de la estructura.
```
typedef struct TipoFecha {
	/* Dar valor a un dato fecha */
	void Poner( int dia, int mes, int anno );
	
	/* Obtener el contenido de un dato fecha */
	int Dia();
	int Mes();
	int Anno();
	
private:
	int dia, mes, anno ;
} ;
```
## 14.3 Metodología basada en abstracciones
La técnica de programación estructurada, basada en refinamientos sucesivos puede ampliarse para contemplar la descomposición modular de un programa. La metodología de desarrollo será esencialmente la misma que se ha presentado en el tema 8, referente al desarrollo usando abstracciones en forma de subprogramas (*abstracciones funcionales*). La diferencia es que ahora disponemos también de un nuevo mecanismo de abstracción, que son los *tipos abstractos de datos*.
Igualmente son de aplicación las técnicas generales de desarrollo: descendente o ascendente. El desarrollo debería atender tanto a la organización de las operaciones como a la de los datos sobre las que operan, de manera que habrá que ir realizando simultáneamente las siguientes actividades: 
- Identificar las operaciones a realizar, y refinarlas. 
- Identificar las estructuras de información, y refinarlas.
### 14.3.1 Desarrollo por re finamiento basado en abstracciones
Sobre el *desarrollo descendente* con abstracciones funcionales: en cada etapa de refinamiento de una operación hay que optar por una de las alternativas siguientes: 
- Considerar la operación como *operación terminal*, y codificarla mediante sentencias del lenguaje de programación. 
- Considerar la operación como *operación compleja* y descomponerla en otras más sencillas. 
- Considerar la operación como *operación abstracta* y especificarla, escribiendo más adelante el subprograma que la realiza.
Para las estructuras de datos:
- Considerar el dato como un *dato elemental* y usar directamente un tipo predefinido del lenguaje para representarlo. 
- Considerar el dato como un *dato complejo*, y descomponerlo en otros más sencillos (como regist.ro, unión o formación). 
- Considerar el dato como un *dato abstracto*  y especificar su interfaz, dejando para más adelante los detalles de su implementación.

# Tema 15 Módulos
## 15.1 Concepto de módulo
==Módulo: Fragmento de programa desarrollado de forma independiente.==
El desarrollo independiente debe serlo en el máximo grado posible. Atendiendo a las técnicas de preparación de programas en lenguajes de programación simbólicos, diremos que un módulo debería ser compilado y probado por separado.
Si el módulo se va a compilar por separado, la persona que lo desarrolle podrá concentrarse en él, prescindiendo en parte de cómo se utiliza ese módulo desde el resto del programa. De la misma forma, quien escriba el resto del programa no se preocupará de los detalles de cómo está codificado el módulo, sino sólo de cómo hay que usarlo.
==Un módulo debe definir un elemento abstracto (o varios relacionados entre sí) y debe ser usado desde fuera con sólo saber qué hace el módulo, pero sin necesidad de conocer cómo lo hace.==
### 15.1.1 Especificación y realización
En un módulo podemos distinguir dos puntos de vista, correspondientes a su especificación y a su realización. ==La primera visión nos dice qué hace el módulo, y la segunda nos dice cómo lo hace.==
La especificación de un módulo que contenga la definición de una serie de elementos abstractos consistirá , fundamentalmente, en el conjunto de las especificaciones de cada uno de ellos, por separado, más una indicación de los posibles efectos de unos sobre otros cuando se usan de forma combinada.
La realización del módulo consistirá en la realización de cada uno de los elementos abstractos contenidos en dicho módulo. 
La especificación del módulo es todo lo que se necesita para poder usar los elementos definidos en él. ==Esta especificación constituye la *interfaz* ==(en inglés interface) entre el módulo (incluida su realización) y el programa que lo usa.

La independencia entre la realización de un módulo y el programa que lo usa se incrementa si la realización de un elemento abstracto no es visible desde donde se usa. Esta característica se denomina ocultación. Referida a los módulos, la ocultación consiste en que el programa que lisa un elemento de un módulo sólo tiene visible la información de la interfaz, pero no la de la realización.
### 15.1.2 Compilación separada
- Compilación separada: El programa está formado por varios ficheros fuente, cada uno de los cuales se compila por separado. 
- Compilación segura: Al compilar un fichero fuente el compilador comprueba que el uso de elementos de otros módulos es consistente con la interfaz. 
- Ocultación: Al compilar un fichero fuente el compilador no usa información de los detalles de realización de los elementos de otros módulos.
![[Pasted image 20241218184026.png]]
Entre las técnicas empleadas por lenguajes de programación en lo que respecta a compilación separada, tenemos situaciones tales como las siguientes:
1. El fichero del programa y del módulo se tratan de forma totalmente separada, sin visibilidad de la interfaz (lenguaje FORTRAN y las primeras versiones del lenguaje C). (NO HAY COMPILACIÓN SEGURA)
3. La. parte necesaria de la interfaz se copia o importa manualmente en el programa que la usa. La compilación de los ficheros del programa y del módulo se hace con total independencia (lenguaje e ANSI con prototipos, C++, y algunas versiones del lenguaje Pascal, con la directiva EXTERN o USE). (SEGURIDAD MAYOR, CON POSIBILIDAD DE ERRORES)
4. La interfaz del módulo y su realización se escriben en ficheros separados. El mismo fichero de interfaz se usa tanto al compilar la realización del módulo como al compilar el programa que lo usa (lenguajes Modula.-2 y Ada). (COMPLETEMANTE SEGURA)
5. La interfaz del módulo y su realización se combinan en un solo fichero fuente. Al compilar el programa que lo usa el compilador lee el fichero fuente del módulo, pero sólo utiliza los elemento de la interfaz (lenguajes Oberon y Java). (COMPLETEMANTE SEGURA)
El lenguaje C± está basado en C++ y comparte sus características en cuanto a compilación separada. y compilación segura.

### 15.1.3 Descomposición modular
La posibilidad de compilar módulos de forma separada permite repartir el trabajo de desarrollo de un programa, a base de realizar su descomposición modular.
La descomposición modular de UI1 programa puede reflejarse en un diagrama de estructura.
![[Pasted image 20241218184835.png]]
Las líneas que indican relaciones de uso pueden llevar punta de Hecha si es necesario indicar expresamente cuál es el sentido de la relación. Normalmente no es necesario, pues, como en este caso, un módulo que usa otro se dibuja encima de él, de manera que las líneas de uso se interpretan siempre de arriba a abajo, estableciendo al mismo tiempo una jerarquía entre módulos.

Para que la descomposición en módulos sea adecuada, conviene que los módulos resulten tan independientes linos de otros como sea posible. Esta independencia se analiza según dos criterios, denominados *acoplamiento* y *cohesión*.

- ==El ***acoplamiento*** entre módulos indica cuántos elementos distintos o características de uno o varios módulos han de ser tenidos en cuenta a la vez al usar un módulo desde otro. Este acoplamiento debe reducirse a un mínimo.==

- ==La ***cohesión*** indica el grado de relación que existe entre los distintos elementos de un mismo modulo, y debe ser lo mayor posible. Esto quiere decir que dos elementos íntimamente relacionados deberían ser definidos en el mismo módulo, y que un mismo módulo no debe incluir elementos sin relación entre sí.==

## 15.2 Módulos en C±
Un programa descompuesto en módulos se escribe como un conjunto de ficheros fuente relacionados entre sí, y que pueden compilarse por separado. Cada fichero fuente constituye así una unidad de compilación.

### 15.2.1 Proceso de compilación simple
Un fichero fuente es un fichero de texto que contiene el código de una unidad de compilación, es decir, es posible invocar el compilador dándole como entrada sólo ese fichero fuente.
==La compilación de un fichero fuente produce un fichero objeto que contiene la traducción del código C± a instrucciones de máquina. Por convenio, los ficheros fuente en C± tienen la extensión **.cpp** (la misma usada habitualmente en C++) y los ficheros objeto la extensión **.o** ==. Como regla de disciplina modular en C± se exige que el nombre del fichero objeto sea el mismo que el del fichero fuente.
![[Pasted image 20241218185756.png]]
En general un fichero objeto no se puede ejecutar directamente. Se necesita un paso adicional de montaje para obtener un programa o fichero ejecutable. ==En MS-Windows los ficheros ejecutables tienen la extensión **.exe** (en UNIX/ Linux no suelen tener extensión).== Si el programa ejecutable se ha generado a partir de un solo fichero fuente, debe tener también el mismo nombre.
==En C y C++ es frecuente que el montador y el compilador sean una misma herramienta, o al menos que se invoquen como si lo fueran. En casos sencillos como éste es posible realizar la compilación y montaje como una sola operación.==

### 15.2.2 Módulo principal
Cuando se descompone un programa en C± en vanos módulos uno de ellos ha de ser el programa principal o módulo principal. Este módulo será el que t:ontenga la función main(). La ejecución del programa completo equivale a la ejecución de dicha función principal. Por supuesto, la función principal puede invocar durante su ejecución operaciones definidas en otros módulos.
Sólo falta indicar que el fichero fuente de ese programa principal debe tener el nombre que se dará finalmente al programa ejecutable y tener la extensión . cpp, tal como se ha indicado anteriormente.

### 15.2.4 Uso de módulos
Para usar los elementos públicos definidos en un módulo hay que incluir la interfaz de ese módulo en el código donde se vaya a utilizar. Esto se consigue con la directiva #include.
La novedad ahora es que los nombres de los ficheros de la propia aplicación deben escribirse entre comillas (" ... ") y no entre ángulos « ... ». Con esto se indica al compilador que debe buscar dichos ficheros en donde reside el código fuente de la aplicación y no donde está instalada la herramienta de compilación.

### 15.2.3 Módulos no principales
Los módulos de la aplicación que no contienen una función main() no permiten generar un programa ejecutable por sí solos. Los elementos que contienen están destinados a ser usados por el programa principal u otros módulos.

==Al escribir el código de estos módulos no principales hay que distinguir claramente ent.re los *elementos públicos*, que deben ser visibles desde fuera del módulo para poder usarlos, y los *elementos privados*, que sólo necesitan ser visibles en el interior del módulo.==

La distinción entre los elementos públicos y los privados se hace repartiendo el código del módulo en dos ficheros fuente separados: un fichero de interfaz o fichero de cabecera, y un fichero de implementación.
Ej:
INTERFAZ:
```
/************************************************
* Interfaz de módulo: Tabulacion
* Este módulo contiene los elementos para
* imprimir series de números en varias columnas
*************************************************/
#pragma once

extern int numColumnas;      /* número de columnas */
extern int anchoCalumna;     /* ancho de cada una */

/*-- Iniciar la impresión --*/
void Iniciar( char titulo[] );

/* Imprime un número, tabulando */
void Imprimir( int numero );

/* Completa la impres~on de la última linea */
void Terminar() ;
```
IMPLEMENTACIÓN:
```
/************************************************
* Módulo: Tabulacion
* Este módulo contiene los elementos para
* imprimir series de números en varias columnas
*************************************************/
#include <stdio.h>
#include <string.h>
#include "Tabulacion.h"

int numColumnas = 4;       /* número de columnas */
int anchoColumna = 10;     /* ancho de cada una */

static int columna = 1;    /* columna actual */

/*-- Iniciar la impresión --*/
void Iniciar(char titulo[]) {
    Terminar();     /* la serie anterior, por si acaso */
    printf("%s\n", titulo);
    columna = 1;
}

/*-- Imprime un número, tabulando --*/
void Imprimir(int numero) {
    if (columna > numColumnas) {
        printf("\n");
        columna = 1;
    }
    printf("%*d", anchoColumna, numero);
    columna++;
}

/*-- Completar la impresión de la última línea --*/
void Terminar() {
    if (columna > 1) {
        printf("\n");
    }
    columna = 1;
}
```
Una buena disciplina dc Hombres exige que ambos ficheros tengan cl mismo nombre que el nombre lógico del módulo. El fichero de interfaz tendrá la extensión. h Y el de implementación la extensión . cpp. Por lo tanto los nombres de los ficheros fuente en este ejemplo deben ser: 
- Interfaz: Tabulacion.h 
- Implementación: Tabulacion.cpp
La directiva #include sirve para hacer referencia a un fichero fuente desde otro, y tiene como parámetro el nombre del fichero físico "Tabulacion.h", incluyendo la extensión.

### 15.2.5 Declaración y definición de elementos públicos
- En la *declaración* de un elemento hay que especificar lo necesario para que el compilador pueda compilar correctamente el código que usa dicho elemento.
- En la *definición* de un elemento hay que especificar lo necesario para que el compilador genere el código del propio elemento.
==En el caso de los elementos públicos de los módulos, la declaración debe ponerse en el fichero de interfaz, y la definición en el fichero de implementación.== En algunos casos la declaración contiene toda la información posible, y no hace falta una definición complementaria.

| **Declaración (fichero.h)**          | **Definición (fichero.cpp)**                               |
| ------------------------------------ | ---------------------------------------------------------- |
| ``typedef`` ... *TipoNuevo* ... ;    | (no aplicable)                                             |
| ``const`` *Tipo constante = valor* ; | (no aplicable)                                             |
| ``extern`` *Tipo variable* ;         | *Tipo variable = valor* ;                                  |
| *Tipo Subprograma( argumentos)* ;    | *Tipo Subprograma( argumentos)* {<br>... *código* ...<br>} |
- Los tipos y constantes se especifican totalmente en el fichero de interfaz. No hay declaración y definición separadas. 
- Las variables se definen de la manera habitual en el fichero de implementación, incluyendo la especificación de valor inicial en su caso. Con ello el compilador reserva espacio para dicha variable en el módulo que la define. En el fichero de interfaz se pone además una declaración que indica el tipo y nombre de la variable, sin indicar valor inicial, y precedida de la palabra clave ``extern`` Esta declaración permite al compilador generar código de las sentencias que usan dicha variable en otros módulos sin reservar espacio para ella, ya que formará parte efectiva del código del módulo que la define. La conexión entre las referencias a la variable y su ubicación real se resuelve durante la fase de montaje, posterior a la compilación.
- Los subprogramas se definen de la manera habitual en el fichero de implementación y permiten al compilador generar el código objeto del subprograma. En el fichero de interfaz se pone además una declaración en forma de prototipo o cabecera de subprograma sólo con el tipo, nombre y argumentos. Esta cabecera permite al compilador generar el código de las sentencias de llamada al subprograma. La conexión entre las llamadas al subprograma y su código real se resuelve durante la fase de montaje, posterior a la compilación.

### 15.2.6 Conflicto de nombres en el ámbito global
El ámbito más externo en la jerarquía de bloques del programa principal y de todos los módulos de una aplicación constituye un espacio de nombres global y único, en el que no debe haber nombres repetidos.
Una técnica sencilla para evitar en lo posible los conflictos de nombres públicos globales e; asignar a cada módulo un prefijo diferente que se habrá de usar en los nombres de todos sus elementos públicos.
Ej:
```
/************************************************
* Interfaz de módulo: Tabulacion (TAB)
*************************************************/
#pragma once

extern int TAB_numColumnas; /* número de columnas */
extern int TAB_anchoColumna; /* ancho de cada una */

/*-- Iniciar la impresión --*/
void TAB_iniciar(char titulo[]);

/* Imprime un número, tabulando */
void TAB_imprimir(int numero);

/* Completa la impresión de la última línea */
void TAB_terminar();
```
El ámbito global más externo incluye también los elementos privados, que no figuran en la interfaz de los módulos. ==Afortunadamente en este caso el lenguaje C± ofrece un mecanismo que evita los conflictos de nombres repetidos, ya que es posible especificar elementos en el ámbito más externo que sólo sean visibles en el fichero fuente donde se definen. Para ello basta poner la palabra clave ``static`` delante de la definición del elemento.==
```
/************************************************
* Módulo: Tabulacion
*************************************************/
static int columna = 1; /* columna actual */
```
Con esta definición es posible reutilizar el nombre columna para elementos globales de otros módulos, sin que haya conflicto entre ellos.

### 15.2.7 Unidades de compilación en C±
Los ficheros fuente de los tipos mencionados pueden ser considerados unidades de compilación, en el sentido de que es posible invocar la compilación de cada uno de ellos por separado. Por lo tanto tendremos como unidades de compilación:
- El módulo principal: *programa*. cpp
- El fichero de interfaz de un módulo: *modulo* .h 
- El fichero de implementación de un módulo: *modulo*. cpp
En realidad a la hora de preparar una aplicación sólo se mandan compilar realmente los ficheros con extensión . cpp, que son los que generan código objeto. Los fichero de interfaz con extensión . h no se mandan compilar por sí mismos ya que en principio no generan código objeto.
Lo que ocurre es que los ficheros de interfaz son parte efectiva de la compilación de los ficheros de implementación. El significado de la directiva #include es equivalente a copiar en ese punto el contenido del fichero fuente indicado. Esta copia o inclusión se hace sobre la marcha durante la compilación, en una fase inicial de la misma denominada *preproceso*.
![[Pasted image 20241218203330.png]]
Finalmente se enumeran aquí las reglas de sintaxis correspondientes a la estructura general de cada. una de las unidades de compilación mencionadas:
![[Pasted image 20241218203415.png]]
![[Pasted image 20241218203432.png]]

### 15.2.8 Compilación de programas modulares. Proyectos
El proceso de compilación y montaje de un programa cuyo código fuente está repartido entre varios módulos requiere una cadena de operaciones:
![[Pasted image 20241218203607.png]]
==La generación del programa ejecutable final exige:== 
1. ==Compilar los módulos uno a uno, generando el correspondiente fichero objeto ( .a) a partir del fuente (. cpp). Cada compilación individual usa también los ficheros de interfaz (. h) mencionados en las directivas #include del módulo. ==
2. ==Montar el programa ejecutable combinando todos los ficheros objeto de los módulos.==
Los entornos de programación modernos simplifican la tarea de recompilar los módulos después de editar al6runo o varios de ellos. Para eso disponen de un mecanismo de proyectos, consistente en disponer de un fichero con información de los ficheros fuente que forman parte de la aplicación. A partir de ahí el entorno automatiza la generación o actualización de los ficheros objeto y el ejecutable final, que se invoca en conjunto como una operación única denominada habitualmente "construir".

La información mínima que debe contener el fichero de descripción de un proyecto será: 
- Nombre del proyecto (= nombre del programa ejecutable) 
- Lista de ficheros fuente de implementación . cpp (incluyendo el programa principal)
Opcionalmente se puede disponer también de otros datos útiles, tales como
- Lista de ficheros de interfaz . h 
- Forma de invocar al compilador, con opciones particulares para ese proyecto 
- etc.
## 15.3 Desarrollo modular basado en abstracciones
### 15.3.1 Implementación de abstracciones como módulos
En la mayoría de los casos los tipos abstractos de datos identificados en una aplicación son buenos candidatos para ser codificados como módulos independientes, y lo mismo ocurre con las abstracciones funcionales de cierta complejidad. Por lo tanto el desarrollo basado en abstracciones lleva implícita una posible descomposición natural del programa en módulos. Esto ocurre de forma obligada en algunos lenguajes con una estricta orientación a objetos, por ejemplo Java.

### 15.3.2 Dependencias entre ficheros. Directivas
Las relaciones de uso entre módulos se corresponden, en principio, con las directivas #include usadas en un fichero fuente para hacer visibles los elementos de otro, y que pueden aparecer en el fichero .cpp y/o en el . h. La recomendación es: 
- Un fichero xxx.h debe incluir otros yyy.h que use directamente . 
- Un fichero xxx.cpp debe incluir su propio xxx.h y otros yyy.h que use directamente. Pero no hace falta hacerlo explícitamente si ya los incluye su xxx.h.
En el ejemplo anterior hay dependencias indirectas. Por ejemplo, el módulo principal DibujarC usa elementos de Tortuga directamente y también indirectamente a través de CurvaC. Si no se toman precauciones el preprocesador incluirá el código de Tortuga.h dos veces, y se tendrán errores por duplicación de definiciones. La directiva #pragma once sirve precisamente para evitar esa duplicación.

NOTA: La directiva #pragma once no es estándar en C++. Eu su lugar la receta habitual es similar a la siguiente (para un fichero xxx. h): 
```
#ifndef xxx_h_ 
#define xxx_h_ I 
... código de la interfaz ...
#endif
```
Este esquema de código es algo más seguro pero bastante más complejo, y por ello se ha decidido no incluirlo en el subconjunto C+-.

### 15.3.3 Datos encapsulados
En este tema y el anterior se ha visto cómo ==al definir un tipo abstracto de datos hay que declarar luego variables de ese tipo para trabajar con ellas. En algunos casos concretos resulta que sólo es necesario una única variable del tipo abstracto. Si es así, existe la posibilidad de encapsular dicha variable en un módulo y evitar la declaración explícita del tipo==. La facilidad de ocultación que provee la programación modular es suficiente para conseguir la abstracción del dato, de forma que sólo sean visibles las operaciones que lo manipulan pero no los detalles de su implementación.

| Tipo abstracto                                                                                                                                                                 | Dato encapsulado                                                                                                                                                                      |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Interfaz                                                                                                                                                                       | Interfaz                                                                                                                                                                              |
| typedef struct Tipo {<br>  void Operacion1()<br>  void Operacion2();<br>private:<br>UnTipo valorInterno;<br>void Operacion3();<br>};<br>                                       | void Operacion1();<br>void Operacion2();                                                                                                                                              |
| Implementación                                                                                                                                                                 | Implementación                                                                                                                                                                        |
| void Tipo : : Operacion3() {<br>...<br>}<br><br>void Tipo : : Operacion1() {<br>... valorInterno ...<br>}<br><br>void Tipo : : Operacion2() {<br>... valorInterno ...<br>}<br> | static UnTipo valorInterno;<br>static void Operacion3() {<br>...<br>}<br><br>void Operacion1() {<br>... valorInterno ...<br>}<br><br>void Operacion2() {<br>... valorInterno ...<br>} |
| Uso                                                                                                                                                                            | Uso                                                                                                                                                                                   |
| Tipo dato;<br><br>dato.Operacion1();                                                                                                                                           | Operacon1();                                                                                                                                                                          |
### 15.3.4 Reutilización de módulos
Los expertos en desarrollo de software suelen considerar que la descomposición modular basada en abstracciones es una buena metodología para desarrollar módulos con bastantes posibilidades de ser reutilizados en el futuro.

Los módulos que definen abstracciones relacionadas entre sí pueden agruparse en una biblioteca o librería que se pone a disposición de quienes desarrollan aplicaciones en un campo determinado.

U n caso extremo de reutilización se tiene en los módulos "estándar" que acompañan a muchos lenguajes de programación . Estos módulos contienen elementos de uso general, que result.an útiles en un porcentaje muy elevado de programas de todo tipo.