/*Center mock CSC P3 2025
Task 1
1.a)
given that A = 3, B = 5
temp=A//A=3
B=temp//B=3
A=B//A=3
Therefore no Swap 

1.b)
Temp=A//if A is 3 Then temp=3
B=temp//B=3
A=B//A=5 
conc. succesfull swap

1.c)
swaping A and B without the use of a third Variable Temp;
A=A+B => A= 3+5
B=A-B => B=  3+5-5...B=3
A=A-B => A=3-3-5...A=5
successfull Swap 
*/
// 2 Write procedure swapRows(MAT,a,b)
#include<stdio.h>
#include<string.h>
#define M 4
#define N 6
void SwapRows(int MAT[N][M],int a,int b)
{
	int temp;
	for (int i = 0; i <M; ++i)
	{
		temp=MAT[a][i];
		MAT[a][i]=MAT[b][i];
		MAT[b][i]=temp;
    }
}

/*
task 2 ....Data entering Subroutines
3.
*/

void ReadNames (char A[][20])
{
	for (int i = 0; i < N; ++i)
	{
		printf("Enter player %d Name\n",i+1 );
		scanf("%s",&A[i]);
	}
}


/*
4.)
*/
void ReadScores(int MAT[][M])
{
	for (int i = 0; i < N; ++i)
	{
		printf("Enter Score %d(4 rounds):\n" ,i+1); 
		for (int j = 0; j < M; ++j)
		{
			scanf("%d",&MAT[i][j]);
		}
	}
}


/*
5.)
*/
void TotalScore(int T[],int MAT[][M])
{
	for (int i = 0; i < N; ++i)
{
	T[i]=0;
	for (int j = 0; j < M; ++j)
	{
		T[i]+=MAT[i][j];
	}
}
}

/* Task 3....Data Display Subroutines
6.)
*/

void Display(char A[][20],int MAT[][M],int T[])
{
		printf("\nplayer\tround 1\tround 2\tround 3\tround 4 Totals \n:");
	for (int i = 0; i < N; ++i)
	{
		printf("%s\t",A[i] );
	
		for (int j= 0; j < M; ++j)
		{
			printf("%d\t",MAT[i][j] );
		}
		printf("%d\n",T[i]);
	}
}


void sorting(char A[][20],int MAT[][M],int T[])
{
	int i,j,max,temp;
	char aux[20];
	for (int i = 0; i < N-2; ++i)
	{
		max=i;
		for (j = i+1; j <N-1; ++j)
		{
			//Sort totals
			if (T[max]<T[j])
			{
				max=j;
			}

		}
		//sort all Data
		if (max!=i)
		{
			//swap Totals Score
			temp=T[i];
			T[i]=T[max];
			T[max]=temp;
			//Swap Rounds
			SwapRows(MAT,max,i);
			//swaping Players
			strcpy(aux,A[max]);
			strcpy(A[max],A[i]);
			strcpy(A[i],aux);
		}
	}
}


int main()
{
	char PLAYER[N][20];
	int ROUNDS[N][M];
	int TOTAL[N];

	//Read Data 
	 ReadNames (PLAYER);
	 ReadScores(ROUNDS);
	 TotalScore(TOTAL,ROUNDS); 
	 //Dislay Data
	 printf("\nUNSORTED LIST\n");
	 Display(PLAYER,ROUNDS,TOTAL);

	 //sorting
	sorting(PLAYER,ROUNDS,TOTAL);

	//Display Sorted data
	 printf("\nSORTED LIST\n");
	 Display(PLAYER,ROUNDS,TOTAL);


	 return 0;
}

