# count-easy-steps
이 수는 인접한 모든 자리의 차이가 1이다. 이런 수를 계단 수라고 한다. 0으로 시작하는 수는 계단수가 아니다.첫째 줄에 N이 주어지고 길이가 N인 계단 수가 총 몇 개 인지 프로그램을 작성해보자! 

dp알고리즘 

#c


#include <stdio.h>
#include <stdlib.h> 


void main(){
	int n,i,j,sum;
	int dp[101][11]; //dp[자릿수][앞에 오는 숫자]  
	scanf("%d",&n);
	for(i=1;i<=9;i++){ //입력받은 수가 1자리라면  
		dp[1][i]=1;}
	sum=0;
	for(i=2;i<=n;i++){ //입력받은 수가 2자리라면  
		dp[i][0]=dp[i-1][1]; //앞 자리수가 0이될수는 없고 10만가능  
		for(j=1;j<=9;j++){ //전의 자릿수와 같고 숫자는 앞뒤로 1만차이나도록  
			dp[i][j]=(dp[i-1][j-1]+dp[i-1][j+1])%1000000000;} }
	for(i=0;i<=9;i++){ //필요한 n자릿수의 합  
		sum+=dp[n][i];}
	printf("길이가 %d인 계단 수는:%d",n,sum%1000000000);  }
 
#python


import sys
input=sys.stdin.readline
n=int(input())
dp=[[0]*10 for _ in range(n+1)]
for i in range(1,10):
  dp[1][i]=1
maxnum=1000000000
for i in range(2,n+1):
  for j in range(10):
    if j==0:
      dp[i][j]=dp[i-1][1]
    elif j==9:
      dp[i][j]=dp[i-1][8]
    else:
      dp[i][j]=dp[i-1][j-1]+dp[i-1][j+1]
total=sum(dp[n])%maxnum
print(total)
