# VueQuest

VueQuest is an interactive quiz application built with Vue.js, TypeScript, and Pico.css. The app allows users to test their knowledge on various topics by answering a series of multiple-choice questions.

## Features

- **Structured Layout**: A clear user interface with a custom `Layout.vue` featuring a header, main content, and footer.
- **State Management**: Handles loading, error, and quiz display states.
- **Interactive Quiz**: Dynamically displays questions, tracks user answers, and shows the final score.
- **Dark Theme**: The design is optimized for a dark theme using Pico.css.
- **Shuffle Functionality**: Randomizes the answer choices for each question using a `shuffleArray` utility function.

## Component Structure

1. **`Layout.vue`**: Manages the overall structure of the app with a header, main content, and footer.
2. **`Quiz.vue`**: The main component that displays the quiz, manages questions, and navigates through steps.
3. **`Progress.vue`**: Displays the user's progress through the quiz questions.
4. **`Question.vue`**: Shows a single question with its choices and handles answer selection.
5. **`Answer.vue`**: Handles the display and selection of an individual answer, showing whether it is correct or incorrect based on user input.
6. **`Recap.vue`**: Displays a summary of the results with the final score and a personalized message based on the outcome.

## Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/Cecile-Hirschauer/VueQuest.git
   
2. Navigate to the project directory:

```bash
cd vuequest
```
3. Install dependencies:

```bash
npm install
```
4. Start the development server:

```bash
npm run dev
```

### Usage
- **Loading the Quiz:** The quiz.json file is loaded from the public folder on component mount. If an error occurs, an error message is displayed to the user.
- **Answering Questions:** Users can select an answer for each question. Answers are stored and used to calculate the final score.
- **Viewing Results:** After answering all questions, a recap of the score is displayed with a success or failure message.
