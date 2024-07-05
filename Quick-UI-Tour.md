# Quick-UI-Tour

Greetings and Welcome!!

This file is a quick tour of the Cuis User Interface (UI).

Smalltalk defined Object Oriented.  All computation is done by objects sending messages to themselves and each other.

Cuis shares with other Smalltalk implementations the characteristic that all objects are live.  All objects can be inspected and changed while they are executing.

There are many great tools waiting to be used.  This tour gives an introduction to a few of the most important ones.

![Cuis Window](UITour/Cuis1.png)

Perhaps the best way to think of Cuis is as a place to explore.

You can open a Cuis image using a portable virtual machine and see the same windows in the same positions pixel-per-pixel on Linux, Macintosh, Windows or any operating system where the VM runs.

You can start an image, do things with it and throw it away or save the image and its  record of the changes to be opened another time and take up right where you left off.

![WorldMenu](UITour/Cuis2.png)

The job of a user interface is to answer the questions: "Where am I" and "What can I do here?".

With a deep feature set, there is a fundamental conflict between showing everything you can interact with and reducing the "clutter" so that one can concentrate on what one wants to do.

The basic solution to this problem is to hide information until it is needed and present it in context.

The initial user interface screen is pretty sparse.  Cuis Smalltalk is an 'Interactive Development Environmant' just waiting for you.

The entry point of this interface is the World Menu which you can get by clicking on the desktop.

If you right-click or cmd-click on the desktop, you will see a World Menu.

The command button "cmd-" may be a control ("ctrl") key [Linux], an Apple key [MacOS], or some other command key based on your keyboard and operating system.

A three button mouse has:
-  button 1 = left mouse button = select
-  button 2 = right mouse button = menu
-  button 3 = center mouse buttom = halo

If your mouse or touchpad has less than three buttons, then you can use ctrl-click for button 3 and ctrl-shift-click for button 2.

A World Menu can be used for one-shot selections.  Just click on your selection, the action takes place and the menu disappears.  If you want to keep the menu up to make several selections, click on the push-pin icon in the upper right-hand corner.  The icon will disappear and the menu will stay up until you dismiss it by clicking on the circle-x close button in the upper left-hand corner.

![World+HelpMenu](UITour/Cuis3.png)

Of particular interest is the Help submenu.

Selecting `About this System..` shows the release and version and displays a Text Editor with basic information about Cuis.

![TerseGuide](UITour/Cuis4.png)

Also available from the Help Menu is the Terse Guide to Cuis.

The Terse Guide has many topics and shows code usages.  

You can select or change code in the Terse Guide pages and "DoIt" (cmd-d) or "PrintIt" (cmd-p) to see results.  Every time you re-visit a topic, the page is created again, so feel free to play.

![Code Editor Shortcuts](UITour/Cuis5.png)

Editor Keyboard Shortcuts gives helpful command-key usages.

The Help menu gives access to a lot of good information.

![SystemBrowser](UITour/Cuis6.png)

The Open menu gives access to fundamental tools.

Clicking on World Menu -> Open.. -> Browser  brings up a System Browser, from which you can view all the code in the Cuis environment.

Left to right at top, clicking on a Class Category shows related Classes. Clicking on a Class shows its code.  Selecting a Method Category shows related methods.  Selecting a Method name shows its code in the lower pane.

The Code Browser gives many ways to find and view code.

![Workspace](UITour/Cuis7.png)

Clicking World Menu -> Open.. -> Workspace  brings up a Workspace window for you to type and run code.

As you type, the system does syntax highlighting which gives clues to class and method names.  If you start typing a method name, you can hit the Tab key which will usually give you a "select list" of possible message name completions.

Again, you can select code and DoIt (cmd-d) or PrintIt (cmd-p) to get results.

![FileList](UITour/Cuis8.png)

When you click on World Menu -> Open.. -> File List you get a multi-pane file browser.

The upper left pane shows a tree-view of the file system.  You click on the small triangles to show/hide subtrees.

Clicking on a Directory shows File names in the right hand pane.  Clicking on a File entry shows its contents in the lower pane.

Shown is the Packages/Features/Graphics-Files-Additional.pck.st -- a packaged (.pck) Smalltalk (.st) code file.

