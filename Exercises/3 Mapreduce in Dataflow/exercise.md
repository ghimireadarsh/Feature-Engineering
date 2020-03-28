### Overview

In this lab, you learn how to use pipeline options and carry out Map and Reduce operations in Dataflow.

#### What you need
You must have completed Lab 0 and have the following:

Logged into GCP Console with your Qwiklabs generated account

### What you learn
In this lab, you learn how to:

* Use pipeline options in Dataflow

* Carry out mapping transformations

* Carry out reduce aggregations


### Identify Map and Reduce operations

#### Step 1
In CloudShell clone the source repo which has starter scripts for this lab:
``` shell
	git clone https://github.com/GoogleCloudPlatform/training-data-analyst
```

Then navigate to the code for this lab.
``` shell
	cd training-data-analyst/courses/data_analysis/lab2/python
```

#### Step 2
Click File > Refresh.

View the source code for __is_popular.py__ for the pipeline using the Cloud Shell in-browser editor or with the command line using nano:

#### Step 3
What custom arguments are defined? ____________________

What is the default output prefix? _________________________________________

How is the variable output_prefix in main() set? _____________________________

How are the pipeline arguments such as --runner set? ______________________

#### Step 4
What are the key steps in the pipeline? _____________________________________________________________________________

Which of these steps happen in parallel? ____________________________________

Which of these steps are aggregations? _____________________________________

### Execute the pipeline

#### Step 1
Install the necessary dependencies for Python dataflow:

``` shell
sudo ./install_packages.sh
```

Verify that you have the right version of pip (should be > 8.0):

``` shell
pip3 -V
```

If not, open a new CloudShell tab and it should pick up the updated pip.

#### Step 2
Run the pipeline locally:

``` shell
python3 ./is_popular.py
```

_Note: If you see an error that says "No handlers could be found for logger "oauth2client.contrib.multistore\_file", you may ignore it. The error is simply saying that logging from the oauth2 library will go to stderr._

#### Step 3
Examine the output file:

``` shell
cat /tmp/output-*
```

### Use command line parameters

#### Step 1

Change the output prefix from the default value:

``` shell
python3 ./is_popular.py --output_prefix=/tmp/myoutput
```

What will be the name of the new file that is written out?

#### Step 2
Note that we now have a new file in the /tmp directory:

``` shell

ls -lrt /tmp/myoutput*

```

### What you learned

In this lab, you:
* Used pipeline options in Dataflow
* Identified Map and Reduce operations in the Dataflow pipeline


