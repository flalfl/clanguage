#pragma warning(disable:4996)
#include <stdio.h>
#include <stdlib.h>

int main(void){
  int i,j,year, month,day,move;
  int sum_year=0,sum_month=0,total_sum=0;
  int leapyear[12]={31,29,31,30,31,30,31,31,30,31,30,31};
  int nonleapyear[12]={31,28,31,30,31,30,31,31,30,31,30,31};
  int k,l,a,kk;
  int total1,total2,total3,year_sum=0,sum2=0;
  int remain=0,remain2=0,remain3;
  inti_sum=0,i_sum2=0;
  
  printf("Current Date :");
  scanf("%d %d %d",&year,&month,&day); 
  puts("");
  
  if(year<=0){
   exit(1);
   }
  
  if(month<1 || month>12)
   exit(1);
  
  if(day<1 || day>31){
   exit(1);
   }
  
  printf("Wanted number of dates moved forward : ");
  scanf("%d",&move);
  puts("");
  
  for(i=1; i<year; i++)
  {
   if((i%4==0&&i%100!=0)||i%400==0)
   sum_year+=366;
   else sum_year+=365;
  }
   
  total_sum+=sum_year;
   
  for(j=0; j<month-1;j++)
  {
   if((i%4==0&&i%100!=0)||i%400==0)
    sum_month+=leapyear[j];
    
   else
   sum_month+=nonleapyear[j];
  }
  
  total_sum+=sum_month;
  total_sum+=day;
  total1=total_sum+move;
  
  for(i=1;year_sum<total1;i++){
   if((i%4==0&&i%100!=0)||i%400==0)
   year_sum+=366;

  else 
  year_sum+=365;
  remain++;
  }
  
  printf("Year : %d ",remain);
  
  for(i=1;i<remain;i++){
  if((i%4==0&&i%100!=0)||i%400==0)
   i_sum+=366;
  
  else 
   i_sum+=365;
  }
  
  total2=total1-i_sum; 
  
  for(j=0;sum2<total2;j++){
  if((remain%4==0&&remain%100!=0)||remain%400==0)
   sum2+=leapyear[j];
  
  else
   sum2+=nonleapyear[j];
  remain2++;
  }
  
  printf("Month : %d ",remain2);
  
  for(j=0;j<remain2-1;j++){
  if((remain%4==0&&remain%100!=0)||remain%400==0)
   i_sum2+=leapyear[j];
  
  else
   i_sum2+=nonleapyear[j];
  }
  
  total3=total2-i_sum2;
  printf("Day : %d",total3);
  return 0;
}  
