# GamesForYou
#### Video Demo:  <URL https://youtu.be/EucxYjQYdQg >
#### Description:

GamesForYou is a simple project made for the final CS50 project.
GamesForYou will choose a random game for PS5 or X box Series X based on the type of game that the user will choose.
In case you are not sure , the program will chose for you  and at the end will show also all statistics of all the users choices (type of games).
GamesForYou take the information of the games form Wikipedia ( Web scraping )

## Directory

In the directory project there are the following directories:

project.py,
test_project.py,
user.csv,
requirements.txt,
README.md

## user.csv

The csv file contains all the information of the users  , we will use the pandas library to generate and read the data from the csv file.


## project.py

In project.py there is code of the project.

We import on this file all the following:

'''
import random
import sys
from csv import DictWriter

import matplotlib.pyplot as plt  # type: ignore
import pandas as pd  # type: ignore # library for data analysis
import requests  # type: ignore # library to handle requests
from bs4 import BeautifulSoup  # type: ignore # library to parse HTML documents
'''

in the main function we will insert all the function to let the program work, the function main to run the program will be called at the end

'''
if __name__ == "__main__":
    main()
    
'''

The main function ask the users personal data and then ask  to chose a console and a genre , with this 2 information the program store in a variable using the web function the random game and store in the user.csv the information.
Then the program will will ask the user if want to see the statistics of the users genre choices , if the user doesn't want to see statistics then the program will end.

In the main function we will have many different functions:

main()
users()
consols()
genres()
web()
write_file()
stat()
graf()
statistics_and_graf()



### users


The function ask the users for a name , surname and age.

Raise an error all the time that name and surname  are not all alpha and if age is less then 18 with sys.exit("") will close the program.
The function  return a dictionary with name surname and age

### consols

Ask the users to type the name of the consol and check if the answer is ps5 or serie x , then return the name of the consol otherwise , if the answer is different then the function will ask all the time to type the name of the consol


### genres

The function ask the users to type the name of the genres and check if the answer is on the list of genres , if yes the function will return the list of genres otherwise , if the answer is different then the function will ask again to type the name of the genres.

The list of genres:
'''
genres =["survival",
        "racing",
        "sports",
        "fighting",
        "shooters",
        "action-adventure",
        "adventure",
        "stealth",
        "horror"]
'''

### web

The function get in input part of the name of the consol and the genres of the game.
The function use "https://en.wikipedia.org/wiki/" + the consol in input with request to get the response in the form of html.
The using beautifulsoup the function is going to find part of the html code we , a table with all the games for the consol.
''' 
soup.find("table", {"id": "softwarelist"})

'''
Then using pandas the function read the html part (table) and convert it to a pandas dataframe.
From the dataframe pandas loc all games with the genres in input and will store a random game in a variable.

the function will return a dictionary with all info about the game
'''
return {"Title": game, "Genre(s)": genres, "Developer(s)": dev, "Publisher(s)": pub}

'''



### write_file

The function take in input all the information about the user plus the name of the game and all the info of the game and will write all on the file user.csv.


### stat

The function stat() read the file csv and using pandas will count the number of the user the average (mean) of the ages and the average of the genres and consol present on the file.
The function return a dictionary with all the information


### graf

The function is made to show a graphic and take in input a dictionary form stat function

'''
import matplotlib.pyplot as plt

'''

I use a template form matplotlib library I add on the axis x = all the genres and  axis y = all the average that we get from stat function.
The function will show the result



### statistics_and_graf

The function will print on the terminal all the information form the stat function with the average and will use the function graf to show the graphic in a different window




## test_project.py

In this file im testing 3 function of my project.py to see if everything works correctly
test_web()
test_consols()
test_genres()
to make everything works correctly
'''
from project import web, consols , genres , stat , users
import pandas as pd
import mock # type: ignore
import builtins
import math
'''

In test web i recreate the dataframe using the link form wikipedia and a genres , and i confront with a list of all expected tittles to see if the dataframe is correct,
using web() at index 0

ex :
'''
df = pd.DataFrame(web("List_of_Xbox_Series_X_and_Series_S_games","Sports"),index=[0])
'''
In test consols and genres im using mock to check if the input of the users  will return the expected result.