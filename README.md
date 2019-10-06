## Welcome to moa-multiflow’s documentation!

This tutorial will show you how to export Jupyter Notebooks from MOA as well as how to configure the Jupyter Notebooks for running the exported tasks. We expect that you have already Python and Jupyter Notebooks installed on your machine. If not, please install them before reading further more. This tutorial describes the configuration process on a Windows 10 computer, but it is possibly applied as well for other operating systems without much modifications.

Jupyter Notebooks nowadays can run the code written in various programming languages by connecting to the corresponding kernels. MOA use Java language, so that we need to install a Jupyter kernel for Java called IJava. You can download and install the latest version of IJava from a [Github repository](https://github.com/SpencerPark/IJava).

## Getting started
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
<set PATH=%PATH%;"<absolute path to Python>\Scripts>"
```
### Setting up IJava for Jupyter Notebooks
Open the Windows console and type jupyter notebook to start it. The Jupyter Notebooks will be opened on the web browser:
![Image](https://github.com/truongtd6285/moa-multiflow/blob/master/images/jb-homepage.png)

Click new and choose Java:
![Image](https://github.com/truongtd6285/moa-multiflow/blob/master/images/jp-kernel.PNG)

We will get Kernel error as the correct path for the IJava kernel was not we configured:
![Image](https://github.com/truongtd6285/moa-multiflow/blob/master/images/jp-kernelerror.png)

To see available kernels for Jupyter Notebooks, run jupyter kernelspec list from the Windows console:
![Image](https://github.com/truongtd6285/moa-multiflow/blob/master/images/jp-kernellist.png)

We edit the configuration file for Java kernel in the folder C:\ProgramData\jupyter\kernels\java:
![Image](https://github.com/truongtd6285/moa-multiflow/blob/master/images/jp-kernelfolder.png)

Open it by any text editor and change “java” to the absolute path to where Java is currently installed on your computer, do not forget to change “\” in the path to “/” or “\\” which is the path format used by JSON.
![Image](https://github.com/truongtd6285/moa-multiflow/blob/master/images/jp-javakernel-config.PNG)

Refresh the Jupyter Notebooks again, it will work properly:
![Image](https://github.com/truongtd6285/moa-multiflow/blob/master/images/jp-kernel-success.png)

## Exporting tasks from MOA GUI to a IPYNB files

From MOA, under tab “Other Tasks” select WriteConfigurationToJupyterNotebook

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/truongtd6285/moa-multiflow/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
