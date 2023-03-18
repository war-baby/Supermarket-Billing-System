#include<iostream>
#include<fstream>

using namespace std;

class shopping {
    private:
        int pcode;
        float price;
        float discount;
        string pname;

    public:
        void menu();
        void administrator();
        void buyer();
        void add();
        void edit();
        void rem();
        void list();
        void receipt();
};

void shopping :: menu() {
    m:
    int choice;
    string email;
    string password;

    cout<<"\t\t\t\t-------------------------------\n";
    cout<<"\t\t\t\t                               \n";
    cout<<"\t\t\t\t     SUPERMARKET MAIN MENU     \n";
    cout<<"\t\t\t\t                               \n";
    cout<<"\t\t\t\t-------------------------------\n";
    cout<<"\t\t\t\t                               \n";

    cout<<"\t\t\t\t|    1) Administrator   |\n";
    cout<<"\t\t\t\t|                       |\n";
    cout<<"\t\t\t\t|    2) Buyer           |\n";
    cout<<"\t\t\t\t|                       |\n";
    cout<<"\t\t\t\t|    3) Exit            |\n";
    cout<<"\t\t\t\t|                       |\n";
    cout<<"\n\t\t\t Please select: ";
    cin>>choice;

    switch(choice) {
        case 1:
            cout<<"\t\t\t Please Login \n";
            cout<<"\t\t\t Enter Email : ";
            cin>>email;
            cout<<"\t\t\t Password : ";
            cin>>password;

            if(email=="admin1001@gmail.com" && password=="admin1001") {
                administrator();
            } else {
                cout<<"Invalid Email and Password!";
            }
            break;

        case 2:
            {
                buyer();
            }

        case 3:
            {
                exit(0);
            }

        default:
            cout<<"Please select from the given options: ";
    }
    
    goto m;
}

void shopping :: administrator() {
    m:
    int choice;
    cout<<"\n\n\n\t\t\t   ADMINISTRATOR MAIN MENU   ";
    cout<<"\n\t\t\t|---- 1) Add the product -------|";
    cout<<"\n\t\t\t|                               |";
    cout<<"\n\t\t\t|---- 2) Modify the product ----|";
    cout<<"\n\t\t\t|                               |";
    cout<<"\n\t\t\t|---- 3) Delete the product ----|";
    cout<<"\n\t\t\t|                               |";
    cout<<"\n\t\t\t|---- 4) Back to main menu -----|";

    cout<<"\n\n\t Please enter your choice: ";
    cin>>choice;

    switch(choice) {
        case 1:
            add();
            break;

        case 2:
            edit();
            break;
        
        case 3:
            rem();
            break;

        case 4:
            menu();
            break;

        default:
            cout<<"Invalid choice!";
    }
    goto m;
}

void shopping :: buyer() {
    m:
    int choice;
    cout<<"\t\t\t-----Buyer------\n";
    cout<<"                      \n";
    cout<<"\t\t\t 1) Buy product \n";
    cout<<"                      \n";
    cout<<"\t\t\t 2) Go back     \n";
    cout<<"\t\t\t Enter your choice: ";

    cin>>choice;

    switch(choice) {
        case 1:
            receipt();
            break;

        case 2:
            menu();

        default:
            cout<<"Invalid choice !";
    }
    
    goto m;
}

void shopping :: add() {
    m:
    fstream data;
    int c;
    int token=0;
    float p, d;
    string n;

    cout<<"\n\n\t\t Add new product ";
    cout<<"\n\n\t Code of the product: ";
    cin>>pcode;
    cout<<"\n\n\t Name of the product:";
    cin>>pname;
    cout<<"\n\n\t Price of the product: ";
    cin>>price;
    cout<<"\n\n\t Discount on the product: ";
    cin>>discount;

    data.open("database.txt", ios::in); // ios::in -- reading mode  ios::out -- writing mode

    if(!data) {
        data.open("database.txt", ios::app|ios::out);
        data<<"  "<<pcode<<"  "<<pname<<"  "<<price<<"  "<<discount<<"\n";
        data.close();
    } else {
        data>>c>>n>>p>>d;

        // eof -- end of file function
        while(!data.eof()) {
            if(c==pcode) {
                token++;
            }
            data>>c>>n>>p>>d;
        }
        data.close();
    

        if(token==1) {
          goto m;
        } else {
             data.open("database.txt", ios::app|ios::out);
            data<<"  "<<pcode<<"  "<<pname<<"  "<<price<<"  "<<discount<<"\n";
            data.close();
        }
    }
    cout<<"\n\n\t\t Record inserted!";
}

