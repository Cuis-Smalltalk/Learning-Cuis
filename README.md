# Learning-Cuis

Greetings and Welcome!!

Smalltalk is a wonderful way of doing things in software and Cuis is a particular implementation of this language and its environment.

Cuis shares ideas with other Smalltalk implementations and shares much of its implementation mechanics with the [Squeak](http://www.squeak.org) and [Pharo](http://www.pharo.org/) environments.

Smalltalk is a big world, which you can use to do just about anything that can be done with a computer.

Cuis is different in that it is actively managed to become smaller, where each component carries its own weight with the minimum of baggage.

We think this makes Cuis easier to learn.

One measure of a Smalltalk's size is the number of Classes which implement its code.

If you open a Workspace in many Smalltalks, you can type and print (cmd-p)
````Smalltalk
	Smalltalk allClasses size.
````   

Here are the ***class counts*** for some related implementations.

Cuis and Pharo both forked from Squeak around release 3.7

![Class Counts](ClassCounts.png)

We are working hard to keep Cuis small and easy to learn, even as more capabilities are added.

![Cuis Lifts Above its Weight](CuisLiftsAboveItsWeight.jpeg)

This project is all about learning Cuis and sharing Cuis code which others may find of interest.

# Beginners: 

***Get Cuis*** from https://github.com/Cuis-Smalltalk/Cuis-Smalltalk-Dev

Take a look at ***Quick-UI-Tour*** (click on file 'Quick-UI-Tour.md' above or)
- https://github.com/Cuis-Smalltalk/Learning-Cuis/blob/master/Quick-UI-Tour.md

Take a look at how ***LayoutMorphs*** are used to maintain visual relations between graphic elements:
- https://github.com/Cuis-Smalltalk/Learning-Cuis/blob/master/LayoutTour.md

Look at the ***Terse Guide*** (World Menu -> Help -> Terse Guide to Cuis)

Look at ***documentation*** available for other wonderful Smalltalk implementations
- http://squeak.org/documentation/

Take a ***detailed tour*** which creates a Package and a GitHub repository for it
- https://github.com/Cuis-Smalltalk/Learning-Cuis/blob/master/SamplePackage1.md

***Subscribe*** and ask questions at the ***Cuis developers email*** list
- http://jvuletich.org/mailman/listinfo/cuis_jvuletich.org
- cuis-dev@cuis-smalltalk.org

Software 'code' is meant to be read as well as written.  Well written software is something we all work on getting better at.  There are some cool Cuis packages on GitHib.

Look at the ***repositories in GitHub*** with names starting 'Cuis-Smalltalk'.  Many of these have a 'RoughGuide.md' file which points out code topics and techniques of interest.

Look at the ***package reference***
- https://github.com/Cuis-Smalltalk/Learning-Cuis/blob/master/PackageRef.md

Examples of Cuis Smalltalk with interesting Features are described in 'PackageRef.md' including:

* Morphic-ColorEditor
* ClassCommentBrowser
* Crypto-NaCl
* Interlingua-English-Lookup
* Morphic-Misc1
* ... -NamedColors
* Code-Patterns
* Ropes
* Morphic-Games-Solitaire
* Life
* Construction



I find it best to "git clone" repositories in a common directory, in my case named 'Cuis'.

For example, to get a copy of the ColorEditor in your image, you first must clone the Cuis-Smalltalk-ColorEditor and (from its 'README.md' file) its dependent repositories Cuis-Smalltalk-Morphic-Misc1 and Cuis-Smalltalk-NamedColors.

Assuming you did a "git clone https://github.com/Cuis-Smalltalk/Cuis-Smalltalk-Dev" into a directory named 'Cuis'.

````
cd Cuis
git clone https://github.com/KenDickey/Cuis-Smalltalk-ColorEditor
git clone https://github.com/KenDickey/Cuis-Smalltalk-Morphic-Misc1
git clone https://github.com/KenDickey/Cuis-Smalltalk-NamedColors
cd Cuis-Smalltalk-Dev
squeak Cuis<version>.image
````
In a workspace
````Smalltalk
  Feature require: #'Morphic-ColorEditor'.
````
Select the code and "do-it" (cmd-d).

If all went well, you should be able to open a ColorEditor via the World Menu -> New morph.. -> ColorEditor -> ColorEditorPanel

***Enjoy!***




# Contributors:

The basic goals here are to develop a strategy which is
- Easy to contribute to
- Orienting and useful to people learning Cuis/Smalltalk
- Simple enough that we will bother to maintain it and not step (often) on each others feet.

The gist is that we, the Cuis community, maintain an overview/README.md page, then just add our own mature/example projects to the list of interesting repositories.

Each Project should supply a 'RoughGuide.md', which describes what the interesting bits of code are, as well as the Project 'README.md' which should
- Name the project/feature(s) -- what is this good for, what does it do?
- List the latest Cuis version+revision the code was tested with.
- Show the Smalltalk code to load the package(s).
- Have useful code/usage examples.
- Optionally, show a screen graphic (what does this look like?)

All project repositories should be named with prefix 'Cuis-Smalltalk-'.

For an example. look at the Cuis-Smalltalk-ColorEditor repository.

ToDo:

-  Using the Styled Text Editor, we start and maintain a Rough Guide to Cuis (Cuis-by-Example).  After the general Smalltalk and Cuis overviews, we can write about parts of the system, patterns of how to get things done, and use forked project examples.

I suspect it would not be too much work to embed Smalltalk WorkSheets (TerseGuide WorkSpaces) as objects in STE, which would allow us to have nice live examples.  Projects could contribute chapters.

Open a FileList after loading STE, select MorphBecomeButton.object and click on button "openSTE" to see some interesting code.

Enjoy!
