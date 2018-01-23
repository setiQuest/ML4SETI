# Getting Started


The following tutorials show you how to get started: from getting the data to some example analysis.  We intended to make access and analysis as democratic as possible: there's no platform or language requirements. However, in the tutorials below, we've used Python 2.7 Jupyter notebooks running on [IBM Data Science Experience (DSX)](https://datascience.ibm.com). Additionally, some of the tutorials use Apache Spark and IBM Object Storage, which are automaticlaly provided by DSX.
If you do create a DSX account, these tutorials below will work well in that environment with little configuration needed (you will need to install a few additionaly Python packages). But these tutorials should be instructive enough to get you started in any environment.

### Tutorials

One thing to note: The `ibmseti` package released version 1.0.5, used in some of the steps below, only works on Python 2.7 at the moment. If you need Pythonn 3 support, `pip install ibmseti==2.0.0.dev5`

  * [Step 1: Get Data](tutorials/Step_1_Get_Data.ipynb)
  * [Step 2: Reading Data and Creating Spectrogram](tutorials/Step_2_reading_SETI_code_challenge_data.ipynb)
  * [Step 2b: List of Signal Classes](tutorials/Step_2b_List_Of_Signal_Classes.ipynb)
  * [Step 3: Build PNG Files](tutorials/Step_3_Build_Set_Of_PNG_Files.ipynb)
  * [Step 4: First Classifier with Watson Visual Recognition](tutorials/Step_4_Classify_with_WatsonVR.ipynb)
  * Step 5: TensorFlow and Neural Nets
    - [A: Intro to Tensorflow](tutorials/Step_5a_Intro_To_Tensor_Flow.ipynb)
    - [B: Understanding Convolutional Neural Nets](tutorials/Step_5b_Underestanding_CNN.ipynb)
    - [C: Convert SETI data to Binary Files](tutorials/Step_5c_Convert_TS_to_unit8Dataset_DSX.ipynb)
    - [D: Build CNN in Tensorflow](tutorials/Step_5d_Build_CNN_Tf_DSX.ipynb)


### Other Information

  * [Moving Data To and From IBM Object Storage](tutorials/General_move_data_to_from_Object_Storage.ipynb)
  * [Moving Data To and From your Nimbix Cloud](tutorials/General_move_data_to_from_Nimbix_Cloud.ipynb)
  * [Connect your IBM DSX Account to an existing AWS EMR cluster](https://apsportal.ibm.com/docs/content/analyze-data/aws-emr.html)

### Judging

See the [Judging Information](Judging_Criteria.ipynb) document for information on setting up your team and submitting a score card to the Scoreboard.

### BUGS

There are bound to be bugs, problems and questions. Please submit bug reports to the "Issues" 
in this GitHub repository. 

You can also chat with organizers and other participants on our [Slack Team](https://ml4seti.mybluemix.net/).
