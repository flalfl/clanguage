#define _CRT_SECURE_NO_WARNINGS
#include<stdio.h>
#include<stdlib.h>
#include<string.h>

int main(void) {
	inti = 0, j = 0, k = 0, n = 0, blank = 0;     
	intkim = 0, lee = 0, LJY = 0;                 
	char name[200] = { '\0' };                
	char students[17][20] = { '\0' };           
	char *result = '\0';
	char temp[100];
	FILE* fp1;
	FILE* fp2;

	if ((fp1 = fopen("name.txt", "r")) == NULL) {
		printf("파일을열수없습니다. ");
		exit(1);
	}
	fscanf(fp1, "%s", &name);                
	fclose(fp1);

	printf("<txt파일의내용> ");
	printf("%s", name);
	puts("");

	result = strtok(name, ",");                  
	while (result != NULL) {
		strcpy(students[i], result);
		result = strtok(NULL, ",");
		i++;
	}

	for (i = 0; i<17; i++) {                  
		if (strncmp(students[i], "김", 2) == 0)
			kim++;
	}
	printf("김씨는 %d명입니다.\n", kim);

	for (j = 0; j<17; j++) {
		if (strncmp(students[j], "이", 2) == 0)
			lee++;
	}
	printf("이씨는 %d명입니다.\n", lee);


	for (n = 0; n<17; n++) {                
		if (strncmp(students[n], "이재영", 6) == 0)
			LJY++;
	}
	printf("'이재영'은 %d명입니다.\n", LJY);


	for (i = 0; i< 17; i++) {                 
		for (j = i + 1; j < 17; j++) {

			if (strcmp(students[i], students[j]) == 0) {
				*students[j] = '\0';
			}
		}
	}
	for (i = 0; i< 17; i++) {
		for (j = i + 1; j < 17; j++) {
			k = i;
			if (strcmp(students[k], students[j]) > 0) {
				k = j;
			}
			strcpy(temp, students[i]);
			strcpy(students[i], students[k]);
			strcpy(students[k], temp);
		}
	}

	printf("<오름차순으로정렬하고난뒤 txt파일의내용>\n");

	for (i = 0; i< 17; i++) {                  
		if (strcmp(students[i], "") == 0)
			blank++;
	}
	for (i = 0 + blank; i<17; i++) {                  
		printf("%s ", students[i]);
	}
  
	if ((fp2 = fopen("name_sort.txt", "w")) == NULL) {
		printf("파일을열수없습니다. ");
		exit(1);
	}
	for (i = 0 + blank; i< 17; i++) {
		fprintf(fp2, "%s ", students[i]);
	}
	return 0;
}
