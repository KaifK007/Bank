#include<iostream>
using namespace std;
class Start;
class Bank
{
    protected :
    void greet()
    {
        cout<<"HELLO THERE!\n";
        data();
    }
    private :
    void data()
    {
        char name[10];
        int accno=0, pin=0, bal=0, op;
        cout<<"Enter name : ";
        cin>>name;
        cout<<"Enter Acc Nmbr : ";
        cin>>accno;
        cout<<"Enter pin : ";
        cin>>pin;
        list();
        cin>>op;
        bank(pin,op,bal);
    }
    void list()
    {
        cout<<"Select your task : \n1. View Balance. \n2. Withdraw. \n3. Deposit. \n4. Exit.\n Answer : ";
    }
    void bank(int pin , int op , int bal)
    {
        char ans;
        int dep=0, withd=0,pin2;
        switch(op)
        {
        
            case 1 :
                cout<<"Enter pin :";
                cin>>pin2;
                if(pin2==pin)
                {
                    cout<<"Current balance : "<<bal<<".\n Do you want to continue?\n Y or N\n";
                    cin>>ans;
                    if(ans=='y')
                    {
                        list();
                        cin>>op;
                        bank(pin,op,bal);
                    }
                    else
                    {
                        cout<<"Thank You!";
                    }
                }
                    break;
            case 2 :
                {
                    if(bal<=0)
                    {
                        cout<<"Transaction not possible.";
                    }
                    else
                    {
                        cout<<"Enter pin :";
                        cin>>pin2;
                        if(pin2==pin)
                        {
                            cout<<"Amount to withdraw : ";
                            cin>>withd;
                            if(withd<=bal)
                            {
                                bal-=withd;
                                cout<<"Current balance : "<<bal<<".\n Do you want to continue?\n Y or N \n";
                                cin>>ans;
                                if(ans=='y')
                                {
                                    list();
                                    cin>>op;
                                    bank(pin,op,bal);
                                }
                                else
                                {
                                    cout<<"Thank You!";
                                }
                            }
                            else
                            {
                                cout<<"Insufficient amount. Thank You!";
                            }
                        }
                        else
                        {
                            cout<<"Wrong pin!";
                        }
                    }
                    break;
                }
            case 3 :
                cout<<"Amount to deposit : ";
                cin>>dep;
                bal+=dep;
                cout<<"Current balance : "<<bal<<".\n Do you want to continue?\n Y or N\n";
                cin>>ans;
                if(ans=='y')
                {
                    list();
                    cin>>op;
                    bank(pin,op,bal);
                }
                else
                {
                    cout<<"Thank You!";
                }
                break;
            default :
                cout<<"Thank You!";
            
        }
    }
};
class Start : protected Bank
{
    public :
    void start()
    {
        greet();
    }
};
int main()
{
    Start s;
    s.start();

    
    return 0;
}

