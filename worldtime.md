#include <stdio.h>
#include <string.h>

int Casecheck(char input[]);

int main(void) {
 char input[13];
 char output[13];
 int inputday;
 char inputtimer[7];
 int time,minute;
 int gmt[8] = {9,0,8,3,4,1,-8,-5};
 int inputcase;
 int outputcase;
 
 gets(input);
 scanf("%d",&inputday);
 getchar();
 gets(inputtimer);
 
 time = (inputtimer[0]-'0') * 10 + inputtimer[1] - '0';
 minute = (inputtimer[2]-'0') * 10 + inputtimer[3] - '0';
 
 if (inputtimer[4]=='p')
  time += 12;
 printf("%s 시각 : %d %s\n",input,inputday,inputtimer);
 gets(output);
 
 inputcase = Casecheck(input);
 outputcase = Casecheck(output);
 
 time += gmt[outputcase]-gmt[inputcase];
 
 if (time >= 24) {
  inputday++;
  time -=24;
 }
 
 if (time < 0) {
  inputday--;
  time += 24;
 }
 
 if (time>=12) {
 printf("%s 시각 : %d %d%dpm\n",output,inputday,time-12,minute);
 }
 
 else if(time<10){
  printf("%s 시각 : %d 0%d%dam\n",output,inputday,time,minute);
 }
 
 else {
  printf("%s 시각 : %d %d%dam\n",output,inputday,time,minute);
 }
}

int Casecheck(char input[]) {
 int Casenum=8;

  if (strcmp(input,"서울")==0) {
   Casenum=0;
}

  else if (strcmp(input,"영국")==0) {
   Casenum=1;
 }

  else if (strcmp(input,"베이징")==0) {
   Casenum=2;
 }

  else if (strcmp(input,"모스크바")==0) {
   Casenum=3;
 }
  
  else if (strcmp(input,"두바이")==0) {
   Casenum=4;
 }
 
  else if (strcmp(input,"시드니")==0) {
   Casenum=5;
 }
 
  else if (strcmp(input,"LA")==0) {
   Casenum=6;
 }
 
  else if (strcmp(input,"NY")==0) {
   Casenum=7;
 }
 
 return Casenum;
} 
