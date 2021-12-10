На начальном этапе разработки нейтронного генератора возникает необходимость оценки нейтронного выхода для различных ядерных реакций. 
Чтобы оценить нейтронный выход для различных реакций можно воспользоваться данными о сечении взаимодействия налетающей частицы с атомами мишени (например из JANIS) и данными о 
потерях энергии налетающей частицей в материале и глубине ее проникновения (с помощью SRIM). Для оценки зависимости нейтронного выхода от энергии налетающей частицы может быть 
использована приведенная ниже программа:

#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#include <math.h>
#include <malloc.h>
int main ()
{
  char *line, *rec;
  char buffer[1024];
  char Sig[1024]="";
  char Enx[1024]="";
  double E,Si,dEe,dEn,dE,LamM,Ex,E0,Eh,lam0,h,x,hm,xm,E00,xx,b,c,cc,N;
  double I, Y;
  int n;
  int k0,k;
  double *a; //указатель на массив E(x)
  double *v; //указатель на массив Sigma(E(x)) 
  double *q; //указатель на массив E(x) соответствующих значеним Sigma(E)
  int i, j, u;
  int L=0;
  //printf("Enter filename Si(E)\n");
  //scanf("%s", &Sig);
  //printf("Enter filename E0\n");
  //scanf("%s", &Enx);
  printf("Enter n, *10^23 [1/m^3]\n");
  scanf("%lf", &N);
  N=N*1E23;
  printf("%E\n",N);
  printf("Enter stepsize [um]\n");
  scanf("%lf", &h);
  
  
  //printf("Enter max differnce between E(x)(tabl) and E(x)(calc)[keV]\n");
  //scanf("%lf", &d);
					//printf("Enter number of E(x) for each E0\n");
					//scanf("%i", &b);
  FILE *f1 = fopen("1.csv","r");  
  FILE *f2 = fopen("2.csv","r");
  //FILE *f1 = fopen(Sig,"r");
  //FILE *f2 = fopen(Enx,"r");
  //strcat(Sig,"_Y(E0).dat");
  FILE *f3 = fopen("E(x).dat","wb");
  FILE *f4 = fopen("Sigma(x).dat", "wb");
  FILE *f5 = fopen("Y(E0).dat","wb");
  FILE *f6 = fopen("LamM(E0).dat","wb");
  if(f1 == NULL)   
  {     
    printf("\n file1 opening failed ");      
    return -1 ;   
    } 
  if(f2 == NULL)   
  {     
    printf("\n file2 opening failed ");      
   return -1 ;   
    } 
   k0=10;
   v=(double*)malloc(k0*2*sizeof(double));
   j=0;
   k=0;
 while((line=fgets(buffer,sizeof(buffer),f1))!=NULL) //читаем стоки из файла сигма от E и пишем в массив.
  { 
	rec = strtok (line,";");
    E=atof(rec);
    printf ("%lf\n",E);
    rec=strtok(NULL,";");
    Si=atof(rec);
    printf ("%E\n",Si);
    k++;
    if (k==k0||k>k0) v=(double*)realloc(v,k*2*sizeof(double));
    *(v+j*2+0)=E;
    *(v+j*2+1)=Si;
    j++;
}
  for (j=0;j<k;j++)
  {
  printf("massiv:%lf%s%E\n",*(v + j*2 + 0),"  ",*(v + j*2 + 1));
  }
  fclose(f1);
  j=0;
  i=0;
 while((line=fgets(buffer,sizeof(buffer),f2))!=NULL) //читаем строки из файла E
 { 
	rec = strtok (line,";");
    E0=atof(rec);
    rec=strtok(NULL,";");
    if (strncmp(rec,"Me*",2)==0)
    E0=E0*1000;
    //fprintf (f6,"%lf\n",E0);
    rec=strtok(NULL,";");
    dEe=atof(rec);
     // printf ("%E\n",dEe);
    rec=strtok(NULL,";");
    dEn=atof(rec);
     //printf ("%E\n",dEn);
    rec=strtok(NULL,";");
    LamM=atof(rec);
    rec=strtok(NULL,";");
    if (strncmp(rec,"A*",1)==0)
    LamM=LamM/10000;
    fprintf (f6,"%lf%s%lf\r\n",E0,"     ",LamM);
    dE=dEn+dEe;
    n=LamM/h;
    (int) n;
    a=(double*)malloc(n*2*sizeof(double));
    I=0;
    x=0;
    xm=0;
   lam0=E0/dE;
   hm=(lam0-LamM)/n;
   E00=E0;
  for(i=0; i<n; i++)   //Считаем значения E(x) от каждой прочитанной строки
  {
	Eh=E0-(h*dE);
	printf("%s%lf%s%lf%s%lf\n", "E:", Eh, "  x:", x, "  E0:", E0);
	x=x+h;
	xm=xm+hm;
	//E2h=E0-(2*h*dE);
	//printf("%s%lf%s%lf%s%lf\n", "E:", E2h, "  x:", x, "  E0:", E0);
	//x=x+h;
	dE=Eh/(lam0-(x+xm));
	//I=I+(Eh+E0)*h/2;
	//Et=Et-I;
	E0=Eh;
	*(a+i*2+1)=Eh;
    *(a+i*2+0)=x;
    printf("%s%lf%s%lf%s%lf\n", "E:", Eh, "  x:", x, "  dE:", dE);
    fprintf(f3,"%lf%s%lf\r\n",*(a + i*2 + 0),"  ",*(a + i*2 + 1));
   }
     q=(double*)malloc(k*2*sizeof(double));
       for (j=0; j<k; j++)  //выбираем значения из массива сечений от x
       {
		  for (i=0; i<n; i++) //сравниваем выбранное значение из массива сечений от E со всеми E из массива E(x)
		   {
			
       //if ((fabs(*(a+i*2+1)-*(v+j*2+0)))<d)  // условие при котором значение E из массива сечений считается равным E из E(x)
           //if (((*(v+j*2+0)) > (*(a+i*2+1))) && ((*(v+j*2+0)) < (*(a+(i+1)*2+1))))   // условие при котором значение E из массива сечений подставляется в формулу для расчёта x
           cc=fabs(*(a+i*2+1)-*(a+(i+1)*2+1));
           b=fabs(*(v+j*2+0)-*(a+i*2+1));
           c=fabs(*(v+j*2+0)-*(a+(i+1)*2+1));
           if(b<=cc && c<cc)
       {
		   xx=*(a+i*2+0)-((*(v+j*2+0)-*(a+i*2+1))*h/(fabs(*(a+i*2+1)-*(a+(i+1)*2+1))));
          //*(q+j*2+0)=*(a+i*2+0);  //запись отобранных величин в новый массив сигма от x. 
          *(q+j*2+0)=xx;            //запись отобранных величин в новый массив сигма от x. 
          *(q+j*2+1)=*(v+j*2+1);
          fprintf(f4,"x,Sigma:%lf%s%E\r\n",*(q + j*2 + 0),"  ",*(q+ j*2 + 1));
		}
		//else
		//continue;
	        }
	   }
	   Y=0;
	   j=0;
	   	   while (j<k)
	   	  {
			   Y=Y+0.5*(fabs(*(q+(j+1)*2+0)-*(q+j*2+0)))*(*(q+(j+1)*2+1)+*(q+j*2+1))/10000;
			   j++;
		   }
		Y=Y*N;
		fprintf(f4,"%s%E\r\n","Y=",Y);
		fprintf(f5,"%lf%s%E\r\n",E00,"  ",Y);
	       }	   
  fclose(f2);
  fclose(f3);
  fclose(f4);
  fclose(f5);
  fclose(f6);
  getchar();
  getchar();
  return 0;
}

Инструкция по использованию:
1)	Найти данные об интересующих взаимодействиях налетающего иона с мишенью из заданного материала: 
1. Сечение взаимодействия в зависимости от энергии. Записать в файл 1.csv, где первая строка - величина энергии иона в кэВ, вторая - сечение взаимодействия в см2.
   Можно найти с помощью JANIS
2. Величину потерь энергии (продольных и поперечных) и максимальную глубину проникновения в зависимости от энергии иона. 
   Записать в файл 2.csv, где первая строчка - энергия в кэВ (если МэВ - то после числа должно стоять MeV), вторая - потери энергии dE/dx продольные,
   3-я поперечные потери энергии, 4-я - максимальная глубина проникновения (в мкм или в ангстремах, если в ангстремах - после числа поставить A). Можно получить с помощью SRIM.
2) Оба файла поместить в одну папку с запускаемым файлом программы.
3) Запустить программу. Указать концентрацию атомов вещества мишени (в м-3) и шаг расчета в мкм.
4) В результате работы программа создает в той же папке файл Y(E0).dat в котором 1-ая строчка - энергия налетающих частиц, вторая строчка - выход нейтронов
   (если исходная реакция - нейтронообразующая).
