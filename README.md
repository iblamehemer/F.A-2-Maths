# F.A-2-Maths
import tkinter as tk
import math

class ScientificCalculator:
    def __init__(self, root):
        self.root = root
        self.root.title("Scientific Calculator")
        self.root.geometry("400x600")
        self.root.configure(background='black')
        
        self.equation = ""
        
        # Entry Widget
        self.result_var = tk.StringVar()
        self.result_display = tk.Entry(root, textvariable=self.result_var, font=("Arial", 20), bg="black", fg="white", bd=10, relief=tk.RIDGE, justify=tk.RIGHT)
        self.result_display.grid(row=0, column=0, columnspan=5, ipadx=8, ipady=15, pady=10)
        
        # Button Layout
        buttons = [
            ('7', 1, 0), ('8', 1, 1), ('9', 1, 2), ('/', 1, 3), ('C', 1, 4),
            ('4', 2, 0), ('5', 2, 1), ('6', 2, 2), ('*', 2, 3), ('√', 2, 4),
            ('1', 3, 0), ('2', 3, 1), ('3', 3, 2), ('-', 3, 3), ('^', 3, 4),
            ('0', 4, 0), ('.', 4, 1), ('+', 4, 2), ('=', 4, 3), ('(', 4, 4),
            ('sin', 5, 0), ('cos', 5, 1), ('tan', 5, 2), ('log', 5, 3), (')', 5, 4),
            ('ln', 6, 0), ('π', 6, 1), ('e', 6, 2), ('!', 6, 3), ('DEL', 6, 4)
        ]
        
        for (text, row, col) in buttons:
            tk.Button(root, text=text, font=("Arial", 16), bg="gray", fg="white", width=5, height=2, command=lambda t=text: self.on_button_click(t)).grid(row=row, column=col, padx=5, pady=5)
        
    def on_button_click(self, button_text):
        if button_text == "C":
            self.equation = ""
        elif button_text == "=":
            try:
                self.equation = str(eval(self.equation.replace("√", "math.sqrt").replace("^", "**").replace("π", "math.pi").replace("e", "math.e").replace("log", "math.log10").replace("ln", "math.log").replace("sin", "math.sin(math.radians").replace("cos", "math.cos(math.radians").replace("tan", "math.tan(math.radians").replace("!", "math.factorial")))
            except:
                self.equation = "Error"
        elif button_text == "DEL":
            self.equation = self.equation[:-1]
        else:
            self.equation += button_text
        
        self.result_var.set(self.equation)

if __name__ == "__main__":
    root = tk.Tk()
    calc = ScientificCalculator(root)
    root.mainloop()
