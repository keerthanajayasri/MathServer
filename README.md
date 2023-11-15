# Ex.05 Design a Website for Server Side Processing
## Date:

## AIM:
To design a website to find total surface area of a square prism in server side.

## FORMULA:
Total Surface Area = 2b<sup>2</sup> + 4bh
<br>b --> Base of Square Prism
<br>h --> Height of Square Prism

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
# math.html
```
<html>
<head>
<meta charset='utf-8'>
<meta http-equiv='X-UA-Compatible' content='IE=edge'>
<title>Area of Triangle</title>
<meta name='viewport' content='width=device-width,initial-scales=1'>
<style>
body {
background-color:cyan;
}
.edge {
width: 1080px;
margin-left: auto;
margin-right: auto;
padding-top: 200px;
padding-left: 300px;
}
.box {
display:block;
border: Thick dashed lime;
width: 600px;
min-height: 300px;
font-size: 20px;
background-color:pink;
}
.formelt{
color: red;
text-align: center;
margin-top: 10px;
margin-bottom: 10px;
}
h1{
color: yellow;
text-align: center;
padding-top: 30px;
}
</style>
</head>
<body>
<div class="edge">
<div class="box">
<h1>Area of a Triangle</h1>
<form method="POST">
{% csrf_token %}
<div class="formelt">
Breadth : <input type="text" name="breadth" value="{{b}}"></input>(in m)<br/>
<div clss="formelt">
Height : <input type="text" name="height" value="{{h}}"></input>(in m)<br/></div>
<div class="formelt">
<input type="submit" value="calculate"></input><br/>
</div>
<div class="formelt">
Area :  <input type="text" name="area" value="{{area}}"></input>m<sup>2</sup><br/>
</div>
</form>
</div>
</div>
</body>
</html>
```
# urls.py
```
from django.contrib import admin
from django.urls import path
from myapp import views


urlpatterns = [
    path('admin/', admin.site.urls),
    path('areaoftriangle/',views.triarea,name="areaoftriangle"),
    path('',views.triarea,name="areaoftriangleroot")
]
```
# views.py
```
from django.shortcuts import render
def triarea(request):
    context={}
    context['area']="0"
    context['b']="0"
    context['h']="0"
    if request.method == 'POST':
        print("POST method is used")
        b = request.POST.get('breadth','0')
        h = request.POST.get('height','0')
        print('request=',request)
        print('Breadth=',b)
        print('height=',h)
        area = (int(b) * int(h))/2
        context['area'] = area
        context['b'] = b
        context['h'] = h
        print('Area=',area)
    return render(request,'myapp/math.html',context) 

```

## SERVER SIDE PROCESSING:

![image](https://github.com/keerthanajayasri/MathServer/assets/121163440/22c50f14-4f11-4012-bdd7-fde9412c2cee)

## HOMEPAGE:

![image](https://github.com/keerthanajayasri/MathServer/assets/121163440/e8dbe00b-82a0-468d-ae05-0e2f3029a181)

## RESULT:
The program for performing server side processing is completed successfully.
