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
