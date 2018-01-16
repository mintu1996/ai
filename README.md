#include<stdio.h>
#include <stdlib.h>
bool match(int A[2][2],int B[2][2]){
	int i,j;
	int d=0;
	for(i=0;i<2;i++){
		for(j=0;j<2;j++){
			if(A[i][j]==B[i][j]){
				d++;
			}
		}
	}
	if(d!=4){
		return false;
	}
	return true;
}
void anticlock(int A[2][2]){
	int i,j,r,c;
	int tmp;
	for(i=0;i<2;i++){
		for(j=0;j<2;j++){
			if(A[i][j]==0){
				r=i;
				c=j;
			}
		}
	}
	if(r==1&&c==1){
		tmp=A[r-1][c];
		A[r-1][c]=A[r][c];
		A[r][c]=tmp;
		printf("BU->");
	}
  else	if(r==0&&c==1){
		tmp=A[r][c-1];
		A[r][c-1]=A[r][c];
		A[r][c]=tmp;
		printf("BL->");
	}
	else if(r==0&&c==0){
		tmp=A[r+1][c];
		A[r+1][c]=A[r][c];
		A[r][c]=tmp;
		printf("BD->");
	}
	else if(r==1&&c==0){
		tmp=A[r][c+1];
		A[r][c+1]=A[r][c];
		A[r][c]=tmp;
		printf("BR->");
	}	
}
void clock(int A[2][2]){
	int i,j,r,c;
	int tmp;
	for(i=0;i<2;i++){
		for(j=0;j<2;j++){
			if(A[i][j]==0){
				r=i;
				c=j;
			}
		}
	}
	if(r==1&&c==1){
		tmp=A[r][c-1];
		A[r][c-1]=A[r][c];
		A[r][c]=tmp;
		printf("BL->");
	}
	else if(r==0&&c==1){
		tmp=A[r+1][c];
		A[r+1][c]=A[r][c];
		A[r][c]=tmp;
		printf("BD->");
	}
	else if(r==0&&c==0){
		tmp=A[r][c+1];
		A[r][c+1]=A[r][c];
		A[r][c]=tmp;
		printf("BR->");
	}
	else if(r==1&&c==0){
		tmp=A[r-1][c];
		A[r-1][c]=A[r][c];
		A[r][c]=tmp;
		printf("BU->");
	}	
}
bool search(int A[2][2]){
	int i,j;
	int flag=0;
	for(i=0;i<2;i++){
		for(j=0;j<2;j++){
			if(A[i][j]==0){
				flag=1;
				break;
			}
		}
	}
	if(flag==1){
		return true;
	}
	return false;
}
void state(){
	int intput1[2][2],output[2][2];
	int i,j;
	int L[2];
	int intput2[2][2];
	printf("enter the input the state\n");
	for(i=0;i<2;i++){
		for(j=0;j<2;j++){
			scanf("%d",&intput1[i][j]);
		}
	}
	for(int h=0;h<2;h++){
		for(int s=0;s<2;s++){
			intput2[h][s]=intput1[h][s];
		}
	}
	printf("enter the output state \n");
	for(i=0;i<2;i++){
		for(j=0;j<2;j++){
			scanf("%d",&output[i][j]);
		} 
	}
	int f=0;
	int g=0;
	int t=0;
   
	if(search(intput1)){
		
	  p:anticlock(intput1);
	  if(g<20){
			g++;
	  if(match(intput1,output)){
			printf("  THIS IS ANTICLOCKWISE ANSWER\n");
		}
		else{
			goto p;
		}
	}
	
	
	else{
		system("cls");
		printf("\n anticlockwise solution not exist\n");
	}
	
	
	 q:clock(intput2);
	 if(t<20){
	   t++;
	 if(match(intput2,output)){
			printf("  THIS IS CLOCKWISE ANSWER\n");
		}
		else{
			goto q;
		}
	}
	else{
		printf("\n clockwise solution not exist\n");
	}
}
	else{
		printf("you not have entre the blank\n");
		state();
	}
}
int main(){
	state();
}
