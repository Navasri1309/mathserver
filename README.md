# Ex.05 Design a Website for Server Side Processing
# Date:02.10.2025
# AIM:
To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side.

# FORMULA:
P = I2R
P --> Power (in watts)
 I --> Intensity
 R --> Resistance

# DESIGN STEPS:
## Step 1:
Clone the repository from GitHub.

## Step 2:
Create Django Admin project.

## Step 3:
Create a New App under the Django Admin project.

## Step 4:
Create python programs for views and urls to perform server side processing.

## Step 5:
Create a HTML file to implement form based input and output.

## Step 6:
Publish the website in the given URL.

# PROGRAM :
```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Lamp Filament Power Calculator</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background: pink;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
    }

    .container {
      background : grey;
      padding: 30px;
      border-radius: 12px;
      box-shadow: 0 8px 20px rgba(0,0,0,0.1);
      width: 360px;
    }

    h2 {
      text-align: center;
      color:black;
      margin-bottom: 20px;
    }

    label {
      display: block;
      margin-top: 15px;
      font-weight: 600;
      color: black;
    }

    input[type="number"] {
      width: 100%;
      padding: 10px;
      margin-top: 5px;
      border: 1px solid black;
      border-radius: 6px;
      font-size: 14px;
    }

    button {
      margin-top: 25px;
      width: 100%;
      padding: 12px;
      background-color: black;
      color: white;
      border: none;
      border-radius: 6px;
      font-size: 16px;
      cursor: pointer;
      transition: background-color 0.3s ease;
    }

    button:hover {
      background-color: pink;
    }

    .result {
      margin-top: 25px;
      text-align: center;
      font-size: 18px;
      color: purple;
      font-weight: bold;
    }
  </style>
</head>
<body>
  <div class="container">
    <h2>Power Calculator</h2>
    <form method="POST">
      {% csrf_token %}
      
      <label for="intensity">Intensity (I)</label>
      <input type="number" step="any" name="intensity" id="intensity" required>

      <label for="resistance">Resistance (R)</label>
      <input type="number" step="any" name="resistance" id="resistance" required>

      <button type="submit">Calculate Power</button>
    </form>

    {% if power %}
      <div class="result">
        Power = {{ power }} watts
      </div>
    {% endif %}
  </div>
</body>
</html>

views.py

from django.shortcuts import render
def power_calculator(request):
    power = None 
    intensity = None
    resistance = None 

    if request.method == 'POST':
        print("POST method is used")
        
        intensity = request.POST.get('intensity','0')
        resistance = request.POST.get('resistance','0')

        
        if intensity and resistance:
            try:
            
                I = float(intensity)
                R = float(resistance)
                power = I**2 * R
                print('request=',request)
                print('intensity=',I)
                print('resistance=',R)
                print('power=',power)  

            except ValueError:
                power = "Invalid input. Please enter numerical values."

    
    return render(request, 'mathapp/power_calc.html', {'power': power, 'intensity': intensity, 'resistance': resistance})

urls.py
from django.contrib import admin
from django.urls import path
from mathapp import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', views.power_calculator, name='power_calculator'),
]

```
# SERVER SIDE PROCESSING:

<img width="1823" height="299" alt="Screenshot 2025-10-02 105224" src="https://github.com/user-attachments/assets/207e585d-d3ce-4d94-abda-76cf8aa975e6" />

# HOMEPAGE:

<img width="1913" height="1103" alt="Screenshot 2025-10-02 105506" src="https://github.com/user-attachments/assets/c56e8e6d-ab00-4195-85a9-82b3264d6fd6" />


# RESULT:
The program for performing server side processing is completed successfully.