void shopping :: edit() {
    fstream data, data1;
    int pkey;
    int token=0;
    int c;
    float p;
    float d;
    string n;

    cout<<"\n\t\t\t Modify the record";
    cout<<"\n\t\t\t Product code : ";
    cin>>pkey;

    data.open("database.txt", ios::in);
    if(!data) {
        cout<<"\n\nFile does not exist";
    } else {
        data1.open("database1.txt", ios::app|ios::out);

        data>>pcode>>pname>>price>>discount;
        while(!data.eof()) {
            if(pkey==pcode) {
                cout<<"\n\t\t Product new code : ";
                cin>>c;
                cout<<"\n\t\t Name of the product : ";
                cin>>n;
                cout<<"\n\t\t Price : ";
                cin>>p;
                cout<<"\n\t\t Discount : ";
                cin>>discount;
                data1<<" "<<c<<" "<<n<<" "<<p<<" "<<d<<"\n";
                cout<<"\n\n\t\t Record edited!";
                token++;
            } else {
                data1<<" "<<pcode<<" "<<pname<<" "<<price<<" "<<discount<<"\n";
            }
            data>>pcode>>pname>>price>>discount;
        }
        data.close();
        data1.close();

        remove("database.txt");
        rename("database1.txt","database.txt");

        if(token==0) {
            cout<<"\n\n Record not found, sorry!";
        }
    }
}

void shopping :: rem() {
    fstream data, data1;
    int pkey;
    int token=0;
    cout<<"\n\n\t Delete product";
    cout<<"\n\n\t Product code : ";
    cin>>pkey;
    data.open("database.txt", ios::in);
    if(!data) {
        cout<<"File does not exist";
    } else {
        data1.open("database1.txt", ios::app|ios::out);
        data>>pcode>>pname>>price>>discount;

        while(!data.eof()) {
            if(pcode==pkey) {
                cout<<"\n\n\t Product deleted succesfully";
                token++;
            } else {
                data1<<" "<<pcode<<" "<<pname<<" "<<price<<" "<<discount<<"\n";
            }
            data>>pcode>>pname>>price>>discount;
        }
        data.close();
        data1.close();
        remove("database.txt");
        rename("database1.txt", "database.txt");

        if(token==0) {
            cout<<"\n\n Record not found";
        }
    }
}

void shopping :: list() {
    fstream data;
    data.open("database.txt", ios::in);
    cout<<"\n\n------------------------------------------\n";
    cout<<"ProNo\t\tName\t\tPrice\n";
    cout<<"\n\n------------------------------------------\n";
    data>>pcode>>pname>>price>>discount;
    while(!data.eof()) {
        cout<<pcode<<"\t\t"<<pname<<"\t\t"<<price<<"\n";
        data>>pcode>>pname>>price>>discount;
    }
    data.close();
}

void shopping :: receipt() {

    fstream data;
    int arr_codes[100];
    int arr_quantity[100];
    char c=0;
    float amount=0;
    float dis=0;
    float total=0;
    string choice;

    cout<<"\n\n\t\t\t\t RECEIPT ";
    data.open("database.txt", ios::in);
    if(!data) {
        cout<<"\n\n Empty Database";
    } else {
        data.close();

        list();
        cout<<"\n---------------------------------\n";
        cout<<"\n|                               |\n";
        cout<<"\n     Please place the order      \n";
        cout<<"\n|                               |\n";
        cout<<"\n---------------------------------\n";

        do {
            m:
            cout<<"\n\n Enter Product code: ";
            cin>>arr_codes[c];
            cout<<"\n\nEnter the product quantity: ";
            cin>>arr_quantity[c];
            for(int i=0; i<c; i++) {
                if(arr_codes[c]==arr_codes[i]) {
                    cout<<"\n\n Duplicate product code; Please try again!";
                    goto m;
                }
            }
            c++;
            cout<<"\n\n Do you want to buy another product? If yes, then press y else n: ";
            cin>>choice;
        } while(choice=="y");
            cout<<"\n\n\t\t\t---------------RECEIPT----------------\n";
            cout<<"\nPRODUCT No.\t\t Product Name\t\t Product Quantity\t\t Price\t\t Amount\t\t Amount with discount\n";

            for(int i=0; i<c; i++) {
                data.open("database.txt", ios::in);
                data>>pcode>>pname>>price>>discount;
                while(!data.eof()) {
                    if(pcode==arr_codes[i]) {
                        amount=price*arr_quantity[i];
                        discount=amount-(amount*discount/100);
                        total=total+discount;
                        cout<<"\n"<<pcode<<"\t"<<pname<<"\t"<<arr_quantity[i]<<"\t"<<price<<"\t"<<amount<<"\t"<<discount;                 
                    }
                    data>>pcode>>pname>>price>>discount;
                }
            }
            data.close();
    }
    cout<<"\n\n---------------------------------------";
    cout<<"\n Total Amount: "<<total;
}

int main() {
    shopping s;
    s.menu();
}
