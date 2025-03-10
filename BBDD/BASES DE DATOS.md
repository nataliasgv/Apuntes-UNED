# TEMA 1 Introducción
## 1.1. Aplicaciones de los sistemas de bases de datos
Un **sistema gestor de bases de datos (SGBD)** consiste en una colección de datos interrelacionados y un conjunto de programas para acceder a dichos datos. La colección de datos, normalmente denominada **base de datos**, contiene información relevante para una . a. El objetivo principal de un SGBD es proporcionar una forma de almacenar y recuperar la información de una base de datos de manera que sea tanto práctica como eficiente.
Aplicaciones de los sistemas de bases de datos:
- Banca: cualquier tipo de transacción
- Líneas aéreas: reservas, información de planificación, etc.
- Universidades: registros, cursos
- Ventas: información de clientes, productos y compras 
- Minoristas en línea: seguimiento de órdenes, recomendaciones personalizadas
- Producción: producción, inventarios, pedidos, cadena de producción
- Recursos humanos: información sobre los empleados, salarios, impuestos y beneficios
## 1.2. Propósito de los sistemas de bases de datos
Inicialmente, las aplicaciones de los sistemas de bases de datos se construyeron encima de los sistemas de archivos.

- Inconvenientes de utilizar sistemas de archivos para almacenar datos: – Redundancia e inconsistencia de datos
- Diversos formatos de archivos, duplicación de la información en archivos diferentes – Dificultad en el acceso a los datos 
- Necesidad de escribir un programa nuevo por cada tarea nueva 
- Aislamiento de datos — diversos archivos con diferentes formatos – Problemas de integridad 
    - Restricciones de consistencia (p. e. el saldo de una cuenta bancaria > 0) pasan a formar parte del código del programa
    - Dificultad para añadir restricciones nuevas o modificar las existentes
- Problemas de atomicidad -
    - Los fallos pueden dejar a las bases de datos en un estado de inconsistencia si se han llevado a cabo actualizaciones parciales 
    - Por ejemplo, la transferencia de fondos de una cuenta bancaria a otra debe ser completa o no llevarse a cabo 
- Anomalías en el acceso concurrente 
	-  Se necesita el acceso concurrente para obtener un buen rendimiento 
	- El acceso concurrente sin control puede conducir a tener datos inconsistentes 
		- P. e. dos personas leyendo y actualizando un saldo al mismo tiempo
- Problemas de seguridad 
	- Dificultad de proporcionar acceso a parte de los datos pero no a todos

## 1.3. Visión de los datos
Un sistema de base de datos es una **colección de datos interrelacionados y un conjunto de programas que permiten a los usuarios tener acceso a esos datos y modificarlos**. Una de las principales finalidades de los sistemas de bases de datos es ofrecer a los usuarios una **visión abstracta de los datos**. Es decir, el sistema oculta ciertos detalles del modo en que se almacenan y mantienen los datos.

### 1.3.1. Abstracción de datos
Los desarrolladores ocultan esa complejidad a los usuarios mediante varios niveles de abstracción para simplificar la interacción de los usuarios con el sistema:

- Nivel físico: describe **cómo** se almacenan realmente los datos 
- Nivel lógico: describe **qué** datos se almacenan en la base de datos y las relaciones existentes entre ellos.
- Nivel de vistas: los programas de aplicación ocultan detalles de los tipos de datos. Las vistas también pueden ocultar información por razones de seguridad.

### 1.3.2. Ejemplares y esquemas
La colección de información almacenada en la base de datos en un momento dado se denomina **ejemplar** de la base de datos El diseño general de la base de datos se denomina **esquema** de la base de datos. Los esquemas se modifican rara vez, si es que se modifican.
El esquema de la base de datos se corresponde con las declaraciones de las variables (junto con las definiciones de tipos asociadas) de los programas. Cada variable tiene un valor concreto en un instante dado. Los valores de las variables de un programa se corresponden en cada momento con un ejemplar del esquema de la base de datos.

- Esquema físico: diseño de la base de datos a nivel físico  
- Esquema lógico: diseño de la base de datos a nivel lógico
**Independencia física de los datos**: la capacidad de modificar el esquema físico sin cambiar el esquema lógico.

### 1.3.3. Modelos de datos
Colección de herramientas conceptuales para describir los datos, sus relaciones, su semántica y las restricciones de consistencia. Los modelos de datos pueden clasificarse en cuatro categorías diferentes:
- **Modelo relacional**: utiliza una colección de tablas para representar tanto los datos como sus relaciones. El modelo relacional es un ejemplo de modelo basado en registros.
- **Modelo entidad-relación**: colección de objetos básicos, denominados entidades, y de las relaciones entre ellos. 
- **Modelo de datos orientado a objetos**: extensión del modelo E-R con conceptos de encapsulación, métodos (funciones) e identidad de objetos 
- **Modelo de datos semiestructurados (XML)**: permite una especificación de datos en el que los elementos de datos individuales del mismo tipo pueden tener diferentes conjuntos de atributos.
- Modelos anteriores:
	-  Modelo de red 
	-  Modelo jerárquico

## 1.4. Lenguajes de bases de datos
- Los sistemas de bases de datos proporcionan: 
	- **Lenguaje de definición de datos (LDD)** para especificar el esquema de la base de datos 
	- **Lenguaje de manipulación de datos (LMD)** para expresar las consultas y las modificaciones de la base de datos
Los lenguajes de definición y manipulación de datos no son dos lenguajes diferentes; simplemente forman parte de un único lenguaje de bases de datos, como puede ser el muy usado SQL.

### 1.4.1. Lenguaje de manipulación de datos
Lenguaje para acceder o manipular los datos organizados mediante el modelo de datos apropiado.
Los tipos de acceso a la información almacenada en la BD son: 
- Inserción de información 
- Recuperación de información 
- Borrado de información 
- Modificación de información almacenada en la base de datos
Existen dos clases de lenguajes 
- **Procedimentales**: el usuario especifica *qué* datos se necesitan y *cómo* han de obtenerse dichos datos 
- **Declarativos** (no procedimentales): el usuario especifica *qué* datos se necesitan *sin* especificar cómo se han de obtener.
Una *consulta* es una instrucción que solicita recuperar información. La parte de los LMD implicada en la recuperación de información se denomina **lenguaje de consultas**. SQL es el lenguaje de consultas utilizado más ampliamente.

### 1.4.2. Lenguaje de definición de datos
Para especificar los esquemas de las bases de datos y propiedades de los datos.
La estructura de almacenamiento y los métodos de acceso usados por el sistema de bases de datos se especifican mediante un conjunto de instrucciones denominado **lenguaje de almacenamiento y definición de datos**. 
Los valores de los datos almacenados en la base de datos deben satisfacer ciertas restricciones de consistencia que permite especificar el LDD y que los sistemas de bases de datos los comprueban cada vez que se accede a la base de datos.
- Restricciones de dominio: valores posibles de cada atributo o restricciones de los datos
- Integridad referencial: datos compartidos en diferentes partes deben ser iguales
- Asertos: condiciones que deben verificar los datos (además de dominio e integridad)
- Autorización: diferenciar usuarios en cuanto al tipo de acceso (lectura, inserción, borrado, etc)
El LDD, al igual que cualquier otro lenguaje de programación, obtiene como entrada algunas instrucciones (sentencias) y genera una salida. La salida del LDD se coloca en el diccionario de datos, que contiene metadatos, es decir, datos sobre datos. El diccionario de datos se considera un tipo especial de tabla, solo accesible y actualizable por el propio sistema de bases de datos (no por los usuarios normales). El sistema de bases de datos consulta el diccionario de datos antes de leer o modificar los datos reales.

## 1.5. Bases de datos relacionales
Las bases de datos relacionales se basan en el modelo relacional y usan un conjunto de tablas para representar tanto los datos como las relaciones entre ellos.

### 1.5.1. Tablas
Cada fila o tupla representa un objeto único de datos implícitamente estructurados en una tabla
Cada tabla tiene varias columnas, y cada columna tiene un nombre único.
	El modelo relacional es un modelo basado en registros o tuplas (la base de datos se estructura en registros de formato fijo).
	Las columnas de la tabla se corresponden con los atributos de cada tupla
