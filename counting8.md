#pragma warning(disable:4996)
#include <stdio.h>

int main(void){
 int count=0;
 int i;

for(i=1;i<=10000;i++){
 if(i%10==8)
   count++;
   
 if(((i%1000)%100)/10==8)
   count++;
   
 if((i%1000)/100==8)
   count++;
   
  if(i/1000==8)
   count++;
 }
 
 printf("%d\n",count);
 return 0;
}
