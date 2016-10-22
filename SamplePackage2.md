Making a Simple Package for Cuis -- Part 2
================================

This is a continuation of
- https://github.com/Cuis-Smalltalk-Learning/Learning-Cuis/blob/master/SamplePackage1.md


### Package loading

You should know how Cuis finds packages to load.

First, Cuis looks in the folder the image is running from, then in its subfolders/subdirectories 'Packages' and 'CompatibilityPackages'.  Then it looks in the parent directory of 'Cuis-Smalltalk-Dev' for directories with names starting 'Cuis-Smalltalk-'.  

So the best thing is for all directories/folders named 'Cuis-Smalltalk-*' to be in the same common directory.  If this directory is named 'Cuis' then there should be a 'Cuis/Cuis-Smalltalk-Dev' and a 'Cuis/Cuis-Smalltalk-IA-EN-Dictionary'.  If this is not the case, you must make it so.

To avoid confusion, make sure your `IA-EN-Dictionary.pck.st` file ***is*** in folder/directory 'Cuis-Smalltalk-IA-EN-Dictionary' and that there is  ***not*** a `IA-EN-Dictionary.pck.st` in 'Cuis-Smalltalk-Dev'.

Also, if you have a 'Cuis-Smalltalk-SamplePkg' directory, you might rename it to something like 'SamplePackage'.

This will ensure that there is only one `IA-EN-Dictionary` feature to find when Cuis looks for a package with this feature.


### Feature require: #'IA-EN-Dictionary'

We start with a "fresh" Cuis development image.

World menu -> Open -> Workspace

````Smalltalk
Feature require: #'IA-EN-Dictionary'
````

Note that Cuis does _syntax hilighting_ as you type.  Very useful, this.

- `Feature` is the name of a class
- `require:` is a message selector on the Feature class
- `#'IA-EN-Dictionary'` is a _symbol_

You also have _word completion_.  If you start typing a word, e.g. 'Fea', then type TAB, you get a context based temporary select list of possible completions.

You can ignore these or select one of them and press enter/CR to complete the word you want.

![Cuis Window](SamplePkg/IA-EN-Dict-023.png)


In a Workspace you can select a line of code and either Cmd-click for the context menu and select DoIt or press Cmd-d to compile and run the code.

If the package loads, skip this paragraph and go to the next one. Otherwise, make sure all words are spelled properly and try DoIt again. If there is still a problem, please ask for help on the Cuis mailing list http://cuis-smalltalk.org/mailman/listinfo/cuis-dev_cuis-smalltalk.org

After the package has been loaded, you should be able to open a code browser, scroll to and select the category and the IEDict class.  You can also move the mouse to the _class category_ pane of the code browser, Cmd-click to get the context menu, select Find (or just Cmd-f) type 'IEDict' and you should get to the class code.

![Cuis Window](SamplePkg/IA-EN-Dict-024.png)


### Initializing the IEDict Class

In the Class pane, under 'IEDict' there are three buttons labled 'instance', '?', and 'class'.  Click on 'class'.

![Cuis Window](SamplePkg/IA-EN-Dict-025.png)

The difference between Class and Instance is that _instance methods_ operate on individual objects which are instances of a class.  _Class methods_ operate on the class code shared by all instances.  We'll get into what this means in a bit more detail below.

To keep things organized, the class browser groups methods into categories.  We will be adding code which does _class initialization_ so we first add this category.

Cmd-click on the method category pane to get its context menu and add a new method category.

![Cuis Window](SamplePkg/IA-EN-Dict-026.png)

![Cuis Window](SamplePkg/IA-EN-Dict-027.png)


Select the 'class initialization' category to get a _method template_.  

Note the syntax hilighting.  The _method selector_ is in black, _comments_ are in green, _temporaries_ are in grey, unknown words in red.


![Cuis Window](SamplePkg/IA-EN-Dict-028.png)


### Reading the Dict Data

The first thing we need to look up words in a dictionary is, of course, the dictionary.  Please open a File List browser and navigate to 'iedict.txt' to see what this text file looks like.  (Cmd-click on World; World->Open->File List).

![Cuis Window](SamplePkg/IA-EN-Dict-029.png)

There is a comment line which indicates the original source of the file, then lines like
- interlingua parolas : english words

Since we want a bidirectional lookup, let's save the data as an array of pairs.

As we only need to read the file once into memory and can share the data, an IEDict class variable is a good home for the data.

Here is one way of doing this.

````Smalltalk
initialize
	"Read in my data"
"
	IEDict initialize.
