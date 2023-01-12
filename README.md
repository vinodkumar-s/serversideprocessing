# Design a Website for Server Side Processing

## AIM:
To design a website to perform mathematical calculations in server side.

## DESIGN STEPS:

Step 1:
Desing your website for calculation using wireframe work.

Step 2:
Then to execute the wireframe work desing use html,css

Step 3:
Use views.py to execute the coding in serverside.

Step 4:
Mention the path of the website in urls.py.

Step 5:
Publish the website in the given URL.


## PROGRAM :
## volume.html
```
<!DOCTYPE html>
<html>
<head>
    <meta charset='utf-8'>
    <meta http-equiv='X-UA-Compatible' content='IE=edge'>
    <title>Math Calculation</title>
    <meta name='viewport' content='width=device-width, initial-scale=1'>
    <script src='main.js'></script>
    <style>
        * {
  box-sizing: border-box;
  font-family: Arial, Helvetica, sans-serif;
}
body {
    background-image: url("/static/images/math.jpg");

}
.container {
  width: 1080px;
  margin-left: auto;
  margin-right: auto;
  padding-top: 200px;
  padding-left: 300px;
}
.content {
  display:block;
  width: 500px;
  min-height: 300px;
  font-size: 20px;
  background-color:paleturquoise;
}
h1{
    color:gold;
    text-align: center;
    padding-top: 25px;
}
.formelement{
    color: darkmagenta;
    text-align: center;
    margin-top: 5px;
    margin-bottom: 5px;
}
    </style>
</head>
<body>
    
    <div class="container">
    <div class="content">
    <h1>VOLUME OF A CUBOID</h1>
    <form method="POST">
        {% csrf_token %}
        <div class="formelement">
        Length : <input type="text" name="length" value="{{l}}"></input>Meters<br/>
        </div>
        <div class="formelement">
        Breadth : <input type="text" name="breadth" value="{{b}}"></input>Meters<br/>
        </div>
        <div class="formelement">
        Width : <input type="text" name="width" value="{{w}}"></input>Meters<br/>
        </div>
        <div class="formelement">
        <input type="submit"  value="Calculate Volume"></input><br/>
        </div>
        <div class="formelement">
        Volume : <input type="text" name="volume" value="{{volume}}"></input>Meter<sup>3</sup><br/>
        </div>
    
    </form>
    </div>
    </div>
</body>
</html>
```
## views.py
```
from django.shortcuts import render

def volumecalculation(request):
    context={}
    context['volume'] = "0"
    context['l'] = "0"
    context['b'] = "0"
    context['w'] = "0"
    if request.method == 'POST':
        l = request.POST.get('length','0')
        b = request.POST.get('breadth','0')
        w = request.POST.get('width','0')
        volume = int(l) * int(b) * int(w)
        context['volume'] = volume
        context['l'] = l
        context['b'] = b
        context['w'] = w
    return render(request,'mathapp/volume.html',context)
 ```
## urls.py
```
from django.contrib import admin
from django.urls import path
from mathapp import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('volumeofacuboid/',views.volumecalculation,name="volumeofacuboid"),
    path('',views.volumecalculation,name="volumeofacuboidroot")
]
```
## OUTPUT:
![output](/area%20calculator.png)




## Result:
A website to perform mathematical calculations in server side is created.