El modelo relacional oculta detalles de implementación de bajo nivel a los desarrolladores de bases de datos y a los usuarios. 
En el modelo relacional es posible crear esquemas que tengan problemas tales como información duplicada, redundante, inconsistente …. que habrá que evitar.

| ID    | nombre   | nombre_dept | sueldo |
| ----- | -------- | ----------- | ------ |
| 2222  | Einstein | Física      | 95.000 |
| 12121 | Wu       | Finanzas    | 90.000 |
| 34324 | Kafz     | Informática | 75.000 |
| ...   | ...      | ...         | ...    |
Tabla profesor

| nombre_dept | edificio | presupuesto |
| :---------- | -------- | ----------- |
| Física      | Watson   | 70.000      |
| Finanzas    | Painter  | 120.000     |
| Informática | Taylor   | 100.000     |
| ...         | ...      | ...         |
Tabla departamento

### 1.5.2. SQL como LMD
El lenguaje de consultas de SQL no es procedimental. Usa como entrada varias tablas (posiblemente solo una) y devuelve siempre una única tabla.
Ejemplo de consulta SQL que halla el nombre de todos los profesores del departamento de Historia: 
```
select profesor.nombre 
from profesor 
where profesor.nombre_dept = «Historia»
```
La consulta especifica que hay que recuperar (*select*) las filas de (*from*) la tabla profesor en las que (*where*) el *nombre_dept* es Historia, y que solo debe mostrarse el atributo *nombre* de esas filas. Más concretamente, el resultado de la ejecución de esta consulta es una tabla con una sola columna denominada *nombre* y un conjunto de filas, cada una de las cuales contiene el nombre de un profesor cuyo *nombre_dept* es Historia.
Ej de más de una tabla, la siguiente consulta busca todos los ID de profesor y el nombre del departamento de todos los profesores con un departamento cuyo presupuesto sea superior a 95.000 €.

```
select profesor.ID, departamento.nombre_dept
from profesor, departamento
where profesor.nombre_dept = departamento.nombre_dept and departamento.presupuesto > 95000;
```

### 1.5.3. SQL como LDD
SQL proporciona un rico LDD que permite definir tablas, restricciones de integridad, aserciones, etc.
Ej, la siguiente instrucción LDD del lenguaje SQL define la tabla departamento:
```
create table departamento
(nombre_dept char (20), 
edificio char (15), 
presupuesto numeric (12,2));
```
Crea la tabla *departamento* con tres columnas: *nombre_dept*, *edificio* y *presupuesto*, cada una de ellas con su tipo de datos específico asociado.
### 1.5.4. Acceso a las bases de datos desde los programas de aplicación
Los programas de aplicación son programas que se usan para interactuar de esta manera con las bases de datos.
Para tener acceso a la base de datos, las instrucciones LMD deben ejecutarse desde el lenguaje anfitrión. Hay dos maneras de conseguirlo:
- Proporcionando una interfaz de programas de aplicación (conjunto de procedimientos) que se pueda usar para enviar instrucciones LMD y LDD a la base de datos y recuperar los resultados.
- Extendiendo la sintaxis del lenguaje anfitrión para que incorpore las llamadas LMD dentro del programa del lenguaje anfitrión. Generalmente, un carácter especial precede a las llamadas LMD y un preprocesador, denominado precompilador LMD, convierte las instrucciones LMD en llamadas normales a procedimientos en el lenguaje anfitrión.

## 1.6. Diseño de bases de datos

### 1.6.1. Proceso de diseño
1. La fase inicial del diseño de las bases de datos, por tanto, consiste en caracterizar completamente los requisitos de datos de los hipotéticos usuarios de la base de datos. **El resultado de esta fase es la especificación de los requisitos de los usuarios.**
2. El diseñador escoge un modelo de datos y, mediante la aplicación de los conceptos del modelo de datos elegido, traduce esos requisitos en un esquema conceptual de la base de datos. El esquema desarrollado en esta fase de **diseño conceptual** ofrece una visión general detallada de la empresa. En este punto, la atención se centra en describir los datos y sus relaciones, más que en especificar los detalles del almacenamiento físico. Un esquema conceptual completamente desarrollado también indica los **requisitos funcionales de la empresa**. (los usuarios describen el tipo de operaciones o transacciones que se llevarán a cabo con los datos).
3. **Fase de diseño lógico**: el diseñador relaciona el esquema conceptual de alto nivel con el modelo de implementación de datos del sistema de bases de datos que se va a usar.
4.  El diseñador usa el esquema de bases de datos específico para el sistema resultante en la **fase de diseño físico**, en la que se especifican las características físicas de la base de datos. Entre esas características están la forma de organización de los archivos y las estructuras de almacenamiento interno.

### 1.6.2. Diseño de la base de datos para una universidad
La especificación de requisitos inicial puede basarse en un conjunto de entrevistas con los usuarios de la base de datos y el propio análisis del diseñador sobre la organización. La descripción que se obtiene de esta fase de diseño sirve como punto inicial para la especificación de la estructura conceptual de la base de datos.
### 1.6.3. El modelo entidad-relación
Se basa en un conjunto de objetos básicos, denominados *entidades*, y las *relaciones* entre esos objetos. 

Las entidades se describen en las bases de datos mediante un conjunto de **atributos** (los atributos *ID*, *nombre* y *sueldo* pueden describir una entidad *profesor*).

Una **relación** es una asociación entre varias entidades (la relación *miembro* asocia un profesor con su departamento).

El conjunto de todas las entidades del mismo tipo y el conjunto de todas las relaciones del mismo tipo se denominan, respectivamente, conjunto de entidades y conjunto de relaciones.

La estructura lógica general de la base de datos se puede expresar gráficamente mediante un diagrama entidad-relación (E-R). Una de las formas más populares de dibujar este tipo de diagramas es utilizar el **lenguaje de modelado unificado** (UML: unified modeling language).
- Las entidades se representan mediante un rectángulo con el nombre de la entidad en la cabecera y la lista de atributos debajo. 
- Las relaciones se representan mediante un rombo que conecta un par de entidades. El nombre de la relación se pone dentro del rombo.
![](img/Pasted%20image%2020250226135236.png)

### 1.6.4. Normalización
La normalización es un método de diseño de bases de datos. El objetivo es generar un conjunto de esquemas de relaciones que permita almacenar información sin redundancias innecesarias, pero que también permita recuperar la información con facilidad.

El enfoque es diseñar esquemas que se hallen en la *forma normal* adecuada. Para determinar si un esquema de relación se halla en una de las formas normales deseadas, hace falta información adicional sobre la empresa real que se está modelando con la base de datos. El enfoque más frecuente es usar **dependencias funcionales**.

- Partida de un esquema de la Base de datos 
- Verificar si cumple condiciones de formas normales 
- Plantear esquemas alternativo

## 1.7. Almacenamiento de datos y consultas
Los sistemas de bases de datos están divididos en módulos que tratan con cada una de las responsabilidades del sistema general.
Los componentes funcionales de los sistemas de Bases de Datos pueden dividirse en:
- Gestor de almacenamiento: 
	- Las BD necesitan una gran cantidad de espacio de almacenamiento. 
	- Objetivo: minimizar la necesidad de intercambio de datos entre los discos y la memoria principal 
- Procesador de consultas: 
	- Facilita el acceso a los datos 
	- Objetivo: Ofrecer buen rendimiento sin necesidad de conocer detalles del diseño físico.
### 1.7.1. Gestor de almacenamiento
El gestor de almacenamiento es un módulo de programa que proporciona la interfaz entre:
- Los datos de bajo nivel en la base de datos 
- Los programas de aplicación y consultas emitidas al sistema
El gestor de almacenamiento traduce las diferentes instrucciones LMD a comandos de bajo nivel del sistema de archivos.
El gestor de almacenamiento es responsable de las siguientes tareas: 
- La interacción con el gestor de ficheros del Sistema Operativo 
- El almacenamiento, recuperación y actualización eficiente de los datos

