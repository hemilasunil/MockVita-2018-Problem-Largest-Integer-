# MockVita-2018-Problem-Largest-Integer-
The casino has introduced a new game in which there are M vertical chutes each containing N single digit (possibly zero) numbers. You can choose any chute and draw the bottom number and when you do this all the other numbers in the chute descend by one slot. You need to build the largest integer using this process drawing all the numbers from the chutes. For example, in the following example, we have three chutes of four numbers each and the largest number that can be drawn is 469534692781. Given the number of chutes and the numbers in each chute, write a program to find the largest integer that could be formed using the above process.


#include<stdio.h>
#define M 10
#define N 10
static int a[M][N],b[N][M];
int main()
{
int m,n,i,j,k,greater=0,l=0,w=0,flag=0,z=0;
scanf("%d,%d,",&m,&n);
z=n;
for(i=0;i<m;i++)
{
for(j=0;j<n;j++)
{
scanf("%d,",&a[i][j]);
}
}
for(i=0;i<m;i++)
{
for(j=0;j<n;j++)
{
b[j][i]=a[i][j];
}
}
while(l<(m*z))
{
//sorting
for(k=0;k<m;k++)
{
if(b[n-1][k]>greater)
{
greater=b[n-1][k];
w=k;
}
}
for(k=0;k<m;k++)
{
if(b[n-1][k]==b[n-1][k+1])
{
flag=1;
}
else
{
flag=0;
goto down;
}
}

if(flag)
{
n=n-1;
}

down: printf("%d",greater);

//shifting
for(i=0;i<n;i++)
{
b[n-i-1][w]=b[n-i-2][w];
}
l++;
greater=0;
}
printf("\n");
}
