# My experimentation with chatgpt

## Basic Weather App

First I wanted to see if chatgpt could create a web application from a high level prompt - "Write a django web application that takes a user's date of birth and tells them what the weather was on that day."

![alt text](images/weather_app.gif?raw=true "Weather App")

weather/views.py
```
from django.shortcuts import render

def get_weather(request):
    # Get the user's date of birth from the request
    date_of_birth = request.POST.get('date_of_birth')

    # Look up the weather for the given date (we'll just return a generic message instead)
    weather = "The weather on your birthday was nice."

    # Return the weather information to the user
    return render(request, 'weather.html', {'weather': weather})

```

urls.py
```
from django.urls import path
from weather import views

urlpatterns = [
    path('weather/', views.get_weather, name='get_weather'),
]

```

Overall I was impressed it understood the prompt but it is clear it took a shortcut in not actually creating a call to a weather API to get the weather.  In a later prompt it made it clear it knew what to do but wasn't going to add the weather lookup logic.

## Simple Script

I actually had a use for this one.  I commonly need to change AWS Athena exports to a json stucture for testing purposes.  Simple prompt - "Write a python script that accepts a file and converts a csv to json structure."


![alt text](images/csv_to_json.gif?raw=true "Json Script")


```
import csv
import json

# Open the input CSV file
with open('input.csv', 'r') as input_file:
    # Read the contents of the CSV file into a list of dictionaries, where
    # each dictionary represents a row in the CSV file with the keys being
    # the column names and the values being the cell values
    csv_data = list(csv.DictReader(input_file))

# Open the output JSON file
with open('output.json', 'w') as output_file:
    # Write the data to the JSON file
    json.dump(csv_data, output_file)

```

Script does what I needed.  ChatGPT hit the mark on this one.

## A letter to my wife


"Write a letter to my wife apologizing for not kissing her goodbye this morning."

![alt text](images/letter1.gif?raw=true "Letter 1")

```
Dear Wife,

I wanted to take a moment to apologize for not kissing you goodbye this morning before I left for work. I know how much you value those small moments of affection and I regret that I missed the opportunity to show you how much I care about you.

I know that the morning rush can sometimes make it difficult to slow down and appreciate each other, but I want you to know that you are always on my mind. I am grateful for the love and support you give me each and every day and I want to do better in showing you how much you mean to me.

I hope that you can forgive me for this oversight and that we can make a conscious effort to be more present with each other in the future. I love you more than words can express and I never want to take you or our relationship for granted.

Sincerely,

[Your Name]
```

Pretty good, but I work from home so I can't have chatgpt being dishonest

![alt text](images/letter2.gif?raw=true "Letter 2")

...

"Write a letter to my wife apologizing for not kissing her goodbye before dropping Elaina off at school this morning."

```
Dear Wife,

I wanted to take a moment to apologize for not kissing you goodbye before dropping Elaina off at school this morning. I know how much you value those small moments of affection and I regret that I missed the opportunity to show you how much I care about you.

I know that the morning rush can sometimes make it difficult to slow down and appreciate each other, but I want you to know that you are always on my mind. I am grateful for the love and support you give me each and every day and I want to do better in showing you how much you mean to me.

I hope that you can forgive me for this oversight and that we can make a conscious effort to be more present with each other in the future. I love you more than words can express and I never want to take you or our relationship for granted.

Sincerely,

[Your Name]





```
