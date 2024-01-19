---
layout: project
type: project
image: <div class="text-center p-4">
  <img width="200px" src="img/hotelmanagement/homepage.jpeg" class="img-thumbnail" >
</div>
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

Attatched at the bottom is the Customer class. Private member variables stores various customer information and two constructors are public. The default constructor initializes bookingID to -1 as an indication a room was added without a customer checked in. The constructor for checking in takes values for member variables and initializes them. There are numerous setters and getters to modify and retrieve values, respectively. In the greater context of the entire code, the Customer class has an instance as a member variable in the HotelManagement class. This allows communication between HotelManagement and Customer. 

This is a snippet the code:

```cpp

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
```
