# Cuarta Práctica Fundamentos de Programación Curso 2024-2025

texWorks

##### Natalia Solana Gavrilenko
DNI:54866052N

### OBJETIVO:

El objetivo de la práctica es desarrollar un programa en C+- para gestionar las reservas de apartamentos en un edificio.

Las operaciones del programa serán las siguientes:

• Editar Edificio

• Listar Edificios

• Apartamentos Disponibles

• Reservar Apartamento

• Reservas Mensuales de Apartamento

El programa se divide en tres módulos, GesRAE, calendario y menu, cada uno de ellos compuesto por una interfaz ".h" y un fichero de implementación ".cpp".

![]( 
        $path = $matches[1]
        $path -replace ' ', '%20'  # Reemplaza los espacios por %20
     ", "%20")) image 20250112070449.png)

La figura muestra la estructura del programa, indicando las relaciones de dependencia de unos módulos respecto a otros. Las flechas indican que un módulo utiliza directamente elementos de otro.

### Módulo GesRAE

Este modulo contiene la interfaz de los métodos principales del programa:

Define las constantes detalladas en el enunciado de la práctica. El  máximo numero de Edificios y de Apartamentos.

```
const int maxEdifs = 5;
const int maxAparts = 20;
```
 
Seguidamente, se crea un vector de caracteres para poder definir elementos de tipo String. Se eligen 9 caracteres como máximo.

```
typedef char tipoString[9];
```

Se define un enumerado con los tipo de Apartamentos que puede tener un edificio:

```
typedef enum TipoTipoApart {
  Basico, Normal, Lujo
  };
```

Se definen las tres estructuras principales del programa, TipoReserva, TipoApart y TipoEdif. 
La estructura TipoReserva incluye un TipoFecha (definido en la interfaz calendario) que designa la fecha de entrada a la reserva, un int con la duración de la estancia y un booleano que establece si un apartamento ha sido reservado o no.
La estructura TipoApart contiene los datos de un apartamento. El identificador de su edificio, un String con la referencia del apartamento, el tipo de apartamento y una lista de reservas (se elige diez como el máximo número de reservas que puede tener un apartamento).
La estructura TipoEdif contiene los datos de un edificio. Su identificador y nombre, el numero de apartamentos de cada tipo, el numero de apartamentos en total y el numero de apartamentos libres de cada tipo. Incluye también una lista con todos los apartamentos del edificio.

```
typedef struct TipoReserva{
  TipoFecha fechaEntrada;
  int duracion;
  bool reservado;
};

typedef struct TipoApart{
  int idEdif;
  tipoString refApart;
  TipoTipoApart tipoApart;

  TipoReserva listaReservas[10];
};

typedef struct TipoEdif{
  int idEdif;
  int numBasicos;
  int numNormales;
  int numLujos;
  tipoString nombre;
  int numAparts;
  int numBasLibres;
  int numNorLibres;
  int numLujLibres;

  TipoApart listaAparts[maxAparts];
};
```
La siguiente estructura contiene la interfaz de los métodos utilizados en GesRAE.cpp. 
```
typedef struct GesRAE{
  void init();
  int buscarEdif(int ident);
  void editarEdif(int idEdif, tipoString nombre, int basicos, int normales, int lujos);
  void listarEdifs();
  void listarApartsLibres(int idEdif, int dia1, int mes1, int anno1, int duracion1);
  void reservarApart(int idEdif, TipoTipoApart tipo, int dia1, int mes1, int anno1, int duracion1);
  void referenciaApart(int idEdif);
  void reservasMensApart(tipoString Ref, int mes, int anno);
  bool fechaReal(int dia, int mes, int anno);
  int diasFecha(int dia, int mes, int anno);
  bool coincidenciaFechas(int dia1, int mes1, int anno1, int duracion1, int dia2, int mes2, int anno2, int duracion2);

  private:
  TipoEdif listaEdifs[maxEdifs];
  int numEdifs;
  TipoEdif edificio;
  bool reservado; /*si un apartamento esta reservado en una fecha concreta*/
  bool completo; /*si todos los apartamentos estan reservados en una fecha concreta*/
  int numReservas;
};
```


A continuación se explica la implementación de cada método.
#### init
Este método inicializa los datos de la práctica.
```
void GesRAE::init(){
  int numEdifs = 0;
  int numReservas = 0;
  for(int i = 0; i < maxEdifs; i++ ){
    listaEdifs[i].numAparts = 0;
    listaEdifs[i].numBasicos = 0;
    listaEdifs[i].numNormales = 0;
    listaEdifs[i].numLujos = 0;
    listaEdifs[i].numBasLibres = 0;
    listaEdifs[i].numNorLibres = 0;
    listaEdifs[i].numLujLibres = 0;
    listaEdifs[i].idEdif = i;

    for(int k = 0; k < maxAparts; k ++){
      strcpy(listaEdifs[i].listaAparts[k].refApart, "APT00X00"); /*añadir el metodo que da nombre a los aprts*/

      for(int n = 0; n < 10; n++){
        listaEdifs[i].listaAparts[k].listaReservas[n].fechaEntrada.dia = 0;
        listaEdifs[i].listaAparts[k].listaReservas[n].fechaEntrada.mes = 1; 
        listaEdifs[i].listaAparts[k].listaReservas[n].fechaEntrada.anno = 0;
        listaEdifs[i].listaAparts[k].listaReservas[n].duracion = 0;
        listaEdifs[i].listaAparts[k].listaReservas[n].reservado = false;
        }
      }
    }
  }
```

#### buscarEdif
Este método retorna la posicion de un edificio según su identificador. Si no se encuentra el edificio, el método retorna -1

```
int GesRAE::buscarEdif( int ident ) {
  for (int pos = 0; pos < numEdifs; pos++) {
    if (listaEdifs[pos].idEdif == ident){
        return pos;
      }
    }
    return -1; 
  }
```

#### referenciaApart
Crea la referencia de cada apartamento de un edificio. Las referencias de los apartamentos se forman con APT seguido del identificador del edificio, el tipo de apartamento (B-Básico/N-Normal/L-Lujo) y el identificador del apartamento.

```
void GesRAE::referenciaApart(int idEdif){

  int pos = buscarEdif(idEdif);

  if(pos != -1){
      for(int i = 0; i < listaEdifs[pos].numAparts; i++){

        if (listaEdifs[pos].listaAparts[i].tipoApart == Basico) {

          sprintf(listaEdifs[pos].listaAparts[i].refApart, "APT%02dB%02d", idEdif, i + 1);
        }
        else if (listaEdifs[pos].listaAparts[i].tipoApart == Normal) {

          sprintf(listaEdifs[pos].listaAparts[i].refApart, "APT%02dN%02d", pos + 1, i + 1);
        }
        else if (listaEdifs[pos].listaAparts[i].tipoApart == Lujo) {

          sprintf(listaEdifs[pos].listaAparts[i].refApart, "APT%02dL%02d", pos + 1, i + 1);
        }
      }
    }
  }
```

####  editarEdif

El método editarEdif permite introducir los datos de uno de los 5 edificios.

```
void GesRAE::editarEdif(int id, tipoString nom, int basicos, int normales, int lujos) {
  int pos = buscarEdif(id);
  if(pos != -1){
      strcpy(listaEdifs[pos].nombre , nom);
      listaEdifs[pos].numBasicos = basicos;
      listaEdifs[pos].numNormales = normales;
      listaEdifs[pos].numLujos = lujos;
      listaEdifs[pos].numAparts = basicos + normales + lujos;
      referenciaApart(id);
    }
    else{
      printf("Edificio no encontrado \n");
    }
  }
```

#### listarEdifs
Lista todos los edificios de la lista de edificios con sus datos.

```
void GesRAE::listarEdifs(){
  for (int pos = 0; pos < maxEdifs; pos++){
    printf("Id     Nombre     Aptos Basicos     Aptos Normales     Aptos de Lujo \n");
    printf("%d      %s             %d                 %d                 %d\n" ,pos + 1, listaEdifs[pos].nombre, listaEdifs[pos].numBasicos, listaEdifs[pos].numNormales, listaEdifs[pos].numLujos);
    }
  }
```

#### Métodos fecha
Los siguientes métodos son necesarios para ver si dos reservas coinciden.

##### fechaReal
Este método se asegura de que la fecha introducida es válida.

```
bool GesRAE::fechaReal(int dia, int mes, int anno){

bool real;

  if (anno >= 1601 && anno <= 3000) {

    if(mes >= 1 && mes<= 12){


      if((dia >= 1 && dia <= 28)&&(mes == 2)){
        real = true;
        }
      else if((dia >= 1 && dia <= 30)&&(mes == 4 || mes == 6 || mes == 9 || mes == 11)){
        real = true;
      }
      else if((dia >= 1 && dia <= 31)&&(mes == 1 || mes == 3 || mes == 5 || mes == 7 || mes == 8 || mes == 10 || mes == 12)){
        real = true;
      }
      else if(dia ==29 && mes == 2&&((anno % 4 == 0) && (anno % 100 != 0)) || (anno % 400 == 0)){
        real = true;
      }
      else{
      real = false;
      }
    }
    else{
      real = false;
      }
  }
  else{
      real = false;
      }
  return real;
}
```

#### compararFechas
Este método compara dos fechas para saber cual de ellas es anterior. Devuelve -1 si la primera fecha es aterior, 1 si la segunda fecha es anterior y 0 si son iguales.

```
int GesRAE::compararFechas(int dia1, int mes1, int anno1, int dia2, int mes2, int anno2){
  if(anno1 < anno2){
    return -1;
    }else if(anno1 > anno2){
      return 1;
      }else{
        if(mes1 < mes2){
          return -1;
          }else if(mes1 > mes2){
            return 1;
            }else{
              if(dia1 < dia2){
                return -1;
                }else if(dia1 > dia2){
                  return 1;
              }else {
                return 0;
                }
            }
      }
}
```
#### diasFecha
Convierte la fecha introducida en un número de días.

```
int GesRAE::diasFecha(int dia, int mes, int anno){

  int dias = dia;
  int diasMes;


  /*establece el numero de dias de cada mes*/
  switch(mes){
    case 4: diasMes = 30;
    break;
    case 6: diasMes = 30;
    break;
    case 9: diasMes = 30;
    break;
    case 11: diasMes = 30;
    break;
    case 2:
    if((anno % 4 == 0 && anno % 100 != 0) || (anno % 400 == 0)){
      diasMes = 29;
      }
    else{
      diasMes = 28;
      }
    break;
    default: diasMes = 31;
    }
  /*suma el dia al numero de dias del mes y lo guarda en dias*/
  for(int n =1; n<mes; n++){
    dias = dias + diasMes;
    }

  /*suma dias al numero de dias en el año*/
  for(int a = 1601; a<anno; a++){
    if((anno % 4 == 0 && anno % 100 != 0) || (anno % 400 == 0)){
      dias = dias + 366;
      }
     else{
       dias = dias + 365;
       }
    }
    return dias;
  }
```

#### coincidenciaFechas
Este método retorna true si dos periodos de reserva se solapan. 
El primer paso es llamar a compararFechas para saber cual es anterior, una vez establecido; crea dos enteros, uno para la fecha de inicio de las reservas a comparar y otro para la fecha de fin. Si el inicio de la primera fecha es menor que el fin de la segunda y el inicio de la segunda es menor que el fin de la primera, las fechas se solapan.  Esta condición solo funciona si la primera fecha es menor que la segunda, por eso es necesario compararlas al principio.

```
bool GesRAE::coincidenciaFechas(int dia1, int mes1, int anno1, int duracion1, int dia2, int mes2, int anno2, int duracion2){

  int dia11;
  int mes11;
  int anno11;

  int dia22;
  int mes22;
  int anno22;

  if(compararFechas(dia1, mes1, anno1, dia2, mes2, anno2)== 1){
    dia11 = dia2;
    mes11 = mes2;
    anno11 = anno2;

    dia22 = dia1;
    mes22 = mes1;
    anno22 = anno1;
    }else if(compararFechas(dia1, mes1, anno1, dia2, mes2, anno2)== -1){
      dia11 = dia1;
      mes11 = mes1;
      anno11 = anno1;

      dia22 = dia2;
      mes22 = mes2;
      anno22 = anno2;
      }else{
        return true; /*si ambas fechas son la misma los periodos coinciden*/
        }

  int inic1 = diasFecha(dia11, mes11, anno11);
  int fin1 = inic1 + duracion1;
  int inic2 = diasFecha(dia22, mes22, anno22);
  int fin2 = inic2 + duracion2;

  return(inic1 < fin2 && inic2 < fin1);
  }
```

### reservarApart
Permite hacer la reserva de un apartamento en para una fecha y duración concreta. Este método hace uso de los métodos explicados anteriormente pra comparar fechas.

```
void GesRAE:: reservarApart(int idEdif, TipoTipoApart tipo, int dia1, int mes1, int anno1, int duracion1){
  int pos = buscarEdif(idEdif);

  if(pos != -1){

    edificio = listaEdifs[pos];

    switch(tipo){

      case B:
      completo = true;/*variable para ver si todos los apartamentos estan reservados*/

        for(int i = 0; i < edificio.numAparts; i++){
          if (edificio.listaAparts[i].tipoApart == Basico){
             reservado = false; /*variable para cada apartamento*/


/*mira cada una de las reservas de cada apartamento de un edificio y las compara con las dadas por el usuario*/
              for(int n = 0; n < 10; n++){
                int dia2 = edificio.listaAparts[i].listaReservas[n].fechaEntrada.dia;
                int mes2 = edificio.listaAparts[i].listaReservas[n].fechaEntrada.mes;
                int anno2 = edificio.listaAparts[i].listaReservas[n].fechaEntrada.anno;
                int duracion2 = edificio.listaAparts[i].listaReservas[n].duracion;

                if(coincidenciaFechas(dia1, mes1, anno1, duracion1, dia2, mes2, anno2, duracion2)== false){

                  edificio.listaAparts[i].listaReservas[n].fechaEntrada.dia = dia1;
                  edificio.listaAparts[i].listaReservas[n].fechaEntrada.mes = mes1;
                  edificio.listaAparts[i].listaReservas[n].fechaEntrada.anno = anno1;
                  edificio.listaAparts[i].listaReservas[n].duracion = duracion1;
                  edificio.listaAparts[i].listaReservas[n].reservado = true;

                  printf("Apartamento reservado con éxito");
                  reservado = true;
                  completo = false; /*hay un apartamento libre*/
                  numReservas++;

                  printf("        Datos de la reserva: \n");
                  printf("\n");
                  printf("    Número de Reserva: %d \n", &numReservas);
                  printf("    Edificio: %s (Id=%d)\n", edificio.nombre, idEdif);
                  printf("    Referencia Apartamento: %s \n", &edificio.listaAparts[i].refApart);
                  printf("    Fecha Entrada: %d/%d/%d \n", &dia1, &mes1, &anno1);
                  printf("    Duración estancia: %d \n", &duracion1);

                  break; /*evita seguir revisando reservas*/
                  }
              }
              if(reservado){
                break; /*evita seguir revisando apartamentos*/
                    }
            }
        }
        if(completo){
          printf("Todos los apartamentos Básicos están reservados en la fecha introducida");
          }
        break;
        case N:
          completo = true;

          for(int i = 0; i < edificio.numAparts; i++){

          if (edificio.listaAparts[i].tipoApart == Normal) {
            reservado = false;

              for(int n = 0; n < 10; n++){
                int dia2 = edificio.listaAparts[i].listaReservas[n].fechaEntrada.dia;
                int mes2 = edificio.listaAparts[i].listaReservas[n].fechaEntrada.mes;
                int anno2 = edificio.listaAparts[i].listaReservas[n].fechaEntrada.anno;
                int duracion2 = edificio.listaAparts[i].listaReservas[n].duracion;

                if(coincidenciaFechas(dia1, mes1, anno1, duracion1, dia2, mes2, anno2, duracion2)== false){
                  edificio.listaAparts[i].listaReservas[n].fechaEntrada.dia = dia1;
                  edificio.listaAparts[i].listaReservas[n].fechaEntrada.mes = mes1;
                  edificio.listaAparts[i].listaReservas[n].fechaEntrada.anno = anno1;
                  edificio.listaAparts[i].listaReservas[n].duracion = duracion1;
                  edificio.listaAparts[i].listaReservas[n].reservado = true;

                  printf("Apartamento reservado con éxito");
                  reservado = true;
                  completo = false;
                  numReservas++;

                  printf("        Datos de la reserva: \n");
                  printf("\n");
                  printf("    Número de Reserva: %d \n", &numReservas);
                  printf("    Edificio: %s (Id=%d)\n", edificio.nombre, idEdif);
                  printf("    Referencia Apartamento: %s \n", &edificio.listaAparts[i].refApart);
                  printf("    Fecha Entrada: %d/%d/%d \n", &dia1, &mes1, &anno1);
                  printf("    Duración estancia: %d \n", &duracion1);

                  break; /*evita seguir revisando reservas
                  }
              }

              if(reservado){
                break;
                    }
            }
        }
        if(completo){
          printf("Todos los apartamentos Normales están reservados en la fecha introducida");
          }
        break;
        case L:
         completo = true;

          for(int i = 0; i < edificio.numAparts; i++){

          if (edificio.listaAparts[i].tipoApart == Lujo) {
            reservado = false;

              for(int n = 0; n < 10; n++){
                int dia2 = edificio.listaAparts[i].listaReservas[n].fechaEntrada.dia;
                int mes2 = edificio.listaAparts[i].listaReservas[n].fechaEntrada.mes;
                int anno2 = edificio.listaAparts[i].listaReservas[n].fechaEntrada.anno;
                int duracion2 = edificio.listaAparts[i].listaReservas[n].duracion;

                if(coincidenciaFechas(dia1, mes1, anno1, duracion1, dia2, mes2, anno2, duracion2)== false){
                  edificio.listaAparts[i].listaReservas[n].fechaEntrada.dia = dia1;
                  edificio.listaAparts[i].listaReservas[n].fechaEntrada.mes = mes1;
                  edificio.listaAparts[i].listaReservas[n].fechaEntrada.anno = anno1;
                  edificio.listaAparts[i].listaReservas[n].duracion = duracion1;
                  edificio.listaAparts[i].listaReservas[n].reservado = true;

                  printf("Apartamento reservado con éxito");
                  reservado = true;
                  completo = false;
                  numReservas++;

                  printf("        Datos de la reserva: \n");
                  printf("\n");
                  printf("    Número de Reserva: %d \n", &numReservas);
                  printf("    Edificio: %s (Id=%d)\n", edificio.nombre, idEdif);
                  printf("    Referencia Apartamento: %s \n", &edificio.listaAparts[i].refApart);
                  printf("    Fecha Entrada: %d/%d/%d \n", &dia1, &mes1, &anno1);
                  printf("    Duración estancia: %d \n", &duracion1);

                  break; /*evita seguir revisando reservas
                  }
              }
              if(reservado){
                break;
                    }
            }
        }
        if(completo){
          printf("Todos los apartamentos de Lujo están reservados en la fecha introducida");
          }
        break;
      }
    }
    else{
      printf("Edificio no encontrado \n");
      }
  }
```

### listarApartsLibres
Por último, este método lista todos los apartamentos disponibles de un edificio.

```
void GesRAE::listarApartsLibres(int idEdif, int dia1, int mes1, int anno1, int duracion1){
  int pos = buscarEdif(idEdif);

  if(pos != -1){/*el edifificio existe
    edificio = listaEdifs[pos];

    for(int i = 0; i < edificio.numAparts; i++){

      for(int n = 0; n < 10; n++){

          int dia2 = edificio.listaAparts[i].listaReservas[n].fechaEntrada.dia;
          int mes2 = edificio.listaAparts[i].listaReservas[n].fechaEntrada.mes;
          int anno2 = edificio.listaAparts[i].listaReservas[n].fechaEntrada.anno;
          int duracion2 = edificio.listaAparts[i].listaReservas[n].duracion;

          if(coincidenciaFechas(dia1, mes1, anno1, duracion1, dia2, mes2, anno2, duracion2)== false){

           TipoTipoApart tipoApartamento = edificio.listaAparts[i].tipoApart;

           switch(tipoApartamento){
             case Basico:
             numBasLibres++;
             break;
             case Normal:
             numNorLibres++;
             break;
             case Lujo:
             numLujLibres++;
             break;
          }
        }
      }
    } /*mira todas las reservas de los apartamentos y cuenta cuanto apartamentos hay libres en esa fecha*/

    printf("El edificio %s desde el %d/%d/%d y %d días de estancia, tendría disponibles: \n",
              edificio.nombre, dia1, mes1, anno1, duracion1 );
    printf("%d apartamentos tipo Básico \n", edificio.numBasLibres);
    printf("%d apartamentos tipo Normal \n", edificio.numNorLibres);
    printf("%d apartamentos tipo Lujo \n", edificio.numLujLibres);
  }
  else{
    printf("Edificio no encontrado \n");
    }
```

### Módulo calendario
Este módulo contiene los elementos necesarios para imprimir un calendario (desde el año 1601 hasta el 3000).
Define un enumerado llamado TipoDia que contiene los días de la semana y una estructura llamada TipoFecha con el día, mes y año.

```
typedef enum TipoDia {LU, MA, MI, JUs, VI, SA, DO};

typedef struct TipoFecha {
	  int dia;
    int mes;
	  int anno;
};
```

Sus métodos son los siguientes:

```
typedef struct Calendario{
  bool bisiesto ( int anno );
  TipoDia sumarDias (TipoDia dia , int n);
  TipoDia diaSemana ( TipoFecha fecha );
  int diasDelMes (TipoFecha fecha);

  void imprimirCalendario(int mes, int anno);

  private:
  int i;
  TipoFecha fecha;
  TipoDia primerDia;
};
```

A continuación se explica la implementación de cada método.

### bisisesto
Comprueba si un año es bisiesto o no.
```
bool Calendario::bisiesto ( int anno ) {
	  return ((anno % 4 == 0) && (anno % 100 != 0)) || (anno % 400 == 0);
  }
```

### sumarDias
Suma un número de días a un día y devuelve el día de la semana correspondiente.

```
TipoDia Calendario::sumarDias (TipoDia dia , int n) {

	   const  int DiasSem = 7;
	   int aux;

	   aux = (int (dia) + n ) % DiasSem;
	   return TipoDia (aux);
	   }
```

### diasDelMes
Retorna el número de días de u mes.
```
int Calendario::diasDelMes (TipoFecha fecha) {
     switch (fecha.mes) {
       case 2:
          if (bisiesto (fecha.anno)) {
            return (29);
          } else { return (28);
          };
          break;
        case 4:
        case 6:
        case 9:
          return (30);
          break;
        default:
          return (31);
       }
     }
```
### diaSemana

Devuelve el día de la semana de una fecha.

```
TipoDia Calendario::diaSemana ( TipoFecha fecha ) {

	   int mes = fecha.mes;
	   int a = fecha.anno;
	   int IncreDias, IncreAnnos, IncreBisies;
	   const int AnnoRef= 1601;
	   const TipoDia DiaReferencia = DO;

	   if (mes == 1) {
		   IncreDias = 0;
	   } else if (mes ==2){
		   IncreDias = 3;
	   } else if (mes == 3 ) {
		   IncreDias = 3;
	   } else if (mes == 4 ) {
		   IncreDias = 6;
	   } else if (mes == 5) {
		   IncreDias = 	1;
	   } else if (mes == 6) {
		   IncreDias =  4;
	   } else if (mes == 7) {
		   IncreDias = 6;
	   } else if (mes == 8) {
		   IncreDias = 2;
	   } else if (mes == 9) {
		   IncreDias = 5;
	   } else if (mes == 10) {
		   IncreDias = 0;
	   } else if (mes == 11) {
		   IncreDias = 3;
	   } else {
	     IncreDias = 5;
	   }

    IncreAnnos = a - AnnoRef;
    IncreBisies = 0;

    /*calcula cuantos años bisiestos ha habido desde el 1601*/
    for (int n=1602; n<a; n++) {
      if (bisiesto(n)) {
        IncreBisies ++;
        }
      }

      /*si el año es bisiesto y el mes posterior a feb incrementa IncreDias*/
       if ( bisiesto(a) && ( mes > 2 )) {
         IncreDias ++;
         }

       IncreDias = IncreDias + IncreAnnos + IncreBisies + fecha.dia;

      /*calcula el dia de la semana sumando el incremento*/
       return sumarDias(DiaReferencia, IncreDias);
    }
```

### imprimirCalendario
Finalmente, este método imprime por pantalla el calendario

```
void Calendario::imprimirCalendario(int mes, int anno) {

if(mes>=1 && mes<=12 && anno>=1601 && anno<=3000){

    fecha.dia = 1;
    fecha.mes = mes;
    fecha.anno = anno;

    primerDia = diaSemana (fecha);

      printf ("\n");

      switch (fecha.mes) {
      case 1:
      printf ("ENERO     ");
      break;
      case 2:
      printf ("FEBRERO   ");
      break;
      case 3:
      printf ("MARZO     ");
      break;
      case 4:
      printf ("ABRIL     ");
      break;
      case 5:
      printf ("MAYO      ");
      break;
      case 6:
      printf ("JUNIO     ");
      break;
      case 7:
      printf ("JULIO                  %d\n", fecha.anno);
      break;
      case 8:
      printf ("AGOSTO                 %d\n", fecha.anno);
      break;
      case 9:
      printf ("SEPTIEMBRE             %d\n", fecha.anno);
      break;
      case 10:
      printf ("OCTUBRE                %d\n", fecha.anno);
      break;
      case 11:
      printf ("NOVIEMBRE              %d\n", fecha.anno);
      break;
      case 12:
      printf ("DICIEMBRE              %d\n", fecha.anno);
      break;
      }

      printf ("             ");
      printf ("%d\n", fecha.anno);
      printf ("===========================\n");
      printf ("LU  MA  MI  JU  VI | SA  DO\n");
      printf ("===========================\n");

    i = 0;

/*imprime tantos puntos como espacios haya hasta el primer dia de la semana del mes*/
    for (int k = int (primerDia); k >= 1; k --) {
      if (i % 7 == 5) {
        printf ("| ");/*si i es igual a 5, 12, etc se imprime una columna, queda impresa en la sexta pos de la semana*/
      }
      if ( i %7 != 0 && i % 7 != 5 ) {
      printf (" ");
      }
      printf (" . ");
      i ++;
    }
/*imprime lso dias del mes*/
    for (int k = 0; k < diasDelMes(fecha); k ++) {
      if (i != 0) {
        if (i % 7 == 0) {
          printf ("\n");/*al final de la semana se pone un salto de linea*/
        }
      }
       if (i % 7 == 5) {
        printf ("| ");/*sexta posicion, columna*/
      }
      if ( i %7 != 0 && i % 7 != 5 ) {/*no es primera pos de la semana ni sexta*/
      printf (" ");
      }
      printf ("%2d ", k+1 );/*ocupa dos espacios mas un espacio mas despues*/
      i ++;
    }

    while ( i % 7 != 0 ) {
      if (i % 7 == 5) {
        printf ("| ");
      }
      if ( i %7 != 0 && i % 7 != 5 ) {
        printf (" ");
      }
      printf (" . ");
      i ++;
    }
    printf ("\n");
  }else{
    printf("Fecha no válida");
    }
}
```

### Módulo menu

La interfaz del módulo menu contiene los métodos implementados en su fichero .cpp. Este módulo define el menú principal del programa, así como los menús secundarios correspondientes a cada operación.

```
typedef struct menu{
  void inicializar();
  void volver();
  void menuPrincipal();
  void menuEditarEdif();
  void menuListEdifs();
  void menuApartsLibres();
  void menuResApart();
  void menuResMens();

  private:

  GesRAE gesRAE;

  };
```

A continuación se explica la implementación de cada método.

### inicializar
Este método llama al método init de GesRAE, e inicializa los datos del programa.
```
void menu::inicializar(){
    gesRAE.init();
}
```

### menuPrincipal

Imprime el menú principal en pantalla. Según la tecla que pulse el usuario, el programa llamará a la función correspondiente de GesRAE.

```
void menu::menuPrincipal(){

  char input;

  do{

    printf("GesRAE: Gestión de Reservas Apartamentos-Edificios \n");
    printf("\n");
    printf("    Editar Edificio                   (Pulsar E) \n");
    printf("    Listar Edificios                  (Pulsar L) \n");
    printf("    Apartamentos Disponibles          (Pulsar A) \n");
    printf("    Reservar Apartamento              (Pulsar R) \n");
    printf("    Reservas Mensuales Apartamento    (Pulsar M) \n");
    printf("    Salir                             (Pulsar S) \n");
    printf("\n");
    printf("Teclear una opción válida\n");

    scanf(" %c" , &input);

    switch(input){
      case 'E':
        menuEditarEdif();
      break;
      case 'L':
        menuListEdifs();
      break;
      case 'A':
        menuApartsLibres();*/
      break;
      case 'R':
        menuResApart();
      break;
      case 'M':
        menuResMens();
      break;
      case 'S':
        printf("Saliendo del programa");
      break;
      default:
      printf("Opción no valida");
      }
    }while(input != 'S');
  }
```


### menuEditarEdif
Imprime el menú que aparece en pantalla cuando se selecciona la opción Editar Edificio. Tras pedir los datos al usuario, llama a la función correspondiente.

```

void menu::menuEditarEdif(){

  char control;
  tipoString nombre;
  int id, numBasicos, numNormales, numLujos;

      printf("Editar Edificio: \n");
      printf("    Identificador(número entre 1 y 5)?");
      scanf("%d" , &id);
      printf("\n");

      printf("    Nombre(entre 1 y 20 caracteres)?");
      scanf("%20s" , &nombre);
      printf("\n");

      printf("    Numero de apartamentos Básicos?");
      scanf("%d" , &numBasicos);
      printf("\n");

      printf("    Numero de apartamentos Normales?");
      scanf("%d" , &numNormales);
      printf("\n");

      printf("    Numero de apartamentos de Lujo?");
      scanf("%d" , &numLujos);
      printf("\n");

      printf("IMPORTANTE: Esta opción borra los datos anteriores. \n");
      printf("Son correctos sus nuevos datos(S/N)? \n");
      scanf(" %c" , &control);
      printf("\n");

      if(control == 'S'){
        gesRAE.editarEdif(id, nombre, numBasicos, numNormales, numLujos);
        printf("Los datos se han guardado");
        menuPrincipal();
      }else{
        printf("Los datos no se han guardado\n");
        menuPrincipal();
        };
}
```

### menuListarEdifs
Imprime el menú que aparece en pantalla al seleccionar la opción Listar Edificios y llama a la función correspondiente.

```
void menu::menuListEdifs(){
  gesRAE.listarEdifs();
  menuPrincipal();
  }
```

### menuApartsLibres
Imprime el menú que aparece en pantalla cuando se selecciona la opción Apartamentos Disponibles. Tras pedir los datos al usuario, llama a la función correspondiente.

```

void menu::menuApartsLibres(){

  int id, dia, mes, anno, duracion;

  printf("Apartamentos disponibles: \n");
  printf("    Identificador del edificio?");
  scanf(" %d", &id);
  printf("\n");

  printf("    Fecha de Entrada: Dia?");
  scanf(" %d", &dia);
  printf("\n");

  printf("    Fecha de Entrada: Mes?");
  scanf(" %d", &mes);
  printf("\n");

  printf("    Fecha de Entrada: Año?");
  scanf(" %d", &anno);
  printf("\n");

  printf("    Dias de duracion de la estancia?");
  scanf(" %d", &duracion);
  printf("\n");

  gesRAE.listarApartsLibres(id, dia, mes, anno, duracion);

  menuPrincipal();
  }
```

### menuResApart
Imprime el menú que aparece en pantalla cuando se selecciona la opción para reservar un apartamento. Tras pedir los datos al usuario, llama a la función correspondiente.

```
void menu::menuResApart(){

  int id, dia, mes, anno, duracion;
  char tipo;
  TipoTipoApart tipoApart;

  printf("Reservar apartamento: \n");

  printf("    Identificador del edificio?");
  scanf(" %d", &id);
  printf("\n");

  printf("Tipo de Apartamento (B-Basico/N-Normal/L-Lujo)?");
  scanf(" %c", &tipo);
  printf("\n");

  printf("    Fecha de Entrada: Dia?");
  scanf(" %d", &dia);
  printf("\n");

  printf("    Fecha de Entrada: Mes?");
  scanf(" %d", &mes);
  printf("\n");

  printf("    Fecha de Entrada: Año?");
  scanf(" %d", &anno);
  printf("\n");

  printf("    Dias de duracion de la estancia?");
  scanf(" %d", &duracion);
  printf("\n");

  printf("Es correcta la operacion (S/N)? \n");

  switch(tipo){

    case 'B':
      tipoApart = Basico;
      gesRAE.reservarApart(id, tipoApart, dia, mes, anno, duracion);
      menuPrincipal();
      break;

    case 'N':
      tipoApart = Normal;
      gesRAE.reservarApart(id, tipoApart, dia, mes, anno, duracion);
      menuPrincipal();
      break;

    case 'L':
      tipoApart = Lujo;
      gesRAE.reservarApart(id, tipoApart, dia, mes, anno, duracion);
      menuPrincipal();
      break;

    default:
    printf("Opción no valida");
    menuPrincipal();

    }
  }
```

