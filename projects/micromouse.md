---
layout: project
type: project
image: 
title: "Hotel Management System"
date: 2023
published: True
labels:
  - School Project
  - Group Project
  - Teamwork
  - C++
summary: "A C++ code my group members and I made in our ICS 212 class."
---
	
While my portfolio is still very fresh (like me), courses at my university offer opportunities to add to it. Among these opportunities was a simple hotel management system for my Program Structures class. I worked on this with a group of my peers- four other students -allowing me to experience coding in a team. Communication was key; our schedules did not necessarily align so we made most of class time and short gatherings in the university library. Workload was split fairly among the five of us: after working on a basic outline together, we each sculpted our own version and shared it with each other when we finished. From there, we compared our work and went with the code that worked the best for us after implementing pieces of our own work with it. Attatched to this website is the code I made prior to the deliberation but after my group and I put together a basic outline.



```cpp
/*
This program is a hotel management system that collects rooms and customer information.
class Customer is the collection of customer information that can be checked in or checked out of rooms.
class Room is the collection of room information.
class HotelManagement is an extension of class Room that associates a customer with a room.
class BookingSystem manages information in system that keeps track of all rooms. 

*/

#include <iostream>
#include <string.h>

using namespace std;

class Customer{
    //Variables
	private: 
		int bookingID;
		string name;
		string address;
        string phoneNum;
		string inDate;
		string outDate;
		double advance;

    public:
        //Default constructor. 
		Customer(){
			bookingID = -1; // -1 When a room is added without a customer checked in. 
		}
        //Constructor for check in. 
		Customer(int bookingID, string name, string address, 
		string phoneNum, string inDate, string outDate, double advance){
			this->bookingID = bookingID;
			this->name = name;
			this->address = address;
			this->phoneNum = phoneNum;
			this->inDate = inDate;
			this->outDate = outDate;
			this->advance = advance;
		}
        //Setters and getters.
		int getID(){
			return bookingID;
		}
		string getName(){
			return name;
		}
		string getAddress(){
			return address;
		}
		string getPhoneNum(){
			return phoneNum;
		}
		string getInDate(){
			return inDate;
		}
		string getOutDate(){
			return outDate;
		}
		double getAdvance(){
			return advance;
		}
		void setID(int bookingID){
			this->bookingID = bookingID;
		}
		void setName(string name){
			this->name = name;
		}
		void setAddress(string address){
			this->address = address;
		}
		void setPhoneNum(string phoneNum){
			this->phoneNum = phoneNum;
		}
		void setInDate(string inDate){
			this->inDate = inDate;
		}
		void setOutDate(string outDate){
			this->outDate = outDate;
		}
		void setAdvance(double advance){
			this->advance = advance;
		}
};

class Room{
    //Variables
	protected:
		int roomNum; 
        char ac; 
		char comfort;
		char size;
		double dailyRate;
        
    public: 
        //Default constructor
        Room(){
        }
        //Constructor for adding room 
        Room(int roomNum, char ac, char comfort, char size, double dailyRate){
			this->roomNum = roomNum;
			this->ac = ac;
			this->comfort = comfort;
			this->size = size;
			this->dailyRate = dailyRate;
		}
        //Getters
        int getRoomNum(){
			return roomNum;
		}
        char getAC(){
            return ac;
        }
        char getcomfort(){
            return comfort;
        }
        char getSize(){
            return size;
        }
        double getDailyRate(){
            return dailyRate;
        }
        //Display room info
        void displayRoom(){
			cout << "Room Number: " << roomNum << "\n";
			cout << "Room with AC/No AC (A/N): " << ac << "\n";
			cout << "Type of Comfort (S/N): " << comfort<< "\n";
			cout << "Room Size (B/S): " << size << "\n";
			cout << "Daily Rate: " << dailyRate << "\n";
	    }
        
};

class HotelManagement: public Room{
    //Variables
    protected:
        Customer customer; //Customer object of a room

    public:
        //Default Constructor
        HotelManagement(){
        }
        //Constructor that calls Room Constructor
        HotelManagement(int roomNum, char ac, char comfort, char size, double dailyRate)
        : Room(roomNum, ac, comfort, size, dailyRate) {
        }
        //Getters for customer info
        int getID(){ 
            return customer.getID();
        }
        string getName(){ 
            return customer.getName();
        }
        //Display customer info
        void displayCustomer(){
            cout << "Booking ID = " << customer.getID() << "\n";
            cout << "Address = " << customer.getAddress() << "\n";
            cout << "Phone number = " <<  customer.getPhoneNum() << "\n";
            cout << "Check in date = " << customer.getInDate() << "\n";
            cout << "Check out date = " << customer.getOutDate() << "\n";
            cout << "Advance = " << customer.getAdvance() <<  "\n";
        }
        //Display check out info
        void displayCheckout(int days){ //Param - number of days customer has been renting room
            cout << "Customer Name : " << customer.getName() << "\n";
            cout << "Room Number : " <<  roomNum << "\n";
            cout << "Address : " << customer.getAddress() << "\n";
            cout << "Phone : " << customer.getPhoneNum() << "\n";
            cout << "Total Amount Due : " << days * dailyRate << " /\n";
            cout << "Advance Paid: " << customer.getAdvance() << " /\n";   
            cout << "***Total Payable: " << days * dailyRate - customer.getAdvance() << "/ only\n";
        }
        //Adds customer to a room with info using constructor
        void addCust(int bookingID, string name, string address, 
        string phoneNum, string inDate, string outDate, double advance){
            customer = Customer(bookingID, name, address, phoneNum, inDate, outDate, advance);
        }
        //Clears customer with default constructor
        void clearCust(){
            customer = Customer();
        }
};

class BookingSystem{
    //Variables
    private:
        HotelManagement rooms[20]; //Array of rooms 
        int roomCount = 0; //Counter for number of rooms 

    public:
        //Default constructor
        BookingSystem(){
        } 
        //Adds Room to array
        void addRoom(){
            int roomNum; 
            char ac; 
            char comfort;
            char size;
            double dailyRate;
            //Collect room info from user
            cout << "Enter room number: ";
            cin >> roomNum;
            cout << "\nRoom with AC/No AC (A/N) : ";
            cin >> ac;
            cout << "\nType of Comfort (S/N) : ";
            cin >> comfort;
            cout << "\nRoom Size (B/S) : ";
            cin >> size;
            cout << "\nDaily Rate: ";
            cin >> dailyRate;
            //Add room if there is space in the array
            if(roomCount < 20){
                //Create new room object and increase room counter 
                rooms[roomCount++] = HotelManagement(roomNum, ac, comfort, size, dailyRate);
                cout << "\nRoom Added Successfully!\n";
            }
        }
        //Gets index of room in array
        int getIndex(){
            int roomNumber;
            cout << "Enter Room Number: "; // Collect room number from user
            cin >> roomNumber;
            int i; 
            // Search through array 
            for(i = 0; i < roomCount; i++){ 
                if(roomNumber == rooms[i].getRoomNum()){ // Check if user input matches room number of objects
                    return i; // Return index and break loop
                    break;
                }
            }
            return -1; // Return -1 if not found
        }
        // Search room with room number
        void searchRoom(){
            int i = getIndex(); // Prompt user to enter room number and get index of room number. 
            if(i>=0){ //If room exists then display room info
                cout << "Room Details\n\n";
                cout << "Room is  available\n";
                rooms[i].displayRoom();
            }
            else{ //Room not found if index is less than 0
                cout << "\nRoom not found\n";
            }
        }
        //Delete room by room number
        void deleteRoom(){
            int i = getIndex();// Prompt user to enter room number and get index of room number. 
            if(i >= 0){ //If room exists then delete room
                cout << "\nRoom Details to Delete\n\n";
                rooms[i].displayRoom(); // Display room info 
                rooms[i] = rooms[roomCount-1]; // Room is replaced by last existing room in array 
                roomCount--; // Decrement room count
                cout << "Room Deleted Successfully!";
            }
        }
        //Search rooms that don't have customers 
        void searchAvailable(){
            for(int i = 0; i < roomCount; i++){ //Loops through rooms and gets customer id
                if(rooms[i].getID() == -1) //Customer objects in rooms that have not checked in have a default value of -1
                    rooms[i].displayRoom(); //Compare values and display room info if there is no customer
            }
        }
        //Searches for customer by name
        void searchCustomer(){
            int i;
            string name;
            cout << "Enter Customer Name: "; // Collect name from user
            cin >> name;
            for(i = 0; i < roomCount; i++){ // Loops through rooms and compares names
                if(name == rooms[i].getName()){  //If it matches then display customer name and room number 
                    cout << "\nCustomer Name: " << name;
                    cout << "\nRoom Number: " << rooms[i].getRoomNum() << "\n";
                    break;
                }
            }
            // Person not found if index goes out of bounds
            if(i >= roomCount){
                cout << "\nPerson not found.";
            }
        }
        // Check in customer to existing room 
        void checkIn(){
            int i;
            //Customer variables to collect
            int roomNum;
            int bookingID;
            string name; 
            string address; 
            string phoneNum;
            string inDate;
            string outDate;
            double advance;
            
            cout << "\nEnter Room Number: "; // Collect room number from user
            cin >> roomNum;
            for(i = 0; i < roomCount; i++){ //Loop through rooms and match room number
                if(roomNum == rooms[i].getRoomNum()){ //If the room is found then collect booking info from user
                    cout << "\nEnter booking id: ";
                    cin >> bookingID;
                    cout << "\nEnter Customer Name (First Name): ";
                    cin >> name;
                    cout << "\nEnter Address (city only): ";
                    cin >> address;
                    cout << "\nEnter Phone: ";
                    cin >> phoneNum;
                    cout << "\nCheck-in Date: ";
                    cin >> inDate;
                    cout << "\nCheck-out Date: ";
                    cin >> outDate;
                    cout << "\nEnter Advance Payment: ";
                    cin >> advance;
                    cout << "\nCustomer Checked-in Successfully..\n";
                    //Add the customer to the room
                    rooms[i].addCust(bookingID, name, address, phoneNum, inDate, outDate, advance);
                }
            }   
        }
        //Checks out customer from associated room
        void checkOut(){
            int days; //Number of days renting room
            int i = getIndex(); // Get the index of room number 
            if(i >= 0){ 
                cout << "\nEnter Number of Days: "; //If it exists then collect number of days from user 
                cin >> days;
                cout << "\n######## CheckOut Details ########\n\n";
                rooms[i].displayCheckout(days); // Display check out details 
                rooms[i].clearCust(); // Clear customer by calling default customer constructor 
            }
        }
        //Displays all customer in rooms
        void summaryReport(){
            for(int i = 0; i < roomCount; i++){ // Loops through rooms and matches customer ID
                if(rooms[i].getID() != -1){  //Customer objects in rooms that have checked in don't have a default value of -1
                    rooms[i].displayCustomer(); //Display customer info
                }
            }
        }
};

int main() {

	BookingSystem booking; 

	int choice;
	bool menu = true;

    while(menu){
        cout << "\n######## Hotel Management #########\n";
        cout << "\n1. Manage Rooms";
        cout << "\n2. Check-In Room";
        cout << "\n3. Available Rooms";
        cout << "\n4. Search Customer";
        cout << "\n5. Check-Out Room";
        cout << "\n6. Guest Summary Report";
        cout << "\n7. Exit\n";
        cout << "\nEnter Option: ";
        cin >> choice;
        switch(choice){
            case 1:
				do{
					cout << "\n### Manage Rooms ###\n";
					cout << "1. Add Room\n";
					cout << "2. Search Room\n";
					cout << "3. Delete Room\n";
					cout << "4. Back to Main Menu\n";
                    cout << "\nEnter Option: ";
					cin >> choice;
                    cout << "\n";
					switch(choice){
						case 1:
						    booking.addRoom();
						    break;
						case 2:
						    booking.searchRoom();
						    break;
						case 3:
						    booking.deleteRoom();
						    break;
						case 4:
                            cout << "Going back to the main menu\n";
						    break;
						default:
						    cout << "\nPlease Enter correct option";
						    break;
					}
				}while(choice != 4);
                break;
        	case 2:
			    booking.checkIn();
 	            break;
            case 3:
			    booking.searchAvailable();
                break;
        	case 4:
			    booking.searchCustomer();
			    break;
            case 5:
			    booking.checkOut();
                break;
            case 6:
			    booking.summaryReport();
			    break;
            case 7:
			    cout << "\nTHANK YOU! FOR USING SOFTWARE\n";
			    menu = false;
			    break;
            default:
			    cout << "\nPlease Enter correct option";
			break;
        }
    } 
	return 0;
}
