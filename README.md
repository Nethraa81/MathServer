# Ex.05 Design a Website for Server Side Processing
## Date:

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
html:

<html>

<head>
    <meta charset='utf-8'>
    <meta http-equiv='X-UA-Compatible' content='IE=edge'>
    <title>POWER FUNCTION</title>
    <meta name='viewport' content='width=device-width, initial-scale=1'>
    <style type="text/css">
        body {
            background-color:rgb(254, 248, 216);
        }

        .edge {
            display: flex;
            height: 100vh;
            width: 100%;    
            justify-content: center;
            align-items: center;
        }

        .box {
            display: block;
            width: 500px;
            min-height: 300px;
            font-size: 20px;
            background: rgb(51, 47, 168);
            background: linear-gradient(90deg, rgb(7, 159, 241) 9%, rgb(118, 204, 224) 56%);
            border-radius: 10px;
            box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
        }

        .formelt {
            color: whitesmoke;
            text-align: center;
            margin-top: 7px;
            margin-bottom: 6px;
        }

        h1 {
            color: white;
            text-align: center;
            padding-top: 20px;
        }
        input{
            margin: 5px;
            padding: 5px;
            border-radius: 5px;
            border: none;

        }
    </style>
</head>

<body>
    <div class="edge">
        <div class="box">
            <h1>POWER</h1>
            <form method="POST">
                {% csrf_token %}
                <div class="formelt">
                    Intensity : <input type="text" name="Intensity" value="{{I}}"></input>(in A)<br />
                </div>
                <div class="formelt">
                    Resistence : <input type="text" name="Resistence" value="{{R}}"></input>(in Ω)<br />
                </div>
                <div class="formelt">
                    <input type="submit" value="Calculate"></input><br />
                </div>
                <div class="formelt">
                    Power : <input type="text" name="Power" value="{{Power}}"></input>W<br />
                </div>
            </form>
        </div>
    </div>
</body>

</html>

views.py:

from django.shortcuts import render

def power(request):
    context={}
    context['Power'] = ""
    context['i'] = ""
    context['r'] = ""
    if request.method == 'POST':
        print("POST method is used")
        I = request.POST.get('Intensity','')
        R = request.POST.get('Resistence','')
        print('request=',request)
        print('Intensity=',I)
        print('Resistence=',R)
        Power = int(I) * int(I) * int(R)
        context['Power'] = Power
        context['i'] = I
        context['r'] = R
        print('Power=',Power)
    return render(request,'power.html',context)

    urls.py:

    from django.contrib import admin
from django.urls import path
from nithish import views
urlpatterns = [
    path('admin/', admin.site.urls),
    path('Power/',views.power,name="Power"),
    path('',views.power,name="Power")
]
```


## SERVER SIDE PROCESSING:


![image](https://github.com/user-attachments/assets/b9f3afbc-90cc-43d4-8db0-127dd73b45b8)

## HOMEPAGE:
![image](https://github.com/user-attachments/assets/141c0a2d-ff36-4871-a35a-c0dce2491a08)


## RESULT:
The program for performing server side processing is completed successfully.
