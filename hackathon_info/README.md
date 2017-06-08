# Hackathon Specific Information

The following document provides most of the information you need to know at the hackathon.



<br>

## Team Formation

After breakfast and the opening talks, we'll help you to form teams. 

1. Acknowlege already constructed teams.
2. Identify ML/DL experts
3. Identify Doman Knowledge experience (SETI@IBMCloud folks, signal processing experience)
4. Identify ML/DL non-beginners
5. Identify strong coders
6. Identify beginners

Coalesce into teams that have a mix of the above.
 

### Fill In Team Handout

1. Quickly Decide Team Name
2. Designate a Spark Enterprise master from team (must have IBM DSX account)
3. Fill in the top portion of Team Handout
4. An IBMer will pick up your handout and return this to you shortly.

<br>

## Sign on to the Scoreboard

1. Each team member should sign in to the main SETI Hackathon Event at https://compete.cognitiveclass.ai/
2. Designate on team member to be the team scoreboard master.
3. [Follow this complete walkthrough for signing on to the Scoreboard.](https://ibm.box.com/v/competitionwalkthrough)
4. The team master will invite all team members by email and submit scores.
5. Use the link below to the Mini Test Set to submit an example score
6. Perform your analysis and submit further results.
7. Note that we have 3 scoreboards: Best Classifier, Best Signal Processing, Best Classifier without NN/Watson
7. Any teammate can submit a result to any of the three Scoreboards

### Mini Test Set

In the interest of time for the hackathon, we'll be using a reduced test data set for scoring. It's about 1/5 the size of the normal primary test set. (In the case of needing a tie break, we'll use more test data.)

Mini Test Set: [example_hackathon_scorecard.csv](https://dal.objectstorage.open.softlayer.com/v1/AUTH_cdbef52bdf7a449c96936e1071f0a46b/simsignals_files/example_hackathon_scorecard.csv)

As a test, submit this scorecard to the scoreboard to ensure you're up and running. 

<br>

## Team Code Repository

Choose one team member to be the team code master. The code master should either

  * Create a Github repository to hold your code that you develop from scratch. 
  * Recommnded: Fork this github repository: [https://github.com/setiquest/ml4seti](https://github.com/setiquest/ml4seti) into your Github account. You can then use the code here as a starting point. 

Team code masters can invite teammates to collaborate through the GH repo Settings.

<br>

## How to Work

**You can run your team in whatever way you wish.** But we do have two suggestion that could maximize your strengths and compute resources. 

We suggest that you 

1. Discuss the strengths and weakeness of each member of your team. 
2. Split your team into two or three groups:
  * Group 1 operate on the Spark Enterprise cluster to focus efforts on Signal Processing techniques.
  * Group 2 operate on the PowerAI system to focus on building neural network classifiers. 
  * Group 3 focus on feature engineering using standard DSX account or laptop data science environment.

The idea is that later on Saturday evening you can begin to pool your work together into a coherent strategy. Additionally, by splitting up, you can submit results for all three scoreboards. 

##### Go For A Narrow Focus

Another suggestion is for your team to focus entirely on one aspect/contest of the hackathon and use all of the compute resources you have available to that aim. 


<br>

## Use Slack

Feel free to create your own team channel if you wish. Also, you may create other channels to discuss particular aspects. A number of channels have already been created, so please join the channels you find useful and begin collaborating and asking questions. 


<br>

## Where to Work

You can use a combination of your laptops, IBM Data Science Experience, IBM PowerAI systems, or even other external cloud providers. It depends on whichever you're most comfortable with -- perhaps you've a full data science environment set up already on your laptop or elsewhere and wish to start there. 

Read below though for how to access the computing resources we've gathered for this weekend.  



<br>

## Setting up PowerAI

Designate a team member to be the PowerAI master. You will use PowerAI systems to build neural network classifiers that require GPU acceleration for training. 

An IBMer will return your Team Handout to you shortly. It will contain the login credentials to your Nimbix Cloud account.

[Your PowerAI master should follow the instructions here to get started.](https://ibm.box.com/v/nimbixsetup)

### Overnight PowerAI Job

On Saturday evening, before you leave, feel free to launch a long job on PowerAI that can run overnight. 

Otherwise, if you do not plan to use PowerAI overnight, please shut down your instance to save on costs. 

### Saving Your Work

When you power down your Nimbix Cloud machine, all data in your local directory will be lost. You can use 
  
  * sftp
  * git commits 
  * File -> Download Jupyter Notebooks to save code from Nimbix. 



<br>

## Using Spark Enterprise

Your team's Spark Enterprise master will eventually find a new project in their DSX account. It will be named

  * `<team name>_Enterprise_SETI` or `<team name>_Enterprise_Spare`

[Here are instructions for using DSX if you're not familiar.](DSX-notebook-setup.md)


### Play Nice!

The most important thing to remember when using the Enterprise cluster is that all teams are sharing this cluster with you. Thus, we ask you to play nice.

  * CREATE and SAVE data only to your local 'team_name' folder.
  * Do NOT write to the local `data` directory

    ```
    import os
    setidata = os.environ['PWD'] + '/data/seti' #NEVER WRITE TO THIS DIRECTORY

    # Create your local team folder
    teamdata = os.environ['PDW'] + '/team_wombat'
    if os.path.exists(teamdata) is False:
      os.mkdir(teamdata)
    ```

  * RUN only ONE Notebook on the Enterprise cluster at a time. (There is a maximum of 10 pyspark kernels allowed on IBM Spark clusters and we are sharing clusters across all teams.)
  * You will eventually need to [save any results to an Object Storage Account to get data from the Spark local file system.](../tutorials/General_move_data_to_from_Object_Storage.ipynb).  You should use you personal Object Storage Account. Here are the steps to get your Object Storage credentials. See Adam, Patrick or Joseph if you need help. 

        1. Log in to https://bluemix.net (use DSX credentials)
        2. Scroll down and click on an Object Storage instance
          * Provision a new Object Storage instance if one does not exist
        3. Select the Service Credentials tab and View Credentials
        4. Copy these into your notebooks where appropriate.


<br>

## Data Location


The `primary_small`, `primary_medium` and `basic` data sets are found in three locations: 

1. Local file space on the Spark Enterprise Clusters in `data/seti`
2. Shared disk on Nimbix/PowerAI in `/data/set`  (note the leading `/`)
3. IBM Object Storage with fast network connection to Spark Enterprise Clusters.

### Data Access Strategy

1. Use index file -- list of UUID, SIGNAL_CLASSIFICATION
2. Read each UUID from the file
3. For each "UUID.dat", retrive that data file from local file space or IBM Object Storage

[This Notebook demonstrates how to access data from all three locations.](GetData_Hackathon.ipynb) When you're using the Spark Enterprise Clusters, we recommend you first try accessing the data in the local file space. If that becomes problemmatic, switch to using IBM Object Storage.

### Good Starting Point!

We also recommend that this example notebook be a starting point for your analysis since you can quickly begin to adapt the data retrieval code and perform some operations. 


<br>

## Awards

Awards for the following contests will be handed out at the end of the day on Sunday. 

Your team can submit results for all of the contests in the hackathon. However, in order to spread the joy, no team can win more than one contest. 

### Best Classifier

This is the top prize for the weekend. Scoring will be done [on the main Scoreboard](https://compete.cognitiveclass.ai/event/5931b5814d48c70020ba8abc) and any classification method may be used. 

Judging will be based on the `primary_testset_mini` data set. 

We will only ask the top 2 or 3 teams make a presentation on Sunday to explain their methods (depending on time).

**Prize**: Organized trip to the Hat Creek Radio Observatory & Allen Telescope Array, Trophy, SETI Hat, SETI Certificate and group photo.

### Best Signal Processing

This prize focusses on finding the best ways to improve the signal-to-noise ratio of the particular signals of interest. Judging will be done using Watons Visual Recogntion. Teams should focus on finding ways to pre-process the
time-series data into 2D images (spectrograms most likely, or possibly other representations) in a way that makes each signal class more distinguishable.  Teams will then package their training images into .zip files and construct a custom classifier with IBM Watson Visual Recognition. 

See an example in [Step_4_Classify_with_WatsonVR notebook](../tutorials/Step_4_Classify_with_WatsonVR.ipynb).

Use the Watson VR Key found on your Team Handout. Be sure to use bulk uploads for classification. That is, submit many test set spectrograms as `.zip` files in one API call. (We have only 50,000 HTTP requests to Watson each day.)

[Submit your scores to the appropriate ScoreBoard.](https://compete.cognitiveclass.ai/event/5937199623f594001f1d6c8d)

In order to win, you must present your methods, and show your code. 

**Prize**: Trophy, SETI Hat, SETI Certificate and group photo.

### Best Classifer without NN or Watson

This is aimed at a combination of signal processing, smart feature engineering and classification approaches that do not use deep learning / neural nets, such as using SVMs. 

[Submit your scores to the appropriate ScoreBoard.](https://compete.cognitiveclass.ai/event/59374590e1965300201e876f)

In order to win, you must present your methods, and show your code. 

**Prize**: Trophy, SETI Hat, SETI Certificate and group photo.


### Most Interesting / Surprising Analysis

This is a subjective award that will be decided upon by our judging panel of SETI and IBM researchers. All teams will have the opportunity to present their work even if they do not place a top score. As teams present their works, the judging panel will note each team's approach and award this prize to the team that purused a particularly interesting aspect. 

**Prize**: "Trophy", SETI Hat, SETI Certificate and group photo.


### Presentations

Presentations do not need to be highly-polished talks. Please just make one or two slides that highlight the tools and techniques that were employed and then show some example code and results. Aim to keep presentations under 7 minutes long and we'll allow 3 minutes for questions. 

[Here is a template.](https://ibm.box.com/v/setipresentationtemplate)


<br>

## IBM Developer Works TV

A videographer will be present during part of the weekend. When you arrive, you were asked to Opt-In (or out-of) a videography and photography waiver. If you are opting out, make sure you have the sticker on your badge. If staged group photos are taken, it is your responsibilty not to be in them.

Hackathon Winners will be offered the chance to be interviewed after the Awards presentations on Sunday. 

The footage captured over the weekend will be used to construct an IBM webpage that is meant to highlight the SETI research and citizen scientist community.  


## Help!

We are all here to help and will be available throughout the weekend for any technical or scientific questions. 



