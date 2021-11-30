# 4003GroupProject

# Timeline

**Data Report:     Dec 3**

**Final Project:   Dec 23**

# Requirement: Data report

Describe your data and how you accessed it in enough detail that someone else
could do it. Yes, that's ``accessed,'' past tense.  You should have done this
already to make sure you have it. Include your Python code.

Internet sources are preferred, because it allows others to use your code and
follow up on your work.

# Requirement: Final project

You should submit your notebook to Brightspace by the due date listed
above. The submission should include any data or supplementary files needed to
execute your project. The final writeup should be a Jupyter notebook and the
file name should be your last names separated by dashes and a short title ---
something like {\tt Jones-Smith-Zhang.ipynb}.

Your project should include:

**Description cell.**  Put a Markdown cell at the top of your notebook that
includes the title of your project, a list of authors, and a short summary of
what you do.  Think of the last one as an advertisement to potential readers.

**Data.**  Description of data sources and the code to read the data into
Python and reformat it as needed. This should be done in enough detail that
someone else can reproduce what you've done.

**Graphics.**  A series of figures that tell us something interesting. Three
or four would be enough, but do what you think works best for your project.
Think about the narrative:  What story do you want to tell?

# Basic Structure

1. What are the distributions of game genres, developers, and prices on Steam?

    a) Games are divided into many genres on Steam: action, adventure, strategy, etc. We are curious about the proportion of different genres. This may give us a hint about the trend of game market preference.
    
    b) Game developers are greatly diversified. By analyzing the proportion of games developed by different developers, we may learn about market concentration and get to know the key players in this industry.
    
    c) We are also interested in how prices are distributed on Steam. What are the higher priced types of games and why?
What are the most recommended games?

2. The number of recommendations on Steam is an important indicator of trending and qualitative games. We are hoping to make use of this information to find out the games with the highest popularity.

    a) What are the characteristics of those most recommended games?
    
3. For those most recommended games, we are going to further analyze their characteristics and try to answer the reasons for their success.

# Where and how to collect data

Finding out that the official Steam website provides an API for the users, our first plan is to use the requests methods to get data from here. However, the documentation shows that the API only provides information about news, users, and items, without any trace of games. Therefore, an alternative API with all the information we need will be used to collect data: SteamApis(https://steamapis.com/). 

Firstly, we will get all games and apps in the database and extract a list of all 10210 apps’ ids. Then we will use the list of id to get all softwares’ details. In practice there’s a problem when trying to get all ids: the request methods in python can only get the information of about 900 games, and it cannot be fixed when we change other parameters such as timeout. However, if we type the same website in Chrome, a full list of all softwares can be reached. Therefore, we will open the website in Chrome and save the contents as a json file, then open and read the file in python and extract the full list of ids. 

Another problem is the limitation of the requests’ frequency: for users without in-website paying, they can only request at most 100 times per minute or 5000 times per day, but we need 10000+ times of requests to get all data. In order to solve this problem, the list of ids should be divided into 3 small lists(5000+5000+210), and the frequency of the requests should be modified manually to prevent the appearance of error 429. We are still working on the data, and more details will be shown in the following data report. 
