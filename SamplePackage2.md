Making a Simple Package for Cuis -- Part 2
================================

This is a continuation of
- https://github.com/Cuis-Smalltalk-Learning/Learning-Cuis/blob/master/SamplePackage1.md

### Feature require: #'IA-EN-Dictionary'

We start with a "fresh" Cuis development image.

World menu -> Open -> Workspace

````Smalltalk
Feature require: #'IA-EN-Dictionary'
````

Note that Cuis does _syntax hilighting_ as you type.  Very useful, this.

You also have _word completion_.  If you start typing a word, e.g. 'Fea', then type TAB, you get a context based temporary select list of possible completions.

You can ignore these or select one of them to complete the word you want.

![Cuis Window](SamplePkg/Sample-Package-026.png)

In a Workspace you can select a line of code and either Cmd-click for the context menu and select DoIt or press Cmd-d to compile and run the code.

If the package loads, skip this paragraph and go to the next one.  Otherwise, you now need to learn how package code is searched for in Cuis. @@@

After the package has been loaded, you should be able to open a code browser and select the category and the IEDict class.  You can also move the mouse to the category pane of the code browser, Cmd-click to get the context menu, select Find (or just Cmd-f) type 'IEDict' and you will get to the class code.

![Cuis Window](SamplePkg/Sample-Package-027.png)

### Initializing the IEDict Class

In the Class pane, under 'IEDict' there are three buttons labled 'instance', '?', and 'class'.  Click on class.

![Cuis Window](SamplePkg/Sample-Package-028.png)

The difference between Class and Instance is that _instance methods_ operate on individual objects which are instances of a class.  _Class methods_ operate on the class code shared by all instances.  We'll get into what this means in a bit more detail below.

To keep things organized, the class browser groups methods into categories.  We will be adding code which does _class initialization_ so we first add this category.

Cmd-click on the method category pane to get its context menu and add a new category.

![Cuis Window](SamplePkg/Sample-Package-029.png)
![Cuis Window](SamplePkg/Sample-Package-030.png)

Select the new category to get a _method template_.  

Note the syntax hilighting.

![Cuis Window](SamplePkg/Sample-Package-031.png)


### Reading the Dict Data

### Lookup


@@@
