# clanguage
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <string.h>

int leap(int y);                           
int TotalDates(int y);                     
int getDay(int y);                         
int MaxdayMonth(int y);                    
int print(int y);                          
int savefile(int y);                       
int year, date;                            
int ycount = 0;
int month[12];

int main(void)
{
   printf("Write the number of year. <Format >> 2016>\n");
   scanf("%d", &year);

   leap(year);

   return 0;
}

int leap(int y)
{
   int i;
   if ((y % 400 == 0) || (y % 4 == 0) && (y % 100 != 0))
      printf("This is leap year.\n");
   else
      printf("This isn't leap year.\n");

   for (i = 1; i < y; i++)                          
   {
      if ((i % 400 == 0) || (i % 4 == 0) && (i % 100 != 0))
         ycount = ycount + 1;
      else
         ycount = ycount;
   }

   printf("Number of leap years : %d\n", ycount);

   return TotalDates(y);
}

int TotalDates(int y)
{
   date = (365 * (y - 1)) + ycount;                  
   printf("Total number of dates from B.C to last year : %d\n", date);
   return MaxdayMonth(y);
}

int MaxdayMonth(int y)
{
   int i;
   for (i = 1; i < y; i++)
   {
      if ((i % 400 == 0) || (i % 4 == 0) && (i % 100 != 0))
         month[1] = 29;  
      else
         month[1] = 28;   
   }

   month[0] = 31;
   month[2] = 31;
   month[3] = 30;
   month[4] = 31;
   month[5] = 30;
   month[6] = 31;
   month[7] = 31;
   month[8] = 30;
   month[9] = 31;
   month[10] = 30;
   month[11] = 31;

   return getDay(y);
}

int getDay(int y)
{
   int a;
   a = (date + 1) % 7;

   switch (a)
   {
   case 1:
      printf("1st January, %d is Monday.\n", y);
      break;
   case 2:
      printf("1st January, %d is Tuesday.\n", y);
      break;
   case 3:
      printf("1st January, %d is Wednesday.\n", y);
      break;
   case 4:
      printf("1st January, %d is Thursday.\n", y);
      break;
   case 5:
      printf("1st January, %d is Friday.\n", y);
      break;
   case 6:
      printf("1st January, %d is Saturday.\n", y);
      break;
   case 0:
      printf("1st January, %d is Sunday.\n", y);
      break;
   }

   printf("\n");

   return print(y);
}

int print(int y) 
{
   int i, j, k, day_remainer, day;              
   int day_sum = 0;                           
   int leapyear_day[12] = { 31,29,31,30,31,30,31,31,30,31,30,31 };
   int nonleapyear_day[12] = { 31,28,31,30,31,30,31,31,30,31,30,31 };

   for (i = 1; i < y; i++)                    
   {                     
      if ((i % 4 == 0 && i % 100 != 0) || (i % 400 == 0))
         day_sum += 366;
      else
         day_sum += 365;
   }

   day_remainer = day_sum % 7;                    
   if ((i % 4 == 0 && i % 100 != 0) || (i % 400 == 0))
   {
      for (j = 0; j < 12; j++)
      {
         printf("    [%d(Year) %d(Month)]\n", y, j + 1);
         printf("Sun Mon Tue Wed Thr Fri Sat\n");

         for (k = 0; k <= day_remainer; k++)        
		 printf("   ");

         for (day = 0; day < leapyear_day[j]; day++) 
         {
            day_remainer++;

            if (day_remainer == 7)             
			{
               printf("\n");
               day_remainer = 0;
            }

            printf("%3d", day + 1);
         }

         printf("\n\n");
      }
   }

   else                                   
      for (j = 0; j < 12; j++) 
      {
         for (j = 0; j < 12; j++) 
         {
            printf("    [%d(Year) %d(Month)]\n", y, j + 1);
            printf(" Sun Mon Tue Wed Thr Fri Sat\n");
            for (k = 0; k <= day_remainer; k++)
               printf("   ");
            for (day = 0; day < nonleapyear_day[j]; day++) 
            {
               day_remainer++;

               if (day_remainer == 7) 
               {
                  printf("\n");
                  day_remainer = 0;
               }

               printf("%3d", day + 1);
            }

            printf("\n\n");
         }
      }

   return savefile(y);
}

int savefile(int y)
{
   int i, j, k, day_remainer, day;               
   int day_sum = 0;                        
   int leapyear_day[12] = { 31,29,31,30,31,30,31,31,30,31,30,31 };
   int nonleapyear_day[12] = { 31,28,31,30,31,30,31,31,30,31,30,31 };
   char text_name[99];                       

   FILE *f;

   printf("Write file name where calender will be saved. <Format >> 2017.cal>\n");
   scanf("%s", text_name);

   strcat(text_name, ".txt");

   f = fopen(text_name, "wt");

   for (i = 1; i < y; i++)                     
   {
      if ((i % 4 == 0 && i % 100 != 0) || (i % 400 == 0))
         day_sum += 366;
      else
         day_sum += 365;
   }

   day_remainer = day_sum % 7;                     
                                          
   if ((i % 4 == 0 && i % 100 != 0) || (i % 400 == 0))
   {
      for (j = 0; j < 12; j++)
      {
         fprintf(f, "    [%d(Year) %d(Month)]\n", y, j + 1);
         fprintf(f, " Sun Mon Tue Wed Thr Fri Sat\n");

         for (k = 0; k <= day_remainer; k++)         
            fprintf(f, "   ");

         for (day = 0; day < leapyear_day[j]; day++)
         {
            day_remainer++;

            if (day_remainer == 7)               
            {
               fprintf(f, "\n");
               day_remainer = 0;
            }

            fprintf(f, "%3d", day + 1);
         }

         fprintf(f, "\n\n");
      }
   }

   else                                    
      for (j = 0; j < 12; j++)
      {
         for (j = 0; j < 12; j++)
         {
            fprintf(f, "    [%d(Year) %d(Month)]\n", y, j + 1);
            fprintf(f, " Sun Mon Tue Wed Thr Fri Sat\n");
            for (k = 0; k <= day_remainer; k++)
               fprintf(f, "   ");
            for (day = 0; day < nonleapyear_day[j]; day++)
            {
               day_remainer++;

               if (day_remainer == 7)
               {
                  fprintf(f, "\n");
                  day_remainer = 0;
               }

               fprintf(f, "%3d", day + 1);
            }

            fprintf(f, "\n\n");
         }
      }

   fclose(f);

   return 0;
}
