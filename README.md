# Program of the Password_Generation with their various Features:
"""
Created on Sun Sep 17 13:05:55 2023

@author: DELL
"""
import tkinter as tk
from tkinter import messagebox
import random
import string

def generate_password():
    password_length = int(length_entry.get())
    if password_length < 8:
        messagebox.showwarning("Warning:", "Password length should be atleast 8 characters.")
        return

    characters = string.ascii_letters + string.digits + string.punctuation
    password = ''.join(random.choice(characters) for i in range(password_length))
    password_entry.delete(0, tk.END)
    password_entry.insert(0, password)

def copy_to_clipboard():
    password = password_entry.get()
    root.clipboard_clear()
    root.clipboard_append(password)
    messagebox.showinfo("Successfully", "Your Password is copied to clipboard !")

# Create the main application window
root = tk.Tk()
root.title("Password Generator by Chetan Dawani")
root.geometry('500x400')
root.resizable(10, 10)
root.config(bg="Blue")

# Create widgets
length_label = tk.Label(root, text="Password Length:", font=('Algerian', 14, 'bold'))
length_label.pack(pady=20)
length_entry = tk.Entry(root)
length_entry.pack(pady=28)

generate_button = tk.Button(root, text="Generate Password", command=generate_password, font=('Algerian', 14, 'bold'))
generate_button.pack(pady=20)

password_entry = tk.Entry(root, show="")
password_entry.pack(pady=20)

copy_button = tk.Button(root, text="Copy to your Clipboard", command=copy_to_clipboard, font=('Algerian', 14, 'bold'))
copy_button.pack(pady=40)

root.mainloop()
