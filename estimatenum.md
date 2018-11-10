#pragmawarning(disable:4996)
#include<stdio.h>
#include<stdlib.h>
#include<time.h>

int number;

int main (void){
	int num1=0,num2=0,num3=0;
	srand((unsigned)time(NULL));
	number = rand()%100+1;
  
	printf("There is a one randomnumber between 1 to 100.\nWrite the number -> ");
	scanf("%d",&num1);

	while(num1!=number){
	if(num1>number){
		printf("Smaller than this number. Try again ->");
		scanf("%d",&num1);
	}
	elseif(num1<number){
		printf("Bigger than this number. Try again ->");
		scanf("%d",&num1);
	}		
}
	printf("That's right. The answer was %d.",num1);
	return 0;
}
