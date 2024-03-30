Assume you oversee a small library and would like to develop a program that looks up books using their ISBNs. A list of books with their corresponding ISBN digits is in front of you. After the librarian inputs an ISBN, your software will look through the list to locate the relevant book.  The book's title and other details will be shown if the book is located. A notice stating that the book is not available in the library will appear if it cannot be located.
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
    obj.add("1000", "The Guide", "R.k.Narayan");
    obj.add("2000", "A Fine Balance", "Rohinton Mistry");
    obj.add("3000", "Mndnight children", "Salman Rushdie");
    
    string input_isbn;
    cout << "Enter ISBN: ";
    cin >> input_isbn;
    obj.display(input_isbn);
    
    return 0;
}

