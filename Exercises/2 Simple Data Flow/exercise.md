My solution of grep.py and grepc.py are also in this folder.
### Overview

In this lab, you learn how to write a simple Dataflow pipeline and run it both locally and on the cloud.

What you learn
In this lab, you learn how to:

1. Write a simple pipeline in Python

2. Execute the pipeline on the local environment

3. Execute the pipeline on GCP

### Introduction

The goal of this lab is to become familiar with the structure of a Dataflow project and learn how to execute a Dataflow pipeline.


### Create a virtual environment

Execute the following command to download and update the packages list.

``` shell
sudo apt-get update
```


Python virtual environments are used to isolate package installation from the system.
``` shell
sudo apt-get install virtualenv

virtualenv -p python3 venv
```

Activate the virtual environment.
``` shell
source venv/bin/activate
```

### Open Dataflow project

#### Step 1
In the CloudShell and clone the source repo which has starter scripts for this lab:

``` shell
git clone https://github.com/GoogleCloudPlatform/training-data-analyst
```
Then navigate to the code for this lab:
``` shell
cd training-data-analyst/courses/data_analysis/lab2/python
```
#### Step 2
Install the necessary dependencies for Python dataflow:
``` shell
./install_packages.sh

```

### Pipeline filtering

#### Step 1
View the source code for the pipeline using the Cloud Shell file browser:


In the file directory, navigate to /training-data-analyst/courses/data_analysis/lab2/python.


Find __grep.py__.

#### Step 2
What files are being read? _____________________________________________________

What is the search term? ______________________________________________________

Where does the output go? ___________________________________________________

There are three transforms in the pipeline:

What does the transform do? _________________________________

What does the second transform do? ______________________________

Where does its input come from? ________________________

What does it do with this input? __________________________

What does it write to its output? __________________________

Where does the output go to? ____________________________

What does the third transform do? _____________________


### Execute the pipeline locally
#### Step 1
Execute locally:
``` shell
	python3 grep.py
```

_Note: if you see an error that says "No handlers could be found for logger "oauth2client.contrib.multistore\_file", you may ignore it. The error is simply saying that logging from the oauth2 library will go to stderr._


#### Step 2
Examine the output file:
``` shell
cat /tmp/output-*
```
Does the output seem logical? ______________________


### Execute the pipeline on the cloud


#### Step 1
If you don't already have a bucket on Cloud Storage, create one from the Storage section of the GCP console. Bucket names have to be globally unique.

#### Step 2
Copy some Java files to the cloud (make sure to replace <YOUR-BUCKET-NAME> with the bucket name you created in the previous step):
``` shell
		gsutil cp ../javahelp/src/main/java/com/google/cloud/training/dataanalyst/javahelp/*.java gs://<YOUR-BUCKET-NAME>/javahelp

```

#### Step 3
Edit the Dataflow pipeline in __grepc.py__ by opening up in the Cloud Shell in-browser editor again or by using the command line with nano:
and changing the PROJECT and BUCKET variables appropriately.


#### Step 4
Submit the Dataflow to the cloud:
``` shell
python3 grepc.py
```

Because this is such a small job, running on the cloud will take significantly longer than running it locally (on the order of 2-3 minutes).


#### Step 5
On your Cloud Console, navigate to the Dataflow section (from the 3 bars on the top-left menu), and look at the Jobs. Select your job and monitor its progress. You will see something like this:

#### Step 6
Wait for the job status to turn to Succeeded. At this point, your CloudShell will display a command-line prompt. In CloudShell, examine the output (make sure to replace <YOUR-BUCKET-NAME> with the bucket name you created an earlier step):

``` shell
gsutil cat gs://<YOUR-BUCKET-NAME>/javahelp/output-*
```


### What you learned

In this lab, you:

1. Executed a Dataflow pipeline locally
2. Executed a Dataflow pipeline on GCP.


