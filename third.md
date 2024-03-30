#include <iostream>
#include <string>
#include <unordered_map>
using namespace std;

class Library {
private:
    struct Book {
        string title;
        string author;
        string isbn;
    };
    unordered_map<string, Book> books;
public:
    void add(string isbn, string title, string author) {
        Book book;
        book.title = title;
        book.author = author;
        book.isbn = isbn;
        books[isbn] = book;
    }

    void display(string isbn) {
        auto it = books.find(isbn);
        if (it != books.end()) {
            cout << "Book found:" << endl;
            cout << "Title: " << it->second.title << endl;
            cout << "Author: " << it->second.author << endl;
        } else {
            cout << "Book not found in the library." << endl;
        }
    }
};

int main() {
    Library obj;
    obj.add("10", "The InterPerter Of Maladies", "Jhumpa Lahiri");
    obj.add("20", "The Inheritance of Loss", "Kiran Desai");
    obj.add("30", "Red Earth and Pouring Rain", "Vikram chandra");
    
    string input_isbn;
    cout << "Enter ISBN: ";
    cin >> input_isbn;
    obj.display(input_isbn);
    
    return 0;
}

}

