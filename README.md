# My Simple To-Do List Application

## Project Summary
This project delivers a complete, functional, and user-friendly To-Do List web application. Designed as a single-page application (SPA), all its components—HTML structure, CSS styling, and JavaScript logic—are contained within a single `index.html` file. The application allows users to effortlessly add new tasks to a list and delete existing ones, providing a straightforward way to manage daily to-dos. It leverages external libraries via CDN for a modern and professional appearance, while maintaining a lean codebase.

## Setup Instructions
As a single-page application, setting up this To-Do List is incredibly simple, requiring no complex build steps or server configurations.

1.  **Save the file:** Copy the entire content provided for `index.html` and save it as `index.html` on your local machine.
2.  **Open in browser:** Navigate to the saved `index.html` file using your operating system's file explorer and open it with any modern web browser (e.g., Google Chrome, Mozilla Firefox, Microsoft Edge, Apple Safari).

    Alternatively, from your terminal:
    *   **macOS/Linux:** `open index.html`
    *   **Windows:** Double-click the `index.html` file or use `start index.html` in Command Prompt/PowerShell.

The application will load directly in your browser, ready for use.

## Usage Guide
The To-Do List application is designed for intuitive use:

### Adding a Task
1.  **Input Field:** Locate the text input field prominently displayed at the top, labeled with the placeholder "Add a new task...".
2.  **Type Task:** Enter the description of your task into this field.
3.  **Add:**
    *   Click the "Add Task" button located next to the input field, or
    *   Press the `Enter` key on your keyboard while the input field is active.
4.  The new task will instantly appear at the bottom of your To-Do list.

### Deleting a Task
1.  **Locate Task:** Find the task you wish to remove from your list.
2.  **Delete Button:** On the right side of each task item, you will see a small "×" (multiplication sign) button.
3.  **Confirm Deletion:** Click this "×" button. A confirmation dialog will pop up asking if you're sure you want to delete the task.
4.  **Action:** Click "OK" to permanently remove the task, or "Cancel" to keep it on the list.

## Code Explanation

### `index.html`
This file contains all the necessary HTML, CSS, and JavaScript for the application.

*   **HTML Structure**:
    *   The `<!DOCTYPE html>`, `<html>`, `<head>`, and `<body>` tags define the standard web page structure.
    *   Essential `<meta>` tags are included for character encoding and responsive design.
    *   A `<title>` tag provides the page title.
    *   The main application content is wrapped within a `div` with the class `todo-container`, which serves as a stylish card for the To-Do list.
    *   An `<h2>` tag displays the application's header.
    *   An `input-group` (Bootstrap component) contains a text `input` field (`#taskInput`) for entering tasks and an "Add Task" `button` (`#addTaskBtn`).
    *   An unordered list (`<ul>`) with the ID `taskList` is where all the To-Do items are dynamically rendered by JavaScript.

*   **CSS Styling (within `<style>` tags)**:
    *   **Bootstrap CDN**: The application uses Bootstrap 5's CSS framework, linked via a CDN, to provide a clean, modern, and responsive base design.
    *   **Custom CSS**: An inline `<style>` block contains additional CSS rules to fine-tune the appearance:
        *   `body` styling for font, background color, and layout (flexbox for centering).
        *   `.todo-container` styling for padding, border-radius, and a subtle `box-shadow` to give it a card-like appearance.
        *   Styling for `.todo-header`, `.input-group`, and `form-control:focus` to integrate with Bootstrap's aesthetics.
        *   `.list-group-item` rules define the look of individual task items, including spacing, borders, and hover effects.
        *   `.task-text` ensures the task description takes up most of the space and handles long words.
        *   `.btn-delete` is styled to be a small, unobtrusive "×" icon using Bootstrap's danger color, with a subtle opacity change on hover.
    *   **Data URI Example**: A `background-image` is applied to the `body` element using a `data:image/svg+xml` URI. This embeds a very subtle geometric pattern directly into the CSS, demonstrating how assets can be included without making additional HTTP requests.

*   **JavaScript Logic (within `<script>` tags)**:
    *   **Bootstrap JS CDN**: The Bootstrap 5 JavaScript bundle (including Popper.js) is included via a CDN. While not strictly necessary for the core To-Do logic, it's a best practice when using Bootstrap components that might require JS functionality.
    *   **DOM Element References**: JavaScript starts by getting references to the key HTML elements (`taskInput`, `addTaskBtn`, `taskList`) to interact with them.
    *   **`tasks` Array**: A global `let tasks = [];` array is used to store all the To-Do items as strings.
    *   **`renderTasks()` Function**:
        *   This function is responsible for updating the UI. It first clears the entire `taskList`.
        *   It then checks if the `tasks` array is empty; if so, it displays a friendly "No tasks yet!" message.
        *   Otherwise, it iterates through each `taskText` in the `tasks` array. For each task, it dynamically creates an `<li>` element, a `<span>` for the task text, and a `<button>` for deletion.
        *   An `onclick` event listener is attached to each delete button, calling `deleteTask(index)` with the specific task's index.
        *   Finally, the newly created `<li>` element is appended to the `taskList`.
    *   **`addTask()` Function**:
        *   Retrieves the value from `taskInput` and uses `.trim()` to remove leading/trailing whitespace.
        *   If the trimmed task text is not empty, it's added to the `tasks` array, the input field is cleared, and `renderTasks()` is called to update the display.
        *   An `alert()` provides feedback if an empty task is attempted to be added.
    *   **`deleteTask(index)` Function**:
        *   Accepts the `index` of the task to be deleted.
        *   It presents a `confirm()` dialog to the user for verification.
        *   If confirmed, it uses `tasks.splice(index, 1)` to remove the task from the array.
        *   `renderTasks()` is then called to refresh the UI, removing the deleted task from view.
    *   **Event Listeners**:
        *   An event listener is set up on `addTaskBtn` to call `addTask()` when clicked.
        *   Another event listener on `taskInput` triggers `addTask()` when the `Enter` key is pressed.
    *   **Initial Render**: `renderTasks()` is called once when the script loads to initialize the display (e.g., show the empty message if no tasks are present initially).

## License
This project is open-source and available under the MIT License.