Entre los componentes del gestor de almacenamiento se encuentran:
- **Gestor de autorizaciones e integridad**: comprueba que se satisfagan las restricciones de integridad y la autorización de los usuarios para tener acceso a los datos. 
- **Gestor de transacciones**: garantiza que la base de datos quede en un estado consistente (correcto) a pesar de los fallos del sistema, y que la ejecución concurrente de transacciones transcurra sin conflictos. 
- **Gestor de archivos**: gestiona la asignación de espacio de almacenamiento de disco y las estructuras de datos usadas para representar la información almacenada en el disco. 
- **Gestor de la memoria intermedia**: es responsable de traer los datos desde el disco de almacenamiento a la memoria principal, así como de decidir los datos a guardar en la memoria caché.
El gestor de almacenamiento implementa varias estructuras de datos como parte de la implementación física del sistema:
- **Archivos de datos**: almacenan la base de datos en sí misma. 
- **Diccionario de datos**: almacena metadatos acerca de la estructura de la base de datos; en particular, su esquema. 
- **Índices**: pueden proporcionar un acceso rápido a los elementos de datos.
### 1.7.2. El procesador de consultas
Entre los componentes del procesador de consultas se encuentran: 
- **Intérprete del LDD**: interpreta las instrucciones del LDD y registra las definiciones en el diccionario de datos. 
- **Compilador del LMD**: traduce las instrucciones del LMD en un lenguaje de consultas a un plan de evaluación que consiste en instrucciones de bajo nivel que entienda el motor de evaluación de consultas. Las consultas se suelen poder traducir en varios planes de ejecución alternativos, todos los cuales proporcionan el mismo resultado. El compilador del LMD también realiza una **optimización de consultas**, es decir, elige el plan de evaluación de menor coste de entre todas las opciones posibles. 
- **Motor de evaluación de consultas**: ejecuta las instrucciones de bajo nivel generadas por el compilador del LMD.
## 1.8. Gestión de transacciones
**Una transacción es una colección de operaciones que se llevan a cabo como una única función lógica en una aplicación de base de datos.**
A menudo, varias operaciones sobre la base de datos forman una única unidad lógica de trabajo lo que implica requisitos como: 
- **Atomicidad**: la transacción se hace completa o no se hace 
- **Consistencia**: después transacción los datos deben ser consistentes 
- **Durabilidad**: Los nuevos datos deben persistir a pesar de fallo en el sistema
El Gestor de transacciones de un sistema de BD consta de: 
- **Gestor de control de concurrencia**: Controlar la interacción entre las transacciones concurrentes para garantizar la consistencia de la base de datos. 
- **Gestor de recuperación de fallos**: Detectar los fallos del sistema y restaurar la base de datos al estado que tenía antes de que ocurriera el fallo.

## 1.9. Arquitectura de las bases de datos
La arquitectura de los sistemas de bases de datos se ve muy influida por el sistema informático subyacente, sobre el que se ejecuta el sistema de bases de datos.
Los sistemas de bases de datos pueden estar: 
- Centralizados 
- Tipo cliente-servidor: una máquina servidor ejecuta el trabajo en nombre de multitud de máquinas clientes) 
- Aprovechar las arquitecturas de computadoras paralelas 
- Distribuidas: se extienden por varias máquinas geográficamente separadas. En una arquitectura de dos capas.
Clasificación por número de capas: 
- Dos capas: La aplicación se divide en un componente que reside en la máquina cliente, que invoca la funcionalidad del sistema de bases de datos en la máquina servidora mediante instrucciones del lenguaje de consultas
![](img/Pasted%20image%2020250226142835.png)
- Tres capas:
	La máquina cliente actúa simplemente como una parte visible al usuario y no alberga llamadas directas a la base de datos.
	El extremo cliente se comunica con un servidor de aplicaciones, generalmente mediante una interfaz de formularios 
	El servidor de aplicaciones, a su vez, se comunica con el sistema de bases de datos para tener acceso a los datos 
	Las aplicaciones de tres capas resultan más adecuadas para aplicaciones de gran tamaño y para las aplicaciones que se ejecutan en la World Wide Web.
![](img/Pasted%20image%2020250226142904.png)

## 1.10. Minería y análisis de datos
**Proceso de análisis semiautomático de grandes bases de datos para descubrir patrones útiles.** Al igual que el descubrimiento de conocimientos en la inteligencia artificial (también denominado aprendizaje de la máquina) o el análisis estadístico, la minería de datos intenta descubrir reglas y patrones en los datos. Sin embargo, la minería de datos se diferencia del aprendizaje de la máquina y de la estadística en que maneja grandes volúmenes de datos, almacenados principalmente en disco.
Algunos tipos de conocimientos descubiertos en las bases de datos pueden representarse:
- Conjunto de reglas:  No son universalmente ciertas, sino que tienen grados de «apoyo» y de «confianza»
- Ecuaciones que relacionan diferentes variables 
- Mecanismos para la predicción de los resultados cuando se conocen los valores de algunas variables
Las grandes compañías disponen de distintas fuentes de datos que necesitan utilizar para tomar decisiones empresariales. Si desean ejecutar consultas eficientes sobre datos tan diversos, las compañías han de construir **almacenes de datos**. Los almacenes de datos recogen datos de distintas fuentes bajo un esquema unificado, en un único punto. Por tanto, proporcionan al usuario una interfaz única y uniforme con los datos.
Los datos textuales también han crecido de manera explosiva. Estos datos carecen de estructura, a diferencia de los datos rígidamente estructurados de las bases de datos relacionales. **La consulta de datos textuales no estructurados se denomina *recuperación de la información***.

## 1.11. Bases de datos específicas
Varias áreas de aplicaciones de los sistemas de bases de datos están limitadas por las restricciones del modelo de datos relacional.

### 1.11.1. Modelos de datos basados en objetos
El modelo de datos orientado a objetos se ha convertido en la metodología dominante de desarrollo de software. Ello ha llevado al desarrollo del **modelo de datos orientado a objetos**, que se puede ver como una ampliación del modelo E-R con las nociones de encapsulación, métodos (funciones) e identidad de objetos.
Los principales proveedores de bases de datos apoyan actualmente el **modelo de datos relacional orientado a objetos** que combina las características del modelo de datos orientado a objetos con el modelo de datos relacional.

### 1.11.2. Modelos de datos semiestructurados
**Permiten la especificación de los datos, de modo que cada elemento de datos del mismo tipo puede tener conjuntos de atributos diferentes.** Esto los diferencia de los modelos de datos mencionados anteriormente, en los que todos los elementos de datos de un tipo dado deben tener el mismo conjunto de atributos.
XML ofrece un modo de representar los datos que tienen una estructura anidada y, además, permite una gran flexibilidad en la estructuración de los datos.

## 1.12. Usuarios y administradores de bases de datos
Uno de los objetivos principales de los sistemas de bases de datos es recuperar información de la base de datos y almacenar en ella información nueva. Las personas que trabajan con una base de datos se pueden clasificar como usuarios o administradores de bases de datos.

### 1.12.1. Usuarios de bases de datos e interfaces de usuario
Hay cuatro tipos diferentes de usuarios de los sistemas de bases de datos, diferenciados por la forma en que esperan interactuar con el sistema. Se han diseñado diversos tipos de interfaces de usuario para los diferentes tipos de usuarios.
#### USUARIOS NORMALES 
Son usuarios no sofisticados que interactúan con el sistema invocando alguno de los programas de aplicación que se han escrito previamente.
La interfaz de usuario habitual para los usuarios normales es una interfaz de formularios, en la que el usuario puede rellenar los campos correspondientes del formulario.
Los usuarios normales también pueden limitarse a leer informes generados por la base de datos.
Ej: Un alumno rellenando un formulario de matrícula
#### PROGRAMADORES DE APLICACIONES
Son profesionales informáticos que escriben programas de aplicación. Los programadores de aplicaciones pueden elegir entre muchas herramientas para desarrollar las interfaces de usuario. Las **herramientas de desarrollo rápido de aplicaciones (DRA)** son herramientas que permiten al programador de aplicaciones crear formularios e informes con un mínimo esfuerzo de programación
#### USUARIOS SOFISTICADOS
Interactúan con el sistema sin escribir programas. En su lugar, formulan sus consultas en un lenguaje de consultas de bases de datos o con herramientas como el software de análisis de datos. Los analistas que remiten las consultas para explorar los datos de la base de datos entran en esta categoría.
#### USUARIOS ESPECIALIZADOS
Son usuarios sofisticados que escriben aplicaciones de bases de datos especializadas que no encajan en el marco tradicional del procesamiento de datos. Entre estas aplicaciones están los sistemas de diseño asistido por computadora, los sistemas de bases de conocimientos y los sistemas expertos, los sistemas que almacenan datos con tipos de datos complejos (por ejemplo, los datos gráficos y los datos de sonido) y los sistemas de modelado del entorno.

