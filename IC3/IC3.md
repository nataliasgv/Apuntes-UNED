# 1. Fundamentos del diseño del hardware digital
## 1.1. INTRODUCCIÓN
El lenguaje para la descripción del hardware o HDL (siglas que provienen del inglés: Hardware Description Language) es un lenguaje, legible tanto por las máquinas como por los seres humanos, ideado para describir tanto el comportamiento como la estructura del hardware.
El HDL que el Departamento de Defensa de EE.UU. creó en los años 80 se llamó VHDL. Las siglas VHDL provienen de VHSIC Hardware Description Language. VHSIC es un acrónimo de Very High Speed Integrated Circuit, que fue el nombre del proyecto llevado a cabo por el Departamento de Defensa de EE.UU.
En 1987, el Institute of Electrical and Electronics Engineers (IEEE) adoptó VHDL como el estándar número 1076.
## 1.2. LENGUAJES PARA LA DESCRIPCIÓN DE HARDWARE
El empleo de HDL presenta ventajas respecto al empleo de descripciones basadas en esquemáticos.
1. Puesto que una descripción HDL es simplemente un fichero de texto, es mucho más portable que un diseño esquemático, que debe ser visualizado y editado empleando la herramienta gráfica específica del entorno de CAD ( ComputerAided Design- Diseño asistido por ordenador) con el que se ha creado.
2. Una descripción esquemática únicamente describe el diseño de manera estructural, mostrando los módulos y la conexión entre ellos. Por el contrario, la descripción del circuito usando un HDL puede realizarse bien mostrando la estructura, o bien describiendo el comportamiento. Es decir, ==los HDL permiten describir el comportamiento que se desea que tenga el circuito, sin hacer ninguna referencia a su estructura.== Las herramientas de síntesis permiten generar automáticamente la estructura del circuito lógico a partir de la descripción de su comportamiento. 
3. ==El mismo HDL que se ha usado para la descripción del circuito, puede emplearse para describir los vectores de test y los resultados esperados del test.== Los vectores de test son los valores de las señales que se aplicarán a los pirres de entrada del circuito con la finalidad de comprobar si el funcionamiento del circuito es correcto. Así pues, pueden realizarse los programas de test (vectores de test e instantes en los cuales son aplicados) del circuito a medida que se diseña el propio circuito, pudiéndose con ello ir realizando diferentes pruebas a medida que se avanza en el diseño.

### 1.2.1. Usos de un programa HDL

- *Documentación formal*. Un programa HDL puede ser usado como una especificación formal de un sistema digital. Se trata de un tipo de documentación explícita y precisa acerca del sistema, que es intercambiable entre diferentes diseñadores y usuarios.
- *Entrada a un simulador*. La simulación por ordenador del circuito permite estudiar y comprobar su operación, sin necesidad de tener que construir físicamente el circuito. Durante la ejecución de la simulación, el simulador interpreta el código HDL y genera las respuestas del circuito.
- *Entrada a una herramienta de síntesis*. El flujo de diseño del hardware digital se basa en un proceso de refinamiento, que convierte gradualmente una descripción de alto nivel del sistema a una descripción estructural de bajo nivel. Algunos de estos pasos de refinamiento pueden ser realizados por las herramientas software de síntesis.

### 1.2.2. HDL más ampliamente usados

- Verilog: se hizo de dominio público y se promovió como un estándar de IEEE en el año 1995, denominado IEEE 1364.
- VHDL
- SystemC: consiste en un conjunto de librerías en C++. Se convirtió en el estándar 1666 de IEEE en el año 2005.

## 1.3. CICLO DE DISEÑO DE LOS CIRCUITOS DIGITALES
![](img/Pasted%20image%2020250219142041.png)
- Establecer la especificación del diseño. Qué se espera que haga el circuito y qué restricciones deben satisfacerse (frecuencia de reloj, retardos, tamaño, etc.).
- Crear un diseño de alto nivel del circuito. Para lo cual puede emplear un lenguaje para la descripción de hardware (HDL).
- Desarrollar un conjunto de programas de test y, si es posible, usar estos programas para testear el diseño de alto nivel, usando para ello una herramienta de simulación (verificación funcional). En función de los resultados de la simulación de los tests, puede ser preciso modificar el diseño de alto nivel.
- Traducir el diseño al nivel de puertas lógicas o de transistores. Síntesis: generación automática del diseño del circuito a partir de la descripción de su comportamiento. El resultado de la síntesis se denomina Netlist: descripción de todas las conexiones y componentes que deben componer el circuito.
- El diseño a nivel de puertas o transistores debe ser vuelto a testear mediante simulación (verificación de tiempos), usando, si es posible, el mismo conjunto de tests que se realizaron sobre el diseño de alto nivel.
- Una vez el diseño ha superado estos tests, puede implementarse en la plataforma hardware seleccionada: PLD (Programmable Logic Device), FPGA (FieldProgrammable Cate Array), ASIC (Application-Specific Integrated Circuit), etc. Se emplean herramientas software para fabricar (en el caso de los ASIC) o programar (en el caso de los FPG A) el circuito integrado a partir de la netlist.
- Una vez implementado, el circuito integrado puede ser testeado con ayuda de un generador de patrones (para generar los vectores de test), y un analizador lógico u osciloscopio (para medir las salidas).

## 1.4. TECNOLOGÍAS DE CIRCUITOS INTEGRADOS

La implementación hardware del circuito digital puede realizarse empleando circuitos integrados de diferentes tecnologías. Una característica fundamental que diferencia cada tecnología de circuitos integrados es la manera de adaptar el circuito a una determinada aplicación.
Así pues, las tecnologías non-ASIC permiten particularizar el circuito en campo, mientras que los circuitos de las tecnologías ASIC deben ser particularizados a su aplicación en la fábrica de circuitos integrados.

### 1.4.1. Clasificación de las tecnologías
#### Full-custom ASIC
Todos los aspectos del circuito integrado son diseñados específicamente para una determinada aplicación, especificándose las características de cada uno de los dispositivos electrónicos (transistores, diodos, capacitares, etc.) que componen el circuito. En consecuencia, el circuito resultante estará completamente optimizado y tendrá el mejor comportamiento posible.

La aplicación fundamental de la tecnología full custom es el diseño de pequeños circuitos digitales básicos, denominados "*celdas estándar*", que posteriormente serán usados de manera modular para componer circuitos de mayor tamaño.

#### Standard-cell ASIC
El circuito integrado es construido conectando entre sí celdas estándar predefinidas, que ya han sido previamente diseñadas y testeadas. Esta tecnología permite trabajar al nivel de puertas lógicas, en lugar de al nivel de transistores, lo cual simplifica bastante el proceso de diseño. 
Los fabricantes de dispositivos normalmente proporcionan librerías de celdas estándar que implementan los bloques constitutivos básicos, tales como puertas lógicas, componentes combinacionales simples, elementos básicos de memoria, memorias RAM, etc.

### Gate array ASIC
El circuito es construido a partir de un array predefinido de "*celdas base*". Al contrario que en la tecnología *standard cell*, el circuito integrado de la tecnología *gate array* consiste en la repetición unidimensional o bidimensional de un único circuito sencillo, llamado celda base, que es similar a una puerta lógica. los fabricantes de*gate array* ASICs proporcionan librerías de componentes prediseñados, denominados "*macro celdas*", que son arrays de celdas base conectadas entre sí para formar bloques lógicos con funcionalidades básicas. Las macro celdas facilitan el diseño, que puede realizarse conectando entre sí macro celdas.

Los primeros niveles de fabricación de los circuitos integrados de la tecnología *gate array*, que están dedicados a la fabricación de los transistores de las celdas base, son comunes a todas las aplicaciones y por ello pueden ser fabricados independientemente de la aplicación.

### Dispositivos complejos programables en campo
La tecnología non-ASIC más versátil es el circuito integrado complejo programable en campo, que consiste en un array de celdas lógicas genéricas y en la interconexión genérica entre ellas. Aunque las celdas lógicas y su interconexión están prefabricadas, el circuito integrado dispone de fusibles que permiten "programar" el circuito integrado, adaptándolo a su aplicación. Este proceso de programación del circuito integrado, consistente en fundir algunos de sus fusibles. ==Esta tecnología se denomina "programable en campo" (*field programmable*), en oposición a las tecnologías ASIC, en las cuales el circuito integrado debe ser particularizado en la fábrica en la que es construido.==
De acuerdo a la estructura circuital de sus celdas lógicas, los dispositivos complejos programables en campo pueden clasificarse en dos tipos: CPLD ( Complex Programmable Logic Device) y FPGA (Field Programmable Gate Array).

### Dispositivos sencillos programables en campo
Dispositivos programables con una estructura interna más sencilla que CPLDs y FPGAs. Este tipo de circuitos integrados se han llamado PLDs ( Programmable Logic Devices). Están compuestos por dos arrays, uno de puertas AND y otro de puertas OR. Pueden programarse las interconexiones en uno de estos arrays o en ambos, con el fin de adaptar el circuito a su aplicación. 
- En los dispositivos PROM (Programmable Read Only Memory) puede programarse el array OR. 
- En los dispositivos PAL (Programmable Array Logic) puede programarse el array AND. 
- En los dispositivos PLA (Programmable Logic Array) pueden programarse ambos arrays.

### Circuitos estándar de pequeña y media integración
Antes de la popularización de los dispositivos programables en campo, la única alternativa que existía a los circuitos integrados ASIC era utilizar circuitos integrados prefabricados SSI/MSI (Small-/Medium-Scaled Integrated circuits). Los circuitos se diseñaban seleccionando cuáles de esos circuitos integrados debían usarse y fabricando una placa impresa específica para la aplicación, con las pistas para la conexión entre los pines de los circuitos integrados, y en la cual se soldaban los circuitos integrados. En este tipo de implementación, la mayor parte de los recursos (potencia consumida, área y coste de fabricación) es consumida por el encapsulado y el routing, y no por el silicio, que es donde se realiza la computación.

## 1.4.2. Comparación entre tecnologías
En esta sección se compararán las tres tecnologías FPGA, gate array y standard cell, empleando para ello cuatro criterios: área, velocidad, potencia consumida y coste.
### Área (tamaño)
Los circuitos integrados pequeños requieren menos recursos, precisan de programas de test más sencillos y tienen un mejor rendimiento en fabricación, entendiendo dicho rendimiento como el porcentaje de chips buenos que se obtienen por oblea.

| Standart cell                                                                                                                                                                                                               | Gate array                                                                                                                                                                                                                                                                                                                                                                                                                                                     | FPGA                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| las celdas estándar y sus interconexiones son particularizadas para la aplicación en concreto, con lo cual no hay desperdicio de área de silicio. ==El chip resultante está completamente optimizado y el área es mínima.== | El circuito debe ser construido a partir de celdas base cuya posición en el circuito está predefinida. Dado que la funcionalidad y posición de las celdas base no son específicas a la aplicación, ==el aprovechamiento del silicio no es óptimo==. Normalmente un circuito integrado de la tecnología gate array ==necesita mayor área== (aproximadamente entre un 20% y un 100% más) ==que ese mismo circuito desarrollado en la tecnología standard cell.== | Una parte considerable del área del circuito integrado está dedicada a posibilitar que el circuito pueda ser programado en campo. Más aun, la funcionalidad de las celdas lógicas y las interconexiones están preestablecidas, siendo frecuente que cierto porcentaje de la capacidad no sea utilizado en la aplicación en concreto a la que se destina el FPGA. ==Puede estimarse que un circuito implementado en la tecnología FPGA tiene entre 2 y 5 veces mayor área que ese mismo circuito implementado en una tecnología ASIC.== |
### Velocidad
Tiempo necesario para que dicho circuito realice su función. Este tiempo se estima considerando el mayor retardo en la propagación que puede producirse en cada etapa del circuito.
Para poder realizar las operaciones más rápidamente, es necesario emplear circuitos con arquitecturas más complejas, que ocupan mayor área. Si se usan arquitecturas idénticas, normalmente un circuito integrado con mayor área es más lento.

==Dado que en la tecnología standard cell las interconexiones y el área pueden ser optimizadas, esta tecnología es la que permite menores retardos de propagación y, consiguientemente, mayor velocidad. En el otro extremo, la tecnología FPGA es la que tiene retardos de propagación mayores. Al igual que sucedía con el área, la diferencia que existe respecto a la velocidad entre las tecnologías ASIC standard cell y gate array es considerablemente menor que entre estas tecnologías ASIC y la tecnología FPGA.==

### Potencia consumida
Energía que consume el circuito integrado por unidad de tiempo. El consumo de potencia está relacionado con el número de transistores que contenga el circuito integrado.
==Respecto a las tres tecnologías que estamos comparando, la tecnología standard cell consume la menor cantidad de potencia, mientras que la tecnología FPGA es la que consume mayor cantidad de potencia de las tres.==

==La tecnología *standard cell* es la mejor elección desde el punto de vista técnico, ya que un chip construido en esa tecnología es tan pequeño, rápido y consume tan poca potencia como sea posible.==

### Coste
Pueden considerarse las tres contribuciones al coste siguientes: el *coste de producción*, el *coste de desarrollo* y el *coste del tiempo de llegada al mercado*.
#### Coste de producción ($Cprod$ )
Los euros que cuesta producir una unidad del circuito integrado. Incluye dos conceptos: el coste de ingeniería ($Cing$) y el coste de fabricación ($Cfab$).

$$
Cprod = Cfab + Cing/Unidades Producidas
$$
- El coste de ingeniería ($Cing$) se produce una única vez durante el proceso de producción del circuito integrado, con independencia del número de unidades que vayan a fabricarse. Se incluye el desarrollo de las máscaras de fotolitografía, el desarrollo de los tests, y la fabricación y test de los prototipos. La repercusión de este coste en cada unidad del circuito depende del número de unidades producidas, siendo la repercusión menor cuanto mayor sea el número de unidades fabricadas.
- El coste de fabricación ($Cfab$) es la suma del coste que conlleva fabricar el dispositivo, encapsularlo y testearlo. El coste de fabricación de un circuito integrado ASIC es menor que el coste de un circuito desarrollado en la tecnología FPGA. Igualmente, el coste de fabricación de un circuito standard cell es menor que el de un circuito gate array.
A medida que el número de unidades fabricadas aumenta, en primer lugar *gate array*, y a continuación *standard cell*, se hacen rentables.
El coste de producción de la tecnología FPGA es constante, debido a que su coste de ingeniería es nulo. ($Cprod = Cfab$)

#### Coste de desarrollo
El proceso de transformar una idea en un circuito integrado conlleva unos costes, entre los cuales se incluyen los ordenadores y el software, y las horas de ingeniería. Aunque el procedimiento de síntesis es similar para todas las tecnologías, ==el desarrollo de ASICs es más complejo y requiere mayor esfuerzo, con lo cual el coste de ingeniería de un circuito integrado ASIC es mucho mayor que el de ese mismo circuito implementado en la tecnología FPGA==. Por este mismo motivo, ==el coste de desarrollo de un circuito *standard cell* es considerablemente mayor que el coste de desarrollo de ese mismo circuito en la tecnología* gate array.*==

##### Coste del tiempo de llegada al mercado
Pérdida de los beneficios económicos que se obtendrían si el circuito se encontrara ya vendiéndose en el mercado.
La tecnología standard cell es la que tiene un tiempo mayor de validación, de desarrollo de los tests y de puesta en producción, variando este tiempo entre unos meses y un año. El tiempo de la tecnología gate array puede variar entre unas cuantas semanas y unos meses. En el caso de la tecnología FPGA, la particularización del circuito a la aplicación se realiza programando un circuito prefabricado, lo cual puede hacerse en minutos.

## 1.5. PROPIEDADES DE LOS CIRCUITOS DIGITALES
### 1.5.1. Retardo de los dispositivos
==Un dispositivo lógico real tiene la propiedad de que un glitch en un puerto de entrada, con una duración inferior al retardo de propagación del dispositivo, no tiene efecto sobre la salida del dispositivo. Se denomina glitch a un cambio temporal (un pico de subida o bajada) e inesperado en el voltaje.==

Este tipo de comportamiento del retardo se denomina *retardo inercial* y es el modelo del retardo usado por defecto para todos los dispositivos en VHDL.
	El *retardo inercial* es adecuado para modelar los retardos a través de dispositivos tales como transistores y puertas lógicas. Un cambio en la entrada de un dispositivo se ha de mantener estable durante cierto tiempo para que este cambio se propague a su salida. Las puertas lógicas actúan así como filtros paso baja. El retardo inercial es debido a la capacidad del dispositivo, la carga que conduce, sus características intrínsecas, número y tipo de los elementos conectados al dispositivo, etc.

Otro tipo alternativo de modelo del retardo, en el cual todos los glitches a la entrada se manifiestan en la salida, se denomina *retardo de transporte* o *retardo puro*. 
	El *retardo de transporte* es adecuado para modelar retardos a través de dispositivos con poca inercia, tales como las líneas de metal construidas en el chip para conectar los dispositivos. Los retardos puros pueden considerarse como desplazamientos en el tiempo de la señal, ya que la señal en sí misma no se modifica. Al describir el retardo de los circuitos, VHDL permite diferenciar entre ambos tipos de retardo

Consideremos en primer lugar un buffer cuya señal de entrada es x y cuya señal de salida es y1. El buffer tiene un retardo inercial de 100 ns. Su comportamiento puede describirse en VHDL de la forma siguiente:
`y1 <= x after 100 ns;`
![](img/Pasted%20image%2020250302184436.png)
donde el símbolo <= representa la asignación del valor de la señal de la derecha ( x) a la señal de la izquierda (y1), una vez transcurrido el retardo indicado tras la palabra reservada **after**. Supongamos que la señal digital x varía de la forma indicada en la tabla siguiente:

| Tiempo (ns) | 0   | 100 | 200 | 300 |
| ----------- | --- | --- | --- | --- |
| x           | ´0´ | ´1´ | ´0´ | ´1´ |
La señal y1 evoluciona según se muestra en la Figura 1.3. Durante los primeros 100 ns, el valor de la señal de salida y1 es indefinido, puesto que no ha sido inicializado: vale 'U' (que proviene del inglés "Uninitialized"). Obsérvese que el buffer no responde ante cambios en la señal de entrada cuya duración sea menor que el retardo inercial. En concreto, el buffer no responde al cambio en la señal x que se produce en el instante 200 ns.

Consideremos ahora una línea de metal que introduce un retardo de transporte en la señal de 100 ns. Llamando x a la señal de entrada e y2 a la señal de salida, el comportamiento de la línea de metal puede ser descrito en VHDL de la manera indicada a continuación, donde la palabra reservada transport indica que el retardo es de transporte:
`y2 <= transport x after 100 ns;`

Si la señal x varía de la forma indicada en la tabla anterior, la evolución de la señal y2 es la mostrada en la Figura 1.3. Observe que la señal y2 es la señal x desplazada 100 ns. 

En resumen, las señales y1 e y2 sólo se diferencian en que la señal y1 no cambia su valor en el instante 300 ns, como consecuencia del cambio de valor en x en el instante 200 ns. Esto sucede porque el cambio en la señal x se mantiene durante un tiempo inferior al valor del retardo inercial (100 ns).
	Cuando se realizan los pasos "Diseño de alto nivel", "Programas de test" y "Simulación: Verificación funcional" en el diseño del hardware digital, se sabe que todos los bloques circuitales del diseño van a tener retardos. Sin embargo, en este punto del ciclo de diseño se desconoce el valor de dichos retardos. Hasta que no se realice la *síntesis*, y por tanto quede especificada la implementación hardware del circuito, no podrá estimarse el retardo de cada bloque circuital. Es práctica común no especificar el valor estimado de los retardos en el diseño de alto nivel de los circuitos. En su lugar, suele asignarse a cada uno de los bloques circuitales un retardo por defecto, denominado *retardo δ*.

### 1.5.2. Ejecución concurrente
==*Los módulos lógicos se ejecutan concurrentemente.*== Cuando cambia el valor de una señal de entrada a varios módulos, todos estos módulos deben ser ejecutados concurrentemente. Así pues, los HDL deben ser capaces de describir de manera precisa este comportamiento concurrente y el simulador debe ser capaz de simularlo. La metodología aplicada para ello por el simulador es la *simulación de eventos discretos*.
### 1.5.3. Diseños marginales
Los retardos de los dispositivos dependen de la condiciones de fabricación del chip. Por este motivo, *no es buena idea diseñar un circuito cuyo funcionamiento dependa de que los retardos tomen un determinado valor o que su magnitud sea mínima*.

### 1.5.4. Fortaleza de las señales
En un circuito digital típico, la transferencia de un valor lógico desde un pin de salida de un módulo, a varios pines de entrada de otros módulos, precisa de la transferencia de carga eléctrica hacia los pines de entrada (en el caso de '1' lógico) o hacia el pin de salida (en el caso de 'O' lógico). El pin de salida debe tener la capacidad de hacer de "fuente" y de "sumidero" de toda la corriente necesaria. Desde el punto de vista práctico, esto implica que la salida de un módulo puede ser conectada como máximo a un determinado número de entradas de otros módulos. En aquellos casos en que la señal deba conectarse a un número de módulos superior a este número máximo, entonces debe emplearse un árbol de buffers.

![](img/Pasted%20image%2020250302200306.png)
Árbol de buffers para llevar una señal a 16 módulos.

==El uso del árbol de buffers tiene un beneficio añadido: igualar los retardos de las señales de entrada a todos los módulos,== ya que el árbol de buffers está diseñado de modo que la longitud de las líneas de todas sus ramas sea la misma. Este tipo de árbol de buffers se emplea para llevar la señal de reloj a los flip-flops en los circuitos secuenciales síncronos, en los cuales es importante que la señal de reloj llegue a todos los flip-flops aproximadamente en el mismo instante.

## 1.6. TEST DE LOS CIRCUITOS
- Verificar el correcto funcionamiento del circuito ya completamente diseñado
- Ayuda esencial para el diseñador durante la fase de diseño del circuito
- En manufactura, para determinar qué chips han resultado defectuosos o tienen limitadas prestaciones
	 El test realizado en manufactura tiene un impacto directo sobre el rendimiento (porcentaje de chips fabricados que no son defectuosos), el cual tiene un impacto directo sobre los beneficios de la compañía fabricante de los chips.
==El test consiste en fijar valores en todas las entradas del circuito y observar qué valores se obtienen en sus salidas. A cada asignación de valores a todas las entradas del circuito se le llama un *vector* de test. El *programa* de test consiste en un conjunto de vectores de test, que se aplican sobre el dispositivo en una determinada secuencia.==
### 1.6.1. Test en manufactura
Detectar problemas en el proceso de fabricación. Las causas de mal funcionamiento de los chips más comunes son:
- **Abiertos**. Conexiones entre los dispositivos que se encuentran abiertas debido a algún problema, por ejemplo, debido a la rotura de la línea de metal que establece la conexión. 
- **Cortos**. Conexiones que se han establecido entre diferentes dispositivos, cuando no deberían haberse producido. 
- **Acopios**. Valores lógicos en una parte del circuito que inadvertidamente cambian el valor lógico en otra parte del circuito.
Modelar estos diferentes tipos de defectos en el circuito es extremadamente difícil. Por ello, se han desarrollado diferentes modelos simplificados de fallos:
- Uno de estos modelos de fallo es considerar que el defecto de fabricación hace que una de las conexiones internas del circuito permanezca siempre a 1, o que permanezca siempre a 0.
	En un circuito típico, este tipo de fallos da lugar a un número muy elevado de patrones de fallo. Un patrón de fallo es una determinada selección de conexiones que se encuentran permanentemente a 1 y de conexiones que se encuentran permanentemente a 0.
	Incluso tomando en consideración que existen patrones de fallo que dan lugar a un comportamiento equivalente (defectuoso) del circuito, el número de patrones de fallo esencialmente distintos es extremadamente grande.
- Por ello, se ha desarrollado un modelo simplificado a partir del anterior. Consiste en suponer que en el circuito hay una única conexión que se encuentra permanentemente a 1, o permanentemente a O. Aunque este modelo de fallos pudiera considerarse · muy restrictivo, ha demostrado ser eficaz.
Una vez se adopta un determinado modelo de fallos, el siguiente paso es crear un conjunto de vectores de test que permita detectar ese tipo de fallos. ==Para que se produzca la detección del fallo, es preciso que la salida del circuito, en caso de estarse produciendo el fallo, sea diferente de la salida de un circuito que funcione correctamente. En este caso, se dice que el fallo se encuentra *cubierto* por el vector de test. Por supuesto, habrá otros tipos de fallos que darán lugar, para ese vector de test, a las mismas salidas que un circuito que funcione correctamente. Se dice entonces que el vector de test *no cubre* esos otros fallos.==

Según se van usando más y más vectores de test, el porcentaje de fallos potenciales (para un determinado modelo de fallo) que son cubiertos se aproxima al 100%. ==Dado un conjunto de vectores de test, la *cobertura de fallos* de ese conjunto de vectores de test (dado un modelo específico de fallos) corresponde con el porcentaje de fallos cubiertos.==

El test de los circuitos secuenciales es más complicado, ya que las salidas del circuito dependen no sólo de las entradas, sino también de su estado. Por tanto, en este tipo de circuitos es preciso poder fijar los valores de todos los fiip-fiops a voluntad. Esto puede hacerse de las dos maneras siguientes:
1. Mediante una secuencia de inicialización (secuencia de valores de las entradas del circuito), se lleva el circuito al estado deseado. A continuación, se aplica el vector de test para probar el circuito en ese estado. Mediante este procedimiento, un único test consiste en una secuencia de inicialización, seguida de otro vector de test.
2. El segundo método consiste en usar en el diseño *scan fiip-fiops*, que son flipflops cuyo valor puede ser cargado desde las entradas al circuito (mientras se realiza el test) , o bien pueden ser usados del mismo modo que un flip-flop sin modificar (durante el modo normal de funcionamiento del circuito). Los scan flip-flops pueden construirse insertando multiplexores en la entrada D de los fli p-flops.
==En el test en manufactura, la calidad de un conjunto de vectores de test ( denominado *programa de test*) se mide por medio de la cobertura de fallos del programa de test (supuesto un determinado modelo de fallo) y del tiempo necesario para aplicar todos los vectores de test al circuito, que es directamente proporcional al número de vectores de test.==

Cuanto mayor sea la cobertura de fallos, menor será el número de chips defectuosos que superarán con éxito el proceso de inspección. Cuanto menor sea el número de vectores de test, menor será el tiempo necesario para ejecutar el programa de test, con lo cual podrán testearse mayor número de chips por unidad de tiempo.

### 1.6.2. Test funcional
El test funcional se emplea en todas las etapas del proceso de diseño del circuito. ==Su objetivo es verificar que el circuito realiza todas las operaciones como debiera.==
En los diseños grandes, que normalmente se diseñan de manera jerárquica, todos los subcircuitos de bajo nivel deben ser comprobados funcionalmente, usando programas de test específicos para cada uno, antes de ser incluidos en los subcircuitos de más alto nivel. 
Aunque todos los subcircuitos sean comprobados por separado, el subcircuito obtenido de la composición de todos ellos debe también ser comprobado, usándose para ello su propio programa de test.
A continuación, una vez se implementa el circuito usando alguna plataforma hardware (ASIC, FPGA, etc.), debe volver a ser testeado de nuevo. Si es posible, debe emplearse para testear el prototipo hardware el mismo conjunto de tests que se ha usado en la fase de simulación.

