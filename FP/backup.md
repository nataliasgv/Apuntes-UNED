
  typedef enum TipoMes {
	 Enero, Febrero, Marzo, Abril, Mayo, Junio, Julio, Agosto,
	 Septiembre, Octubre, Noviembre, Diciembre};

	 typedef enum TipoDia {LU, MA, MI, JUs, VI, SA, DO};

  typedef struct TipoFecha {
	  int dia;
	  TipoMes mes;
	  int anno;
  };

  bool bisiesto ( int anno ) {
	  return ((anno % 4 == 0) && (anno % 100 != 0)) || (anno % 400 == 0);
  }



   TipoDia SumarDias (TipoDia dia , int N) {

	   const  int DiasSemana = 7;
	   int aux;

	   aux = (int (dia) + N ) % DiasSemana;
	   return TipoDia (aux);
	   }


   TipoDia DiaSemana ( TipoFecha fecha ) {

	   TipoMes M = fecha.mes;
	   int A = fecha.anno;
	   int IncreDias, IncreAnnos, IncreBisis;
	   const int AnnoOrigen= 1601;
	   const TipoDia DiaReferencia = DO;

	   if (M == Enero) {
		   IncreDias = 0;
	   } else if (M == Febrero ){
		   IncreDias = 3;
	   } else if (M == Marzo ) {
		   IncreDias = 3;
	   } else if (M == Abril ) {
		   IncreDias = 6;
	   } else if (M == Mayo) {
		   IncreDias = 	1;
	   } else if (M == Junio) {
		   IncreDias =  4;
	   } else if (M == Julio) {
		   IncreDias = 6;
	   } else if (M == Agosto) {
		   IncreDias = 2;
	   } else if (M == Septiembre) {
		   IncreDias = 5;
	   } else if (M == Octubre) {
		   IncreDias = 0;
	   } else if (M == Noviembre) {
		   IncreDias = 3;
	   } else {IncreDias = 5;
	   }

    IncreAnnos = A - AnnoOrigen;
    IncreBisis = 0;

    for (int N=1602; N<A; N++) {
      if (bisiesto (N)) {
        IncreBisis ++;
        }
      }

       if ( bisiesto (A) && ( M > Febrero )) {
         IncreDias ++;
         }

       IncreDias = IncreDias + IncreAnnos + IncreBisis + fecha.dia;


       return SumarDias (DiaReferencia, IncreDias);
    }



   int DiasDelMes (TipoFecha fecha) {
     switch (fecha.mes) {
       case Febrero:
          if (bisiesto (fecha.anno)) {
            return (29);
          } else { return (28);
          };
          break;
        case Abril:
        case Junio:
        case Septiembre:
          return (30);
          break;
        default:
          return (31);
       }
     }


int main () {

  int aux;
  int i;

  TipoFecha fecha;
  TipoDia PrimerDia;

  fecha.dia = 1;

  do {
	  printf ("%cMes, entre el 1 y el 12?", 168);
	  scanf ("%d", &aux);

  } while (aux < 1 || aux > 12);

 printf("%ca%co, entre 1601 y 3000?",168,164);
  scanf ("%d", &fecha.anno);

  fecha.mes = TipoMes (aux - 1);
  PrimerDia = DiaSemana (fecha);


  if (fecha.anno >= 1601 && fecha.anno <= 3000) {

	  printf ("\n");

	  switch (fecha.mes) {
	  case Enero:
	  printf ("ENERO     ");
	  break;
	  case Febrero:
	  printf ("FEBRERO   ");
	  break;
	  case Marzo:
	  printf ("MARZO     ");
	  break;
	  case Abril:
	  printf ("ABRIL     ");
	  break;
	  case Mayo:
	  printf ("MAYO      ");
	  break;
	  case Junio:
	  printf ("JUNIO     ");
	  break;
	  case Julio:
	  printf ("JULIO     ");
	  break;
	  case Agosto:
	  printf ("AGOSTO    ");
	  break;
	  case Septiembre:
	  printf ("SEPTIEMBRE");
	  break;
	  case Octubre:
	  printf ("OCTUBRE   ");
	  break;
	  case Noviembre:
	  printf ("NOVIEMBRE ");
	  break;
	  case Diciembre:
	  printf ("DICIEMBRE ");
	  break;
	  }

	  printf ("             ");
	  printf ("%d\n", fecha.anno);
	  printf ("===========================\n");
	  printf ("LU  MA  MI  JU  VI | SA  DO\n");
	  printf ("===========================\n");

	i = 0;


/*imprime tantos puntos como espacios haya hasta el primer dia de la semana del mes*/
	for (int k = int (PrimerDia); k >= 1; k --) {
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
	for (int k = 0; k < DiasDelMes (fecha); k ++) {
	  if (i != 0) {
		  if (i % 7 == 0) {
			  printf ("\n"); /*al final de la semana se pone un salto de linea*/
		  }
	  }
	   if (i % 7 == 5) {
		  printf ("| "); /*sexta posicion, columna*/
	  }
	  if ( i %7 != 0 && i % 7 != 5 ) { /*no es primera pos de la semana ni sexta*/
		printf (" ");
	  }
	  printf ("%2d ", k+1 ); /*ocupa dos espacios mas un espacio mas despues*/
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
  }
}