### 1.12.2. Administrador de bases de datos
Una de las principales razones de usar un SGBD es tener un control centralizado tanto de los datos como de los programas que tienen acceso a esos datos. La persona que tiene ese control central sobre el sistema se denomina **administrador de bases de datos (ABD)**.
Funciones:
- **Definición del esquema.** El ABD crea el esquema original de la base de datos mediante la ejecución de un conjunto de instrucciones de definición de datos en el LDD.
- **Definición de la estructura y del método de acceso.**
- **Modificación del esquema y de la organización física.** Reflejar las necesidades cambiantes de la organización, o para alterar la organización física a fin de mejorar el rendimiento.
- **Concesión de autorización para el acceso a los datos.** Regular las partes de la base de datos a las que puede tener acceso cada usuario. La información de autorización se guarda en una estructura especial del sistema que el SGBD consulta siempre que alguien intenta tener acceso a los datos del sistema.
- **Mantenimiento rutinario.**
	- Copia de seguridad periódica de la base de datos.
	- Asegurarse de que se dispone de suficiente espacio libre en disco para las operaciones normales y aumentar el espacio en el disco según sea necesario.
	- Supervisar los trabajos que se ejecuten en la base de datos y asegurarse de que el rendimiento no se degrade debido a que algún usuario haya remitido tareas muy costosas

# TEMA 2 Introducción al modelo relacional

## 2.1. La estructura de las bases de datos relacionales
**Una base de datos relacional consiste en un conjunto de tablas, a cada una de las cuales se le asigna un nombre único.**
En terminología matemática, una tupla es sencillamente una secuencia (o lista) de valores. Una relación entre n valores se representa matemáticamente como una **n-tupla** de valores, es decir, como una tupla con n valores, que se corresponde con una fila de una tabla. En el modelo relacional, el término **relación** se utiliza para referirse a una tabla, mientras el término *tupla* se utiliza para referirse a una fila. De forma similar, el término **atributo** se refiere a una columna de una tabla.
En el modelo relacional: 
- Relación → Tabla (tiene un nombre) 
- Tupla → Fila
- Atributo → Columna (tiene un nombre)
![](img/Pasted%20image%2020250226212957.png)
Se utiliza el término **ejemplar de relación** para referirse a una instancia específica de una relación, es decir, qué contiene un determinado conjunto de filas. 
El orden en que las tuplas aparecen en una relación es irrelevante, ya que la relación es un conjunto de tuplas.
Para cada atributo de una relación existe un conjunto de valores permitidos, llamado **dominio** del atributo.
Por tanto, el dominio del atributo sueldo de la relación profesor es el conjunto de todos los posibles valores de sueldo, mientras que el dominio del atributo nombre es el conjunto de todos los posibles nombres de profesor.
Es necesario que, para toda relación r, los dominios de todos los atributos de r sean atómicos. Un dominio es **atómico** si los elementos del dominio se consideran unidades indivisibles.
Por ejemplo, suponga que la tabla profesor tiene un atributo *número_teléfono*, que puede almacenar un conjunto de números de teléfono correspondientes al profesor. Entonces, el dominio de *número_teléfono* no sería atómico, ya que un elemento del dominio es un conjunto de números de teléfono, y tiene subpartes, que son cada uno de los números de teléfono individuales del conjunto.
El valor **null (nulo)** es un valor especial que significa que el valor es desconocido o no existe.

## 2.2. Esquema de la base de datos
- Esquema de una BD: 
	- Diseño lógico de la BD 
	- Esquema de una relación consiste en un lista de los atributos y de sus dominios correspondientes
	- Normalmente no cambia
- Ejemplar o instancia de una BD:
	- Instantánea de los datos almacenados en la BD en un momento dato
**El concepto de *relación* se corresponde con el concepto de variable de los lenguajes de programación.**
**El concepto *esquema de la relación* se corresponde con el concepto de definición de tipos de los lenguajes de programación.**
**El concepto de *ejemplar de la relación* se corresponde con el concepto de valor de una variable en los lenguajes de programación.** El valor de una variable dada puede cambiar con el tiempo; de manera parecida, el contenido del ejemplar de una relación puede cambiar con el tiempo cuando la relación se actualiza. Sin embargo, el esquema de una relación normalmente no cambia.
Utilizar atributos comunes en esquemas de relación es una forma de relacionar tuplas de relaciones diferentes. (Aunque es importante conocer la diferencia entre un esquema de relación y un ejemplar de relación, normalmente se utiliza el mismo nombre).

Notación empleada:
$r (A1, A2, …, An )$ es un esquema de una relación o tabla de nombre r 
-  $r$ es el **nombre** de la relación o tabla 
- $A1, A2, …, An$ son los nombres de los **atributos** 
- $D1, D2, …. Dn$ Son los **dominios de los atributos**. $Ai ⊆ Di$ 
- $t$ de $r$ es una **tupla**, representada por una fila en una relación o tabla 
	- Una relación o tabla es un conjunto de tuplas $t (a1, a2, …, an)$ donde cada $ai ∈ Di$ 
	- Formalmente, dados los conjuntos de dominios $D1, D2, …. Dn$ una **relación** $r$ es un subconjunto de $D1 x D2 x … x Dn$ 
	- Los valores actuales (**ejemplar**) de una relación, están especificados mediante una tabla
-  Una base de datos relacional consiste en múltiples relaciones o tablas 
- La información es organizada en tablas o relaciones: profesor, estudiante, tutor 
- No existe una forma única de organizar la información en tablas o relaciónes 
	- Ejemplo de mal diseño Tutores (profesor_id, nombre_Prof, nombre_dept, salario, estudiante_id, …) 
		- Repetición de información: si dos estudiantes tienen el mismo profesor, aparecen dos tuplas en la relación con la misma información del profesor  
		- Necesidad de valores nulos (un estudiante sin tutor)
- La teoría de normalización trata el problema del cómo proponer “buenos” esquemas para una base de datos relacional
## 2.3. Claves
Las relaciones o tablas y los atributos (columnas) tienen nombre, las tuplas (filas) no 
Las tuplas de una relación tienes que ser distinguibles. Dos tuplas de una relación no pueden tener los mismos valores en todos sus atributos.
**Superclave**: Conjunto de uno o varios atributos que, considerados conjuntamente, permiten identificar de manera unívoca una tupla de la relación.
Ejemplo superclaves:  
- *ID *
- *ID* y *nombre* 
**Si K es superclave también lo es Cualquier superconjunto de K**

**Clave candidata:** Superclave para la que no hay subconjunto de atributos que también sea superclave. No es única, es posible que varios conjuntos de atributos puedan ser claves candidatas.
**Clave primaria:** De entre todas las claves candidata, es la clave candidata elegida por el diseñador de la base de datos como medio principal para la identificación de las tuplas de una relación La clave primaria debe escogerse de manera que los valores de sus atributos no se modifiquen nunca, o muy rara vez.
Los atributos de clave primaria de un esquema de relación se indican antes que el resto de los atributos y subrayados.
![](img/Pasted%20image%2020250227164945.png)

**Clave externa**: El esquema de una relación puede incluir entre sus atributos la clave primaria de otra relación
![](img/Pasted%20image%2020250227165259.png)
![](img/Pasted%20image%2020250227165327.png)
**Restricción de integridad referencial:** Requiere que los valores que aparecen en determinados atributos de una tupla en la relación referenciante también aparezcan en otros atributos de al menos una tupla de la relación referenciada.
	Si en una tupla de profesor se menciona un *nombre_dept*, se requiere que exista una tupla en departamento con ese *nombre_dept*

