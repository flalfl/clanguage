#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <stdlib.h>

int main(void){
 int S[10]={0};
 inti;
 intmin,temp,answer;

 printf("1차원들의 점 입력 : ");
  for(i=0;i<10;i++){
   scanf("%d",&S[i]);
 }
  min= (S[1]-S[0])*(S[1]-S[0]);
 for(i=0; i<10; i++){
 if(i==9)
   break;
 temp=(S[i+1]-S[i])*(S[i+1]-S[i]);
  if(min>=temp){
   min=temp;
  }
  answer=S[i+1]-S[i];
  if(answer<0)
   answer=-(S[i+1]-S[i]);
 }
 printf("결과값은 ");
 for(i=0; i<10; i++){
 if(i==9)
   break;
  if(min==(S[i+1]-S[i])*(S[i+1]-S[i])){
   printf("(%d, %d) ",(S[i]>S[i+1])?S[i+1]:S[i],(S[i]<S[i+1])?S[i+1]:S[i]);}
 }
 printf("이고 거리는 %d이다.\n",answer);
 return 0;
}
