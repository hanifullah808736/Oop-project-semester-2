
#include <iostream>
#include <string>

using namespace std;

class LibraryItem {
protected:
    string title;

public:
    LibraryItem(const string& title) : title(title) {}

    const string& getTitle() const { return title; }
    virtual void display() const = 0;
};

class Book : public LibraryItem {
private:
    string author;
    string genre;
    bool isAvailable;

public:
    Book(const string& title, const string& author, const string& genre)
        : LibraryItem(title), author(author), genre(genre), isAvailable(true) {}

    void display() const override {
        cout << "\nBook details:\n";
        cout << "Title: " << title << endl;
        cout << "Author: " << author << endl;
        cout << "Genre: " << genre << endl;
        cout << "Status: " << (isAvailable ? "Available" : "Not Available") << endl;
    }

    void setAvailability(bool available) { isAvailable = available; }
};

class Borrower {
private:
    string name;
    string address;
    string contact;

public:
    Borrower(const string& name, const string& address, const string& contact)
        : name(name), address(address), contact(contact) {}

    const string& getName() const { return name; }

    void display() const {
        cout << "\nBorrower details:\n";
        cout << "Name: " << name << endl;
        cout << "Address: " << address << endl;
        cout << "Contact: " << contact << endl;
    }
};

class Library {
private:
    static const int MAX_BOOKS = 100;
    static const int MAX_BORROWERS = 100;
    Book* books[MAX_BOOKS];
    Borrower* borrowers[MAX_BORROWERS];
    int numBooks;
    int numBorrowers;

public:
    Library() : numBooks(0), numBorrowers(0) {}

    void addBook(Book* book) {
        if (numBooks < MAX_BOOKS) {
            books[numBooks++] = book;
            cout << "Book added successfully.\n";
        } else {
            cout << "Cannot add more books. Library is full.\n";
        }
    }

    void deleteBook(const string& title) {
        bool found = false;
        for (int i = 0; i < numBooks; ++i) {
            if (books[i]->getTitle() == title) {
                found = true;
                delete books[i];
                books[i] = books[numBooks - 1];
                --numBooks;
                cout << "Book deleted successfully.\n";
                break;
            }
        }
        if (!found) {
            cout << "Book not found.\n";
        }
    }

    void searchBook(const string& title) const {
        bool found = false;
        for (int i = 0; i < numBooks; ++i) {
            if (books[i]->getTitle() == title) {
                found = true;
                books[i]->display();
                break;
            }
        }
        if (!found) {
            cout << "Book not found.\n";
        }
    }

    void addBorrower(Borrower* borrower) {
        if (numBorrowers < MAX_BORROWERS) {
            borrowers[numBorrowers++] = borrower;
            cout << "Borrower added successfully.\n";
        } else {
            cout << "Cannot add more borrowers. Borrower list is full.\n";
        }
    }

    void deleteBorrower(const string& name) {
        bool found = false;
        for (int i = 0; i < numBorrowers; ++i) {
            if (borrowers[i]->getName() == name) {
                found = true;
                delete borrowers[i];
                borrowers[i] = borrowers[numBorrowers - 1];
                --numBorrowers;
                cout << "Borrower deleted successfully.\n";
                break;
            }
        }
        if (!found) {
            cout << "Borrower not found.\n";
        }
    }

    void searchBorrower(const string& name) const {
        bool found = false;
        for (int i = 0; i < numBorrowers; ++i) {
            if (borrowers[i]->getName() == name) {
                found = true;
                borrowers[i]->display();
                break;
            }
        }
        if (!found) {
            cout << "Borrower not found.\n";
        }
    }
};

int main() {
    Library library;

    while (true) {
        cout << "\n=== Library Management System ===\n";
        cout << "1. Add new book\n";
        cout << "2. Delete book\n";
        cout << "3. Search book by title\n";
        cout << "4. Add new borrower\n";
        cout << "5. Delete borrower\n";
        cout << "6. Search borrower by name\n";
        cout << "7. Exit\n";
        cout << "Enter your choice: ";

        int choice;
        cin >> choice;
        cin.ignore(); // clear newline from input buffer

        switch (choice) {
            case 1: {
                string title, author, genre;
                cout << "Enter book title: ";
                getline(cin, title);
                cout << "Enter author: ";
                getline(cin, author);
                cout << "Enter genre: ";
                getline(cin, genre);

                library.addBook(new Book(title, author, genre));
                break;
            }
            case 2: {
                string title;
                cout << "Enter the title of the book to delete: ";
                getline(cin, title);
                library.deleteBook(title);
                break;
            }
            case 3: {
                string title;
                cout << "Enter the title of the book to search: ";
                getline(cin, title);
                library.searchBook(title);
                break;
            }
            case 4: {
                string name, address, contact;
                cout << "Enter borrower name: ";
                getline(cin, name);
                cout << "Enter address: ";
                getline(cin, address);
                cout << "Enter contact: ";
                getline(cin, contact);
                library.addBorrower(new Borrower(name, address, contact));
                break;
            }
            case 5: {
                string name;
                cout << "Enter the name of the borrower to delete: ";
                getline(cin, name);
                library.deleteBorrower(name);
                break;
            }
            case 6: {
                string name;
                cout << "Enter the name of the borrower to search: ";
                getline(cin, name);
                library.searchBorrower(name);
                break;
            }
            case 7:
                cout << "Exiting program.\n";
                return 0;
            default:
                cout << "Invalid choice. Please enter a valid option.\n";
        }
    }

    return 0;
}
