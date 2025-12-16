# Library-_-Management-CPP
A simple Library Management System implemented in C++.

#include <iostream>
#include <string>
using namespace std;

const int size = 100;
string titles[size], authors[size];
bool available[size];
int countbooks = 0;

void addBook();
void searchBook();
void borrowBook();
void returnBook();
void displayBook();

int main() {
int choice ;
do{
cout << "Library menu:\n";
cout << "1. Add new book\n";
cout << "2. Search for a book\n";
cout << "3. Borrow a book\n";
cout << "4. Return a book\n";
cout << "5. Display all books\n";
cout << "6. Exit\n";
cout << "Enter choice: ";
cin >> choice;
switch (choice) {
case 1: addBook(); break;
case 2: searchBook(); break;
case 3: borrowBook(); break;
case 4: returnBook(); break;
case 5: displayBook(); break;
case 6: cout << "Exit\n"; break;
default: cout << "Invalid choice\n";
}} while (choice != 6);
return 0;}
void addBook() {
if (countbooks >= size) {
cout << "Library is Full\n";
return;}
cin.ignore();
cout << "Enter book title: ";
getline(cin, titles[countbooks]);
cout << "Enter author name: ";
getline(cin, authors[countbooks]);
available[countbooks] = true;
countbooks++;
cout << "Book added successfully!\n";}
void searchBook() {
string searchTitle;
cout << "Enter title to search: ";
cin.ignore();
getline(cin, searchTitle);
bool found = false;
for (int i = 0; i < countbooks; i++) {
if (titles[i] == searchTitle) {
cout << "Book found: " << titles[i] << " by " << authors[i]
<< " - " << (available[i] ? "Available" : "Not Available ") << endl; 
found = true;
break;}}
if (!found)
cout << "Book not found\n";}
void borrowBook() {
string title;
cout << "Enter title to borrow: ";
cin.ignore();
getline(cin, title);
for (int i = 0; i < countbooks; i++) {
if (titles[i] == title) {
if (available[i]) {
available[i] = false;
cout << "You borrowed: " << titles[i] << endl;
} else {
cout << "Book already borrowed\n";}
return;}}
cout << "Book not found\n";}
void returnBook() {
string title;
cout << "Enter title to return: ";
cin.ignore();getline(cin, title);
for (int i = 0; i < countbooks; i++) {
if (titles[i] == title) {
if (!available[i]) {
available[i] = true;
cout << "Book returned: " << titles[i] << endl;
} else 
{ cout << "This book was not borrowed\n";}
return;}}
cout << "Book not found\n";}
void displayBook() {
if (countbooks == 0) {
 cout << "No books in the library\n";
 return;}
cout << "Library book list:\n";
for (int i = 0; i < countbooks; i++) {
cout << i + 1 << ". " << titles[i] << " by " << authors[i]
<< " - " << (available[i] ? "Available" : "Not Available ") << endl;}}
    
