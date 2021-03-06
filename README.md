# Tkinter
General Information about TKinter


https://datatofish.com/matplotlib-charts-tkinter-gui/ <br/>
https://datatofish.com/how-to-create-a-gui-in-python/ <br/>



https://www.datacamp.com/community/tutorials/gui-tkinter-python <br/>
https://docs.python.org/3/library/tk.html <br/>
https://datatofish.com/entry-box-tkinter/ <br/>
https://pythonspot.com/tkinter/ <br/>
https://www.tcl.tk/man/tcl8.6/TkCmd/contents.htm <br/>

### Ejemplos Tkinter con dataframe
https://songhuiming.github.io/pages/2016/05/13/tkinter-read-data-dropdown-menu-select-data-and-print-dataframe/
https://towardsdatascience.com/you-can-manage-cigars-with-tkinter-a2c39990e1b2


### Listbox


### Text Widget
The Text widget provides formatted text display. It allows you to display and edit text with various styles and attributes. The widget also supports embedded images and windows.
https://effbot.org/tkinterbook/text.htm
https://docs.python.org/2/library/tkinter.html
https://www.python-course.eu/tkinter_text_widget.php

### Entry Widget
The Entry widget is a standard Tkinter widget used to enter or display a single line of text.
https://effbot.org/tkinterbook/entry.htm
https://docs.python.org/2/library/tkinter.html

### Message box
https://pythonspot.com/tk-message-box/

from tkinter import messagebox
messagebox.showinfo("Title", "a Tk MessageBox")

showwarning()
showinfo()
showerror()

´´´
import tkinter
from tkinter import messagebox

# hide main window
root = tkinter.Tk()
root.withdraw()

# message box display
messagebox.showerror("Error", "Error message")
messagebox.showwarning("Warning","Warning message")
messagebox.showinfo("Information","Informative message")

´´´
### askquestion dialog
https://pythonspot.com/tkinter-askquestion-dialog/

´´´
import tkinter
from tkinter import messagebox
 
messagebox.askokcancel("Python","Would you like to save the data?")
´´´
´´´
import tkinter
from tkinter import messagebox
 
messagebox.askokcancel("Title","The application will be closed")
messagebox.askyesno("Title","Do you want to save?")
messagebox.askretrycancel("Title","Installation failed, try again?")
´´´





```python

import tkinter as tk
from matplotlib.backends.backend_tkagg import FigureCanvasTkAgg
from matplotlib.figure import Figure
 
root= tk.Tk()
  
canvas1 = tk.Canvas(root, width = 1000, height = 350)
canvas1.pack()
  
button1 = tk.Button (root, text='Exit Application', command=root.destroy)
canvas1.create_window(85, 300, window=button1) 

entry1 = tk.Entry (root)
canvas1.create_window(100, 200, window=entry1) 
  
entry2 = tk.Entry (root)
canvas1.create_window(100, 220, window=entry2) 
          
entry3 = tk.Entry (root)
canvas1.create_window(100, 240, window=entry3) 
  
  
def insert_number():
    global x1 
    global x2 
    global x3 
    x1 = float(entry1.get()) 
    x2 = float(entry2.get()) 
    x3 = float(entry3.get()) 
      
    figure1 = Figure(figsize=(5,4), dpi=100) 
    subplot1 = figure1.add_subplot(111) 
    xAxis = [float(x1),float(x2),float(x3)] 
    yAxis = [float(x1),float(x2),float(x3)] 
    subplot1.bar(xAxis,yAxis, color = 'g') 
    bar1 = FigureCanvasTkAgg(figure1, root) 
    bar1.get_tk_widget().pack(side=tk.LEFT, fill=tk.BOTH, expand=0)
      
    figure2 = Figure(figsize=(5,4), dpi=100) 
    subplot2 = figure2.add_subplot(111) 
    labels2 = 'Label1', 'Label2', 'Label3' 
    pieSizes = [float(x1),float(x2),float(x3)]
    explode2 = (0, 0.1, 0)  
    subplot2.pie(pieSizes, explode=explode2, labels=labels2, autopct='%1.1f%%', shadow=True, startangle=90) 
    subplot2.axis('equal')  
    pie2 = FigureCanvasTkAgg(figure2, root) 
    pie2.get_tk_widget().pack()
          
      
button2 = tk.Button (root, text='Click to Draw Chart ',command=insert_number) 
canvas1.create_window(97, 270, window=button2) 
  
root.mainloop()

```

