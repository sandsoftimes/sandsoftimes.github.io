---
layout: post
title: Post-Fix Evaluation using Stack Data Structure in C++
date: 2020-06-23 20:52:55.000000000 +05:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Misc
tags: []
meta:
  _wpas_done_all: '1'
author:
  login: SandsOfTime
  email: janeebee1092@gmail.com
  display_name: SandsOfTime
  first_name: Muhammad
  last_name: Sharjeel Akhtar
permalink: "/2020/06/23/post-fix-evaluation-using-stack-in-c-plus-plus"
---
Just like the other data structures, **STACK** has multiple applications. Here is one of them for the evaluation of **post-fix** Expression. The code is mentioned in the separate portions for better understanding. Better is you put the complete code in a single file with a `cpp` extension and run it then. Here is the code, take a look at it,

Initial imports are,

```
#include<iostream>
using namespace std;
#define size 100
```

Create a user-defined class with the name of `Stack` will the data-members and member-functions in it,

```
class Stack{
    private:
    int top;
    int arr[size];
    public:
        Stack(){
            top=-1;
            int arr[size];
        }
        void push(int val){
            if(top>(size-1)){
                cout<<"Stack Overflow Occured";
            }
            else{
                top++;
                arr[top]=val;
            }
        }
        int pop(){
            int item;
            if(top<0){
                
                cout<<"Stack Overflowed Occur";
            }
            else{
                item=arr[top];
                top--;
                return item;
            }
        }
        int peek(){
            if(top<(size-1) && top>=0){
                int x=arr[top];
                return x;
            }
            else{
                cout<<"Stack is Empty";
            }
        }
        void EvaluatePostFix(char postfix[]){
            int i;
            char ch;
            int val;
            int A,B;
            for(int i=0;postfix[i]!=')';i++){
                ch=postfix[i];
                if(isdigit(ch)){
                    push(ch-'0');
                }
                else if(ch=='+'||ch=='-'||ch=='*'||ch=='/'){
                    A=pop();
                    B=pop();
                    switch(ch){
                        case '*':
                        val=B*A;
                        break;
                        case '-':
                        val=B-A;
                        break;
                        case '/':
                        val=B/A;
                        break;
                        case '+':
                        val=B+A;
                        break;
                    }
                    push(val);
                }
            }
            cout<<"The result of the expression is: "<<pop();
        }
        void isEmpty(){
            if(top==-1){
                cout<<"Stack is Empty ";
            }
        }
        void display(){
            if(top!=-1){
                for(int i=top;i>-1;i--){
                    cout<<arr[i]<<" ";
                }
            }
        }
};
```

Here is the `main` of program,

```
int main(){
    Stack s1;
    int i;
    char ch[size];
    cout<<"Enter the expression inside the character array: ";
    for(int i=0;i<=size;i++){
        cin>>ch[i];
        if(ch[i]==')'){
            break;
        }
    }
    s1.EvaluatePostFix(ch);
    return 0;
}
```