### 1.6.3. Programas de test funcional
El programa de test es algo que depende del circuito. Sin embargo, en general se sigue el criterio de probar todos los posibles vectores de entrada, siempre que esto sea posible.
Si el número de posibles vectores de entrada es muy grande:
1. Puede emplearse el conocimiento sobre el funcionamiento de circuito para descartar aquellos vectores de entrada que no tienen ninguna función en el circuito, o que nunca ocurrirán en la práctica.
2. El circuito puede dividirse en varios subcircuitos, que son testeados exhaustivamente (usando todas las combinaciones de los vectores de entrada para cada sub circuito). A continuación, el circuito completo puede testaerse usando un conjunto no exhaustivo de vectores de entrada, simplemente para comprobar que los subcircuitos han sido integrados adecuadamente.
3. Se escoge un conjunto representativo de vectores de entrada, con el fin de ejercitar el circuito bajo condiciones normales de funcionamiento y bajo condiciones extremas.
Al testear un circuito, es deseable poder comparar de manera automática las salidas del circuito con las correspondientes salidas que se obtendrían si el circuito funcionara correctamente.
4. Una forma es almacenar en un fichero las salidas de un circuito que funcione correctamente, y compararlas con las salidas obtenidas. 
5. Otro procedimiento consiste en calcular la salida esperada del circuito usando un método diferente al empleado en el test, y comparar los resultados. Cuando no es posible aplicar un método de cálculo alternativo al del test, puede comprobarse si los resultados obtenidos del test son "razonables".
### 1.6.4. Banco de pruebas
Muchas herramientas de simulación incluyen menús que permiten asignar valores a las entradas del circuito. Una alternativa mucho más ventajosa consiste en codificar el programa de test usando un HDL. Es decir, implementar el programa de test en otro módulo de código HDL, que es denominado *banco de pruebas*.
El *banco de pruebas* contendrá el circuito que está siendo probado (denominado abreviadamente UUT, del inglés "*Unit Under Test*') como un subcircuito. Todas las entradas al UUT serán generadas dentro del banco de pruebas, y todas las salidas del circuito serán comprobadas dentro del banco de pruebas.
El banco de pruebas debe incluir:
- Un subcircuito generador de los vectores de test. 
- El circuito que está siendo probado (UUT). 
- Un subcircuito de comprobación de los resultados obtenidos del test.
## 1.7. REPRESENTACIONES Y NIVELES DE ABSTRACCIÓN
### 1.7.1. Representación del sistema
Cada una de las tareas del proceso de desarrollo y producción del hardware digital, requiere el conocimiento de un tipo específico de información acerca del sistema, que va desde la especificación del sistema hasta el layout de los componentes físicos. 
El mismo sistema es descrito de diferentes formas y es examinado desde diferentes perspectivas. Estas perspectivas se denominan las representaciones o visiones del sistema:
#### Representación del comportamiento
Describe la funcionalidad del sistema. Ignorándose su implementación interna, y enfocándose en la relación entre las señales de entrada y de salida, definiendo qué señales de salida deben obtenerse cuando se aplica un determinado conjunto de señales de entrada.
#### Representación de la estructura 
Describe la implementación interna del sistema, especificando de qué componentes se compone y cómo están conectados estos componentes entre sí. Corresponde con una representación esquemática o diagrama del sistema. 
Normalmente se emplea el término "*net*" para describir un conjunto de cables o líneas conductoras que están conectados a un mismo nodo, y se usa el término "*netlist*" (lista de *nets*) para referirse a la descripción esquemática del sistema.
#### Representación física
Describe las características físicas del sistema, especificando las dimensiones de los componentes electrónicos, su posición en el circuito integrado y el camino físico del cableado de conexión entre los componentes. Añade, por tanto, información adicional a la visión estructural del mismo. Se trata de la especificación final para la fabricación del sistema.

### 1.7.2. Niveles de abstracción
Cuando el número de transistores que componen un circuito integrado se hace del orden de cientos de millones, es imposible para un ser humano, e incluso para un ordenador, procesar esa cantidad de información directamente. El método que posibilita diseñar sistemas tan complejos consiste en describir el sistema mediante diferentes abstracciones. 
==Una *abstracción* es un modelo simplificado del sistema, el cual muestra sólo unas determinadas características relevantes del sistema e ignora todos los demás detalles.==
En una abstracción sólo se muestra la información que es crítica para ese nivel en la representación del sistema.
Una abstracción de alto nivel está enfocada y muestra únicamente los datos más vitales. Por otra parte, una abstracción de bajo nivel es más detallada y tiene en cuenta información que es ignorada en abstracciones de nivel superior.
En el desarrollo de sistemas digitales suelen considerarse los cuatro niveles de abstracción siguientes: 
#### Nivel de transistor 
Nivel más bajo. En este nivel, los bloques básicos constitutivos de la visión estructural del circuito son los dispositivos electrónicos, tales como los transistores, resistencias y capacitares. 

La descripción del *comportamiento* se realiza normalmente mediante ecuaciones diferenciales y algebraicas, que son simuladas usando entornos de simulación de sistemas analógicos, como por ejemplo Spice. Al nivel de transistor, el circuito digital es tratado como un sistema analógico, en el cual las señales son de tiempo continuo, pudiendo tomar cualquier valor en un rango continuo. 

La *visión física* del circuito al nivel de transistor consiste en el layout de los componentes y sus conexiones. Define las máscaras fotolitográficas que deben usarse en los diferentes niveles del proceso de fabricación y es, por tanto, el resultado final del proceso de diseño.
#### Nivel de puertas lógicas 
Los bloques constitutivos básicos son puertas lógicas, tales como puertas AND, OR, XOR, MUX 2:1 de un bit, elementos básicos de memoria, tales como latch y flip-flop. En lugar de considerar que las señales tienen valores continuos, se considera únicamente si la señal está por encima o por debajo de un valor umbral, lo cual es interpretado como '1' lógico y '0' lógico, respectivamente.

Puesto que se realiza la simplificación de considerar que las señales tienen únicamente dos valores, el *comportamiento* es descrito mediante ecuaciones booleanas. Es decir, la abstracción esencialmente convierte un sistema continuo, que era descrito mediante ecuaciones diferenciales y algebraicas, en un sistema discreto, descrito mediante ecuaciones booleanas. 

En este nivel se simplifica también el modelado de la respuesta temporal. Se define el retardo en la *propagación* como el intervalo de tiempo que precisa un sistema para proporcionar una señal de salida estable. 
La representación *física* en este nivel consiste en la situación espacial de las puertas o celdas, y el camino (*routing*) que sigue el conexionado entre ellas.

En el nivel inferior de abstracción, se hablaba del *área de silicio* necesaria para construir el circuito. En este nivel, se cuenta el número de puertas lógicas que componen el circuito (denominado *gate count*), de modo que la medida es independiente de la tecnología. ==Se usa el área de la puerta N AND de dos entradas como unidad básica de medida, ya que este normalmente es el circuito lógico más sencillo desde el punto de vista físico. ==Así pues, en lugar de emplear el área física para expresar el tamaño a la complejidad del circuito, se emplea el número equivalente de puertas N AND en una determinada tecnología en particular.
#### Nivel de transferencia entre registros (RTL: Register Transfer Level) 
Los bloques constitutivos básicos son módulos construidos a partir de puertas. Estos módulos incluyen unidades funcionales (sumadores, comparadores, etc.), componentes de almacenamiento (registros, etc.) y componentes de enrutamiento de los datos (multiplexores, etc.) Este nivel podría llamarse abstracción al "nivel de módulos", sin embargo en diseño digital se emplea normal
mente el término "transferencia entre registros" y nosotros seguiremos esta terminología.

Hablaremos de "*nivel de transferencia entre registros*" (RTL: Register Transfer Level) para referirnos a la abstracción al nivel de módulos y llamaremos "*metodología de transferencia entre registros*" a la metodología específica de diseño.

La representación de los datos al nivel de transferencia entre registros es más abstracta. Frecuentemente las señales se agrupan entre sí y son interpretadas como un tipo especial de dato, tal como un número entero o el estado de un sistema. La representación del comportamiento a este nivel usa expresiones generales para especificar las operaciones funcionales y el camino de los datos, y emplea una máquina de estado finito para describir el sistema diseñado mediante la metodología de transferencia entre registros.

Una característica importante de la descripción al nivel de transferencia entre registros es el uso de una señal de *reloj* común en los elementos almacenadores. La señal de reloj tiene la función de sincronización, haciendo que se almacenen los datos en los componentes almacenadores en instantes específicos de tiempo, determinados por el flanco de subida de la señal de reloj. En un sistema bien diseñado, el periodo de la señal de reloj es lo suficientemente largo como para permitir que todas las señales se estabilicen dentro del periodo. ==Puesto que las señales son muestreadas sólo en los instantes de flanco de subida de la señal de reloj, las diferencias en los retardos de propagación y los glitches no tienen efecto sobre la operación del sistema. Esto permite considerar el tiempo en términos de número de ciclos de la señal de reloj, en lugar de tener que considerar todos los retardos en la propagación.==

El layout físico en esta abstracción se denomina fioor plan. Se emplea para encontrar el camino más lento entre los elementos de almacenamiento y así determinar el periodo de la señal de reloj.
#### Nivel de procesador
El mayor nivel de abstracción. Los bloques constitutivos básicos en este nivel, llamados frecuentemente intellectual properties (IPs), incluyen procesadores, módulos de memoria, etc. 

La descripción del comportamiento del circuito es similar a un programa codificado en un lenguaje de programación convencional, tal como C. Las señales son agrupadas e interpretadas como varios tipos de datos. El tiempo se mide en términos de pasos de computación, los cuales están compuestos de un conjunto de operaciones que se realizan entre dos instantes sucesivos de sincronización. 

El layout físico al nivel de procesador se denomina también floor plan. En este caso, los componentes usados en el fl.oor plan son mucho mayores que los usados en el nivel de transferencia entre registros.
![](img/Pasted%20image%2020250302213053.png)
El nivel de abstracción y la representación son dos dimensiones independientes del sistema. Cada nivel de abstracción tiene sus propias representaciones. Cada uno de los tres brazos muestra una representación o visión del sistema, y el nivel de abstracción aumenta al progresar desde el centro hacia los extremos. 

### 1.7.3. VHDL en el flujo de desarrollo
Los lenguajes para la descripción del hardware (HDL) constituyen un marco para el intercambio de información entre diseñadores y entre herramientas software. Permiten modelar y describir el circuito de manera precisa, de acuerdo a la representación del comportamiento y de acuerdo a la representación de la estructura, en cada uno de los cuatro niveles de abstracción.

Las herramientas de síntesis transforman automáticamente una descripción en VHDL del comportamiento del circuito al nivel de transferencia entre registros en una descripción en VHDL de la estructura del circuito al nivel de puertas lógicas (netlist al nivel de puertas). Asimismo, puede programarse en VHDL el banco de pruebas para testear la descripción RTL del comportamiento y puede emplearse ese mismo banco de pruebas para testear la descripción estructural al nivel de puertas. Puede emplearse una herramienta software para, a partir de la netlist al nivel de puertas en VHDL, generar automáticamente el layout del circuito, que no está expresado en VHDL.

## 1.8. CONCEPTOS BÁSICOS A TRAVÉS DE UN EJEMPLO
Un sistema digital puede ser descrito en cuatro niveles de abstracción (transistor, puertas lógicas, RTL y procesador) y desde tres visiones o representaciones diferentes (comportamiento, estructura y física). 

El lenguaje VHDL permite realizar descripciones del comportamiento y la estructura de los circuitos digitales al nivel de puertas lógicas, RTL y procesador. Es decir, permite: 
- Describir el comportamiento del circuito mediante funciones lógicas, operaciones de transferencia entre registros y algoritmos. 
- Describir la estructura del circuito mediante la instanciación y conexión de unidades de diseño de diferente complejidad, desde puertas lógicas hasta IPs.
En esta sección se mostrarán diferentes diseños de un circuito muy sencillo: un detector de paridad. Se trata de un circuito con tres entradas, agrupadas en un bus, y una salida. La salida toma el valor '1' cuando hay un número par de entradas con valor '1 '. Se supone que el cero es un número par.

### 1.8.1. Comportamiento al nivel de funciones lógicas
A partir de la tabla de la verdad, puede obtenerse la función lógica que describe la salida del circuito:
$$
par = a'_2 \cdot a'_1 \cdot a'_0 + a'_2 \cdot a_1 \cdot a_0 + a_2 \cdot a'_1 \cdot a_0 + a_2 \cdot a_1 \cdot a'_0
$$
El código VHDL que describe el circuito, en base a su comportamiento al nivel de función lógica, consta de dos unidades de diseño: entity y architecture.

- La unidad de diseño **entity** especifica los puertos de entrada y salida del circuito. El circuito tiene un puerto de salida (par) y un puerto de entrada (a), que es un vector de tres componentes: a(2), a(1) y a(O).
	La señal par es del tipo **std_logic**. ==Una señal del tipo **std_logic** usa un sistema lógico con nueve valores==. Además de 'O' y '1', usados para los valores binarios, hay otros valores que sirven para representar valores intermedios y desconocidos. Los más comúnmente usados son: 'U' (cuando a la señal no se le ha asignado todavía un valor), 'X' (cuando el valor de la señal no puede ser determinado, por ejemplo debido a que es generada por dos puertas lógicas, y una trata de poner el valor de la señal a 'O' y la otra a '1 ') y 'Z' (alta impedancia). Los conjuntos de líneas de señal pueden ser usados como un único elemento (denominado bus) en un circuito lógico digital. El tipo std_logic_ vector representa un vector de señales del tipo std_logic.
```vhdl
-- Detector de número par de entradas '1' 
-- entity 
-- fichero: detector Par. vhd 
library IEEE; 
use IEEE. std_logic_1164. all; 

entity detectorPar is 
	port ( par : out std_logic; 
			a : in std_logic_vector(2 downto o) );
end entity detectorPar;
```

- La unidad de diseño **architecture** especifica la operación interna y la organización del circuito.
	Las palabras reservadas (por ejemplo, entity, is, port, in, out, end) y los nombres definidos por el usuario (por ejemplo, not1, xor2, and2, x0, x1, y) pueden escribirse en VHDL indistintamente en mayúsculas o en minúsculas, puesto que en VHDL no se diferencia entre los caracteres en mayúscula y en minúscula. 

	Los nombres definidos por el usuario deben comenzar por una letra, seguida opcionalmente por cualquier secuencia de letras, números y caracteres guión bajo, con la limitación de que ni pueden aparecer dos guiones bajos seguidos, ni el guión bajo puede ser el último carácter del nombre. 
	Los *comentarios* comienzan con doble guión ( --) y se extienden hasta el final de la línea.
```vhdl
-- Detector de número par de entradas '1' 
-- architecture comportamiento func logica 
-- fichero: comp_funcLog. vhd 
library IEEE; 
use IEEE. std_logic_1164. all; 

architecture comp_funcLog of detectorPar is
	signal p1, p2, p3, p4 : std_logic; 
begin 
	par <= ( p1 or p2 ) or ( p3 or p4 ) after 20 ns; 
	p1 <= ( not a(2) ) and ( not a(1) ) and ( not a(O) ) after 15 ns; 
	p2 <= ( not a(2) ) and a(1) and a(O) after 12 ns; 
	p3 <= a(2) and ( not a(1) ) and a(O) after 12 ns; 
	p4 <= a(2) and a(1) and ( not a(O) ) after 12 ns; 
end architecture comp_funcLog;
```

La primera línea de la **architecture** muestra el nombre del cuerpo, *comp_funcLog*, y la correspondiente **entity**, *detectorPar*. La siguiente línea es la declaración de las señales:
```vhdl
signal p1, p2, p3, p4 : std_logic; 
```

Las señales p1, p2, p3 y p4 pueden ser interpretadas como conexiones entre las partes internas. La declaración es visible sólo dentro de la **architecture**.

La descripción de la **architecture** está comprendida entre **begin** y **end architecture**. Está compuesta por cinco *asignaciones concurrentes a señales*:

```vhdl
	par <= ( p1 or p2 ) or ( p3 or p4 ) after 20 ns; 
	p1 <= ( not a(2) ) and ( not a(1) ) and ( not a(O) ) after 15 ns; 
	p2 <= ( not a(2) ) and a(1) and a(O) after 12 ns; 
	p3 <= a(2) and ( not a(1) ) and a(O) after 12 ns; 
	p4 <= a(2) and a(1) and ( not a(O) ) after 12 ns;
```

Una asignación concurrente puede ser interpretada como un bloque del circuito. La señal de la izquierda de la asignación es la salida del bloque. Todas las señales que intervienen en la parte derecha de la asignación son las entradas al bloque. El resultado está disponible tras un cierto retardo, que se especifica mediante la cláusula **after**. 
Ej:
```vhdl
par <= ( p1 or p2 ) or ( p3 or p4 ) after 20 ns;
```
Bloque circuital con entradas p1, p2, p3 y p4, y salida par. El bloque realiza la operación OR de las cuatro entradas, y la operación tarda 20 ns en realizarse.

Esta **architecture** contiene cinco asignaciones concurrentes, que son interpretadas como cinco bloques circuitales. Las asignaciones concurrentes están conectadas a través de las señales que tienen en común. Cuando una señal aparece en la parte izquierda de una asignación y en la parte derecha de otra, esto significa que hay una conexión entre el bloque circuital representado por la primera asignación y el bloque circuital representado por la segunda.
![](img/Pasted%20image%2020250303123116.png)

Puesto que cada sentencia de asignación concurrente representa una parte del circuito y su interconexión, el orden en que se escriben las sentencias de asignación concurrente es indiferente.

Al contrario de lo que sucede con las sentencias en un lenguaje de programación, las *sentencias concurrentes* de asignación a señal son independientes entre sí, y pueden activarse en paralelo. Si alguna de las señales de entrada cambia de valor en el instante *t*, la sentencia concurrente es activada en dicho instante *t*. Es decir:
1. Se evalúa la expresión de la parte derecha de la asignación, usando para ello el valor que tienen las señales de entrada en dicho instante t. 
2. Se planifica asignar a la señal de salida (la situada en la parte izquierda de la asignación) el valor calculado, de manera que el nuevo valor se asignará a la señal una vez haya transcurrido el retardo de propagación especificado en la sentencia de asignación.

Como se explicó anteriormente, cuando se realiza el diseño de alto nivel frecuentemente se desconoce el valor del retardo de los bloques circuitales, ya que todavía no se ha realizado la síntesis. Es decir, no se ha especificado cómo va a implementarse en hardware el bloque circuital. Por este motivo, ==en el diseño de alto nivel de los circuitos no suele indicarse explícitamente el valor del retardo, omitiéndose la cláusula **after** en las sentencias de asignación a señal.==
Puede escribirse:
`par<= (pi or p2) or (p3 or p4 );`
Que se interpreta como:
```vhdl
par <= (pi or p2 ) or (p3 or p4 ) after δ;
```

El circuito puede ser descrito mediante la función lógica siguiente:

$$
par = (a_2 \oplus a_1 \oplus a_0)'
$$
El cuerpo de la architecture basado en esta función lógica:
```vhdl
-- Detector de número par de entradas '1' 
-- architecture comportamiento func log xor 
-- fichero: comp_funcLog_xor.vhd 
library IEEE; 
use IEEE.std_logic_1164. all; 

architecture comp_funcLog_xor of detectorPar is 
	signal impar : std_logic; 
begin 
	par <= not impar; 
	impar <= a(2) xor a(1) xor a(O);
end architecture comp_funcLog_xor;
```
![](img/Pasted%20image%2020250303124504.png)
### 1.8.2. Descripción de la estructura
En la visión estructural, el circuito está compuesto de *componentes* (esto es, bloques circuitales) conectados entre sí. La descripción especifica el tipo de cada componente y su conexión. Para ello, en el cuerpo de la **architecture**, el componente primero debe ser *declarado*, y a continuación *instanciado* y *conectado*.
![](img/Pasted%20image%2020250303124848.png)
Esta descripción corresponde con la función lógica $par = (a_2 \oplus a_1 \oplus a_0)'$
En el siguiente código se define la puerta inversora y la puerta XOR de dos entradas.
```vhdl
-- Inversor de 1 entrada: not1 
-- fichero: notl. vhd 
library IEEE; use IEEE. std_logic_1164. all; 
entity not1 is 
	port ( yO : out std_logic; 
			xO : in std_logic ) ; 
end entity not1; 
architecture not 1 of not 1 is 
begin 
	yO <= not xO; 
end architecture not 1; 
--------------------------------------------------------------
-- OR exclusiva de 2 entradas: xor2
-- fichero: xor2. vhd 
library IEEE; use IEEE. std_logic_1164.all; 
entity xor2 is 
	port ( yO : out std_logic; 
			xO, x1 : in std_logic );
end entity xor2; 
architecture xor2 of xor2 is 
begin 
	 yO <= xO xor x1; 
end architecture xor2;
--------------------------------------------------------------
-- Detector de número par de entradas '1' 
-- architecture estructura puertas xor-not 
-- fichero: estruc_xor_not. vhd 
library IEEE; use IEEE. std_logic_1164. all; 
architecture estruc_xor _not of detectorPar is 
	component xor2 is 
		port ( yO : out std_logic; 
				xO, x1 : in std_logic );
	end component xor2; 
	component not 1 is 
		port ( yO : out std_logic; 
				xO : in std_logic ) ; 
	end component not 1; 
	signal s1, s2 : std_logic; 
begin 
	unit1 : xor2 port map ( xO => a(O), x1 = > a(1), yO = > s1 ); 
	unit2 : xor2 port map ( xO = > s1, x1 = > a(2), yO = > s2 ); 
	unit3 : not1 port map ( xO => s2, yO = > par );
end architecture estruc_xor _not;
```

Dentro de la architecture, en primer lugar se declaran los componentes. La declaración de la puerta XOR es la siguiente:
```vhdl
component xor2 is 
		port ( yO : out std_logic; 
				xO, x1 : in std_logic );
	end component xor2; 
```
La información contenida dentro de la declaración es similar a la declaración de la entity del componente, en la cual se especifican sus puertos de entrada y salida. 

Aparte de la declaración de los componentes, en la architecture se declaran también dos señales internas:
```vhdl
signal s1, s2 : std_logic;
```

El cuerpo de la architecture consiste en tres sentencias, en cada una de las cuales se instancia y conecta un componente:
`unit1 : xor2 port map ( xO => a(O), x1 => a(1), yO=> s1 );`
Hay tres elementos en esta sentencia. El primero es la etiqueta **unit1**, que sirve para designar este componente. El segundo es la clase del componente: **xor2**. La tercera es **port map ( ... )**, que define la correspondencia entre las señales formales (puertos definidos en la entity del componente) y las señales actuales (las señales usadas en el cuerpo de la **architecture**).
En este ejemplo, port map ( ... ) indica que xO, x1, yO están conectadas a a(O), a(1), s1 respectivamente.

Las tres instanciaciones de los componentes describen el circuito completo.
La instanciación de un componente es un tipo de sentencia concurrente y puede mezclarse en el cuerpo de una architecture con otros tipos de sentencias concurrentes, tales como las sentencias de asignación concurrente a señal o como los bloques process, que explicaremos a continuación.

### 1.8.3. Descripción abstracta del comportamiento
En un diseño grande, la implementación puede ser muy compleja. Por este motivo, el diseño se realiza en diferentes pasos, progresando desde una descripción inicial abstracta del funcionamiento del circuito, independiente de la plataforma hardware que vaya a usarse para implementar el circuito, hasta llegar a la descripción detallada al nivel hardware.

El lenguaje VHDL facilita al diseñador realizar una descripción abstracta del comportamiento del circuito. Uno de los recursos que proporciona para ello el lenguaje son los bloques **process**. ==Un bloque **process** es una construcción que encapsula un fragmento de código VHDL secuencial, y dentro de la cual pueden declararse y usarse variables, que son locales al bloque **process**.== La característica distintiva del código secuencial es que es ejecutado en el mismo orden en el cual ha sido escrito. La sintaxis básica del bloque **process** es la siguiente:
```vhdl
process ( lista_de_sensibilidad ) 
	Declaración de variables locales 
begin 
	Código_secuencial 
end process;
```

==En el bloque **process** puede especificarse una lista de señales, denominada *lista de sensibilidad*, que defina las condiciones para la ejecución del bloque: cuando cambia el valor de alguna de las señales incluidas en esta lista, entonces se ejecuta el cuerpo del bloque **process**.==
Ejemplos de descripción abstracta del comportamiento del circuito detector de un número par de entradas '1':
1.
```vhdl
-- Detector de número par de entradas '1 ' 
-- architecture comportamiento red xor 
-- fichero: comp_recLxor. vhd 
library IEEE; 
use IEEE. std_logic_1164. all; 

architecture comp_red_xor of detectorPar is 
	signal impar : std_logic; 
begin 
	par <= not impar; 
	process (a) 
		variable tmp : std_logic; 
	begin 
		tmp := '0'; 
		for i in 2 downto O loop 
			tmp := tmp xor a(i); 
		end loop; 
		impar <= tmp; 
	end process; 
end architecture comp_red_xor;
```
![](img/Pasted%20image%2020250303131004.png)
La **architecture** *comp_red_xor* contiene un bloque *process*, que utiliza una variable y un bucle **for**. Al contrario de lo que sucede con las señales y las asignaciones a señales, la variable y el bucle no tienen una correspondencia directa con el hardware. El bloque **process** se trata como una unidad indivisible, cuyo comportamiento es especificado mediante sentencias secuenciales.

2.
```vhdl
-- Detector de número par de entradas '1' 
-- architect7LTe comportamiento algoTitmo 
-- fichem: comp_alg. vhd 
library IEEE; 
use IEEE . std_logic_1164. all; 

architecture comp_alg of detectorPar is 
begin 
	process (a) 
		variable suma, r : integer; 
	begin 
		suma :=O; 
		for i in 2 downto O loop 
			if a( i) = ' 1 ' then 
				suma := suma + 1; 
			end if; 
		end loop; 
		r := suma mod 2; 
		if (r = o) then 
			par < = '1'; 
		else 
		par < = '0'; 
		end if; 
	end process; 
end architecture comp_alg;
```
![](img/Pasted%20image%2020250303131321.png)
El segundo ejemplo usa únicamente un bloque **process**, en el cual se describe el algoritmo que realiza la operación que se desea que realice el circuito. En primer lugar, el algoritmo suma el número de '1' en las entradas, calcula el resto de la división entre 2, y finalmente usa una sentencia if para generar el resultado en función del valor del resto de la división.
### 1.8.4. Banco de pruebas
Uno de los usos principales de un programa en VHDL es la simulación, que se usa para ==estudiar la operación del circuito y para verificar que el diseño se ha realizado correctamente.==
Se pueden programar unas rutinas en VHDL que generen los vectores de test y otras que comparen las respuestas obtenidas de aplicar los vectores de test al circuito, con las respuestas que deberían obtenerse del circuito.
Ej de banco de pruebas para el circuito detector de un número par de entradas '1':
```vhdl
-- Banco de pruebas del detector de número par de entradas '1' 
-- fichero: bp_detectorPar. vhd 
library IEEE; use IEEE.std_logic_1164.all; 

entity bp_detectorPar is 
end entity bp_detectorPar; 

architecture bp_arch of bp_detectorPar is 
	component detectorPar is 
		port ( par :  out std_logic; 
				a  :  in std_logic_vector(2 downto o) );
	end component detectorPar; 
	signal test_in : std_logic_vector(2 downto O); 
	signal test_out : std_logic; 
begin 
	-- Instancia del circuito que va a ser testeado 
	UUT : detectorPar port map ( par => test_out, a => test_in ); 
	-- Vectores de test 
	vect_test: process 
	begin 
		test_in <= "000";     wait for 200 ns;
		test_in <= "001";     wait for 200 ns; 
		test_in <= "010";     wait for 200 ns; 
		test_in <= "011";     wait for 200 ns; 
		test_in <= "100";     wait for 200 ns; 
		test_in <= "101";     wait for 200 ns; 
		test_in <= "110";     wait for 200 ns; 
		test_in <= "111";     wait for 200 ns; 
	end process vect_ test; 
	-- Verificación de las salidas 
	verif : process 
		variable error _status : boolean;
	begin
		wait on test_in;      wait for 100 ns;
		if (( test_in = "000" and test_out = '1') or
			( test_in = "001" and test out = '0') or
			( test_in = "010" and test_out = '0') or
			( test_in = "011" and test out = '1') or
			( test_in = "100" and test out = '0') or
			( test_in = "101" and test_out = '1') or
			( test_in = "110" and test out = '1') or
			( test_in = "111" and test_out = '0')) 
		then 
			error_status := false; 
		else 
			error _status := true; 
		end if; 
		assert not error _status report "Test fallado." severity note; 
	end process verif; 
end architecture bp_arch;
```
El banco de pruebas consta de una **entity** y una **architecture**. Puesto que el banco de pruebas está autocontenido, la **entity** no tiene ningún puerto. La **architecture** consta de tres sentencias concurrentes: la instanciación del componente a testear y dos bloques **process**. Un bloque **process** se usa para generar los vectores de test y el otro se usa para comprobar que las salidas del circuito son correctas.

==El bloque **process** llamado *vect_test* es el generador de estímulos: produce todas las combinaciones de valores de la entrada al circuito, desde "000" hasta "111".== Cada una de las combinaciones de las entradas se mantiene durante 200 ns. Obsérvese que las comillas simples (' ') se usan para los bits individuales, mientras que las comillas dobles (" ") se usan para los vectores.

El segundo bloque **process**, llamado *verif*, espera a que se produzca un cambio en las señales de entrada, a continuación espera 100 ns más, con el fin de permitir que se estabilicen las señales de salida del circuito, y entonces comprueba el valor obtenido de las salidas con el valor correcto conocido. Si ambos valores no coinciden, muestra un mensaje indicando el error.
![](img/Pasted%20image%2020250303133640.png)
### 1.8.5. Configuración
El lenguaje VHDL separa de manera intencionada la declaración de la **entity** y la **architecture** en dos. unidades de diseño independientes. Esto facilita asociar múltiples **architecture** con una determinada **entity**.
A la hora de realizar la simulación y la síntesis, debemos especificar qué **architecture** asociar con la **entity**. Esto puede hacerse definiendo una **configuration**, como la mostrada a continuación para nuestro circuito ejemplo. Si no se ha definido una **configuration**, el entorno de simulación escogerá por defecto la última **architecture** que ha sido compilada.
```vhdl
-- Detector de número par de entradas '1' 
-- Configuration 
--fichero: conf_detectorPar.vhd 
configuration conf_detectorPar of bp_detectorPar is 
	for bp_arch 
		for uut: detectorPar 
			use entity work. detectorPar( comp_alg); 
		end for; 
	end for; 
end configuration conf _detectorPar;
```

### 1.9.1. Diseño de un buffer triestado
El buffer triestado tiene dos entradas ( d y E) y una salida (y). Dependiendo del valor de la entrada E, la salida puede tomar el valor de la entrada o el valor Z (alta impedancia). Cuando el buffer se encuentra en el estado de alta impedancia, se comporta como un circuito abierto.

```vhdl
-- Modelo del buffer triestado 
-- buffer Triestado.vhd 
library IEEE; 
use IEEE. std_logic_1164.all; 

entity Buffer_TriEstado is port 
	( y : out std_logic; 
		E : in std_logic; 
		d : in std_logic ) ; 
end entity Buffer_TriEstado ; 

architecture Behavioral of Buffer_TriEstado is 
begin 
	process (E, d) 
	begin 
		if (E = ' 1 ') then 
			y<= d; 
		else 
			y<= 'Z'; 
		end if; 
	end process; 
end architecture Behavioral;
```
Obsérvese que el diseño consta de tres partes. En primer lugar, se indica qué librerías van a usarse en la definición del modelo. A continuación, se define la interfaz del circuito (módulo entity). Finalmente, se define el comportamiento del circuito (módulo architecture).

### 1.9.2. Diseño del banco de pruebas
```vhdl
-- Banco de pruebas 
-- bp_bufferTriestado.vhd 
library IEEE; 
use IEEE. std_logic_1164.all; 

entity bp_Buffer_TriEstado is 
end entity bp_Buffer_TriEstado; 

architecture bp_Buffer_TriEstado of bp_Buffer_TriEstado is 
	signaL y : std_logic; -- Conectar salida UUT 
	signaL d, E : std_logic; -- Conectar entradas UUT 
	
	component Buffer_ TriEstado is port 
		( y : out std_logic; 
		  E, d : in std_logic ) ; 
	end component Buffer_TriEstado; 
	
begin 
	-- Instanciar y conectar UUT 
	uut : component Buffer_TriEstado port map 
			( y => y, E => E, d => d ); 
	gen_ ve e_ test : process Ç
	begin 
		E <= '0'; d <= '0'; 
		wait for 10 ns; 
		d <= '1'; 
		wait for 10 ns; 
		E<= '1'; 
		wait for 10 ns; 
		d <= '0'; 
		wait for 10 ns; 
		report "Final de la simulación"; 
		wait; 
	end process gen_vec_test; 
end architecture bp_Buffer_TriEstado;
```
La definición del banco de pruebas contiene las mismas tres partes que la descripción del circuito: en primer lugar se indica qué librerías van a usarse, a continuación se define la interfaz del circuito (módulo **entity**) y finalmente se define su comportamiento (módulo **architecture**).

La interfaz del banco de pruebas no contiene ningún puerto. En la **architecture** se instancia el circuito que va a ser probado (UUT) y se definen las señales y, E y d, que son conectadas a los puertos del UUT. En el bloque **process** llamado *gen_vec_test*, se define la secuencia de vectores de test que son aplicados al UUT

# TEMA 2 CONCEPTOS BÁSICOS DE VHDL
## 2.1. INTRODUCCIÓN
Se ha definido un subconjunto del lenguaje VHDL, denominado VHDL synthesis interoperability subset (estándar IEEE 1076.6), que contiene los tipos de datos, operadores y otras capacidades de VHDL que deberían ser usados para crear código VHDL sintetizable. Esto es, código a partir del cual las herramientas de CAD puedan generar automáticamente circuitos hardware que funcionen.

NOTA CLASE 3/3/25
mirar ej 2.5
**after** desde el momento que se ejecuta la instrucción cuenta, la siguiente instrucción será en el mismo instante, o puedes poner el mismo valor hay que ir incrementando.
**wait** podemos poner el mismo valor e irá añadiéndose

## 2.2. UNIDADES DE DISENO
Se denomina *entidad de diseño* al bloque constitutivo básico para la descripción del hardware en VHDL. Consta al menos de las dos *unidades de diseño* siguientes:
- **Entity**: representa la definición de la interfaz entre el diseño y el entorno en el cual se usa. Esta definición incluye los *puertos de conexión* (señales de entrada y/ o salida) del circuito y sus *constantes generic*, así como declaraciones y sentencias que forman parte del diseño. 
- **Architecture**: permite definir el comportamiento y la estructura de la entidad de diseño. Es decir, cómo los puertos de salida de la entidad de diseño se relacionan con sus puertos de entrada.
Un fichero con código VHDL puede contener varias unidades de diseño, pero una unidad de diseño no puede ser dividida en dos o más ficheros.

Un tercer tipo de unidad de diseño de VHDL es el **package**, el cual se emplea normalmente para agrupar una colección de tipos de datos, subprogramas y componentes, que están de alguna forma relacionados entre sí y que van a ser usados por otros programas VHDL.

Finalmente, otro tipo de unidad de diseño. de VHDL es la **configuration**, que ==permite relacionar en tiempo de compilación la entity con la architecture.==

El hecho de que la **entity** y la **architecture** se definan por separado, y que puedan ser compiladas separadamente, facilita la definición de **varias architecture para una misma entity.** Ej: varias architecture de una misma entidad de diseño, correspondientes a diferentes versiones del circuito: velocidad baja, media y alta.

Si no se define la configuration, en la cual se especifica explícitamente la architecture que corresponde con la entity, entonces el entorno de simulación asocia a la entity aquella de sus architecture que ha sido compilada en último lugar.

## 2.3. ENTITY
La entity especifica la interfaz del diseño, definiendo la parte de él que es visible desde "el mundo exterior".

En el Tema 1 se mostraron algunos ejemplos de declaración de **entity**. Así, en el Código VHDL l. 7, que describe un banco de pruebas para el circuito detector de paridad, se encuentra la declaración
```vhdl
entity bp_detectorPar is 
end entity bp_detectorPar; 
```
que sólo contiene el nombre asignado a la **entity**, ``bp_detectorPar``, y las siguientes palabras reservadas del lenguaje: **entity**, **is** y **end**. ==En la entity se declara la lista de señales que componen la interfaz del circuito. A estas señales de la interfaz se las denomina *puertos*.== Dado que la interfaz del banco de pruebas no contiene ninguna señal, en su entity no se declara ningún puerto.
![](img/Pasted%20image%2020250310132309.png)
	Entity de las puertas NOT, XOR y AND
### 2.3.1. Cláusula port
Las señales de la interfaz, a las que se denomina puertos, se declaran mediante la cláusula opcional port, en la cual se indica el nombre de los puertos, su modo y su tipo. La sintaxis es:
```vhdl
entity nombre_entity is 
	port ( 
		nombres_puertos : modo tipo_dato;
		nombres_puertos : modo tipo_dato;
		...
		nombres_puertos : modo tipo_dato 
		) ; 
end entity nombre_entity;
```

Los puertos declarados en la **entity** son visibles desde la propia **entity** y desde las **architecture** asociadas a la **entity**. 
El *modo* del puerto indica la dirección de la señal: 
- ==Las palabras reservadas **in** y **out** indican que la señal fluye hacia el circuito o desde el circuito, respectivamente. Describen el hecho de que el puerto correspondiente es una entrada o una salida del circuito. ==
- ==La palabra reservada **inout** indica que la señal fluye en ambas direcciones, es decir, que se trata de un puerto bidireccional.==
En este texto se aplica el convenio de declarar primero los puertos de salida y a continuación los de entrada, si bien este convenio no es universalmente aceptado.

==Al describir los circuitos debe tenerse en cuenta que un puerto cuyo modo es **out** no puede ser usado como una señal de entrada.==
Ej:
![](img/Pasted%20image%2020250310163310.png)
```vhdl
--CÓDIGO INCORRECTO:

library IEEE; 
use IEEE. std_logic_1164. all; 

entity modoPuertos is
	port ( x, y : out std_logic; 
			a, b : in std_logic); 
end entity modoPuertos; 

architecture arch_incorrecta of modoPuertos is 
begin 
	x <=a and b; 
	y <= not x; --MAL, produce errOr de compilación 
end architecture arch_incorrecta;
```

Puesto que en el código se usa la señal x para calcular la señal y, el compilador de VHDL considera que la señal x fluye hacia el circuito. Esto contradice el hecho de que el modo de la señal x es out. La consecuencia de ello es que se produce un error de compilación.

Una posible solución sería cambiar el modo del puerto x a inout. Sin embargo, ésta no es una buena solución, ya que de hecho no se trata de un puerto bidireccional.

Una alternativa mucho mejor es definir una señal interna para representar el resultado intermedio.
![](img/Pasted%20image%2020250310163841.png)
```vhdl
library IEEE; 
use IEEE. std_logic_1164.all; 
entity modoPuertos is 
	port ( x, y : out std_logic; 
			a, b : in std_logic);
end entity modoPuertos;

architecture arch_correcta of modoPuertos is
	signal ab : std_logic;
begin
	ab <= a and b;
	x <= ab;
	y <= not ab;
end architecture arch_correcta;
```
### 2.3.2. Cláusula generic
La cláusula **generic** se usa para declarar aquellas constantes cuyo valor necesite ser modificado a fin de adaptar el diseño a sus diferentes aplicaciones. A estas constantes se las denomina *constantes generic*.
Las constantes generic son visibles desde la propia **entity** en que son declaradas y desde las **architecture** asociadas a la **entity**. Ejemplos típicos de *constantes generic* son el valor de determinados retardos, el número de bits de un bus de señales, etc.
Ej:
```vhdl
entity and2 is 
	generic ( Tpd: time); 
	port ( yO : out std_logic; 
			xO, x1 : in std_logic ); 
end entity and2;
```
Esta **entity** incluye una constante **generic**, Tpd, del tipo predefinido **time**. El valor de esta constante **generic** puede ser usado en el cuerpo de cualquier **architecture** asociada a esta **entity**.
### 2.3.3. Declaraciones
En la **entity** pueden declararse subprogramas, atributos, tipos de datos, constantes, señales, etc. Estas declaraciones son visibles desde la propia **entity** y las **architecture** asociadas.
Ej:
```vhdl
entity bp is
	constant WORD_SZ : integer := 16;
	constant DELAY : time      := 10 ns;
end entity bp;
```

### 2.3.4. Sentencias
En la **entity** pueden incluirse sentencias **assert**, llamadas concurrentes a procedimientos y bloques **process**. En ninguno de los casos deben producirse asignaciones a señal. 
El propósito de estas sentencias puede ser realizar comprobaciones sobre algunas de las características de la **entity**. Por ejemplo, si se incluye una sentencia **assert** en la **entity**, el mensaje se mostraría (si procede) al comienzo de la simulación, para cada una de las **architecture** que tenga esa **entity**.
### 2.3.5. Resumen
```vhdl
entity nombre_entity is
		cláusula generic 
		cláusula port 
		declaraciones 
begin 
	sentencias
end entity nombre_entity;
```
Ej: entity de un registro de desplazamiento de longitud N bits
```vhdl
entity shiftReg is 
	generic (N : integer );
	port   (SO              :  out std_logic; 
			RSTn, clk, SI : in std_logic ); 
	signal T: std_logic_vector( N downto O); 
begin 
	assert (N>3) and (N<33) 
		report "N fuera del rango 4 a 32";
end entity shiftReg;
```
## 2.4. ARCHITECTURE
La **architecture** permite definir el comportamiento y la estructura de la entidad de diseño. Esta definición puede realizarse mediante: 
- Una *descripción estructural*, en la cual el componente es descrito mediante la instanciación y conexión de otros componentes de más bajo nivel. 
- Una *descripción de su comportamiento*, en la que se describe el comportamiento que debe tener el componente. 
- Una *descripción mixta* de la estructura y del comportamiento, que incluya la instanciación y conexión de componentes de más bajo nivel, y código describiendo el comportamiento.
![](img/Pasted%20image%2020250310174626.png)
	Architecture de las puertas NOT, XOR y AND
La definición de la unidad de diseño **architecture** tiene la sintaxis siguiente:
```vhdl
architecture nombre_architecture of nombre_entity is 
	Declaración de señales locales y constantes locales 
	Declaración de los componentes 
	Declaración de los subprogramas (procedimientos y funciones) 
begin 
	Instanciación de los componentes 
	Asignaciones concurrentes a señales y bloques process
end architecture nombre_architecture;
```
El área de texto previa a la palabra reservada ***begin*** es la parte declarativa. Es donde se declaran las señales y constantes (todas ellas locales a la definición de la **architecture**), los componentes que van a ser instanciados en la **architecture** y los subprogramas. Entre las palabras reservadas **begin** y **end** se define la estructura y el comportamiento de la entidad de diseño. Para ello, pueden emplearse sentencias concurrentes de asignación a señal, bloques **process**, y la instanciación y conexión de componentes.
## 2.5. ASIGNACIONES CONCURRENTES
Las asignaciones a señales directamente contenidas entre las palabras reservadas **begin** y **end** de la **architecture** se denominan *asignaciones concurrentes*, debido a que todas ellas se ejecutan de forma concurrente. Es decir, *el orden de ejecución de las sentencias concurrentes no está determinado por el orden en que se han escrito*. 
VHDL tiene dos tipos de asignaciones concurrentes a señal: la *asignación concurrente condicional* y la *asignación concurrente de selección*. Las *asignaciones concurrentes simples* (por ejemplo, e <= u and v;) pueden considerarse un caso particular de *asignación condicional*, en la cual no hay expresión condicional. A continuación, analizaremos cada uno de estos tres tipos de asignación concurrente a señal.

### 2.5.1. Asignaciones concurrentes simples
Sintaxis:
```vhdl
señal <= forma_de_onda;
```
donde la cláusula ``forma_de_onda`` consiste en la especificación de la expresión para el cálculo del nuevo valor de la señal y la especificación del tiempo que transcurre (retardo) entre el cálculo de dicho valor y su asignación a la señal.
La ejecución de una sentencia de asignación concurrente simple se produce en el instante en que cambia el valor de alguna de las señales que aparecen en la expresión escrita a la derecha del símbolo<=.
Ej:
```vhdl
yO <= not xO;
```

Es ejecutada cada vez que se produce un cambio en el valor de la señal x0. Se dice que esta sentencia, de la cual se calcula y0, es *"sensible"* a la señal x0.
Cuando no se especifica el retardo, VHDL considera que existe un retardo infinitesimal $\delta$. Es decir, la expresión not x0 se evalúa en el instante en que cambia el valor de x0, calculándose el nuevo valor de y0. Este nuevo valor se asigna a la señal transcurrido un tiempo $\delta$.
La asignación concurrente
```vhdl
y <= x1 + x2 after 10 ns;
```

indica que en el instante en que x1 o x2 cambien, debe evaluarse la expresión x1+x2, y el resultado debe asignarse a la señal y transcurridos 10 ns de *retardo inercial*. Puede emplearse la cláusula **transport** para indicar que el retardo en la asignación del nuevo valor a la señal es un **retardo de transporte**:
```vhdl
y <= transport x1 + x2 after 10 ns;
```

En el código VHDL usado para síntesis no se especifica el retardo de los componentes (los retardos dependen de los componentes, la tecnología, el cableado (*routing*) entre componentes, etc., es imposible sintetizar un circuito con un determinado valor del retardo), usándose en su lugar el retardo $\delta$. En este caso, la sintaxis es: 
``señal <= expr_nuevo_valor_señal; ``
donde se omite la cláusula **after** e implícitamente se entiende que la asignación del nuevo valor a la señal se produce tras un retardo $\delta$.
La *implementación conceptual* de las asignaciones concurrentes simples es sencilla. La asignación puede ser traducida mediante un bloque circuital, cuya salida es la señal situada en el lado izquierdo de la asignación y cuyas entradas son las señales situadas en el lado derecho de la asignación. Cada operador que interviene en la asignación es reemplazado por un bloque circuital, cuyas entradas y salidas son conectadas adecuadamente.
Ej:
```vhdl
y <= '1'; 
y <= a + b + e - 1; 
y <= ( x1 and x2) or ( x3 and x4 );
```
![](img/Pasted%20image%2020250310191601.png)
Cuando una señal aparece como entrada (en el lado derecho) y salida (en la parte izquierda) de la sentencia de asignación, se forma un lazo cerrado de realimentación, que da lugar a la creación de un estado interno o a comportamiento oscilatorio.
Ej:
```vhdl
y<= (y and (noten) ) or ( x anden);
```
Obsérvese que la salida (y) depende de las entradas (en, x) y del estado interno (el valor anterior de y), con lo cual el circuito no es combinacional, ya que en un circuito combinacional la salida es función únicamente de las entradas.
Cuando una asignación concurrente contiene un lazo cerrado, el valor de la señal de salida es sensible al retardo interno en la propagación y puede oscilar. Este tipo de circuito confunde a las herramientas de síntesis, y complica la verificación y el test del circuito. Es una mala práctica de diseño y debe evitarse por completo cuando se diseña para síntesis.

### 2.5.2. Asignaciones concurrentes condicionales
Sintaxis de una *asignación concurrente condicional* a una señal:
```vhdl
señal   <=  expr_nuevo_valor_señal_1 when expr_booleana_1 else
			expr_nuevo_valor_señal_2 when expr_booleana_2 else
			expr_nuevo_valor_señal_3 when expr_booleana_3 else
...
			expr_nuevo_valor_señal_n;
```
Estas expresiones lógicas son evaluadas por orden, primero ``expr_booleana_1`` , luego ``expr _booleana_2`` y así sucesivamente, hasta que una de ellas vale *true*, en cuyo caso se calcula el nuevo valor de la señal de la correspondiente expresión. Si ``expr_booleana_1``, ... , ``expr_booleana_i-1`` valen false y ``expr_booleana_i`` vale *true*, entonces el nuevo valor de la señal es el obtenido de evaluar ``expr _nuevo_ valor _señal_i``.

Si todas las expresiones booleanas valen *false*, el nuevo valor de la señal se calcula evaluando ``expr _nuevo_ valor _señal_n``. En cualquier caso, el nuevo valor calculado se asigna a la señal una vez ha transcurrido un retardo, que por defecto vale $\delta$.

En la síntesis hardware de una sentencia concurrente condicional se emplean los circuitos necesarios para obtener cada uno de los nuevos valores de la señal (``expr_nuevo_valor_señal_1, ... , expr_nuevo_valor_señal_n``), los circuitos necesarios para obtener cada una de las expresiones booleanas ( ``expr_booleana_1, ... , expr_booleana_n-1``), y el circuito que implementa la *red de prioridad*.

La *red de prioridad* puede implementarse mediante la conexión de multiplexores de dos entradas (MUX 2:1). Para entender cómo se construye la red de prioridad, consideremos primero una sentencia condicional con una única cláusula **when**:

```vhdl
señal   <=  expr_nuevo_valor_señal_1 when expr_booleana_1 else
			expr_nuevo_valor_señal_2;
```
En este caso, la red de prioridad consiste en un único multiplexor. Se conecta a la entrada '1' del MUX 2:1 la salida del circuito que implementa`` expr _nuevo_ valor _señal_1`` y se conecta a la entrada '0' la salida del circuito que implementa ``expr _nuevo_ valor _señal_2``. La salida del circuito que implementa la expresión booleana se conecta a la entrada de selección del MUX.
![](img/Pasted%20image%2020250310193420.png)

La generalización al caso de más de una cláusula **when** es inmediata. Por ejemplo, en la figura se muestra la red de prioridad que implementa una sentencia concurrente con tres cláusulas **when**:
```vhdl
señal   <=  expr_nuevo_valor_señal_1 when expr_booleana_1 else
			expr_nuevo_valor_señal_2 when expr_booleana_2 else
			expr_nuevo_valor_señal_3 when expr_booleana_3 else
			expr_nuevo_valor_señal_4;
```
![](img/Pasted%20image%2020250310193714.png)
El proceso de síntesis se realiza de manera análoga para cualquier número de cláusulas **when**. ==Dado que cada cláusula **when** introduce una etapa adicional en la red de multiplexores, el número de etapas de la *red de prioridad* crece al aumentar el número de cláusulas **when**.==

### 2.5.3. Asignaciones concurrentes de selección
Sintaxis:
```vhdl
with expresión_selección select 
	señal  <=   expr_nuevo_valor_señal_1 when valor_selección_1,
				expr_nuevo_valor_señal_2 when valor_selección_2,
				...
				expr_nuevo_valor_señal_n when valor_selección_n;
```
Si no se indica el retardo, se asume implícitamente que la asignación a la señal debe realizarse transcurrido un retardo 5.
El resultado de evaluar ``expresión_selección`` debe ser o bien un número entero o bien un vector unidimensional. En cualquier caso, el resultado obtenido de evaluar la expresión de selección tiene un número finito de posibles valores. Por ejemplo, una señal del tipo ``bit_vector(1 downto 0)`` puede tomar $2^2$ posibles valores: "00", "01", "10" y "11".

El valor que se asigna a la señal depende del valor de la expresión de selección. Cada una de las selecciones ``valor _selección_1, ... , valor _selección_n`` debe ser uno o varios de los posibles valores de ``expresión_selección``, pero satisfaciendo dos condiciones: 
1. Deben ser mutuamente excluyentes. Es decir, un mismo valor no puede aparecer en más de una de las selecciones. 
2. Deben incluir todos los posibles valores de ``expresión_selección``. Puede emplearse la palabra reservada **others** como último valor de selección (esto es, ``valor _selección_n``) para representar todos los valores que no han sido usados hasta el momento.
Cada uno de los posibles valores de ``expresión_selección`` debe aparecer en una y sólo en una de las selecciones.

Conceptualmente, la implementación hardware de una asignación concurrente de selección puede realizarse empleando un multiplexor, que utiliza la señal ``expresión_selección`` para seleccionar cuál de las expresiones del nuevo valor de la señal debe usarse para evaluar la señal. Cada uno de los posibles valores de la señal ``expresión_selección`` corresponde con un puerto de entrada del multiplexor.
![](img/Pasted%20image%2020250310195152.png)
Todas las sentencias concurrentes de selección tienen un diagrama conceptual similar. La diferencia está en el número de valores que puede tomar la expresión de selección, el cual determina el tamaño del multiplexor.

Ej: Multiplexor de 4 entradas de 8 bits
```vhdl
-- MUX 4:1 de 8 bits 
-- fichero: mux_4x1_8bits_archSelec.vhd 
library IEEE; 
use IEEE.std_logie_1164.all; 

entity mux4 is 
	port (  x             : out std_logic_vector(7 downto O);
			a, b, e, d    : in std_logic_ vector(7 downto O);
			s             : in std_logic_vector(1 downto o) );
end entity mux4;  

architecture arch_selec of mux4 is
begin 
	with s select
	 x <= a when "00",
	 b when "01", 
	 e when "10", 
	 d when others; 
end architecture arch_selec;
```

### 2.5.4. Sensibilidad de las sentencias concurrentes
Una asignación concurrente es ejecutada cada vez que cambia el valor de alguna de las señales a las que es sensible. 
	==Una asignación concurrente simple es *sensible* a todas las señales que intervienen en la expresión para el cálculo del nuevo valor de la señal. ==
	==Una sentencia concurrente condicional es *sensible* a todas las señales que intervienen en las expresiones para el cálculo del nuevo valor de la señal y también a todas las señales que intervienen en las expresiones booleanas. ==
	==Una sentencia concurrente de selección es *sensible* a todas las señales que Intervienen en la expresión de selección y a todas las señales que intervienen en las expresiones para el cálculo del nuevo valor de la señal.==

## 2.6. SENTENCIA GENERATE
Las sentencia **generate** facilita la ejecución iterativa o condicional de una porción de código concurrente.
### 2.6.1. Sentencia generate iterativa
Sintaxis:
```vhdl
etiqueta: for índice in rango_bucle generate 
	Declaración de señales locales y constantes locales 
begin 
	Sentencias_ concurrentes 
end generate etiqueta;
```
==El bucle **generate** repite las sentencias concurrentes del cuerpo del bucle un número fijo de iteraciones, que está determinado por el rango de valores ``rango_bucle``. Para que la sentencia sea sintetizable, es necesario que los límites del rango sean estáticos.==

El índice del bucle (``índice``) especifica el valor del rango de valores que corresponde con la iteración actual, con lo cual va tomando los sucesivos valores de ``rango_bucle``. El índice del bucle (``índice``) no necesita ser declarado, ya que automáticamente pertenece al mismo tipo de dato que ``rango_bucle``.
Si no se realiza la declaración de señales y constantes locales, puede omitirse la palabra reservada **begin**.
Ej:
```vhdl
signal z std_logic_vector( 7 downto 0); 
signal x std_logic_vector( 7 downto 0); 
signal y std_logic_vector(15 downto 0); 
E1: for i in x'range generate 
	z(i) <= x(i) AND y(i+8); 
end generate E1;
```
El rango de índices del vector x, (``7 downto 0``), se obtiene invocando el atributo **range** del vector, de la forma ``x'range``.
### 2.6.2. Sentencia generate condicional
Sintaxis:
```vhdl
etiqueta: if expresión_ booleana generate 
	Declaración de señales locales y constantes locales 
begin 
	Sentencias_ concurrentes 
end generate etiqueta;
```
Las sentencias concurrentes se ejecutan sólo si ``expresión_booleana`` vale true. Si no se realiza la declaración de señales y constantes locales, puede omitirse la palabra reservada **begin**.
Es posible anidar sentencias generate.
Ej: una sentencia generate condicional anidada dentro de una sentencia iterativa:
```vhdl
etiqueta1: for índice in rango_bucle generate
	...
	etiqueta2: if expresión_ booleana generate
		...
	end generate etiqueta2; 
	...	
end generate etiqueta!;
```

## 2.7. BLOQUE PROCESS
Para describir la operación de un determinado circuito, puede ser preciso emplear una secuencia de sentencias que se ejecuten justamente en el orden en que han sido escritas.
Sintaxis:
```vhdl
etiqueta: process ( lista_de_sensibilidad ) 
	Declaración de variables locales 
	Declaración de subprogramas (funciones y procedimientos) 
begin 
	Código_secuencial 
end process etiqueta;
```
La *etiqueta* con la que se inicia y finaliza la declaración es opcional. Su finalidad es documentar el código, para lo cual es recomendable emplear etiquetas que describan la finalidad del bloque.
La *lista de sensibilidad* es también opcional. Proporciona un mecanismo para definir la condición de ejecución del bloque: el bloque **process** se ejecuta cada vez que cambia el valor de una de las señales de su lista de sensibilidad.

En un bloque **process** no pueden declararse señales. Sin embargo, todas las señales declaradas en la **architecture**, y todas las señales y puertos declarados en la **entity**, son visibles desde dentro del bloque **process**. Por ejemplo, pueden intervenir en la parte derecha e izquierda de las asignaciones secuenciales, respetando siempre las limitaciones de lectura y escritura que impone el modo de los puertos (no se pueden leer puertos con modo **out**, ni escribir puertos con modo **in**).

La declaración de variables es opcional y se realiza antes de la palabra reservada **begin**. La sintaxis es:
``variable nombre_variable tipo rango := valor_inicial;``
El rango y el valor inicial son opcionales .. El valor inicial no es sintetizable, sólo se tiene en cuenta para la simulación.

Las variables declaradas dentro del bloque **process** son visibles sólo dentro del bloque. El valor de una variable no puede pasarse directamente fuera del bloque **process**. Cuando es necesario emplear el valor de una variable fuera del bloque **process**, éste debe ser asignado a una señal.
Las sentencias contenidas dentro de un bloque **process** son ejecutadas secuencialmente (en el mismo orden en que están escritas). Por ello, las sentencias de asignación a variables y a señales contenidas dentro del bloque **process** se denominan *sentencias secuenciales*.

Los bloques **process** se ejecuta concurrentemente unos respecto a los otros. El bloque **process** en su conjunto se considera una sentencia concurrente de alto nivel dentro de la definición de la **architecture**.

Las sentencias interiores a un bloque **process** se ejecutan repetidamente y consecutivamente, desde la primera sentencia del bloque hasta la última sentencia del bloque, una y otra vez, en un bucle infinito. Para evitarlo es preciso indicar en .qué punto debe suspenderse su ejecución y en qué situaciones debe reanudarse su ejecución. Esto puede hacerse de una de las dos maneras siguientes: mediante el uso de sentencias **wait** o mediante una *lista de sensibilidad*.

### 2. 7.1. Sentencias wait
Pueden incluirse sentencias **wait** en el código secuencial del bloque **process**. Al llegar a una sentencia **wait**, se suspende la ejecución de las sentencias del bloque. La ejecución queda suspendida hasta que ocurre cierto evento o hasta que transcurre cierto tiempo. 
Cuando finaliza la ejecución de la última sentencia del bloque **process**, comienza inmediatamente a ejecutarse de nuevo la primera sentencia del código del bloque.
#### Wait on
La sintaxis de la sentencia es: 
```vhdl
wait on señal1 , señal2, ... , señalN;
```

Se suspende la ejecución del código secuencial hasta que cambia el valor de una o varias de las señales señal1, señal2, ... , señalN.
#### Wait until 
La sintaxis de la sentencia es:
```vhdl
wait until expresión_booleana;
```

Se suspende la ejecución hasta que se evalúe la expresión booleana y ésta valga *true*. El simulador evalúa la expresión booleana únicamente cuando cambia el valor de alguna de las señales que intervienen en la expresión booleana. 
Si la expresión booleana contiene señales y variables, y en cierto instante cambia el valor de alguna de las variables, pero no cambia el valor de ninguna de las señales, entonces la expresión booleana no es evaluada en ese instante

Por ejemplo, las condiciones de las sentencias 
``wait until v<30; wait until true;`` 
nunca serían evaluadas, ya que no contienen ninguna señal.

Es posible especificar explícitamente la lista de sensibilidad de la sentencia **wait until**:
```vhdl
wait on señal1, señal2, ... , señalN 
until expresión_ booleana;
```
Cuando cambia el valor de alguna de las señales señal1 , ... , señal N, entonces se comprueba la expresión booleana. Si vale true, se reanuda la ejecución de las sentencias del bloque **process**.
#### Wait for 
La sintaxis de la sentencia es: 
``wait for expresión_ temporal;``

Se suspende la ejecución hasta que transcurra determinado intervalo de tiempo, que es calculado evaluando la expresión temporal. 
Un caso particular es cuando la expresión temporal es 0 ns. Cuando en el instante t se ejecuta la sentencia 
``wait for 0 ns; ``
la ejecución del código secuencial queda suspendida durante un tiempo $\delta$, reanundándose en t + $\delta$. De esta manera, se permite que se asignen a las señales los valores calculados en el instante t.
### 2.7.2. Lista de sensibilidad
Puede definirse la lista de señales a las cuales el bloque **process** es sensible. Esta lista se escribe, entre paréntesis, a continuación de la palabra reservada **process**. En este caso, el bloque **process** es ejecutado sólo en el instante en que una o varias de estas señales a las que es sensible cambia de valor.
```vhdl
process (reset_n, clk) is  -- Proceso activo cuando cambia el valor de reset o de clk
begin 
	if reset_n = '0' then  -- Comprueba reset asíncmno 
		q <= '0'; 
		q_n <= '1';
```
El bloque **process** sólo se ejecuta cuando se produce un cambio en el valor de la señal de reset o en el valor de la señal de reloj.

==No se permite emplear sentencias **wait** y **lista de sensibilidad** en un mismo bloque **process**. Debe optarse por uno de estos dos procedimientos para controlar la ejecución del bloque **process**.==

A todos los efectos, la lista de sensibilidad es equivalente a una sentencia **wait**.
Los dos bloques **process** siguientes son equivalentes:

```vhdl
procA: process (a1, a2) 
begin 
	a1 <= '0'; 
	a2 <= '1' after 2 ns; 
end process procA;
```
```
procB: process 
begin 
	a1 <= '0'; 
	a2 <= '1' after 2 ns; 
	wait on a1, a2; 
end process procB;
```
## 2.8. CÓDIGO SECUENCIAL
### 2.8.1. Asignación secuencial a una señal
Sintaxis:
```vhdl
señal <= expr_nuevo_valor_señal;
```
donde implícitamente se entiende que la asignación del nuevo valor de la señal se produce tras un retardo $\delta$. Como consecuencia del retardo $\delta$, si el bloque **process** tiene lista de sensibilidad (por tanto no tiene sentencias **wait**), entonces se asigna a las señales su nuevo valor una vez ha finalizado la ejecución de todas las sentencias del bloque.

Dentro de un bloque **process** pueden realizarse varias asignaciones secuenciales a una misma señal. Si todas las asignaciones a la señal tienen un retardo b, entonces sólo la última de ellas tiene efecto. Dado que el valor de la señal no es actualizado hasta que se completa la ejecución del bloque, la señal nunca adquiere valores "intermedios".
### 2.8.2. Asignación secuencial a una variable
Dentro de un bloque process pueden declararse variables. Sintaxis:
`variable := expr_nuevo_valor_variable;`
No se produce retardo o en las asignaciones a variables. Es decir, se asigna el nuevo valor a la variable en el mismo instante en que se evalúa la expresión.
### 2.8.3. Sentencia if
Sintaxis:
```vhdl
if expresión_booleana_1 then
	sentencias_secuenciales
elsif expresión_booleana_2 then
	sentencias_secuenciales 
...	
else 
	sentencias secuenciales 
end if;
```
Las expresiones booleanas son evaluadas secuencialmente. Cuando una de las expresiones vale true, se ejecutan las sentencias secuenciales de la rama correspondiente, ignorándose las sentencias de las demás ramas. Si ninguna de las expresiones vale true y existe rama **else**, entonces se evalúan las sentencias de la rama **else**.

Una cuestión que debe tenerse en cuenta es que cuando se asigna valor a una señal en alguna de las ramas de una sentencia if, pero no en todas las ramas, entonces se está introduciendo "memoria" en el circuito. Es decir, la síntesis de ese código VHDL dará lugar a un circuito secuencial. Esta situación se produce siempre que no existe la rama else, ya que en este caso no hay sentencias de asignación a las señales en caso de que todas las expresiones booleanas valgan false. Así pues, ==si se desea sintetizar un circuito combinacional, debe incluirse la rama **else**.==
La semántica de VHD L especifica que si no se asigna valor a una señal, entonces ésta mantiene su anterior valor.
### 2.8.4. Sentencia case
Sintaxis:
```vhdl
case expresión_case is 
	when valor_1 => 
		sentencias_secuenciales 
	when valor_2 => 
		sentencias_secuenciales 
	...
	when valor_n => 
		sentencias_secuenciales
end case;
```

Cada término valor_i debe ser un valor o conjunto de valores que puede tomar expresión_case. ==Los valores valor_1, ... , valor_n deben ser exclusivos entre sí y deben cubrir completamente el conjunto de valores posibles de expresión_case.== Puede emplearse **others** en la última selección para cubrir todos los valores no considerados

La sentencia secuencial case es similar a la sentencia select de asignación concurrente. Las siguientes sentencias son equivalentes:
```vhdl
with expresión_selección select
señal <= expr_nuevo_valor_señal_1
			when valor_selección_1, 
		expr_nuevo_valor_señal_2 
			when valor_selección_2, 
		...	
		expr_nuevo_valor_señal_n 
			when valor_selección_n;
```
```
case expresión_selección is 
	when valor_selección_1 => 
		señal <= expr_nuevo_valor_señal_1; 
	when valor_selección_2 => 
		señal <= expr_nuevo_valor_señal_2;
	...	
	when valor_selección_n => 
		señal <= expr_nuevo_valor_señal_n; 
end case;
```
Por otra parte, si se asigna valor a alguna señal en unas ramas de la sentencia case y no en otras, se está introduciendo "memoria" en el circuito, ya que la semántica de VHDL especifica que ==si no se asigna valor a una señal, entonces ésta conserva su valor anterior.==
### 2.8.5. Bucle for
Sintaxis:
```vhdl
for índice in rango_bucle loop
	sentencias_secuenciales 
end loop;
```
El bucle for anterior repite las sentencias secuenciales del cuerpo del bucle un número fijo de iteraciones, que está determinado por el rango de valores rango_bucle. El índice del bucle (índice) especifica el valor del rango de valores que corresponde con la iteración actual, con lo cual va tomando los sucesivos valores de rango_bucle. El índice del bucle (índice) no necesita ser declarado, ya que automáticamente pertenece al mismo tipo de dato que rango_bucle.

## 2.9. DESCRIPCIÓN DE LA ESTRUCTURA
VHDL permite diseñar circuitos de forma *modular* y *jerárquica*. Es decir, es posible describir un circuito mediante instanciación y conexión de otros circuitos que han sido previamente definidos

Para describir un circuito mediante la instanciación y conexión de circuitos previamente definidos, primero es necesario *declarar* los componentes. A continuación, deben *instanciarse* tantos componentes como requiera el diseño y debe especificarse cómo deben *conectarse*.
1. ***Declarar los componentes***. Un componente (**component**) representa la pareja **entity**/**architecture** que define un determinado circuito (aquel que va a instanciarse). La declaración del componente es muy similar a la declaración de la **entity** del circuito que va a ser usado como componente. Sintaxis:
	``` vhdl
	component nombre_componente is 
		cláusula_generic; 
		cláusula_port; 
	end component nombre_ componente;
	```
	En el cuerpo de la declaración deben escribirse las cláusulas **generic** y **port** que aparecen en la declaración de la **entity** del circuito que está siendo declarado como componente, en caso de que las haya.
	==Si el nombre que se asigna al componente, nombre_componente, es igual al nombre de la **entity** del circuito que está siendo declarado como componente y además existe una única **architecture** para esa **entity**, entonces la declaración del componente especifica de manera unívoca una **entity**/**architecture**. En este caso, no es necesario definir una configuration en la cual se especifique qué architecture está asociada a esa entity.==
	Si hay varias **architecture** asociadas a la **entity**, entonces aparte de la declaración del componente debe definirse una **configuration**, en la cual se especifique qué **architecture** de las asociadas a la **entity** debe emplearse en el componente.
2. ***Instanciar los componentes e indicar su conexión.*** Sintaxis:
	```vhdl
	nombre instancia  : component nombre_componente 
						port map ( asociación_puertos_señales );
	```
	La palabra reservada **component** es opcional. Las palabras reservadas **port map** están seguidas por una lista, escrita entre paréntesis, que relaciona los puertos de la instancia del componente con las señales del circuito compuesto.
	La conexión entre instancias de componentes se indica asociando a los puertos a conectar una misma señal del modelo compuesto. 
	La asociación entre los puertos de las instancias de los componentes y las señales del circuito compuesto puede realizarse de dos maneras: 
	- *Asociación posicional*, es decir, mediante la posición en que el puerto se declara en la cláusula port de la **entity** del componente. 
	- *Asociación nominal o explícita*, en la cual se especifica el nombre del puerto asociado a la señal, de la forma: puerto => señal.

Ej: Multiplexor de 2 señales de 1 bit
![](img/Pasted%20image%2020250317175553.png)
```vhdl
-- MUX 2:1 de 1 bit 
-- fichero: mux2_1bit.vhd 
library IEEE; use IEEE.std_logic_1164.all; 
entity Mux2_1bit is
	port ( d         :  out std_logic;
			i0,i1    :  in  std_logic;
			s0       :  in  std_logic);
end entity Mux2_1bit;

architecture Mux2_1bit of Mux2_1bit is
	component not1 is
		port (y0     :  out std_logic;
			  x0     :  in  std_logic);
	end component not1;
	component or2 is
		port (y0     :  out std_logic;
			  x0, x1 :  in std_logic);
	end component or2;
	component and2 is
		port (y0     :  out std_logic;
			  x0, x1 :  in std_logic);
	end component and2;
	signal n1, n2, n3 : std_logic;
begin
	Inv_1  : not1  port map ( x0 => s0, y0 => n1); 
	And2_1 : and2 port map ( xO => iO, x1 => n1, yO => n2); 
	And2_2 : and2 port map ( xO => i1, x1 => sO, yO => n3); 
	Or2_1 : or2 port map ( xO => n2, x1 => n3, yO => d);)
end architecture Mux2_1bit;
```
### 2.9.1. Diseños con estructura regular
El uso de la sentencia **generate** condicional resulta particularmente útil para realizar las conexiones de los elementos extremos de una estructura repetitiva.
Ej: Detector de paridad de 8 bits
```vhdl
library IEEE;
use IEEE.std_logic_1164.all;

entity paridad is 
port (  parity        : out std_logic; 
		parity_IN     : in std_logic_vector(7 downto 0));
end entity paridad; 

architecture paridad of paridad is

	signal temp: std_logic_vector(6 downto 0);
	
	component xor2 is
		port ( yO       : out std_logic;
				xO, x1 : in std_logic ); 
	end component xor2; 
	
begin
	parity <= temp(6);
	gen_array: for I in 0 to 6 generate
		
		inicial: if I = 0 generate
			xor_O: xor2 
					port map (temp(0), parity_IN(0), parity_IN(1)); 
		end generate inicial; 
		
		intermedio: if I /= O generate
			resto_xor: xor2 
					port map (temp(I), temp(I-1), parity_IN(I+1)); 
		end generate intermedio; 
		
	end generate gen_array; 

end architecture paridad;
```
La primera sentencia **generate** condicional, que tiene la etiqueta inicial, se ejecuta sólo cuando el índice I del bucle es igual a 0. En el cuerpo de este **generate** condicional está la instanciación de la puerta xor_0.
La segunda sentencia **generate** condicional, que tiene la etiqueta intermedio, se ejecuta cuando el índice I del bucle es distinto de 0. En el cuerpo de esta sentencia están las instanciaciones del resto de puertas XOR de dos entradas. Las asociaciones de los puertos de entrada y salida dependen del índice I del bucle.
## 2.10. PARAMETRIZACIÓN
La *parametrización* es una propiedad fundamental en la reutilización del código, ya que permite adaptar un mismo fragmento de código a diferentes usos. En la Sección 2.3.2 se explicó cómo pueden declararse constantes **generic** al declarar una **entity**. El valor de estas constantes **generic** puede ser usado en la **architecture** asociada a la **entity**. Esto permite parametrizar tanto la descripción del comportamiento como la descripción de la estructura.
### 2.10.1. Parametrización del comportamiento
En la Sección 2.3.2 se mostró la siguiente entity de una puerta AND: 
```vhdl
entity and2 is 
	generic ( Tpd    :   time); 
	port    ( yO     :   out std_logic; 
			  xO, xl :   in std_logic ); 
end entity and2;
```
La constante **generic** Tpd especifica el retardo de propagación del módulo. Su valor es usado en la sentencia que define el comportamiento de la puerta:
```vhdl
architecture and2D of and2 is 
begin 
	yO <= xO and x1 after Tpd;
end architecture and2D;
```
### 2.10.2. Parametrización de la estructura
Cuando se instancia un componente, puede asignarse valor a sus constantes **generic**. Esto permite adaptar la instancia del componente a la aplicación en concreto a la que vaya a destinarse al formar parte del circuito de nivel jerárquico superior. Sintaxis:
```vhdl
nombre instancia  :  component nombre_componente 
					 generic map ( valores_constantes_generic ) 
					 port map ( asociación_puertos_señales );
```
Por ejemplo, podría asignarse el valor 3 ns a la constante **generic** Tpd, al instanciar un componente and2 llamado puertaAND1, de la forma siguiente:
```vhdl
puertaAND1   :   component and2 
				 generic map eTpd => 3ns) port map e yO=> sig_out, xO =>sigO, x1 => sig1);
```
## 2.11. SENALES, VARIABLES Y CONSTANTES
- Las señales corresponden con las señales lógicas reales existentes en el circuito. Se emplean señales para representar datos a los que deba asignarse valor fuera de los bloques secuenciales (**process**, **function** y **procedure**), y datos que necesitan ser transferidos desde un puerto de entrada o a un puerto de salida. Los puertos sólo pueden ser señales. 
- Las variables pueden o no corresponder con señales físicas reales. Dos ejemplos típicos de uso de las variables son los siguientes:
	- Cuando hace falta realizar una serie de cálculos para poder asignarle valor a una señal, se definen nuevas variables, se hacen los cálculos usando esas variables, y finalmente se asigna el resultado de los cálculos a la señal. 
	- Puesto que una señal de salida (un puerto cuyo modo es **out**) no puede ser leída, puede ser necesario definir una variable, leer y escribir sobre esa variable tantas veces como sea necesario, y finalmente asignar esa variable a la señal de salida.
- Las constantes corresponden a magnitudes cuyo valor no cambia durante la simulación (típicamente retardos, número de líneas de buses, número de bits de palabras, etc.)

==Constantes y señales pueden ser declaradas en un **package**, **entity** o **architecture** (en la parte dedicada a las declaraciones), mientras que las variables sólo pueden ser declaradas y únicamente son visibles dentro de bloques de código secuencial (**process**, **function** y **procedure**). Las señales no pueden ser declaradas dentro de bloques de código secuencial.==
Sintaxis:
```vhdl
signal nombre_señal        : tipo_dato := valor_inicial;
variable nombre_variable   : tipo_dato := valor_inicial;
constant nombre_constante  : tipo_dato := expresión;
```
---

Respecto a la asignación de valor a las variables, señales y constantes:
- Para **asignar valor a una variable** se emplea : =. La sintaxis es: 
```vhdl
nombre_variable := expresión; 
```
Sólo puede asignarse valor a las variables en sentencias incluidas dentro de los bloques de código secuencial. La asignación a la variable del nuevo valor se realiza inmediatamente. Es decir, sin ningún retardo. 
- Para **asignar valor a una señal** se emplea <=. La sintaxis es: 
```vhdl
nombre_señal <= forma_de_onda;
```
Las sentencias de asignación a señal pueden ser tanto asignaciones concurrentes, como asignaciones secuenciales (aquellas situadas dentro de los bloques de código secuencial). En ambos casos, salvo que se indique explícitamente el retardo, se asigna a la señal el nuevo valor una vez transcurrido un retardo $\delta$

Debe tenerse en cuenta que las señales definidas en el **port** de una **entity** tienen una dirección, lo cual condiciona su uso: no puede leerse el valor de una señal de salida (**out**), ni asignarse un valor a una señal de entrada (**in**).
Las señales declaradas en la definición de la **architecture** puede ser usadas tanto en la parte derecha como en la izquierda de las asignaciones.

Las sentencias de definición de constantes pueden situarse en las unidades de diseño **entity** y **architecture**, antes de la palabra reservada **begin**. También pueden definirse constantes dentro de la definición de un **package**.
## 2.12. TIPOS DE DATOS Y OPERADORES
Un tipo de dato en VHDL está definido por los dos conjuntos siguientes: el conjunto de valores que puede tomar el objeto y el conjunto de operaciones que pueden realizarse sobre los objetos de ese tipo de dato.

Se dice que VHDL es un lenguaje "*fuertemente tipado*". Esto significa que a un objeto sólo puede asignársele un valor de su tipo y que sólo pueden realizarse sobre el objeto las operaciones definidas para su tipo de dato. Para asignar a un objeto un valor de un tipo diferente, previamente debe convertirse el valor al tipo de dato del objeto, usando para ello una *función de conversión del tipo*.

En VHDL se emplean tipos de datos para modelar las señales, variables y constantes. Estos tipos de datos pueden ser los estándar de VHDL o bien tipos definidos por el programador. Los tipos de datos más comúnmente usados para las señales son los tipos estándar **std_logic, std_logic_vector, signed y unsigned**. El programador puede definir sus propios tipos de datos, bien como un subconjunto de los tipos de datos estándar, o bien puede definir sus propios *tipos enumerados*.
### 2.12.1. Tipos predefinidos en VHDL
- integer
	- natural: incluye el cero y los números positivos.
	- positive: solo números positivos.
- boolean
- bit
- bit_vector: vector unidimensional de elementos del tipo bit.
Los literales de vectores de bits se escriben entre comillas dobles y opcionalmente precedidos por una letra que indica la base en la cual están expresados: B (binario), o (octal) y X (hexadecimal). Si no se especifica la base, el vector se interpreta como binario.
Un guión bajo insertado entre dígitos adyacentes no altera el valor, pero hace que las cadenas sean más fácilmente legibles para el programador.
#### Operadores
![](img/Pasted%20image%2020250324181137.png)

Precedencia de los operadores:
![](img/Pasted%20image%2020250324181341.png)

Si una expresión consta de varios operadores con la misma precedencia, entonces comienza a evaluarse el operador situado más a la izquierda en la expresión y se progresa avanzado hacia la derecha.
Es importante tener en cuenta que, al contrario de lo que sucede en álgebra booleana, los operadores **and** y **or** tienen la misma precedencia en VHD L y, por tanto, deben usarse paréntesis para indicar el orden en que deben realizarse las operaciones lógicas.
### 2.12.2. Tipos del paquete IEEE.std_logic_1164
Con el fin de reflejar mejor las propiedades del hardware digital, en el estándar IEEE 1164 se introdujeron nuevos tipos de datos, que extendían los tipos **bit** y **bit_vector**.
Estos nuevos tipos de datos fueron definidos en el paquete IEEE. std_logic_1164. Entre estos nuevos tipos, sin duda los más ampliamente usados son **std_logic** y **std_logic_vector**.

Para poder usar en los diseños estos tipos de dato, es necesario especificar que se desea usar el paquete IEEE. std_logic_1164.
```vhdl
library IEEE; 
use IEEE.std_logic_1164.all;
```
#### std_logic
El tipo **std_logic** es más versátil que bit, ya que aparte de los valores '0' y ' 1 ' , puede tomar otros siete valores. De estos valores, los más comunes son los tres siguientes:
- '**U**' El valor de la señal está sin inicializar. Es decir, aún no se ha asignado valor a la señal.
- '**X**' No puede determinarse el valor de la señal. 
- '**Z**' Alta impedancia. El valor indica que la señal ha quedado desconectada. Los buffers triestado proporcionan una salida con este valor.
Los restantes posibles valores de una señal del tipo std_logic son: 
- 'W' ( desconocida débil) 
- 'L' (cero débil)
- 'H' (uno débil): Junto con 'L', indica que la señal es obtenida de circuitos de lógica cableada, en los cuales la corriente es débil.
- '-' (don't care): ) Se usa para facilitar el diseño lógico. Cuando don't care se usa como valor de salida, indica que el valor exacto ('0' ó '1 ') no es importante
Algunos comentarios respecto a la interpretación que hacen las herramientas de síntesis de los valores del tipo std_logic: 
- Los valores '0' y 'L' son interpretados como O lógico. 
- Los valores '1' y 'H' son interpretados como 1 lógico. 
- El valor 'Z' es interpretado como alta impedancia. 
- Los valores '-'y 'X' son interpretados como *don't care*. 
- Algunas herramientas de síntesis no aceptan los valores 'U' y 'W' . Por el contrario, otras interpretan 'W' como *don't care*.
#### std_logic_ vector
El tipo de dato std_logic_vector es un vector de elementos del tipo std_logic.
Ej:
```vhdl
signal a: std_logic_vector ( 7 downto O);
```
La señal tiene 8 bits, que están indexados desde 7 hasta O. El bits más significativo, es decir, el situado más a la izquierda, tiene el índice 7.
Es posible acceder a uno de los bits usando su índice. 
Ej: a(2). 
También, es posible acceder a una conjunto de bits especificando su rango. 
Ej: a(7 downto 2),

Otra forma de std_logic_ vector es usando un rango ascendente:
```vhdl
signal a: std_logic_vector (Oto 7 );
```
En este caso, el bit más significativo (situado más a la izquierda) tiene el índice 0, lo cual puede inducir a error si el bus o vector es interpretado como un número binario.

entidad igual mismo banco de pruebas, distinta arquitectura
de programacion funcional a programacion estructural, si eran cuatro ahora ponemos seis, crear los componentes y meterlos a mano
#### Operadores
En VHDL pueden emplearse funciones con el mismo nombre para operados de distinto tipo. Es decir, pueden definirse varias funciones con el mismo nombre, cada una para un tipo diferente de dato. Esto se denomina *sobrecarga de los operadores*.
En el paquete IEEE. std_logic_1164 se han sobrecargado todos los operadores lógicos (**and, or, nand, nor, xor, xnor**) para **std_logic** y **std_logic_vector**. Obsérvese que en el paquete `IEEE.std_logic_1164` no se han sobrecargado las operaciones aritméticas y por tanto estas operaciones no pueden aplicarse a estos tipos de datos.
#### Conversión de tipos
En el paquete IEEE. std_logic_1164 se han definido las funciones para la conversión entre los tipos **bit** y **std_logic**, así como entre los tipos **bit_vector** y **std_logic_vector**.
![](img/Pasted%20image%2020250324183559.png)

### 2.12.3. Operadores sobre bit_vector y std_logic_vector
Algunas operaciones, tales como la concatenación, las operaciones relacionales y la agregación, están definidas sobre los tipos **bit_vector** y **std_logic_vector**.
#### Operadores relacionales
Los operadores relacionales (=, /=, <, <=, >, >=) pueden ser empleados para comparar dos datos de tipo vector. Los dos operandos deben tener el mismo tipo de elementos, pero sus longitudes pueden ser diferentes.
Cuando se aplica el operador, los dos vectores son comparados elemento a elemento. La comparación comienza por el elemento situado más a la izquierda y continúa hasta que puede establecerse cuál es el resultado. Si se alcanza el final de un vector antes que el final del otro, entonces se considera que el primer vector (el de menor longitud) es menor que el segundo, y por tanto, se considera que los dos vectores no son iguales.
#### Operador concatenación
El operador de concatenación, &, permite concatenar elementos, segmentos de vectores y vectores completos, para formar vectores de mayor longitud.
Ej: desplazar los elementos del vector a dos posiciones hacia la derecha e insertar dos bits 'O' por la izquierda.
```vhdl
y<= "00" & a( 7 downto 2 );
```
#### Agregación de vectores
La agregación no es un operador, sino una construcción que permite asignar valor a vectores. La forma más sencilla de expresar una agregación es usar una colección de valores escritos entre comillas dobles.
Ej: 
```vhdl
x1 <= "101111";  -- Representación binaria del decimal 47 
x2 <= 0"57";     -- Representación octal del decimal 47
x3 <= H"2F";     -- Representación hexadecimal del decimal 47
```
Otra posibilidad es especificar la lista de valores, cada uno en su correspondiente posición. Este tipo de agregación se denomina agregación mediante *asociación posicional*. La asignación:
```vhdl
y<= "10101010";
```
es equivalente a:
```vhdl
y <= ('1','0','1','0', '1','0','1','0') ;
```
También, puede emplearse la forma 
índice => valor
para especificar de manera explícita el valor para cada índice. Esta forma de agregación se denomina *asociación mediante nombre*. La sentencia anterior puede escribirse de la forma siguiente:
```vhdl
y <= ( 7 => '1', 6 => '0', 5 => '1', 4 => '0', 3 => '1', 2 => '0', 1 => '1',  0 => '0' ) ;
```
o equivalentemente, con las asociaciones en un orden cualquiera.
También, es posible combinar los índices, como por ejemplo en:
```vhdl
y <= ( 7 | 5 | 3 | 1 => '1',
	   6 | 4 | 2 | 0 => '0' ) ;
```
o bien, emplear la palabra reservada **others** para referirse a todos los índices que no han sido nombrados.
```vhdl
y <= ( 7 | 5 | 3 | 1 => '1',
	   others        => '0' ) ;
```
También puede emplearse la palabra reservada others para asignar el mismo valor a todos los componentes de un vector.
```vhdl
y <= ( others => '0' );
```
Este tipo de sentencia tiene la ventaja de que es independiente del número de componentes que tenga la señal.
### 2.12.4. Tipos del paquete IEEE.numeric_std
Como hemos visto anteriormente, no pueden realizarse operaciones aritméticas sobre los datos de los tipos **bit_vector** y **std_logic_vector**.
Sí pueden realizarse operaciones aritméticas sobre los datos del tipo **integer**. Por ejemplo, para realizar la suma de las señales a y b, puede emplearse el tipo **integer**:
```vhdl
signal a, b, suma : integer; 
suma <= a + b;
```
Una alternativa mucho más adecuada desde el punto de vista de la síntesis es usar un vector de ceros y unos, e interpretarlo como un número binario con signo o sin signo. De esta manera, quedan definidas de manera precisa la anchura de los operandos y el tamaño del circuito sumador, con lo cual se obtiene un mejor control sobre el hardware resultante de la síntesis. El paquete `IEEE.numeric_std` fue desarrollado con este propósito.
#### unsigned y signed
Son vectores de elementos del tipo **std_logic**:
- Para el tipo de dato **unsigned**, el vector se interpreta como un número binario sin signo, donde el elemento situado más a la izquierda es el bit más significativo del número binario.
- Para el tipo de dato **signed**, se interpreta el vector como un número binario con signo, en el formato de complemento a 2. El elemento situado más a la izquierda es el bit más significativo del número binario, que representa el signo del número.
Obsérvese que los tres tipos de dato **std_logic_vector**, **unsigned** y **signed** están definidos como vectores de elementos del tipo **std_logic**. Puesto que VHDL es un lenguaje *fuertemente tipado*, estos tres tipos son considerados como tipos de datos independientes.
Ej:
Vector de 4 bits: "1100"

| unsigned | signed | std_logic_vector               |
| -------- | ------ | ------------------------------ |
| 12       | -4     | 4 bits independientes entre sí |
Puesto que los tipos de dato **unsigned** y **signed** son vectores, sus declaraciones son similares a las del tipo **std_logic_vector**.
Ej:
```vhdl
signal a: signed ( 15 downto O);
```
Para poder usar los tipos de dato **unsigned** y **signed**, debe incluirse la sentencia especificando que va a usarse el paquete ``IEEE.numerie_std``. Asimismo, puesto que el paquete ``IEEE.numeric_std`` emplea el tipo de dato **std_logic**, debe indicarse que va a usarse el paquete ``IEEE. std_logic_1164``.
#### Operadores
En este paquete se sobrecargan todos los operadores aritméticos: ``abs, *, 1, mod, rem, + ``y` - .
==La definición de los operadores suma y resta sigue el modelo de un sumador físico. Es decir, cuando se produce rebosamiento, el resultado de la suma es como un contador que puede dar tantas vueltas como sea preciso.==
Los operadores relacionales ( =, !=, <, <=, >, >=) han sido sobrecargados. Los operadores relacionales aplicados a datos del tipo **unsigned** o **signed** no comparan los componentes del vector elemento a elemento, sino que interpretan los vectores como números binarios.
Ej: 
"011" > "1000"

| std_logic_vector | unsigned | signed |
| ---------------- | -------- | ------ |
| *false*          | *false*  | *true* |
| 001 < 1000       | 3 < 8    | 3 > -8 |
#### Funciones
Se definen algunas funciones nuevas:
- ``shift_left (a, b)``, shift_right (a, b), rotate_left (a, b), rotate_right (a, b): se emplean para realizar las operaciones de desplazamiento y rotación. El operando a es de tipo unsigned o signed, mientras que bes de tipo natural. El resultado es del mismo tipo que el operando a.
- ``resize (a, b)``: se emplea para modificar el tamaño (es decir, el número de bits) del operando a, que debe ser del tipo unsigned y signed. El operando b es de tipo natural y representa el nuevo número de bits del dato. El resultado es del mismo tipo que el operando a. 
- ``std_match(a, b)``: se emplea para comparar vectores que tienen el valor'-' ( don't care). El operando a debe ser del tipo **unsigned**, **signed std_logic_vector** o **std_logic**. El operando b debe ser del mismo tipo que a. El resultado es del tipo **boolean**.
#### Conversión entre tipos
Hay tres funciones de conversión entre tipos en el paquete ``IEEE.numeric_std``. Estas son: ``to_unsigned``, ``to_signed`` y ``to_integer``.
![](img/Pasted%20image%2020250416165415.png)
- La función ``to_integer`` tiene como parámetro un objeto del tipo **unsigned** o **signed** y devuelve un objeto del tipo **integer**.
- Las funciones ``to_unsigned`` y ``to_signed`` convierten un **integer** en un objeto del tipo **unsigned** y **signed**, respectivamente, con el número de bits especificado. Estas funciones tienen dos parámetros. El primero es el número del tipo **integer** que se desea convertir. El segundo es el número deseado de bits del nuevo tipo de dato.
Los tipos **std_logic_vector**, **unsigned** y **signed** están definidos como un vector de elementos **std_logic**. Se trata de tipos de datos muy próximos entre sí, que pueden convertirse entre sí escribiendo el objeto original entre paréntesis, delante del cual debe escribirse el nuevo tipo de dato. Este tipo de conversión se denomina *casting*.
Ej:
```vhdl
signal u1, u2 unsigned         ( 7 downto 0 );
signal x1, x2 std_logic_vector ( 7 downto 0 );
u1 <= unsigned( x1 ); 
x2 <= std_logic_vector( u2 );
```
El tipo **std_logic_vector** no es interpretado como un número. Por ello, este tipo no puede ser convertido directamente a **integer** o viceversa.
Ej:
```vhdl
signal si, s2, s3, s4, s5, s6              : std_logic_vector  ( 3 downto O); 
signal u1, u2, u3, u4, u5, u6, u7          : unsigned          ( 3 downto O); 
signal sg                                  : signed            ( 3 downto O);

...

u5 <= sg; -- Error
u4 <= 5;  -- Error
```
Para poder realizar las asignaciones anteriores, es necesario realizar la conversión entre los tipos:
```vhdl
u5 <= unsigned( sg );      -- Bien, casting 
u4 <= to_unsigned( 5,4 );  -- Bien, función de conversión
```
No es posible realizar operaciones aritméticas sobre objetos del tipo **std_logic_vector**. Así pues, las siguientes sentencias no son válidas: 
```vhdl
s5 <= s2 + si; -- Error, operador + indefinido 
s6 <= s2 + 1;  -- Error, operador + indefinido 
```
Para solucionar el problema, es preciso convertir los operandos al tipo **unsigned** o **signed**, realizar la suma, y a continuación convertir el resultado al tipo **std_logic_vector**. 
```vhdl
s5 <= std_logic_vector( unsigned(s2) + unsigned(s1) ); -- Bien
s6 <= std_logic_vector( unsigned(s2) + 1 );            -- Bien
```
### 2.12.5. Tipos time y string
Los tipos de datos **time** y **string** son útiles, en el proceso de depuración del modelo, para mostrar mensajes que son generados durante la simulación.
Las variables del tipo **time** son usadas para representar el tiempo simulado. La unidad por defecto de este tipo de variables es el **fs** (femtosegundo = $10^{-15} s$). Los valores del tiempo pueden representarse en otras unidades escribiendo la unidad de tiempo tras el valor del tiempo, el cual es escrito como una constante entera o real. Las unidades de tiempo disponibles son: **fs, ps, ns, us** (microsegundos), **ms, sec, min y hr** (horas).
Para mostrar mensajes de texto y valores de datos en la pantalla, es preciso convertir todos los argumentos de la sentencia **report** (la sentencia "print" de VHDL) a tipos de dato **string**.
### 2.12.6. Tipos definidos por el usuario
#### Tipos enteros definidos por el usuario
Puede definirse un tipo de datos especificando un determinado rango de valores de los números enteros. Ej:
```vhdl
type miEntero       is range -32 to 32; 
type palabraMemoria is range 0 to 1024;
```
#### Tipos enumerados
supongamos una señal llamada ``opcode``, que representa el código de operación de un circuito. Suponiendo que sólo puede tomar cuatro valores (suma, resta, salto y parar), entonces es posible definir un nuevo tipo ( **type**), llamado, por ejemplo, ``opcode_type``, de la manera siguiente:
```vhdl
type opcode_type is (SUMA, RESTA, SALTO, PARAR);
```
U na forma alternativa de programar el ejemplo anterior es definir ``SUMA``, ``RESTA``, ``SALTO`` y ``PARAR`` como constantes ( **constant**) de dos bits, y definir opcode como una señal que sea un vector de dos bits.
#### Tipos vectoriales definidos por el usuario
VHDL permite al usuario definir sus propios tipos vectoriales. Por ejemplo, vectores 1D en los cuales los componentes sean a su vez de tipo vectorial 1D, por ejemplo **std_logic_vector**. Estos vectores unidimensionales, cuyos componentes son a su vez vectores unidimensionales, se denominan vectores 1D x 1D.
En general, puede declararse un nuevo tipo vectorial empleando la sintaxis mostrada a continuación:
```vhdl
type nombre_ tipo is array especificacion_dimension of tipo_dato;
```
Supongamos que se quiere definir un nuevo tipo vectorial 1D x 1D, que sea un vector de 4 componentes, donde cada uno de los componentes sea a su vez un vector de 8 componentes del tipo **std_logic**. El nuevo tipo, al que se asigna el nombre ``regFile_type``, puede declararse de la forma siguiente:
```vhdl
type regFile_type is array (Oto 3) of std_logic_vector(7 downto O);
```
Puede declararse una constante y una señal de este tipo, a las cuales se asignan los nombres ``data`` y ``reg_file`` respectivamente, y asignar valor a la constante, de la forma mostrada a continuación:

```vhdl
constant data : regFile_type := 
			( ( '0', '0', '1', '1', '0', '0', '0', '0' ) , 
			  ( '1', '0', '1', '0', '1', '0', '1', '1' ) , 
			  ( '0', '1', '0', '1', '0', '0', '1', '0' ) ,
			  ( '1', '0', '1', '0', '0', '1', '0', '0' ) ) ; signal reg_file : regFile_type;
```
Para referirse a los elementos de los objetos de tipo vectorial 1D x 1D, se emplean dos pares de paréntesis. Por ejemplo, ``reg_file(2)(3)``.

El siguiente ejemplo muestra la declaración de un tipo vectorial bidimensional, llamado ``matriz2D``, y de una constante y una señal de ese tipo.
```vhdl
type matriz2D is array (0 to 3, 7 downto 0) of std_logic; constant data : matriz2D := 
			( ( '0', '0', '1', '1', '0', '0', '0', '0' ) , 
			  ( '1', '0', '1', '0', '1', '0', '1', '1' ) , 
			  ( '0', '1', '0', '1', '0', '0', '1', '0' ) ,
			  ( '1', '0', '1', '0', '0', '1', '0', '0' ) ) ;
signal mem_data : matriz2D;
```
Para referirse a los elementos de los objetos de tipo vectorial 2D, se emplea un único par de paréntesis. Por ejemplo, ``mem_data(2, 3)``.
## 2.13. ATRIBUTOS
Puede considerarse que los atributos son propiedades de los tipos de datos. En la tabla se muestran algunos de los atributos que son soportados por la mayoría de las herramientas de síntesis.
![](img/Pasted%20image%2020250416173046.png)VHDL permite al usuario definir sus propios atributos.
Ej, dada la señal:
```vhdl
signal d : std_logic_vector( 7 downto 0);
```
los valores de sus atributos son:
```vhdl
d'low=0         d'high=7              d'left=7        d'right=0 
d'length=0      d'range=(7 downto 0)  d'reverse_range=(0 to 7)
```
Asimismo, existen atributos que resultan útiles para programar bancos de prueba y que, por tanto, no necesitan ser sintetizados. Un atributo particularmente útil es 
```vhdl
<tipo>'image(señal)
```
el cual se usa para convertir el valor de una señal a un string, de modo que pueda ser mostrado en la consola (con el fin de depurar o monitorizar).
## 2.14. LIBRERÍAS
A excepción de los tipos **bit** y **bit_vector**, todos los demás tipos precisan de la inclusión de alguna librería de diseño.
VHDL permite organizar las librerías, estructurando su contenido en sub-librerías denominadas **packages**.
Por este motivo, además de especificar qué librerías deben ser incluidas, conviene que el diseñador indique qué paquetes en concreto de la librería son usados en la definición del circuito. Si no se especifica el paquete, o si un mismo objeto está definido en varios paquetes, es preciso referirse a él usando la notación punto:
```vhdl
librería.paquete.objeto
```
Entre los paquetes más comúnmente usados, cabe mencionar los siguientes, pertenecientes a la librería IEEE:

| IEEE. std_logic_1164                                                                                                                                | IEEE. numeric_std                                                                                                                              | IEEE.math_real                                                                                                                                                                  |
| --------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Incluye la definición de los tipos de datos **std_logic** y **std_logic_vector**, y de las operaciones en las que intervienen estos tipos de datos. | Incluye la definición de los tipos de datos **unsigned** y **signed**, y de las operaciones más comunes realizadas sobre estos tipos de datos. | Incluye la definición de las operaciones en las que intervienen números reales (tipo **real**). Estos son números reales en coma flotante de 64 bits según el estándar de IEEE. |
```vhdl
library IEEE; 
use IEEE.std_logic_1164.all; 
use IEEE.numeric_std.all;
```
La primera sentencia indica que va a emplearse la librería de IEEE. Las otras dos indican que los paquetes IEEE.stcLlogic_ll64 y IEEE.numeric_std deben estar listos para su uso en el código VHDL que sigue a continuación.
Existen librerías y paquetes que son cargados por defecto, con lo cual no necesitan ser incluidas. Las más notables son las dos siguientes:

| work                                                                                                                                             | std                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------- |
| Librería por defecto donde se compilan todos los tipos, las funciones, **entity**, **architecture**, **package**, etc. definidos por el usuario. | Contiene la mayoría de las definiciones y construcciones estándar soportadas por VHDL. |
## 2.15. ASSERT
La sentencia assert se usa para hacer comprobaciones de condiciones lógicas que, dado el valor esperado en ese punto del estado del programa, deberían valer true. Se emplea frecuentemente para depurar el código al simularlo, siendo ignorada por las herramientas de síntesis.
```vhdl
assert condición_booleana report mensaje_a_mostrar 
						  severity nivel_severity;
```
Mientras la condición booleana vale *true*, la sentencia no realiza ninguna acción. Cuando la condición se hace *false*, la sentencia muestra el texto ``mensaje_a_mostrar`` en la consola. 
La cláusula **severity** se usa para indicar qué gravedad tiene la violación de la condición booleana. Posibles valores de ``nivel_severity`` son:

| note           | warning | error | failure                                           |
| -------------- | ------- | ----- | ------------------------------------------------- |
| No es un error | Aviso   | Error | Error grave que provoca que termine la simulación |
## 2.16. SUBPROGRAMAS
Hay dos tipos de subprogramas: las funciones y los procedimientos.
Lo subprogramas (funciones y procedimientos) pueden ser definidos dentro de paquetes (**package**), de modo que sean fácilmente reutilizados en diferentes proyectos, o en el propio código principal del diseño. En este último caso, los subprogramas deben ser definidos dentro de la sección de declaración de la **entity**, **architecture** o de los bloques **process**.
### 2.16.1. Funciones
Una función es una rutina que devuelve un valor. La función puede ser invocada desde sentencias concurrentes y secuenciales. Al realizar la llamada o invocación a la función, se especifican los *parámetros actuales*, que son asociados a los *parámetros formales* usados en la definición de la función.
En la definición de la función pueden emplearse las sentencias propias del *código secuencial* (**if, case, for, assert**, etc.), salvo la sentencia **wait**, que no puede emplearse en la definición de la función. Por otra parte, dentro de una función no pueden declararse señales o instanciarse componentes. Se emplea la sentencia **return** para especificar qué valor devuelve la función. La *declaración* de la función sigue la sintaxis siguiente:
```vhdl
function nombre_función lista_param_formales return tipo_dato is 
	declaracion de variables locales y constantes locales 
begin 
	sentencias secuenciales 
end function nombre_función;
```
donde ``lista_param_formales`` especifica los *parámetros formales* de entrada a la función, que pueden ser constantes y señales, pero no variables. La función puede tener un número cualquiera de *parámetros formales* (inclusive ninguno). La lista de *parámetros formales* se escribe entre paréntesis. La sintaxis para declarar un *parámetro formal* es:
```vhdl
constant nombre_constante : tipo_dato;
```
si se trata de una constante, donde la palabra reservada **constant** es opcional, o bien
```vhdl
signal nombre_señal : tipo_dato;
```
si se trata de una señal. El tipo del *parámetro formal* puede ser cualquiera de los tipos sintetizables, **boolean, std_logic, integer**, etc.
Cuando se declaran *parámetros formales* vectoriales o enteros, no debe especificarse su rango. Por ejemplo, no hay que especificar el **range** en el caso de los parámetros **integer**, ni **to / downto** para los parámetros **std_logic_vector**. Esto facilita la reutilización de la función en diferentes contextos.
La función devuelve un único valor, cuyo tipo debe especificarse al declarar la función.
Ej:
```vhdl
function f ( c1, c2   : integer;
			signal s  : std_logic_vector) return boolean is
...			
end function f;
```
recibe tres parámetros formales: las **constant** c1 y c2, de tipo **integer**, y la **signal** s, de tipo **std_logic_vector**. El valor que devuelve la función es de tipo **boolean**.
### 2.16.2. Procedimientos
El procedimiento es más versátil que la función, ya que puede devolver más de un valor. Los procedimientos pueden declararse en la parte declarativa de las **architecture** y de los bloques **process**, y también, como se explicará más adelante, dentro de paquetes (**package**). La sintaxis para la declaración de un procedimiento es la siguiente:
```vhdl
procedure nombre_procedimiento lista_param_formales is 
	declaracion de variables locales y constantes locales 
begin 
	sentencias secuenciales 
end procedure nombre_procedimiento;
```
En este caso, en la lista de *parámetros formales* no sólo se especifican los parámetros formales de entrada, sino ==también los parámetros formales de salida.== Es decir, aquellos que son calculados en el procedimiento.
Los parámetros formales de un procedimiento pueden ser **constantes**, **variables** y **señales**. La sintaxis para declarar cada parámetro formal en la lista de parámetros, según se trate de una constante, una señal o una variable, es la siguiente:
```vhdl
constant  nombre_constante : modo tipo_dato;
signal    nombre_señal     : modo tipo_dato;
variable  nombre_variable  : modo tipo_dato;
```
(IMPORTANTE)
El modo del parámetro formal condiciona su uso en el procedimiento:
- Puede modificarse en el procedimiento el valor de los parámetros formales declarados como **out** o **inout**, pero no el valor de los parámetros formales declarados como **in**. 
- Puede leerse en el procedimiento el valor de los parámetros formales declarados como **in** o **inout**, pero no puede leerse dentro del procedimiento el valor de los parámetros formales declarados como **out**. 
- Si no se especifica la dirección de un parámetro formal del procedimiento, se asume por defecto que es **in**. 
- Un parámetro formal **out** o **inout** es por defecto una *variable*, a menos que se indique explícitamente que es una señal. 
- Se considera que un parámetro **in** es una *constante* dentro del bloque del procedimiento. No obstante, si el parámetro **in** es una señal, entonces los cambios que se produzcan en la señal fuera del procedimiento se producirán igualmente en el valor de la señal dentro del procedimiento.

La invocación del procedimiento es una sentencia por sí misma, que puede formar parte de código concurrente o secuencial. 
- Cuando el procedimiento es invocado fuera de un bloque de código secuencial, entonces la invocación es una sentencia concurrente. Esta sentencia concurrente es equivalente a un bloque **process** que contuviera la llamada al procedimiento, seguida de una sentencia **wait on** cuya lista de sensibilidad contuviera todos los parámetros del procedimiento que son señales con modo **in** e **inout**. Los procedimientos invocados en sentencias concurrentes no pueden tener parámetros formales variable. 
- Cuando el procedimiento es invocado en un fragmento de código secuencial, por ejemplo, dentro de un bloque **process**, entonces no existe un **wait** implícito al final del procedimiento. Esto significa que, una vez ejecutada la última sentencia del procedimiento, se ejecuta la sentencia secuencial siguiente a la de invocación del procedimiento.

Los *parámetros actuales* de la invocación al procedimiento se hacen corresponden con los *parámetros formales* del procedimiento, bien por asociación posicional o bien mediante la sintaxis 
``param_formal => param_actual``
Al igual que se indicó en el caso de las funciones, ==cuando se declaran parámetros formales vectoriales o enteros, no debe especificarse su rango. Su rango será el de los parámetros actuales con los cuales se asocian al realizar la invocación al procedimiento.==

Ej: Procedimiento que devuelve dos parámetros de entrada ordenados:
```vhdl
library IEEE; 
use IEEE.std_logic_1164.all; 

entity minMax is 
	generic ( limite : integer : = 255 ); 
	port ( min_out, max_out : out integer range O to limite; 
		ena          : in std_logic; 
		d1_in, d2_in : in integer range O to limite ); 
end entity minMax; 

architecture minMax of minMax is 
	procedure ordena ( signal in1, in2 : in integer range O to limite; 
					   signal min, max : out integer range O to limite ) is 
		begin 
			if (in1>in2) then 
				max <= in1; 
				min <= in2; 
			else 
				max <= in2; 
				min <= in1; 
			end if; 
	end procedure ordena; 
		
begin 
	process (ena) 
	begin
		if (ena= ' 1 ' ) then 
			ordena(d1_in, d2_in, min_out, max_out); 
		end if; 
	end process; 
	
end architecture minMax;
```
### 2.16.3. Diferencias entre funciones y procedimientos
- Una función tiene cero o más parámetros formales de entrada, y devuelve un único valor. Los parámetros de entrada sólo pueden ser **constant** (por defecto) o **signal**. No se permiten parámetros **variable**. Los parámetros formales de las funciones siempre tienen el modo **in**, por ello no debe especificar su modo. 
- Un procedimiento puede tener cualquier número de parámetros **in**, **out** e **inout**, los cuales pueden ser **constant**, **signal** y **variable** (sólo cuando se llama al procedimiento desde código secuencial). Los parámetros de entrada (modo **in**) se consideran por defecto **constant**, mientras que los de salida (modos **out** e **inout**) se consideran por defecto **variable**.
- Una función es invocada como parte de una sentencia, mientras que la invocación a un procedimiento es una sentencia en sí misma. 
- En los procedimientos puede usarse la sentencia **wait**, en las funciones no. En todo caso, la sentencia **wait** no es sintetizable.
- La declaración de funciones y procedimientos puede realizarse o bien dentro de **packages**, con lo cual se facilita su reutilización desde diferentes diseños, o bien en el código principal del diseño (en la parte declarativa de la **entity**, de la **architecture** o de un bloque **process**).
## 2.17. PAQUETES
Como se ha explicado anteriormente, los fragmentos de código secuencial pueden encapsularse en subprogramas, es decir, en funciones y procedimientos. Cuando los subprogramas deban ser usados desde varios diseños, la reutilización se facilita si los subprogramas son definidos dentro de paquetes (**package**), que a su vez son compilados dentro de una librería (por defecto en la librería **work**). Además de subprogramas, en un paquete pueden declararse también componentes, tipos de datos y constantes.
La sintaxis para la declaración y definición de un paquete consta de dos partes:
```vhdl
package nombre_paquete is 
	declaraciones 
end package nombre_paquete; 

package body nombre_paquete is 
	descripción de funciones y procedimientos 
end package body nombre_paquete;
```
1. La primera parte, es decir, la declaración del paquete (**package**), es obligatoria y contiene todas las declaraciones de componentes, tipos y subprogramas. 
2. La segunda parte, esto es, el cuerpo del paquete (**package body**), es necesaria sólo cuando se han declarado subprogramas (procedimientos o funciones) en la primera parte. En este caso, en la segunda parte se incluye la descripción del cuerpo de los subprogramas.
Ej: Paquete que contiene la declaración de un tipo de dato y una constante.
```vhdl
library IEEE; 
use IEEE.std_logic_1164.all; 

package ejemplo1 is 
	type estado is (st1, st2, st3, st4); 
	constant datoInicial : std_logic_vector(7 downto 0) := "11111111";
	end package ejemplo1;
```
Si este **package** se compila en la librería **work**, para poder usar en un diseño el tipo de dato y la constante que se declaran en este **package**, es necesario incluir en el diseño la sentencia:
``use work.ejemplo1.all;``
# TEMA 3 SIMULACIÓN DEL CÓDIGO VHDL
## 3.1. INTRODUCCIÓN
Diferencias entre **signal** y **variable**.
![](img/Pasted%20image%2020250426135339.png)

En VHDL hay dos tipos de código: el código **concurrente** y el **código** secuencial.
	Las *sentencias concurrentes* son la asignación condicional (**when-else**), la asignación de selección (**with-select-when**) y la sentencia **generate**. 
	Las *sentencias secuenciales* son las incluidas dentro de bloques **process**, **function** o **procedure**. Sentencias secuenciales son **if**, **wait**, **case** y **for**. Aun cuando dentro de estos bloques la ejecución es secuencial, el bloque en su conjunto es concurrente con el resto de bloques y sentencias concurrentes.
	La ejecución de una sentencia de asignación secuencial se produce en el instante en el cual cambia el valor de alguna de las señales a las cuales la sentencia es sensible. El nuevo valor es asignado transcurrido un retardo, que por defecto es $\delta$. Existen dos formas alternativas de controlar la ejecución de un bloque **process**: mediante lista de sensibilidad y mediante sentencias **wait**. Debe optarse por una de ellas, ya que en un mismo bloque **process** no puede haber sentencias **wait** y lista de sensibilidad.
## 3.2. PROCESAMIENTO DEL CÓDIGO VHDL
Normalmente, el código VHDL es procesado por la herramienta de CAD siguiendo las etapas consecutivas siguientes:
1. *Análisis*. Durante la etapa de análisis, el entorno de simulación comprueba la sintaxis y semántica del código VHD L. El análisis se realiza sobre cada una de las unidades de diseño. Si no hay errores, el entorno de simulación traduce el código VHDL que describe la unidad de diseño a un formato propio y lo almacena en la correspondiente librería. Cuando existen dependencias entre las unidades de diseño, ·la compilación de las mismas debe realizarse siguiendo un determinado orden.
2. *Elaboración*. En un diseño complejo, normalmente el sistema es descrito de manera modular y jerárquica. Durante la etapa de elaboración el entorno de simulación comienza por la unidad de diseño de nivel jerárquico superior y enlaza la declaración de la entity del sistema con la definición de su architecture. En la architecture, va reemplazando cada componente instanciado por su definición. Este proceso se repite recursivamente, descendiendo por los niveles jerárquicos del diseño, hasta que se obtiene una descripción "plana" del sistema, en la cual se ha deshecho la jerarquía y composición.
3. *Ejecución*. Durante la etapa de ejecución, la descripción plana del sistema, obtenida de la elaboración, sirve como entrada al software de simulación o de síntesis.
	Al comienzo de la simulación se resuelve el problema de la *inicialización*. Se denomina *inicialización* al cálculo del valor inicial (es decir, en el instante de tiempo cero) de las *señales explícitas* (aquellas señales declaradas en las **entity** y en las **architecture**) y de las *señales implícitas*.
	En la *inicialización*, los bloques **process** son ejecutados hasta que son suspendidos. Si el bloque **process** tiene sentencias **wait**, se ejecuta el bloque hasta que queda suspendido en la primera sentencia **wait**. Si el bloque **process** tiene lista de sensibilidad, se ejecuta una vez el código completo del bloque, quedando suspendido tras la ejecución de la última sentencia del bloque.
## 3.3. ORDEN DE COMPILACIÓN
El orden de compilación de las unidades de diseño puede ser el siguiente:
1. Declaraciones de los paquetes (**package**), teniendo en cuenta las interdependencias entre los paquetes. Por ejemplo, si un paquete ``paqueteA`` necesita declaraciones de un paquete ``paqueteE``, entonces ``paqueteE`` debe compilarse primero. 
2. Las **entity** que hacen uso de los paquetes anteriores. 
3. Las **architecture**. El orden en la compilación de las **architecture** puede ser cualquiera, ya que cuando en una **architecture** se instancian componentes (por ejemplo, en los bancos de prueba y en las descripciones estructurales), esta **architecture** puede ser compilada sin necesidad de haber compilado previamente las **architecture** de los componentes que utiliza. 
4. Las unidades de diseño **configuration**. 
5. El cuerpo de los paquetes (**package body**). Los cuerpos de los paquetes pueden ser compilados en cualquier orden una vez han sido compiladas sus declaraciones, no tienen forzosamente que compilarse al final. De hecho, normalmente los cuerpos de los paquetes son compilados a continuación de sus declaraciones.

Reglas para la recompilación, en caso de que se modifique el código de una unidad de diseño:
1. Si la declaración de un **package** cambia, entonces no sólo debe recompilarse el cuerpo de ese paquete (**package body**), además deben recompilarse todos los paquetes (la declaración y el cuerpo), las **entity**, las **architecture** y las **configuration** que hacen uso del **package** cuya declaración se ha modificado. 
2. Si el cuerpo de un paquete (**package body**) cambia, entonces sólo es preciso recompilar el cuerpo del paquete. 
3. Si se modifica una **entity**, entonces todas las **architecture** que usan esa **entity**, incluyendo aquellas en las cuales se declaran o instancian componentes de esa **entity**, deben ser recompiladas. Las declaraciones de **configuration** deben ser también recompiladas. 
4. Si una **architecture** cambia, entonces sólo es preciso recompilar dicha **architecture**. 
5. Si cambia una **configuration**, sólo es preciso recompilar dicha **configuration**.
## 3.4. DRIVERS
Los *drivers* no son definidos explícitamente por el diseñador en el código VHDL del diseño, sino que son creados automáticamente por el simulador en la fase de *elaboración* del código. 
Cada señal tiene asociado uno o varios drivers. El valor de la señal viene determinado en todo momento por el valor de sus drivers. En el caso más sencillo, en que la señal tiene un único driver, el valor de la señal coincide en todo momento con el valor de su driver. 
Cada driver de una señal está asociado a una o varias asignaciones a dicha señal. Cada señal tiene un driver asociado a cada asignación concurrente a la señal y un driver asociado a cada bloque **process** en el cual hay asignaciones a la señal. Las reglas que se siguen para establecer dicha asociación son las siguientes:
- Se asocia un driver para la señal por cada asignación concurrente en la cual se asigne valor a la señal. 
- Si dentro de un bloque **process** se asigna valor a una señal mediante una única asignación secuencial, entonces se asocia a dicha asignación secuencial un driver para la señal. 
- Si dentro de un bloque **process** se asigna valor a una misma señal en varias asignaciones secuenciales, entonces se asocia a todas ellas un único driver para la señal. 
- Si se asigna valor a una misma señal en cierto número de bloques **process**, entonces se asocia un driver para la señal por cada uno de estos bloques **process**.
Cada driver contiene una cola. En ella van almacenándose las *transacciones* futuras planificadas para la señal, debidas a la ejecución de las asignaciones asociadas al driver. Cada una de estas transacciones planificadas consta de: ==el nuevo valor que debe asignarse a la señal y el instante de tiempo en que debe asignarse dicho valor.==
Al ir avanzando la simulación, el valor del driver va cambiando de acuerdo a las transacciones planificadas en su cola. Las transacciones van siendo eliminadas de la cola a medida que se van asignando al driver los valores planificados.
El valor de la señal en cada instante se calcula a partir del valor de sus drivers en ese instante. Si los drivers asociados a una señal proporcionan diferentes valores, entonces para decidir qué valor asignar debe recurrirse a la función de resolución del tipo de dato de la señal. Si el tipo de dato no tiene función de resolución, se produce un error. Este es el caso, por ejemplo, de los tipos **boolean** e **integer**.
Una función de resolución es una función que examina los valores de los drivers de la señal y resuelve el conflicto, devolviendo un valor. La función de resolución es invocada automáticamente por el simulador cuando el tipo de la señal tiene una función de resolución asociada. Los tipos ``std_logic`` y `std_logic_vector` tienen definidas funciones de resolución en el paquete ``std_logic_1164``. 
Si una señal del tipo ``std_logic`` tiene dos drivers, el conflicto se resuelve de manera automática, según se muestra en la tabla. Por ejemplo, si un driver está a '0' y el otro a ' 1 ' , el valor resultante es 'X'
![](img/Pasted%20image%2020250426153624.png)
## 3.5. INICIALIZACIÓN
Se llama inicialización a los cálculos que realiza el simulador en el instante inicial de la simulación, con el fin de calcular los valores de las señales en t = 0.
	Cuando al declarar una señal se especifica su valor inicial, entonces en el instante t = 0 los drivers de la señal tienen dicho valor. Dado que el valor de la señal se calcula en todo momento del valor de sus drivers, la señal tendrá en t = 0 también dicho valor. 
	Si no se especifica ningún valor al declarar la señal, entonces el simulador asume que los drivers de la señal (y consecuentemente la señal) tienen en t = 0 el valor por defecto correspondiente al tipo de dato de la señal. Si la señal es del tipo ``std_logic``, el valor inicial por defecto es '``U``'.

A continuación, también en el instante t = O, se ejecutan las sentencias concurrentes y los bloques **process** una vez.
	Si el bloque **process** tiene lista de sensibilidad, se ejecuta el código secuencial completo del bloque.
	Si el bloque no tiene lista de sensibilidad, se ejecutan por orden las sentencias secuenciales, comenzando por la primera, hasta que se encuentra una sentencia **wait**, en la cual se suspende la ejecución del bloque. 
	Por ello, una sentencia **wait on** al final del bloque **process** es equivalente a la lista de sensibilidad, siempre que en la sentencia **wait on** aparezcan las mismas señales que en la lista de sensibilidad. Para conseguir un comportamiento idéntico al de la lista de sensibilidad, la sentencia **wait** debe colocarse al final del bloque **process**, no al principio. de manera que durante la inicialización el bloque sea ejecutado una vez.
Al ejecutar los bloques **process** en t = 0, se añaden a las colas de los drivers las transacciones planificadas para las señales. Si no se especifica el retardo en las asignaciones, se planificará asignar los nuevos valores a las señales en el instante t = $\delta$.

## 3.6. ATRIBUTOS DE LAS SEÑALES
Los atributos de las señales proporcionan información acerca de los instantes en los cuales se producen cambios en el valor de la señal y también acerca del valor en sí de la señal.
- Un *evento* es un cambio en el valor de la señal, que ocurre cuando se asigna a la señal un nuevo valor, diferente del que tenía anteriormente. 
- Se dice que una señal está *activa* cuando su valor es actualizado, con independencia de que el nuevo valor sea el mismo que el valor actual o sea diferente. Por ejemplo, si en determinado instante el valor de la señal es '1' y se le asigna el valor ' 1 ' , en ese instante la señal está activa, pese a que su valor no cambie. 
- Se llama *transacción* a asignar valor a una señal, ya sea este valor igual o diferente al valor que tiene la señal previamente a dicha asignación. En el instante en que se produce la transacción, la señal está activa. Cuando el valor asignado es diferente que el valor previo, se dice además que se ha producido un evento.
- Se denomina *señal implícita* a una señal que no está declarada en el código VHDL, pero que se deduce del empleo de los atributos ``'stable``, ``'quiet``, ``'delayed`` y ``'transaction``. Cada vez que uno de estos atributos es usado en un diseño, el simulador genera automáticamente una señal implícita. VHDL impone una restricción al uso de las señales implícitas: no pueden ser leídas desde dentro de un subprograma.
Los atributos de las señales pueden clasificarse en dos tipos: aquellos que representan una señal implícita y aquellos que equivalen a la llamada a una función.
![](img/Pasted%20image%2020250426154753.png)
## 3.7. EL RETARDO DELTA
Uno de los requisitos que debe satisfacer la simulación del código concurrente es el siguiente: ==el resultado de la simulación debe ser independiente del orden en que se ejecuten en un determinado instante las sentencias concurrentes.== 
Para satisfacer este requisito, una vez se han evaluado todas las sentencias concurrentes activas en el instante t y se han calculado los nuevos valores de las señales, estos nuevos valores se asignan a las señales en el instante t + $\delta$ (supuesto que no se indique en el código explícitamente el retardo). 
El tiempo $\delta$ es una cantidad infinitesimal de tiempo, que representa un tiempo mayor que cero, pero que se considera cero cuando se suma a una cantidad de tiempo no infinitesimal.
## 3.8. GESTIÓN DE LA COLA DE TRANSACCIONES DEL DRIVER
Cada driver contiene una cola, en la cual van almacenándose las transacciones planificadas para la señal. Cuando se ejecuta una sentencia de asignación a la señal, las transacciones calculadas en dicha sentencia son añadidas a la cola del driver asociado a dicha asignación. Una vez añadidas las nuevas transacciones, se aplican unas reglas para decidir si las transacciones que estaban anteriormente almacenadas en la cola deben ser eliminadas o no. Estas reglas dependen de si las nuevas transacciones deben producirse con un retardo inercial o de transporte.

Supongamos que en el instante t se añaden a la cola un conjunto de transacciones, que están planificadas para los instantes futuros t 1 , t 2 , . . .
	**Regla 1** Se eliminan de la cola todas las transacciones planificadas para instantes de tiempo iguales o posteriores a t1.
	**Regla 2** Si las nuevas transacciones tiene retardo inercial (para retardo de transporte este paso no se realiza), se van inspeccionando las transacciones que se encontraban en la cola del driver, progresando hacia atrás en el tiempo, desde el instante t 1 hacia el cero:
		**Regla 2.1** Si la transacción que está siendo inspeccionada asigna a la señal el mismo valor que la nueva transacción planificada para t1 , entonces la transacción inspeccionada se mantiene en la cola. 
		**Regla 2.2** Si la transacción inspeccionada asigna a la señal un valor diferente del que asigna la nueva transacción planificada para t1 , entonces se elimina de la cola la transacción que está siendo inspeccionada y todas las transacciones planificadas para instantes anteriores a ésta.
Ejemplo en pag 223
# TEMA 4 DISEÑO DE LÓGICA COMBINACIONAL
## 4.2. DISEÑO PARA SÍNTESIS DE LÓGICA COMBINACIONAL
La característica fundamental de un bloque lógico combinacional es que su comportamiento y sus salidas dependen únicamente del valor actual de las entradas. No dependen del valor pasado de las entradas, ni tampoco del estado.
### 4.2.1. Empleo de sentencias concurrentes
Los circuitos lógicos combinacionales pueden ser descritos empleando sentencias concurrentes de asignación a señales. Este tipo de sentencias modelan de manera correcta el comportamiento de los dispositivos combinacionales, que están activos durante todo el tiempo de manera concurrente.
- En la parte izquierda de una sentencia de asignación concurrente debe aparecer, o bien una señal local de la **architecture**, o bien una señal de la interfaz (definida en la **entity**) del tipo **out** o **inout**. 
- En la parte derecha de la asignación concurrente pueden aparecer señales locales de la **architecture** y también señales de la interfaz, del tipo **in** o **inout**.
El que la herramienta de síntesis cree una única puerta lógica o un array de puertas lógicas, depende del tipo de señales usadas en la sentencia de asignación concurrente.
Ej:
- Puerta NAND
```vhdl
nand_out <= iO nand i1;
```
- Array de inversores
```vhdl
inv_vec <= not iO_vec; -- donde inv_vec e iO_vec son std_logic_vector.
```

Es posible sintetizar multiplexores y decodificadores que están descritos mediante sentencias concurrentes condicionales.
- Multiplexor 4:1
```vhdl
with sel_vec select
	mux41out <=     iO when "00", 
					i1 when "01", 
					i2 when "10", 
					i3 when others;
```
Es aconsejable usar sentencias concurrentes de selección para describir multiplexores y decodificadores, ya que el empleo de sentencias concurrentes condicionales puede dar lugar a la síntesis de circuitos innecesariamente complejos. Esto es debido a que las condiciones de las sentencias condicionales no tienen forzosamente que ser excluyentes entre sí, cosa que sí sucede siempre con las condiciones de las sentencias concurrentes de selección.

Finalmente, los circuitos que realizan operaciones aritméticas pueden ser descritos aplicando las correspondientes operaciones aritméticas a los tipos de datos adecuados. Por ejemplo, los operandos std_logic_ vector deben ser convertidos a unsigned antes de emplear los operandos suma o multiplicación.
- Sumador:
```vhdl
add_uvec <= unsigned(iO_vec) + i1_uvec; -- donde i1_uvec y add_uvec son unsigned.
```
- Multiplicador
```vhdl
mult_uvec <= unsigned(iO_vec) * i1_uvec; -- donde i1_uvec y mult_uvec son unsigned.
```
### 4.2.2. Empleo de bloques process
Cierto número de cláusulas de VHDL (tales como **if**, **case** y **for**) sólo pueden ser usadas dentro de bloques **process**.
Los bloques process pueden ser usados para describir lógica combinacional. Para que el circuito resultante de la síntesis sea combinacional, deben respetarse las reglas siguientes: 
1. Todas las entradas del circuito deben estar incluidas en la lista de sensibilidad del bloque **process**. 
2. Ninguna otra señal debe estar incluida en la lista de sensibilidad. 
3. Ninguna de las sentencias internas al bloque **process** debe ser sensible al flanco de subida o de bajada de ninguna señal.
## 4.3. FUNCIONES LÓGICAS
En esta sección se describe el modelado de dos funciones lógicas y de su banco de pruebas. Las dos funciones lógicas (F y G), que dependen de 3 variables (a, b y e), son las siguientes:
```
F = a and b or not c 
G = a and b or not b and c
```
### 4.3.1. Diseño del circuito
```vhdl
-- Funciones lógicas: 
-- F = ab + c' 
-- G = ab + b'c 
-- Fichero: funcLog_F_G.vhd 
library IEEE; use IEEE.std_logie_1164.all;

entity funeLog_F_G is port 
	( F, G : out std_logic;
	  a, b, e : in std_logic ); 
end entity funeLog_F_G; 

architecture funeLog_F_G of funeLog_F_G is 
begin 
	F <= (a and b) or not c; G <= (a and b) or (not b and c); 
end arch1tecture funeLog_F_G;
```
Obsérvese que el orden en el cual deben realizarse las operaciones booleanas debe indicarse explícitamente mediante paréntesis en el código VHDL (en caso contrario se obtiene error).
### 4.3.2. Programación del banco de pruebas
```vhdl
-- Banco de pruebas 
-- Fichero: bp_funcLog_F_G.vhd 
library IEEE; 
use IEEE.std_logie_1164.all; 
use IEEE.numerie_std.all; 

entity bp_funeLog_F_G is 
end entlty bp_funeLog_F_G; 

architecture bp_funeLog_F_G of bp_funeLog_F_G is 
	signal yO, y1 : std_logic; -- Conectar salidas UUT
	signal xO, x1, x2 : std_logic;  -- Conectar entradas UUT 
	
	component funeLog_F_G is port 
		( F, G : out stdJogic; 
		  a, b, e : in std_logic); 
	end component funeLog_F_G; 
	
begin
	-- Instanciar y conectar UUT 
	uut : component funeLog_F_G port map 
		( F = > yO, G = > y1, 
		  a => xO, b => x1, e = > x2 ); 
	gen_vec_test : process 
		variable test_in : unsigned (2 downto O); -- Vector de test 
	begin 
		test_in := B"000"; 
		for count in 0 to 7 loop 
			x2 <= test_in(2); 
			x1 <= test_in(1); 
			x0 <= test_in(0); 
			wait for 10 ns; 
			test_in := test_in + 1; 
		end loop; 
		wait; 
	end process gen_vec_test; 

end architecture bp_funeLog_F_G;
```

Puesto que el banco de pruebas no va a ser sintetizado, puede emplearse para su programación cualquier instrucción VHDL disponible (incluso aquellas que darían lugar a circuitos no sintetizables). Instrucciones útiles de este tipo son **wait**, **assert** y **report**, que permiten controlar el progreso de la simulación, comprobar y mostrar sus resultados.

Como programa VHDL, el banco de pruebas es un tipo especial de pareja **entity-architecture**, que no tiene ni entradas ni salidas externas. Por este motivo, la **entity** del banco de pruebas no contiene ningún puerto.

La **architecture** del banco de pruebas contiene un proceso (bloque **process**) en el cual se generan los vectores de test y se introducen como entradas del UUT. El bloque **process** se emplea para encapsular una secuencia de sentencias que serán ejecutadas secuencialmente.

En el código del banco de pruebas, la variable ``test_in`` se usa para almacenar en un mismo vector de tres bits las entradas al UUT, de modo que este vector pueda ser incrementado (con el fin de generar todas las posibles combinaciones de vectores de test) empleando un bucle **for**. La variable ``test_in`` se ha declarado de tipo **unsigned**, ya que se emplea para realizar operaciones aritméticas. La longitud del vector se especifica por el rango (2 **downto** 0). ==El primer número del rango (2) indica el índice del bit más significativo del vector, y el segundo número del rango (0) indica el índice del bit menos significativo del vector.==

La segunda sentencia **wait**, que está situada al final del bloque **process**, no tiene ninguna indicación acerca del tiempo que hay que esperar. Este tipo de sentencia **wait** se emplea para suspender indefinidamente la ejecución del bloque **process**, ya que "espera para siempre".
## 4.4. MULTIPLEXOR DE 4 ENTRADAS
![](img/Pasted%20image%2020250503122328.png)
Multiplexor de 4 entradas (i3, i2, i1, i0), dos entradas de selección (si, so) y una salida (d).

### 4.4.1. Diseño usando sentencias secuenciales
#### Diseño de un MUX 4:1 mediante una sentencia **if**
```vhdl
-- MUX 4x1 
-- Fichero: mux_4xLprocess_if.vhd 
library IEEE; use IEEE.std_logic_1164.all; 

entity mux_4x1 is port 
	( d : out std_logic; 
	  i3, i2, i1, i0 : in std_logic; 
	  s1, s0 : in std_logic ) ; 
end entity mux_4x1; 

architecture mux_4x1 of mux_4x1 is 
begin 
	process (i3, i2, i1, i0, s1, s0) 
	begin 
		if (s1='0' and s0='0') then 
			d <= i0; 
		elsif (s1='0' and s0=' 1 ') then 
			d <= i1; 
		elsif (s1=' 1' and s0='0') then 
			d <= i2; 
		else 
			d <= i3; 
		end if; 
	end process; 
end architecture mux_4x1;
```
#### Descripción del MUX 4:1 mediante sentencias **if** y **case**
```vhdl
-- MUX 4x1 
-- Fichero: mux_4xLprocess_if_case.vhd 
library IEEE; use IEEE.std_logic_1164.all; 

entity mux_4x1 is port 
	( d : out std_logic; 
	  i3, i2, i1, i0 : in stdlogic; 
	  s1, s0 : in std_logic ); 
end entity mux_4x1; 

architecture mux_4x1 of mux4x1 is 
begin 
	process (i3, i2, i1, i0, s1, s0) 
		variable sel : integer; 
	begin 
		if (s1='0' and s0='0') then 
			sel := 0; 
		elsif (s1= '0' and s0='1') then 
			sel := 1; 
		elsif (s1='1'and s0='0') then 
			sel := 2; 
		else 
			sel := 3; 
		end if; 
		case sel is 
			when 0 => 
				d <= i0; 
			when 1 => 
				d <= i1; 
			when 2 => 
				d <= i2; 
			when others => 
				d <= i3; 
		end case; 
	end process; 
end architecture mux_4x1;
```
Obsérvese que en ambos diseños el bloque **process** es sensible a las señales i3, i2, i1, i0, s1, s0. Esto significa que las sentencias del bloque se ejecutarán cada vez que alguna de estas señales cambie de valor.

#### Banco de pruebas del MUX 4:1.
```vhdl
-- Banco de pruebas 
-- Fichero: bp_mux_4x1.vhd 
library IEEE; use IEEE.std_logic_1164.all; 

entity bp_mux_4x1 is 
end entity bp_mux_4x1; 

architecture bp_mux_4x1 of bp_mux_4x1 is
	signal d                  : std_logic; -- Conectar salida UUT 
	signal i0, i1, i2, i3, 
		   s0, s1             : std_logic; -- Conectar entradas UUT 

component mux_4x1 is port 
	( d : out std_logic; 
	  i3, i2, i1, i0 : in std_logic; 
	  s1, s0 : in std_logic ) ; 
end component mux_4x1; 

begin 
	-- Instanciar y conectar UUT 
	uut : component mux_4x1 port map 
		( d = > d, 
		  i0 = > i0, i1 = > i1, i2 = > i2, i3 = > i3, 
		  s0 = > s0, s1 = > s1 ); 
	gen_vec_test : process 
	begin 
		i0 < = '0'; i1 < = '0'; i2 <= '1'; i3 < = '0'; s0 < = '0'; s1 < = '0'; 
		wait for 5 ns; 
		i0 < = '1'; 
		wait for 5 ns; 
		s0 < = '1'; 
		wait for 10 ns; 
		s0<= '0'; s1 < = '1'; 
		wait for 10 ns; s0 < = '1'; 
		wait; 
	end process gen_vec_test; 
	
end architecture bp_mux_4x1;
```
Banco de pruebas que aplica algunos vectores de test al multiplexor. Un error que a veces se comete consiste en olvidar incluir en la lista alguna de las variables a las que es sensible el bloque **process**. La consecuencia de este error es que el bloque **process** no se ejecutará cuando cambie el valor de la variable no incluida en la lista, con lo cual el modelo simulado no reproducirá correctamente el circuito real.
### 4.4.2. Diseño usando sentencias concurrentes
#### Diseño de un MUX 4:1 mediante una sentencia concurrente
```vhdl
-- MUX 4x1 
-- Fichero: mux_4x1concnrrente1.vhd 
library IEEE; use IEEE.std_logic_ii64.all; 

entity mux_4x1 is port 
	( d : out std_logic; 
      i3, i2, i1, i0 : in std_logic; 
      si, sO : in std_logic ); 
end entity mux_4x1; 

architecture mux_4x1_concurrente of mux_4x1 is 
begin 
	d    <= i0 when (s1='0' and s0='0') else 
		    i1 when (s1='0' and s0='1') else 
		    i2 when (s1=' 1' and s0='0') else 
		    i3; 
end architecture mux_4x1_concurrente;
```

Describe el circuito multiplexor usando una sentencia concurrente, en la cual se asigna valor a la señal ``d`` en función del valor que tomen las entradas al circuito.
#### Diseño de un MUX 4:1 mediante dos sentencias concurrentes.
```vhdl
-- MUX 4x1
-- Fichero: mux_4x1concurrente.vhd 
library IEEE; use IEEE.std_logic_ii64.all; 

entity mux_4x1 is port 
	( d : out std_logic; 
	  i3, i2, ii, iO : in std_logic; 
	  si, sO : in std_logic ) ; 
end entity mux_4x1; 

architecture mux_4xi_concurrente of mux_4x1 is 
	signal sel : integer; 
begin 
	sel <=   0 when (s1='0' and s0='0') else 
	         1 when (s1= '0' and s0= '1' ) else 
	         2 when (s1='1' and s0='0') else 
	         3; 
	d <=     iO when sel = O else 
			 i1 when sel = 1 else 
			 i2 when sel = 2 else 
			 i3; 
end architecture mux_4x1_concurrente;
```
El código ilustra el empleo de señales del tipo **integer**. Este diseño es una variación del anterior, describiéndose en este caso el comportamiento del circuito mediante dos sentencias concurrentes. En la primera, se asigna valor a la señal **integer** ``sel`` en función del valor de las entradas de selección. En la segunda, se asigna valor a la salida del circuito en función de las entradas de datos y del valor de la señal entera.
## 4.5. RESTADOR COMPLETO DE 1 BIT
VHDL permite describir la **architecture** de un circuito mediante su *comportamiento* y también mediante su *estructura*, es decir, indicando cómo están conectados los subcircuitos que lo componen.
### 4.5.1. Descripción del comportamiento
Tabla de la verdad del *circuito restador de 1 bit*. Este circuito calcula el resultado (res) y el acarreo (acarreo) obtenidos de realizar la resta (a- b) de dos bits (a,b).

| a   | b   | res | acarreo |
| --- | --- | --- | ------- |
| 0   | 0   | 0   | 0       |
| 0   | 1   | 1   | 1       |
| 1   | 0   | 1   | 0       |
| 1   | 1   | 0   | 0       |
Un *circuito restador completo de 1 bit* tiene una entrada adicional: el acarreo de entrada. Conectando varios de estos circuitos, puede obtenerse un restador de números de varios bits.
```vhdl
-- Restador completo de 1 bit 
-- Fíchero: restadorCompleto1bitComport.vhd 
library IEEE; 
use IEEE.std_logic_1164.all; 
use IEEE.numeric_std.all; 

entity rest_completo is port 
	( res, acarreo_out : out std_logic; 
	  a, b, acarreo_in : in std_logic); 
end entity rest_completo; 

architecture rest_completo_comport of rest_completo is 
	signal result : unsigned ( 1 downto 0 ); 
begin 
	result <= ('0' & a) - ('0' & b) - ('0' & acarreo_in);
	acarreo_out <= result(1); 
	res <= result(0); 
end architecture rest_completo_comport;
```
En la **architecture**, se define una señal del tipo **unsigned** de 2 bits, llamada ``result``, con el fin de almacenar el resultado de la operación de sustracción. Al declararla, se indica que la señal tiene 2 bits, especificando para ello su rango: ( 1 downto 0). ==Si no se especifica el rango, las señales del tipo **unsigned** tienen por defecto 32 bits. El tipo de la señal debe ser **unsigned**, a fin de permitir el uso del operador resta.== 
==Las señales de entrada, de 1 bit, deben ser extendidas a 2 bits (concatenando un 0), de modo que el resultado de la resta pueda ser almacenado en una señal de 2 bits del tipo **unsigned**.==

Finalmente, el resultado de la resta se asigna a ``res`` y ``acarreo_out``. Obsérvese que es posible realizar las asignaciones:
```vhdl
acarreo_out <= result(1); 
res <= result(0);
```
porque cada elemento de una señal del tipo **unsigned** es del tipo **std_logic** que es exactamente el tipo de las señales ``res`` y ``acarreo_out``.

### 4.5.2. Descripción de la estructura
![](img/Pasted%20image%2020250503131026.png)

#### Diseño de las puertas lógicas XOR2, NOTl , AND2 y OR3.
```vhdl
-- Puerta OR exclusiva de 2 entradas. Fichero: xor2.vhd 
library IEEE; use IEEE.std_logic_1164.all; 

entity xor2 is port 
	( y0 : out std_logic;
	  x0, x1 : in std_logic ); 
end entity xor2; 

architecture xor2 of xor2 is 
begin 
	y0 <= x0 xor x1; 
end architecture xor2; 
----------------------------------------------------
-- Inversor de 1 entrada. Fichero: notl.vhd 
library IEEE; use IEEE.std_logic_1164.all; 

entity not 1 is port 
	( y0 : out std_logic; 
	  x0 : in std_logic ) ; 
end entity not1; 

architecture not 1 of not 1 is 
begin 
	y0 <= not x0; 
end architecture not 1;
----------------------------------------------------
-- Puerta AND de 2 entradas. Fichero: and2.vhd 
library IEEE; use IEEE.std_logic_1164.all;

entity and2 is port 
	( y0 : out std_logic; 
	  x0, x 1 : in std_logic ) ; 
end entity and2; 

architecture and2 of and2 is 
begin 
	y0 <= x0 and x1; 
end architecture and2; 
----------------------------------------------------
-- Puerta OR de 3 entradas. Fichero: or3.vhd 
library IEEE; use IEEE.std_logic_1164.all; 

entity or3 is port 
	( y0 : out std_logic; 
	  x0, x1, x2 : in std_logic ); 
end entity or3; 
architecture or3 of or3 is 
begin 
	y0 <= x0 or x1 or x2; 
end architecture or3;
```
#### Descripción de la estructura de un restador completo de un bit.
Para componer el circuito restador usando las puertas lógicas anteriores, es necesario instanciar los componentes necesarios y conectarlos. Para ello, es preciso escribir la **entity** de cada uno de los componentes, instanciar los componentes y describir la conexión entre ellos.
```vhdl
-- Restador completo de 1 bit 
-- Fichero: restadorCompletolbitEstruc.vhd 
library IEEE; use IEEE.std_logie_1164.all; 

entity rest_eompleto is port 
	( res, acarreo_out : out std_logic; 
	  a, b, acarreo_in : in std_logic); 
end entity rest_eompleto; 

architecture rest_completo_estruc of rest_completo is 

	signal not_a, c, d, e, f : std_logic; 
	
	-- Declaración de las clases de los componentes 
	component xor2 is port 
		( y0 : out std_logic; 
		  x0, x1 : in std_logic ) ; 
	end component xor2; 
	
	component not1 is port 
		( y0 : out std_logic; 
		  x0 : in std_logic ) ; 
	end component not 1; 
	
	component and2 is port 
		( y0 : out std_logic; 
		  x0, x1 : in std_logic ) ; 
	end component and2; 
	
	component or3 is port 
		( y0 : out std_logic; 
		  x0, x1, x2 : in std_logic ) ; 
	end component or3; 

begin 
	-- Instanciación y conexión de los componentes 
	g0 : component xor2 port map (c, a, b ); 
	g1 : component xor2 port map (res, c, acarreo_in); 
	-- g2 : component not1 port map (not_a, a); 
	g2 : component not1 port map (y0 => not_a, x0 = > a); 
	g3 : component and2 port map (d, not_a, acarreo_in); 
	g4 : component and2 port map (e, not_a, b); 
	g5 : component and2 port map (f, b, acarreo_in); 
	g6 : component or3 port map (acarreo_out, d, e, f); 

end architecture rest_completo_estruc;
```
En el modelo anterior, se realiza la conexión entre los componentes mediante asociación posicional. Es posible también usar asignación implícita. Por ejemplo: 
``g2 : component not1 port map (y0=> not_a, x0 =>a);``
### 4.5.3. Programación del banco de pruebas
#### Banco de pruebas del restador completo de un bit.
```vhdl
-- Banco de pruebas del restador completo de 1 bit. Fichero: restadorCompleto1bitbp.vhd 
library IEEE; use IEEE.std_logic_1164.all; use IEEE.numeric_std.all; 

entity bp_rest_completo is
end entity bp_rest_completo; 
-- El banco de pruebas no tiene ni entradas ni salidas 

architecture bp_rest_completo of bp_rest_completo is 
	signal res, acarreo_out : std_logic; -- Para conectar el UUT 
	signal a, b, acarreo_in : std_logic; -- Para conectar el UUT 
	
	component rest_completo is port 
		( res, acarreo_out : out std_logic; 
		  a, b, acarreo_in : in std_logic); 
	end component rest_completo; 
begin 
	-- Instanciar y conectar UUT 
	uut : component rest_completo port map 
		(res, acarreo_out, a, b, acarreo_in); 
	-- Crear vectores de test y comprobar salidas del UUT 
	gen_vec_test : process 
		variable test_in : unsigned (2 downto 0); -- Vector de test
		variable esperado : unsigned (1 downto 0); -- Salida esperada
		variable num_errores : integer := 0; -- Numero de errores esperado 
	begin 
		test_in := B"000"; 
		for count in 0 to 7 loop 
			a          <= test_in(2); 
			b          <= test_in(1); 
			acarreo_in <= test_in(0); 
			wait for 10 ns;   
			esperado := ('0' & a) - ('0' & b) - ('0' & acarreo_in); 
			if (esperado /= ( acarreo_out & res )) then -- Comprueba resultado
				report "ERROR : Esperado ("           & -- Report del error
						std_logic'image(esperado(1)) & 
						std_logic'image(esperado(0)) & 
						") /= actual ("              & 
						std_logic'image(acarreo_out) & 
						std_logic'image(res)         &
						") en el instante "          & 
						time'image(now);
				num_errores := num_errores + 1; 
			end if; 
			test_in := test_in + 1; 
		end loop;
		report "Test completo. Hay "       &
				integer'image(num_errores) & 
				"errores.";
		wait;
	end process gen_vec_test; 
end architecture bp_rest_completo;
```

La conexión del UUT en el banco de pruebas se realiza instanciando el restador binario como un subcircuito dentro del banco de pruebas. Aunque la conexión se realiza mediante *asociación posicional*, podría haberse realizado la asociación nombrando explícitamente los puertos: 
```vhdl
uut : component rest_completo port map
	(res => res, acarreo_out => acarreo_out, 
	 a=> a, b => b, acarreo_in => acarreo_in);
```
Se han definido señales internas al banco de pruebas para todas las conexiones al UUT. Aunque en este ejemplo si lo sean, los nombres de las señales no tienen que ser idénticos a los nombres de los puertos del UUT.

Se ha definido un proceso (**process**) para generar las formas de onda de las entradas al UUT, y en ese mismo proceso se han incluido las sentencias para comprobar si las salidas del UUT coinciden con las esperadas.
==Es esencial tener en cuenta que el método empleado para calcular las salidas "esperadas" del UUT debe ser diferente del método empleado en el propio UUT para obtener las salidas.== En este ejemplo, el UUT contiene una descripción estructural de la arquitectura del restador, mientras que las salidas "esperadas" (variable ``esperado``) se calculan a partir de una descripción del comportamiento del restador: 
``esperado := ('0' & a)- ('0' & b)- ('0' & acarreo_in);``

El comando **report** se usa para escribir texto en la consola. El argumento del comando (esto es, el texto a escribir) debe ser del tipo **string**. Por ejemplo, cadenas de caracteres concatenadas mediante el operador &. Por ello, todo lo que se desee mostrar deben ser convertido previamente al tipo **string**. Por ejemplo, ``std_logic' image (res)`` se usa para convertir el valor de res, que es del tipo **std_logic**, a un dato del tipo **string**.

Asimismo, **now** es una función predefinida que devuelve el tiempo simulado como un dato del tipo **time**. Puede usarse ``time'image(now)`` para obtener una representación del tipo **string** del tiempo actual de la simulación.
#### Banco de pruebas del restador completo de un bit usando un procedimiento.
```vhdl
-- Banco de pruebas del restador completo de 1 bit empleando un procedimiento 
-- Fichero: restadorCompleto1bitbp_procedure.vhd 
library IEEE; use IEEE.std_logic_1164.all; use IEEE.numeric_std.all; 

entity bp_rest_completo is 
end entity bp_rest_completo;
-- El banco de pruebas no tiene ni entradas ni salidas 

architecture bp_rest_completo_procedure of bp_rest_completo is 
	signal res, acarreo_out : std_logic; -- Para conectar el UUT 
	signal a, b, acarreo_in : std_logic; -- Para conectar el UUT 
	procedure error_check( esperado, actual : in unsigned; 
						   num_errores : inout integer ) is 
	begin 
		if (esperado /= actual) then -- Comprueba resultado y report del error
			report "ERROR : Esperado ("           & 
					std_logic'image(esperado(1))  & 
					std_logic'image(esperado(0))  & 
					") /= actual ("               & 
					std_logic'image(actual(1))    & 
					std_logic'image(actual(0))    & 
					") en el instante"            &
					time'image(now); 
			num_errores := num_errores + 1;
		end if; 
	end procedure error_check; 
	
	component rest_completo is port 
		( res, acarreo_out : out std_logic; 
		  a, b, acarreo_in : in std_logic); 
	end component rest_completo; 
begin 
	-- Instanciar y conectar UUT 
	uut : component rest_completo port map 
		(res, acarreo_out, 
		 a, b, acarreo_in); 
	-- Crear vectores de test y comprobar salidas del UUT 
	gen_vec_test : process 
		variable test_in : unsigned (2 downto 0); -- Vector de test 
		variable esperado : unsigned (1 downto 0); --Salida esperada 
		variable num_errores : integer := 0; -- Numero de errores 
	begin 
		test_in := B"000"; 
		for count in 0 to 7 loop
			a <= test_in(2); 
			b <= test_in(1); 
			acarreo_in <= test_in(0);
			wait for 10 ns; 
			esperado := ('0' & a) - ('0' & b) - ('0' & acarreo_in); 
			error_check(esperado, acarreo_out & res, num_errores ); 
			test_in := test_in + 1; 
		end loop; 
		report "Test completo. Hay " & integer'image(num_errores) & " errores."; 
		wait; 
	end process gen_vec_test; 
end architecture bp_rest_completo_procedure;
```
Banco de pruebas para el circuito restador completo de 1 bit, programado empleando un procedimiento que realiza la comparación entre el valor esperado y el actual, y que, en su caso, muestra los correspondientes mensajes de error.
#### Banco de pruebas del restador completo de un bit usando una función.
```vhdl
-- Banco de pruebas del restador completo de 1 bit empleando una funcion 
-- Fichero: restadorCompleto1bi1bp_funcion. 
vhd library IEEE; use IEEE.std_logic_1164.all; use IEEE.numeric_std.all; 

entity bp_rest_completo is 
end entity bp_rest_completo; -- El banco de pruebas no tiene ni entradas ni salidas 

architecture bp_rest_completo_funcion of bp_rest_completo is 
	signal res, acarreo_out : std_logic; -- Para conectar el UUT 
	signal a, b, acarreo_in : std_logic; -- Para conectar el UUT 
	
	function error_check( esperado, actual : unsigned; 
						  tnow : time ) return integer is 
	begin 
		assert ( esperado = actual ) -- Comprobacion usando assert y report del error 
			report "ERROR : Esperado ("          & 
				std_logic'image(esperado(1))     & 
				std_logic'image(esperado(0))     & 
				") /= actual ("                  &
				std_logic'image(actual(1))       &
				std_logic'image(actual(0))       & 
				") en el instante "              &
				time'image(tnow) 
			severity error; -- Opcion severity 
		if ( esperado / = actual ) then 
			return 1; -- Indica error 
		else 
			return 0; -- Indica que no hay error 
		end if; 
	end function error_check; 
	
	component rest_completo is port 
		( res, acarreo_out : out std_logic; 
		  a, b, acarreo_in : in std_logic); 
	end component rest_completo; 
begin 
	uut : component rest_completo port map (res, acarreo_out, a, b, acarreo_in); gen_vec_test : process 
		variable test_in : unsigned (2 downto 0); -- Vector de test 
		variable esperado : unsigned (1 downto 0); --Salida esperada 
		variable num_errores : integer := 0; -- Numero de errores 
	begin 
		test_in := B"000"; 
		for count in 0 to 7 loop
			a <= test_in(2); b <= test_in(1); acarreo_in <= test_in(0);
			wait for 10 ns;
			esperado := ('0' & a) - ('0' & b) - ('0' & acarreo_in);
			num_errores := num_errores + error_check( esperado, acarreo_out & res, now ); 
			test_in := test_in + 1; 
		end loop; 
		report "Test completo. Hay " & integer'image(num_errores) & "errores."; 
		wait; 
	end process gen_vec_test; 
end architecture bp_rest_completo_funcion;
```
Obsérvese que se ha sustituido la cláusula **if**, que compara el valor esperado con el valor actual, por una sentencia **assert**. El motivo es únicamente ilustrar el uso de la sentencia **assert**.
## 4.6. SUMADOR COMPLETO DE 1 BIT
Un sumador completo es un circuito con tres bits de entrada ($x_i, y_i, c_i$) y dos bits de salida: el bit suma ($s_i$) y el bit acarreo ($C_{i+1}$). El funcionamiento del circuito está descrito por la tabla de la verdad siguiente:

| $c_i$ | $x_i$ | $y_i$ | $c_{i+1}$ | $s_i$ |
| ----- | ----- | ----- | --------- | ----- |
| 0     | 0     | 0     | 0         | 0     |
| 0     | 0     | 1     | 0         | 1     |
| 0     | 1     | 0     | 0         | 1     |
| 0     | 1     | 1     | 1         | 0     |
| 1     | 0     | 0     | 0         | 1     |
| 1     | 0     | 1     | 1         | 0     |
| 1     | 1     | 0     | 1         | 0     |
| 1     | 1     | 1     | 1         | 1     |
Simplificando las funciones lógicas mediante mapas de Karnaugh, se llega a las expresiones mostradas a continuación.
$$c_{i+1} = x_iy_i + x_ic_i +y_ic_i$$
$$s_i = x_i \oplus y_i \oplus c_i$$
### 4.6.1. Diseño del circuito
![](img/Pasted%20image%2020250503145122.png)
#### Diseño de las puertas lógicas AND2, OR3 y XOR2 con retardo.
```vhdl
-- AND de 2 entradas con retardo 
-- Fichero: and2_retardo.vhd 
library IEEE; use IEEE.std_logic_1164.all; 

entity and2 is 
	generic ( DELAY : time := 10 ns ); 
	port ( y0 : out std_logic; 
		   x0, x 1 : in std_logic ) ;
end entity and2; 

architecture and2 of and2 is 
begin 
	y0 <= ( x0 and x1 ) after DELAY; 
end architecture and2; 
-----------------------------------------------
-- OR de 3 entradas con retardo 
-- Fichero: or3_retardo.vhd 
library IEEE; use IEEE.std_logic_1164.all; 

entity or3 is 
	generic ( DELAY : time := 10 ns );
	port ( y0 : out std_logic; 
		   x0, x1, x2 : in std_logic ); 
end entity or3; 

architecture or3 of or3 is 
begin
	y0 <= ( x0 or x1 or x2 ) after DELAY;
end architecture or3; 
-----------------------------------------------
-- OR exclusiva de 2 entradas con retardo 
-- Fichero: xor2_retardo.vhd 
library IEEE; use IEEE.std_logic_1164.all; 

entity xor2 is 
	generic ( DELAY : time := 10 ns ); 
	port ( y0 : out std_logic; 
		   x0, x 1 : in std_logic ) ;
end entity xor2;

architecture xor2 of xor2 is
begin 
	y0 <= ( x0 xor x1 ) aftter DELAY;
end architecture xor2;
```
#### Package con los componentes del sumador y diseño del sumador
```vhdl
-- Package en el que se definen los componentes 
-- Fichero: puertasLogicas_package.vhd 
library IEEE; use IEEE.std_logic_1164.all; 

package puertasLogicas_package is
	component xor2 is 
		generic ( DELAY : time := 10 ns ); 
		port ( y0 : out std_logic; x0, x1 : in std_logic ) ; 
	end component xor2; 
	
	component and2 is 
		generic ( DELAY : time := 10 ns ); 
		port ( y0 : out std_logic; x0, x 1 : in std_logic ) ; 
	end component and2; 
	
	component or3 is 
		generic ( DELAY : time := 10 ns ); 
		port ( y0 : out std_logic; x0, x1, x2 : in std_logic ); 
	end component or3; 
end package puertasLogicas_package; 
------------------------------------------------
-- Sumador completo de 1 bit 
-- Fichero: snmadorCompleto1bitEstruc.vhd library IEEE; 
use IEEE. std_logic_1164. all; 
use work.puertasLogicas_package.all; 

entity sum_completo is port 
	( s, C_out : out std_logic; 
	  x, y, C_in : in std_logic); 
end entity sum_completo; 

architecture sum_completo_estruc of sum_completo is 
	signal n1, n2, n3, n4: std_logic;
begin
	-- Instanciación y conexión de los componentes 
	XOR2_1 : component xor2 port map (x0 => x, x1 =>y,       y0 => n1   ); 
	XOR2_2 : component xor2 port map (x0 => C_in, x1 => n1,  y0 => s   ); 
	AND2_1 : component and2 port map (x0 => x, x1 =>y,       y0 => n2   ); 
	AND2_2 : component and2 port map (x0 => x, x1 => C_in,   y0 => n3   ); 
	AND2_3 : component and2 port map (x0 => y, x1 => C_in,   y0 => n4   ); 
	OR3_1  : component or3 port map (x0 => n2, x1 => n3, x2 => n4, y0 => C_out); 
end architecture sum_completo_estruc;
```
### 4.6.2. Banco de pruebas
```vhdl
-- Banco de pruebas del sumador completo de 1 bit 
-- Fichero: sumadorCompleto1bitbp.vhd library IEEE; 
use IEEE.std_logic_1164.all; use IEEE.numeric_std.all; 

entity bp_sum_completo is 
end entity bp_sum_completo;
-- El banco de pruebas no tiene ni entradas ni salidas 

architecture bp_sum_completo of bp_sum_completo is 
	signal s, C_out, 
	       x, y, C_in : std_logic; -- Para conectar el UUT 
	
	component sum_completo is 
		port ( s, C_out : out std_logic; 
			   x, y, C_in : in std_logic); 
	end component sum_completo; 

begin 
	-- Instanciar y conectar UUT 
	uut : component sum_completo port map 
		(s => s, C_out => C_out, x => x, y => y, C_in => C_in); 
		-- Crear vectores de test y comprobar salidas del UUT 
		gen_vec_test : process 
			variable test_in : unsigned (2 downto 0); -- Vector de test
			variable esperado : unsigned (1 downto 0); --Salida esperada 
			variable num_errores : integer := 0; -- Numero de errores 
		begin 
			test_in := B"000"; 
			for count in 0 to 7 loop 
				C_in <= test_in(2); 
				x <= test_in(1); 
				y <= test_in(0); 
				wait for 50 ns; 
				esperado := ('0' & x) + ('0' & y) + ('0' & C_in); 
				if (esperado /= ( C_out & s ) ) then -- Comprueba resultado 
					report "ERROR : Esperado ("       & 
						std_logic'image(esperado(1))  & 
						std_logic'image(esperado(0))  & 
						") /= actual ("               & 
						std_logic'image(actual(1))    & 
						std_logic'image(actual(0))    & 
						") en el instante"            &
						time'image(now); 
					num_errores := num_errores + 1;
				end if; 
				test_in := test_in + 1; 
			end loop; 
			report "Test completo. Hay " & integer'image(num_errores) & " errores."; 
			wait; 
		end process gen_vec_test; 
end architecture bp_sum_completo;
```
## 4.7. UNIDAD ARITMÉTICO LÓGICA
En esta sección se realizará el diseño de una AL U que realiza operaciones entre dos operandos, A y B, en función del valor de la señal de entrada de selección de función, ``mode``, que tiene 3 bits.
![](img/Pasted%20image%2020250503151332.png)
### 4.7.1. Diseño de la ALU
En estos diseños se empleará un **package** para definir tanto la constante que determina el tamaño de palabra de los operandos, como la constante que determina el tamaño de la palabra de selección de la operación. Obsérvese que para poder usar este **package** se incluye en ambos diseños la sentencia: 
``use work.ALU_CONSTANTS.all;``
```vhdl
-- Definición de constantes globales de la ALU. Fichero: ALU_CONSTANTS.vhd 
package ALU_CONSTANTS is 
	constant WIDTH integer := 16; -- Núm. bits de los operandos
	constant SEL_BITS : integer := 3; -- Núm. bits selección de operación 
end package ALU_CONSTANTS; 
-----------------------------------------------
-- ALU diseñada mediante una sentencia concurrente. Fichero: ALU_concurrente.vhd 
library IEEE; 
use IEEE.std_logic_1164.all; 
use IEEE.numeric_std.all; 
use work.ALU_CONSTANTS.all; 

entity ALU is 
	port ( C : out std_logic_vector (WIDTH-1 downto 0); 
		   A, B : in std_logic_vector (WIDTH-1 downto 0);
		   mode : in std_logic_vector (SEL_BITS-1 downto 0) );
end entity ALU;  

architecture ALU_concurrente of ALU is 
begin 
	C <= std_logic_vector (signed(A)+signed(A)) when (mode= "000" ) 
	else std_logic_vector (signed(A)+signed(B)) when (mode= "001" ) 
	else std_logic_vector (signed(A)-signed(B)) when (mode= "010" ) 
	else std_logic_vector ( -signed(A))         when (mode= "011" ) 
	else A and B                                when (mode= "100" ) 
	else A or B                                 when (mode= "101" ) 
	else A xor B                                when (mode= "110" ) 
	else not A; 
end architecture ALU_concurrente; 
-----------------------------------------------
-- ALU diseñada mediante un bloque process. Fichero: ALU_bloqueProcess.vhd 
library IEEE; 
use IEEE.std_logic_1164.all; 
use IEEE.numeric_std.all; 
use work.ALU_CONSTANTS.all; 

architecture ALU_bloqueProcess of ALU is 
begin 
	process (A, B, mode) is 
	begin 
		case mode is 
			when "000" = > C <= std_logic_vector(signed(A)+signed(A)); 
			when "001" = > C <= std_logic_vector(signed(A)+signed(B)); 
			when "010" = > C <= std_logic_vector(signed(A)-signed(B)); 
			when "011" = > C <= std_logic_vector(-signed(A)); 
			when "100" = > C <= A and B; 
			when "110" = > C <= A or B; 
			when "110" = > C <= A xor B; 
			when others => C < =not A; 
		end case; 
	end process; 
end architecture ALU_bloqueProcess;
```
### 4.7.2. Programación del banco de pruebas
Debe seleccionarse un conjunto de vectores de test, por ejemplo, atendiendo a los criterios siguientes: 
- Se escogen valores de los operandos entorno al cero. Por ejemplo: -2, -1, 0, 1 y 2. 
- Se escogen valores de los operandos en el límite inferior de su rango. Por ejemplo, si ``MIN_NEG_DATA`` representa el valor mínimo que puede tomar el operando, entonces se escogen los valores`` MIN_NEG_DATA, ... , MIN_NEG_DATA+4 `` para cada uno de los operandos. 
- Se escogen valores de los operandos en el límite superior de su rango. Si ``MAX_POS_DATA`` representa el valor máximo que puede tomar el operando, entonces se escogen los valores ``MAX_POS_DATA-4, ... , MAX_POS_DATA`` para cada uno de los operandos. 
- Finalmente, se escogen algunos valores "al azar", más o menos distribuidos uniformemente en el rango de los operandos.
```vhdl
-- Definición de constantes globales del banco de pruebas de la ALU 
--Fichero: TB_ALU_CONSTANTS.vhd 
use work.ALU_CONSTANTS.all; 

package TB_ALU_CONSTANTS is 
	constant SEL_MAX : integer := 2**SEL_BITS - 1; 
	constant MAX_POS_DATA : integer := 2**(WIDTH-1) - 1; 
	constant MIN_NEG_DATA : integer := -2**(WIDTH-1); 
	constant DELAY : time := 10 ns; 
end package TB_ALU_CONSTANTS; 
-------------------------------------------
-- Banco de pruebas para la ALU 
-- Fichero: TB_ALU.vhd 
library IEEE; use IEEE.std_logic_1164.all; 
use IEEE.numeric_std.all; 
use work.ALU_CONSTANTS.all; 
use work.TB_ALU_CONSTANTS.all; 

entity TB_ALU is
end entity TB_ALU; 

architecture TB_ALU of TB ALU is 
	signal A,B,C : std_logic_ vector (WIDTH-1 downto 0); 
	signal mode : std_logic_vector (SEL_BITS-1 downto 0); 
	
	component ALU is 
	port ( C : out std_logic_ vector (WIDTH-1 downto 0); 
		   A, B : in std_logic_ vector (WIDTH-1 downto 0); 
		   mode : in std_logic_vector (SEL_BITS-1 downto 0) ); end component ALU;

-- Procedure que calcula C (expectec_C) y lo compara con el valor de C que se pasa como argumento (actual_C) 
-- Si ambos valores no coinciden, se muestra un mensaje y se incrementa el contador de errores (error_count) 
procedure check_ALU 
	( i, j, k : in integer; 
	  actual_C : in std_logic_vector (WIDTH-1 downto 0);
	  error_count : inout integer ) is 
	variable expected_C : integer; 
begin 
	 case k is
		when 0      => expected_C := i*2;
		when 1      => expected_C := i+j;
		when 2      => expected_C := i-j;
		when 3      => expected_C := -i;
		when 4      => expected_C := TO_INTEGER(signed( 
						std_logic_vector(TO_SIGNED(i,WIDTH)) and 
						std_logic_vector(TO_SIGNED(j ,WIDTH)) ));
		when 5      => expected_C := TO_INTEGER(signed( 
						std_logic_vector(TO_SIGNED(i,WIDTH)) or 
						std_logic_vector(TO_SIGNED(j ,WIDTH)) ));
		when 6      => expected_C := TO_INTEGER(signed( 
						std_logic_vector(TO_SIGNED(i,WIDTH)) xor 
						std_logic_vector(TO_SIGNED(j ,WIDTH)) ));
		when others => expected_C := TO_INTEGER(signed( 
						not std_logic_vector(TO_SIGNED(i,WIDTH)) ));
end case; 
expected_C := TO_INTEGER(TO_SIGNED(expected_C,WIDTH) ); -- Trunca el resultado a WIDTH bits
assert( expected_C = TO_INTEGER(signed(actual_C)) ) 
	report "ERROR. Ops: " & integer'image(i) & "," & integer'image(j) &
		" , Operacion: " & integer'image(k) &
		" , resultado esperado: " & integer'image(expected_C) &
		" , resultado actual: " & 
		integer'image(TO_INTEGER(signed(actual_C))) &
		" en el instante " & time'image(now); 
	if (expected_C /= TO_INTEGER(signed(actual_C))) then error_count := error_count + 1; 
	end if; 
end procedure check_ALU; 
-- Fin de la definición del procedure
-------------------------------------------
begin 
	UUT : component ALU port map (e, A, B, mode); 

-- bloque process para generar los vectores de test y comprobar el resultado 
	main : process is 
		variable error_count : integer := 0; 
	begin 
		report "Comienza la simulación";
		-- Vectores de test: operandos con valor próximo a cero
		for i in -2 to 2 loop 
			for j in -2 to 2 loop 
				for k in 0 to SEL_MAX loop 
					A <= std_logic_vector(TO_SIGNED( i,WIDTH) );
					b <= std_logic_vector(TO_SIGNED(j ,WIDTH) ); 
					mode <= std_logic_vector(TO_SIGNED(k,SEL_BITS)); 
					wait for DELAY; 
					check_ALU(i, j, k, e, error_count);
				end loop; 
			end loop; 
		end loop; 
		
		-- Vectores de test: operandos con valor próximo al mínimo 
		for i in MIN_NEG_DATA to MIN_NEG_DATA+4 loop 
			for j in MIN_NEG_DATA to MIN_NEG_DATA+4 loop 
				for k in 0 to SEL_MAX loop 
					A <= std_logic_vector(TO_SIGNED( i,WIDTH) ); 
					b <= std_logic_vector(TO_SIGNED(j ,WIDTH) ); 
					mode <= std_logic_vector(TO_SIGNED(k,SEL_BITS)); 
					wait for DELAY; 
					check_ALU(i, j, k, e, error_count); 
				end loop;
			end loop; 
		end loop; 
		
		-- Vectores de test: operandos con valor próximo al máximo 
		for i in MAX_POS_DATA-4 to MAX_POS_DATA loop 
			for j in MAX_POS_DATA-4 to MAX_POS_DATA loop 
				for k in O to SEL_MAX loop 
					A <= std_logic_vector(TO_SIGNED(i,WIDTH)); 
					b <= std_logic_vector(TO_SIGNED(j ,WIDTH) ); 
					mode <= std_logic_vector(TO_SIGNED(k,SEL_BITS)); 
					wait for DELAY; 
					check_ALU ( i, j, k, e, error_ count); 
				end loop; 
			end loop; 
		end loop;

		-- Vectores de test: operandos con valores al azar 
		for i in O to 9 loop 
			for j in O to 9 loop 
				for k in O to SEL_MAX loop 
					A <= std_logic_vector(TO_SIGNED(41 *i-273,WIDTH)); 
					b <= std_logic_vector(TO_SIGNED(89*j-384,WIDTH)); 
					mode <= std_logic_vector(TO_SIGNED(k,SEL_BITS) ); 
					wait for DELAY; 
					check_ALU(41 *i-273, 89*j-384, k, e, error_count); 
				end loop; 
			end loop; 
		end loop; 
		
		wait for DELAY; 
		-- Informe mostrando el resultado del test 
		if (error_count=0) then 
			report "Finaliza la simulación sin errores"; 
		else 
			report "Finaliza la simulación:" & integer'image(error_count) & "errores"; 
		end if; 
		wait; -- Termina la simulación 
	end process main; 
end architecture TB_ALU;
```
# TEMA 5 REGISTROS Y MEMORIAS
## 5.2. REGISTRO DE 4 BITS
En la figura se muestra un registro de 4 bits. El registro tiene una entrada de reloj, una entrada de reset síncrono (rst), cuatro entradas de datos (13 , 12 , 11 , 10 ) y cuatro salidas de datos (Q3 , Q2 , Q1 , Q0 ). Si la señal de reset vale '1' cuando se produce el flanco de subida del reloj, entonces se almacena en el registro el valor "0000". Si la señal de reset vale 'O' cuando se produce el flanco de subida de la señal de reloj, entonces el registro se carga con los datos de entrada.
![](img/Pasted%20image%2020250505141807.png)
### 5.2.1. Descripción del comportamiento
Una forma de diseñar el registro es mediante la descripción de su estructura, usando 4 flip-flops. Otra posibilidad, es describirlo indicando cuál es su comportamiento.
```vhdl
-- Registro de 4 bits con reset síncrono 
-- Fichero: Reg4.vhd 
library IEEE; 
use IEEE.std_logic_1164.all; 

entity Reg4 is 
	port ( Q : out std_logic_vector(3 downto 0); 
		   I : in std_logic_vector (3 downto 0); 
		   clk, rst : in std_logic ); 
end entity Reg4; 

architecture Reg4 of Reg4 is 
begin 
	process (clk) 
	begin 
		if rising_edge(clk) then 
			if(rst = '1') then 
				Q <= "0000"; 
			else 
				Q <= I; 
			end if; 
		end if; 
	end process; 
end architecture Reg4;
```
### 5.2.2. Banco de pruebas
El programa de test aplica los cuatro vectores de test siguientes: reset, carga "1111" , carga "1010" y carga  "0000" .
```vhdl
-- Banco de pruebas del registro de 4 bits. Fichero: bp_Reg4.vhd 
library IEEE;
use IEEE.std_logic_1164.all; 

entity bp_Reg4 is 
end entity bp_Reg4; 

architecture bp_Reg4 of bp_Reg4 is 
	constant PERIODO : time := 10 ns; -- Periodo reloj
	signal Q : std_logic_vector(3 signal downto 0); -- Salidas UUT
	signal clk : std_logic := '0'; -- Entradas UUT port
	signal I : std_logic_vector(3 signal downto 0); 
	signal rst : std_logic; 
	
	component Reg4 is      
		port ( Q : out std_logic_vector(3 downto 0); 
			   I : in std_logic_vector(3 downto 0); 
			   clk, rst : in std_logic ); 
	end component Reg4; 
	
begin 
	uut : component Reg4 port map (Q, I, clk, rst); 
	clk <= not clk after (PERIODO/2); 
	gen_vec_test : process is 
	begin 
		report "Comienza la simulación"; 
		
		I <= "1111"; -- Reset 
		rst <= '1'; 
		wait until rising_edge(clk); 
		wait for (PERIODO/2); 
		
		I <= "1111"; -- Carga 1111 
		rst <= '0'; 
		wait until rising_edge(clk); 
		wait for (PERIODO/2); 
		
		I <= "1010"; --Carga 1010 
		rst <= '0'; 
		wait until rising_edge(clk); 
		wait for (PERIODO/2); 
		
		I <= "0000"; -- Carga 0000 
		rst <= '0'; 
		wait until rising_edge(clk); 
		wait for (PERIODO/2); 
		
		report "Finaliza la simulación"; 
		wait; -- Final del bloque process 
	end process gen_vec_test; 
end architecture bp_Reg4;
```
Tras aplicar cada uno de estos vectores de test, se ejecutan las dos sentencias wait siguientes:
```vhdl
wait until rising_edge(clk); 
wait for (PERIODO/2);
```
La primera de ellas espera hasta que se produzca el siguiente flanco de subida de la señal de reloj. La segunda espera durante la mitad del periodo de la señal de reloj. En general, la sentencia
``wait until condición; ``
espera hasta que la condición cambie de valer *false* a valer *true*. Si la condición inicialmente vale *true*, entonces la sentencia **wait** espera hasta que la condición se haga *false* y posteriormente vuelva a valer *true*.
## 5.3. REGISTRO MULTIFUNCIÓN
El registro descrito anteriormente tenía una única entrada de control: la entrada de reset síncrono. Un registro más general tiene más entradas de control, tales como carga paralelo (*Ld*), desplazamiento hacia la derecha (*Shr*) y hacia la izquierda (*Shl*). Asimismo, tiene las entradas de datos correspondientes a los desplazamientos (*Shr_In*, *Shl_In*).
![](img/Pasted%20image%2020250505143411.png)
### 5.3.1. Descripción del comportamiento
```vhdl
-- Registro mnltifunción de 4 bits 
-- Fichero: Reg4mf.vhd 
library IEEE; 
use IEEE.std_logic_1164.all; 

entity Reg4mf is 
	port ( Q : out std_logic_vector(3 downto 0); 
		   I : in std_logic_vector(3 downto 0); 
		   Shr_In, Shl_In : in std_logic; 
		   Ld, Shr, Shl : in std_logic; 
		   clk, rst : in std_logic ); 
end entity Reg4mf; 

architecture Reg4mf of Reg4mf is 
	signal R : std_logic_vector(3 downto 0); 
begin 
	Q <= R; 
	process (clk) 
	begin 
		if rising_edge(clk) then 
			if(rst = '1') then 
				R <= "0000"; 
			elsif (Ld = '1') then 
				R <= I; 
			elsif (Shr = '1') then
				R(3) <= Shr_In; 
				for index in 0 to 2 loop 
					R(index) <= R(index+1); 
				end loop; 
			elsif (Shl = '1') then 
				R(0) <= Shl_In; 
				for index in 0 to 2 loop 
					R(index+1) <= R(index); 
				end loop; 
			end if; 
		end if; 
	end process; 
end architecture Reg4mf;
```
Se emplea una sentencia **if** para fijar las prioridades entre las diferentes entradas de control: *rst* tiene la máxima prioridad, seguido de *Ld*, a continuación *Shr* y finalmente *Shl*.

Los desplazamientos se describen empleando sentencias for. Por ejemplo, la sentencia siguiente:
```vhdl
for index in 0 to 2 loop 
	R(index) <= R(index+1); 
end loop;
```
es equivalente a escribir:
```vhdl
R(0) <= R(1); 
R(1) <= R(2); 
R(2) <= R(3);
```
==Debe tenerse en cuenta que estas sentencias de asignación a señal producen un cambio en el valor de la señal transcurrido un retardo $\delta$, empleándose el valor actual de las señales para calcular los nuevos valores.==

En el diseño del registro de 4 bits mostrado en la Sección 5.2, se empleó la señal Q del puerto de salida para almacenar la palabra de 4 bits contenida en el registro. Sin embargo, en el diseño del registro multifunción, se emplea la señal R para almacenar la palabra de 4 bits. La razón para definir la señal R es que las operaciones de desplazamiento requieren leer la palabra almacenada y un puerto de salida no puede ser leído.
Dado que en el puerto de salida del registro Q debe obtenerse en todo momento el valor almacenado, R, es necesario copiar en todo momento el valor de la señal R en la señal Q.
`Q <= R`
que se ejecuta cada vez que cambia el valor de R, asignando transcurrido un tiempo infinitesimal $\delta$ este nuevo valor a la señal Q.

Obsérvese que esta sentencia no ha sido incluida dentro de ningún bloque **process**. Recuérdese que este tipo de sentencias de asignación a señal, que se encuentran en la **architecture** fuera de los bloques **process**, se denominan *sentencias concurrentes de asignación a señal*.
Puede considerarse que una sentencia concurrente de asignación a señal constituye por sí misma un bloque process, que se ejecuta concurrentemente con el resto de bloques process.
La sentencia:
`Q <= R`
es equivalente al bloque **process**:
```vhdl
process (R) 
begin 
	Q <= R; 
end process;
```
Cada vez que cambia el valor de la señal R, se ejecuta el bloque **process**, con lo cual el valor de Q es actualizado al nuevo valor de R transcurrido un tiempo $\delta$ (delta).
### 5.3.2. Banco de pruebas
```vhdl
-- Banco de pruebas del registro multifunción 
-- Fichero: bp_Reg4mf.vhd 
library IEEE; 
use IEEE.std_logic_1164.all;

entity bp_Reg4mf is 
end entity bp_Reg4mf; 

architecture bp_Reg4mf of bp_Reg4mf is 
	constant PERIODO : time := 10 ns; 
	signal Q : std_logic_vector(3 downto 0); 
	signal clk : std_logic := '0'; 
	signal I : std_logic_vector(3 downto 0); 
	signal rst : std_logic; 
	signal Shr_In, Shl_In : std_logic; 
	signal Ld, Shr, Shl : std_logic; 
	
	component Reg4mf is 
		port ( Q : out std_logic_vector(3 downto 0); 
			   I : in std_logic_vector ( 3 downto 0); 
			   Shr_In, Shl_In : in std_logic; 
			   Ld, Shr, Shl : in std_logic; 
			   clk, rst : in std_logic ); 
	end component Reg4mf; 
begin
	-- Instanciar y conectar UUT 
	uut : component Reg4mf port map 
		(Q, I, Shr_In, Shl_In, Ld, Shr, Shl, clk, rst); 
	clk <= not clk after (PERIODO/2); 
	gen_vec_test : process is 
		variable numTest : integer := 0; 
	begin
		 report "Comienza la simulación"; 
		 -- Reset 
		 I <= "1111"; Shr_In <= '1'; Shl_In <= '1'; 
		 rst <= '1'; Ld <= '1'; Shr <= '1'; Shl <= '1'; 
		 wait until rising_edge(clk); 
		 wait for (PERIODO/2); 
		 numTest := numTest + 1; 
		 assert ( Q = "0000") 
			 report "Error vector " & integer' image(numTest);
		-- Carga 1111 
		I <= "1111"; Shr_In <= '0'; Shl_In <= '0'; 
		rst < = '0'; Ld < = '1'; Shr < = '1'; Shl < ='1';
		wait until rising_edge(clk); 
		wait for (PERIODO/2); 
		numTest := numTest + 1; 
		assert ( Q = "1111") 
			report "Error vector " & integer' image(numTest);
...
		-- Desplazamiento Derecha, Carga serie '1' 
		I <= "1111"; Shr_In <= '1'; Shl_In <= '1'; rst <= '0';
		Ld <= '0'; Shr <= '1'; Shl <= '0';
		wait until rising_edge(clk); 
		wait for (PERIOD0/2); 
		numTest := numTest + 1; 
		assert ( Q = "1001" ) 
			report "Error vector " & integer' image(numTest);
...
		report "Finaliza la simulación"; 
		wait; -- Final del bloque process
	end process gen_vec_test; 
end architecture bp_Reg4mf;
```
## 5.4. REGISTRO DE DESPLAZAMIENTO
En aquellos casos en que sólo se requiera la operación de desplazamiento y la entrada serie de bits, puede emplearse un circuito más sencillo.
![](img/Pasted%20image%2020250505151324.png)El registro de desplazamiento de 32 bits tiene una entrada de control (*Shr*), una entrada de datos (*Shr_in*), una entrada de reset síncrono (*rst*) y una salida paralelo de 32 bits (*Q*). En la tabla mostrada en la parte derecha se describe su operación. Si cuando se produce el flanco de subida del reloj la entrada de control *Shr* vale '1', entonces el registro desplaza su contenido una posición hacia la derecha y carga *Shr_in* en el bit situado más a la izquierda.
### 5.4.1. Descripción del comportamiento
```vhdl
-- Registro de desplazamiento de 32 bits 
-- Fichero: RegDesp32.vhd 
library IEEE; 
use IEEE.std_logic_1164.all; 

entity RegDesp32 is 
	port ( Q : out std_logic_vector(31 downto 0); 
		   Shr, Shr_in : in std_logic; clk, rst : in std_logic );
end entity RegDesp32; 

architecture RegDesp32 of RegDesp32 is 
	signal R : std_logic_ vector ( 31 downto 0); 
begin 
	process (clk) 
	begin 
		if rising_edge(clk) then 
			if (rst = '1') then 
				R <= X"00000000" ; 
			elsif (Shr = '1') then 
				R(31) <= Shr_in; 
				for index in 0 to 30 loop 
					R(index) <= R(index+1); 
				end loop; 
			end if; 
		end if; 
	end process; 
	Q <= R; 
end architecture RegDesp32;
```
El bucle for se expande:
```vhdl
R(31) <= Shr_in; 
for index in 0 to 30 loop 
	R(index) <= R(index+1);
end loop;
```
es equivalente a:
```vhdl
R(31) <= Shr_in;
R(0) <= R(1);
R(1) <= R(2);
...
R(30) <= R(31);
```
### 5.4.2. Banco de pruebas
```vhdl
-- Banco de pruebas del registro de 32 bits. Fichero: bp_RegDesp32.vhd 
library IEEE; 
use IEEE.std_logic_1164.all; 

entity bp_RegDesp32 is 
end entity bp_RegDesp32; 

architecture bp_RegDesp32 of bp_RegDesp32 is 
	constant PERIODO : time : = 10 ns; 
	signal Q : std_logic_vector(31 downto 0); 
	signal clk : std_logic := '0'; 
	signal Shr : std_logic; 
	signal Shr in : std_logic; 
	signal rst : std_logic; 
	
	component RegDesp32 is 
		port ( Q : out std_logic_vector(31 downto 0); 
			   Shr, Shr_in : in std_logic; ç
			   clk, rst : in std_logic ); 
	end component RegDesp32; 
	
begin 
	uut : component RegDesp32 port map (Q, Shr, Shr_in, clk, rst);
	clk < = not clk after (PERIODO/2); 
	
	gen_vec_test : process is
	begin 
		report "Comienza la simulación"; 
		-- Reset 
		rst < = '1'; Shr < = '1'; Shr_in < = '1'; 
		wait until rising_edge(clk); 
		wait for (PERIODO/2); 
		-- Carga serie 16 bits '1' 
		rst < = '0'; Shr < = '1'; Shr_in < = '1';
		for index in O to 15 loop 
			wait until rising_edge(clk); 
		end loop; 
		wait for (PERIODO/2); 
		assert ( Q = X"FFFF0000") report "Fallado Q=FFFF0000";
		-- Carga serie 16 bits '0'  
		rst < = '0'; Shr <= '1'; Shr_in < = '0';
		for index in 0 to 15 loop 
			wait until rising_edge(clk); 
		end loop;  
		wait for (PERIODO/2);
		assert ( Q = X"0000FFFF") report "Fallado Q=0000FFFF";
		Shr < = '0'; 
		report "Finaliza la simulación"; 
		wait; -- Final del bloque process 
	end process gen_vec_test; 
end architecture bp_RegDesp32;
```
En primer lugar, el programa de test resetea el circuito. A continuación, pone las señales *Shr* y *Shr_in* al valor '1' y espera durante 16 ciclos de reloj. Con ello, se realizan 16 desplazamientos hacia la derecha, introduciéndose 16 bits '1' por la parte izquierda del registro. El valor almacenado resultante es X"FFFF0000". A continuación, el programa de test pone la señal *Shr_in* al valor '0' y espera durante otros 16 ciclos de reloj. El valor almacenado resultante es X"0000FFFF" . Finalmente, el programa de test pone la señal *Shr* al valor '0' y finaliza el bloque **process** en el que se aplican los vectores de test.
### 5.4.3. Banco de pruebas con acceso a fichero
```vhdl
-- Banco de pruebas del registro de 32 bits con acceso a fichero 
-- Fichero: bp_RegDesp32fich.vhd 
library IEEE; 
use IEEE.std_logic_1164.all; 
use std.textio.all; 
entity bp_RegDesp32 is 
end entity bp_RegDesp32; 

architecture bp_RegDesp32 of bp_RegDesp32 is 
	constant PERIODO : time : = 10 ns; 
	signal Q : std_logic_vector(31 downto 0); 
	signal clk : std_logic := '0'; 
	signal Shr : std_logic; 
	signal Shr in : std_logic; 
	signal rst : std_logic; 
	
	component RegDesp32 is 
		port ( Q : out std_logic_vector(31 downto 0); 
			   Shr, Shr_in : in std_logic; ç
			   clk, rst : in std_logic ); 
	end component RegDesp32; 
	
begin 
	uut : component RegDesp32 port map (Q, Shr, Shr_in, clk, rst);
	clk < = not clk after (PERIODO/2);
	
	gen_vec_test : process is 
		file fichVectores : text; 
		variable inputLinea : line; 
		variable inputBi t : bit; 
	begin 
		report "Comienza la simulación"
		-- Reset 
		rst <= '1'; Shr <= '1'; Shr _in < = '1';
		wait until rising_edge(clk);  
		wait for (PERIOD0/2); 
		-- Carga de vectores de test desde fichero 
		rst <= '0'; 
		file_open(fichVectores, "vectores.txt", read_mode); 
		while not endfile(fichVectores) loop 
			readline(fichVectores, inputLinea); 
			for i in inputLinea' range loop 
				read(inputLinea, inputBit); 
				if inputBi t = '1' then 
					Shr_in < = '1'; 
				else 
					Shr_in < = '0'; 
				end if; 
				wait until rising_edge(clk); 
			end loop; -- bucle for 
		end loop; -- bucle while 
		file_close(fichVectores); 
		
		Shr <= '0'; 
		wait until rising_edge(clk); report "Finaliza la simulación"; 
		wait; -- Final del bloque process 
	end process gen_vec_test; 
end architecture bp_RegDesp32fich;
```
El código muestra un banco de pruebas en el cual se van leyendo los bits de carga serie (*Shr_in*) de un fichero. Para ello, se usa el paquete ``std.textio.all``, en el cual se define el tipo **file** y los subprogramas (procedimientos y funciones) asociados que permiten leer de ficheros: **file_open(), file_close(), endfile(), readline()** y **read()**.
En primer lugar, el banco de pruebas abre el fichero usando una llamada al procedimiento **file_open()**. Este procedimiento tiene tres parámetros: el identificador del fichero, el nombre del fichero y el modo de acceso. El modo de acceso puede tomar tres valores: **read_mode**, **write_mode** y **append_mode**. La sentencia 
``file_open(fichVectores, "vectores.txt", read_mode);`` 
abre en modo lectura el fichero llamado "``vectores.txt``", asociándole el identificador ``fichVectores``.
Antés de empezar a leer de fichero, el banco de pruebas resetea el registro. A continuación, pone la señal de reset a '0' y, dado que la señal de control del desplazamiento (*Shr*) tiene el valor '1', comienzan a introducirse bits en el registro. Los bits son leídos del fichero cuyo identificador es ``fichVectores``. La lectura de los bits se realiza mediante el bucle **while**.
## 5.5. REGISTER FILE
Un register file es un módulo compuesto de varios registros, y de la lógica de acceso a ellos para lectura y escritura. Por ejemplo, un register file de tamaño 4 x 32, contiene 4 registros, cada uno de los cuales tiene 32 bits.
![](img/Pasted%20image%2020250505160511.png)
Los registros tienen una entrada de datos de 32 bits y una entrada de control para carga paralelo (*Ld*). También disponen de una entrada de reset síncrono (*rst*). La entrada de reset del register file está conectada a la entrada de reset de cada uno de los registros. Finalmente, el register file tienen una salida de 32 bits.
Además de los cuatro registros de 32 bits, el register file está compuesto por dos decodificadores 2:4 con entrada enable, uno para escritura (situado en la parte izquierda) y otro para lectura (situado en la parte derecha), y por cuatro buffers triestado.
En este caso, el propósito de los buffers triestado es permitir que las salidas de los registros se conecten al bus *R_data*, evitando así tener que utilizar un multiplexor, que es un circuito más grande y lento. Esta estructura de conexión al bus a través de buffers triestado funciona correctamente cuando se garantiza que en todo momento no hay más de un buffer que tenga una salida diferente de alta impedancia ( 'Z'). El decodificador de lectura garantiza este comportamiento.
### 5.5.1. Registro triestado
Puede considerarse que el registro y su buffer triestado constituyen a su vez un registro con una nueva entrada: *OE* ( *Output Enable*). En función del valor que se asigne a la entrada *OE*, puede obtenerse en la salida del registro triestado, o bien el valor almacenado (si *OE*='1'), o bien alta impedancia (si *OE*='0').
![](img/Pasted%20image%2020250505161608.png)
```vhdl
-- Registro de 32 bits con output enable 
-- Fichero: Reg32_0E.vhd 
library IEEE; 
use IEEE.std_logic_1164.all; 

entity Reg32_OE is 
	port ( Q : out std_logic_vector(31 downto 0); 
		   I : in std_logic_vector(31 downto 0); 
		   Ld, DE : in std_logic; 
		   clk, rst : in std_logic); 
end entity Reg32_OE; 

architecture Reg32_OE of Reg32_DE is
	signal R : std_logic_vector(31 downto 0); 
begin 
	regProc: process (clk) 
	begin 
		if rising_edge(clk) then 
			if (rst = '1') then 
				R <= (others => '0'); 
				-- Igual que escribir R <= X"00000000", pero asi no especifico el num de bits 
				--others solo se puede usar en sentencias de asignación, no como parte de una condición
			elsif (Ld = '1 ') then 
				R <= I; 
			end if; 
		end if; 
	end process regProc; 
	
	outputProc: process (R, OE) 
	begin 
		if (OE='1') then 
			Q <= R; 
		else 
			Q <= (others => 'Z'); 
		end if; 
	end process outputProc; 
end architecture Reg32_OE;
```
La descripción consta de dos bloques **process**: ``regProc`` describe el comportamiento de reset síncrono y almacenamiento, mientras que ``outputProc`` describe la lógica combinacional del comportamiento como buffer triestado del registro.
### 5.5.2. Descripción estructural del register file
Empleando los componentes diseñados en temas anteriores, puede realizarse la descripción estructural del register file. Se han definido ocho señales internas al register file, que corresponden con las salidas del decodificador de escritura (``W_d3, W_d2, W_d1, W_d0``) y con las salidas del decodificador de lectura (``R_d3, R_d2, R_d1, R_d0``).
```vhdl
-- Register fil e 4x32. 
-- Descripción estructural 
-- Fichero: RegFile4x32_estruc.vhd 
library IEEE; 
use IEEE.std_logic_1164.all; 

entity RegFile4x32 is 
	port ( R_data : out std_logic_vector(31 downto 0); 
		   W_data : in std_logic_vector(31 downto 0); 
		   R_addr, W_addr : in std_logic_vector(1 downto 0);
		   R_en, W_en : in std_logic; 
		   clk, rst : in std_logic ); 
end entity RegFile4x32; 

architecture RegFile4x32_estruc of RegFile4x32 is 
	component Dcd2x4 is 
		port ( d3, d2, d1, d0 : out std_logic;
			   i1, i0 : in std_logic;
			   en : in std_logic );
	end component Dcd2x4; 
	
	component Reg32_OE is
		port ( Q : out std_logic_vector(31 downto 0); 
			   I : in std_logic_vector(31 downto 0); 
			   Ld, DE : in std_logic; 
			   clk, rst : in std_logic ) ; 
	end component Reg32_OE; 
	
	signal W_d3, W_d2, W_d1, W_dO : std_logic; 
	signal R_d3, R_d2, R_d1, R_dO : std_logic; 
begin 
	R_Dcd : Dcd2x4 port map (R_d3, R_d2, R_d1, R_d0, R_addr(1), R_addr(0), R_en);
	W_Dcd : Dcd2x4 port map (W_d3, W_d2, W_d1, W_d0, W_addr(1), W_addr(0), W_en); 
	Reg0 : Reg32_OE port map (R_data, W_data, W_d0, R_d0, clk, rst ); 
	Reg1 : Reg32_OE port map (R_data, W_data, W_d1, R_d1, clk, rst ); 
	Reg2 : Reg32_OE port map (R_data, W_data, W_d2, R_d2, clk, rst ); 
	Reg3 : Reg32_OE port map (R_data, W_data, W_d3, R_d3, clk, rst ); 
end architecture RegFile4x32_estruc;
```
### 5.5.3. Drivers y función de resolución
Obsérvese que en el bloque **process** ``outputProc``, del registro *Reg32_0E*, se escribe en el puerto de salida *Q*. En la descripción del register file, este puerto de salida es mapeado con la señal *R_data*. Dado que cada instancia del componente *Reg32_0E* da lugar a una instancia del bloque **process** *outputProc*, la señal *R_data* es escrita en el register file desde cuatro bloques **process**.
el valor de una señal está determinado en todo momento por el valor de sus *drivers*. Si un bloque **process** contiene una sentencia de asignación a señal, entonces el bloque **process** tendrá un *driver* para esa señal. En el caso del register file, la señal *R_data* tiene cuatro *drivers*.
Por la forma en que se ha realizado el diseño del register file, en cada instante a lo sumo uno de los drivers escribe el valor '0' ó '1' en la señal, mientras que los demás drivers escriben el valor 'Z'. En consecuencia, en cada instante se escriben cuatro valores en la señal, tres de los cuales son 'Z', y el cuarto es '0', '1' ó 'Z'.
Como se explicó en la **Sección 3.4**, el simulador dispone de un método para decidir qué valor asignar a la señal cuando ésta tiene *drivers* con diferentes valores. El método consiste en disponer de una *función de resolución*, cuya entrada son los múltiples valores de los *drivers* y que devuelve sólo uno, que es el que se asigna a la señal.
Cuando hay varios drivers para una misma señal, el simulador automáticamente llama a la función de resolución asociada con el tipo de dato de la señal. En el caso de la señal *R_data*, como es del tipo **std_logic_vector**, el simulador llama a la función de resolución de ese tipo, que se encuentra definida en el paquete ``IEEE.std_logic_1164.all``. Esta función de resolución devuelve '0' si uno de los *drivers* es '0' y los demás 'Z'. Devuelve '1' si uno de los *drivers* es '1' y los demás 'Z'. Sin embargo, si unos *drivers* valen '0' y otros valen '1', entonces la función de resolución devuelve 'X', cuyo significado es "valor desconocido".
### 5.5.4. Banco de pruebas del register file
```vhdl
-- Banco de pruebas del register file. Fichero: bp_RegFile4x32.vhd 
library IEEE; 
use IEEE.std_logic_1164.all; 
use std.textio.all; ç

entity bp_regFile4x32 is 
	constant PERIODO : time := 10 ns;
end entity bp_regFile4x32;  

architecture bp_regFile4x32 of bp_regFile4x32 is 
	signal R_data : std_logic_vector(31 downto 0); 
	signal W_data : std_logic_vector(31 downto 0); 
	signal R_addr, W_addr : std_logic_vector(1 downto 0); 
	signal R_en, W_en : std_logic; 
	signal rst : std_logic; 
	signal clk : std_logic := '0'; 
	
	component RegFile4x32 is 
		port ( R_data : out std_logic_vector(31 downto 0);
			   W_data : in std_logic_vector(31 downto 0);
			   R_addr, W_addr : in std_logic_vector(1 downto 0); 
			   R_en, W_en : in std_logic; clk, rst : in std_logic ) ; 
	end component RegFile4x32; 
begin 
	uut : component RegFile4x32 port map 
	(R_data, W_data, R_addr, W_addr, R_en, W_en, clk, rst); 
	
	clk <= not clk after (PERIOD0/2); 
	
	gen_vec_test : process is 
		file fichVectores : text; 
		variable inputLinea : line; 
		variable inputBit : bit; 
		constant numBits : integer := 38; -- Num bits menos 1
		variable aux : std_logic_vector(numBits downto 0);
		
	begin 
		report "Comienza la simulación"; 
		-- Carga de vectores de test desde fichero
		file_open(fichVectores, "vectores. txt", read_mode ); 
		while not endfile(fichVectores) loop 
		
			-- Lectura desde fichero 
			readline(fichVectores, inputLinea); 
			for i in numBits downto 0 loop 
				read(inputLinea, inputBit); 
				if inputBit = '1' then 
					aux (i) := '1' ; 
				else 
					aux (i) := '0' ; 
				end if; 
			end loop; -- bucle for
			-- Asigna valor a W_data, W_addr, W_en, R_addr, R_en
			rst <= aux(38); 
			W_data <= aux(37 downto 6); 
			W_addr <= aux(5 downto 4); 
			W_en <= aux(3); 
			R_addr <= aux(2 downto 1); 
			R_en <= aux(0); 
			wait for PERIODO; 
		end loop; -- bucle while 
		file_close(fichVectores); 
		wait until rising_edge(clk); 
		report "Finaliza la simulación"; 
		wait; -- Final del bloque process 
	end process gen_vec_test; 
end architecture bp_regFile4x32;
```
El código es un banco de pruebas para el register file, que lee los vectores de test de un fichero. Cada una de las líneas de este fichero (*vectores.txt*) consta de una palabra de 39 bits.
Interpretación de cada línea del fichero vectores.txt:
![](img/Pasted%20image%2020250505165753.png)
Obsérvese que la línea leída del fichero es asignada a la variable ``aux``, del tipo **std_logic_vector**, que es definida dentro del bloque **process** ``gen_vec_test``. A continuación, descomponiendo esta palabra como se muestra en la figura, se asigna valor a los puertos de entrada del register file.
### 5.5.5. Descripción del comportamiento del register file
```vhdl
-- Register file 4x32. 
-- Descripción del comportamiento 
-- Fichero: RegFile4x32_comp.vhd 
library IEEE; 
use IEEE.std_logic_1164.all; 
use IEEE.std_logic_unsigned.all; 

entity RegFile4x32 is 
	port ( R_data : out std_logic_vector(31 downto 0);
		   W_data : in std_logic_vector(31 downto 0);
		   R_addr, W_addr : in std_logic_vector(1 downto 0);
		   R_en, W_en : in std_logic;
		   clk, rst : in std_logic );
end entity RegFile4x32;

architecture RegFile4x32_comp of RegFile4x32 is
	type regfile_type is
		array (= to 3) of std_logic_vector(31 downto 0);
	signal regfile: regfile_type;
begin
	W_process : process (clk)
	begin
		if rising_edge(clk) then
			if (rst ='1') then
				regfile(0) <= X"00000000";
				regfile(1) <= X"00000000";
				regfile(2) <= X"00000000";
				regfile(3) <= X"00000000";
			elsif (W_en = '1') then
				regfile(conv_integer(W_addr)) <= W_data;
			end if;
		end if;	
	end process W_process;
	R_process : process (R_addr, R_en, regfile)
	begin
		if (R_en ='1') then
			R_data <= regfile(conv_integer(R_addr));
		else
			R_data <= (others => 'Z');
		end if;
	end process R_process;
end architecture RegFile4x32_comp;
```
Un **array** es otra forma de declaración de tipo, en la cual el objeto está formado por un conjunto de elementos, todos del mismo tipo y accesibles mediante un índice. En la declaración anterior se indica que ``regfile_type`` consiste en consta de tres elementos, numerados de 0 a 3, del tipo **std_logic_vector** y con 32 bits.
El diseño del register file consta de dos bloques **process**. En el bloque **process** *W_process* se escribe en los registros, tanto en la operación de reset como en la operación normal de escritura, en la cual la dirección del registro viene determinada por el vector de dos bits *W_addr*. Obsérvese cómo se realiza la conversión del vector de dos bits a un entero, que es usado como índice del **array** regfile:
`regfile(conv_integer(W_addr)) <= W_data;`
La función **conv_integer**, incluida en ``IEEE.std_logic_unsigned.all``, realiza la conversión de **std_logic_vector** a **integer**.
## 5.6. BUS BIDIRECCIONAL Y MEMORIAS
Se pretende describir usando VHDL el comportamiento de dos unidades de memoria y un bus que conecta ambas. Para simplificar, se supone que las unidades de memoria tienen capacidad para almacenar una única palabra de N bits. Una de las memorias tiene capacidad de lectura y escritura. La otra sólo de lectura. Además de las dos memorias, se modela un bus de N líneas que puede leer de ambas memorias y escribir en la memoria que admite escritura.
### 5.6.1. Memoria de sólo lectura
Los puertos de la memoria son los siguientes: 
- Señal de entrada de 1 bit (``OE_n``). Cuando esta señal se pone a '0', habilita la operación de lectura de la memoria. Cuando está a '1 ', la operación de lectura está deshabilitada. 
- Vector de salida de N bits (``data``). Contiene el dato almacenado en memoria (palabra de N bits) una vez ejecutada la operación de lectura. Está a alta impedancia cuando la operación de lectura está deshabilitada (``OE_n`` = '1').
```vhdl
-- Fuente de datos unidireccional (lectura) 
-- Fichero: fuente Unidireccional.vhd 
library IEEE; 
use IEEE.std_logic_1164.all; 

entity fuenteUnidireccional is 
	generic ( WORD_SIZE integer := 8; -- Bits por palabra, por defecto 8 
			  READ_DELAY : time := 10 ns); -- RetaTdo en la lectura, por defecto 10 ns 
	port ( data : out std_logic_vector(WORD_SIZE-1 downto 0); --Datos de salida 
		   OE_n : in std_logic); -- Habilita lectura 
end entity fuenteUnidireccional; 

architecture fuenteUnidireccional of fuenteUnidireccional is 
begin 
	rom : process (OE_n) 
	begin 
		if (OE_n = '0') then 
			data <= ( 0 => '1', others = > '0') after READ_DELAY; 
		else 
			data <= (others => 'Z'); 
		end if; 
	end process rom; 
end architecture fuenteUnidireccional;
```
Se definen dos constantes **generic**: ``WORD_SIZE``, que contiene el número de bits de la palabra (*N*) y ``READ_DELAY``, que contiene el tiempo de retardo entre que se habilita la señal de lectura hasta que el dato está disponible.

La sentencia ``data<= (0 => '1', others => '0' ) after READ_DELAY; ``indica que debe asignarse al vector de señales ``data``, una vez transcurrido el retardo de tiempo ``READ_DELAY``, una palabra del tamaño de ``data``, con todos sus bits igual a '0' excepto el menos significativo, que debe valer '1' (es decir, ``data<= "00 ... 01" ;``). Esta palabra es la que se encuentra almacenada en la memoria y es la que se lee cada vez que se habilita la operación de lectura.
La sentencia ``data<= (others => 'Z');`` asigna al vector de señales data una palabra, con el mismo número de bits que data, con todos sus bits al valor 'Z' (alta impedancia).
### 5.6.2. Memoria de lectura y escritura
```vhdl
-- Fuente de datos bidireccional (lectura y escritura) 
-- Fichero: fuenteBidireccional.vhd 
library IEEE; 
use IEEE.std_logic_1164.all; 

entity fuenteBidireccional is 
	generic ( WORD_SIZE : integer := 8; -- Bits por palabra, por defecto 8 bits 
			  READ_DELAY : time := 10 ns; -- Retardo en la lectura, por defecto 10 ns
			  WRITE_DELAY : time := 10 ns); --Retardo en la escritura, por defecto 10 ns 
	port ( data : inout std_logic_vector(WORD_SIZE-1 downto 0); -- Señal bidireccional datos
		   OE_n : in std_logic; -- Habilita lectura 
		   WE_n : in std_logic ) ; -- Habilita escritura 
end entity fuenteBidireccional; 

architecture fuenteBidireccional of fuenteBidireccional is 
	signal data_stored : std_logic_vector(WORD_SIZE-1 downto 0); 
begin 
	ram : process (OE_n, WE_n, data) 
	begin 
		if ( OE_n = '0' ) then 
			data <= data_stored after READ_DELAY; 
		elsif ( WE_n = '0' ) then 
			data_stored <= data after WRITE_DELAY; 
		else data <= (others => 'Z'); 
		end if; 
	end process ram; 
end architecture fuenteBidireccional;
```
Como puede observarse en el código, los puertos de esta memoria son los indicados a continuación: 
- Señal de entrada de 1 bit (``OE_n``). Cuando esta señal se pone a '0', habilita la operación de lectura de la memoria. Cuando está a '1 ', la operación de lectura está deshabilitada. 
- Señal de entrada de 1 bit (``WE_n``). Cuando esta señal se pone a '0', habilita la operación de escritura en la memoria. Cuando está a '1', la operación de escritura está deshabilitada. 
- Vector de entrada y salida de N bits (``data``).
### 5.6.3. Bus bidireccional
```vhdl
-- Conexión de la fuente de datos bidireccional y la fuente unidireccional mediante un bus 
-- Fichero: bus.vhd 
library IEEE; 
use IEEE.std_logic_1164.all; 

entity tb_bus is 
	constant WORD_SZ : integer := 16; -- Bits por palabra 
	constant PERIOD  : time := 100 ns; -- Periodo ciclo reloj
end entity tb_bus;  

architecture tb_bus of tb_bus is  
	signal data : std_logic_vector(WORD_SZ-1 downto 0); -- Datos en el bus
	signal OE1_n : std_logic --Habilita lectura memoria lectura/escritura
	signal OE2_n : std_logic --Habilita lectura memoria solo lectura
	signal WE_n : std_logic --Habilita escritura
	signal writeData : std_logic_vector(WORD_SZ-1 downto 0); -- Datos a escribir
	
	component fuenteBidireccional is 
		generic ( WORD_SIZE integer := 8; -- Bits por palabra
				  READ_DELAY time := 10 ns; -- Retardo en la lectura 
				  WRITE_DELAY : time := 10 ns); --Retardo en la escritura 
		port ( data : inout std_logic_vector(WORD_SIZE-1 downto 0); -- Señal de datos bidireccional 
			   OE_n : in std_logic; -- Habilita lectura 
			   WE_n : in std_logic ); -- Habilita escritura 
	end component fuenteBidireccional; 
	
	component fuenteUnidireccional is 
		generic ( WORD_SIZE integer := 8; -- Bits por palabra 
				  READ DELAY time := 10 ns); --- Retardo en la lectura 
		port ( data : out std_logic_vector(WORD_SIZE-1 downto 0); -- Señal de datos bidireccional 
			   OE_n : in std_logic); -- Habilita lectura 
	end component fuenteUnidireccional; 
	
begin -- Instanciar las fuentes de datos, asignando valor a sus constantes generic 
	U1 : component fuenteBidireccional 
		 generic map (WORD_SZ, 30 ns, 40 ns) -- Asigna valor constantes generic
		 port map (data, OE1_n, WE_n); 
	U2 : component fuenteUnidireccional 
		 generic map (WORD_SZ, 20 ns ) -- Asigna valor constantes generic 
		 port map (data, OE2_n);
	data <= writeData when ( WE_n = '0') else ( others = > 'Z'); 
	vectoresTest : process is 
	begin 
		OE1_n <= '1 '; OE2_n <= '1'; WE_n <= '1'; -- Deshabilita señales 
		writeData <= B"0000_1111_1100_0011"; --Dato a escribir {=0x0fc3) 
		wait for PERIOD; 
		WE_n <= '0'; -- Habilita escritura (se escribe Ox0fc3)
		wait for PERIOD; 
		WE_n <= '1'; -- Deshabilita escritura
		OE2_n <= '0'; -- Habilita lectura desde la fu ente unidireccional
					  -- El dato en el bus debe ser Ox0001
		wait for PERIOD; 
		OE2_n <= '1'; -- Deshabilita lectura de la fu ente unidireccional
		OE1_n <= '0'; -- Habilita lectura desde la fuente bidireccional
					  -- El dato en el bus debe ser Ox0fc3
		wait for PERIOD; 
		wait; 
	end process vectoresTest; 
end architecture tb_bus;
```
Al instanciar las memorias, se asignan nuevos valores al tamaño de la palabra, que pasa a ser 16 bits, y a los retardos: 
- Memoria de sólo lectura: retardo en la lectura de 20 ns. 
- Memoria de lectura y escritura: retardo en la lectura de 30 ns y retardo en la escritura de 40 ns.
Las operaciones que se realizan son las siguientes: 
1. **tiempo= 0 (instante inicial)**. Se asigna valor '1' a las señales ``OE1_n``, ``OE2_n`` y ``WE_n``, es decir, inicialmente se encuentras deshabilitadas las operaciones de lectura y escritura en las memorias. También, en el instante inicial, se asigna el valor 0x0fc3 a la señal ``writeData`` del banco de pruebas, cuya finalidad es almacenar el valor que va a ser escrito en la memoria. 
2. **tiempo = 100 ns.** Se habilita la operación de escritura, para ello se pone a '0' la señal ``WE_n``. A consecuencia de ello, en el instante tiempo = 140 ns se escribe el valor 0x0fc3 en la memoria. 
3. **tiempo = 200 ns.** Se deshabilita la operación de escritura, poniendo la señal ``WE_n`` al valor '1'. Se habilita la operación de lectura de la memoria de sólo lectura, para lo cual se pone la señal ``OE2_n`` a '0'. A consecuencia de ello, el valor 0x0001 está disponible en el bus en el instante tiempo = 220 ns. 
4. **tiempo = 300 ns.** Se deshabilita la lectura de la memoria de sólo lectura, para lo cual se pone la señal ``OE2_n`` a '1'. Finalmente, se habilita la lectura de la memoria de lectura y escritura, para lo cual se pone la señal ``OE1_n`` a '0'. A consecuencia de ello, en el instante tiempo = 330 ns el valor 0x0fc3 está disponible en el bus.
# TEMA 6 DISEÑO DE LÓGICA SECUENCIAL
## 6.1. INTRODUCCIÓN
Algunos problemas de diseño pueden ser resueltos usando máquinas de estado finito. Una máquina de estado finito consiste esencialmente en un conjunto de estados (codificados usando flip-fiops) y transiciones entre estos estados, gobernadas por un conjunto de bits de condición.
Una *máquina de estado finito de Moore* (o simplemente, "máquina de Moore") es una máquina de estado en la cual las salidas del circuito dependen del estado actual y no del valor actual de las entradas. Por el contrario, las salidas de una *máquina de Mealy* dependen del estado actual y también del valor actual de las entradas.
## 6.2. DISEÑO DE MÁQUINAS DE ESTADO FINITO
Las máquinas de Moore y Mealy pueden ser diseñadas de manera sistemática siguiendo los pasos descritos a continuación:
1. Dibujar el diagrama de estados del circuito. 
2. Definir un conjunto de *variables* de estado y codificar los estados del diagrama de estados usando estas variables de estado. 
3. Escribir la *tabla de transición del estado* usando el diagrama dibujado en el Paso 1 y la codificación de los estados del Paso 2. 
4. Formular, a partir de la tabla de transición del estado del Paso 3, las funciones lógicas simplificadas para el nuevo estado y las salidas. 
5. Diseñar el circuito empleando un flip-flop por cada *variable de estado*, y lógica combinacional para las funciones de transición del estado y de salida obtenidas en el Paso 4. Obsérvese, que el diseño estructural de la *máquina de estado finito* (FSM) puede representarse de manera genérica.
![](img/Pasted%20image%2020250506164736.png)
### 6.2.1. Circuito detector de secuencias
El método anterior puede aplicarse al diseño de un circuito que detecte la secuencia 101. El circuito tiene una única entrada, por la que recibe bits en serie, y una única salida, en la que genera un bit 1 cuando detecta la secuencia 101 en los bits de entrada, y genera un O en caso contrario. Obsérvese que también deben detectarse las secuencias cuando se encuentran solapadas, por ejemplo: 10101
**Primer paso**: Dibujar el diagrama de estados.
![](img/Pasted%20image%2020250506173035.png)
Cada estado del diagrama "recuerda" una porción de la secuencia 101. Lastransiciones entre los estados están etiquetadas x/y, donde x corresponde con el valor de la entrada que produce la transición, e y corresponde con el valor de la variable de salida dado el estado en el que empieza la transición y el valor de entrada x. ==Dado que la salida depende del estado actual y de la variable de entrada, este tipo de diagrama corresponde con una máquina de Mealy==. En este tipo de diagrama debe tenerse en cuenta que debe escribirse una transición desde cada estado por cada posible valor que puede tomar la entrada en ese estado.

**Segundo paso**: Codificar los estados.
Puesto que hay tres estados, son necesarias dos variables de estado: A y B. Obsérvese la diferencia conceptual entre los estados de la máquina y las variables de estado definidas para codificar dichos estados. Por simplicidad en la exposición, realizaremos una codificación binaria de los estados:

| Estado | A   | B   |
| ------ | --- | --- |
| $S_0$  | 0   | 0   |
| $S_1$  | 0   | 1   |
| $S_2$  | 1   | 0   |
**Tercer paso**: Escribir la tabla de transición de estados.

| Estado<br>A B | Entrada<br>x | Próximo estado<br>N A    N B | Salida<br>y |
| ------------- | ------------ | ---------------------------- | ----------- |
| $S_0$ : 0 0   | 0            | $S_0$ : 0 0                  | 0           |
| $S_0$: 0 0    | 1            | $S_1$: 0 1                   | 0           |
| $S_1$: 0 1    | 0            | $S_2$: 1 0                   | 0           |
| $S_1$: 0 1    | 1            | $S_1$: 0 1                   | 0           |
| $S_2$: 1 0    | 0            | $S_0$ : 0 0                  | 0           |
| $S_2$: 1 0    | 1            | $S_1$: 0 1                   | 1           |
**Cuarto paso**: Obtener las funciones lógicas simplificadas que ==relacionan el próximo estado y la salida, con el estado actual y la entrada.==
$$N\,A=\overline{x}\,B$$
$$N\,B=x$$
$$y=x\,A$$
**Quinto paso**: Sintetizar el circuito secuencial síncrono que implemente las funciones lógicas anteriores. Si se usan flip-flops D, las entradas al flip-flop corresponden con el nuevo estado ($D_A= N A, D_B =N B$), mientras que las salidas del flip-flop corresponden con el estado actual ($Q_A = A, Q_B = B$).
![](img/Pasted%20image%2020250506174133.png)
## 6.3. SÍNTESIS DE LÓGICA SECUENCIAL
El comportamiento y la salida de un bloque de lógica secuencial depende del valor actual de sus entradas y de sus variables de estado. El valor de las variables de estado se almacena típicamente en elementos de memoria, ya sea en *latches* o en *flip-flops*.

Se llama *latches* a aquellos circuitos cuyo estado cambia únicamente cuando su entrada *enable* está a un determinado nivel ('0' ó '1').
```vhdl
process (enable, D) is 
begin 
	if (enable = '1') then 
		q <= D; 
	end if; 
end process;
```

Se llama *flip-flops* a aquellos circuitos cuyo estado cambia o bien en el flanco de subida del reloj, o bien en el flanco de bajada del reloj.
### 6.3.1. Sentencias condicionales incompletas
Obsérvese que el latch se define empleando una cláusula **if-then** sin **else**. Se denomina *sentencias condicionales incompletas* a este tipo de sentencias. Las sentencias condicionales incompletas son sintetizadas mediante latches debido a que la salida debe mantener su valor si ninguna de las condiciones de la cláusula se satisface. 
Un motivo por el cual podría pensarse en omitir el caso **else**, es que sea indiferente el valor que se asigne a las señales en este caso (ya que en la práctica nunca se producirá). Si no deseamos que el circuito se sintetice mediante un latch, debemos incluir el caso **else** en la sentencia condicional y asignar a las señales el valor 'X'.
### 6.3.2. Sentencias condicionales completas
Una característica inherente a las sentencias **if-elsif-else** es que las condiciones no tienen forzosamente que ser excluyentes entre sí. La herramienta de síntesis asume, por tanto, que deben comprobarse las condiciones en un cierto orden de prioridad, generando la lógica para ello.
En aquellos casos en que las condiciones de la sentencia condicional completa sean excluyentes entre sí, es preferible emplear sentencias **case** o **with**. Esto es debido a que las sentencias **case** y **with** se sintetizan de manera natural en multiplexores o estructuras equivalente a multiplexores, que son rápidas y ocupan relativamente poco área.
### 6.3.3. Retardos
En la descripción para síntesis de los circuitos combinacionales debe evitarse el uso de retardos. Lo mismo aplica a la descripción de circuitos secuenciales. Los retardos en el hardware son dependientes de la tecnología empleada en su fabricación y están sujetos a la variabilidad del proceso de fabricación, por ello es extremadamente difícil construir circuitos que presenten un determinado retardo.
Cuando es preciso emplear retardos para describir adecuadamente el circuito, puede definirse un retardo constante en la parte superior del código
`constant DEL : time := 1 ns;`
y usar este retardo en el código del circuito.
`A <= B after DEL;`
Puede asignarse un valor positivo a esta constante de retardo para realizar la simulación del circuito y posteriormente asignarle el valor cero cuando vaya a realizarse la síntesis.
Obsérvese que esta discusión acerca de los retardos aplica a los circuitos, no a los bancos de prueba, que no necesitan ser sintetizados.
### 6.3.4. Inicialización
Debe evitarse inicializar las variables y las señales al declararlas, ya que este tipo de inicialización no puede ser sintetizada. 
La inicialización de una variable o señal implica una acción que se realiza únicamente una vez al comienzo de la simulación. Si es preciso realizar una acción al comienzo de la simulación, entonces debe situarse en la secuencia de acciones que se ejecutan cuando se activa la señal de reset. Estas acciones se definen típicamente dentro de un bloque **process** sensible a la señal de reset.
### 6.3.5. Bloques process
Las asignaciones a señales dentro de los bloques process deben cumplir que:
- La señal en la parte izquierda de la asignación secuencial debe ser una señal definida dentro del bloque **process**, o una señal **out** o **inout** de la interfaz del circuito.
- Las señales en la parte derecha de la asignación secuencial deben ser señales definidas dentro del bloque **process**, o señales **in** o **inout** de la interfaz del circuito. 
- No se debe asignar valor a una determinada señal dentro de más de un bloque **process**. Es decir, cada señal debe ser evaluada en un único bloque **process**.
Para asignar valor a las salidas de los fiip-fiops y latches dentro de un bloque **process**, pueden emplearse sentencias de asignación a señal (usan el operador <=) y sentencias de asignación a variable (usan el operador :=). Las asignaciones a variable tienen efecto inmediatamente, mientras que las asignaciones a señal tienen efecto en un instante de tiempo $\delta$ unidades de tiempo posterior al tiempo simulado actual (suponiendo que no se ha especificado el retraso en la asignación empleando la cláusula **after**).
Cuando se emplean bloques **process** para describir un circuito secuencial, debe indicarse la lista de sensibilidad de cada bloque **process** con el fin de controlar cuándo se activa el bloque. Cuando se especifica una lista de sensibilidad, el simulador no ejecuta el bloque **process** hasta que no se produce un cambio en alguna de las señales que componen la lista.
No es posible emplear simultáneamente una lista de sensibilidad y sentencias **wait**. Sin embargo, no es recomendable emplear este segundo método (uso de sentencias **wait** dentro del bloque **process**), ya que puede dar lugar a circuitos no sintetizables.
## 6.4. FLIP-FLOP JK
En esta sección se describe el diseño de un fiip-fiop JK con reset asíncrono activado al nivel LOW. Este circuito puede encontrarse en dos estados: Q='0' y Q='1'. La tabla de transición de estados, considerando únicamente las entradas J y K, así como el estado actual (Qt) y el siguiente estado (Qt+I), es la mostrada a continuación. Las transiciones de estado se producen en el flanco de subida de la señal de reloj.

| J   | K   | Nuevo Estado         |
| --- | --- | -------------------- |
| 0   | 0   | $Q_{t+1} = Q_t$      |
| 0   | 1   | $Q_{t+1} = 0$        |
| 1   | 0   | $Q_{t+1} = 1$        |
| 1   | 1   | $Q_{t+1} = not\,Q_t$ |
![](img/Pasted%20image%2020250507175814.png)
Transición de estados de un flip-flop JK. En los arcos del diagrama se muestra el valor de las señales JK. El bit '-' es "don't care" (por ejemplo, "0-" representa "00" ó "01").
### 6.4.1. Diseño del flip-flop
```vhdl
-- Biestable JK con reset asíncrono en nivel LOW 
-- Fichero: fiipfiop_JK.vhd 
library IEEE; 
use IEEE.std_logic_1164.all; 

entity flipflop_JK is 
	port ( q, q_n  : out std_logic;
		   clk, J, K, reset_n  : in std_logic ) ;
end entity flipflop_JK; 

architecture flipflop_JK of flipflop_JK is 
	signal q_interna : std_logic; 
begin 
	q <= q_interna; 
	q_n <= not q_interna; 
	process (reset_n, clk) is 
		variable JK : std_logic_vector( 1 downto 0); 
	begin 
		if (reset_n = '0') then 
			q_interna <= '0'; 
		elsif rising_edge(clk) then 
			JK := J & K; 
			case (JK) is 
				when "01" = > q_interna <= '0'; 
				when "10" = > q_interna <= '1';
				when "11" => q_interna <= not q_interna; 
				when others => null; 
			end case; 
		end if; 
	end process; 
end architecture flipflop_JK;
```
La **architecture** contiene un bloque **process** que es sensible a la señal de reset y a la señal de reloj. En el cuerpo del bloque **process** se examina primero la señal de reset, ya que en caso de estar activa esa señal (con valor '0') la máquina debe pasar al estado Q='0'.
### 6.4.2. Banco de pruebas
```vhdl
-- Banco de pruebas del flip-flop JK 
-- Fichero: bp_fiipfiopJK.vhd 
library IEEE; 
use IEEE.std_logic_1164.all; 

entity bp_flipflopJK is 
end entity bp_flipflopJK; 

architecture bp_flipflopJK of bp_flipflopJK is 
	constant PERIODO : time := 100 ns; -- Reloj 
	signal q, q_n : std_logic; -- Salidas UUT 
	signal clk : std_logic := '0'; -- Entradas UUT 
	signal J, K, reset_n : std_logic; 
	
	component flipflop_JK is 
		port ( q, q_n  : out std_logic;
			   clk, J, K, reset_n  : in std_logic ) ;
	end component flipflop_JK; 
	-- Procedimiento para comprobar las salidas del flip-flop
	procedure comprueba_salidas 
		( esperado_q : std_logic; 
		  actual_q, actual_q_n : std_logic; 
		  error_count : inout integer) is 
	begin 
		-- Comprueba q 
		if ( esperado_q /= actual_q ) then 
			report "ERROR: Estado esperado ("     & 
				    std_logic' image(esperado_q)  &
				    "), estado actual ("          & 
				    std_logic' image(actual_q)    & 
				    " ), instante: "              &
				    time' image(now);
			error count := error_count + 1; 
		end if; 
		-- Comprueba q_n 
		if ( (not esperado_q) /= actual_q_n ) then 
			report "ERROR: q_n esperado ("        & 
			        std_logic' image((not esperado_q))    & 
			        "), valor actual ("                   & 
			        std_logic' image(actual_q_n)          &
			        " ), instante: "                      & 
			        time' image (now); 
			error_count := error_count + 1; 
		end if; 
	end procedure comprueba_salidas;
	begin 
	-- Instanciar y conectaT UUT 
		uut : component flipflop_JK port map 
						(q, q_n, clk, J, K, reset_n); 
						
		reset_n <= '1', 
				   '0' after (PERIODO/ 4), 
				   '1' after (PERIODO+PERIOD0/4); 
		clk <= not clk after (PERIOD0/2); 
		gen_ vec_ test : process is 
			variable error _count : integer := 0; -- Núm. errores 
		begin 
			report "Comienza la simulación"; 
			-- Vectores de test y comprobación del resultado 
			J <= '0'; K <= '0'; wait for PERIODO; -- 1 
			comprueba_salidas(' 0',q,q_n,error _count); 
			J <= '0'; K <= '1'; wait for PERIODO; -- 2 
			comprueba_salidas('0',q,q_n,error _count ); 
			J <= '1'; K <= '0'; wait for PERIODO; -- 3 
			comprueba_salidas('1',q,q_n,error_count); 
			J <= '0'; K <= '1'; wait for PERIODO; -- 4 
			comprueba_salidas('0',q,q_n,error _count ); 
			J <= '1'; K <= '1'; wait for PERIODO; -- 5 
			comprueba_salidas('1',q,q_n,error_count); 
			J <= '0'; K <= '0'; wait for PERIODO; -- 6 
			comprueba_salidas('1',q,q_n,error_count); 
			J <= '1'; K<= '0'; wait for PERIODO; -- 7
			comprueba_salidas('1',q,q_n,error_count); 
			J <= '1'; K <= '1'; wait for PERIODO; -- 8 
			comprueba_salidas('0',q,q_n,error _count ); 
			J <= '0'; K <= '0'; -- Deja el fiip-fiop en el estado '0' 
		-- Informe final 
		if (error_count =0) then 
			report "Simulación finalizada sin errores"; 
		else 
			report "ERROR: Hay "                  & 
					integer' image (error_ count) & 
					" errores.";
		end if;  
		wait; -- Final del bloque process, pero como la architecture tiene sentencias de asignación concurrente, esta sentencia wait no finaliza la simulación 
	end process gen_vec_test; 
end architecture bp_flipflopJK;
```
Se ha definido un procedure, que comprueba que los valores actuales de la salida del flip-flop coinciden con los esperados, mostrando el correspondiente mensaje en caso de que no coincidan.
Obsérvese que la sentencia wait que hay al final del bloque process finaliza la ejecución de dicho bloque, pero no la simulación, ya que la simulación de las sentencias de asignación concurrente a las señales de reset y reloj se realiza indefinidamente. Por tanto, la simulación del banco de pruebas no finaliza por sí misma, siendo preciso fijar su duración: 900 ns.
## 6.5. MÁQUINAS DE ESTADO FINITO DE MOORE
![](img/Pasted%20image%2020250507183505.png)
La transición entre los tres estados depende del valor de la entrada, x. La salida del circuito, z, vale 1 en el estado $S_2$ y 0 en los demás estados. Este código puede ser adaptado fácilmente para la descripción de otras máquinas de Moore.
### 6.5.1. Diseño de la máquina
```vhdl
-- Paquete con la definición de las constantes globales
-- Fichero: STATE_CONSTANTS.vhd 
library IEEE; 
use IEEE.std_logic_1164.all; 
package STATE_CONSTANTS is 
	constant STATE_BITS: integer := 2; -- Bits codifican estado
	constant S0: std_logic_vector(1 downto 0) := "00"; --Estados 
	constant S1: std_logic_vector(1 downto 0) := "01"; 
	constant S2: std_logic_vector(1 downto 0) := "10";
end package; 
--------------------------------------------
-- Máquina de Moore 
-- Fichero: maquinaMooreSimple.vhd 
library IEEE; 
use IEEE.std_logic_1164.all; 
use work.STATE_CONSTANTS.all; 
-- Definición de la entity 
entity maquinaMooreSimple is 
	port( z : out std_logic; -- Señal de salida 
		  state : out std_logic_vector(STATE_BITS-1 downto 0);
		  -- Estado actual de la máquina 
		  reset_n : in std_logic; -- Señal reset activada en bajo 
		  clk : in std_logic· -- Señal de reloj 
		  x : in std_logic); -- Señal de entrada 
end entity maquinaMooreSimple; 

-- Definición de la architecture 
architecture maquinaMooreSimple of maquinaMooreSimple is 
	signal internal_state: std_logic_vector(STATE_BITS-1 downto 0);
begin 
	state <= internal_state; -- Estado actual 
	-- Genera la salida 
	salida: process(internal_state) is 
	begin 
		case internal_state is 
			when S0     => z <= '0'; 
			when S1     => z <= '0'; 
			when S2     => z <= '1'; 
			when others => z <= 'X'; 
		end case; 
	end process salida;
	-- Genera el siguiente estado 
	proximo_estado: process(reset_n,clk) is 
	begin 
		if (reset_n = '0') then -- Reset asíncrono
			internal_state <= S0; 
		elsif rising_edge( clk) then -- En flanco subida del reloj 
			case internal_state is 
				when S0 => -- Estado actual: S0 
					if ( x = ' 1 ' ) then 
						internal_state <= S1; 
					else 
						internal_state <= S2; 
					end if; 
				when S1 => -- Estado actual: S1 
					if ( x = '0' ) then 
						internal_state <= S2; 
					end if; 
				when S2 => -- Estado actual: S2 
					if (x = '0') then 
						internal_state <= S0; 
					end if; 
				when others => -- Por completitud
					internal_state <= "XX"; 
			end case; 
		end if; 
	end process proximo_estado; 
end architecture maquinaMooreSimple;	
```
En primer lugar, se define un **package** con las constantes que serán usadas en el circuito y en el banco de pruebas. En el diseño de la máquina puede observarse que:
- La interfaz del circuito está compuesta por dos puertos de salida y tres puertos de entrada. Cuando la señal de reset pasa de valer '1' a valer '0', entonces la máquina pasa al estado $S_o$
- Se ha definido una señal interna a la **architecture**, llamada ``internal_state``, que almacena el estado actual en que se encuentra la máquina. Cabe preguntarse por qué no se usa directamente la señal ``state``, ya que ambas señales representan lo mismo y, de hecho, la sentencia ``state <= internal_state;`` hace que ambas tengan el mismo valor. El motivo es que, por ser ``state`` una señal de salida de la interfaz, no puede ser leída en el cuerpo de la **architecture**. Puesto que ``internal_state`` es una señal interna, puede ser leída y escrita.
- La **architecture** contiene dos bloques **process**:
	1. El primero, que es activado cuando hay un cambio en ``internal_state``, describe los cambios en la señal de salida, z.
	2. El segundo, que es activado cuando cambia la señal de ``reset`` asíncrono (``reset_n``) o la señal de reloj (``clk``), describe los cambios en el estado de la máquina, actualizando el valor de la señal ``internal_state``. Puesto que se comprueba antes el valor de ``reset_n``, esta señal tiene prioridad sobre la señal de reloj. Se emplea la función estándar de VHDL **rising_edge** para representar que las transiciones en el estado sólo se producen en el flanco de subida de la señal de reloj.
- Se ha añadido una cláusula **when others** al final de las dos sentencias case, con el fin de contemplar todos los casos posibles.
### 6.5.2. Banco de pruebas
```vhdl
-- Banco de pruebas para la máquina de Moore. Fichero: bp_maquinaMooTeSimple.vhd 
library IEEE; 
use IEEE.std_logic_1164.all; 
use work.STATE_CONSTANTS.all; 

entity bp_maquinaMooreSimple is 
	constant PERIODO : time := 100 ns; -- Periodo reloj 
end entity bp_maquinaMooreSimple; 

architecture bp_maquinaMooreSimple of bp_maquinaMooreSimple is
	signal z : std_logic; 
	signal state : std_logic_vector(STATE_BITS-1 downto 0); 
	signal reset_n : std_logic; 
	signal clk : std_logic := '0'; -- Inicializada a '0' 
	signal x : std_logic; 
	
	component maquinaMooreSimple is 
		port( z : out std_logic; -- Señal de salida 
		      state : out std_logic_vector(STATE_BITS-1 downto 0); -- Estado actual de la máquina 
		      reset_n : in std_logic; -- Señal reset activada en bajo 
		      clk : in std_logic; -- Señal de reloj 
		      x : in std_logic); -- Serial de entrada 
	end component maquinaMooreSimple; 
	
	-- Procedimiento para comprobar el resultado 
	procedure comprueba_state_z 
		(esperado_state : std_logic_vector(STATE_BITS-1 downto 0); 
		 esperado_z : std_logic; 
		 actual_state : std_logic_vector(STATE_BITS-1 downto 0); 
		 actual z : std_logic; 
		 error _count : inout integer ) is 
	begin -- Comprueba el estado 
		assert ( esperado_state = actual_state ) 
			report "ERROR : estado esperado ("       & 
				std_logic' image( esperado_state(1)) & std_logic' image( esperado_state(O)) &
				"), estado actual ("                 & std_logic' image(actual_state(1)) & std_logic' image(actual_state(O)) & 
				") en el instante "                  & time' image(now); 
		if ( esperado_state 1 /= actual_state ) then 
			error_count := error_count + 1; 
		end if; -- Comprueba la salida 
		if ( esperado_z 1 /= actual_z ) then 
			report "ERROR: salida esperada ("        & 
					std_logic' image (esperado_z)    & 
					"), salida actual ("             & 
					std_logic' image ( actual_z)     & 
					")en el instante "               & time'image(now); 
				error_count := error_count + 1; 
		end if; 
	end procedure comprueba_state_z;
	begin -- Cuerpo de la architecture 
		UUT : component maquinaMooreSimple port map ( z, state, reset_n, clk, x );
		-- Genera un único pulso LOW en el instante PERIOD0/4: resetea la máquina 
		reset_n <= '1', 
				   '0' after ( PERIOD0/4 ), 
				   '1' after ( PERIODO + PERIOD0/4 ); 
		-- Genera señal clk, asumiendo que se inicializó a 0. Flanco de subida en los instantes: 
		-- PERIOD0/2, PERIODO+PERIOD0/2, 2*PERIODO+PERIOD0/2, ... 
		clock : clk <= not clk after ( PERIOD0/2 ); 
		
		-- main process: genera vectores de test y comprueba resultados 
		main : process is 
			variable error _count : integer := O; -- Num. errores 
		begin 
			report "Comienza la simulación"; 
			x <= '0'; -- Valor inicial de entrada a UUT 
			wait for PERIODO; 
			-- En el instante PERIODO, el estado debería ser S0
			comprueba_state_z(SO, '0', state, z, error _count);
			wait for PERIODO; -- En el instante 2*PERIODO, el estado debería ser S2 
			comprueba_state_z(S2, '1 ', state, z, error _count); x <= '1 '; 
			wait for PERIODO; 
			-- En el instante 3*PERIODO, el estado debería ser S2 
			comprueba_state_z(S2, '1', state, z, error _count ); x <= '0'; 
			wait for PERIODO; 
			-- En el instante 4 *PERIODO, el estado debería ser S0 
			comprueba_state_z(S0, '0', state, z, error _count); x <= '1'; 
			wait for PERIODO; 
			-- En el instante 5*PERIODO, el estado debería ser S1 
			comprueba_state_z(S1, '0', state, z, error_count); wait for PERIODO; 
			-- En el instante 6*PERIODO, el estado debería ser S1 
			comprueba_state_z(S1, '0', state, z, error_count); x <= '0';
			wait for PERIODO; 
			-- En el instante 7*PERIODO, el estado debería ser S2 
			comprueba_state_z(S2, '1', state, z, error _count); x <= '1 '; 
			-- El estado final es S2 
			wait for PERIODO; 
			if (error_count = 0) then
				report "Simulación finalizada con 0 errores";
			else 
				report "ERROR: hay " & integer'image(error_count) & " errores."; 
			end if; 
			wait; -- Final de la ejecución del bloque process. 
		end process main; 
	end architecture bp_maquinaMooreSimple;
```
La señal de reloj, que inicialmente vale 0, tiene un periodo (``PERIODO``) de T = 100 ns. Esto implica que los flancos de subida de la señal de reloj se producen en los instantes: 0.5 · T = 50 ns, 1.5 · T = 150 ns, 2.5 · T = 250 ns, ... que son precisamente los instantes en que se producen las sucesivas transiciones en el estado.
Para generar la señal de reloj se emplea la siguiente sentencia concurrente: ``clk <= not clk after ( PERIOD0/2 );`` donde se asume que la señal de reloj ha sido inicializada al valor '0'. Obsérvese que de esta forma se crea una señal de reloj infinitamente larga, con lo cual la simulación no finalizará automáticamente, sino que hay que definir el instante de finalización.
### 6.5.3. Modelado estructural
Ahora veremos cómo describir la máquina de estado finito de Moore empleando código VHDL estructural.
Para emplear código VHDL estructural, en primer lugar hay que decidir qué componentes van a usarse en el diseño. Emplearemos puertas lógicas básicas (AND, OR, inversor, NAND, NOR y XOR), así como flip-flops D. La tabla de transición de estados y salidas para la máquina descrita es:

| Estado<br>A B | Entrada<br>x | Próximo estado<br>N A    N B | Salida<br>y |
| ------------- | ------------ | ---------------------------- | ----------- |
| $S_0$ : 0 0   | 0            | $S_0$ : 1 0                  | 0           |
| $S_0$: 0 0    | 1            | $S_1$: 0 1                   | 0           |
| $S_1$: 0 1    | 0            | $S_2$: 1 0                   | 0           |
| $S_1$: 0 1    | 1            | $S_1$: 0 1                   | 0           |
| $S_2$: 1 0    | 0            | $S_0$ : 0 0                  | 1           |
| $S_2$: 1 0    | 1            | $S_1$: 1 0                   | 1           |
Las funciones lógicas simplificadas que relacionan el próximo estado (N A, N B) y la salida (z), con el estado actual (A, B) y la entrada (x) son:
$$NA = \overline{x}\overline{A}+x\,A$$
$$NB = x \overline{A}$$
$$z= A$$
```vhdl
-- Máquina de Moore, diseño estructural 
-- Fichero: maquinaMooreSimple_estruc.vhd
library IEEE; 
use IEEE. std_logic_1164.all; 
architecture maquinaMooreSimple_estruc of maquinaMooreSimple is  
	signal A, B : std_logic; -- Variables de estado actuales 
	signal NA, NB : std_logic; -- Próximas variables de estado 
	
	-- Componente: fiip-fiop D 
	component flipflop_D is 
		port ( q, q_n : out std_logic; 
			   d, clk, reset_n : in std_logic); 
	end component flipflop_D; 
begin 
	state <= A & B; -- Muestra estado actual en el puerto de salida 
	-- Conexiones de los flip-flops 
	-- Las salidas q_n se dejan sin conectar 
	dff_A: component flipflop_D port map 
		( q => A, d => NA, clk => clk, reset_n => reset_n ); 
	dff_B: component flipflop_D port map 
		( q => B, d => NB, clk => clk, reset_n => reset_n ); 
	-- Funciones para el cálculo del nuevo estado y la salida 
	NA <= ((not x) and (not A)) or (x and A); 
	NB <= x and (not A); 
	z <=A; 
end architecture maquinaMooreSimple_estruc;
```
## 6.6. MÁQUINAS DE ESTADO FINITO DE MEALY
En las máquinas de Mealy, las salidas del circuito dependen del estado actual y del valor actual de las entradas. eterminado estado, sus salidas pueden cambiar si cambian las entradas. Como ejemplo de implementación de una máquina de Mealy, consideremos la máquina para el reconocimiento de la secuencia de bits 0110. Obsérvese que se permite el solapamiento de secuencias (por ejemplo, 0110110).
![](img/Pasted%20image%2020250509155758.png)
La salida de la máquina es un '1' lógico cada vez que se detecta el patrón 0110 en la secuencia de bits de entrada, que se supone que está sincronizada con el reloj de la máquina. El tiempo que transcurre entre la entrada del último '0' del patrón y la salida del '1' es igual al retardo de una puerta lógica. Para los demás bits de la secuencia de entrada, la salida de la máquina es '0'.
### 6.6.1. Diseño de la máquina
Además de la entrada serie de la secuencia de bits (``x``) y la entrada del reloj (``clk``), la máquina tiene una entrada de reset síncrono activada en '0' (``reset_n``). Esto significa que si cuando se produce un flanco de subida de la señal del reloj, la entrada ``reset_n`` vale '0', entonces se resetea la máquina, es decir, pasa al estado S0. La máquina tiene dos salidas: el estado actual de la máquina (``state``) y la salida de detección del patrón 0110 (``z``).
```vhdl
-- Definición de las constantes globales 
--Fichero: seq0110_CONST.vhd 
library IEEE; 
use IEEE. std_logic_1164.all; 

package seq0110_CONST is 
	constant STATE_BITS : integer := 2; -- Num. bits del estado 
	constant SO : std_logic_vector(1 downto 0) := "00"; 
	constant 81 : std_logic_vector(1 downto 0) := "01"; 
	constant 82 : std_logic_vector(1 downto 0) := "10"; 
	constant 83 : std_logic_vector(1 downto 0) := "11"; 
end package seq0110_CONST; 
------------------------------------------
-- Máquina de Mealy detectora de la secuencia O11O 
-- Fichero: seq011O.vhd 
library IEEE; 
use IEEE.std_logic_1164.all; 
use work. seq0110_CONST.all; 

entity seq0110 is 
	port ( z : out std_logic; -- Señal de salida 
		   state : out std_logic_vector(STATE_BITS-1 downto 0); -- Estado actual
		   reset_n : in std_logic; -- Reset síncrono activado LOW
		   clk : in std_logic; -- Señal de reloj
		   x : in std_logic ) ; -- Bit de entrada
end entity seq0110; 

-- Definición de la architecture 
architecture seq0110 of seq0110 is  
	signal internal_state : std_logic_vector(STATE_BITS-1 downto 0); 
	signal z : std_logic; -- Señal de salida obtenida de circ. combinacional
begin 
	state <= internal_state; 

-- Cálculo de la salida 
	z <= '1' when ((internal_state = S3) and (x = '0')) else '0';
	ffD_salida: process (clk) is -- flip-flop D
	begin 
		if (rising_edge(clk)) then
			z_long <= z; 
		end if; 
	end process ffD_salida;

-- Cálculo del próximo estado
	proximo_estado: process (clk) is 
	begin 
		if ((reset_n = '0') and rising_edge(clk)) then -- Reset síncrono
			internal_state <= S0; 
		elsif rising_edge(clk) then -- Flanco de subida del reloj 
			case internal_state is 
				when S0 =>
					if ( x = 'O' ) then -- Primer bit del patrón
						internal_state <= S1; 
					else 
						internal_state <= S0; 
					end if; 
				when S1 => 
					if ( x = '1' ) then -- Segundo bit del patrón
						internal_state <= S2; 
					else 
						internal_state <= S1; 
					end if; 
				when S2 => 
					if ( x = '1' ) then -- Tercer bit del patrón
						internal_state <= S3; 
					else 
						internal_state <= S1; 
					end if; 
				when others => 
					if ( x = 'O' ) then -- Cuarto bit del patrón
						internal_state <= S1; 
					else 
						internal_state <= S0; 
					end if; 
			end case; 
		end if; 
	end process proximo_estado;    
end architecture seq0110;
```
Las constantes globales, que son usadas tanto en el diseño del circuito como en el banco de pruebas, son definidas en el **package** mostrado en el código.
Se han definido dos bloques **process**: uno para generar la salida, que es sensible al estado y a la entrada, y otro para generar el próximo estado y resetear la máquina, que es sensible únicamente a la señal de reloj. Puesto que la máquina tiene reset síncrono, este segundo bloque **process** no es sensible a la señal de reset.
El bloque **process** usado para generar el próximo estado corresponde directamente con el diagrama mostrado en la figura. La señal de reset no se ha incluido en la lista de señales a las que es sensible el bloque. Así pues, este bloque sólo es activado cuando se produce un cambio en la señal de reloj.

En el bloque **process** usado para generar la señal de salida, la siguiente sentencia concurrente:
`z <= '1' when ((internal_state = S3) and (x = '0')) else '0';`
es activada cada vez que se produce un cambio en alguna de las señales de la parte derecha de la asignación.
Puesto que éste es un bloque combinacional, la duración de la señal '1' de salida puede ser más pequeña que un ciclo de reloj, ya que su duración depende del tiempo durante el cual la entrada x siga valiendo '0' mientras la máquina permanezca en el estado S3.
Para garantizar que la salida '1' tiene una duración de al menos un ciclo de reloj, es necesario hacer pasar la señal de salida por un flip-flop D.
### 6.6.2. Banco de pruebas
```vhdl
-- Banco de pruebas 
-- Máquina detectora secuencia 0110. Fichero: bp_seq0110.vhd 
library IEEE; 
use IEEE.std_logic_1164.all; 
use work.seq0110_CONST.all; 

entity bp_seq0110 is
	constant PERIODO : time := 100 ns; -- Periodo reloj 
end entity bp_seq0110; 

architecture bp_seq0110 of bp_seq0110 is 
	signal z_long : std_logic; -- Salida de la máquina 
	signal state : std_logic_vector(STATE_BITS-1 downto 0); -- Estado actual 
	signal reset_n : std_logic; -- Reset síncrono activado LOW 
	signal clk : std_logic := '0'; -- Señal de reloj 
	signal x : std_logic; -- Entrada a la máquina 
	
	component seq0110 is 
		port (z_long : out std_logic; 
			  state : out std_logic_vector(STATE_BITS-1 downto 0); 
			  reset_n : in std_logic; 
			  clk : in std_logic; 
			  x : in std_logic ); 
	end component seq0110; 
	-- Procedimiento para comprobar si se produce error	
	procedure comprueba_estado_salida 
		( esperado_state : std_logic_vector(STATE_BITS-1 downto 0); 
		  esperado_z     : std_logic; 
		  actual_state   : std_logic_vector(STATE_BITS-1 downto 0); 
		  actual z       : std_logic; 
		  error_count    : inout integer) is 
	begin 
		-- Comprueba el estado 
		assert (esperado_state = actual_state) 
			report "ERROR: Estado esperado ("      & 
				std_logic'image(esperado_state(1)) & std_logic'image( esperado_state(O)) & 
				"), estado actual ("               & 
				std_logic'image(actual_state(1))   & std_logic' image(actual_state(O)) & 
				"), instante: "                    & time'image(now); 
		if (esperado_state /= actual_state) then 
			error_count := error_count + 1; 
		end if; 
		-- Comprueba salida 
		assert(esperado_z = actual_z) 
		report "ERROR: Salida esperada ("       & 
			std_logic'image(esperado_z)         & 
			"), salida actual ("                & 
			std_logic'image(actual_z)           & 
			"), instante:  "                    & time' image(now); 
		if (esperado_z / = actual_z) then 
			error_count := error_count + 1; 
		end if; 
	end procedure comprueba_estado_salida;
begin 
	UUT: component seq0110 port map (z_long, state, reset_n, clk, x); 
	reset_n <= '1', 
			   '0' after ( PERIODO/ 4 ), 
			   '1' after ( PERIODO + PERIOD0/4 ); 
	clk <= not clk after ( PERIOD0/2 ); 
	-- Generar vectores de test y comprobar el resultado 
	main : process is
		variable error_count : integer := 0; -- Núm. errores 
	begin 
		report "Comienza la simulación";
		x <= '0'; wait for PERIODO; -- Comprueba reset, empieza en S0
		comprueba_estado_salida(S0, '0' ,state,z_long,error_count ); 
		x <= '1 '; wait for PERIODO; -- Sigue en S0 
		comprueba_estado_salida(S0, '0' ,state,z_long,error_count ); 
		x <= '0'; wait for PERIODO; -- Va a S1 
		comprueba_estado_salida(S1, '0' ,state,z_long,error_count ); 
		x <= '0'; wait for PERIODO; -- Sigue en S1 
		comprueba_estado_salida(S1, '0' ,state,z_long,error_count ); 
		x <= '1'; wait for PERIODO; -- Va a S2 
		comprueba_estado_salida(S2, '0' ,state,z_long,error_count ); 
		x <= '0'; wait for PERIODO; -- Va a S1 
		comprueba_estado_salida(S1, '0' ,state,z_long,error _count ); 
		x <= '1'; wait for PERIODO; -- Va a S2 
		comprueba_estado_salida(S2, '0' ,state,z_long,error_count ); 
		x <= '1'; wait for PERIODO; -- Va a S3 
		comprueba_estado_salida(S3, '0' ,state,z_long,error_count ); 
		x <= '1'; wait for PERIODO; -- Va a S0 
		comprueba_estado_salida(S0, '0' ,state,z_long,error_count ); 
		x <= '0'; wait for PERIODO; -- Va a S1 
		comprueba_estado_salida(S1, '0' ,state,z_long,error_count ); 
		x <= '1'; wait for PERIODO; -- Va a S2 
		comprueba_estado_salida(S2, '0' ,state,z_long,error_count ); 
		x <= '1'; wait for PERIODO; -- Va a S3 
		comprueba_estado_salida(S3, '0' ,state,z_long,error_count ); 
		x <= '0'; wait for PERIOD0/4; -- Va a S1 
		comprueba_estado_salida(S3, '0' ,state,z_long,error_count); --Salida '0' en S3 
		wait for 3*(PERIOD0/4); 
		comprueba_estado_salida(S1, '1' ,state,z_long,error_count); -- Salida '1' en S1 
		wait for PERIODO; -- Sigue en S1 
		comprueba_estado_salida(S1, '0' ,state,z_long,error_count ); 
		wait for PERIODO; -- Tests finalizados 
		if(error_count = 0) then report "Simulación finalizada sin errores"; 
		else report "ERROR: Hay " & integer'image(error_count) & " errores.";
		end if; 
		wait; -- Detiene este bloque process 
	end process main; 
end architecture bp_seq0110;
```
Este banco de pruebas testea sistemáticamente el circuito, pasando al menos una vez por cada uno de los arcos de transición entre estados de la máquina.
## 6.7. MÁQUINAS DE ESTADO FINITO SEGURAS
Una máquina de estado finito (FSM) *segura* es una FSM tal que en su definición se ha considerado la posibilidad de que la máquina alcance un estado ilegal y, en tal caso, se ha descrito cómo debe realizarse la transición a un estado legal. En teoría, los estados ilegales son inalcanzables. Sin embargo, en la práctica la máquina puede entrar en un estado ilegal debido a un error en el circuito.
Consideremos de nuevo la FSM de Moore que se diseñó en la Sección 6.5. El estado S3 es un estado ilegal y, por tanto, no ha sido considerado en el diseño. Si debido a un error en el circuito la máquina entra en ese estado, queda atrapada en él.
En la Figura b se muestra la versión segura de esta FSM, en la cual se ha incluido explícitamente en el diseño el estado ilegal S3. En el diseño seguro, si la máquina alcanza el estado S3 , entonces la salida es '0' y el siguiente estado es S0.
![](img/Pasted%20image%2020250509164525.png)
En el diseño VHDL de una FSM segura, se emplea la opción **others** dentro de la cláusula **case** con el fin de describir el comportamiento de la máquina .en los estados ilegales.
```vhdl
architecture maquinaMooreSimple of maquinaMooreSimple is 
	signal internal_state: std_logic_vector(STATE_BITS-1 downto 0); 
begin 
	state <= internal_state; -- Muestra el estado 
	-- Genera la salida 
	salida: process(internal_state) is 
	begin 
		case internal_state is 
			when S0     => z <= '0'; 
			when S1     => z <= '0'; 
			when S2     => z <= '1'; 
			when others => z <= '0'; -- Salida en el estado ilegal 
		end case; 
	end process salida;
	
	-- Genera el siguiente estado 
	proximo_estado: process(reset_n,clk) is 
	begin
		if ((reset_n = '0') then -- Reset asíncrono
			internal_state <= S0; 
		elsif rising_edge(clk) then -- Flanco de subida del reloj 
			case internal_state is 
				when S0 =>
					if ( x = '1' ) then -- Estado actual: S0
						internal_state <= S1; 
					else 
						internal_state <= S2; 
					end if; 
				when S1 => 
					if ( x = '0' ) then -- Estado actual: S1
						internal_state <= S2;
					end if; 
				when S2 => 
					if ( x = '0' ) then -- Estado actual: S2
						internal_state <= S0;
					end if; 
				when others =>         -- Del estado ilegal va a S0
						internal_state <= "00"; 
					end if; 
			end case; 
		end if; 
	end process proximo_estado; 
end architecture maquinaMooreSimple;
```
Uno podría pensar que no es necesario incluir la opción **others** cuando el número de estados es potencia de dos. Esto es así cuando se codifican los estados empleando el mínimo número de bits. Sin embargo, recuérdese que también es posible codificar los estados de modo que el registro de estado tenga un bit por cada estado del diagrama de transiciones. Desde el punto de vista estructural, se emplearía un flip-flop D por cada estado de la FSM. Este tipo de codificación, que se denomina *one-hot encoding*, da lugar a numerosos estados ilegales. En este caso, el uso de **others** garantiza que estos estados ilegales, en caso de producirse, tendrán una transición a un estado legal.
# TEMA 7 METODOLOGÍA DE TRANSFERENCIA ENTRE REGISTROS
## 7.1. INTRODUCCIÓN
El comportamiento de los sistemas se describe frecuentemente mediante *algoritmos*. Es decir, mediante una secuencia de acciones o pasos, que deben ejecutarse para resolver un problema o realizar una tarea. Dos características básicas de los algoritmos son, por una parte, el empleo de **variables**, que sirven para almacenar los resultados intermedios de los cálculos, y por otra parte, la **ejecución secuencial** de las acciones. Es decir, los pasos de un algoritmo se ejecutan uno tras otro, siguiendo un orden bien establecido.
La *metodología de transferencia entre registros* (metodología RT) permite describir de manera algorítmica el comportamiento del hardware. En esta metodología, los *registros* se emplean para almacenar los datos intermedios, desempeñando de esta forma el mismo papel que juegan las *variables* en los algoritmos.
En la notación RT ( *Register Transfer*), todas las operaciones son descritas como la transferencia de datos de uno o más registros, a otro registro. Durante la transferencia de los datos, éstos pueden transformarse mediante operaciones combinacionales aritméticas y lógicas, desplazamientos, etc. Por lo general, la síntesis de este tipo de descripciones da lugar a circuitos secuenciales, si bien en algunos casos sencillos puede dar lugar a circuitos combinacionales. En este tema nos centraremos en el diseño de programas RT para síntesis de circuitos secuenciales síncronos con camino de datos. En estos circuitos cabe distinguir dos partes:
- El *camino de los datos*, que consiste en componentes, tanto combinacionales como secuenciales, que almacenan, combinan y manipulan los datos. Entre los componentes que típicamente forman parte del camino de datos se encuentran los registros, los sumadores, los multiplexores, etc. 
- La *lógica de control,* que consiste en la lógica necesaria para generar las señales de control que controlan todos los componentes del camino de datos.
El camino de datos envía *señales de status* (que indican el estado de determinados datos) a la lógica de control, que a su vez envía *señales de control* al camino de datos, basadas en la señales de status recibidas y en el propio estado interno de la lógica de control.
==Llamamos a esta metodología de implementación metodología de transferencia entre registros porque un algoritmo es transformado en una secuencia de acciones que especifican cómo los datos son manipulados y transferidos entre registros.==
Una implementación RT típica incluye un camino de datos y la lógica de control. Este tipo de circuito, consistente en una máquina de estado finito (FSM) a la que se ha añadido el camino de datos, se denomina FSMD (FSM con un camino de Datos).
## 7.2. OPERACIONES DE TRANSFERENCIA ENTRE REGISTROS
### 7.2.1. Operación RT básica
La acción básica en la metodología RT es la *operación de transferencia entre registros*:
$$r_{dest} \leftarrow f(r_{orig1}, r_{orig2}, · · ·, r_{origN} );$$
donde los registros situados en el lado de la derecha son los registros origen de los datos $(r_{orig1}, r_{orig2}, · · ·, r_{origN} )$, la función $f$ representa la operación a realizar, y el registro situado en el lado de la izquierda es el registro destino ($r_{dest}$), en el cual se almacena el resultado de la operación. En resumen, esta notación significa que el nuevo valor de $r_{dest}$ se calcula evaluando $f(r_{orig1}, r_{orig2}, · · ·, r_{origN} )$, y que el resultado se almacena en $r_{dest}$ en el siguiente flanco de subida de la señal de reloj.
La única restricción que se impone a la función $f$ es que debe poder ser sintetizada mediante un circuito combinacional. Durante la transferencia de los datos, éstos pueden transformarse mediante operaciones combinacionales aritméticas y lógicas, desplazamientos, etc. En la tabla se muestran algunos ejemplos de operaciones RTL y sus correspondientes sentencias VHDL.
![](img/Pasted%20image%2020250509171751.png)
La mayor diferencia entre una variable de un algoritmo y un registro es que en la operación RT está implícito el papel de la señal de reloj. Las acciones que implica la operación RT
$$r_{dest} \leftarrow f(r_{orig1}, r_{orig2}, · · ·, r_{origN} );$$son las siguientes:
1. Se produce el flanco de subida de la señal de reloj. Transcurrido un cierto retardo interno de propagación de los registros, los datos de salida de los registros están disponibles. 
2. Los datos son operados por el circuito combinacional que realiza la función $f$ y el resultado es ruteado a la entrada del registro $r_{dest}$. Se asume que el periodo de la señal de reloj es lo suficientemente grande como para acomodar el retardo de propagación de los registros y del circuito combinacional. 
3. En el siguiente flanco de subida de la señal de reloj, el resultado es almacenado en el registro $r_{dest}$.
### 7.2.2. Programa RT
Como punto de partida para el diseño de la FSMD, se describe su operación como un algoritmo en notación RT. Este algoritmo se denomina *programa RT*.
Aquellas operaciones que pueden realizarse simultáneamente, pueden definirse en un mismo paso del programa RT. Las operaciones que deben ejecutarse consecutivamente, deben forzosamente definirse en pasos consecutivos. Los pasos del algoritmo irán ejecutándose en el circuito secuencial en ciclos consecutivos de la señal de reloj.
Las operaciones que se realizan en un mismo paso del programa RT serán traducidas a sentencias VHDL que se ejecutarán concurrentemente. Así pues, varias operaciones pueden realizarse en un mismo paso del programa RT si pueden ser ejecutadas unas independientemente de las otras. Es decir, si no existe dependencia entre los datos y los recursos involucrados en dichas operaciones.
Como ejemplo de construcción de un programa RT, consideremos el diseño de un circuito que, dado un número de entrada (``n``), calcula su factorial (``fact``).
```
Paso O.  fact<15:0> <- 1; 
		 fin <- O; 
		 num <- 2; 
Paso 1.  if (num <= n) then begin 
			 fact <- fact * num; 
			 num <- num + 1 ; 
			 go to Paso 1; 
		 end /* if */ 
Paso 2.  fin <- 1;
```
Al decidir qué operaciones se engloban en un mismo paso, debe tenerse en cuenta que todas las sentencias RT de un mismo paso serán operaciones que el circuito realizará concurrentemente.
==Una implicación de este hecho es que si en un mismo paso del programa RT se asigna valor a una variable y se usa esa variable, entonces se está usando el valor *antiguo* de la variable y no el valor actualizado de la misma.==
Ej: supongamos que el Paso 1 del programa RT anterior se sustituye.
```
Paso 1.  if (num <= n) then begin 
			 num <- num + 1; 
			 fact <- fact * num; 
			 go to Paso 1; 
		 end 1* if *1
```
La diferencia introducida en el Paso 1 es que ahora se ha escrito la sentencia que calcula el nuevo valor de num antes que la sentencia que calcula el nuevo valor de f act. Es decir, se ha intercambiado el orden de estas dos sentencias
```
 num <- num + 1; 
 fact <- fact * num;
```
Sin embargo, ambas versiones del Paso 1 son equivalentes, ya que en la sentencia ` fact <- fact * num;` se utiliza el valor *antiguo* de ``num``. 
## 7.3. MÁQUINAS DE ESTADO FINITO CON CAMINO DE DATOS
En esta sección de describen algunos aspectos de la síntesis de los programas RT. En particular, se describen los fundamentos de las máquinas de estado finito con camino de datos (FSMD), que son circuitos secuenciales síncronos empleados para sintetizar los programas RT.
### 7.3.1. Múltiples operaciones RT y camino de datos
Un programa RT consiste en varios pasos y, en general, un determinado registro puede ser cargado con diferentes datos en diferentes pasos del algoritmo. Por ejemplo, el registro r1 puede ser cargado con el valor 0 en el paso de inicialización, seguidamente puede sumarse su contenido al del registro r2 en un paso de suma, y finalmente puede incrementarse su contenido. Así pues, hay tres operaciones RT que usan el registro r1 como registro destino:
$$r_1 \leftarrow 0$$
$$r_1 \leftarrow r_1 + r_2$$
$$r_1 \leftarrow r_1 +1$$
Debido a que hay varias posibilidades, es necesario emplear un circuito multiplexor para enrutar el valor deseado hasta la entrada del registro r1.
![](img/Pasted%20image%2020250509173750.png)
Se puede escoger la operación RT deseada asignando el valor adecuado a la señal de selección del multiplexor.
### 7.3.2. Lógica de control mediante FSM
Como hemos indicado anteriormente, el *camino de datos* realiza todas las operaciones RT del algoritmo. Ahora bien, es necesario disponer de un mecanismo para especificar cuándo y qué operaciones RT deben realizarse. Esta es la finalidad de la *lógica de control*.
==La *lógica de control* (también llamada *camino de control*) se usa para determinar el orden de las operaciones RT y para realizar selectivamente ciertas operaciones RT dependiendo del valor de comandos externos o de señales de status.== Típicamente, la lógica de control se implementa mediante una máquina de estado finito (FSM). Los motivos son principalmente los siguientes:
- La transición entre los estados de una FSM se produce en los instantes en que se produce el flanco de subida de la señal de reloj. Puesto que el instante en que se produce la ejecución de las operaciones RT está también dictado por la señal de reloj, puede asociarse la operación RT a un estado de la FSM. 
- En una FSM las transiciones entre los estados se producen siguiendo una secuencia bien definida. Así pues, la FSM puede emplearse para definir la secuencia en la cual deben ejecutarse la operaciones RT. 
- En función del valor de sus señales de entrada, la FSM puede realizar unas u otras transiciones entre estados, con lo cual la FSM permite realizar bifurcaciones en la secuencia de operaciones RT. Esto posibilita la implementación de las sentencias **if** y de los bucles que pueda haber en el programa RT.
Puesto que se asocia la operación RT con un estado de la FSM, puede extenderse la definición de la FSM indicando la operación RT que debe realizarse en cada estado. Esta definición extendida de la FSM constituye la definición de la FSMD: en los arcos de transición entre estados, o en los estados, además de especificar la salida de la FSM se especifica qué operación RT debe realizarse.
### 7.3.3. Diagrama de bloques básico de la FSMD
Diagrama de bloques conceptual de la FSMD:
![](img/Pasted%20image%2020250509174602.png)El *camino de datos* puede realizar todas las operaciones RT necesarias. Está compuesto de las tres partes siguientes:
- *Registros de datos*, en los que se almacenan los resultados intermedios de los cálculos. 
- *Unidades funcionales*, que realizan las funciones ($f$) especificadas en las operaciones RT. Entre las unidades funcionales típicas se encuentran un sumador, un restador, un circuito incrementador y uno decrementador, etc.
- El *conexionado de enrutamiento*, que conecta por una parte las salidas de los registros con las entradas de las unidades funcionales, y por otra las resultados obtenidos de las unidades funcionales con las entradas a los registros. Normalmente el enrutamiento se realiza mediante multiplexores.
El *camino de datos* normalmente tiene las siguientes señales de entrada y salida: 
- Los *datos de entrada*, que son los datos externos que debe procesar la FSMD. 
- Los *datos de salida*, que son los resultados del programa que implementa la FSMD.
- La *señal de control*, que especifica qué operación RT debe ejecutarse. Esta señal es generada por la *lógica de control*. 
- La *señal de status interna* es una señal generada por el camino de datos cuya finalidad es informar a la lógica de control de que se ha satisfecho cierta condición, por ejemplo, que el contenido de un registro es cero. Esta señal es usada por la lógica de control para determinar la secuencia futura de acciones.
La lógica de control es una FSM y como tal contiene un registro de estado, la lógica para el cálculo del siguiente estado y la lógica para el cálculo de la salida. La lógica de control normalmente tiene las siguientes señales de entrada y salida: 
- Los *comandos externos*, que son señales externas que señalan que deben realizarse determinadas acciones, por ejemplo, que comience la operación de la FSMD. 
- La *señal de status interna*, que proviene del camino de datos, y que es empleada para determinar el siguiente estado. 
- La *señal de control*, que es una señal de salida de la FSM cuya finalidad es controlar la operación del camino de datos. 
- La *señal de status externa*, que es una señal de salida de la FSM cuya finalidad es indicar cuál es el estado de la operación de la máquina, por ejemplo, si se encuentra libre u ocupada.
Además de estas señales, los registros del camino de datos y de la lógica de control están conectados a la misma señal de reloj y opcionalmente a una señal de reset asíncrono. Obsérvese que el camino de datos tiene la forma de un circuito secuencial y que la lógica de control es una FSM, y por tanto, es otro circuito secuencial. Por tanto, puede considerarse que la FSMD es la combinación de dos circuitos secuenciales, ambos sincronizados por la misma señal de reloj.
## 7.4. DESCRIPCIÓN DEL PROGRAMA RT USANDO VHDL
Aunque el programa RT puede ser escrito en formato libre y posteriormente traducido a VHDL, suelen ofrecerse algunas recomendaciones acerca de su estructura, con el fin de facilitar su posterior traducción a VHDL sintetizable. Una posible estructura del programa RT es la mostrada a continuación.
```
Paso 0.      Inicializa variables; 
		     while (true) do begin 
Paso 1.      Paso 1 del algoritmo;
Paso 2.      Paso 2 del algoritmo;
...
Paso k.      for i <- 0 to max-1 do begin ...
...
Paso m.      Llamada a la función FUNCION_1; 
...
Paso n.      Paso n del algoritmo; 
		end    /* de while */
```
En esta "plantilla" de programa RT hay un paso de inicialización (Paso 0), seguido de un bucle **while** infinito, dentro del cual se definen una serie de pasos. Este programa RT puede traducirse a VHDL aplicando la siguiente plantilla:
```vhdl
package DEFS is 
	constant FUNCION_1 : integer := z; -- z es un número de estado que define unívocamente esta función. Debe satisfacerse: z > m + x + 1 
...
end package DEFS; 

architecture ... 
	signal state : integer; -- Contador que indica el paso del seudocodigo ejecutandose 
	...
	seudocodigo : process ( reset_n, clk ) is 
	begin 
		if ( reset_n = '0') then 
			...         -- Operaciones de inicialización (Paso 0 del seudocódigo) 
			state <= 1; -- Inicializa state 
		elsif rising_edge( clk ) then 
			state <= state + 1; -- Incrementa state
			case ( state ) is   -- state codifica los pasos del algoritmo
				when 1 =>   
					... -- Operaciones del Paso 1 del seudocodigo 
				when 2 => 
					... -- Operaciones del Paso 2 del seudocodigo 
				...
				when k => 
					i <= O; -- Inicialización del bucle for 
				when k + 1 =>
					... -- Primer paso dentro del bucle for 
				when k + 2 => 
					... -- Segundo paso dentro del bucle for 
				...
				when k + x = > 
					... -- Último paso dentro del bucle for 
					if (i < max) then 
						state <= k+1; 
					end if; 
					i <= i + 1; 
				...
				when m + x => -- Se supone que FUNCION_1 es llamada aquí 
					ret_state <= m + x + 1; -- Return state 
					state <= FUNCION_1;     -- Va a la FUNCION_1 
				when m + x + 1 = > 
					...
				when FUNCION_1 => 
					-- Operaciones del Paso 1 de la función FUNCION_1 
				when FUNCION_1 + 1 => 
					-- Operaciones del Paso 2 de la función FUNCION_1 
				...
				when FUNCION_1 + y => -- Último paso de FUNCION_1 
					state <= ret_state; -- return al procedimiento que hace la llamada 
				...
				when others => -- Paso n del seudocodigo 
					state < =O; 
			end case;
		end if; -- de rising_edge(clk) 
	end process seudocodigo; 
end architecture ... ;
```
Se define una señal, llamada ``state``, cuyo valor indica qué paso del algoritmo se está ejecutando en cada momento.
El seudocódigo es traducido esencialmente a un bloque **process**, que es sensible a la señal de reset (``reset_n``) y a la señal de reloj (``clk``). El circuito descrito por la plantilla tiene reset asíncrono activado LOW. Las acciones de reset son las definidas en el Paso 0 del seudocódigo. Además, en la operación de reset se asigna a la señal state su valor inicial.
Cada vez que se produce un flanco de subida de la señal de reloj se ejecutan dos sentencias concurrentes. La primera de ellas incrementa el valor de la señal state. La otra es un bloque case, que ejecuta las sentencias del correspondiente paso del seudocódigo. Obsérvese que el bucle for del seudocódigo, mostrado en la parte de la izquierda, se ha traducido de la forma mostrada en la parte de la derecha:
![](img/Pasted%20image%2020250510133934.png)
## 7.5. CIRCUITO DETECTOR DE SECUENCIA
Supongamos que deseamos diseñar un circuito para la detección de la siguiente secuencia de entrada serie: 0111 1110. El siguiente programa RT permite resolver este problema:
```
Paso O.     prev_data <- 1111 1111;               /*Almacena 8 bits anteriores*/
			while (true) do                       /*Se repite indefinidamente*/
				data_in <- siguiente dato de entrada;
				prev_data <- prev_data << 1       /*Desplazamiento izqda*/
				prev_data[0] <- data_in;          /*Se almacena data_in en LSB*/
				if (prev_data == 0111 1110) then  
					detectado <- 1;               /*Secuencia detectada*/
				else 
					detectado <- 0;               /*Secuencia no detectada*/
			end while
```
Dos diseños de un circuito detector de la secuencia 0111 1110, una en la cual ``prev_data`` es una variable y otra en la cual es una señal.
```vhdl
-- Circuito detector de secuencia 0111 1110 
-- Fichero: detector_sec.vhd 
library IEEE; 
use IEEE.std_logic_1164.all;
use IEEE.numeric_std.all; 

entity detector_sec is 
	port ( detectado : out std_logic; 
		   reset_n : in std_logic; 
		   clk : in std_logic; 
		   data_in : in std_logic ) ; 
end entity detector _sec; 

architecture detector sec1 of detector sec is 
begin 
	process (reset_n, clk) is 
		variable prev_data : unsigned (7 downto 0); 
	begin 
		if (reset_n = '0') then
			prev_data := B"1111_1111"; 
		elsif rising_edge( clk) then 
			prev_data := prev_data sll 1; -- sll = leftshiftlogical
			prev_data(0) := data_in; 
			if (prev_data = B"0111_1110") then 
				detectado <= '1'; 
			else 
				detectado <= '0'; 
			end if;
		end if; 
	end process; 
end architecture detector_sec1; 

architecture detector_sec2 of detector_sec is 
	signal prev_data : unsigned (7 downto 0); 
begin 
	process (reset_n, clk) is 
	begin 
		if (reset_n = '0') then
			prev_data <= B"1111_1111"; 
		elsif rising_edge(clk) then 
			prev_data <= (prev_data(6 downto 0) & data_in); 
			if ((prev_data(6 downto 0) & data_in) = B"0111_1110") then 
				detectado <= '1 '; 
			else 
				detectado <= '0'; 
			end if; 
		end if; 
	end process; 
end architecture detector_sec2;
```
La única diferencia entre la descripción en VHDL y la descripción algorítmica, aparte del uso de la sintaxis de VHDL, es que en el código VHDL no se ha incluido la sentencia`` data_in <- siguiente dato de entrada;`` En el código VHDL no es necesario realizar la asignación del siguiente bit de la secuencia de entrada a ``data_in``, porque se supone que los bits de datos entran en sincronía con el flanco de subida de la señal de reloj.
La sentencia ``prev_data <= (prev_data(6 downto O) & data_in);`` realiza un desplazamiento lógico de un bit hacia la izquierda e inserta ``data_in`` en el bit menos significativo.

Puesto que la asignación a señales no tiene efecto inmediatamente, sino un delta de tiempo posterior al tiempo simulado actual, esta operación de desplazamiento se ejecuta concurrentemente con la sentencia **if** que comprueba la igualdad con B"0111_1110". Puesto que el valor de ``prev_data`` todavía no ha sido actualizado en el momento en que se realiza la comparación, es necesario realizar la comparación usando el valor de ``prev_data`` anterior al desplazamiento.
## 7.6. CONTROL DE UNA MÁQUINA EXPENDEDORA
Se plantea el problema de diseñar un circuito de control para una máquina automática expendedora de dos tipos de bebida: botellas de agua y latas de refresco. La máquina sólo acepta monedas de 10 céntimos, 20 céntimos y 50 céntimos. El precio de una botella de agua es 70 céntimos y el de una lata de refresco es 60 céntimos.
En la siguiente tabla se resumen las entradas al circuito.
![](img/Pasted%20image%2020250510135849.png)
En la siguiente tabla se muestran algunas de las señales de salida del circuito.
![](img/Pasted%20image%2020250510140126.png)
- Las señales ``dispensa_refresco``, ``dispensa_agua`` y ``devuelve_cambio`` se usan para controlar la entrega al cliente de una lata de refresco, una botella de agua, y del dinero que ha introducido en la máquina y aun no ha gastado (es decir, del cambio). 
- La señal ``beep`` sirve para indicar al cliente que no ha introducido dinero suficiente para comprar el producto que ha seleccionado. Por tanto, esta señal se activa cuando el cliente selecciona un producto sin haber introducido el dinero suficiente para comprarlo. 
- En la señal ``total``, de 5 bits, se lleva la cuenta del dinero que ha introducido el cliente en la máquina y que todavía no ha gastado.
- La señal ``devuelve_moneda`` se activa si el cliente introduce más dinero del que puede ser almacenado en la señal total. En este caso, se devuelve la última moneda introducida por el cliente.
### 7.6.1. Protocolo de handshaking
El circuito de control de la máquina expendedora se diseñará usando un protocolo de *handshaking* de cuatro fases. En este circuito, la interfaz de handshaking se establece entre el cliente, que realiza una selección, y la máquina, que responde a la selección del cliente.
El protocolo *handshaking* de cuatro fases permite comunicar asíncronamente dos circuitos, que llamaremos A y B. Los dos circuitos están comunicados mediante un bus, por el que circulan los datos que se desean transmitir desde A a B, y por dos señales, ``req`` (petición) y ``ack`` (recepción), que se emplean para implementar el protocolo, el cual funciona de la manera siguiente:
1. El circuito A comprueba si ``ack='0'``. En caso afirmativo, pone en el bus el dato que quiere transmitir al circuito B y cambia el valor de la señal ``req`` de '0' a '1'. 
2. El circuito B, al detectar que ``req`` pasa de valer '0' a valer '1 ', carga el dato (por ejemplo, en latches), lo procesa y entonces cambia el valor de la señal ``ack`` de '0' a '1'. Con ello indica al circuito A que ha recibido los datos y los ha procesado. 
3. El circuito A espera hasta que detecta ``ack='1'``, lo cual indica que los datos han sido recibidos y procesados, y entonces el circuito A pone ``req='0'``. 
4. Al ver el circuito B que el circuito A ha puesto ``req='0'``, entonces pone ``ack='0'``, quedando así preparado para la recepción del siguiente dato. 
5. Finalmente, el circuito A debe esperar hasta que ``ack='0'`` para enviar el siguiente dato y poner de nuevo ``req='1' ``(que es nuevamente el primer paso del protocolo).
### 7.6.2. Descripción del algoritmo
A continuación, se muestra el algoritmo que debe implementar el circuito de la máquina expendedora. En el algoritmo se representa el dinero en unidades de 10 céntimos, ya que todas las entradas, salidas y cálculos internos pueden realizarse usando múltiplos de 10 céntimos. Esto permite usar menos bits en el registro total. Todas las selecciones del cliente (agua, refresco o devolución del dinero), así como la entrada de monedas (10 céntimos, 20 céntimos y 50 céntimos), están codificadas en una única señal de entrada al circuito, llamada data, de 3 bits. La codificación es la mostrada en la tabla. Obsérvese que la codificación de las monedas coincide con su valor en múltiplos de 10 céntimos.
![](img/Pasted%20image%2020250510142703.png)
Al observar ``req='1'``, el circuito decodifica la señal de 3 bits data para determinar la acción solicitada, realiza las acciones solicitadas y a continuación, usando la señal ``ack``, notifica que ya ha realizado la acción solicitada.
### 7.6.3. Diseño del circuito de control
```
Algoritmo del circuito de la máquina expendedora: 
Paso 0. total<4:0> <- 0;           ack <- 0; 
        beep <- 0;                 devuelve_moneda <- O; 
        dispensa_refresco <- O;    dispensa_agua <- O; 
        devuelve_cambio <- 0;      MAX <- 31; 
        
        while (true) do begin
        
Paso 1.    wait until (req=1); 

Paso 2.    case (data) is begin 
		   m10, m20 or m50: 
			   if (total + data > MAX) then 
				   devuelve_moneda <- 1; 
				else 
					total <- total + data; 
				end if; 
			selec_refresco: 
				if (total < 6) then 
					beep <- 1; 
				else 
					total <- total - 6; 
					dispensa_refresco <- 1; 
				end if; 
			selec_agua: 
				if (total < 7) then 
					beep <- 1; 
				else 
					total <- total - 7; 
					dispensa_agua <- 1; 
				end if; 
				devolucion: 
					devuelve_cambio <- 1; 
					total <- O; 
			end /* de case (data) */
Paso 3.     ack <- 1 until (req=O); 
Paso 4.     ack <- O;                beep <- 0;
			devuelve_moneda <- O;    dispensa_refresco <- 0;
			dispensa_agua <- O;      devuelve_cambio <- 0;
		end /* del bucle while */
```

```vhdl
-- Definición de las constantes 
-- Fichero: maqExpend_defs.vhd 
library IEEE; 
use IEEE.std_logic_1164.all; 
use IEEE.numeric_std.all; 

package maqExpend_defs is 
	constant TOTAL_BITS : integer := 5; -- Bits del registro total 
	constant MAX : integer := 31; -- Num. máx. en el registro total 
	constant ESTADO_BITS : integer := 2; -- Bits del estado de la máquina 
	constant DATA_BITS : integer := 3; -- Bits de la señal data 
	constant DATA_m10 : unsigned(DATA_BITS-1 downto 0) := "001"; 
	constant DATA_m20 : unsigned(DATA_BITS-1 downto 0) := "010"; 
	constant DATA_m50 : unsigned(DATA_BITS-1 downto 0) := "101"; 
	constant DATA_devolucion : unsigned(DATA_BITS-1 downto 0) := "100"; 
	constant DATA_selec_agua : unsigned(DATA_BITS-1 downto 0) := "011"; 
	constant DATA_selec_refresco : unsigned(DATA_BITS-1 downto 0) := "000"; 
end package maqExpend_defs;
```
La definición de las constantes se agrupa en un **package**.
Las constantes ``TOTAL_BITS`` y ``DATA_BITS`` representan el número de bits del registro ``total`` y el número de bits de la señal ``data``, respectivamente. También se define una constante por cada uno de los valores que puede tener la señal ``data``. 
```vhdl
-- Circuito de la máquina expendedora 
-- Fichero: maquinaExpend.vhd 
library IEEE; 
use IEEE.std_logic_1164.all;
use IEEE.numeric_std.all; 
use work.maqExpend_defs.all; 

entity maquinaExpend is 
	port ( total              : out unsigned(TDTAL_BITS-1 downto 0); 
		   ack                : out std_logic; 
		   beep               : out std_logic;
		   devuelve_moneda    : out std_logic;
		   dispensa_refresco  : out std_logic;
		   dispensa_agua      : out std_logic;
		   devuelve_cambio    : out std_logic;
		   req                : in std_logic;
		   data               : in unsigned(DATA_BITS-1 downto 0);
		   reset_n            : in std_logic; -- Reset asíncrono activado LOW
		   clk                : in std_logic ); 
end entity maquinaExpend; 

architecture maquinaExpend of maquinaExpend is 
	signal total_int : unsigned(TDTAL_BITS-1 downto 0); 
	signal estado    : unsigned(ESTADO_BITS-1 downto 0); 
begin 
	total <= total_int; 
	algoritmo : process (reset_n, clk) is 
	begin 
		if (reset_n = '0') then 
			total_int <= ( others = > '0'); -- Inicializa el registro 
			ack               <= '0'; 
			beep              <= '0'; 
			devuelve_moneda   <= '0'; 
			dispensa_refresco <= '0'; 
			dispensa_agua     <= '0'; 
			devuelve_ cambio  <= '0'; 
			estado            <= "00"; --Estado inicial 
		elsif rising_edge(clk) then 
			estado <= estado + 1; -- Actualiza estado para el siguiente pulso de reloj 
			case estado is -- Los pasos del algoritmo se codifican como estados 
				when "00" => 
					if (req = '0') then --Espera hasta que (req='1') 
						estado <= "00"; 
					end if;
				when "01" =>
					case (data) is 
						when DATA_m10 | DATA_m20 | DATA_m50 => 
							if ( (total_int + data) > MAX ) then 
								devuelve_moneda <= '1'; 
							else 
								total_int <= total_int + data; 
							end if;
						when DATA_selec_refresco => 
							if (total_int < 6) then 
								beep <= '1'; 
							else 
								total_int <= total_int - 6; 
								dispensa_refresco <= '1'; 
							end if; 
						when DATA_selec_agua => 
							if (total_int < 7) then 
								beep <= '1'; 
							else 
								total_int <= total_int - 7; 
								dispensa_agua <= '1'; 
							end if; 
						when DATA_devolucion => 
							total_int <= (others => '0'); 
							devuelve_cambio <= '1'; 
						when others => 
							assert false report "Caso indefinido."; 
					end case; 
				when "10" => 
					ack <= '1'; 
					if (req = '1') then -- Espera hasta que (req= '0') 
						estado <= "10"; 
					end if; 
				when others => 
					ack <= '0'; 
					beep <= '0'; 
					devuelve_moneda <= '0'; 
					dispensa_refresco <= '0'; 
					dispensa_agua <= '0'; 
					devuelve_cambio <= '0'; 
			end case; -- case estado 
		end if; 
	end process algoritmo; 
end architecture maquinaExpend;
```
La señal de entrada ``data`` está codificada tal como se indica en la tabla. La señal ``reset_n`` es una señal de reset asíncrono activada LOW. 
Las operaciones del Paso 0 del seudocódigo se ejecutan cuando ``(reset_n = '0')``. Asimismo, en esta parte del código se inicializa la señal ``estado``, que representa el estado actual en el que se encuentra la máquina. 
En cada flanco de subida de la señal de reloj, un bloque **case** comprueba el valor del estado (señal ``estado``). Las operaciones del Paso 1 del seudocódigo son ejecutadas cuando ``estado='0'``. Las operaciones del Paso 2 son ejecutadas cuando ``estado=1``. Continuando de esta manera, las operaciones del Paso k + 1 del seudocódigo son ejecutadas cuando ``estado=k``.
### 7.6.4. Programación del banco de pruebas
```vhdl
-- Banco de pruebas para el circuito de la máquina expendedora 
-- Fichero: bp_maquinaExpend.vhd 
library IEEE; 
use IEEE.std_logic_1164.all; 
use IEEE.numeric_std.all; 
use work.maqExpend_defs.all; 

entity bp_maquinaExpend is 
end entity bp_maquinaExpend; 

architecture bp_maquinaExpend of bp_maquinaExpend is 
	component maquinaExpend is 
		port ( total : out unsigned(TOTAL_BITS-1 downto 0); 
			   ack : out std_logic; 
			   beep : out std_logic; 
			   devuelve_moneda : out std_logic; 
			   dispensa_refresco : out std_logic; 
			   dispensa_agua : out std_logic; 
			   devuelve_cambio : out std_logic; 
			   req : in std_logic; 
			   data : in unsigned(DATA_BITS-1 downto 0); 
			   reset_n : in std_logic; 
			   clk : in std_logic ) ; 
	end component maquinaExpend; 
	
	constant PERIODO : time := 100 ns; -- Periodo señal de reloj 
	signal total             : unsigned(TOTAL_BITS-1 downto 0); 
	signal ack               : std_logic;
	signal beep              : std_logic;
	signal devuelve_moneda   : std_logic;
	signal dispensa_refresco : std_logic;
	signal dispensa_agua     : std_logic;
	signal devuelve_cambio   : std_logic;
	signal req               : std_logic; 
	signal data              : unsigned(DATA_BITS-1 downto 0); 
	signal reset_n           : std_logic;
	signal clk               : std_logic;
begin         
	uut : maquinaExpend port 
		map ( total, ack ,beep, devuelve_moneda, dispensa_refresco, dispensa_agua, devuelve_cambio, req, data, reset_n, clk );
	-- Crea un pulso de reset 
	reset_n <= '1', 
			   '0' after (PERIOD0*3/ 4), 
			   '1' after (2*PERIODO);
	-- Señal de reloj 
	clock : process is 
	begin 
		clk <= '0'; wait for (PERIOD0/2); 
		clk <= '1'; wait for (PERIOD0/2); 
	end process clock; 
	-- Vectores de test 
	generar_vectores: process is 
	begin 
		req <= '0'; data <= (others = > '0'); 
		wait for (PERIOD0*3); wait for (PERIOD0/4); 
		
		req <= '1'; data <= DATA_m50; -- Introduce moneda de 50 cent. 
		wait for (PERIOD0*5); 
		req <= '0'; wait for (PERIOD0*2); 
		
		req <= '1'; data <= DATA_m20; -- Introduce moneda de 20 cent. 
		wait for (PERIOD0*3); 
		req <= '0'; wait for (PERIOD0*2); 
		
		req <= '1'; data <= DATA_selec_agua; -- Selecciona agua 
		wait for (PERIOD0*3); 
		req <= '0'; wait for (PERIOD0*2); 
		...
		report "Final de la simulación"; 
	end process generar_vectores; 
end architecture bp_maquinaExpend;
```