## 2.4. Diagramas de esquema
El esquema de la base de datos, junto con las dependencias de claves primaria y externa, se puede mostrar gráficamente mediante diagramas de esquema. 
- Cada relación aparece como un cuadro con el nombre de la relación en la parte superior y los atributos en el interior 
- Los atributos que son clave primaria se muestran subrayados. 
- Las dependencias de clave externa aparecen como flechas desde los atributos de clave externa de la relación referenciante a la clave primaria de la relación referenciada 
- Las restricciones distintas de las restricciones de clave externa, no se muestran explícitamente en los diagramas de esquema. 
- Otros diagramas como el de entidad- relación permiten representar distintos tipos de restricciones ![](img/Pasted%20image%2020250227165840.png)

## 2.5. Lenguajes de consulta relacional
**Lenguaje en el que los usuarios solicitan información de la base de datos.** Estos lenguajes suelen ser de un nivel superior al de los lenguajes de programación habituales.
### LENGUAJES PROCEDIMENTALES
El usuario indica al sistema que lleve a cabo una serie de operaciones en la base de datos para calcular el resultado deseado.
	Ej: Algebra relacional: consta de un conjunto de operaciones que toma una o dos relaciones como entrada y genera una nueva relación como resultado.
### LENGUAJES NO PROCEDIMENTALES
El usuario describe la información deseada sin establecer un procedimiento concreto para obtener esa información.
	Ej: Cálculo relacional de tuplas y Cálculo relacional de dominios. El cálculo relacional usa la lógica de predicados para definir el resultado deseado sin proporcionar ningún procedimiento concreto para obtener dicho resultado.
## 2.6. Operaciones relacionales
Todos los lenguajes procedimentales de consulta relacional proporcionan un conjunto de operaciones:
	Se aplican a una única relación o a un par de relaciones 
	El resultado es una única relación 
Permite combinar varias operaciones de forma modular

### Operación selección de tuplas
El resultado es una relación con las tuplas que satisfacen algún criterio en alguno de sus atributos 
	Ej: tuplas de relación profesor con atributo sueldo>85.000€ 
### Operación proyección 
Consiste en seleccionar ciertos atributos de una relación, dando como resultado una nueva relación que solo contiene los atributos seleccionados 
	Ej: lista de ID de la relación profesor
### Operación join (reunión) 
Permite combinar dos relaciones mezclando pares de tuplas, una de cada relación, en una única tupla 
- **Reunión natural:** hace casar las tuplas cuyos valores coinciden para los atributos que son comunes a ambas relaciones 
- **Producto cartesiano:** combina todos los pares de tuplas de las dos relaciones.
![](img/Pasted%20image%2020250227170803.png)

Como las relaciones son conjuntos también se usan las aperaciones:
![](img/Pasted%20image%2020250227170904.png)
Tuplas duplicadas: El resultado de una consulta puede contener tuplas duplicadas (desde el punto de vista matemático deberían eliminarse). Existen lenguajes que las eliminan y otros que no (para no sobrecargar el procesamiento con la eliminación).

### ALGEBRA RELACIONAL
Define un conjunto de operaciones sobre relaciones, de manera similar a las operaciones algebraicas habituales como la suma, la resta o la multiplicación que operan sobre números. El álgebra relacional normalmente opera con una o dos relaciones como entrada y devuelve una relación como salida.

| Símbolo (Nombre)                                         | Ejemplo de uso                                                                                                                                                                                                                                                                                                       |
| -------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| σ (Selección)                                            | $$σ_{sueldo>=85000}(profesor)$$ <br>Devuelve las filas de la relación de entrada que satisfacen el predicado.                                                                                                                                                                                                        |
| Π (Proyección)                                           | $$Π_{ID,sueldo}(profesor)$$<br>Genera los atributos indicados de las filas de la relación de entrada. Elimina de la salida las tuplas duplicadas.                                                                                                                                                                    |
| ⋈ (Reunión natural)                                      | $$profesor ⋈ departamento$$ <br>Genera pares de filas de las dos relaciones de entrada que tienen los mismos valores en todos los atributos con el mismo nombre.                                                                                                                                                     |
| × (Producto cartesiano)<br><br><br><br><br><br>∪ (Unión) | $$profesor × departamento $$<br>Genera todos los pares de filas de las dos relaciones de entrada (independientemente de que tengan o no los mismos valores en el o los atributos comunes). <br>$$Π_{nombre}(profesor) ∪ Π_{nombre}(estudiante)$$ <br>Genera la unión de las tuplas de las dos relaciones de entrada. |
# TEMA 3 Introducción a SQL
Aunque nos referimos al lenguaje SQL como un «lenguaje de consulta», puede hacer mucho más que realizar consultas a la base de datos. Puede definir estructuras, modificar los datos y especificar restricciones de seguridad.

## 3.1. Introducción al lenguaje de consultas SQL
El lenguaje SQL tiene varios componentes: 
- **Lenguaje de definición de datos (LDD).** El LDD de SQL proporciona comandos para la definición de esquemas de relación, borrado de relaciones y modificación de los esquemas de relación. 
- **Lenguaje interactivo de manipulación de datos (LMD).** El LMD de SQL incluye un lenguaje de consultas como comandos para insertar, borrar y modificar tuplas en la base de datos. 
- **Integridad.** El LDD de SQL incluye comandos para especificar las restricciones de integridad que deben cumplir los datos almacenados en la base de datos. Las actualizaciones que violan las restricciones de integridad se rechazan. 
- **Definición de vistas.** El LDD de SQL incluye comandos para la definición de vistas. 
- **Control de transacciones.** SQL incluye comandos para especificar el comienzo y el final de las transacciones.
- **SQL incorporado y SQL dinámico.** SQL incorporado y SQL dinámico definen cómo se pueden incorporar instrucciones de SQL en lenguajes de programación de propósito general como C, C++ y Java. 
- **Autorización.** El LDD de SQL incluye comandos para especificar los derechos de acceso a las relaciones y a las vistas.

## 3.2. Definición de datos de SQL
El conjunto de relaciones de cada base de datos debe especificarse en el sistema en términos de un lenguaje de definición de datos (LDD). El LDD de SQL no solo permite la especificación de un conjunto de relaciones, sino también de la información relativa a esas relaciones, incluyendo: 
- El esquema de cada relación. 
- El dominio de valores asociado a cada atributo. 
- Las restricciones de integridad. 
- El conjunto de índices que se deben mantener para cada relación. 
- La información de seguridad y de autorización de cada relación. 
- La estructura de almacenamiento físico de cada relación en el disco.
### 3.2.1. Tipos básicos
- **char**(*n*). Una cadena de caracteres de longitud fija, con una longitud n especificada por el usuario. También se puede utilizar la palabra completa **character**. 
- **varchar**(*n*). Una cadena de caracteres de longitud variable con una longitud máxima n especificada por el usuario. La forma completa, **character varying**, es equivalente. 
- int. Un entero (un subconjunto finito de los enteros dependiente de la máquina). La palabra completa, **integer**, es equivalente. 
- **smallint**. Un entero pequeño (un subconjunto dependiente de la máquina del tipo de dominio entero).
- **numeric**(*p, d*). Un número de coma fija, cuya precisión la especifica el usuario. El número está formado por p dígitos (más el signo), y de esos p dígitos, d pertenecen a la parte decimal. Así, **numeric**(3,1) permite que el número 44.5 se almacene exactamente, pero ni 444.5 ni 0.32 se pueden almacenar exactamente en un campo de este tipo. 
- **real, double precision**. Números de coma flotante y números de coma flotante de doble precisión, con precisión dependiente de la máquina. 
- **float**(*n*). Un número de coma flotante cuya precisión es, al menos, de n dígitos.
Todos los tipos incluyen un valor especial llamado valor ***null*** **(nulo)**. Un valor nulo indica una ausencia de valor que puede existir o no pero que puede no ser conocido.