### The Canvas

The Canvas is your GUI screen in which you can place items, such as buttons. You can control the dimensions of the Canvas by changing the width and height values.


``` python
canvas1 = tk.Canvas(root, width = 1000, height = 350)
canvas1.pack()

```

### The Exit Application Button

The exit application button (in our case ‘button1’) triggers the ‘destroy’ command to close the tkinter GUI upon a click.
You can position the button on the Canvas by specifying the coordinates (in our case, the coordinates are 85 and 300).


``` python

button1 = tk.Button (root, text='Exit Application', command=root.destroy)
canvas1.create_window(85, 300, window=button1) 
```

### The Entry Boxes

The 3 entry boxes are used to collect information from the user. That information will then be used to create the matplotlib charts.
As before, you can control the position of the entry boxes by specifying the coordinates.

``` python

entry1 = tk.Entry (root)
canvas1.create_window(100, 200, window=entry1) 
  
entry2 = tk.Entry (root)
canvas1.create_window(100, 220, window=entry2) 
          
entry3 = tk.Entry (root)
canvas1.create_window(100, 240, window=entry3)  
```

### The Function

Lastly, the ‘insert_number’ function will be called when the user clicks on the second button (i.e., ‘button2’) to draw the charts.

The information collected in the entry boxes, will then be used to depict the bar and pie charts. Here is a full guide that explains how to place charts on a tkinter GUI.



``` python
def insert_number():
    global x1 
    global x2 
    global x3 
    x1 = float(entry1.get()) 
    x2 = float(entry2.get()) 
    x3 = float(entry3.get()) 
      
    figure1 = Figure(figsize=(5,4), dpi=100) 
    subplot1 = figure1.add_subplot(111) 
    xAxis = [float(x1),float(x2),float(x3)] 
    yAxis = [float(x1),float(x2),float(x3)] 
    subplot1.bar(xAxis,yAxis, color = 'g') 
    bar1 = FigureCanvasTkAgg(figure1, root) 
    bar1.get_tk_widget().pack(side=tk.LEFT, fill=tk.BOTH, expand=0)
      
    figure2 = Figure(figsize=(5,4), dpi=100) 
    subplot2 = figure2.add_subplot(111) 
    labels2 = 'Label1', 'Label2', 'Label3' 
    pieSizes = [float(x1),float(x2),float(x3)]
    explode2 = (0, 0.1, 0)  
    subplot2.pie(pieSizes, explode=explode2, labels=labels2, autopct='%1.1f%%', shadow=True, startangle=90) 
    subplot2.axis('equal')  
    pie2 = FigureCanvasTkAgg(figure2, root) 
    pie2.get_tk_widget().pack()
          
      
button2 = tk.Button (root, text='Click to Draw Chart ',command=insert_number) 
canvas1.create_window(97, 270, window=button2) 

```


### The full Python Code with a Background Image


To add a background image, you’ll need to install the PIL package.

Please note that you will need to change the path (for the background image) to the location where your image is stored on your computer. Specifically, you’ll need to change the portion in green (i.e., line 16 in the code below) to your desired path.

imagepath1 = r’C:\Users\Doron E\Desktop\Web Images\panorama_pic.jpg’

Additional comments are available within the code to clarify each component of the code:

