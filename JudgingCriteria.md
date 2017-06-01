#Judging Criteria

This document shows where to get the test data set, and explains how the judging will be done for the "Best Classification" system. 

Read the [Step 1: Get Data tutorial](../tutorials/Step_1_Get_Data.ipynb) for information on where to get the training and test data sets. 

## Test Data Set

Once you've trained your model, done all of your testing, and tweaks and are ready to submit an entry to the contest, you'll need to download the test data set and apply your model to that.  

The test data set is similar to the labeled data, except that the JSON header is missing the 'signal_classification' key, and just contains the 'uuid'. 

Like the other sets, this set is found in a `.zip` file in the `simsignals_v2_zipped` container;

https://dal.objectstorage.open.softlayer.com/v1/AUTH_cdbef52bdf7a449c96936e1071f0a46b/simsignals_v2_zipped/primary_testset.zip

There are approximately 1000 simulations of each of the 7 signal classes -- but not exactly 1000 (+- some largeish number) so you can't cheat :). 

See the [Judging Criteria document](https://github.com/setiQuest/ML4SETI/blob/master/JudgingCriteria.md) for more details.

#### UUID list

https://dal.objectstorage.open.softlayer.com/v1/AUTH_cdbef52bdf7a449c96936e1071f0a46b/simsignals_files/public_list_primary_testset_1june_2017.csv

### Generate CSV File with Scores

For each simulated file in the test data set , your job is to create a CSV file where each line contains the UUID, followed by scores for each signal class. The signal class with the highest score would be your model's class estimation. 

For example, each line in the CSV file should look like:

  * `abdefg-adbc12-23234-123123-cvaf, 0.1, 0.023, 0.451, 0.232, 0.001, 0.07, 0.0083`

**THE COLUMN ORDER OF THE NUMBERS IS CRITICAL! THEY MUST BE THE SCORE FOR EACH CLASS IN THIS ORDER:**

  * `uuid, brightpixel, narrowband, narrowbanddrd, noise, squarepulsednarrowband, squiggle, squigglesquarepulsednarrowband`

In the example above, the `abdefg-adbc12-23234-123123-cvaf` would be labeled as a `narrowbanddrd` because it has the highest score. 

### Measured by Logistical Loss

In this contest, because we are using all the scores, we'll use the [LogLoss function](http://scikit-learn.org/stable/modules/generated/sklearn.metrics.log_loss.html) as a measure of your model. These details will be found in an upcoming notebook. There will be a website that you use to submit your CSV file containing the scores for your team. This website will also contain a scoreboard. This will be implemented **after** the hackathon on June 11th -- more details to come. 

## Submit Your Results

