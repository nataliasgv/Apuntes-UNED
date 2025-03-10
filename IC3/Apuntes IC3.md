# 1. Fundamentos del diseño del hardware digital
## 1.1. INTRODUCCIÓN
El lenguaje para la descripción del hardware o HDL (siglas que provienen del inglés: Hardware Description Language) es un lenguaje, legible tanto por las máquinas como por los seres humanos, ideado para describir tanto el comportamiento como la estructura del hardware.
El HDL que el Departamento de Defensa de EE.UU. creó en los años 80 se llamó VHDL. Las siglas VHDL provienen de VHSIC Hardware Description L.anguage. VHSIC es un acrónimo de Very High Speed Integrated Circuit, que fue el nombre del proyecto llevado a cabo por el Departamento de Defensa de EE.UU.
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
![[Pasted image 20250219142041.png]]
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
![[Pasted image 20250302184436.png]]
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

![[Pasted image 20250302200306.png]]
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
1. U na forma es almacenar en un fichero las salidas de un circuito que funcione correctamente, y compararlas con las salidas obtenidas. 
2. Otro procedimiento consiste en calcular la salida esperada del circuito usando un método diferente al empleado en el test, y comparar los resultados. Cuando no es posible aplicar un método de cálculo alternativo al del test, puede comprobarse si los resultados obtenidos del test son "razonables".
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
![[Pasted image 20250302213053.png]]
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
```
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
```
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
`signal p1, p2, p3, p4 : std_logic; `

Las señales p1, p2, p3 y p4 pueden ser interpretadas como conexiones entre las partes internas. La declaración es visible sólo dentro de la **architecture**.

La descripción de la **architecture** está comprendida entre **begin** y **end architecture**. Está compuesta por cinco *asignaciones concurrentes a señales*:

```
	par <= ( p1 or p2 ) or ( p3 or p4 ) after 20 ns; 
	p1 <= ( not a(2) ) and ( not a(1) ) and ( not a(O) ) after 15 ns; 
	p2 <= ( not a(2) ) and a(1) and a(O) after 12 ns; 
	p3 <= a(2) and ( not a(1) ) and a(O) after 12 ns; 
	p4 <= a(2) and a(1) and ( not a(O) ) after 12 ns;
```

Una asignación concurrente puede ser interpretada como un bloque del circuito. La señal de la izquierda de la asignación es la salida del bloque. Todas las señales que intervienen en la parte derecha de la asignación son las entradas al bloque. El resultado está disponible tras un cierto retardo, que se especifica mediante la cláusula **after**. 
Ej:
`par <= ( p1 or p2 ) or ( p3 or p4 ) after 20 ns;`
Bloque circuital con entradas p1, p2, p3 y p4, y salida par. El bloque realiza la operación OR de las cuatro entradas, y la operación tarda 20 ns en realizarse.

Esta **architecture** contiene cinco asignaciones concurrentes, que son interpretadas como cinco bloques circuitales. Las asignaciones concurrentes están conectadas a través de las señales que tienen en común. Cuando una señal aparece en la parte izquierda de una asignación y en la parte derecha de otra, esto significa que hay una conexión entre el bloque circuital representado por la primera asignación y el bloque circuital representado por la segunda.
![[Pasted image 20250303123116.png]]

Puesto que cada sentencia de asignación concurrente representa una parte del circuito y su interconexión, el orden en que se escriben las sentencias de asignación concurrente es indiferente.

Al contrario de lo que sucede con las sentencias en un lenguaje de programación, las *sentencias concurrentes* de asignación a señal son independientes entre sí, y pueden activarse en paralelo. Si alguna de las señales de entrada cambia de valor en el instante *t*, la sentencia concurrente es activada en dicho instante *t*. Es decir:
1. Se evalúa la expresión de la parte derecha de la asignación, usando para ello el valor que tienen las señales de entrada en dicho instante t. 
2. Se planifica asignar a la señal de salida (la situada en la parte izquierda de la asignación) el valor calculado, de manera que el nuevo valor se asignará a la señal una vez haya transcurrido el retardo de propagación especificado en la sentencia de asignación.

Como se explicó anteriormente, cuando se realiza el diseño de alto nivel frecuentemente se desconoce el valor del retardo de los bloques circuitales, ya que todavía no se ha realizado la síntesis. Es decir, no se ha especificado cómo va a implementarse en hardware el bloque circuital. Por este motivo, ==en el diseño de alto nivel de los circuitos no suele indicarse explícitamente el valor del retardo, omitiéndose la cláusula **after** en las sentencias de asignación a señal.==
Puede escribirse:
`par<= (pi or p2) or (p3 or p4 );`
Que se interpreta como:
`par <= (pi or p2 ) or (p3 or p4 ) after δ;`

El circuito puede ser descrito mediante la función lógica siguiente:

$$
par = (a_2 \oplus a_1 \oplus a_0)'
$$
El cuerpo de la architecture basado en esta función lógica:
```
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
![[Pasted image 20250303124504.png]]
### 1.8.2. Descripción de la estructura
En la visión estructural, el circuito está compuesto de *componentes* (esto es, bloques circuitales) conectados entre sí. La descripción especifica el tipo de cada componente y su conexión. Para ello, en el cuerpo de la **architecture**, el componente primero debe ser *declarado*, y a continuación *instanciado* y *conectado*.
![[Pasted image 20250303124848.png]]
Esta descripción corresponde con la función lógica $par = (a_2 \oplus a_1 \oplus a_0)'$
En el siguiente código se define la puerta inversora y la puerta XOR de dos entradas.
```
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
```
component xor2 is 
		port ( yO : out std_logic; 
				xO, x1 : in std_logic );
	end component xor2; 
```
La información contenida dentro de la declaración es similar a la declaración de la entity del componente, en la cual se especifican sus puertos de entrada y salida. 

