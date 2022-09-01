#include <stdio.h>
#include <stdlib.h>
enum Que {INSERT_F = 1,DELETE_F,INSERT_M,DELETE_M,INSERT_R,DELETE_R,REVERSE,CIRCUL,DISPLAY,EXIT};
struct node
{
	int data;
	struct node* link; 
};
struct node* head = NULL;
void insert_f (int item)
{
	struct node* temp = (struct node*) malloc (sizeof(struct node));
	if (temp !=NULL)
	{
		temp -> data = item;
		temp -> link = head;
		head = temp;
	}
	else
	{
		printf("\nheap memory full ");
	}

}
void del_f ()
{
   if (head==NULL)
   {
      printf("\nmemory is empty");
   }
   else
   {
	struct node* temp = head;
	head = temp -> link ;
	free (temp);
	temp = NULL; 
   }
}
void insert_m (int item,int position)
{
   int count = 1;
   if (head==NULL)
   {
      printf("\nmemory is empty");
   }
   else
   {
	   struct node* ptr = head;
	   struct node* temp = (struct node*)malloc (sizeof (struct node));
	      if (temp != NULL)
            {
		         while (count < position - 1)
		            {
			            ptr = ptr ->link;
			            count++;
		            }
		            temp -> data = item ;
		            temp -> link = ptr -> link ;
		            ptr  -> link = temp ;
         	}
	      else
	         {
		         printf("\nheap memory full ");
	         }
   	
   }
}
void del_m (int position)
{
   int count = 1;
  	struct node* ptr = head;
	struct node* pre = NULL;
   if (ptr == NULL)
   {
      printf("\nmemory is empty");
   }
   else
   {
	
	while (count < position)
	{
		pre = ptr;
		ptr = ptr -> link;
		count ++;
	}
	pre -> link = ptr -> link ;
	free (ptr);
	ptr = NULL; 
   }
}

void insert_r (int item)
{
   if (head == NULL)
   {
      printf("\nhead is empty");
   }
   else
   {
	   struct node* ptr = head;
	   struct node* temp = (struct node*)malloc (sizeof (struct node));
	      if (temp != NULL)
            {
		         while (ptr != NULL)
		            {
			            ptr = ptr ->link;
		            }
		            temp -> data = item ;
		            temp -> link = NULL ;
		            ptr  -> link = temp ;
         	}
	      else
	         {
		         printf("\nheap memory full ");
	         }
   }	
   
}
void del_r ()
{
  	struct node* ptr = head;
	struct node* pre = NULL;
   if (ptr == NULL)
   {
      printf("\nmemory is empty");
   }
   else
   {
      
	   while (ptr ->link != NULL)
	   {
		   pre = ptr;
		   ptr = ptr -> link;
	   }
	   pre -> link = ptr -> link ;
	   free (ptr);
	   ptr = NULL; 
   }
}
void reverse ()
{
   if (head == NULL)
   {
      printf("memory is empty");
   }
   else 
   {
   struct node* pre, *current;
   pre = head;
   current = head -> link;
   head = head -> link;
   pre -> link = NULL;
   while (head != NULL)
   {
      head = head -> link;
      current -> link = pre;
      pre = current;
      current = head;
   }
   head = pre;
   printf("\n successfully linked list is reversed\n");
   }
}
void circul ()
{
  	struct node* ptr = head;
   if (ptr == NULL)
   {
      printf("\nmemory is empty");
   }
   else
   {
	   while (ptr ->link != NULL)
	   {   
		   ptr = ptr -> link;
	   }
	   ptr -> link =head;
	   
   }
}
void display ()
{
   if (head==NULL)
   {
      printf("\nmemory is empty");
   }
   else
   {
      
	struct node* temp = head ;
	printf("\nelements are :\n ");
	while (temp != NULL)
	{
		printf("\n%d",temp -> data);
		temp = temp -> link;
	}
   }
	
}
int main ()
{
   while (1)
   {
	int choose;
	printf("\n\t choose any one : \n\t 1 - INSERT_F \n\t 2 - DELETE_F\n\t 3 - INSERT_M\n\t 4 - DELETE_M\n\t 5 - INSERT_R\n\t 6 - DELETE_R\n\t 7 - REVERSE \n\t 8 - CIRCUL\n\t 9 - DISPLAY\n\t 10 - EXIT\n");
	scanf("%d",&choose);
	switch (choose)
	{
	case INSERT_F :
		{
			int item ;
			printf("\n\tenter the item :");
			scanf("%d",&item);
			insert_f(item);
		}
	break;
	case DELETE_F :
		{
			del_f();
		}
	break;
	case INSERT_M :
		{
			int item, pos ;
			printf("\n\tenter the item : \n");
			scanf("%d",&item);
			printf("\n\tenter the position : \n");
			scanf("%d",&pos);
			insert_m(item,pos);
		}
	break;
	case DELETE_M :
		{
		   int pos ;
		   printf ("enter the position to do delition in middle : \n");
		   scanf("%d",&pos);
			del_m(pos);
		}
	break;
	case INSERT_R :
		{
			int item ;
			printf("\n\tenter the item :");
			scanf("%d",&item);
			insert_r(item);
		}
	break;
	case DELETE_R :
		{
			del_r();
		}
	break;
	case CIRCUL :
		{
			circul();
		}
	break;
	case DISPLAY :
		{
			display();
		}
	break;
	case REVERSE :
		{
			reverse();
		}
	break;
        case EXIT :
         	{
			exit (0);
         	}
	break;
        default :
         	{
            		printf("\n\t invalid input");
         	}
	   }
   }
	return 0;
}









