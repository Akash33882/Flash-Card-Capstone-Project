# 🇫🇷 Flashy – French Vocabulary Flashcard App

A simple and interactive **French-to-English flashcard learning application** built with **Python, Tkinter, and Pandas**.

The app displays French words on flashcards, automatically flips them to reveal their English meanings after 3 seconds, and allows users to mark words they already know. Known words are removed from future practice sessions and saved automatically.

## 📸 Preview

> A desktop flashcard application with a clean card-based interface for learning French vocabulary.

---

## ✨ Features

* 🇫🇷 Displays French vocabulary words
* 🇬🇧 Automatically reveals the English translation
* ⏱️ Flashcards flip automatically after **3 seconds**
* ❌ **Unknown button** skips to another word
* ✅ **Known button** removes the word from the learning list
* 💾 Automatically saves learned words
* 🔄 Continues learning only the remaining words
* 📊 Uses Pandas for CSV data management
* 🖥️ Simple graphical interface using Tkinter

---

## 🛠️ Technologies Used

| Technology  | Purpose                              |
| ----------- | ------------------------------------ |
| 🐍 Python   | Main programming language            |
| 🖼️ Tkinter | Graphical User Interface             |
| 🐼 Pandas   | Reading and updating vocabulary data |
| 🎲 Random   | Selecting random flashcards          |
| 📄 CSV      | Storing vocabulary data              |

---

## 📂 Project Structure

```text
Flashy/
│
├── main.py
│
├── data/
│   ├── french_words.csv
│   └── words_to_learn.csv
│
├── images/
│   ├── card_front.png
│   ├── card_back.png
│   ├── right.png
│   └── wrong.png
│
└── README.md
```

### Files & Folders

**`main.py`**
Contains the main application logic and Tkinter user interface.

**`data/french_words.csv`**
Contains the original French-English vocabulary list.

**`data/words_to_learn.csv`**
Stores the vocabulary words that the user has not learned yet. This file is created automatically after marking words as known.

**`images/`**
Contains the flashcard backgrounds and button images.

---

## 🚀 How to Run

### 1. Clone the Repository

```bash
git clone https://github.com/YOUR-USERNAME/YOUR-REPOSITORY.git
```

### 2. Open the Project

```bash
cd YOUR-REPOSITORY
```

### 3. Install Dependencies

Make sure Python is installed on your computer.

Install Pandas:

```bash
pip install pandas
```

> Tkinter is included with most standard Python installations. On some Linux distributions, you may need to install it separately.

### 4. Run the Application

```bash
python main.py
```

---

## 🎮 How to Use

1. Start the application.
2. A French word appears on the flashcard.
3. Wait **3 seconds**.
4. The card automatically flips and displays the English translation.
5. Click:

   * ❌ **Wrong** – You don't know the word, so it remains in the learning list.
   * ✅ **Right** – You know the word, so it is removed from the learning list.
6. Continue practicing until you become familiar with the vocabulary.

---

## 🧠 How It Works

The application first checks whether `words_to_learn.csv` exists.

```python
try:
    data = pandas.read_csv("data/words_to_learn.csv")
except FileNotFoundError:
    original_data = pandas.read_csv("data/french_words.csv")
    to_learn = original_data.to_dict(orient="records")
else:
    to_learn = data.to_dict(orient="records")
```

If the learning file does not exist, the application loads the original vocabulary.

If it already exists, the application continues from the user's previous progress.

### Flashcard Selection

A random word is selected:

```python
current_card = random.choice(to_learn)
```

### Automatic Card Flip

The card flips after 3 seconds:

```python
flip_timer = window.after(3000, func=flip_card)
```

### Saving Learned Words

When the user clicks the ✅ button, the current word is removed and the remaining words are saved:

```python
to_learn.remove(current_card)

data = pandas.DataFrame(to_learn)
data.to_csv("data/words_to_learn.csv", index=False)
```

This allows learning progress to persist between sessions.

---

## 🎯 Learning Objectives

This project demonstrates practical use of:

* Python functions
* Global variables
* Tkinter GUI development
* Event-driven programming
* `after()` timers
* Pandas DataFrames
* CSV file handling
* Dictionaries and lists
* Exception handling
* Random selection
* Basic application state management

---

## 🔮 Future Improvements

Possible improvements include:

* 🌍 Support for multiple languages
* 🔊 French pronunciation/audio
* 📈 Learning progress statistics
* 🔥 Daily learning streak
* 🎯 Difficulty levels
* 🔍 Search vocabulary
* 📝 Add custom words
* 🌙 Dark mode
* 💾 Backup and restore progress
* 📊 Track learned vs. remaining words
* 🏆 XP and achievement system
* ⌨️ Keyboard shortcuts
* 🖥️ Improved responsive UI

---

## 🐛 Troubleshooting

### `FileNotFoundError`

Make sure your project has the required folders:

```text
data/
images/
```

and that the required files are inside them.

### Pandas is not installed

Run:

```bash
pip install pandas
```

### Images are not loading

Make sure the image paths match the project structure:

```text
images/card_front.png
images/card_back.png
images/right.png
images/wrong.png
```

---

## 👨‍💻 Author

**Akash**

Engineering Student | Python Developer | AI & Data Science Enthusiast

---

## ⭐ If You Like This Project

If you found this project useful or interesting, consider giving the repository a ⭐ on GitHub!

---

## 📜 License

This project is created for **learning and educational purposes**.
