//AKASH CHANDRAN
# sparse-addition-project-
#include<stdio.h>

#include<stdlib.h>

#define max 5

int main()

{
	
 int matrix[max][max];
 
 int spmatrix[max][3];
 
int matrix1[max][max];
 
   
int matrix2[max][max];
    
 int spmatrix1[max][3];
	
int amatrix[max][3];
	
 int i,j,k,row,r,c,col;
	
 printf("Enter the order of sparse matrix 1\n");
	
 scanf("%d%d",&row,&col);
	
 printf("Enter the element of the sparse matrix 1\n");
 
for(i=0;i<row;i++)
	for(j=0;j<col;j++)
		scanf("%d",&matrix[i][j]);
		
		printf(" Matrix 1\n");
		
 for(i=0;i<row;i++){
	for(j=0;j<col;j++){
		printf("%d\t",matrix[i][j]);  }
			printf("\n");
		}
		
k=1;
	for(i=0;i<row;i++)
	for(j=0;j<col;j++)
	if(matrix[i][j]!=0)
	{
		spmatrix[k][0]=i;
		spmatrix[k][1]=j;
		spmatrix[k][2]=matrix[i][j];
		k++;
	}
	spmatrix[0][0]=row;
	spmatrix[0][1]=col;
	spmatrix[0][2]=k-1;
	
printf("Enter the order of sparse matrix 2\n");
	scanf("%d%d",&r,&c);
	printf("Enter the element of the sparse matrix 2\n");
	for(i=0;i<r;i++)
	for(j=0;j<c;j++)
		scanf("%d",&matrix1[i][j]);
		
		printf(" Matrix 2\n");
		
 for(i=0;i<r;i++){
	for(j=0;j<c;j++){
		printf("%d\t",matrix1[i][j]);  }
			printf("\n");
		}
		
k=1;
	for(i=0;i<r;i++)
	for(j=0;j<c;j++)
	if(matrix1[i][j]!=0)
	{
		spmatrix1[k][0]=i;
		spmatrix1[k][1]=j;
		spmatrix1[k][2]=matrix1[i][j];
		k++;
	}
	spmatrix1[0][0]=r;
	spmatrix1[0][1]=c;
	spmatrix1[0][2]=k-1;
	
	

printf("ELEMENTS OF THE SPARSE MATRIX 1 \n");
	printf("row\tcolumn\tnon zero\n");
	for(i=0;i<=spmatrix[0][2];i++)
	{
		for(j=0;j<3;j++)
			printf("%d\t",spmatrix[i][j]);

		printf("\n");
	}
	
printf("ELEMENTS OF THE SPARSE MATRIX 2 \n");
	printf("row\tcolumn\tnon zero\n");
	for(i=0;i<=spmatrix1[0][2];i++)
	{
		for(j=0;j<3;j++)
			printf("%d\t",spmatrix1[i][j]);

	printf("\n");
}
i=1;
	j=1;
	k=1;
	if(spmatrix[0][0]==spmatrix1[0][0]&&spmatrix[0][1]==spmatrix1[0][1])
	{
	    while(i<r&&j<c)
	    {
	        if((spmatrix[i][0]==spmatrix1[j][0])&&(spmatrix[i][1]==spmatrix1[j][1])){
	            amatrix[k][0]=spmatrix[i][0];
	            amatrix[k][1]=spmatrix1[j][1];
	            amatrix[k][2]=spmatrix[i][2]+spmatrix1[j][2];
	            i++;
	            j++;
	            k++;
	            
	 }
else if(spmatrix[i][0]==spmatrix1[j][0]){
	            if(spmatrix[i][1]<spmatrix1[j][1]){
	                amatrix[k][0]=spmatrix[i][0];
	            amatrix[k][1]=spmatrix[i][1];
	            amatrix[k][2]=spmatrix[i][2];
	            i++;
	            k++;
	            }
	            else
	            
 {
	                amatrix[k][0]=spmatrix1[j][0];
	            amatrix[k][1]=spmatrix1[j][1];
	            amatrix[k][2]=spmatrix1[j][2];
	            j++;
	            k++;
	            }
	        }
	        else{
	            if(spmatrix[i][0]<spmatrix1[j][0]){
	                amatrix[k][0]=spmatrix[i][0];
	            amatrix[k][1]=spmatrix[i][1];
	            amatrix[k][2]=spmatrix[i][2];
	            i++;
	            k++;
	            }
	            else
	            
 {
	                amatrix[k][0]=spmatrix1[j][0];
	            amatrix[k][1]=spmatrix1[j][1];
	            amatrix[k][2]=spmatrix1[j][2];
	            j++;
	            k++;
	            }
	            
	        }
	    }
	    
 while(i<r){
	         amatrix[k][0]=spmatrix[i][0];
	            amatrix[k][1]=spmatrix[i][1];
	            amatrix[k][2]=spmatrix[i][2];
	            i++;
	            k++;
	    }
	    while(j<c){
	        amatrix[k][0]=spmatrix1[j][0];
	            amatrix[k][1]=spmatrix1[j][1];
	            amatrix[k][2]=spmatrix1[j][2];
	            j++;
	            k++;
	    }
	    amatrix[0][0]=spmatrix[0][0];
	            amatrix[0][1]=spmatrix[0][1];
	            amatrix[0][2]=k-1;
	    }
	else{
	    printf("\nMatrix are not suitable for addition\n");
	}
	
	printf("ELEMENTS OF THE SPARSE MATRIX 3 \n");
	printf("row\tcolumn\tnon zero\n");
	for(i=0;i<=amatrix[0][2];i++)
{
		for(j=0;j<3;j++)
			printf("%d\t",amatrix[i][j]);

  printf("\n");
}
	
for(i=0;i<r;i++)
	  for(j=0;j<c;j++)
	        matrix2[i][j]=matrix1[i][j]+matrix[i][j];
	        
printf(" Matrix sum\n");
		
 for(i=0;i<row;i++){
	for(j=0;j<col;j++){
		printf("%d\t",matrix2[i][j]);  }
			printf("\n");
		}
	        
	 
	
return 0;
}
