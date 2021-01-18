#include <iostream>
#include <fstream>
#include <string>
#include<cstdlib>
#include <conio.h>
using namespace std;
//Functions
void interface()
{
	cout << "\n\n\t\t\t\t****************************************************************\n" << endl;
	cout << " \t\t\t\t\t\tPlease Choose one of the following:\n" << endl;
	cout << " \t\t\t\t\t\t\t1--->Accountant" << endl;
	cout << " \t\t\t\t\t\t\t2--->Customer" << endl;
	cout << " \t\t\t\t\t\t\t3--->Exit" << endl;
	cout << "\t\t\t\t****************************************************************" << endl;

}
void customer()
{
	cout << "\n\n\n\t\t\t\t****************************************************************\n" << endl;
	cout << "\t\t\t\t\t\t\t1---> Open an account" << endl;
	cout << "\t\t\t\t\t\t\t2---> Deposit Money" << endl;
	cout << "\t\t\t\t\t\t\t3---> Withdraw Money" << endl;
	cout << "\t\t\t\t\t\t\t4---> Account Details" << endl;
	cout << "\t\t\t\t\t\t\t5---> Exit" << endl;
	cout << "\n\t\t\t\t****************************************************************\n" << endl;

}
void accountant()
{
	cout << "\n\n\n\t\t\t\t****************************************************************\n" << endl;
	cout << "\t\t\t\t\t\t\t1---> Apply for Card" << endl;
	cout << "\t\t\t\t\t\t\t2---> Display All Accounts" << endl;
	cout << "\t\t\t\t\t\t\t3---> Update Account" << endl;
	cout << "\t\t\t\t\t\t\t4---> Delete Account" << endl;
	cout << "\t\t\t\t\t\t\t5---> Exit" << endl;
	cout << "\n\t\t\t\t****************************************************************\n" << endl;
}
void ending() {
	cout << "\n\n\n\t\t\t\t****************************************************************\n" << endl << endl;
	cout << "\t\t\t\t\t\t\tThankyou" << endl;
	cout << "\t\t\t\t****************************************************************\n" << endl;
}
//Accountant Class
class acc
{
public:
	
