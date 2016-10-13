Making a Simple Package for Cuis
================================

This is a quick tutorial which shows the process of creating a simple package in Cuis Smalltalk and making it sharable on GitHub.

### Basic Orientation

It would be good for you to read through the Cuis documentation on package based code sharing before going through this tutorial.

You can find information at the web site or from within a running Cuis.

From the Cuis-Smalltalk-Dev web site:

- https://github.com/Cuis-Smalltalk/Cuis-Smalltalk-Dev/blob/master/Documentation/CuisAndGitHub.md
- https://github.com/Cuis-Smalltalk/Cuis-Smalltalk-Dev/blob/master/Documentation/CodeManagementInCuis.md

Within a running Cuis image, use Cmd-Click (the Command key depends on your Operating System) to get the World Menu.  Then open the pages from the Help submenu.

![Cuis Window](SamplePkg/Sample-Package-0001.png)`

![Cuis Window](SamplePkg/Sample-Package-0002.png)

We will be following the recipies for developing with packages.

![Cuis Window](SamplePkg/Sample-Package-0003.png)


The first step in developing a package is to get yourself an account on GitHub
- https://github.com

This step is not shown.

When you have an account, creating a new repository is easy.

We like easy.  We can deal with easy.  ;^)


### Creating a GitHub Repository

The first thing is to think of a good, descriptive-but-not-too-long name.

The convention for Cuis is to start all names with 'Cuis-Smalltalk-'.  This allows tools to have a common searching convention for finding packages.

![Cuis Window](SamplePkg/Sample-Package-001.png)

Shareable Cuis code by convention uses the MIT open source licence.

I typically create a default README.md file as well.

![Cuis Window](SamplePkg/Sample-Package-002.png)

![Cuis Window](SamplePkg/Sample-Package-003.png)

One thing which you might observe in these tutorials is that I am a poor typist.

The first thing I notice is that I have to fix the package name!

I could delete the repository and start over, but fortunately GitHub settings allows me to fix this.

![Cuis Window](SamplePkg/Sample-Package-004.png)

OK.  Now that I have a repository set up, I can clone it and add files.

![Cuis Window](SamplePkg/Sample-Package-005.png)

I am a Linux user, so I use the command line.

Being lazy, I "Copy" the github name from the web page.

![Cuis Window](SamplePkg/Sample-Package-006.png)

I can now "git clone", paste the name, and get a local copy of my shiny new repository.

![Cuis Window](SamplePkg/Sample-Package-007.png)

![Cuis Window](SamplePkg/Sample-Package-008.png)

### Add a new file to a Git repository

For this tutorial I wanted an example where a small amount of code gives useful tool.
 I have been thinking of rewriting one of my earliest Cuis projects which I think fits this goal: an Interlingua<->English word lookup.

This is how this current lookup window appears:

![Cuis Window](SamplePkg/Sample-Package-009.png)

The way this works is

- Enter a word, or part of a word. 
- Either press <enter> or click on one of the four buttons.

Pressing enter (carriage return) is the same as clicking on button labeled  'Interlingua Contains'.

Having decided this, the first thing I did was add the Interlingta->English dictionary to the local Git repository.

[1] copy the file into the local repository
[2] "git add" to make the repository aware of the file
[3] "git commit" to declare the file as ready for update
[4] "git push" to actually update the repository on GitHub from the local version.

Here is what this lookes like in a Linux shell:

![Cuis Window](SamplePkg/Sample-Package-010.png)

### Creating a Cuis Category

OK.  Now for the fun part: some Smalltalk code!

First we need a code Browser. 

Command-Click on the World background to get a World Menu.

 World->Open..->Browser

![Cuis Window](SamplePkg/Sample-Package-011.png)

The upper left _pane_ in the Browser lists class _categories_.

We want to add a new category.  Cmd-Click on this pane to gets it's context menu and select 'add item..'

![Cuis Window](SamplePkg/Sample-Package-012.png)

Now we can create a category 'IA-EN-Dictionary'.  

![Cuis Window](SamplePkg/Sample-Package-013.png)

As you might suspect, the international code for English is 'EN' and Interlinguag is 'IA'.

### Adding a Class

We will be creating a specialized SystemWindow with its associated data _model_.

This is a common pattern.  If you open a HierarchyBrowser on 'SystemWindow' you will see this a lot. (Not shown here; you can look later).

Since our dictionary will work in both directions, Interlingua->English and English->Interlingua, we will NOT be using a Smalltalk dictionary here, so we can inherit directly from Object.

The class will be called 'IEDict'.

We add a Class Variable, 'DictData', to hold our (what else?) dictionary data.  Note that Class Variable names are by convention capitalized.  This helps distinguish then from instance variables.

Access to a class variable is shared by all instances of that class.  An instance variable is unique to each instance of the class.

It is a bit subtle, but there is a thin red border around the lower pane where we typed in the #IEDict definition fields.  This means that we have started an edit, but not yet saved it.

![Cuis Window](SamplePkg/Sample-Package-014.png)

The code you are looking at is just code.  It is text which will be compiled and the compiled code then invoked to create a new Smalltalk class.

Cmd-click on this pane to see the context menu.  We can select 'Accept (s)'.  If we did not wish to use the menu, we could just type Cmd-s (hold down the command key and press 's').  This is why the '(s)' in 'Accept (s)'.

![Cuis Window](SamplePkg/Sample-Package-015.png)

Congratulations!  You have created a new Class!

![Cuis Window](SamplePkg/Sample-Package-016.png)

### Add a Class Comment

Noting the red 'THIS CLASS HAS NO COMMENT!' now is a good time to add some description of the new class.

![Cuis Window](SamplePkg/Sample-Package-017.png)

To save the class comment, I type Cmd-s (or use the context menu selection Save).

![Cuis Window](SamplePkg/Sample-Package-018.png)


### Creating a Package and adding it to GitHub.

OK.  We have an IEDict class and are about to start adding Smalltalk code.

But this is a perfect time to pause and save our work to GitHub.

The first thing to do is to create a Package which can be added to our GitHub  repository.

I open an Installed Packages browser from the World Menu -> Open.. submenu.

![Cuis Window](SamplePkg/Sample-Package-019.png)

Clicking on the _new_ button, I fill in exactly the same name as I gave the system category: 'IA-EN-Dictionary'.  Copy/Paste from the class browser would work here as well.

![Cuis Window](SamplePkg/Sample-Package-020.png)

Now I just fill in the package comment and click the 'save' button.

![Cuis Window](SamplePkg/Sample-Package-021.png)

I can open a File Browser to check that the package was created.

![Cuis Window](SamplePkg/Sample-Package-022.png)

I find a file 'IA-EN-Dictionary.pck.st' was created in the directory where the Cuis image file was found 'Cuis-Smalltalk-Dev'.

This package text file contains the code and some _meta-data_ about the code and looks fine.  However, THE PACKAGE FILE IS NOT IN THE 'Cuis-Smalltalk-SamplePkg' DIRECTORY.

Gotta fix this!

In my case, I get a Linux command shell, move the file to the Cuis-Smalltalk-SamplePkg directory, "git add", "git commit", "git push".

![Cuis Window](SamplePkg/Sample-Package-023.png)

Our Cuis-Smalltalk-SamplePkg repository on GitHub has now been updated to contain our package.

Anyone with access to this director on GutHub can now "git clone" the directory and share our code.

All that remains to do is quit out of Cuis WITHOUT saving our changes.

![Cuis Window](SamplePkg/Sample-Package-024.png)
![Cuis Window](SamplePkg/Sample-Package-025.png)

This is OK as we are not changing the base Cuise image.  All our work is saved in GitHub.


### Feature require: #'IA-EN-Dictionary'


### Initializing the IEDict Class

### Reading the Dict Data

### Lookup


@@@

