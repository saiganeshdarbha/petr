# petr
#include<cstdio>
#include<cstring>
#include<string.h>
#include<algorithm>
#include<iostream>
#include<stdlib.h>
using namespace std;
const int inf=0x3f3f3f3f;
const int maxn=1000000; 
int a[maxn];
int main(){ 
    int n;
    cin>>n; 
    for(int i=0;i<n;i++){
        cin>>a[i];
    }
    int flag=0;
    int ans=0;
    For(int i=0;i<1<<n;i++){//shares 1<<n states enumerates each state 
        ans=0;
                 For(int j=0;j<n;j++){//Enumerate each bit of each state, such as 1111 
                         If(i&(1<<j)){//here is 1 and add (clockwise) 
                ans+=a[j];
                ans=ans%360;
                         }else{ // 0 wants to reduce (counterclockwise) 
                ans-=a[j];
                ans=ans%360;
            }
        }
                 If(ans==0){//that is a turn 
            flag=1;
            break;
        }
    }
    if(flag){
        cout<<"YES";
    }else{
        printf("NO");
    }
    return 0;
}
