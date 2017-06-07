# Hackathon Specific Information

The following document provides most of the information you need to know at the hackathon in SF-Galvanzie on June 10-11, 2017

This information is organized in the order of how the hackathon will proceed. 


## Team Formation

After breakfast and the opening talks, we'll help you to form teams. 

Once you've identified your teammates, you should determine your team name and identify two representatives for your team. One representative must have an IBM Data Science Experience (DSX) account, who will be the team representative for the Spark Enterprise cluster. The other will be the representative for the PowerAI machine. Choose one team member to bring the team name, the names and email addresses of the two team representatives up to the front where we will register your team on those systems. 


## Sign on to the Scoreboard

1. Each team member should in to the SETI Hackathon Event at https://compete.cognitiveclass.ai/
2. Designate a team scoreboard master.
3. The team master will Submit a test score and invite all team members by email (use the link below for test set).
4. Perform your analysis and submit further results.

TODO: remove above and put in link to Daniel's walkthrough document on Box. 

### Mini Test Set

In the interest of time for the hackathon, we'll be using a reduced test data set for scoring. It's about 1/5 the size of the normal primary test set. (In the case of needing a tie break, we'll use more test data.)

Mini Test Set: [https://dal.objectstorage.open.softlayer.com/v1/AUTH_cdbef52bdf7a449c96936e1071f0a46b/simsignals_files/example_hackathon_scorecard.csv](https://dal.objectstorage.open.softlayer.com/v1/AUTH_cdbef52bdf7a449c96936e1071f0a46b/simsignals_files/example_hackathon_scorecard.csv)

## Team Code Repository

Choose one team member to be the code master. You can make your own GH repo to hold your code, but one suggestion is for the code master to fork our github repository: [https://github.com/setiquest/ml4seti](https://github.com/setiquest/ml4seti) into their own account. You can then use your own fork of this repository as a starting point. You can invite your teammates to collaborate through the repo Settings.

You should 
After you've logged in to your PowerAI system on Nimbix Cloud, we recommend that you clone this Github repository in order to easily download the tutorials found here. You'll want to run the 'Step 5' tutorials that use TensorFlow to build neural net models on these PowerAI systems. 

```
git clone https://github.com/setiQuest/ML4SETI
```

## Setting up PowerAI

[Please follow the instructions here.](https://ibm.box.com/v/setipowerai)

TODO: include in instructions for team to clone their code repository BEFORE launching the jupyter notebook. 

When you access your Jupyter notebook, you should see these tutorials in your local user space, which you can then copy and/or modify. 

### Data Location


There are multiple ways of accessing the data during the hackathon. There are

  * zipped `small` and `medium` primary data sets on both Spark Enterprise and PowerAI
  * full `primary` data set on Spark Enterprise
  * data available on Object Storage


As such, there are different ways you can write your analysis.

We've created these redundancies to ensure we can work around any potential problems or bottlenecks. 



## Using Spark Enterprise


### Setup

  1. Form Team
  2. Sign up for https://datascience.ibm.com (DSX)
  3. Register Team with Adam
    * one account per team
  4. Find the shared Project in you DSX account
  5. Use only ONE notebook (one pyspark kernel) at a time in the Enterprise account
    * Your kernel doesn't die when you close the Notebook --> make sure to call "Stop Kernel" from the project page.
    * Use your personal free-tier Spark service for prototyping

### Play Nice!

The most important thing to remember when using the Enterprise cluster is that all teams are sharing this cluster with you. Thus, we ask you to play nice.

  * Save data only to your 'team_name' folder, which you must create.
  * Do NOT write to the local `data/` directory

    ```
    import os
    setidata = os.environ['PWD'] + '/data'
    teamdata = os.environ['PDW'] + '/my_team_name'

    if os.path.exists(teamdata) is False:
      os.mkdir(teamdata)
    ```
  * Run only one Notebook on the Enterprise cluster (There is a maximum of 10 pyspark kernels allowed on IBM Spark clusters.)

### Data Location


There are multiple ways of accessing the data during the hackathon. There are

  * zipped `small` and `medium` primary data sets on both Spark Enterprise and PowerAI
  * full `primary` data set on Spark Enterprise
  * data available on Object Storage


As such, there are different ways you can write your analysis.

We've created these redundancies to ensure we can work around any potential problems or bottlenecks. 



##### Use the filelists

Because the data are stored locally, your executor nodes can directly access the data files.  

```
filecontents = open("data/seti/simsignals_files/public_list_primary_v2_medium_1june_2017.csv").read()
primary_medium_files = [line.split(',') for line in filecontents.split('\n')]
primary_medium_files = full_primary_files[1:-1] #strip the header and empty last element
primary_medium_files = map(lambda x: x[0]+".dat", full_primary_files)  #now list of file names (<uuid>.dat)

rdd = sc.parallelize(primary_medium_files, 60)
datafolder = os.environ['PWD']

def processdata(row):
  aca = ibmseti.compamp.SimCompamp(open(datafolder + "/" + row, 'r').read())
  spectrogram = aca.get_spectrogram()

```

## Awards

The following awards will be handed out at the end of the day on Sunday. 

Your team can take aim at all of the awards in the hackathon. However, in order to spread the joy, no team can win more than one award. 

### Best Classifier

This is the top prize for the weekend. Scoring will be done with the Scoreboard and any method may be used. 

Judging will be based on the `primary_testset_mini` found in `simsignals_v2_zipped`.

We will only ask the top 2 or 3 teams make a presentation on Sunday to explain their methods (depending on time).

### Best Signal Processing

This prize focusses on finding the best ways to improve the signal-to-noise ratio of the particular signals of interest. Judging will be done using Watons Visual Recogntion. Teams should focus on finding ways to pre-process the
time-series data into 2D images (spectrograms most likely, or possibly other representations) in a way that makes each signal class more distinguishable.  Teams will then package their training images into .zip files and construct a custom classifier with IBM Watson Visual Recognition. 

#### This award does NOT use the Scoreboard. 

A separate "test" set is provided for self-scoring. One should not use this 

Once they have completed the training of their Watson VR custom classifier, teams should measure their classification accuracy with their reserved test set. See the [Step_4_Classify_with_WatsonVR notebook](../tutorials/Step_4_Classify_with_WatsonVR.ipynb).

Teams will present their work and show their final notebook and calculation as verification. As such, this award is based on an honor system and we trust that teams will be respectful. 


### Best Classifer without NN or Watson

This is aimed at a combination of signal processing,  smart feature engineering and classification approaches that do not use deep learning / neural nets. 

This award is also given based on the honor system. Teams should reserve part of the primary training set
This is very similar to the "Best Classifer" award in that teams should post their results to the Scoreboard using the `primary_testset_mini` test set. However, make sure to indicate **FUCK*** There needs to be a way for teams to submit multiple results... otherwise, this needs to be done on the honor system as well because teams wouldn't be able to submit   

However, teams will need to briefly present their methods and results. 

### Most Interesting / Surprising Analysis

This is a subjective award that will be decided upon by our judging panel of SETI and IBM researchers. As teams present their works, the judging panel will note each team's approach and award this prize to the team that purused a particularly interesting aspect. 

#### Presentations

Presentations do not need to be highly-polished talks. Please just make one or two slides that highlight the tools and techniques that were employed and then show some example code and results. Aim to keep presentations under 7 minutes long and we'll allow 3 minutes for questions. 


## Organize Your Teams

You will have access to one PowerAI system and one Spark Enterprise Cluster. We suggest that you split your team in a way that one subset works on signal processing techniques with the Spark cluster,  another subset focuses on building out a NN on PowerAI and potentially a third subset focuses on different feature extraction techniques that could feed into a classification system.  This way your whole team can potentially submit a result for each contest. Your team should organize, create a plan and periodically check in as a whole to exchange useful code. 

### Overnight PowerAI Job

On Saturday evening, before you leave, feel free to launch a large job on PowerAI that you can set up to run overnight. 

If you do not plan to use PowerAI overnight, we please ask that you shut down your instance to save on costs. 


## IBM Developer Works TV

## Saving Your Work