The File List is context sensitive.  Viewing a text file or an image file or a file with Smalltalk Package code gives you different option buttons.

You can also "right-click" or "double-click" to get a context sensitive menu in many browser panes.  This works in most browsers.

In the picture above, a Package File has been selected.  Cuis Packages implement system Features.  The file shown implements a Feature named 'Graphics-Files-Additional' and requires the Feature 'Compression" be present.  Packages specify any additional Features they require to be useful.

Clicking on the "installPackage" button has the same effect as running the code in the previous Workspace picture.
````Smalltalk
  Feature require: #'Graphics-Files-Additional'.
````

![InstalledPackages](UITour/Cuis9.png)

One way of keeping Cuis small and understandable is to use a small core of code and load Package Files to add Features.  Note the Terse Guide topic 'Features'.

World Menu -> Open.. -> Installed Packages shows the packages loaded into your Cuis environment.

You can create your own packages and add/remove requirements so that any packages your package requires will be loaded when you need them.   Note the Terse Guide topic 'Features'.

![MorphMenu-BoxedMorph](UITour/Cuis10.png)

Smalltalks which descend from Squeak, like Cuis, have a system in which all graphic entities are objects called Morphs.

You can get morphs directly via World Menu -> New Morph...

This brings up a Morph Menu.

In this case, I selected a Basic Morph called a BoxedMorph.

I then cmd-clicked on the BoxedMorph to bring up a "halo" of "construction handles" (small circles around the Morph) and used the one in the lower right (Change Size) to make it bigger.

![BoxedMorph-Menu](UITour/Cuis11.png)

Clicking on the blue halo button gives a menu for the morph.

![ObjectInspector](UITour/Cuis12.png)

Selecting debug -> inspect morph gives an Object Inspector tool which allows one to see the inner structure of the morph, its "state".

One can click on a Morph's "instance variables" to see their values, and in turn "inspect" those values.

![BoxedMorph-Color](UITour/Cuis13.png)

You can also write code in the lower pane in which "self" is bound to the object clicked on in the upper left pane.  So one can do things like changing the setting of the "color" instance variable.

![BoxedMorph-Color](UITour/Cuis14.png)

![BoxedMorph-Code](UITour/Cuis15.png)
Another useful operation in a Morph's Menu is to look at its Code.

![BoxedMorph-Browsing](UITour/Cuis16.png)
The upper-left pane of the Browser shows the Class inheritance hierarchy for a BoxedMorph.  Each "child" or specialization of a Class has code which essentially says "I am like my parent but for these changes/extensions", which it then defines.

![Browsers are Morphs too](UITour/Cuis17.png)

Each graphical element in the UI is a Morph, which may be composed of sub-morphs.

This is also true of the UI tools.  You can click-select graphical elements (middle-click multiple times to select an interior submorph).  This means that you can look at any graphical element in the system, see how it is composed and how its code works.

![Send Morph to back](UITour/Cuis18.png)

In this case, I get the Morph Menu of the browser and "send it to the back" so that I can again see the BoxedMorph.

![Color method](UITour/Cuis19.png)
Looking again at the BoxedMorph's code, I see how the `color:` method is implemented.

![Breaking into the Debugger](UITour/Cuis20.png)

We learn by making mistakes and correcting them.

If you can make mistakes faster, you can learn faster!  

We like to make mistakes cheap and easy to fix.

Here I did a silly thing.  I typed the code to add the number 3 to a text string and pressed cmd-d (DoIt).  And guess what?  Things break!

![Debug1](UITour/Cuis21.png)

When this happens I get a textual view of the "code stack" showing what the system was doing when things broke.

I can move down the stack by selecting a frame just below the active one.  Clicking on the lower left pane shows the value for self, the String object which gets the message.

![Debug2](UITour/Cuis22.png)

Clicking on the next frame down (the "+" frame) shows what the fuss is about and I see the method code for "+" in the String class.

![Debug3](UITour/Cuis23.png)

At this point I am just going to close the debugger and ignore this as adding a string and a number really is a silly thing to do.  But I could have written or changed some code and them re-executed the stack frame to continue the computation -- without unwinding the stack! 

Well, this is enough for the brief introduction to the Cuis User Interface.

There is much to learn, but much help is available!

We hope you found the tour useful and have fun with Cuis!

