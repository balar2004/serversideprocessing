# Design a Website for Server Side Processing

## AIM:
To design a website to perform mathematical calculations in server side.

## DESIGN STEPS:

### Step 1:

Clone the repository from GitHub

### Step 2:

Create Django Admin project.

### Step 3:

Create a New App

### Step 4:

Publish the website in the given URL.

### Step 5:

Create a HTML file of forms.

### Step 6:

Publish the website in the given URL.

## PROGRAM :
HTML CODE:
```
<!DOCTYPE html>
<html>
    <head>
        <Title>Calculate Area of Rectangle</Title>
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <style>
        body{background-color: rgba(0, 0, 255, 0.521);
        }
        .edge
        { 
        width: 1080px;
        margin-left:auto; 
        margin-right:auto; 
        padding-top:200px; 
        padding-left:300px; 
        } 
        .box
        { 
        display:block; 
        border:blue; 
        width:800px; 
        min-height:300px; 
        font-size:20px;
        background-color:rgba(90, 29, 102, 0.8); 
        } 
        .formelt{
        color: rgb(22, 19, 19); 
        text-align:center; 
        margin-top:5px; 
        margin-bottom:5px; 
        } 
        h1 
        {
        color: yellow; 
        text-align:center; 
        padding-top:20px; 
        }
        </style>
    </head>
    <body>
        <div class="edge">
            <div class="box">
                <h1>Area of Rectangle</h1>
                <form method="POST">
                {% csrf_token%}
                <div class="formelt">
                    Length: <input type="text" name="length" value="{{1}}"></input>(in m)<br/>
                </div>
                <div class="formelt">
                    Breadth: <input type="text" name="breadth" value="{{1}}"></input>(in m)<br/>
                </div>
                <div class="formelt">
                    <input type="submit" value="Calculate"></input><br/>
                </div>
                <div class="formelt">
                    Area: <input type="text" name="area" value="{{area}}"></input>m<sup>2</sup><br/>
                </div>
                </form>
            </div>

        </div>
    <h4 style="text-align: center;">Copyright @ 2023, Developed by Bala</h4>
    </body>
</html>
```
Views.py:
```
from django.shortcuts import render
from django.contrib.auth.decorators import permission_required

# Create your views here.

def serverside(request):
    context={}
    context['area'] = "0"
    context['l'] = "0"
    context['b'] = "0"
    if request.method == 'POST':
        print("POST method is used")
        l = request.POST.get('length','0')
        b = request.POST.get('breadth','0')
        print('request=',request)
        print('Length=',l)
        print('Breadth=',b)
        area= int(l) * int(b)
        context['area'] = area
        context['l'] = l
        context['b'] = b
        print('Area=', area)
    return render(request,"html/serverside.html",context)
```
Urls.py:
```
    """serverside URL Configuration

The `urlpatterns` list routes URLs to views. For more information please see:
    https://docs.djangoproject.com/en/3.1/topics/http/urls/
Examples:
Function views
    1. Add an import:  from my_app import views
    2. Add a URL to urlpatterns:  path('', views.home, name='home')
Class-based views
    1. Add an import:  from other_app.views import Home
    2. Add a URL to urlpatterns:  path('', Home.as_view(), name='home')
Including another URLconf
    1. Import the include() function: from django.urls import include, path
    2. Add a URL to urlpatterns:  path('blog/', include('blog.urls'))
"""
from django.contrib import admin
from django.urls import path

from project import views
from django.contrib.auth import views as auth_views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('serverside/',views.serverside,name='serverside')
]
```

## OUTPUT:

![output](./home/project/serversideprocessing/output.jpg)

### Home Page:

http://bala.student.saveetha.in/serverside/

## Result:

The program for implementing server side processing is completed successfully.