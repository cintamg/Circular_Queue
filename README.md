# Circular_Queue
Tis is to implement circular queue.
#include<stdio.h>
#define MAX 5
int enqueue(int x);
int dequeue();
void display();
int front=-1,rear=-1;
int cqueue[MAX];
void main()
{
    int ele,ch=0,res;
    while(ch!=4)
    {
    printf("1.Insert\n2.Delete\n3.Display\n4.Exit\n");
    printf("Enter your choice\n");
    scanf("%d",&ch);
    switch(ch)
    {
    case 1:
        printf("Enter the element you want to insert\n");
        scanf("%d",&ele);
        res=enqueue(ele);
        if(res==-1)
            printf("Overflow\n");
        else
        {
            printf("%d inserted successfully\n",ele);
            printf("Front = %d , Rear = %d\n",front,rear);
        }
        break;
    case 2:
        res=dequeue();
        if(res==-1)
            printf("Underflow\n");
        else
        {
            printf("%d deleted successfully\n",res);
            printf("Front = %d , Rear = %d\n",front,rear);
        }
        break;
    case 3:
        display();
        break;
    case 4:
        printf("Exiting....");
        break;
    default:
        printf("Invalid choice\n");
        break;
    }
}
}
int enqueue(int x)
{
    if(front==-1)
    {
        front=rear=0;
        cqueue[0]=x;
    }
    else if(front==(rear+1)%MAX)
        return -1;
    else
    {
        rear=(rear+1)%MAX;
        cqueue[rear]=x;
    }
}
int dequeue()
{
    if(front==-1)
        return -1;
    int copy=cqueue[front];
    if(front==rear)
        front=rear=-1;
    else
        front=(front+1)%MAX;
    return copy;
}
void display()
{
    int i;
    if(front==-1)
        printf("Queue is empty\n");
    else
    {
        printf("\nQUEUE\t: ");
        if(rear>=front)
        {
            for(i=front;i<=rear;i++)
            printf("%d ",cqueue[i]);
        }
        else
        {
            for(i=front;i<MAX;i++)
                printf("%d ",cqueue[i]);
            for(i=0;i<=rear;i++)
                printf("%d ",cqueue[i]);
        }
        printf("/n");
    }
}
