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

Day 9 - 16/03/25

So I started today with a bit of a panic.
I DID NOT SAVE MY LAST MODIFICATIONS YESTERDAY!!
What an idiot but obviouslyy we learn from mistakes right.
I had to do all the modifications to my functions and visualisations again and also reorganise the table of contents again.
But maybe it's for the best as I think I made a bit of a mess of everything yesterday and today I got to start over with it and knew exactly what I wanted to have at that point.
I also spent a few hours coding for missing values and outliers and I think I got to a point where I am ok with it. It was really hard to determine what is the outliers in this dataset but at the end I decided it could be the user engagement, e.g, the people who barely used the platform.
As of now I set that to 1% of all users but I might play around with it later.
I really need to focus on creating a data frame for modelling so I want to pretty much merge all 3 data sets together as both questions.csv and lectures.csv have foreign keys for train.csv dataset so hopefully merging it wont be a pain.

OK so I think I put in quite the work today.
I have worked on feature engineering - I performed one hot encoding on features in both questions_df and lectures_df, I also came up with a few ideas for new features to be added and prepped the code for them.
I have got a function to merge all 3 datasets and prepped some stuff for train/test split.
There are 2 approaches I can take, either take the last 5 latest answers from each user in the dataset for a validation set, or (which I incline to more) group users by their activity level and then do a train/test split.
There is actually so much code in my notebook now that I am starting to get lost in it even though I am keeping the table of contents pretty neat so might need to do something about that.
I might be dine for today as again my brain is not really braing anymore and my upper back hurt like hell.
I do have work all day tomorrow which will be quite tricky since my computer needs to be connected to an external monitor but I'll see if I can get some stuff done on my ipad, at least make a list of questions for the tutor and make sure I do have a working data frame for him to see and help me build a model with.

Day 10 - 17/03/25

I managed to prep a bit of work on the ipad at work but could only really code when I got back home.
I wasn't too happy about the feedback I received from my lecturer as last week he told me just sack my perfectionism off and make sure I have done all the steps to get to a working data frame.
That is what I did but he complained that my code is too messy and he can't read it, however, I know what has been done so why does that matter plus he did say that right now I shouldn't care if its messy.
Also I found out at the start of the lesson that I am technically supposed to be presenting this online next monday so that kinda changes things and my timeline lol.
The code unfortunatelly keeps crashing on my laptop as it is a piece of sh*t so my tutor suggested I just get a sample out of the data so I can at least find out if my code is coding.
I tried to use 'chunksize' but it would take forever so using dask and sample of a 100k rows which is decent enough.
I am not working the morning so will put in some work.

Day 11 - 18/03/25

I managed to get up early enough today so I can code for coupla hours before going.
I've got everything done up until train/test split.
I think I managed to fix all the merging issues and got the one hot encoding working.
The sample is not the best as it doesn't represent the data properly but it works enough to find out if the code is ok.
I have created an extra feature to calculate knowledge growth rate as something similar was done in another notebook on kaggle.
I am also saving all the code I am working on with the sampled dataset into a new branch as I dont want to mix the code at the moment.

When I got back at the evening, I started on building a model. I opened a new separate notebook for it and had a look at some past projects, e.g. chess figures, we did in the class to know where to start or if there is also any code I could copy and modify to nmy needs.
I also consulted my bestie Claude and together we decided to use a LSTM based model using tensorflow keras API.
I discussed this with the lecturer once he had a minute for me and he approved of it.
He also said that he's more hopeful for my project now and that it looks like I know what I am doing and that he previously had someone who also was a bit ˇbehind' because they had a more challenging project and it ended up being one of the best out of the group so that was nice to hear.
I think him doubting me before I also started doubting myself which isn't great as I do think I can managed this.

I build a pretty simple sequential neural network model with few options to modify it to make it more layered.
I got early stopping and model checkpoint done.
And I started coding the training bit for the model.
Tomorrow is another day so will continue then plus I know that I will do most of it at the weekend anyway.

Day 12 - 19/03/25

We have our last class with the tutor befor the mock up presentations and my dug is sick which is great timing.
I didnt do any progress during the day and once I finally properly hopped on the call I loaded all my code needed to run the model and just went for it.
It needed a few tweaks but it actually ended up running which was a bit of a surprise to me lol.
The accuracy stands at about 64% and it ran for 11 epochs, it's not great but considering that the winning model of the kaggle competition had accuracy of roughly 81%, its a good start.
The lecturer said it was ok and I should focus on playing with the model now to raise the accuracy and evaluation.

Day 13 - 20/03/25

Took a day off from coding today as it was first day of spring and finally gorg weather here so took the dug out for a big walk after work and the just chilled.

Day 14 - 21/03/25

Did nothing again lol.
The good weather doesnt make me want to sit at a computer and code.
Plus we were out most arvo with my sister and the dug again.

Day 15 - 22/03/25

Had a slow morning today and then took the dug out for a big walk again so finally got around working on the project again after 4pm.
I started with organising the sections and cleaning the code, getting rid of stuff that is not needed.
I had to switch around the order of train test split and scaling as I found out that if you scale both x and y before train test split it can lead to data leakage plus y variable is already a binary value (0, 1) so it doesnt need to be scaled.
There is quite a bit of work to be done on the modeling but I will leave that for tomorrow.
I managed to organise the sections a bit better today so the notebook flows and removed code that I don't need or like.
Plan for tomorrow is to organise the EDA section, train and evaluate the model and start on my presentation slides.
I am also crating another branch off the main one just cos I did a lot of amendments on the chunksize one and probably want to focus on few different bits without changing that.
I decided to keep everything in one notebook for the purpose of presenting the project so need to organise the sections and different notebooks on github.

Day 16 - 23/03/25

I started a bit earlier today as the weather isnt great so it was just a quick walk with the dug.
I filled in some more info into my presentation.
I chose a pretty simple format in google docs for the mock up presentation but I might make it more interesting for the final exam.
I also added info about all variables into my main notebook.
Next thing I did was consulting my bestie Claude on how to evaluate my model and gpt some code prepped.
I noticed I had not done a validation split in ma data that I will later need for the evaluation so I went back and corrected that.
If my dataset was small, I could do cross validation instead of having to split the validation set but the dataset is huge.
