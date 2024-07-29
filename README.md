# First Grader Quiz 

## Table of Contents
1. [Introduction](#introduction)
2. [Features](#features)
3. [Technologies Used](#technologies-used)
4. [Vue.js 3 Topics covered](#vuejs-3-topics-covered)
5. [Installation](#installation)
6. [Usage](#usage)
7. [Screenshots](#screenshots)
8. [Project structure](#project-structure)
9. [Future Improvements](#future-improvements)
10. [Contact](#contact)

## Introduction

This is a quiz website for first graders covering several topics in subjects like Math, English and French. 

## Features

- The user can choose the number of questions (5, 10 or 15).
- Feedback on answers.
- Supports multiple subjects and question categories.
- Responsive design for different screen sizes.

## Technologies Used

- Vue.js 3 with Composition API
- Quasar Framework
- JavaScript
- HTML5 & CSS3
- Vue Router

## Vue.js 3 Topics Covered

- **Reactive Properties:** Using 'ref' for state management.
- **Computed Properties:** Creating derived state with 'computed'.
- **Two-way data binding:** Using 'v-model' for two-way data binding.
- **Watchers:** Responding to changes in reactive properties with 'watch'.
- **Lifecycle Hooks:** Managing component lifecycle with hooks like 'onMounted'.
- **Props and Emits:** Passing data and events between components with 'props' and 'emit'.
- **Routing:** Implementing navigation using Vue Router.
- **Conditional Rendering:** Displaying elements conditionally using 'v-if'.
- **List Rendering:** Rendering lists of elements with 'v-for'.

## Installation

To run this project locally, follow these steps:

1. Clone the repository:
```bash
git clone https://github.com/Pushtika/First-Grader-Quiz-Vuejs.git
cd First-Grader-Quiz-Vuejs
```
2. Install dependencies:
```bash
npm install
```
3. Start the development server:
```bash
quasar dev
```

## Usage

1. Select the number of questions using the dropdown menu.
2. Answer the questions displayed on the screen.
3. Click the "Submit" button to see your results.
4. Use the "Go back" button to return to the main menu and choose a different quiz.

## Screenshots
![image](https://github.com/user-attachments/assets/05fb4062-7aec-4eb6-900e-7f997f903172)
![image](https://github.com/user-attachments/assets/8f85af3a-6a1a-4b03-9cbb-574047b64058)
![image](https://github.com/user-attachments/assets/db9f9296-4ff7-4daf-8ac6-5ecd5b5c3a27)
![image](https://github.com/user-attachments/assets/75659442-9133-4346-87a2-509c30139af1)


## Project Structure

- `src/`
  - `components/` - Vue components like TabView, Categories, Quiz and Question.
  - `data/` - JSON data files, one for each subject.
  - `pages/` - Page components.
  - `App.vue` - Root component.
  - `main.js`- Application entry point.
 
## Future Improvements

- Add more subjects and question categories.
- Implement a timer.
- Use Pinia for state management.

## Contact

Feel free to reach out if you have any questions or want to discuss this project further.

* Email: pushtikareesaul@gmail.com
* LinkedIn: https://www.linkedin.com/in/pushtika-reesaul/
