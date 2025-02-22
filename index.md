---
layout: home
title: "Welcome to My Blog"
description: "A blog about coding and open-source projects"
---

# 🚀[Panel](_images/logo_horizontal_light_theme.png)-Easy Python Dashboards.

This blog explains a powerful opensource library called Panel which helps us build interactive web apps and can also be used in data analysis in a very effiecient way.




## 📝 Overview.

  Panel is an open-source Python library designed to simplify the development of various tools, web applications, and data analysis workflows—all within the Python ecosystem. Its seamless integration with multiple Python libraries enhances convenience, particularly for data scientists. Panel provides powerful visualization tools, interactive data tables, and collaborative features, enabling efficient and streamlined workflows.

## ❓‍💬  Why should we use this? 

### 1. Easy to use

   • No need to write heavy HTML or JavaScript code
    for making web apps, everything can be made 
    using python only.

### 2. Supports Multiple Data visualization Libraries
   
   • One of the major  advantages of panel is it can
     do all the things done by libraries like 
     Matplotlib, Bokeh, Holoviews and more by
      integrating all these libraries.

   • Allows combining different visualization tools                 

 
### 3. Interactive Web applications
  
   • Offers sliders, buttons, text inputs and
     dropdowns.
   
   • Enables users to interact with data
     dynamically.


### 4. Supports Live Data and streaming updates
  
   • Can handle real time data updates and stream visualizations dynamically.

### 5.  Deployment & Sharing

   • Dashboards can be exported to static HTML or hosted as a web app.

   • Can be deployed using Flask, FastAPI, or even cloud platforms.





## 🖥️ Installation and setup
 
### Using pip.
     
    • pip install panel watchfiles

### Using conda

    • conda install panel watchfiles  
   

   ✅ Tip

We recommend also installing [Watchfiles](https://watchfiles.helpmanual.io/)
 while developing. This will provide a significantly better experience when using Panel’s autoreload features when activating --dev mode. It’s not needed for production.
   
   ✅ Tip

To incorporate highlighted code sections into your app, you’ll need to install [pygments](https://pygments.org/), a powerful syntax highlighting library.


## ⭐ Key features 
We have already seen why should we use this  library, now lets dive into some more cool features this library offers.
### 1️⃣ Interactive dasboards with minimal code.
   • Create interactive dashboards and web applications with minimal code.

   • It follows an object-oriented approach where Python objects (widgets, plots, layouts) can be directly manipulated.

   • This is a standalone tool that worls well with jupyter notebooks.

### 2️⃣ Supports and integrates multiple Visualization libraries.
• Panel works seamlessly with various plotting libraries as follow:

   • Matplotlib

   • Bokeh

   • Ploty

   • Altair

   • Holoviews

   • Datashader (for large datasets)   

• Lets now see a simple example of integrating panel with matplotlib to make a sine wave more interactive.
```python

import panel as pn
import numpy as np
import matplotlib.pyplot as plt

pn.extension()

def plot_sine_wave(freq=1):

   x = np.linspace(0, 10, 100)
   y = np.sin(freq * x)
   fig, ax = plt.subplots()
   ax.plot(x, y)
   ax.set_title(f"Sine Wave (Frequency={freq})")
   return fig
slider = pn.widgets.IntSlider(name="Frequency", start=1, end=10, step=1)
interactive_plot = pn.bind(plot_sine_wave, freq=slider)

dashboard = pn.Column("# Interactive Sine Wave", slider, pn.pane.Matplotlib(interactive_plot))

dashboard.show()

```




• This creates a more interactive sine wave where we can adjust the frequency of the plot too!

### 3️⃣ Interactive widgets

• Panel provides a variety of widgets including buttons, slides, dropdowns, checkboxes, text inputs and many more that enable user interaction as we have seen in the above sine wave example!

• These widgets help us analyse the data more dynamically.

### 4️⃣ Reactive programming(How do interactive dashboards work?)

• Now, one of the most important features of Panel is  reactive programming, that is if a widgets value changes, then any  linked function or vizualization that is related to the widget will update automatically without needing to manually refresh the page. Let us look at a simple example:
```python
   
   import panel as pn
   pn.extension()
   slider=pn.widgets.IntSlider(name='Value',start=0,end=100,step=1,value=50)

   @pn.depends(slider)
   def update_text(value):
      return f"Slider Value: {value}"
   pn.Row(slider, update_text).servable()

   ```
• Here @pn.depends(slider) automatically updates update_text() whenever the slider value gets changes by the user, no need to call the function manually everytime! The UI updates reactively.


### 5️⃣ Inbuit HTML Templates in Panel

Panel Provides ready-made templates buit in HTML that come with great layouts with great responsiveness. Some of them include:

• FastListTemplate- Great for heavy data dashboards

• MaterialTemplate- Uses Googles Material Design

• BootstrapTemplate- Based on Bootstrap

Given below is a simple way to create a structered dashboard with given inbuit templates:
```python
import panel as pn
pn.extension()
template=pn.template.FastlistTemplate(
   title=" your title "
   main=[
      "main matter you want to write"
   ]
)
template.servable()
```
Here we are using a template called FastlistTemplate which is inbuit present in panel which isb mostly used for dashboards with heavy data.

### Lets dive into real time examples and explore some important functions this library offers.

#### A Basic Panel app

The following code creates a simple web app with a text input and a button.
```python
import panel  as pn
pn.extension()
def greet(name):
   return f"Hello, {name}!"

text_input = pn.widgets.TextInput(name="Enter your name")
button=pn.widgets.Button(name="Greet", button_type="primary")
output=pn.pane.Markdown("")

button.on_click(lambda event: output.object = greet(text_input.value))
app = pn.Column(text_input, button, output)
app.show()
```



