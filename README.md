# Mini-Project
Write an efficient code to find nth Fibonacci number. The range of n can be 0-20,000
#include <stdio.h>
#define N 20000

char a[N], b[N], c[N], carry=0;
int i;
int k=N-1;
void fibb(int n){
    if(n==0){
        printf("%d", 0);
        return;
    }
    else if(n==1){
        printf("%d", 1);
        return;
    }
    a[N-1]=1;
    b[N-1]=0;
    for(int i=2; i<=n; i++){
        for(int i=N-1; i>=k; i--){
            int a1 = a[i]+b[i]+carry;
            c[i]=(a1%10);
            carry=a1/10;
            if(i==k && carry>0) k--;
        }
        for(int i=N-1; i>=k; i--){
            b[i]=a[i];
            a[i]=c[i];   
        }
    }
    for(int i=k; i<N; i++)
    
        printf("%d", c[i]);
    printf("\n");
}

int main()
{
    int n;
    scanf("%d", &n);
    printf("fibanoci series of %d is :",n);
    fibb(n);
    return 0;
}
