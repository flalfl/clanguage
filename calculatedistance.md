#include <stdio.h>
int main (void){
 int S[7]={1,3,4,8,13,17,20};
 inttemp,i,j,min = S[1]-S[0],index;
 
 for(i=0;i<7;i++){
  if(i==6)
   break;
   
  temp = S[i+1]-S[i];
  
  if(min>temp){
   min=temp;
   index=i;
  }
 }
 printf("Result : (%d, %d)",S[index],S[index+1]);
 
 return 0;
}
