# Welcome to moa-multiflow’s documentation!

The idea of this project is creating a more flexible tool for testing, learning machine learning algorithms by combining the strength of [MOA](https://moa.cms.waikato.ac.nz/blog/) via [moa-flow API](https://github.com/Waikato/moa-flow/blob/master/README.md) with the dynamic and interactive abilities of script languages. You can export a IPYNB file for a task from MOA, then run it interactively on a web-browser with Jupyter Notebook. Jupyter Notebooks nowadays can run the code written in various programming languages by connecting to the corresponding kernels. MOA use Java language, so that we will use a Jupyter kernel for Java called [IJava](https://github.com/SpencerPark/IJava).

![Image](/images/moa-jb-demo.PNG)
![Image](/images/moa-jb-demo1.PNG)
![Image](/images/moa-jb-demo2.PNG)

This tutorial will show you how to export Jupyter Notebooks from MOA as well as how to configure the Jupyter Notebooks for running the exported tasks. We expect that you have already Python and Jupyter Notebooks installed on your machine. If not, please install them before reading further more. This tutorial describes the configuration process on a Windows 10 computer, but it is possibly applied as well for other operating systems without much modifications. 

## moa-flow API
With moa-flow API, you can simlify your work with MOA by using a predesigned workflow API. You can find documentation for moa-flow API [here](https://github.com/Waikato/moa-flow/blob/master/README.md)

## MOA Notebook
### Getting started
You can download and install the latest version of IJava from [IJava Github repository](https://github.com/SpencerPark/IJava).

To avoid getting in troubles with the whole installation process, please note some
points as follow:
- IJava requires Java JDK version 9 or later.
- The Java command must be is in the PATH and its version is 9 or later. In
Windows, you can manually add Java to the PATH by command:
```
set PATH=%PATH%;"<absolute path to Java>\bin"
```
- If you cannot start Jupyter Note book, check if python scripts folder was added
to the PATH. In Windows, you can manually add it to the PATH by command:
```
set PATH=%PATH%;"<absolute path to Python>\Scripts"
```
### Setting up IJava for Jupyter Notebooks
Open the Windows console and type jupyter notebook to start it. The Jupyter Notebooks will be opened on the web browser:
![Image](/images/jb-homepage.png)

Click new and choose Java:
![Image](/images/jp-kernel.PNG)

We will get Kernel error as the correct path for the IJava kernel was not we configured:
![Image](/images/jp-kernelerror.png)

To see available kernels for Jupyter Notebooks, run jupyter kernelspec list from the Windows console:
![Image](/images/jp-kernellist.png)

We edit the configuration file for Java kernel in the folder C:\ProgramData\jupyter\kernels\java:
![Image](/images/jp-kernelfolder.png)

Open it by any text editor and change “java” to the absolute path to where Java is currently installed on your computer, do not forget to change “\” in the path to “/” or “\\” which is the path format used by JSON.
![Image](/images/jp-javakernel-config.PNG)

Refresh the Jupyter Notebooks again, it will work properly:
![Image](/images/jp-kernel-success.png)

### Exporting tasks from MOA GUI to a IPYNB files
At that moment, there are 6 tasks that can be exported to Jupyter Notebooks files:
- EvaluateInterleavedTestThenTrain
  * Test configuration: 
` WriteConfigurationToJupyterNotebook -t (EvaluateInterleavedTestThenTrain -l (meta.AdaptiveRandomForest -l (ARFHoeffdingTree -e 2000000 -g 75 -s GiniSplitCriterion -c 0.01 -l MC) -o (Percentage (M * (m / 100))) -m 80) -s (ArffFileStream -f <path>\elecNormNew.arff) -i 100000 -f 4532) -j <path>\outputfile.ipynb `
  
- EvaluatePrequential
  * Test configuration: 
` WriteConfigurationToJupyterNotebook -t (EvaluatePrequential -l (meta.AdaptiveRandomForest -l (ARFHoeffdingTree -e 2000000 -g 75 -s GiniSplitCriterion -c 0.01 -l MC) -o (Percentage (M * (m / 100))) -m 80) -s (ArffFileStream -f <path>\elecNormNew.arff) -i 100000 -f 4532) -j <path>\outputfile.ipynb `
  
- EvaluatePrequentialCV
  * Test configuration: 
` WriteConfigurationToJupyterNotebook -t (EvaluatePrequentialCV -l (meta.AdaptiveRandomForest -l (ARFHoeffdingTree -e 2000000 -g 75 -s GiniSplitCriterion -c 0.01 -l MC) -o (Percentage (M * (m / 100))) -m 80) -s (ArffFileStream -f <path>\elecNormNew.arff) -i 100000 -f 4532) -j <path>t\outputfile.ipynb `
  
- EvaluatePrequentialDelayed
  * Test configuration: 
` WriteConfigurationToJupyterNotebook -t (EvaluatePrequentialDelayed -l (meta.AdaptiveRandomForest -l (ARFHoeffdingTree -e 2000000 -g 75 -s GiniSplitCriterion -c 0.01 -l MC) -o (Percentage (M * (m / 100))) -m 80) -s (ArffFileStream -f <path>\elecNormNew.arff) -i 100000 -f 4532) -j <path>\outputfile.ipynb `
  
- EvaluatePrequentialDelayedCV
  * Test configuration: 
` WriteConfigurationToJupyterNotebook -t (EvaluatePrequentialDelayedCV -l (meta.AdaptiveRandomForest -l (ARFHoeffdingTree -e 2000000 -g 75 -s GiniSplitCriterion -c 0.01 -l MC) -o (Percentage (M * (m / 100))) -m 80) -s (ArffFileStream -f <path>\elecNormNew.arff) -i 100000 -f 4532) -j <path>\outputfile.ipynb `

- EvaluatePrequentialRegression
  * Test configuration: 
` WriteConfigurationToJupyterNotebook -t (EvaluatePrequentialRegression -l (meta.AdaptiveRandomForestRegressor -l (ARFFIMTDD -s GiniSplitCriterion -g 75 -l 0.01) -o (Percentage (M * (m / 100))) -m 80) -e BasicRegressionPerformanceEvaluator -i 100000 -f 4532) -j <path>\outputfile.ipynb -e `

From MOA, under tab “Other Tasks” select WriteConfigurationToJupyterNotebook:
![Image](/images/moa-jb-home.png)

Select “Configure” to open “Configure task”. In the field “NotebookFile”, locate the place where you want to save the exported file and input its name.
![Image](/images/moa-jb-savefile.PNG)

You can click “Edit” button and configure the task with desired parameters
![Image](/images/moa-jb-edittasks.PNG)

You can export IPYNB files with or without running the tasks by tick or untick the runConfig option corresponding. By default, MOA exports the files without running the task.
![Image](/images/moa-jb-runconfig.PNG)

Open the exported IPYNB file on Jupyter Notebooks and run all codes cell. At that step, you have successfully export a task from MOA GUI and run it on Jupyter Notebooks. Example of the running results can be found [here].

### Displaying the output result in table format
The result table has long rows, but the CSS style of Jupyter Notebooks is designed to wrap the long rows by default, which makes the table distorted. To come up with that, we need to customise the default CSS file of Jupyter Notebooks by adding a file named [custom.css](/css/custom.css) following the instruction as bellow:
-	Find your configuration directory by typing following command to the console: 
```
jupyter --config-dir 
```
(mine is C:\Users\username\\.jupyter). 
-	Create a new folder (if not existed yet) named custom inside .jupyter\, then copy & paste the file custom.css into that folder (mine is: C:\Users\username\\.jupyter\custom\custom.css).
-	Restart the Jupyter Notebooks, the table will be displayed correctly.

### Examples
[Here](/examples/example.ipynb) you can find examples for a task running on Jupyter Notebook with moa-flow API.