El tipo de dato **char** almacena una cadena de caracteres de tamaño fijo. Suponga, por ejemplo, un atributo A del tipo **char**(10). Si guardamos la cadena «Avi» en este atributo, se añaden 7 espacios para que tenga un total de 10 caracteres de tamaño. Por otro lado, suponga un atributo B del tipo **varchar**(10), donde guardamos «Avi»; en este atributo no se añaden espacios extra. ==Cuando se comparan dos valores de tipo **char**, si tienen distinto tamaño se añaden automáticamente espacios extra al más pequeño para que tengan el mismo tamaño antes de realizar la comparación.==

Cuando se compara un tipo **char** con un tipo **varchar**, uno esperaría que se añadiesen espacios extra al tipo **varchar** para que tengan el mismo tamaño antes de la comparación; sin embargo, puede que se haga o no, dependiendo del sistema de bases de datos. El resultado final es que aunque se guarde el mismo valor «Avi», en los atributos A y B como se ha indicado, la comparación A=B puede devolver falso. ==Se recomienda que siempre se utilice el tipo **varchar** en lugar del tipo **char** para evitar estos problemas. ==
SQL también proporciona el tipo **nvarchar** para guardar datos en varios idiomas utilizando la representación Unicode. Sin embargo, muchas bases de datos permiten guardar Unicode incluso en tipos **varchar** (en la representación UTF-8).

### 3.2.2. Definición básica de esquemas
Las relaciones se definen mediante el comando create table. 
**create table** *r* ($A_1 \ D_1, \ A_2 \ D_2, \ ..., \ A_n \ D_n,$
			 $(restricción \_integridad_1)$
			 ...,
			 $(restricción\_integridad_k))$

- r es el nombre de la relación 
- $A_i$ nombre de atributo en el esquema de la relación r 
- $D_i$ es el dominio del atributo $A_i$
Ej:
**create table** *departamento* 
	(*nombre_dept*     **varchar** (20),
	*edificio*                **varchar** (15), 
	*presupuesto*        **numeric** (12,2), 
	**primary key** *(nombre_dept)*);
La relación tiene tres atributos *nombre_ dept*, que es una cadena de caracteres de un tamaño máximo de 20; *edificio*, que es una cadena de caracteres de un tamaño máximo de 15 y *presupuesto*, que es un número con un total de 12 dígitos, de los cuales 2 están tras el punto decimal. El comando **create table** también indica que el atributo *nombre_dept* es la clave primaria de la relación *departamento*.

El punto y coma que se muestra al final de las sentencias create table, así como al final de otras sentencias de SQL que se verán más adelante en este capítulo, en la mayoría de las implementaciones de SQL son opcionales.

SQL admite un número variable de restricciones de integridad. En esta sección solo se tratarán algunas de ellas:
- **primary key** $(A_{j1} , A_{j2} , …, A_{jm})$: la especificación de **clave primaria** determina que los atributos $A_{j1} , A_{j2} , …, A_{jm}$ forman la clave primaria de la relación. Los atributos de la clave primaria tienen que ser *no nulos* y *únicos*.
- **foreign key** $(A_{k1} , A_{k2} , …, A_{kn})$ **references** *s*: la **clave externa** indica que los valores de los atributos $(A_{k1} , A_{k2} , …, A_{kn})$ de cualquier tupla en la relación se deben corresponder con los valores de los atributos de la clave primaria de otras tuplas de la relación *s*.
- **not null**: la restricción not null en un atributo indica que no se permite el valor nulo para ese atributo.
Ej:
**create table** *profesor*( 
	*ID*                      **char**(5), 
	*nombre*             **varchar**(20) **not null**, 
	*nombre_dept*    **varchar**(20), 
	*sueldo*               **numeric**(8,2), 
	**primary key** (*ID*), 
	**foreign key** (*nombre_dept*) **references** *departmento*)
En SQL se evita que cualquier actualización de la base de datos viole las restricciones de integridad de los atributos de clave primaria o, si la tupla tiene los mismos valores en la clave primaria que otra de la tuplas, SQL indica un error y evita dicha actualización.
De forma similar, durante una inserción de una tupla *asignatura* con un valor de *nombre_dept* que no exista en la relación departamento, que generaría una violación de la restricción de clave externa de *asignatura*, SQL impediría realizar tal inserción.

Todas las relaciones recién creadas están inicialmente vacías. Se utiliza el comando insert para introducir datos en la relación. Por ejemplo, si se desea introducir el hecho de que existe un profesor de nombre Smith en el departamento de Biología con un *profesor_id* 10211 y un sueldo de 66.000 €, se escribirá:

**insert into** *profesor*
	**values** (10211, ´Smith´, ´Biología´, 66000);
Los valores se indican en el orden en que se encuentran los atributos en el esquema de relación.

Se puede utilizar el comando **delete** para eliminar tuplas de una relación. 
	**delete from** *estudiante*; 
elimina todas las tuplas de la relación *estudiante*. Otras formas del comando delete (borrar) permiten indicar tuplas concretas para eliminarlas.

Para eliminar una relación de una base de datos SQL se utiliza el comando **drop table**. Este comando elimina toda la información de la relación indicada de la base de datos.
	**drop table** *r*; 
es una acción mucho más drástica que: 
	**delete from** *r*; 
Esta última mantiene la relación r, solo elimina las tuplas de r. La primera elimina no solo las tuplas de r, sino también el esquema de r.

Se utiliza el comando **alter table** para añadir atributos a una relación ya existente. Todas las tuplas de la relación tendrán el valor null en los nuevos atributos añadidos.
	**alter table** *r* **add** *A D*;
- r es el nombre de la relación existente
- A es el nombre del atributo a añadir 
- D es el tipo del atributo añadido.
Se pueden eliminar atributos de una relación utilizando el comando:
	**alter table** *r* **drop** *A*;
- r es el nombre de la relación existente
- A es el nombre del atributo a eliminar 
## 3.3. Estructura básica de las consultas SQL
La estructura básica de una consulta SQL consta de tres cláusulas: **select**, **from** y **where**. Las consultas tienen como entrada las relaciones indicadas en la cláusula **from**, operan con ellas como se indica en las cláusulas **where** y **select** y generan como resultado una **relación**.
### 3.3.1. Consultas sobre una relación única
Supongamos la consulta, a «encontrar los nombres de departamento de todos los profesores»
	**select** *nombre_dept* 
	**from** *profesor*;
El resultado es una relación que consta de un único atributo con el encabezado *nombre*.

| nombre_dept |     |
| ----------- | --- |
| Informática |     |
| Finanzas    |     |
| Música      |     |
| Finanzas    |     |
Según la definición matemática, formal, del modelo de relación, una relación es un conjunto. Por tanto, nunca deberían aparecer tuplas repetidas en una relación. En la práctica, la eliminación de duplicados es muy costosa. Por tanto, en SQL se permiten duplicados en las relaciones, así como en los resultados de expresiones SQL.
En aquellos casos en los que se desee forzar a que no existan duplicados, se añade la palabra clave **distinct** tras **select**. Se puede escribir la consulta anterior como:
	**select distinct** *nombre_dept*
	**from** *profesor*;
si deseamos eliminar los duplicados.

SQL nos permite utilizar la palabra clave **all** para indicar explícitamente que los duplicados no se eliminen: 
	**select all** *nombre_dept* 
	**from** *profesor*

