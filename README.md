# Learning-Cuis

Greetings and Welcome!!

Smalltalk is a wonderful way of doing things in software and Cuis is a particular implementation of this language and its environment.

Cuis shares much with other Smalltalk implementations and shares much of its implementation mechanics with the Squeak and Pharo environments.

Smalltalk is a big world, which you can use to do just about anything that can be done with a computer.

Cuis is different in that it is actively managed to become smaller, where each component carries its own weight with the minimum of baggage.

We think this makes Cuis easier to learn.

One measure of a Smalltalk's size is the number of Classes which implement its code.

If I open a Workspace in the current Cuis and print (cmd-p)
````Smalltalk
	Smalltalk allClasses size.
````   

- Cuis 4.2 (rev 2658) --> 497 

For comparison, here are the class counts for some related implementations

-  Squeak 4.4 --> 2511
-  Squeak 4.5 --> 2175
-  Squeak 5.0 --> 2244
-  eToys  5.0 --> 2236
-  Pharo  2.0 --> 3226
-  Pharo  3.0 --> 4020
-  Pharo  4.0 --> 4924


This project is all about learning Cuis and sharing Cuis code which others may find of interest.

# Beginners: 

Take a look at Quick-UI-Tour (click on file 'Quick-UI-Tour.md' above).  

Get Cuis from https://github.com/Cuis-Smalltalk/Cuis-Smalltalk-Dev

Look at the Terse Guide (World Menu -> Help -> Terse Guide to Cuis)

Look at documentation available for other wonderful Smalltalk implementations
- http://squeak.org/documentation/

Look at the repositories here
- https://github.com/Cuis-Smalltalk-Learning

Subscribe and ask questions at the Cuis developers email list
- http://jvuletich.org/mailman/listinfo/cuis_jvuletich.org
- cuis-dev@cuis-smalltalk.org


# Contributors:

The basic goals here are to develop a strategy which is
- Easy to contribute to
- Orienting and useful to people learning Cuis/Smalltalk
- Simple enough that we will bother to maintain it and not step (often) on each others feet.

The gist is that we, the Cuis community,  maintain an overview page, then just _fork_ our own mature/example projects (e.g. Cuis-Smalltalk-ColorEditor) where each has/adds its own explanation about what is interesting to learn there.  Each contributed project adds an author to the repository who is responsible for keeping his/her stuff up to date and supplying an orienting overview for learning.

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
