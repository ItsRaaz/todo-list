# todo-list
Create a simple Todo list with vanilla JS (as you see in the GIF below). Vanilla JS means no plugins, no libraries, nothing.  Refer to the question doc for more details:

**#HTML:**
<!DOCTYPE html>
<html>
<head>
  <title>Todo List</title>
</head>
<body>
  <h1>Todo List</h1>
  <input id="todoInput" type="text" placeholder="Enter a new task">
  <button id="addButton">Add</button>
  <ul id="todoList"></ul>

  <script src="script.js"></script>
</body>
</html>

**#JAVASCRIPT:**
// Get elements from the DOM
const todoInput = document.getElementById("todoInput");
const addButton = document.getElementById("addButton");
const todoList = document.getElementById("todoList");

// Function to add a new task
function addTask() {
  const taskText = todoInput.value.trim();

  if (taskText !== "") {
    // Create a new list item
    const listItem = document.createElement("li");
    const taskLabel = document.createElement("span");
    taskLabel.textContent = taskText;
    const deleteButton = document.createElement("button");
    deleteButton.textContent = "Delete";

    // Add event listener to delete button
    deleteButton.addEventListener("click", function () {
      listItem.remove();
    });

    // Append elements to the list item
    listItem.appendChild(taskLabel);
    listItem.appendChild(deleteButton);

    // Append the list item to the todo list
    todoList.appendChild(listItem);

    // Clear the input field
    todoInput.value = "";
  }
}

// Add event listener to add button
addButton.addEventListener("click", addTask);

// Add event listener to input field for "Enter" key press
todoInput.addEventListener("keypress", function (event) {
  if (event.key === "Enter") {
    addTask();
  }
});
