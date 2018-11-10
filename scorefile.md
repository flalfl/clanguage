#pragma warning(disable:4996)
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
	
int main (void){
	FILE* fp1;
	inti=0;
	charinfor[50];

	printf("Name Midtermscore Finalscore(if you want to exit please write 'exit')\n");
	
	if ((fp1 = fopen("grade.txt", "w")) == NULL) {
		printf("Cannot open the file. ");
		exit(1);
	}

	while(1) {
		gets(infor);
		if(strcmp(infor,"exit")==0)
			break;
		fputs(infor,fp1);
	}fclose(fp1);
	
	if ((fp1 = fopen("grade.txt", "r")) == NULL) {
		printf("Cannot open the file. ");
		exit(1);
	}

	while(feof(fp1)==0){	
		fgets(infor,sizeof(infor),fp1);
		printf("%s",infor);
	}
	return 0;
	}

