# Ex.05 Design a Website for Server Side Processing
## Date:25.04.25

## AIM:
 To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side. 


## FORMULA:
P = I<sup>2</sup>R
<br> P --> Power (in watts)
<br> I --> Intensity
<br> R --> Resistance

## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub.

### Step 2:
Create Django Admin project.

### Step 3:
Create a New App under the Django Admin project.

### Step 4:
Create python programs for views and urls to perform server side processing.

### Step 5:
Create a HTML file to implement form based input and output.

### Step 6:
Publish the website in the given URL.

## PROGRAM :
```
math.html

<html>
    <head>
        <title>LAMP FILAMENT POWER CALCULATOR</title>
        <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
        }
        .container {
            max-width: 400px;
            margin: auto;
            padding: 20px;
            border: 1px solid #ccc;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        label {
            display: block;
            margin-top: 10px;
        }
        input {
            width: 100%;
            padding: 8px;
            margin-top: 5px;
        }
        button {
            margin-top: 15px;
            padding: 10px 20px;
            background-color: white;
            color: rgb(34, 150, 129);
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        button:hover {
            background-color: rgb(36, 74, 135);
        }
        .result {
            margin-top: 20px;
            font-size: 1.2em;
            color: #333;
        }
        </style>
    </head>
    <body>
        <div class="container">
            <h2>Lamp Filament Power Calculator</h2>
            <form id="powerForm">
                <label for="intensity">INTENSITY (I) IN AMPERES:</label>
                <input type="number" id="intensity" name="intensity" required>

                <label for="resistance">RESISTANCE (R) IN OHMS:</label>
                <input type="number" id="resistance" name="resistance" required>
                
                <button type="button" onclick="calculatePower()">Calculate Power</button>
            </form>
        <div class="result" id="result"></div>
    </div>
    <script>
     function calculatePower() {
        const intensity = parseFloat(document.getElementById('intensity').value);
        const resistance = parseFloat(document.getElementById('resistance').value);
        
        if (isNaN(intensity) || isNaN(resistance)) {
            document.getElementById('result').innerText = "Please enter valid numeric values for both fields.";
            return;
        }
        
        const power = intensity ** 2 * resistance;
        document.getElementById('result').innerText = `Power (P): ${power.toFixed(2)} Watts`;
        }
    </script>
    </body>
</html>

views.py

from django.shortcuts import render
def rectarea(request):
    context={}
    context['area']="0"
    context['l']="0"
    context['b']="0"
    if request.method== 'POST':
        print("POST method is used")
        l=request.POST.get('length','0')
        b=request.POST.get('breadth','0')
        print('request=',request)
        print('Length=',l)
        print('Breadth=',b)
        area=int(l)*int(b)
        context['area']=area
        context['l']=l
        context['b']=b
        print('Area=',area)
    return render(request,'mathapp/math.html',context)

urls.py

from django.contrib import admin
from django.urls import path
from mathapp import views
urlpatterns=[
    path('admin/',admin.site.urls),
    path('areaofrectangle/',views.rectarea,name="areaofrectangle"),
    path('',views.rectarea,name="areaofrectangleroot")
]
```

## SERVER SIDE PROCESSING:
![image](https://github.com/user-attachments/assets/74adc3b2-27f3-47f6-bcb5-20ab27e952dc)


## HOMEPAGE:
![image](https://github.com/user-attachments/assets/f20b37af-4cfa-42eb-9399-74cb9d520d83)


## RESULT:
The program for performing server side processing is completed successfully.
