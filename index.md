# ✨ Markdown exercise ✨
## Header
# 1. h1 header
## 2. h2 header
### 3. h3 header
#### 4. h4 header
##### 5. h5 header
###### 6. This is h6, the smallest header

## Adding an image
![Image of a laptop with graphs below](https://i.pinimg.com/564x/24/67/e9/2467e9cfebbdcb769d507968b1457380.jpg)

![Image of a notebook with a hand drawing a graph](https://i.pinimg.com/564x/9b/fc/57/9bfc57d18d9de4ce1fb6276ff0b0303e.jpg)

![Image of a hand pointing to a code written on the desktop screen](https://i.pinimg.com/564x/a6/61/74/a66174d1fa0db9149aa4e84f4e6418c8.jpg)

## Adding a code

### Simple calculator with basic operations + GUI
```
import tkinter as tk

class Calculator:
    def __init__(self, master):
        self.master = master
        master.title("Calculator")

        # Input boxes
        self.num1_label = tk.Label(master, text="First Number:")
        self.num1_label.grid(row=0, column=0)
        self.num1_entry = tk.Entry(master)
        self.num1_entry.grid(row=0, column=1)

        self.num2_label = tk.Label(master, text="Second Number:")
        self.num2_label.grid(row=1, column=0)
        self.num2_entry = tk.Entry(master)
        self.num2_entry.grid(row=1, column=1)

        # Operation buttons
        self.add_button = tk.Button(master, text="+", command=self.add)
        self.add_button.grid(row=2, column=0)

        self.subtract_button = tk.Button(master, text="-", command=self.subtract)
        self.subtract_button.grid(row=2, column=1)

        self.multiply_button = tk.Button(master, text="*", command=self.multiply)
        self.multiply_button.grid(row=3, column=0)

        self.divide_button = tk.Button(master, text="/", command=self.divide)
        self.divide_button.grid(row=3, column=1)

        # Output label
        self.result_label = tk.Label(master, text="")
        self.result_label.grid(row=4, column=0, columnspan=2)

    def add(self):
        try:
            num1 = float(self.num1_entry.get())
            num2 = float(self.num2_entry.get())
            result = num1 + num2
            self.result_label.config(text=result)
        except ValueError:
            self.result_label.config(text="Invalid input")

    def subtract(self):
        try:
            num1 = float(self.num1_entry.get())
            num2 = float(self.num2_entry.get())
            result = num1 - num2
            self.result_label.config(text=result)
        except ValueError:
            self.result_label.config(text="Invalid input")

    def multiply(self):
        try:
            num1 = float(self.num1_entry.get())
            num2 = float(self.num2_entry.get())
            result = num1 * num2
            self.result_label.config(text=result)
        except ValueError:
            self.result_label.config(text="Invalid input")

    def divide(self):
        try:
            num1 = float(self.num1_entry.get())
            num2 = float(self.num2_entry.get())
            if num2 == 0:
                self.result_label.config(text="Cannot divide by zero")
            else:
                result = num1 / num2
                self.result_label.config(text=result)
        except ValueError:
            self.result_label.config(text="Invalid input")

root = tk.Tk()
my_calculator = Calculator(root)
root.mainloop()
```

### To-do list with checkbox GUI
```
import tkinter as tk

class ToDoListGUI:
    def __init__(self):
        self.tasks = {}

        # Main window
        self.root = tk.Tk()
        self.root.title("Goal-getter")

        # Create the task entry field and add button
        self.task_entry = tk.Entry(self.root, width=30)
        self.task_entry.pack(side=tk.LEFT, padx=5, pady=5)
        self.add_button = tk.Button(self.root, text="Add", command=self.add_task)
        self.add_button.pack(side=tk.LEFT, padx=5, pady=5)

        # Create the remove button
        self.remove_button = tk.Button(self.root, text="Remove", command=self.remove_task)
        self.remove_button.pack(side=tk.LEFT, padx=5, pady=5)

        # Create the quit button
        self.quit_button = tk.Button(self.root, text="Quit", command=self.root.quit)
        self.quit_button.pack(side=tk.LEFT, padx=5, pady=5)

        # Create the task list frame
        self.task_frame = tk.Frame(self.root)
        self.task_frame.pack(side=tk.LEFT, padx=5, pady=5)

    def add_task(self):
        task = self.task_entry.get()
        if task:
            task_var = tk.BooleanVar()
            task_checkbox = tk.Checkbutton(self.task_frame, text=task, variable=task_var)
            task_checkbox.pack(side=tk.TOP, anchor=tk.W)
            self.tasks[task] = (task_checkbox, task_var)
            self.task_entry.delete(0, tk.END)

    def remove_task(self):
        for task in list(self.tasks.keys()):
            if self.tasks[task][1].get():
                self.tasks[task][0].destroy()
                del self.tasks[task]

    def run(self):
        self.root.mainloop()
```
```
todo_list_gui = ToDoListGUI()
todo_list_gui.run()
```