"
	| curIndex aLine |
	DictData := Array new: 30811. "We know the exact size (wc -l iedict.txt) less 1"

	(self package asFileName asFileEntry parent  // 'iedict.txt') readStreamDo: [ :fileStream |
		fileStream nextLine. "Skip initial comment line"
		curIndex := 1.
		aLine := fileStream nextLine. 
		[aLine isNil] whileFalse: [
			DictData at: curIndex 
				put: ((aLine findBetweenSubStrs: ':') 
					collect: [:str| str withBlanksTrimmed]). 
			aLine := fileStream nextLine. 
			curIndex := 1 + curIndex.
		]
	] 
````

![Cuis Window](SamplePkg/IA-EN-Dict-030.png)


When I Accept this, I am adding code for the first time since the image started, so the code browser asks who I am.  This is so that my initials get placed into the code's meta-data.  

There is a `versions` button in the code browser which lets you see previous versions of the current method.  You can select a previous version and _revert_ to it if you need to back off a change.

If you are unknown to the code browser, you may be asked to add your initials.  Please do so!

![Cuis Window](SamplePkg/IA-EN-Dict-031.png)


The text file 'iedict.txt' is read from IEDict's package file name directory.  (Cuis' FileEntry differs from Squeak's DirectoryEntry by the way.  We think it is simpler to use.)

The comment line is skipped and each line is read in as a String which is split on the colon into two substrings which are stored sequentially in an Array which is available in IEDict's DictData class variable.

Now a class' `initialize` method is invoked when a class is filed-in/loaded.  Since we have already created the class IEDict we need to invoke `IEDict>>initialize` ourselves.

Did I mention that I like to make things easy for myself?


### Class initialization

You may have noticed the comment 
````Smalltalk
"
	IEDict initialize.
"
````
One can select any text in a code browser window and DoIt (Cmd-d).  When I am changing method code and may want to invoke the method again, I just add the invocation code as a comment so that I can DoIt without having to open a Workspace.

Did I tell you I was lazy?  ;^)

We DoIt and..

![Cuis Window](SamplePkg/IA-EN-Dict-032.png)

![Cuis Window](SamplePkg/IA-EN-Dict-033.png)

Oops!

Well, I guess we are not perfect.  (You already knew that? ;^)

Let's look at the stack with the debugger to see where we went wrong.

![Cuis Window](SamplePkg/IA-EN-Dict-034.png)

@@@

![Cuis Window](SamplePkg/IA-EN-Dict-044.png)

Well, without a visible change it is hard to see that `IEDict>>initialize` succeeded.  I could open an object explorer on the IEDict class object, but since we need lookup methods in any case, why not just write them and use them to be sure we read in the dictionary?



### Lookup

For lookup we use the `String>>match:` method.  This does "regular expression"  matching.

````Smalltalk
interlinguaContains: aString
	"Answer all definition pairs which contain aString looking in the Interlingua side"

	| matchStr |
	matchStr :=  ('*' , aString , '*' ) .
	
	^DictData select: [ :pairArray | matchStr match: (pairArray at: 1) ]
````

Lookup functions for our four buttons are just slight variations on the above.

Cmd-p (print) will show the result in a Workspace.

![Cuis Window](SamplePkg/Sample-Package-036.png)

### Wash, rinse, repeat

Now is a good time to save our work.  (The power goes out here in winter in high winds, so I save my work frequently).

We need to 
- Save the Package
- "git commit"
- "git push"

You remember how to open the package browser and "save", right?

Here is the last time I will bore you with a non-Smalltalk screen shot

![Cuis Window](SamplePkg/Sample-Package-035.png)

### IEDictWindow

OK.  Now to make a window to show our stuff.

How do we do this?

Well, there is a lot of good code in SystemWindow that we can reuse just by subclassing.  (Did I tell you I was lazy?)

The IEDictWindow needs to keep track of two things: the text query and the result.

These will be Morphs, graphical screen objects.

![Cuis Window](SamplePkg/Sample-Package-037.png)

### Opening a IEDictWindow (a new instance)

We want to open a new IEDictWindow by asking its class to make one.

The first step is to add a method category to the class side

![Cuis Window](SamplePkg/Sample-Package-038.png)

Now we add the code to create an instance

![Cuis Window](SamplePkg/Sample-Package-039.png)

`IEDictWindow class>>open` uses the inherited method `SystemWindow class>>open:label:`

Let's take a brief look at this.  Select the text which contains `open:*label:` and Cmd-m (iMplementors).

![Cuis Window](SamplePkg/Sample-Package-040.png)

Implementors shows just one implementor: SystemWindow.

![Cuis Window](SamplePkg/Sample-Package-041.png)

The `SystemWindow class>>open:label:` method sets the window's _model_, invokes #buildMorphicWindow, sets the label (if any), and returns the window.

So our next task is to go to the _instance_ side of the class and implement `IEDictWindow>>buildMorphicWindow`.

![Cuis Window](SamplePkg/Sample-Package-042.png)

..which we will do in Part 3 of this tutorial
- https://github.com/Cuis-Smalltalk-Learning/Learning-Cuis/blob/master/SamplePackage3.md
