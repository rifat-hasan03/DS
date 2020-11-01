# DS

#include<stdio.h>
#include<string.h>
#include<windows.h>
#include<stdlib.h>
#include<conio.h>

//struct Node

struct Node{
    char foodname[30];
    int data,stock;
    float price;
    struct Node *next;
};

typedef struct Node node;


//Global Type veriable 
node *head, *menu;

int credit_card[20];
float total_poisa[20];
char problem_box[20];

//Function for print any word
void print(char list[]){
    printf("%s",list);
}

//Function for print a new line
void line (int cnt){
    int i;
    for(i=1;i<=cnt;i++);
    printf("\n");
}


//Function for print a new tab
void tab(int cnt){
    int i;
    for(i=1;i<=cnt;i++);
    printf("\t");
}

//Function for main menu

fooodlist(){
    line(10); tab(20); print("1.   \"* Food Menu                              |\"");line(2);sleep(350);system("color 4F");
     line(10); tab(20); print("2.   \"* Admin Log In                          |\"");line(2);sleep(350);
      line(10); tab(20); print("3.   \"* Rules &reg                           |\"");line(2);sleep(350);
       line(10); tab(20); print("4.   \"* Problem & suggestion                |\"");line(2);sleep(350);
        line(10); tab(20); print("5.   \"* Exit                               |\"");line(2);sleep(350);
}


//Function for insert food list
void insertfood(char foodname[30],int data, int stock, float price){
    node *temp;
    temp=(node*)malloc(sizeof(node));
    temp->data=data;
    temp->stock=stock;
    temp->price=price;
    strcpy(temp->foodname,foodname);
    temp->next=NULL;
    
    if(head==NULL){
        head=temp;
        menu=head;
    }
    else
   {
       while(head->next!=NULL)
       {
           head=head->next;
       }
       head->next=temp;
   }
}    


//Function for print foodlist
void foodlist(){
    node *start;
    start = menu;
    
    printf("------------------------------\n");system("color 3A");
    printf("Item Number | Food Name | price | stock  \n");
    
    while(start != NULL)   {
        printf("------------------------------\n");
        line(30);tab(30);
        printf("%d      | %s     |%d     |%.2f      \n",start->data, start->foodname, start->stock, start->price);sleep(200);line(3);
        printf("------------------------------\n");
        start=start->next;
    }
}


//Function for count the total food Item
int count(){
    int cnt=0;
    node *temp;
    temp=menu;
    
    while(temp!=NULL){
        temp=temp->next;
        cnt++;
    }
    return cnt;
}


//total take for order
int total_money(int foodchoice, int much){
    scr();
    node *temp;
    temp=(node*)malloc(sizeof(node));
    temp=menu;
    
    while(temp->data !=foodchoice){
        int o;
        float total=temp->price*much;
        
        
        line(3);tab(2); print("Total money for your order: ");line(2);system("color 7c");
        line(3);tab(2); printf("%.2f,total");line(2);
        line(10);tab(20);print("Enter your table Number: ");line(2);
        line(10);tab(70);scanf("%d",&o);line(2);
        return total;
    }
}



//Function for payment
void payment(float money){
    scr();
    back_option;
    line(10);tab(20);print("How you pay this money:");line(2);system("color 0F");
    line(10);tab(70);print("1. cash");line(2);
    line(10);tab(70);print("2. credit card");line(2);
    
    int choose;
    float taka;
    
    line(5);tab(3); scanf("%d",&choose);line(2);
    
    if(choose==1){
        scr();
        
        give :
        
        line(5); tab(5); print("How much you give: ");line(2);system("color  69");
        line(5);tab(5);scanf("%f",&taka);line(2);
        
        if(money>taka){
            scr();
            line(10);tab(10);printf("please give %.2f some also ", money-taka);line(2);
            goto give;
        }
        else
        {
            scr();
            line(5);tab(5);printf("you paben %.2f",taka-money);line(2); 
        }
    }
    else if(choose==2){
        scr();
        int card_num[20], i=0;
        line(5);tab(5);print("please give your card Number:");line(2);
        line(5);tab(10);scanf("%d",&card_num[i]); line(2);
        credit_card[i]=card_num[i];
        i++;
        scr();
        line(2);tab(2);printf("Thank you sir");line(2);
    }
    else{
        line(10);tab(5);printf("please Enter correct password sir");line(2);
        goto back_option;
    }
}