Aparte de la declaración de los componentes, en la architecture se declaran también dos señales internas:
`signa! s1, s2 : std_logic;`

El cuerpo de la architecture consiste en tres sentencias, en cada una de las cuales se instancia y conecta un componente:
`unit1 : xor2 port map ( xO => a(O), x1 => a(1), yO=> s1 );`
Hay tres elementos en esta sentencia. El primero es la etiqueta **unit1**, que sirve para designar este componente. El segundo es la clase del componente: **xor2**. La tercera es **port map ( ... )**, que define la correspondencia entre las señales formales (puertos definidos en la entity del componente) y las señales actuales (las señales usadas en el cuerpo de la **architecture**).
En este ejemplo, port map ( ... ) indica que xO, x1, yO están conectadas a a(O), a(1), s1 respectivamente.

Las tres instanciaciones de los componentes describen el circuito completo.
La instanciación de un componente es un tipo de sentencia concurrente y puede mezclarse en el cuerpo de una architecture con otros tipos de sentencias concurrentes, tales como las sentencias de asignación concurrente a señal o como los bloques process, que explicaremos a continuación.

### 1.8.3. Descripción abstracta del comportamiento
En un diseño grande, la implementación puede ser muy compleja. Por este motivo, el diseño se realiza en diferentes pasos, progresando desde una descripción inicial abstracta del funcionamiento del circuito, independiente de la plataforma hardware que vaya a usarse para implementar el circuito, hasta llegar a la descripción detallada al nivel hardware.

El lenguaje VHDL facilita al diseñador realizar una descripción abstracta del comportamiento del circuito. Uno de los recursos que proporciona para ello el lenguaje son los bloques **process**. ==Un bloque **process** es una construcción que encapsula un fragmento de código VHDL secuencial, y dentro de la cual pueden declararse y usarse variables, que son locales al bloque **process**.== La característica distintiva del código secuencial es que es ejecutado en el mismo orden en el cual ha sido escrito. La sintaxis básica del bloque **process** es la siguiente:
```
process ( lista_de_sensibilidad ) 
	Declaración de variables locales 
begin 
	Código_secuencial 
end process;
```

==En el bloque **process** puede especificarse una lista de señales, denominada *lista de sensibilidad*, que defina las condiciones para la ejecución del bloque: cuando cambia el valor de alguna de las señales incluidas en esta lista, entonces se ejecuta el cuerpo del bloque **process**.==
Ejemplos de descripción abstracta del comportamiento del circuito detector de un número par de entradas '1':
1.
```
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
![[Pasted image 20250303131004.png]]
La **architecture** *comp_red_xor* contiene un bloque *process*, que utiliza una variable y un bucle **for**. Al contrario de lo que sucede con las señales y las asignaciones a señales, la variable y el bucle no tienen una correspondencia directa con el hardware. El bloque **process** se trata como una unidad indivisible, cuyo comportamiento es especificado mediante sentencias secuenciales.

2.
```
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
![[Pasted image 20250303131321.png]]
El segundo ejemplo usa únicamente un bloque **process**, en el cual se describe el algoritmo que realiza la operación que se desea que realice el circuito. En primer lugar, el algoritmo suma el número de '1' en las entradas, calcula el resto de la división entre 2, y finalmente usa una sentencia if para generar el resultado en función del valor del resto de la división.
### 1.8.4. Banco de pruebas
Uno de los usos principales de un programa en VHDL es la simulación, que se usa para ==estudiar la operación del circuito y para verificar que el diseño se ha realizado correctamente.==
Se pueden programar unas rutinas en VHDL que generen los vectores de test y otras que comparen las respuestas obtenidas de aplicar los vectores de test al circuito, con las respuestas que deberían obtenerse del circuito.
Ej de banco de pruebas para el circuito detector de un número par de entradas '1':
```
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
![[Pasted image 20250303133640.png]]
### 1.8.5. Configuración
El lenguaje VHDL separa de manera intencionada la declaración de la **entity** y la **architecture** en dos. unidades de diseño independientes. Esto facilita asociar múltiples **architecture** con una determinada **entity**.
A la hora de realizar la simulación y la síntesis, debemos especificar qué **architecture** asociar con la **entity**. Esto puede hacerse definiendo una **configuration**, como la mostrada a continuación para nuestro circuito ejemplo. Si no se ha definido una **configuration**, el entorno de simulación escogerá por defecto la última **architecture** que ha sido compilada.
```
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

```
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
```
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
```
entity bp_detectorPar is 
end entity bp_detectorPar; 
```
que sólo contiene el nombre asignado a la **entity**, ``bp_detectorPar``, y las siguientes palabras reservadas del lenguaje: **entity**, **is** y **end**. ==En la entity se declara la lista de señales que componen la interfaz del circuito. A estas señales de la interfaz se las denomina *puertos*.== Dado que la interfaz del banco de pruebas no contiene ninguna señal, en su entity no se declara ningún puerto.
![[Pasted image 20250310132309.png]]
	Interfaces de las puertas NOT, XOR y AND
### 2.3.1. Cláusula port
Las señales de la interfaz, a las que se denomina puertos, se declaran mediante la cláusula opcional port, en la cual se indica el nombre de los puertos, su modo y su tipo. La sintaxis es:
```
entity nombre_entity is 
	port ( 
		nombres_puertos nombres_puertos modo tipo_dato; modo tipo_dato; nombres_puertos modo tipo_dato ) ; end entity nombre_entity;
```