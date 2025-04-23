# Ex.05 Design a Website for Server Side Processing
## Date: 23.04.2025

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
    <title>Power Calculation</title>
</head>
<body style="text-align: center;
             background-color: black;
             padding: 20px; color: white;">
    <h1 style="background-color: cyan; color: white; font-size: 50px; padding: 20px; border-radius: 10px;">
        Power of Lamp Filament
    </h1>
    <form method="POST" style="background-color: cyan; display: inline-block; padding: 50px; border-radius: 10px;">
        {% csrf_token %}
        <label for="intensity" style="color: white; font-size: large; background-color: red; padding: 5px; border-radius: 5px;">Intensity (I) in amperes:</label><br>
        <input type="number" id="intensity" name="intensity" step="0.01" value="{{ intensity }}" required style="padding: 8px; margin: 10px; border-radius: 5px; width: 200px;"><br><br>
        
        <label for="resistance" style="color: white; font-size: large; background-color: red; padding: 5px; border-radius: 5px;">Resistance (R) in ohms:</label><br>
        <input type="number" id="resistance" name="resistance" step="0.01" value="{{ resistance }}" required style="padding: 8px; margin: 10px; border-radius: 5px; width: 200px;"><br><br>
        
        <input type="submit" value="Calculate" style="background-color: yellow; color: black; padding: 10px 20px; border: none; cursor: pointer; font-size: medium; border-radius: 5px;"><br><br>
        
        <label for="power" style="color: white; font-size: large;">Power (P) in watts:</label><br>
        <input type="number" id="power" name="power" value="{{ power }}" readonly style="padding: 8px; margin: 10px; border-radius: 5px; width: 200px; background-color: white; color: black;"><br>
    </form>
</body>
</html>

views.py

from django.shortcuts import render 
def EnergyCalc(request): 
    context = {
        'power': "0", 
        'intensity': "0", 
        'resistance': "0"
    }
    if request.method == 'POST': 
        print("POST method is used")
        intensity = request.POST.get('intensity', '0')
        resistance = request.POST.get('resistance', '0')
        print('request=', request) 
        print('intensity=', intensity) 
        print('resistance=', resistance) 
        power = (int(intensity) ** 2) * int(resistance)
        context['power'] = power
        context['intensity'] = intensity
        context['resistance'] = resistance 
        print('power=', power)  
    return render(request, 'mathapp/math.html', context)


urls.py

from django.contrib import admin
from django.urls import path
from mathapp import views 

urlpatterns = [
    path('admin/', admin.site.urls),  
    path('', views.EnergyCalc, name="EnergyCalc"),  
]
```


## SERVER SIDE PROCESSING:
![web ssp 1](https://github.com/user-attachments/assets/de0501c4-ed53-4681-a776-2022e75bd75c)

## HOMEPAGE:
![web ssp 2](https://github.com/user-attachments/assets/8d48eb20-760b-4ade-8da2-e12a1520fa7b)

## RESULT:
The program for performing server side processing is completed successfully.