	char name[20];
	int ID;
	char address[30];
	int balance;
	char type[10];
	
public:
	acc();
	void setname();
	void setID();
	void setaddress();
	void setbalance(int b);
	void settype();
	string getname();
	int getID();
	string getaddress();
	int getbalance();
	string gettype();
};
string acc::gettype()
{
	return type;
}
int acc::getbalance()
{
	return balance;
}
string acc::getaddress()
{
	return address;
}
int acc::getID()
{
	return ID;
}
string acc :: getname()
{
	return name;
}
acc::acc() :name("0"),ID(0),address("0"),balance(0),type("0") {}
void acc::settype()
{
	cout << "Settype is called" << endl;
	int t = 0;
	while (t != 1 && t != 2)
	{
		cout << "(1) Savings account" << endl;
		cout << "(2) Current account" << endl;
		cout << "Enter your choice" << endl;
		cin >> t;
		if (t == 1)
		{
			strcpy_s(type, "savings");
		}
		else if (t == 2)
		{
			strcpy_s(type, "current");
		}
		else
		{
			cout << "Enter a correct choice" << endl;
		}
	}
}
void acc::setname()
{
	cin.ignore();
	cout << "Enter your name" << endl;
	cin.getline(name, 20);
}
void acc::setID()
{
	cout << "Enter your acc ID" << endl;
	cin >> ID;
}
void acc:: setaddress()
{
	cout << "Enter your address" << endl;
	cin.getline(address,30);
}
void acc :: setbalance(int b)
{
	balance = b;
}
//Card Class
class card
{

public:
	int ID;
	double cardno;
	double cvcno;
	char iss[20];
	char exp[20];

public:
	card();
	void setID(int a);
	void setcardno();
	void setcvcno();
	void issdate();
	int getID();
	double getcardno();
	double getcvcno();
	string getissdate();
	string getexpdate();
};
card::card():ID(0),cardno(0),cvcno(0),iss("0"),exp("0")
{}
void card::setID(int a)
{
	ID = a;
}
int card::getID()
{
	return ID;
}
void card::setcardno()
{
	cout << "Enter the card number" << endl;
	cin >> cardno;
}
void card::setcvcno()
{
	cout << "Enter card verification code" << endl;
	cin >> cvcno;
}
void card::issdate()
{
	string a,d,m;
	int y;
	cout << "Enter day: " << endl;
	cin.ignore();
	cin >> d;
	cout << "Enter month: " << endl;	
	cin.ignore();
	cin >> m;
	cout << "Enter year: " << endl;
	cin.ignore();
	cin >> y;
	 string yy;
	 //converting y from int to string
	 yy = to_string(y);
	 //Date display a=dd/mm/yy
	 a = d + '/' + m + '/'+yy;
	 //Storing a in issue date
	 for (int i = 0; i < a.length(); i++)
	 {
		 iss[i] = a[i];
	 }
	 //Exp date:
	 y++;
	 string yt = to_string(y);
	 a = d + '/' + m + '/' + yt;
	 for (int i = 0; i < a.length(); i++)
	 {
		 exp[i] = a[i];
	 }
}
double card::getcardno()
{
	return cardno;
}
double card::getcvcno()
{
	return cvcno;
}
string card::getissdate()
{
	return iss;
}
string card::getexpdate()
{
	return exp;
}
//Reading from a file
int main()
{
	ofstream file7;
	file7.open("cards.txt", ios::binary | ios::app | ios::in);
	file7.close();
	ofstream file8;
	file8.open("input.txt", ios::binary | ios::app | ios::in);
	file8.close();
	card b;
	acc a;
	short i = 0, t = 0;
	//loop 1
	while (i == 0)
	{
		system("pause");
		system("cls");
		interface();
		cout << "Enter your choice" << endl;
		cin >> t;
		//switch 1
		switch (t)
		{
		//Accountant
		case 1:
		{

			system("pause");
			system("cls");
			cout << "*******************************" << endl << endl;
			cout << "*     Welcome Accountant      *" << endl << endl;
			cout << "*******************************" << endl;
			short a = 0;
			while (a == 0)
			{
				system("pause");
				system("cls");
				accountant();
				short e;
				cout << "Enter your choice" << endl;
				cin >> e;
				switch (e)
				{
					//Apply Debit card
				case 1:
				{
					cout << "How do you want to find your account\n(1) Account ID\n(2) Account Holder Name" << endl;
					short f = 0;
					cin >> f;
					int c = 0;
					string e;
					int j = 0;
					switch (f)
					{
					case 1:
					{
						cout << "Enter Your Acc ID" << endl;
						cin >> c;
						break;
					}
					case 2:
					{
						cout << "Enter Account Holder Name" << endl;
						cin.ignore();
						getline(cin, e);
						//exp
						ifstream file;
						file.open("input.txt", ios::binary | ios::app | ios::in);
						short d = 0;
						file.seekg(0);
						acc b;
						while (!file.eof())
						{
							file.read((char*)(&b), sizeof(b));
							if (file.tellg() == -1)
							{
								continue;
							}
							if (b.getID() == c || b.getname() == e)
							{
								d++;
							}
						}
						if (d > 1)
						{
							cout << "Multiple records found please enter Acc ID" << endl;
							system("pause");
							exit(0);
						}
						else if (d == 0)
						{
							cout << "No record found" << endl;
							system("pause");
							exit(0);
						}
						j = b.getID();
						file.close();
						//end of exp
						break;
					}
					default:
					{
						cout << "Invalid choice" << endl;
						break;
					}
					}
					ifstream filea;
					filea.open("input.txt", ios::binary | ios::app | ios::in); short d = 0;
					filea.seekg(0);
					acc b;
					
					while (!filea.eof())
					{
						filea.read((char*)(&b), sizeof(b));
						if (filea.tellg() == -1)
						{
							continue;
						}
						if (b.getID() == c || b.getname() == e)
						{
							cout << "Record Found" << endl;
							d++;
							cout << "ID:\t" << b.getID() << endl << "Name\t" << b.getname() << endl;
							cout << "Balance\t" << b.getbalance() << endl << "Type\t" << b.gettype() << endl << "Address\t" << b.getaddress() << endl;
							cout << "-----------------------------------------------------------------------------------------------------" << endl;
							cout << "Enter the data asked in following fields" << endl;
							card f;
							f.ID = c;
							f.setcardno();
							f.setcvcno();
							f.issdate();
							ofstream filex;
							filex.open("cards.txt", ios::binary | ios::out | ios::app);
							if (filex.is_open())
							{
								cout << "File successfully opened" << endl;
							}
							else
							{
								cout << "error opening file" << endl;
							}
							filex.write((char*)&f, sizeof(f));
							filex.close();
						}
					}
					filea.close();
					break;
				}
				//Display All Accounts
				case 2:
				{
					cout << "Displaying all accounts" << endl;
					ifstream file4;
					file4.open("input.txt", ios::binary | ios::app | ios::in);
					file4.seekg(0);
					acc w;
					if (file4.is_open())
					{
						cout << "file is open" << endl;
					}
					else {
						cout << "Failed file opening";
						exit(0);
					}
					while (!file4.eof())
					{
						file4.read((char*)&w, sizeof(w));
						if (file4.tellg() == -1)
						{
							continue;
						}
						else
						{
							cout << "ID:\t" << w.getID() << endl << "Name\t" << w.getname() << endl;
							cout << "Balance\t" << w.getbalance() << endl << "Type\t" << w.gettype() << endl << "Address\t" << w.getaddress() << endl;
							cout << "-----------------------------------------------------------------------------------------------------" << endl;
						}
					}
					file4.close();
					break;
				}
				//Update Account
				case 3:
				{
					cout << "How do you want to find your account\n(1) Account ID\n(2) Account Holder Name" << endl;
					short f = 0;
					cin >> f;
					int c = 0;
					string e;
					switch (f)
					{
					case 1:
					{
						cout << "Enter Your Acc ID" << endl;
						cin >> c;
						break;
					}
					case 2:
					{
						cout << "Enter Account Holder Name" << endl;
						cin.ignore();
						getline(cin, e);
						//exp
						ifstream file;
						file.open("input.txt", ios::binary | ios::app | ios::in);
						short d = 0;
						file.seekg(0);
						acc b;
						while (!file.eof())
						{
							file.read((char*)(&b), sizeof(b));
							if (file.tellg() == -1)
							{
								continue;
							}
							if (b.getID() == c || b.getname() == e)
							{
								d++;
							}
						}
						if (d > 1)
						{
							cout << "Multiple records found please enter Acc ID" << endl;
							system("pause");
							exit(0);
						}
						else if (d == 0)
						{
							cout << "No record found" << endl;
							system("pause");
							exit(0);
						}
						file.close();
						//end of exp
						break;
					}
					default:
					{
						cout << "Invalid choice" << endl;
						break;
					}
					}
					fstream file9;
					file9.open("input.txt", ios::binary | ios::in | ios::out); short d = 0;
					file9.seekg(0);
					file9.seekp(0);
					acc b;
					if (file9.is_open())
					{
						cout << "File successfully opened" << endl;
					}
					else
					{
						cout << "Error in file opening" << endl;
						exit(0);
					}
					while (!file9.eof())
					{
						file9.read((char*)(&b), sizeof(b));
						if (b.getID() == c || b.getname() == e)
						{
							d++;
							cout << "ID:\t" << b.getID() << endl << "Name\t" << b.getname() << endl;
							cout << "Balance\t" << b.getbalance() << endl << "Type\t" << b.gettype() << endl << "Address\t" << b.getaddress() << endl;
							cout << "-----------------------------------------------------------------------------------------------------" << endl;
							acc c;
							c.setname();
							c.setaddress();
							c.ID = b.ID;
							c.settype();
							file9.seekp(-72, ios::cur);
							file9.write((char*)&c, sizeof(c));
							break;
						}
					}
					file9.close();
					//end
					break;
				}
					//Delete Account
				case 4:
				{
					cout << "How do you want to find your account\n(1) Account ID\n(2) Account Holder Name" << endl;
					short f = 0;
					cin >> f;
					int c = 0;
					string e;
					switch (f)
					{
					case 1:
					{
						cout << "Enter Your Acc ID" << endl;
						cin >> c;
						break;
					}
					case 2:
					{
						cout << "Enter Account Holder Name" << endl;
						cin.ignore();
						getline(cin, e);
						//exp
						ifstream file;
						file.open("input.txt", ios::binary | ios::app | ios::in); short d = 0;
						file.seekg(0);
						acc b;
						cout << "size of b is" << sizeof(b) << endl;
						while (!file.eof())
						{
							file.read((char*)(&b), sizeof(b));
							if (file.tellg() == -1)
							{
								continue;
							}
							if (b.getID() == c || b.getname() == e)
							{
								d++;
							}
						}
						if (d > 1)
						{
							cout << "Multiple records found please enter Acc ID" << endl;
							system("pause");
							file.close();
							exit(0);
						}
						else if (d == 0)
						{
							cout << "No record found" << endl;
							system("pause");
							exit(0);
						}
						file.close();
						break;
					}
					default:
					{
						cout << "Invalid choice" << endl;
						break;
					}
					}
					ifstream file;
					ofstream file1;
					fstream file2;
					/*ifstream file3;
					*/file2.open("cards.txt", ios::binary|ios::in | ios::out | ios::app);
					/*file3.open("card.txt", ios::binary | ios::out | ios::app);*/
					file.open("input.txt", ios::binary | ios::in | ios::app);
					file1.open("temp.txt", ios::binary | ios::in | ios::app);
					short d = 0;
					file.seekg(0);
					file1.seekp(0);
					acc b;
					short h=0;
					while (!file.eof())
					{
						file.read((char*)(&b), sizeof(b));
						if (file.tellg() == -1)
						{
							continue;
						}
						if (b.getID() != c && b.getname() != e)
						{
							h++;
							file1.write((char*)&b, sizeof(b));
						}
					}
					if (h == 0)
					{
						cout << "No record found " << endl;
					}
					if (h == 1)
					{
						cout << "Record Deleted" << endl;
					}
					while (!file2.eof())
					{
						card n;
						file2.read((char*)(&n), sizeof(n));
						if (file2.tellg() == -1)
						{
							continue;
						}
						if (n.getID() != c)
						{
							file2.write((char*)&b, sizeof(b));
						}
					}
					file2.close();
					//file3.close();
					file.close();
					file1.close();
					remove("input.txt");
					rename("temp.txt", "input.txt");
					remove("cards.txt");
					rename("card.txt", "cards.txt");
					break;
				}
				//Exit
				case 5:
				{a = 1;
				break; }
				//default 
				default:
				{
					cout << "You entered invalid value" << endl;
					break;
				}
				}
			}
			break;
		}
		//Customer
		case 2: {
			system("pause");
			system("cls");
			customer();
			cout << "Enter your choice" << endl;
			short d;
			cin >> d;
			system("cls");
			//switch 2
			switch (d)
			{
				//Open Account
			case 1:
			{
				int z, d = 0;
				acc a, b;
				a.setID();
				z = a.ID;
				/*cout << "first ID " << a.ID << endl;
				cout << "Value of z " << z << endl;
				*/ifstream file2;
				ifstream file1;
				file2.open("input.txt", ios::binary | ios::in | ios::app);
				file2.seekg(0);
				if (file2.is_open())
				{
					cout << "File opened" << endl;
				}
				while (!file2.eof())
				{
					file2.read((char*)(&b), sizeof(b));
					if (b.ID == z)
					{
						d++;
					}
				}
				if (d > 0)
				{
					cout << "An account with this ID already exists enter another one" << endl;
					system("pause");
					file2.close();
					file1.close();
					break;
				}
				else {
					file2.close();
					file1.close();
					a.setname();
					a.setaddress();
					a.settype();
					ofstream file;
					file.open("input.txt", ios::binary | ios::app | ios::out);
					file.write((char*)&a, sizeof(a));
					file.close();
					break;
				}
			}
			//Cash Deposit
			case 2:
			{
				cout << "How do you want to find your account\n(1) Account ID\n(2) Account Holder Name" << endl;
				short f = 0;
				cin >> f;
				int c = 0;
				string e;
				switch (f)
				{
				case 1:
				{
					cout << "Enter Your Acc ID" << endl;
					cin >> c;
					break;
				}
				case 2:
				{
					cout << "Enter Account Holder Name" << endl;
					cin.ignore();
					getline(cin, e);
					//exp
					ifstream file;
					file.open("input.txt", ios::binary | ios::app | ios::in); short d = 0;
					file.seekg(0);
					acc b;
					cout << "size of b is" << sizeof(b) << endl;
					while (!file.eof())
					{
						file.read((char*)(&b), sizeof(b));
						if (file.tellg() == -1)
						{
							continue;
						}
						if (b.getID() == c || b.getname() == e)
						{
							d++;
						}
					}
					if (d > 1)
					{
						cout << "Multiple records found please enter Acc ID" << endl;
						system("pause");
						file.close();
						exit(0);
					}
					else if (d == 0)
					{
						cout << "No record found" << endl;
						system("pause");
						exit(0);
					}
					file.close();
					break;
				}
				default:
				{
					cout << "Invalid choice" << endl;
					break;
				}
				}
				fstream file5;
				file5.open("input.txt", ios::binary | ios::in | ios::out);
				short d = 0;
				file5.seekg(0);
				file5.seekp(0);
				acc h;
				if (file5.is_open())
				{
					/*cout << "file is open" << endl;*/
				}
				else {
					cout << "Failed file opening";
					exit(0);
				}
				while (!file5.eof())
				{
					file5.read((char*)(&h), sizeof(h));
					if (file5.tellg() == -1)
					{
						continue;
					}
					if (h.getID() == c || h.getname() == e)
					{
						d++;
						cout << "ID:\t" << h.getID() << endl << "Name\t" << h.getname() << endl;
						cout << "Balance\t" << h.getbalance() << endl << "Type\t" << h.gettype() << endl << "Address\t" << h.getaddress() << endl;
						cout << "-----------------------------------------------------------------------------------------------------" << endl;
						int g;
						cin.ignore();
						cout << "How much do you want to deposit" << endl;
						cin >> g;
						if (g > 0)
						{
							acc e;
							e.ID=h.ID;
							strcpy_s(e.address, h.address);
							strcpy_s(e.name,h.name);
							strcpy_s(e.type, h.type);
							e.balance = g+h.balance;
							file5.seekp(-72, ios::cur);
							file5.write((char*)&e, sizeof(e));
							file5.close();
							break;
						}
						else
						{
							cout << "Invalid Value" << endl;
						}
					}
				}
				file5.close();
				break;
			}
			//Money Withdraw
			case 3:
			{
				cout << "How do you want to find your account\n(1) Account ID\n(2) Account Holder Name" << endl;
				short f = 0;
				cin >> f;
				int c = 0;
				string e;
				switch (f)
				{
				case 1:
				{
					cout << "Enter Your Acc ID" << endl;
					cin >> c;
					break;
				}
				case 2:
				{
					cout << "Enter Account Holder Name" << endl;
					cin.ignore();
					getline(cin, e);
					//exp
					ifstream file;
					file.open("input.txt", ios::binary | ios::app | ios::in);
					short d = 0;
					file.seekg(0);
					acc b;
					while (!file.eof())
					{
						file.read((char*)(&b), sizeof(b));
						if (file.tellg() == -1)
						{
							continue;
						}
						if (b.getID() == c || b.getname() == e)
						{
							d++;
						}
					}
					if (d > 1)
					{
						cout << "Multiple records found please enter Acc ID" << endl;
						system("pause");
						exit(0);
					}
					else if (d == 0)
					{
						cout << "No record found" << endl;
						system("pause");
						exit(0);
					}
					file.close();
					//end of exp
					break;
				}
				default:
				{
					cout << "Invalid choice" << endl;
					break;
				}
				}
				fstream file6;
				file6.open("input.txt", ios::binary | ios::in | ios::out); short d = 0;
				file6.seekg(0);
				acc b;
				while (!file6.eof())
				{
					file6.read((char*)(&b), sizeof(b));
					if (file6.tellg() == -1)
					{
						cout << "Problem run" << endl;
						continue;
					}
					if (b.getID() == c || b.getname() == e )
					{
						d++;
						cout << "ID:\t" << b.getID() << endl << "Name\t" << b.getname() << endl;
						cout << "Balance\t" << b.getbalance() << endl << "Type\t" << b.gettype() << endl << "Address\t" << b.getaddress() << endl;
						cout << "-----------------------------------------------------------------------------------------------------" << endl;
						int g;
						cout << "How much do you want to withdraw" << endl;
						cin.ignore();
						cin >> g;
						if (g > b.getbalance())
						{
							cout << " You don't have enough balance and your transaction cannot be processed " << endl;
							file6.close();
							break;
						}
						else if (g <= b.getbalance() && g > 0)
						{
							b.balance = b.balance - g;
							file6.seekp(-72, ios::cur);
							file6.write((char*)&b, sizeof(b));
							cout << "Record updated" << endl;
							file6.close();
							break;
						}
						else
						{
							cout << "Invalid Value" << endl;
						}
					}
				}
				file6.close();
				break;
			}
			//Account Details
			case 4:
			{
				cout << "How do you want to find your account\n(1) Account ID\n(2) Account Holder Name" << endl;
				short f = 0;
				cin >> f;
				int c = 0;
				string e;
				switch (f)
				{
				case 1:
				{
					cout << "Enter Your Acc ID" << endl;
					cin >> c;
					break;
				}
				case 2:
				{
					cout << "Enter Account Holder Name" << endl;
					cin.ignore();
					getline(cin, e);
					//exp
					ifstream file;
					file.open("input.txt", ios::binary | ios::app | ios::in); short d = 0;
					file.seekg(0);
					acc b;
					while (!file.eof())
					{
						file.read((char*)(&b), sizeof(b));
						if (file.tellg() == -1)
						{
							continue;
						}
						if (b.getID() == c || b.getname() == e)
						{
							d++;
						}
					}
					if (d > 1)
					{
						cout << "Multiple records found please enter Acc ID" << endl;
						system("pause");
						file.close();
						exit(0);
					}
					else if (d == 0)
					{
						cout << "No record found" << endl;
						system("pause");
						exit(0);
					}
					file.close();
					break;
				}
				default:
				{
					cout << "Invalid choice" << endl;
					break;
				}
				}
				
				ifstream file;
				file.open("input.txt", ios::binary | ios::app | ios::in);
				short d = 0;
				file.seekg(0);
				acc b;
				if (file.is_open())
				{
					cout << "file is open" << endl;
				}
				else { cout << "Failed file opening"; }
				while (!file.eof())
				{
					file.read((char*)(&b), sizeof(b));
					if (file.tellg() == -1)
					{
						continue;
					}
					if (b.getID() == c || b.getname() == e)
					{
						d++;
						cout << "ID:\t" << b.getID() << endl << "Name\t" << b.getname() << endl;
						cout << "Balance\t" << b.getbalance() << endl << "Type\t" << b.gettype() << endl << "Address\t" << b.getaddress() << endl;
						cout << "-----------------------------------------------------------------------------------------------------" << endl;
					}
				}
				ifstream file2;
				file2.open("cards.txt");
				card a;
				if (file2.is_open())
				{
					cout << "File successfully opened" << endl;
				}
				else {
					cout << "Failed to open file" << endl;
				}
				file2.seekg(0);
				short z = 0;
				while (!file2.eof())
				{
					if (file2.tellg() == -1)
					{
						continue;
					}

					file2.read((char*)&a, sizeof(a));
					if (z==0)
					{ 
					if (b.getID() == a.getID())
					{
						z++;
						cout << endl << "Card Details" << endl;
						cout << "Card Number:\t " << a.getcardno() << endl << "CVC Number:\t" << a.getcvcno() << endl;
						cout << "Issue Date:\t" << a.getissdate() << endl << "exp date:\t" << a.getexpdate() << endl;
						cout << "---------------------------------------------------------------------------------------" << endl;
					}
					}
				}
				file2.close();

				file.close();
				break;
			}
			}//end switch 2
			break;
		}
		//exit 
		case 3: {
			system("pause");
			system("cls");
			i = 1;
			break;
		}
			  //main default
		default: {
			system("cls");
			cout << "Invalid choice" << endl;
			break;
		}
		}
	}
	ending();
	return 0;
}