//Function for food order
int orderlist(){
    int foodchoice,much,i,j,k;
    
    food_choice;
    line(2);print("whice product  !");line(3);
    
    tab(5);scanf("%d",&foodchoice);
    i=count();
    
    if(foodchoice>=1 && foodchoice<=1){
        line(2);tab(2);print("How much you need: ");
        tab(3);scanf("%d",&much);
        
        k=total_money(foodchoice,much);
        payment (k);
        return k;
    }
    else{
        scr();
        line(5);tab(3);print("Enter correct Item Number please: "); line(2);
        foodlist();
        goto food_choice;
    }
}

//Function for windows size

void windows(){
    system ("title ........ code by me .........");
    system("mode con: lines=35 cols=120");
}



//main Function :


int main(){
    windows();
    
    line(30); tab(20); print("*****************************");line(2);
    line(30); tab(20); print("* Walcome To Our Resturant  *");line(2);
    line(30); tab(20); print("*****************************");line(2);sleep(3000);
    
    main_menu:
    line(5); tab(5); print("Enter your choice sir/Medam :");line(4);
    
    fooodlist();
    
    head=NULL;
    
    insertfood("Beef",1,50,150.50);
    insertfood("chikn",2,45,50.75);
    insertfood("shing",3,30,60.50);
    insertfood("utkol",4,45,70.25);
    insertfood("gojal",5,430,80.00);
    
    
    int choose, foodstock, fooddate, backmenu;
    float foodprice;
    char choice,addfood[30];
    char Problem[2000],problem_box[2000];
    
    line(5);tab(3);print("---->"); scanf("%c",&choice);
    
    
    if(choice>='1' && choice<='5'){
        if(choice=='1')  ///Food menu
        {
            food_list:
            scr();
            line(30);tab(20);print("Enter your choice: ");line(3);
            
            foodlist();
            orderlist();
            
            
            line(10);tab(5);printf("Thank you for choosing");line(2);
            
            another_food:
            
            line(10);tab(5);printf("Are you want to buy another food:");line(2);
            line(3);tab(2);printf("press 1 for main menu 2 for foodlist or 0 for exit=>");
            tab(5);fflush(stdin);scanf("%d",&backmenu);
            
            
            switch(backmenu){
                case 1:
                
                scr();
                goto main_menu;
                break;
                
                case 2:
                
                scr();
                goto food_list;
                break;
                
                case 0:
                
                scr();
                line(10);tab(5); printf("......Thank you sir..........");line(5);
                break;
                
                default:
                
                printf("Enter correct press sir: ");
                goto another_food;
            }
        }
        else if(choice=='2'){             //Admin panel
            scr();
            int pass;
            
            admin_log:
            
            line(5);tab(5);print("Enter 0 for go to the main menu");line(2);system("color 9F");
            line(10);print("Enter the password:");line(4);
            line(3);tab(2);fflush(stdin);scanf("%d",&pass);
            
            if(pass==15215){
                choose_option;
                scr();
                
                line(5);tab(5);print("1. Total Money"); line(2);system("color 1E");
                line(5);tab(5);print("2. problem and suggestion"); line(2);
                line(5);tab(5);print("3. Add Food"); line(2);
                line(5);tab(5);print("4. Delete Food"); line(2);
                line(5);tab(5);print("5. All card number"); line(2);
                line(5);tab(5);print("6. Total Item"); line(2);
                line(5);tab(5);print("Enter 0 for go to the main menu"); line(2);
                
                line(5);tab(5);scanf("%d",&choose);
                
                if (choose>=0 && choose<=7){
                    if(choose==1){
                        scr();
                        int k;
                        line(5);tab(5);
                        orderlist(k);
                        printf("%d",k);
                        
                        line(2);
                    }
                    else if(choose==2){
                        scr();
                        int q=0;
                        line(5);tab(5);printf("%s",problem_box[q]);line(2);
                        q++;
                    }
                    else if(choose==3){
                        scr();
                        print("Enter list number:");
                        scanf("%d",&fooddate);
                        print("Enter food Name:");
                        scanf("%s",&addfood);
                        print("Enter food price:");
                        scanf("%f",&foodprice);
                        print("Enter food stock:");
                        scanf("%d",&foodstock);   //insertfood();
                        
                       line(5);tab(5);print("sorry ...... we work for improving this softwer:)Thank u");line(2); 
                    
                    }
                         
                    else if(choose==4){
                        scr();
                        line(5);tab(5);print("sorry ...... we work for improving this softwer:)Thank u");line(2);
                        

                    }
                    else if(choose==5){
                        int k=0;
                    }
                }
            }
        }                  
    }
    }








































