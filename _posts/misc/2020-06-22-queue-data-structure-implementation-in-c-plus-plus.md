---
layout: post
title: Queue Data Structure Rules and Implementation in C++
date: 2020-06-22 20:52:55.000000000 +05:00
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
permalink: "/2020/06/22/queue-data-structure-implementation-in-c-plus-plus"
---
Queue is also one of the famous data structure. Although it is pretty similar to stack but it has its own applications. You might know the working law of Queue **"THE-FIFO-Principal"**. Here i've defined some rules of queue alongside with its implementaion in `c++`/

## Rules:

The queue follow the basic rule of, 

* First In First Out.
* Two pointers will be used in queue.
* One will be used for insertion and the second one will be used in deletion.
* Insertion in queue in known as Enqueue.
* Deletion in queue is known as Dequeue.
* Insertion in queue is done through rear pointer.
* Deletion through queue is done through front pointer.
* Queue can be implemented by two ways.
* First by: Array data structure
* Second by: Linked List data structure.

## Implementation:

Below is the provided code of Linked List Implementation of queue.I have covered the 4 basic functions of the queue in ths implementation.

* Enqueue(): Insertion in queue.
* Dequeue(): Deletion in queue.
* isFull(): Checking whether the queue is Full or not.
* isEmpty(): Checking whether the queue is Empty or not.

## Code In C++:

Here are the initial imports,

```
#include<iostream>
using namespace std;
```

Then define a node class for a basic node objects,

```
class Node{
    public:
    int data;
    Node*next;
    Node(int data){
        this->data=data;
        next=NULL;
    }
};
```

Now we've the queue class,

```
class Queued{
    private:
    Node*front,*rear;
    int length;
    public:
    Queued(){
        front=rear=NULL;
        length=0;
    }
    void Enqueue(int valve){
        Node*n=new Node(valve);
        if(front==NULL){
            cout<<"Queue is Empty right now, u can insert elements: "<<endl;
            front=rear=n;
        }
        else{
            rear->next=n;
            rear=n;
        }
    }
    int Dequeue(){
        if(front!=NULL){
        Node*t=front;
        front=front->next;
        cout<<"The value stored in the Node was: ";
        if(t->data!=0){
        return t->data;}
        }
    }
    bool isEmpty(){
        if(front==NULL){
            return true;
        }
    }
    bool isFull(){
        if(front==rear){
            return true;
        }
    }
};
```

At the end we've the objects and function calls in the `main` of function,

```
int main(){
    Queued obj1;
    obj1.Enqueue(25);
    obj1.Enqueue(28);
    obj1.Enqueue(28);
    obj1.Enqueue(25);
    cout<<obj1.Dequeue()<<endl;
    cout<<obj1.Dequeue()<<endl;
    cout<<obj1.Dequeue()<<endl;
    cout<<obj1.Dequeue()<<endl;
    if(obj1.isEmpty()){
        cout<<"The Queue is Empty: ";
    }
    cout<<"\n";
    /*
    if(obj1.isFull()){
        cout<<"The Queue is Full: ";
    }
    */
}
```

Before running, do remember to keep the complete code in a single file with a `cpp` extension.