import os

# From here the todolist functions are starting

class ToDoList:
    def __init__(self):
        self.tasks = []

    def add_task(self, task):
        self.tasks.append({'task': task, 'done': False})
        print(f"Added task: '{task}'")

    def view_tasks(self):
        if not self.tasks:
            print("No tasks in the list.")
            return
        for i, task in enumerate(self.tasks, 1):
            status = "Done" if task['done'] else "Not Done"
            print(f"{i}. {task['task']} - {status}")

    def mark_task_done(self, task_number):
        if 0 < task_number <= len(self.tasks):
            self.tasks[task_number - 1]['done'] = True
            print(f"Marked task {task_number} as done.")
        else:
            print("Invalid task number.")

    def remove_task(self, task_number):
        if 0 < task_number <= len(self.tasks):
            removed_task = self.tasks.pop(task_number - 1)
            print(f"Removed task: '{removed_task['task']}'")
        else:
            print("Invalid task number.")

    def clear_screen(self):
        os.system('cls' if os.name == 'nt' else 'clear')

# The main function is define here        

def main():
    todo_list = ToDoList()
    while True:
        print("\nTo-Do List Application")
        print("1. Add Your Imporatant Task")
        print("2. View Your Tasks")
        print("3. Mark Task As You Done")
        print("4. Remove Your Completed Task")
        print("5. Clear Screen")
        print("6. Exit")
        choice = input("Select Your Option: ")

        if choice == '1':
            task = input("Enter the task: ")
            todo_list.add_task(task)
        elif choice == '2':
            todo_list.view_tasks()
        elif choice == '3':
            try:
                task_number = int(input("Enter task number to mark as done: "))
                todo_list.mark_task_done(task_number)
            except ValueError:
                print("Please enter a valid number.")
        elif choice == '4':
            try:
                task_number = int(input("Enter task number to remove: "))
                todo_list.remove_task(task_number)
            except ValueError:
                print("Please enter a valid number.")
        elif choice == '5':
            todo_list.clear_screen()
        elif choice == '6':
            print("Exiting the application.")
            break
        else:
            print("Invalid choice. Please try again.")

if __name__ == "__main__":
    main()

