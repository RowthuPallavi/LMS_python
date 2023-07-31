# LMS_python
Library Management System
class Book:
    def __init__(self, title, author, isbn):
        self.title = title
        self.author = author
        self.isbn = isbn
        self.is_borrowed = False

class Library:
    def __init__(self):
        self.books = []

    def add_book(self, book):
        self.books.append(book)

    def display_books(self):
        for book in self.books:
            status = "Available" if not book.is_borrowed else "Borrowed"
            print(f"Title: {book.title}, Author: {book.author}, ISBN: {book.isbn}, Status: {status}")

    def find_book_by_title(self, title):
        for book in self.books:
            if book.title.lower() == title.lower():
                return book
        return None

    def borrow_book(self, title):
        book = self.find_book_by_title(title)
        if book is not None and not book.is_borrowed:
            book.is_borrowed = True
            print(f"{book.title} has been borrowed successfully.")
        elif book is not None and book.is_borrowed:
            print(f"{book.title} is already borrowed.")
        else:
            print("Book not found in the library.")

    def return_book(self, title):
        book = self.find_book_by_title(title)
        if book is not None and book.is_borrowed:
            book.is_borrowed = False
            print(f"{book.title} has been returned successfully.")
        elif book is not None and not book.is_borrowed:
            print(f"{book.title} is already in the library.")
        else:
            print("Book not found in the library.")
