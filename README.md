class Task:
    """Represents a single task"""
    def __init__(self, title, description, due_date):
        self.title = title
        self.description = description
        self.due_date = due_date
        self.completed = False
    def mark_completed(self):
        """Mark the task as completed"""
        self.completed = True
    def __str__(self):
        """Return a string representation of the task"""
        status = "Completed" if self.completed else "Not Completed"
        return f"{self.title}: {self.description} - Due: {self.due_date} - Status: {status}"
class ToDoList:
    """Represents a To-Do List"""
    def __init__(self):
        self.tasks = []
    def add_task(self, title, description, due_date):
        """Add a new task to the list"""
        task = Task(title, description, due_date)
        self.tasks.append(task)
    def view_tasks(self):
        """View all tasks in the list"""
        for i, task in enumerate(self.tasks, start=1):
            print(f"{i}. {task}")
    def delete_task(self, task_number):
        """Delete a task from the list"""
        try:
            del self.tasks[task_number - 1]
        except IndexError:
            print("Invalid task number.")
    def mark_task_completed(self, task_number):
        """Mark a task as completed"""
        try:
            task = self.tasks[task_number - 1]
            task.mark_completed()
        except IndexError:
            print("Invalid task number.")
def main():
    """Main application loop"""
    todo_list = ToDoList()
    while True:
        print("\nTo-Do List Menu:")
        print("1. Add Task")
        print("2. View Tasks")
        print("3. Delete Task")
        print("4. Mark Task Completed")
        print("5. Quit")
        choice = input("Enter your choice: ")
        if choice == "1":
            title = input("Enter task title: ")
            description = input("Enter task description: ")
            due_date = input("Enter task due date: ")
            todo_list.add_task(title, description, due_date)
        elif choice == "2":
            todo_list.view_tasks()
        elif choice == "3":
            task_number = int(input("Enter task number to delete: "))
            todo_list.delete_task(task_number)
        elif choice == "4":
            task_number = int(input("Enter task number to mark completed: "))
            todo_list.mark_task_completed(task_number)
        elif choice == "5":
            break
        else:
            print("Invalid choice. Please try again.")
if __name__ == "__main__":
    main()
