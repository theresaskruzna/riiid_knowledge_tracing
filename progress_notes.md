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

I went through the list of variables and performed some basic analysis on them.
I looked at factors like how many unique values there are, for features with only few categorical values I looked at counts for each of them and had a look at some percentage proportions.
One feature was particluarly interesting - timestamp, as the values are given in miliseconds and the maxium value is 87 BILLION!! miliseconds which I had no idea how that translates to normal time, turns out its nearing the 3 year mark.
That means that the longest standing user of the platform has been active on it for nearly 3 years at the time of creating this dataset.
It would be interesting to see whats their pattern of interacting and how they actually do with answering questions.
Another interesting thing to see I just thought now would be the interaction patter of the person who is the most succesful with their answers so will have to pull that data out of the dataset too.

Day 4 - 11/03/25

I had to work all day today so it was quite tricky to make any progress on the project.
I took my ipad to work and wrote some code for memmory optimisation like dropping a column and defining data types for all columns using chatgpt and claude.
When I finally got home, I copied all the code into my collab notebook and made some changes and polishing.
Next thing I focused on creating some funtions.
First function I made was for checking memory usage.
The next function I coded was to create a KDE plot.
I consulted both chatgpt and claude and sort of merged what I was given by both.
I decided to just create a simple one and keep extra parameters as comments within the function for now so they can be added if I decide to.
I also added comments to each line of the code as that helps me to understand what each line or parameter actually does as I don't want to just copy paste things but actually understand what they do and what can happen if I omit it.

Day 5 - 12/03/25

Again working all day then had a yoga class in the evening oopsies.
So it's 9.15pm now and I don't think I'll get much done today as I usually had to bed by 11pm to get 8 hours of sleep before another long work day.
Righto, I had created a histogram function using the kde plot as an inspo and getting help from claude to alter it.
I want to keep it nice and concise across all the functions as in some ways I am quite the perfectionist.
I managed to create both bar plor and histogram functions and since I am doing these I might as well just do the rest - box plot, scatter plot and heatmap functions.

Day 6 - 13/03/25

Surprise surprise, we have a class today lol - the email about it apparently went out last month but since I was away in Indo/Australia I must have missed it when it probably landed in my spam folder that clears itself each month as it is not in my main inbox. 
Or they just didn't send it to me as it seems that our tutor also had not known we have a class today.
We did go over my project tho and I got some valuable feedback. I do know that this is a challenge as he did confirm that we hadn't really worked on the model, I will most likely need for this project, during our classes but he also didn't flat out say I should abandon this project and do one of the ones he gave us to choose from.
I implemented some of his feedback straight away, for instance, to create a separated file for all my functions to call tghem from.
I think I also finalised all the functions for my visualisations so I can finbally use them in my main code tomorrow.
I promised I'll have a dataframe to work with for modeal building on Monday so that will be my goal for the weekend to finalise the EDA and feature engineering and merge my datasets into a single dataframe.

Day 7 - 14/03/25

Took a break from coding today as my brain was a mush anyway so don't think I would come up with anything decent.

Day 8 - 15/03/25

Rested and ready to jump back in.
Started off with splitting data exploration into a different notebook to keep my main notebook better organised.
Implemented dtypes and usecols into the code for better memory optimisation when reading my file.
So I made a bit of a mess in my files after I decided to take out the data exploration into a different file as I forgot that I renamed myy original file where I kept most of my code and kept working in an alternate on.
I had to do all the changes to my original file again lol.
Next thing on the list was prepping my visualisations.
I copied some predefined functions from a separate file for now but will look into calling them out of that file in the future.
I also added some simple value count and unique value count to the questions.csv and lectures.csv datasets.

I spent few hours by coding visualisations for all feature as well as prepping code for outliers and merging datasets.
Now I am contemplating if to take a break and return to this later or just push through.
It's currently 5.30pm and I have to take the dug out in abou 1-2 hours.
I could probably test run the notebook to see if the code is working as so far I have just been filling the notebook withiut running it lol.

So I did a lot of testing on the code I had written and although I made a huge mess of it at first, I think I managed to get all of it wotking at the end.
Challenge was again the size of the dataset so I had to apply some sampling within my functions for the visualisations and then cross check if they actually work with some sample EDAs from the competition.
I did a basic heatmap for the correlation but to be honest, I am not sure if its telling much.
I also did reorganise my table of contents a bit so it makes more sense.
I am planning to finish off the EDA tomorrow so I can start on some feature engineerings (already have a couple of ideas) and producing a df for modeling that my tutor requested to be ready by Monday class.
Time for bed now as it's nearly 11pm.
