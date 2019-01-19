# Tkinter
General Information about TKinter


## https://datatofish.com/matplotlib-charts-tkinter-gui/
## https://datatofish.com/how-to-create-a-gui-in-python/



´´´python

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

´´´

### The Canvas

The Canvas is your GUI screen in which you can place items, such as buttons. You can control the dimensions of the Canvas by changing the width and height values.


´´´ python
canvas1 = tk.Canvas(root, width = 1000, height = 350)
canvas1.pack()

´´´

### The Exit Application Button

The exit application button (in our case ‘button1’) triggers the ‘destroy’ command to close the tkinter GUI upon a click.
You can position the button on the Canvas by specifying the coordinates (in our case, the coordinates are 85 and 300).


´´´ python

button1 = tk.Button (root, text='Exit Application', command=root.destroy)
canvas1.create_window(85, 300, window=button1) 
´´´

### The Entry Boxes

The 3 entry boxes are used to collect information from the user. That information will then be used to create the matplotlib charts.
As before, you can control the position of the entry boxes by specifying the coordinates.

´´´ python

entry1 = tk.Entry (root)
canvas1.create_window(100, 200, window=entry1) 
  
entry2 = tk.Entry (root)
canvas1.create_window(100, 220, window=entry2) 
          
entry3 = tk.Entry (root)
canvas1.create_window(100, 240, window=entry3)  
´´´


### The Function

Lastly, the ‘insert_number’ function will be called when the user clicks on the second button (i.e., ‘button2’) to draw the charts.

The information collected in the entry boxes, will then be used to depict the bar and pie charts. Here is a full guide that explains how to place charts on a tkinter GUI.



´´´ python
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
´´´


### The full Python Code with a Background Image


To add a background image, you’ll need to install the PIL package.

Please note that you will need to change the path (for the background image) to the location where your image is stored on your computer. Specifically, you’ll need to change the portion in green (i.e., line 16 in the code below) to your desired path.

imagepath1 = r’C:\Users\Doron E\Desktop\Web Images\panorama_pic.jpg’

Additional comments are available within the code to clarify each component of the code:

´´´python
#How to Create a GUI in Python 
 
# Import modules
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

´´´
