```python

#How to Create a GUI in Python 
 
#Import modules
import tkinter as tk # module to create a GUI 
from PIL import ImageTk # module to add a background picture
from matplotlib.backends.backend_tkagg import FigureCanvasTkAgg
from matplotlib.figure import Figure

 
root= tk.Tk()
 
canvas1 = tk.Canvas(root, width = 1000, height = 350) # create the canvas (tkinter module)
canvas1.pack()
 
 
imagepath1 = r'C:\Users\Doron E\Desktop\Web Images\panorama_pic.jpg' #include the path for the image (use 'r' before the path string to address any special character such as '\'. Also, make sure to include the image type - here it is jpg)
image1 = ImageTk.PhotoImage(file = imagepath1) # PIL module
canvas1.create_image(700, 250, image = image1) # create a canvas image to place the background image
 
 
button1 = tk.Button (root, text='Exit Application', command=root.destroy) # create an Exit button to close the main window
canvas1.create_window(85, 300, window=button1) # create a canvas window to place the Exit Application button on top of the background image
 
 
entry1 = tk.Entry (root) # create 1st entry box
canvas1.create_window(100, 200, window=entry1) # create a canvas window to place the 1st entry box on top of the background image
 
entry2 = tk.Entry (root) # create 2st entry box
canvas1.create_window(100, 220, window=entry2) # create a canvas window to place the 2nd entry box on top of the background image
         
entry3 = tk.Entry (root) # create 3st entry box
canvas1.create_window(100, 240, window=entry3) # create a canvas window to place the 3rd entry box on top of the background image
 
 
def insert_number(): # create a function/command to be called by the button (i.e., button2 below)
    global x1 # add 'global' before the variable x1, so that you can use that variable outside of the command/function if ever needed 
    global x2 # add 'global' before the variable x2, so that you can use that variable outside of the command/function if ever needed 
    global x3 # add 'global' before the variable x3, so that you can use that variable outside of the command/function if ever needed 
    x1 = float(entry1.get()) # store the data input by the user as a variable x1 (float is added to handle any formatting issues)
    x2 = float(entry2.get()) # store the data input by the user as a variable x2 (float is added to handle any formatting issues)
    x3 = float(entry3.get()) # store the data input by the user as a variable x3 (float is added to handle any formatting issues)
     
    # create a bar chart once the variables x1, x2 and x3 are inserted by the user (and the user then clicks on button2 below)
    figure1 = Figure(figsize=(5,4), dpi=100) # create a Figure (matplotlib module)
    subplot1 = figure1.add_subplot(111) # add a subplot
    xAxis = [float(x1),float(x2),float(x3)] # intakes the values inserted under x1, x2 and x3 to represent the x Axis  
    yAxis = [float(x1),float(x2),float(x3)] # intakes the values inserted under x1, x2 and x3 to represent the y Axis 
    subplot1.bar(xAxis,yAxis, color = 'g') # create the bar chart based on the input variables x1, x2, and x3
    bar1 = FigureCanvasTkAgg(figure1, root) # create a canvas figure (matplotlib module)
    bar1.get_tk_widget().pack(side=tk.LEFT, fill=tk.BOTH, expand=0)
     
     
    # create a pie chart once the variables x1, x2 and x3 are inserted by the user (and the user then clicks on button2 below)
    figure2 = Figure(figsize=(5,4), dpi=100) # create a Figure (matplotlib module)
    subplot2 = figure2.add_subplot(111) # add a subplot
    labels2 = 'Label1', 'Label2', 'Label3' # add labels for each slice in the pie chart
    pieSizes = [float(x1),float(x2),float(x3)] # intakes the values inserted under x1, x2 and x3 to represent the pie slices 
    explode2 = (0, 0.1, 0)  # explodes the 2nd slice (i.e. 'Label2')
    subplot2.pie(pieSizes, explode=explode2, labels=labels2, autopct='%1.1f%%', shadow=True, startangle=90) # create the pie chart based on the input variables x1, x2, and x3
    subplot2.axis('equal')  # Use equal to draw the pie chart as a circle 
    pie2 = FigureCanvasTkAgg(figure2, root) # create a canvas figure (matplotlib module)
    pie2.get_tk_widget().pack()
     
     
     
button2 = tk.Button (root, text='Click to Draw Chart ',command=insert_number) # button to call the 'insert_number' command above 
canvas1.create_window(97, 270, window=button2) # create a canvas window to place button2 on top of the background image
 
 
root.mainloop()

```





