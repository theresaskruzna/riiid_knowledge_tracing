# Progress notes

From the beginning this was going to be a challenge, however, that makes it more interesting and a learning curve.

The Riiid dataset was an original dataset for a kaggle competion from about 4 years ago.
The person who won it created a very sophisticated model, however, my initial approach will be more basic in the eyes of skilled ML engineers.

I started with consulting chatgpt and claude on the best way to approach this project.
With the help of these 2 chatbots, I managed to generate a pretty decent action plan for the next 2+ weeks until the deadline.
I created a github repository and set up set up google collab notebooks for this project.

After important some basic libraries to start with, the first issue I ran into was that the usual downloading through kagglehub that my course lecturer showed us wasn't avaliable.
This might have been due to the fact that it was a competition using Kaggle API for submissions.
I didn't want to waste time trying to figure out how to use kagglehub so I consulted with chatgpt and Claude.
They both usggested dowloading Kaggle API package and dowloading a directory with the dataset into my home folder.
That is what I did to get the dataset into my collab notebook.

Next issue I ran into was that the main file train.csv was too large (5.85GB) as it contains 100+ millions of rows of data.
This made my runtime crash as I ran out of RAM. I could've tried using Pycharm or VScode but am sure my laptops RAM and CPU are even worse.
I spent quite few hours trying to figure out the best way around it, eg. converting .csv to pkl.gzip, but other options also needed significant memory to run.
Eventually, I found a dataset on kaggle that was already converted and of high quality and used it to replace train.csv file with.
Now I managed to load all required into the notebook I can finally start my EDA for this project.

I have run into another bump, loading the pickle dataset as of now I am downloading a whole directory of other formats too but I don't need them.
I will have a look at fixing that tomorrow to just download the single data set out of the directory but for now it has already loaded the director so will be working with it in this runtime session to analyse my data.

I am just testing all the code cells i prepared to start my EDA and my runtime keeps crashing on some of them.
This super frustrating but at least I can see what code won't be working and where I have to use alternate methods.
I finally managed to get to the last code cell I wanted to test.
There are 2 code cells for the EDA that crashed the session: .describe for individual features and .duplicated to find duplicates in the dataset.
I will try and fix that tomorrow as some of the data types in the data set need to be changed, e.g. object to boolean.
This will hopefully help with the code running more smoothly.
Once I sort out some of the issues with the data, I'll do some visualisations to see distributions and relationships and draw out some hypothesis for my analysis and forecasting.
From looking at the datasets and decription of the compettion, I have identified answered_correctly as the target variable.
