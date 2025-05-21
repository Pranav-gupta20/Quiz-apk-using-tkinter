
🧠 Quiz Application using Python Tkinter
This is a multiple-choice quiz application built using Python's tkinter module. It displays general knowledge questions to the user, who can select one answer from four options. After answering all questions, the app shows the final score.

💡 Key Features:
User Interface:
Designed using tkinter, the GUI has a colorful layout with questions, options, and navigation.

Question Shuffling:
The questions are randomized using random.shuffle() each time the quiz is started.

Answer Selection:
Users select answers using radio buttons. A warning pops up if they try to proceed without choosing an option.

Score Calculation:
Each correct answer increases the score by one. At the end, the total score is shown using a message box.

Questions Included:
Topics include general knowledge, such as geography, history, and science.

🧩 How It Works:
Launch App: The main window is created with a title and background.

Display Questions: One question is shown at a time with four radio button options.

Next Button: Takes the user to the next question or shows the result when the quiz ends.

Final Result: A message box displays the score like Your Score: 7/12.

🛠️ Technologies Used:
tkinter – for GUI

random – to shuffle questions

messagebox – to show warnings and results

