#include<stdio.h>
#include<stdlib.h>
#include<string.h>
#include<ctype.h>

#define MALLOC(p,s,t)\
        p=(t)malloc(s);\
        if(p==NULL){\
        printf("Insufficient Memory\n");\
        exit;\
        }
        
struct details
{
    char name[30];
    char num[15];
    char email[50];
    char address[100];
    struct details *link;
};
typedef struct details *contact;

char name[30];
char num[15];
char email[50];
char address[100];

contact insert(contact,char [],char [],char [],char []);
contact delete(contact,char []);
contact edit(contact,char []);
void search(contact,char []);
void display(contact);
int compare(char [],char []);
void reset();
void red();
void blue();

int main()
{
    system("clear");
    int done=0,c1,c2,z=0,x=0;
    contact gmail,phone,sim;
    MALLOC(gmail,sizeof(struct details),contact);
    MALLOC(phone,sizeof(struct details),contact);
    MALLOC(sim,sizeof(struct details),contact);
    gmail->link=NULL;
    phone->link=NULL;
    sim->link=NULL;
    while(!done)
    {
        printf("\n1. ADD A CONTACT\n2. DELETE A CONTACT\n3. EDIT A CONTACT\n4. SEARCH A CONTACT\n5. DISPLAY CONTACTS\n6. EXIT FROM PHONE DIRECTORY\n\n");
        printf("Enter a choice : ");
        blue();
        scanf("%d",&c1);
        reset();
        system("clear");
        switch(c1)
        {
            case 1: printf("Enter the name      : ");
                    blue();
                    scanf(" %[^\n]s",name);
                    reset();
                    printf("Enter the number    : ");
                    blue();
                    scanf("%s",num);
                    reset();
                    while(z<strlen(num))
                    {
                        if(!isdigit(num[z]) && (num[z]!='+'))
                        {
                            system("clear");
                            red();
                            printf("INVALID NUMBER\n");
                            reset();
                            x=1;
                            break;
                        }
                        z++;
                    }
                    if(x==1)
                    {
                        break;
                    }
                    printf("Enter the E-Mail ID : ");
                    blue();
                    scanf(" %[^\n]s",email);
                    reset();
                    printf("Enter the Address   : ");
                    blue();
                    scanf(" %[^\n]s",address);
                    reset();
                    printf("\nWhere do you want to save this contact details?\n1. G-Mail\n2. Phone\n3. SIM\n\n");
                    printf("Enter a choice : ");
                    blue();
                    scanf("%d",&c2);
                    reset();
                    system("clear");
                    switch(c2)
                    {
                        case 1: gmail=insert(gmail,name,num,email,address);
                                break;
                        case 2: phone=insert(phone,name,num,email,address);
                                break;
                        case 3: sim=insert(sim,name,num,email,address);
                                break;
                        default:red();
                                printf("\nINVALID CHOICE\n");
                                reset();
                    }
                    break;
            case 2: printf("\nFrom where do you want to delete the contact details?\n1. G-Mail\n2. Phone\n3. SIM\n\n");
                    printf("Enter a choice : ");
                    blue();
                    scanf("%d",&c2);
                    reset();
                    system("clear");
                    printf("Enter the name of the contact you want to delete : ");
                    blue();
                    scanf(" %[^\n]s",name);
                    reset();
                    system("clear");
                    switch(c2)
                    {
                        case 1: gmail=delete(gmail,name);
                                break;
                        case 2: phone=delete(phone,name);
                                break;
                        case 3: sim=delete(sim,name);
                                break;
                        default:red();
                                printf("\nINVALID CHOICE\n");
                                reset();
                    }
                    break;
            case 3: printf("\nThe contact details which you want to edit is present in\n1. G-Mail\n2. Phone\n3. SIM\n\n");
                    printf("Enter a choice : ");
                    blue();
                    scanf("%d",&c2);
                    reset();
                    system("clear");
                    printf("Enter the name of the contact you want to edit : ");
                    blue();
                    scanf(" %[^\n]s",name);
                    reset();
                    system("clear");
                    switch(c2)
                    {
                        case 1: gmail=edit(gmail,name);
                                break;
                        case 2: phone=edit(phone,name);
                                break;
                        case 3: sim=edit(sim,name);
                                break;
                        default:red();
                                printf("\nINVALID CHOICE\n");
                                reset();
                    }
                    break;
            
            case 4: printf("\nIn which directory you want to search.\n1. G-Mail\n2. Phone\n3. SIM\n\n");
                    printf("Enter a choice : ");
                    blue();
                    scanf("%d",&c2);
                    reset();
                    system("clear");
                    printf("Enter the name of the contact you want to search : ");
                    blue();
                    scanf(" %[^\n]s",name);
                    reset();
                    system("clear");
                    switch(c2)
                    {
                        case 1: search(gmail,name);
                                break;
                        case 2: search(phone,name);
                                break;
                        case 3: search(sim,name);
                                break;
                        default:red();
                                printf("\nINVALID CHOICE\n");
                                reset();
                    }
                    break;
            case 5: printf("\nDo you want to display\n1. All contacts\n2. Contacts saved in G-Mail\n3. Contacts saved in Phone\n4. Contacts saved in SIM\n\n");
                    printf("Enter a choice : ");
                    blue();
                    scanf("%d",&c2);
                    reset();
                    system("clear");
                    switch(c2)
                    {
                        case 1: printf("\n               G-MAIL\n");
                                printf("************************************");
                                display(gmail);
                                printf("\n               PHONE\n");
                                printf("************************************");
                                display(phone);
                                printf("\n                SIM\n");
                                printf("************************************");
                                display(sim);
                                break;
                        case 2: printf("\n               G-MAIL\n");
                                printf("************************************");
                                display(gmail);
                                break;
                        case 3: printf("\n               PHONE\n");
                                printf("************************************");
                                display(phone);
                                break;
                        case 4: printf("\n                SIM\n");
                                printf("************************************");
                                display(sim);
                                break;
                        default:red();
                                printf("\nINVALID CHOICE\n");
                                reset();
                    }
                    break;
            case 6: done=1;
                    system("clear");
                    break;
            default:red();
                    printf("\nINVALID CHOICE\n");
                    reset();
        }
    }
    return 0;
}
contact insert(contact head,char name [],char num [],char email [],char address[])
{
    contact temp,cur,pre,dup;
    MALLOC(temp,sizeof(struct details),contact);
    strcpy(temp->name,name);
    strcpy(temp->num,num);
    strcpy(temp->email,email);
    strcpy(temp->address,address);
    temp->link=NULL;
    if(head->link==NULL)
    {
        head->link=temp;
        return head;
    }
    red();
    dup=head->link;
    while(dup!=NULL && compare(dup->name,temp->name)!=0 && compare(dup->num,temp->num)!=0)
    {
        dup=dup->link;
    }
    if(compare(dup->name,temp->name)==0 && compare(dup->num,temp->num)==0)
    {
        printf("\nA CONTACT WITH THIS NAME AND NUMBER ALREADY EXISTS\n");
        reset();
        return head;
    }
    if(compare(dup->name,temp->name)==0)
    {
        printf("\nA CONTACT WITH THIS NAME ALREADY EXISTS\n");
        reset();
        return head;
    }
    if(compare(dup->num,temp->num)==0)
    {
        printf("\nA CONTACT WITH THIS NUMBER ALREADY EXISTS\n");
        reset();
        return head;
    }
    pre=head;
    cur=head->link;
    while(cur->link!=NULL && compare(cur->name,temp->name)<0)
    {
        pre=cur;
        cur=cur->link;
    }
    if(cur==NULL)
    {
        pre->link=temp;
        reset();
        return head;
    }
    pre->link=temp;
    temp->link=cur;
    reset();
    return head;
}
contact delete(contact head,char name[30])
{
    contact pre,cur;
    int i;
    pre=NULL;
    cur=head;
    while(cur->link!=NULL && compare(cur->name,name)!=0)
    {
        pre=cur;
        cur=cur->link;
    }
    if(compare(cur->name,name)==0)
    {
        red();
        printf("\nTHE CONTACT %s WILL BE PERMANENTLY DELETED!\n",name);
        reset();
        printf("DO YOU WANT TO CONTINUE? (1/0) : \n");
        blue();
        scanf("%d",&i);
        reset();
        if(i==1)
        {
            pre->link=cur->link;
            free(cur);
        }
        return head;
    }
    red();
    printf("\nNO SUCH CONTACT FOUND IN THE DIRECTORY\n");
    reset();
    return head;
}
contact edit(contact head,char name[30])
{
    int i,a;
    contact temp,cur;
    temp=head;
    cur=head;
    while(cur->link!=NULL && compare(cur->name,name)!=0)
    {
        cur=cur->link;
    }
    if(compare(cur->name,name)!=0)
    {
        red();
        printf("\nNO SUCH CONTACT FOUND IN DIRECTORY\n");
        reset();
        return head;
    }
    printf("DO YOU WANT TO EDIT NAME? (1/0) : ");
    blue();
    scanf("%d",&i);
    reset();
    if(i==1)
    {
        printf("Enter new name : ");
        blue();
        scanf(" %[^\n]s",name);
        reset();
        while(temp->link!=NULL && compare(temp->name,name)!=0)
        {
            temp=temp->link;
        }
        if(compare(temp->name,name)==0)
        {
            red();
            printf("\nCONTACT WITH SUCH NAME ALREADY EXISTS\n");
            reset();
            printf("DO YOU WANT TO CONTINUE TO EDIT THE NAME? (1/0) : ");
            blue();
            scanf("%d",&a);
            reset();
            if(a==1)
            {
                printf("Enter a different name : ");
                blue();
                scanf(" %[^\n]s",name);
                reset();
                strcpy(cur->name,name);
            }
        }
        else
        {
            strcpy(cur->name,name);
        }
    }
    printf("DO YOU WAN TO EDIT NUMBER? (1/0) : ");
    blue();
    scanf("%d",&i);
    reset();
    if(i==1)
    {
        printf("Enter new number : ");
        blue();
        scanf("%s",num);
        reset();
        while(temp->link!=NULL && compare(temp->num,num)!=0)
        {
            temp=temp->link;
        }
        if(compare(temp->num,num)==0)
        {
            red();
            printf("\nCONTACT WITH SUCH NUMBER ALREADY EXISTS\n");
            reset;
            printf("DO YOU WANT TO CONTINUE TO EDIT THE NUMBER? (1/0) : ");
            blue();
            scanf("%d",&a);
            reset();
            if(a==1)
            {
                printf("Enter a different number : ");
                blue();
                scanf("%s",num);
                reset();
                strcpy(cur->num,num);
            }
        }
        else
        {
            strcpy(cur->num,num);
        }
    }
    printf("DO YOU WAN TO EDIT E-MAIL ID? (1/0) : ");
    blue();
    scanf("%d",&i);
    reset();
    if(i==1)
    {
        printf("Enter new E-Mail ID : ");
        blue();
        scanf("%s",email);
        reset();
        strcpy(cur->email,email);
    }
    printf("DO YOU WAN TO EDIT ADDRESS? (1/0) : ");
    blue();
    scanf("%d",&i);
    reset();
    if(i==1)
    {
        printf("Enter new ADDRESS : ");
        blue();
        scanf("%s",address);
        reset();
        strcpy(cur->address,address);
    }
    return head;
}
void search(contact head,char name [])
{
    contact cur;
    cur=head;
    while(cur->link!=NULL && compare(cur->name,name)!=0)
    {
        cur=cur->link;
    }
    if(compare(cur->name,name)==0)
    {
        printf("\t   Name    : %s\n\t   Number  : %s\n\t   E-Mail  : %s\n\t   Address : %s\n\n",cur->name,cur->num,cur->email,cur->address);
    }
    else
    {
        red();
        printf("CONTACT WITH SUCH NAME DOESN'T EXIT\n");
        reset();
    }
}
void display(contact head)
{
    contact cur;
    cur=head->link;
    int count=1;
    printf("\n");
    if(head->link==NULL)
    {
        red();
        printf("          NO CONTACTS FOUND\n\n");
        reset();
        return;
    }
    while(cur!=NULL)
    {
        printf("\t%d. Name    : %s\n\t   Number  : %s\n\t   E-Mail  : %s\n\t   Address : %s\n\n",count,cur->name,cur->num,cur->email,cur->address);
        count++;
        cur=cur->link;
    }
    printf("\n");
}
int compare(char str1[],char str2[])
{
    int i;
    char a[30],b[30];
    for(i=0;i<=strlen(str1);i++)
    {
        if(str1[i]>=65 && str1[i]<=90)
        {
            a[i]=tolower(str1[i]);
        }
        else
        {
            a[i]=str1[i];
        }
   }
   for(i=0;i<=strlen(str2);i++)
    {
        if(str2[i]>=65 && str2[i]<=90)
        {
            b[i]=tolower(str2[i]);
        }
        else
        {
            b[i]=str2[i];
        }
   }
   return strcmp(a,b);
}
void reset()
{
    printf("\033[0m");
}
void red()
{
    printf("\033[0;31m");
    printf("\033[1m");
}
void blue()
{
    printf("\033[0;34m");
    printf("\033[1m");
}






