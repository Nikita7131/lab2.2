# lab2.2 від творця лаба 1.2 (~200 cимволів) в 3 рядка коду

![alt tag](https://github.com/Nikita7131/lab2.2/blob/main/images.png "Описание небудет)")​

![alt tag](https://github.com/Nikita7131/lab2.2/blob/main/%D0%B1%D0%BB%D0%BE%D0%BA-%D1%81%D1%85%D0%B5%D0%BC%D0%B0.pdf "Описание небудет)")​


```ruby

#include <stdio.h>
#include <stdlib.h>
#include <math.h>
#include <Windows.h>


int main(){

  double Eqt(double x);

  double Left_Rect(double a,double b, int n);
  double Right_Rect(double a,double b, int n);
  double Trapeze(double a,double b, int n);
  double Parabola(double a,double b, int n);

  void Tabulation(double value);

  void GetDat();

  int A[20];
  int B[20];
  int N[20];

  int Metod_Used = 0;

  int Gaps = 1;

  double DeltaMath = 0;

  int StD_Math = 0;

  int StD_CNT = 0;


  printf("\n");
 switch(Metod_Used){
  case 5:
   case 1:
     printf("             Left_Rect          ");
     if(Metod_Used != 5){printf("Delta N            ");}
   if(Metod_Used == 1){break;}
   case 2:
     printf("Right_Rect         ");
     if(Metod_Used != 5){printf("Delta N            ");}
   if(Metod_Used == 2){break;}
   case 3:
     printf("Trapeze            ");
     if(Metod_Used != 5){printf("Delta N            ");}
   if(Metod_Used == 3){break;}
   case 4:
     printf("Parabola           ");
     if(Metod_Used != 5){printf("Delta N            ");}
   if(Metod_Used == 3){break;}
  break;
 }

for(int i = 0; i < Gaps; i++){
do{
 printf("\n#%d",i+1);
 Tabulation(i+1);
 StD_CNT += 2;
 switch(Metod_Used){
  case 5:
   case 1:
     printf("%f", Left_Rect(A[i],B[i],N[i]));
     Tabulation(Left_Rect(A[i],B[i],N[i]));
     if(Metod_Used != 5){
      DeltaMath = Left_Rect(A[i],B[i],N[i]) - Left_Rect(A[i],B[i],N[i] + StD_CNT);
      printf("%f", DeltaMath);Tabulation(DeltaMath);
     }
   if(Metod_Used == 1){break;}
   case 2:
     printf("%f", Right_Rect(A[i],B[i],N[i]));
     Tabulation(Right_Rect(A[i],B[i],N[i]));
     if(Metod_Used != 5){
       DeltaMath = Right_Rect(A[i],B[i],N[i]) - Right_Rect(A[i],B[i],N[i] + StD_CNT);
       printf("%f", DeltaMath);Tabulation(DeltaMath);
     }
   if(Metod_Used == 2){break;}
   case 3:
     printf("%f", Trapeze(A[i],B[i],N[i]));
     Tabulation(Trapeze(A[i],B[i],N[i]));
     if(Metod_Used != 5){
      DeltaMath = Trapeze(A[i],B[i],N[i]) - Trapeze(A[i],B[i],N[i] + StD_CNT);
      printf("%f", DeltaMath);Tabulation(DeltaMath);
      }
   if(Metod_Used == 3){break;}
   case 4:
     printf("%f", Parabola(A[i],B[i],N[i]));
     Tabulation(Parabola(A[i],B[i],N[i]));
     if(Metod_Used != 5){
       DeltaMath = Parabola(A[i],B[i],N[i]) - Parabola(A[i],B[i],N[i] + StD_CNT);
       printf("%f", DeltaMath);Tabulation(DeltaMath);
     }
   if(Metod_Used == 3){break;}
  break;
 }
}while(0.00001 <= DeltaMath && DeltaMath <= 0.001);
}
 printf("\n\n\n");
  return 0;
}
void GetDat(){

  SetConsoleOutputCP(1251);
  SetConsoleCP(1251);
  printf("\n Виберіть метод обчислення інтегралу:\n");
  printf("\n   1 - лівих квадратів");
  printf("\n   2 - правих квадратів");
  printf("\n   3 - трапецій");
  printf("\n   4 - парабол");
  printf("\n   5 - всі методи\n");
  while(Metod_Used == 0 || Metod_Used >= 6){
    printf("\n ВАША ВІДПОВІДЬ:");
    scanf("%d", &Metod_Used);
  }
  printf("\n Виберіть кількість проміжків: ");
  scanf("%d", &Gaps);
  if(Gaps == 0){Gaps = 1;}
  printf("\n");
 for(int i = 0; i < Gaps; i++){
  do{
   printf(" Проміжок #%d , введіть a, b, N : ",i+1);
   scanf("%d %d %d",&A[i], &B[i], &N[i]);
  }while(N[i] == 0);
 }
}
double Eqt(double x){ // рівняння
   double math_X = 0;
   math_X = (2*x+3);
   math_X *= x;
   math_X += 2;
  return 1.0/math_X;
}
double Left_Rect(double a,double b, int n){ // метод лівих квадратів
   double h = (b - a) / n;
   double sum = 0.0;
   for(int i = 0; i <= n - 1; i++){
    sum += h * Eqt(a + i * h);
   }
 return sum;
}
double Right_Rect(double a,double b, int n){ // метод правих квадратів
   double h = (b - a) / n;
   double sum = 0.0;
   for(int i = 1; i <= n; i++){
    sum += h * Eqt(a + i * h);
   }
 return sum;
}
double Trapeze(double a,double b, int n){  // метод трапецій
   double h = (b - a) / n;
   double sum = Eqt(a) + Eqt(b);
   for(int i = 1; i <= n - 1; i++){
    sum += 2 * Eqt(a + i * h);
   }
   sum *= h / 2;
 return sum;
}
double Parabola(double a, double b, int n){  // метод парабол
   double h = (b - a) / n;
   double sum = Eqt(a) + Eqt(b);
   int k;
   for(int i = 1; i <= n - 1; i++){
    k = 2 + 2 * (i % 2);
    sum += k * Eqt(a + i * h);
   }
   sum *= h / 3;
 return sum;
}
void Tabulation(double value){
 int i = 12 - (value / 10);
 while(i > 0){
   i --;
   printf(" ");
 }
}


```
