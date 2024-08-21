# 03
#include <iostream>
#include <fstream>
#include <vector>
#include <string>

using namespace std;

struct Contact {
    string name;
    string phone;
    string email;
};

// Function prototypes
void addContact(vector<Contact> &contacts);
void viewContacts(const vector<Contact> &contacts);
void deleteContact(vector<Contact> &contacts);
void saveContactsToFile(const vector<Contact> &contacts);
void loadContactsFromFile(vector<Contact> &contacts);

int main() {
    vector<Contact> contacts;
    int choice;

    // Load contacts from file
    loadContactsFromFile(contacts);

    do {
        cout << "\nContact Management System" << endl;
        cout << "1. Add New Contact" << endl;
        cout << "2. View Contacts" << endl;
        cout << "3. Delete Contact" << endl;
        cout << "4. Save and Exit" << endl;
        cout << "Enter your choice: ";
        cin >> choice;
        cin.ignore();  // Ignore newline character from previous input

        switch (choice) {
            case 1:
                addContact(contacts);
                break;
            case 2:
                viewContacts(contacts);
                break;
            case 3:
                deleteContact(contacts);
                break;
            case 4:
                saveContactsToFile(contacts);
                cout << "Contacts saved. Exiting the program." << endl;
                break;
            default:
                cout << "Invalid choice. Please try again." << endl;
        }
    } while (choice != 4);

    return 0;
}

void addContact(vector<Contact> &contacts) {
    Contact newContact;
    cout << "Enter name: ";
    getline(cin, newContact.name);
    cout << "Enter phone number: ";
    getline(cin, newContact.phone);
    cout << "Enter email: ";
    getline(cin, newContact.email);

    contacts.push_back(newContact);
    cout << "Contact added successfully!" << endl;
}

void viewContacts(const vector<Contact> &contacts) {
    if (contacts.empty()) {
        cout << "No contacts found." << endl;
    } else {
        for (size_t i = 0; i < contacts.size(); ++i) {
            cout << "\nContact " << i + 1 << ":" << endl;
            cout << "Name: " << contacts[i].name << endl;
            cout << "Phone: " << contacts[i].phone << endl;
            cout << "Email: " << contacts[i].email
