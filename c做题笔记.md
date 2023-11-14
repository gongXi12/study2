# 1.sqrt

返回值为double或者float，要类型转换。

## 2.函数递归

```c
void print(int num)

{

 if (num > 9)

  print(num / 10);

 printf("%d,", num % 10); 

}
```

正序输出一个数的每个数字

## 3.翻译日期

```c
#include <stdio.h>
#include <string.h>
int compare(char *a, char **b);
char *b[7] = {"Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "sUnday"};
int main(int argc, char const *argv[])
{
  char a[20];
  scanf("%s", a);
  switch (compare(a, b))
  {
  case 1:
    printf("星期一");
    break;
  case 2:
    printf("星期二");
    break;
  case 3:
  	printf("星期三");
	break;
  case 4:
​    printf("星期四");
​    break;
  case 5:
​    printf("星期五");
​    break;
  case 6:
​    printf("星期六");
​    break;
  case 7:
​    printf("星期日");
​    break;
  default:
​    printf("星期0");
​    break;
  }
}
int compare(char *a, char **b)
{
  for (int i = 0; i < 7; i++)
  {
  if (!strcmp(a, b[i]))
      return (i + 1);
  }
  return -1;
}
```

## 4.连接字符串 不用库函数

```c
#include<stdio.h>

int main()

{

 char a[20],b[20];

 int i,j;

 scanf("%s",a);

 scanf("%s",b);

 while(a[i])

 {

  i++;

  } 

  for(j=0;j<10&&b[j]!='\0';j++)

  {

  a[i++]=b[j];

  }

 printf("%s",a);

 return 0;

}
```

## 5.矩阵逆置

```c
#include <stdio.h>
int main() 
{    
    int matrix[4][3], transpose[3][4];    
    int i, j;        
    printf("Enter the elements of the matrix:\n");    
    for (i = 0; i < 4; i++) 
    {        
        for (j = 0; j < 3; j++) 
        {            
            scanf("%d", &matrix[i][j]);       
        }    
    }
    
    for (i = 0; i < 3; i++) 
    {        
        for (j = 0; j < 4; j++) 
        {            
            transpose[i][j] = matrix[j][i];        
        }    
    }
    
    printf("Transpose of the matrix:\n");    
    for (i = 0; i < 3; i++) 
    {        
        for (j = 0; j < 4; j++) 
        {            
            printf("%d ", transpose[i][j]);        
        }        
        printf("\n");    
    }    
    return 0;
}
```

## 6.小数

想要计算结果的小数

例如 **avg=(a+b)/2**

错误，应该是

**avg=(a+b)/2.0**

## 7.选择排序

```c
#include <stdio.h>
void main()
{ 
    void  sort(int array[], int n);
    int a[10],i;
    printf("enter the array:\n");
    for(i=0;i<10;i++)
        scanf("%d",&a[i]);
    sort(a,10);
    printf("the sorted array:\n");
    for(i=0;i<10;i++)
        printf("%d",a[i]);
    printf("\n");

}
void  sort(int array[], int n)
{ 
    int i,j,k,t;
    for(i=0;i<n-1;i++)
    {
        k=i;

        for(j=i+1;j<n;j++)
            if(array[j]<array[k])
            	k=j;
           		t=array[k];
            	array[k]=array[i];
            	array[i]=t;
    }

}
```

## 8.十个字符串排序

```c
#include  "stdio.h"
#include  "string.h"
int main() {
	void sort(char (*p)[6]);
	int i;
	char str[10][6]={"abc","edf","ghi","jkl","mno","pqr","stu","vwx","yz1","234"};
	char (*p)[6];
	p=str;
	sort(p);
	for (i=0; i <10; i++)
		printf("%s ",str[i]);
	return 0;
}

void sort(char (*s)[6]) {
	int i,j;
	char temp[6],*t=temp;
	for (i=0; i <9; i++)
		for (j=0; j <9-i; j++)
			if (strcmp(s[j],s[j+1])>0) {
				strcpy(t,s[j]);
				strcpy(s[j],s[+j+1]);
				strcpy(s[j+1],t);
			}
}
```