import tkinter as tk
from tkinter import messagebox
import random
quiz = [
    {
        "question": "What is the capital of France?",
        "options": ["Paris", "London", "Berlin", "Rome"],
        "answer": "Paris"
    },
    {
        "question": "Which planet is known as the Red Planet?",
        "options": ["Earth", "Mars", "Jupiter", "Saturn"],
        "answer": "Mars"
    },
    {
        "question": "Who was the first President of India?",
        "options": ["Jawaharlal Nehru", "Mahatma Gandhi", "Rajendra Prasad", "Sardar Patel"],
        "answer": "Rajendra Prasad"
    },
    {
        "question": "Which is the largest continent by area?",
        "options": ["Africa", "Asia", "Europe", "North America"],
        "answer": "Asia"
    },
    {
        "question": "Which planet is known as the 'Morning Star'?",
        "options": ["Mars", "Venus", "Jupiter", "Mercury"],
        "answer": "Venus"
    },
    {
        "question": "Who wrote the national anthem of India?",
        "options": ["Rabindranath Tagore", "Bankim Chandra Chatterjee", "Subhash Chandra Bose", "Sarojini Naidu"],
        "answer": "Rabindranath Tagore"
    },
    {
        "question": "Which is the longest river in the world?",
        "options": ["Amazon River", "Nile River", "Yangtze River", "Mississippi River"],
        "answer": "Nile River"
    },
    {
        "question": "Who is known as the Father of the Indian Constitution?",
        "options": ["Mahatma Gandhi", "B.R. Ambedkar", "Jawaharlal Nehru", "Sardar Patel"],
        "answer": "B.R. Ambedkar"
    },
    {
        "question": "Which Indian city is also known as the 'Silicon Valley of India'?",
        "options": ["Mumbai", "Hyderabad", "Bangalore", "Pune"],
        "answer": "Bangalore"
    },
    {
        "question": "In which year did India gain independence from British rule?",
        "options": ["1945", "1946", "1947", "1948"],
        "answer": "1947"
    },
    {
        "question": "Which is the smallest country in the world by area?",
        "options": ["Monaco", "Vatican City", "Nauru", "San Marino"],
        "answer": "Vatican City"
    },
    {
        "question": "What is the capital of Japan?",
        "options": ["Kyoto", "Osaka", "Tokyo", "Hiroshima"],
        "answer": "Tokyo"

    }
    


]
class QuizApp:
    def __init__(self, root):
        self.root = root
        self.root.title("Quiz Application")
        self.root.configure(bg="skyblue")  # Background color of the window
        
        # to Shuffle the quiz questions
        random.shuffle(quiz)
        
        self.score = 0
        self.current_question = 0

        # Create UI elements
        self.question_label = tk.Label(
            root, 
            text=quiz[self.current_question]["question"], 
            font=("Arial", 14), 
            bg="lightblue",  # Background color of the question label
            fg="darkblue"    # Text color of the question label
        )
        self.question_label.pack(pady=20)

        self.var = tk.StringVar()

        self.option_buttons = []
        for i in range(4):
            btn = tk.Radiobutton(
                root, 
                text="", 
                variable=self.var, 
                value="", 
                font=("Arial", 12),
                bg="lightyellow",  # Background color of the option buttons
                fg="black",        # Text color of the option buttons
                activebackground="yellow",  # Background color when the button is active
                activeforeground="blue"     # Text color when the button is active
            )
            btn.pack(anchor="w", pady=10)
            self.option_buttons.append(btn)

        self.next_button = tk.Button(
            root, 
            text="Next", 
            command=self.next_question, 
            bg="green",      # Background color of the Next button
            fg="white",      # Text color of the Next button
            activebackground="darkgreen",  # Background color when the button is active
            activeforeground="grey"       # Text color when the button is active
        )
        self.next_button.pack(pady=20)

        self.update_question()

    def update_question(self):
        self.question_label.config(text=quiz[self.current_question]["question"])
        options = quiz[self.current_question]["options"]
        self.var.set(None)

        for i in range(4):
            self.option_buttons[i].config(text=options[i], value=options[i])

    def next_question(self):
        if self.var.get() == "":
            messagebox.showwarning("Warning", "Please select an option.")
            return

        if self.var.get() == quiz[self.current_question]["answer"]:
            self.score += 1

        self.current_question += 1

        if self.current_question == len(quiz):
            self.show_result()
        else:
            self.update_question()

    def show_result(self):
        messagebox.showinfo("Result", f"Your Score: {self.score}/{len(quiz)}")
        self.root.quit()
if __name__ == "__main__":
    root = tk.Tk()
    app = QuizApp(root)
    root.mainloop()
    


