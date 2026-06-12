# Beginner Explanatory Guide: Exercise 2: Navigating a Codebase

> **Task Type**: Service Task  
> **Domain/Focus**: Codebase Navigation, Python Fundamentals

---

## 1. The Goal (In-Depth Beginner Explanation)

### The Core Problem
In software development, understanding how to navigate a codebase is crucial for effective collaboration and efficient problem-solving. This exercise focuses on a mini project that simulates a task manager application, which is a common type of software used to manage tasks and their priorities. The core problem this task addresses is the need for developers to quickly orient themselves within a new codebase, especially when they are assigned to work on a sprint task. 

Currently, the task manager application has a few functionalities, such as adding tasks and marking them as complete. However, there are also areas that need improvement, such as handling duplicate task titles. By practicing the 3-minute orientation routine, developers can learn to identify the structure of the code, understand its components, and recognize areas that require attention, such as bugs or features that need to be implemented. This skill is essential for maintaining the software's quality and ensuring that users can effectively manage their tasks.

### Jargon Buster (Key Terms Explained)
* **Codebase**: A codebase is the collection of source code used to build a particular software application. It includes all the files and directories that contain the code, documentation, and resources needed to run the application. For example, in our task manager project, the codebase includes files like `taskManager.py` and `test_tasks.py`.

* **Entry Point**: The entry point of an application is the first piece of code that runs when the application starts. In Python applications, this is typically the main script that is executed. For instance, in our task manager, `taskManager.py` serves as the entry point where the main classes and functions are defined.

* **Markers**: Markers are comments in the code that indicate areas needing attention, such as `TODO`, `BUG`, or `FIXME`. These markers help developers quickly identify parts of the code that require further work or debugging. For example, in `taskManager.py`, there is a `BUG` marker indicating that the code does not check for duplicate task titles when adding a new task.

* **Test Cases**: Test cases are specific scenarios used to verify that a piece of code behaves as expected. They are essential for ensuring that the application functions correctly and helps catch bugs early. In our project, `test_tasks.py` contains test cases that check if tasks can be added successfully.

### Expected Outcome
After completing this exercise, you should be able to navigate the codebase of the task manager application confidently. You will understand the structure of the project, identify the key components such as classes and methods, and recognize areas that need improvement. 

**Before vs. After**:
- **Before**: A developer may feel lost in the codebase, unsure of where to find specific functionalities or how to address existing issues.
- **After**: A developer can quickly locate the main components of the application, understand their purpose, and identify tasks that need to be addressed, such as fixing bugs or adding new features.

---

## 2. Related Coding Concepts & Syntax (50% Theory, 50% Practice)

### Concept 1: Classes and Objects in Python
#### 📘 Theoretical Overview (50%)
* **Why it exists**: Classes and objects are fundamental concepts in object-oriented programming (OOP). A class is a blueprint for creating objects, which are instances of that class. This allows developers to model real-world entities and their behaviors in code. Without classes, code would be less organized and harder to manage, especially in larger applications.

* **Key Mechanisms**: In Python, a class is defined using the `class` keyword, followed by the class name. Inside a class, you can define attributes (variables) and methods (functions) that describe the behavior of the objects created from the class. For example, the `Task` class in our project has attributes like `title` and `priority`, and methods like `complete()` that define what a task can do.

#### 💻 Syntax & Practical Examples (50%)
* **Language Syntax**:
  ```python
  class ClassName:
      def __init__(self, parameters):
          # Constructor method to initialize attributes
          self.attribute = parameters

      def method_name(self):
          # Method to define behavior
          pass
  ```

* **Real-World Application**:
  ```python
  class Task:
      def __init__(self, title, priority='medium'):
          self.title = title
          self.priority = priority
          self.done = False

      def complete(self):
          self.done = True
  ```

In this example, the `Task` class has a constructor that initializes the task's title and priority, and a method `complete()` that marks the task as done.

---

## 3. Step-by-Step Logic & Walkthrough

1. **Step 1: Locate and Analyze the Target File**
   * Navigate to the `sample_project/src/` directory and open the `taskManager.py` file. This file contains the main logic for the task manager application.
   * Focus on the first 20 lines to identify the classes defined, which are `Task` and `TaskManager`.

2. **Step 2: Input Verification & Validation**
   * Check the `add` method in the `TaskManager` class for input validation. Currently, it does not check for duplicate task titles, which is a potential bug.

3. **Step 3: Core Implementation / Modification**
   * Modify the `add` method to include a check for duplicate titles before adding a new task. This can be done by iterating through the existing tasks and comparing their titles with the new title.

4. **Step 4: Output Verification & Testing**
   * After implementing the changes, run the test cases in `test_tasks.py` to ensure that the application behaves as expected. You can use the command `pytest test_tasks.py` to execute the tests.

---

## 4. Detailed Walkthrough of Test Cases

### Test Case 1: Standard / Success Case
* **Description**: This test checks if a task can be added successfully to the task manager.
* **Inputs**:
  ```json
  {
    "title": "Write tests",
    "priority": "medium"
  }
  ```
* **Step-by-Step Execution Trace**:
  1. The `add` method is called with the title "Write tests".
  2. The method checks if the title already exists in the `tasks` list (this is where the new validation logic would be added).
  3. Since the title is unique, a new `Task` object is created and added to the `tasks` list.
  4. The length of `tasks` is now 1, confirming that the task was added successfully.
* **Expected Output**: The length of `tm.tasks` should be 1.

### Test Case 2: Edge Case / Validation Fail
* **Description**: This test checks the behavior when trying to add a task with a duplicate title.
* **Inputs**:
  ```json
  {
    "title": "Write tests",
    "priority": "medium"
  }
  ```
* **Step-by-Step Execution Trace**:
  1. The `add` method is called with the title "Write tests" for the first time, and it is added successfully.
  2. The `add` method is called again with the same title "Write tests".
  3. The method checks for duplicates and finds that the title already exists in the `tasks` list.
  4. The method does not add the task again and returns an appropriate message or value indicating the failure to add a duplicate task.
* **Expected Output**: The length of `tm.tasks` should remain 1, and an error message should indicate that the task could not be added due to a duplicate title.