La cláusula **select** también puede contener expresiones aritméticas que incluyan los operadores **+, −, ∗** y **/** con constantes o atributos de las tuplas. Por ejemplo, la consulta:
	**select** *ID, nombre, nombre_dept, sueldo ∗ 1.1* 
	**from** *profesor*; 
devuelve una relación que es la misma que la relación profesor excepto que el atributo sueldo se multiplica por 1.1.

La cláusula **where** permite seleccionar solamente aquellas filas de la relación resultado de la cláusula **from** que satisfagan determinado predicado. Suponga la consulta «encontrar los nombres de todos los profesores del departamento de Informática cuyo sueldo sea superior a 70.000 €»
	**select** *nombre*
	**from** *profesor*
	**where** *nombre_dept* = ´Informática´ **and** *sueldo* > 70000;
SQL permite el uso de operadores lógicos **and**, **or** y **not** en la cláusula where.
### 3.3.2. Consultas sobre varias relaciones
Suponga que se desea responder a la siguiente consulta: «obtener los nombres de todos los profesores, junto con los nombres de sus departamentos y el nombre del edificio donde se encuentra el departamento».
En SQL, para responder a la consulta anterior se indican las relaciones a las que se necesita acceder en la cláusula **from** y se especifica la condición de coincidencia en la cláusula **where**.
**select** *nombre, profesor.nombre_dept, edificio*
**from** *profesor, departamento*
**where** *profesor.nombre_dept = departamento.nombre_dept;*

| nombre     | nombre_dept | edificio |
| ---------- | ----------- | -------- |
| Srinivasan | Informática | Taylor   |
| Wu         | Finanzas    | Painter  |
| Mozart     | Música      | Packard  |
| Einstein   | Historia    | Watson   |
| El Said    | Física      | Taylor   |
| Gold       | Informática | Painter  |
Fíjese que el atributo *nombre_dept* existe tanto en la relación *profesor* como en *departamento*, y el nombre de la relación se usa como un prefijo (en *profesor.nombre_dept*, y en *departamento. nombre_dept*) para indicar claramente a qué atributo se refiere. Al contrario, los atributos *nombre* y *edificio* aparecen solo en una de las relaciones y, por tanto, no hay que indicar como prefijo el nombre de la relación.

#### RESUMEN

- La cláusula **select** se utiliza para indicar los atributos deseados en el resultado de una consulta. 
- La cláusula **from** indica la lista de relaciones a las que hay que acceder para evaluar la consulta. 
- La cláusula **where** es un predicado que incluye atributos de la relación de la cláusula from. 
Una consulta típica de SQL tiene la forma: 
**select** $A_1 , A_2 , …, A_n$ 
**from** $r_1 , r_2 …, r_m$ 
**where** $P$;

Donde Ai representa un atributo, los ri una relación y P es un predicado. Si se omite la cláusula where, el predicado P es true.

En general, el significado de una consulta en SQL se puede entender de la siguiente forma: 
1. Genere un producto cartesiano de las relaciones de la cláusula from 
2. Aplique los predicados indicados en la cláusula where al resultado del paso 1 
3. Para cada tupla del paso 2, extraiga los atributos (o resultado de las expresiones) indicados en la cláusula select
### 3.3.3. La unión natural
Es un caso habitual que la condición de coincidencia de la cláusula from suele requerir que todos los atributos con los mismos nombres tengan el mismo valor.
Ya se ha visto cómo el producto cartesiano junto con el predicado de la cláusula where se pueden utilizar para reunir la información de varias relaciones.
==La operación unión natural opera con dos relaciones y genera como resultado una relación. Al contrario que el producto cartesiano de dos relaciones, que concatena todas las tuplas de la primera relación con cada una de las tuplas de la segunda, la unión natural solo considera aquellos pares de tuplas con los mismos valores en los atributos que aparecen en los esquemas de ambas relaciones.==

Supóngase la consulta «Para todos los profesores de la universidad que hayan enseñado alguna asignatura, encontrar su nombre y la asignatura_id de todas las asignaturas que hayan enseñado»
**select** *nombre, asignatura_id* 
**from** *profesor, enseña* 
**where** *profesor.ID = enseña.ID;

Esta consulta se puede escribir de forma más concisa usando la unión natural de SQL como:
**select** *nombre, asignatura_id* 
**from** *profesor* **natural join** *enseña;*

Una cláusula from en una consulta SQL puede tener muchas relaciones combinadas utilizando la unión natural, como se muestra a continuación:
**select** $A_1 , A_2 , …, A_n$ 
**from** $r_1 \ natural \ join \ r_2 \ natural \ join \ … \ natural \ join \ r_m$ 
**where** $P$;

Para obtener las ventajas de la unión natural evitando el peligro de la igualdad errónea entre atributos, SQL proporciona una ==forma del constructor unión natural que permite indicar exactamente qué columnas se deberían igualar.==

**select** *nombre, asignatura_id* 
**from** (*profesor* **natural join** *enseña*) **join** *asignatura*
	**using** (*asignatura_id*)
1. Se calcula: (profesor natural join enseña) 
	raux(ID, enseña.asignatura_id, enseña.secc_id, enseña.semestre, enseña.año, profesor.nombre, nombre_dept, profesor.sueldo) 
2. Se calcula: raux join asignatura using (asignatura_id) 
	r(asignatura_id, ID, enseña.secc_id, enseña.semestre, enseña.año, profesor.nombre, profesor.nombre_dept, profesor.sueldo, asignatura.nombre_asig, asignatura.nombre_dept, asignatura.créditos)

La operación es similar a r1 **natural join** r2, excepto que un par de tuplas t1 de r1 y t2 de r2 casan si t1.A1 = t2.A1 y t1.A2 = t2.A2; incluso si r1 y r2 tienen un atributo común de nombre A3, no se requiere que t1.A3 = t2.A3

### 3.4.1. La operación de renombrado
Los nombres de los atributos en el resultado de una consulta provienen de los nombres de los atributos en las relaciones de la cláusula **from** pero … 
- Dos relaciones de la cláusula **from** pueden tener atributos con los mismos nombres 
- Si se utiliza una expresión aritmética en la cláusula **select**, el atributo resultado no tiene nombre 
- Puede que queramos cambiar este nombre en el resultado 
- Se desean comparar tuplas de la misma relación
SQL permite el renombrado de relaciones y de atributos de la relación resultado con clausula **as**
nombre_anterior **as** nombre_nuevo 
Se puede usar tanto en clausula **from** como **select**
El nuevo nombre se denomina *nombre de correlación* en la norma de SQL, pero normalmente se llaman *alias de tabla*, o *variable de correlación*, o *variable de tupla*.

En el ejemplo anterior, si se desea sustituir el nombre del atributo nombre por el nombre nombre_profesor, se puede rescribir la consulta anterior como:
**select** *nombre* **as** *nombre_profesor, asignatura_id* 
**from** *profesor, enseña* 
**where** *profesor.ID = enseña.ID;

Una razón para renombrar una relación es s==ustituir un nombre de la relación muy largo por una versión más corta que se pueda usar de forma más sencilla en la consulta.== 
Ej: «Para todos los profesores de la universidad que hayan enseñado alguna asignatura, encontrar sus nombres y las asignatura_id de todas las asignaturas que hayan enseñado»:
**select** *T.nombre, S.asignatura_id* 
**from** *profesor* **as** *T, enseña* **as** *S* 
**where** *T.ID = S.ID;

Otra razón para renombrar una relación es el caso en el que ==se desean comparar tuplas de la misma relación==. Entonces se necesita realizar el producto cartesiano de una relación consigo misma, y sin el renombrado, resulta imposible distinguir una tupla de la otra. 
Ej: «Encontrar los nombres de todos los profesores cuyo sueldo sea mayor que al menos un profesor del departamento de Biología».

**select distinct** *T.nombre* 
**from** *profesor* **as** *T, profesor* **as** *S* 
**where** *T.sueldo > S.sueldo* **and** *S.nombre_dept = ´Biología´;*
### 3.4.2. Operaciones con cadenas de caracteres
SQL especifica las cadenas de caracteres encerrándolas entre comillas simples.
La norma SQL especifica que la operación de igualdad entre cadenas de caracteres sí es sensible a mayúsculas. SQL Server y MySQL no.

**Funciones que operan con cadenas:** 
- Concatenación de cadenas: **||** 
- Extraer subcadenas: **substring()** 
- Cálculo longitud de subcadenas: **len()** o **length()** 
- Conversión a mayúsculas o minúsculas: **upper()** y **lower()** 
- Eliminar espacios en blanco al final: **trim()** 
Se pueden usar operadores de comparación con cadenas.

También se puede realizar la comparación de patrones utilizando el operador **like**.
- **like** cierto si cumple el patrón 
- **not like** cierto si no cumple el patrón
Los patrones se escriben utilizando caracteres especiales:
- **Tanto por ciento (%).** El carácter % coincide con cualquier subcadena de caracteres. 
- **Subrayado ( _ ).** El carácter _ coincide con cualquier carácter.
Los patrones distinguen mayúsculas de minúsculas.
Ejemplos de patrones: 
- ' Intro%'  la cadena empieza por “lntro”. 
- ' %lnfor%' la cadena contiene “Infor”
- '_ _ _ ' la cadena tiene exactamente tres caracteres 
- '_ _ _ % ' la cadena tiene, al menos, tres caracteres.
Ej: Encontrar los nombres de todos los departamentos cuyo nombre de edificio incluye la subcadena “Watson” 
**select** *nombre_dept* 
**from** *departamento* 
**where** *edificio* **like** *'%Watson%';*

Para que los patrones puedan contener los caracteres especiales de patrón (esto es, % y _ ) SQL permite la especificación de un carácter de escape. El carácter de escape se utiliza inmediatamente antes de los caracteres especiales de patrón para indicar que ese carácter especial se va a tratar como un carácter normal. El carácter de escape para una comparación **like** se define utilizando la palabra clave **escape**.
- **like** ´ab\%cd%´ **escape** ´\´ coincide con todas las cadenas que empiecen por «ab%cd». 
- **like** ´ab\\cd%´ **escape** ´\´ coincide con todas las cadenas que empiecen por «ab\cd».
### 3.4.3. Especificación de atributos en la cláusula Select
El símbolo asterisco « * » se puede utilizar en la cláusula **select** para indicar «todos los atributos». Por tanto, el uso de *profesor*.* en la cláusula **select** de la consulta: 
**select** *profesor*.* 
**from** *profesor, enseña* 
**where** *profesor.ID = enseña.ID;* 
indica que se seleccionan todos los atributos de *profesor*. ==Una cláusula **select** de la forma **select** * indica que se seleccionan todos los atributos de la relación resultado de la cláusula **from**.==

### 3.4.4. Orden en la presentación de las tuplas
SQL ofrece al usuario cierto control sobre el orden en el cual se presentan las tuplas de una relación. La cláusula **order by** hace que las tuplas del resultado de una consulta se presenten en un cierto orden. 
Ej: obtener una relación en orden alfabético de todos los profesores del departamento de Física
**select** *nombre* 
**from** *profesor* 
**where** *nombre_dept = ´Física´*
**order by** *nombre;*

De manera predeterminada, la cláusula **order by** coloca los elementos en orden ascendente. Para especificar el tipo de ordenación se puede especificar **desc** para orden descendente o **asc** para orden ascendente. Además, se puede ordenar con respecto a más de un atributo. 
Ej: listar todos los profesores en orden descendente de sueldo
**select** * 
**from** *profesor* 
**order by** *sueldo* **desc**, *nombre* **asc**;
### 3.4.5. Predicados de la cláusula where
SQL incluye el operador de comparación **between** para simplificar las cláusulas **where** que indican que un valor sea menor o igual que algún valor, y mayor o igual que otro.
Ej: Lista de los nombres de los profesores con sueldos entre 90.000 € y 100.000 €
**select** *nombre* 
**from** *profesor* 
**where** *sueldo* **between** *90000* **and** *100000*; 
en lugar de: 
**select** *nombre* 
**from** *profesor* 
**where** *sueldo <= 100000* **and** *sueldo >= 90000*;
De forma similar se puede utilizar el operador de comparación **not between**.
### 3.5.1. La operación unión
Para encontrar todas las asignaturas que se enseñaron en el otoño de 2009 o en la primavera de 2010, o en ambas, se escribe:
(**select** *asignatura_id* 
**from** *sección* 
**where** *semestre = ´Otoño´* **and** *año = 2009*) 
**union** 
(**select** *asignatura_id* 
**from** *sección* 
**where** *semestre = ´Primavera´* **and** *año = 2010*); 
A diferencia de la cláusula **select**, la operación **union** elimina los valores duplicados automáticamente.
Si se desea mantener todos los duplicados, hay que escribir **union all** en lugar de **union**
### 3.5.2. La operación intersección
Para encontrar todas las asignaturas que se enseñaron en el otoño de 2009, así como en la primavera de 2010, escribimos: 
(**select** *asignatura_id* 
**from** *sección* 
**where** *semestre = ´Otoño´* **and** *año = 2009*) 
**intersect** 
(**select** *asignatura_id* 
**from** *sección* 
**where** *semestre = ´Primavera´* **and** *año = 2010*); 
La operacion **intersect** elimina los valores duplicados automáticamente. Si se quisieran mantener todos los duplicados habría que escribir **intersect all**.
### 3.5.3. La operación excepto
Para encontrar todas las asignaturas que se enseñaron en el semestre de otoño de 2009 pero que no se enseñaron en el semestre de primavera de 2010, escribimos:
(**select** *asignatura_id* 
**from** *sección* 
**where** *semestre = ´Otoño´* **and** *año = 2009*) 
**except** 
(**select** *asignatura_id* 
**from** *sección* 
**where** *semestre = ´Primavera´* **and** *año = 2010*); 
La operación **except** da como salida todas las tuplas de su primera entrada que no existen en la segunda; es decir, realiza la diferencia. Si se quisiesen mantener los duplicados, se debería utilizar **except all**.

**RESUMEN**: Las operaciones de conjuntos **union**, **intersect**, y **except** operan sobre relaciones y corresponden a las operaciones de álgebra relacional $\cup, \ \cap, \ -$

## 3.6. Valores nulos
Algunos de los valores de una tupla puede tener valor nulo: **null** (el valor es desconocido o no existe)
El problema surge al trabajar con estos valores nulos. Las comparaciones con valores null son un problema. El resultado de cualquier operación aritmética que incluyan, por ejemplo +, -, * o /, es null si cualquier valor de entrada es null.
El predicado **is null** (o **is not null**) se usan para comprobar valor nulo.
SQL trata como **unknown** (desconocido) el resultado de cualquier comparación en la que intervenga el valor **null** excepto para los predicados **is null** o **is not null**.

Hay que manejar tres valores lógicos: **true** - **false** – **unknown**

| OPERACIÓN |     | RESULTADO                                                                                      |
| --------- | --- | ---------------------------------------------------------------------------------------------- |
| OR        |     | (unknown or true) = true,<br>(unknown or false) = unknown <br>(unknown or unknown) = unknown   |
| AND       |     | (true and unknown) = unknown<br>(false and unknown) = false<br>(unknown and unknown) = unknown |
| NOT       |     | (not unknown) = unknown                                                                        |
“P is unknown” se evalúa como true si P es unknown.
El resultado del predicado de una clausula where se trata como false si se evalúa como unknown. ==Si el predicado de la cláusula **where** se evalúa a **false** o a **unknown** para una de las tuplas, dicha tupla no se añade al resultado.==
### 3.7. Funciones de agregación
Las funciones de agregación toman una colección de valores (un conjunto o multiconjunto) y devuelven un único valor. 
-  Media: **avg**. (sólo con números)
- Mínimo: **min**. Si cadena, se queda con el primero por orden alfabético
- Máximo: **max**. Si cadena, se queda con el último por orden alfabético
- Total: **sum**. (sólo con números)
- Recuento: **count**.
### 3.7.1. Agregación básica
Ej: «Encontrar el sueldo medio de los profesores del departamento de Informática»
**select avg** (*sueldo*) 
**from** *profesor* 
**where** *nombre_dept = ´Informática´;*
El resultado de esta consulta es una relación con un único atributo, que contiene una única tupla con un valor numérico correspondiente a la media del sueldo de todos los profesores del departamento de Informática. El sistema de base de datos puede dar un nombre arbitrario al atributo de la relación resultado que se genera de la agregación; sin embargo, podemos asignarle un nombre con sentido utilizando la cláusula **as**:
**select avg** (*sueldo*) **as** *med_sueldo*
**from** *profesor* 
**where** *nombre_dept = ´Informática´;*

A veces interesa mantener duplicados, por ejemplo, para avg 
Si interesa eliminar duplicados se usa clausula distinct

Usaremos la función de agregación count muy a menudo para contar el número de tuplas de una relación
**count** (*atributo*) 
**count** (* ) para contar el número total de tuplas de una relación
SQL no permite el uso de distinct con count (* ) 
==Se puede usar la palabra **all** en lugar de **distinct** para indicar que se mantengan los duplicados (es opción por defecto y no es necesario)==
**select** **count** (* ) 
**from** *asignatura*;
### 3.7.2. Agregación con agrupamiento