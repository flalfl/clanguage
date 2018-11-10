#include <stdio.h>
#include <time.h>
#include <stdlib.h>
#include <Windows.h>
#define SIZE 7
 
enum pattern {spade, heart, clover, diamond};
char cardnumber[13] = {'A','2','3','4','5','6','7','8','9','T','J','Q','K'};
 
struct player {
	int card[7];
};
 
int printcard(int deck[]);
 
int main() {
	srand((unsigned)time(NULL));
	struct player player1;
	struct player player2;
	int i,j,end=0;
 
	while(end==0) {
	for (i=0;i<SIZE;i++) {
		player1.card[i] = rand()%52;
		for (j=0;j<i;j++) {
			if (player1.card[i] == player1.card[j])
				i--;
		}
	}
  
	for (i=0;i<SIZE;i++) {
		player2.card[i] = rand()%52;
		for (j=0;j<i;j++) {
			if (player2.card[i] == player2.card[j]) {
				i--;
				break;
			}
		}
    
		for (j=0;j<SIZE;j++) {
			if (player2.card[i] == player1.card[j]) {
				i--;
				break;
			}
		}
	}
	
  end += printcard(player1.card);
	end += printcard(player2.card);
  
	if (end==0) {
	Sleep(1000);
	system("cls");
	}
	}
}
 
int printcard(int deck[]) {
	int i,j,pattern,num;
	int he=0,di=0,cl=0,sp=0;
 
	for (i=0;i<SIZE;i++) {
		pattern = deck[i]/13;
		num = deck[i]%13;
		switch(pattern) {
		case spade:
			printf("♠%c ",cardnumber[num]);
			sp++;
			break;
		case heart:
			printf("♥%c ",cardnumber[num]);
			he++;
			break;
		case clover:
			printf("♣%c ",cardnumber[num]);
			cl++;
			break;
		case diamond:
			printf("◆%c ",cardnumber[num]);
			di++;
			break;
		}
	}
	if (he>4) {
		printf("Heart Flush\n");
		return 1;
	}
	else if (sp>4) {
		printf("Spade Flush\n");
		return 1;
	}
	else if (cl>4) {
		printf("Clover Flush\n");
		return 1;
	}
	else if (di>4) {
		printf("Diamond Flush\n");
		return 1;
	}
	else {
		printf("        %d %d %d %d\n",sp,he,cl,di);
		return 0;
	}
} 
