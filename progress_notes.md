# Progress notes

From the beginning this was going to be a challenge, however, that makes it more interesting and a learning curve.

The Riiid dataset was an original dataset for a kaggle competion from about 4 years ago.
The person who won it created a very sophisticated model, however, my initial approach will be more basic in the eyes of skilled ML engineers.

Day 1 - Saturday 08/03/25

I started with consulting chatgpt and claude on the best way to approach this project.
With the help of these 2 chatbots, I managed to generate a pretty decent action plan for the next 2+ weeks until the deadline.
I created a github repository and set up set up google collab notebooks for this project.

After important some basic libraries to start with, the first issue I ran into was that the usual downloading through kagglehub that my course lecturer showed us wasn't avaliable.
This might have been due to the fact that it was a competition using Kaggle API for submissions.
I didn't want to waste time trying to figure out how to use kagglehub so I consulted with chatgpt and Claude.
They both usggested dowloading Kaggle API package and dowloading a directory with the dataset into my home folder.
That is what I did to get the dataset into my collab notebook.

Day 2 - Sunday 09/03/25

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

Day 3 - 10/03/25

Let's start with fixing the issue of loading the unessential data converted data sets.
I am again consulting claude on this matter, I really prefer claude to gpt as it has more query allowance to chatgpt and úrovides better and cleaner code.
I did quite an extensive research on comparing them both and it did say claude is better for this purpose - I might even pay for the plus version.

Right so the initil approach for downloading just the one file doesn't work and the other that claude suggested seems to complicated.
I saved the alternate code to my 'extra code' section and might come back to it later or ask the tutor next week whilst I am working with what I already tested to be working so I am not wasting time.

Next task on the list is fixing the data types in my dataset so it loads faster.
The one that definitely needs fixing is 'prior_question_had_explanation' as its meant to me boolean which is even written in the feature list of the og Riiid dataset.
I have also cross checked all other variables and the other one that stands out is 'answered_correctly' as it only has 3 values (-1, 0, 1).
In the feature list it states that -1 is to be treated as 0 so using boolean here too could be beneficial.
The author of the pickle dataset has already converted 'content_type_id' into boolean so he saved me a job there.
Next thing I did was to check if the int64 and int32 variables need to stay this format using .max function.
Coverting them to a lower integer format could save me some more needed memory space.
Last but not least, 'prior_question_elapsed_time' is currently float64 since it has decimals but because it's already in miliseconds and 'timestamp' doesnt have decimals I am thiking to covert it to int32.
It's kind of annoying that our next class with the tutor isn't until next monday as I need to keep progressing to make it to the deadline.
And staying in that thursdy class wouldn't make any difference as I only got to this point after 2 days of playing around with the dataset.

Next one up today, we have sorting out the questions.csv and lectures.csv datasets.
These datasets are much smaller than train.pkl.gzip.
I had a look at the data types and will be changing unnecessary int64 to int16 and int8 accordingly.
Both datasets have 4 features, no duplicates and only questions.csv has 1 missing value for the 'tags' variable so will most likely just get rid of the row where it's missing.
The next thing I should be doing is some data visualisations on key distributions and relationships within the datasets before I start on my feature engineering.

Right, I decided to deal with the 1 missing value in the question.csv as it was easy enough.
I first cross checked the representation of this particular question in the train.pkl.gzip dataset but as it was only asked once in this huge dataset, I decided to delete it altogether.
I can see that the 3 datasets are pretty interconnected as we see features like question_id from the smaller ones represented in the main dataset.
So I'll have a look at each variable now and how it may be connected to the other datasets.