# Ejemplo de programacion




Siempre declarar las variables

```
from tkinter import *
#import tkinter
#import tkinter as Tk
from tkinter import messagebox
from tkinter import filedialog
#import Tkinter as Tk
#import Tkinter as tk
#import messagebox
root = Tk()
ss = Tk()
counter=0


root.title("Matias")
ss.title("Jose")
root.geometry("740x700")
ss.geometry("740x700")
a = StringVar()

def hello():
    b= a.get()
    label13=tkinter.Label(ss,text=b,fg='red',bg='yellow',font=10).pack()
def newfi():
    label14=Label(ss,text='Click on new file',font=10).pack()
def dele():
    label15=Label(ss,text='deleted',fg='red',bg='yellow',font=10).pack()
def mbox():
    messagebox.showinfo("save","are you sure to save")
    #messagebox.showinfo(title='save' ,message='are you sure to save')
    #messagebox.showinfo('save','are you sure to save')
def mfileopen():
    file1 = filedialog.askopenfile()
    label16=Label(text=file1).pack()
    file2=file1.name
    f=open(file2)
    label17=Label(text=f.read()).pack()
      
def mquit():
    mess = messagebox.askyesno(title='quit', message='are you sure to quit') #Para cerrar la ventana
    if mess==1:
        root.destroy()
             
def counter_label3(label3):
    counter=0
    def count():
        global counter
        counter += 1
        label3.config(text=str(counter))
        label3.after(1,count)
    count()

"""
https://www.tutorialesprogramacionya.com/pythonya/detalleconcepto.php?punto=69&codigo=69&inicio=60
https://pythonspot.com/tkinter-askquestion-dialog/
https://pythonspot.com/tk-message-box/        
An error box
tkMessageBox.showerror("Error","No disk space left on device")
A warning box 
tkMessageBox.showwarning("Warning","Could not start service")
An information box
tkMessageBox.showinfo("Information","Created in Python.")
"""   
#label1 = Label(text='Asignacion')
label1=Label(root,text='Asignacion',fg='red',bg='yellow',font=10)
label1.place(x=100,y=200)
#label1.pack()

label2 = Label(ss,text='Asignacion2',fg='blue',bg='gray',font=10)
#label2.grid(row=1000,column=1000)
label2.place(x=100,y=300)
#label2.pack()

label3=Label(root,fg='red',bg='yellow',font=10)
label3.place(x=100,y=400)

counter_label3(label3)


#Ingreso de boton
button1 = Button(root,text='enter',fg='white',bg='green',command= hello,font=('arial',10,'bold')).pack() #Fg = letter, bg = Fondo
button2 = Button(ss,text='Delete',fg='white',bg='red',command= dele,font=10).pack() #Fg = letter, bg = Fondo
button3 = Button(root,text='stop',command= root.destroy,font=('arial',10,'bold')).pack() #Fg = letter, bg = Fondo
Button4=Button(text="open file", width=30,command=mfileopen).pack()

#Ingreso de texto
text1= Entry(root,textvariable= a).pack()
#text1= Entry(root).pack()
#text2= Entry(ss,textvariable= a).pack()


Ingreso de menu

mymenu= Menu()
listone= Menu()
listone.add_command(label='New File', command = newfi)
listone.add_command(label='Open File')
listone.add_command(label='Save File',command = mbox)
listone.add_command(label='Quit',command = mquit)

listtwo= Menu()
listtwo.add_command(label='undo')
listtwo.add_command(label='redo')

mymenu.add_cascade(label="File", menu=listone)
mymenu.add_cascade(label="Edit",menu=listtwo)
mymenu.add_cascade(label="Format")
mymenu.add_cascade(label="Run")


root.config(menu=mymenu)
root.mainloop()



```


























