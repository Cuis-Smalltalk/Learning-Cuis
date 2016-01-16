# Learning-Cuis
Quick-UI-Tour

Greetings and Welcome!!

This file is a quick tour of the Cuis User Interface (UI).

Smalltalk defined Object Oriented.  All computation is done by objects sending messages to themselves and each other.

Cuis shares with other Smalltalk implementations the characteristic that all objects are live.  All objects can be inspected and changed while they are executing.

There are many great tools waiting to be used.  This tour gives an introduction to a few  of the most important ones. 

![Cuis Window](UITour/Cuis01.png)

Perhaps the best way to think of Cuis is as a playground.

You can open a Cuis image using a protable virtual machine and see the same windows in the same positions pixel-per-pixel on Linux, Macintosh, Windows or any operating system where the VM runs.

You can start an image, do things with it and throw it away or save the image and its  record of the changes to be opened another time and take up right where you left off.

![WorldMenu](UITour/Cuis02-WorldMenu.png)

If you cmd-click on the desktop, you will see a World Menu.  

The command button "cmd-" may be a control ("ctrl") key, a window key, an apple key, or some other command key based on your keyboard and operating system.

A World Menu can be used for one-shot selections.  Just click on your selection, the action takes place and the menu disappears.  If you want to keep the menu up to make several selections, click on the push-pin icon in the upper right-hand corner.  The icon will disappear and the menu will stay up until you dismiss it by clicking on the circle-x close button in the upper left-hand corner.

![World+HelpMenu](UITour/Cuis03-World+HelpMenu.png)

Of particular interest is the Help submenu.

Editor Keyboard Shortcuts gives helpful command-key usages.

The Help menu gives access to a lot of good information.

![TerseGuide](UITour/Cuis04-TerseGuide.png)

Also available from the Help Menu is the Terse Guide to Cuis.

The Terse Guide has many topics and shows code usages.  

Every time you re-visit a topic, the page is created again.  So you can write code here and "DoIt" (cmd-d) or "PrintIt" (cmd-p) to see results.

![SystemBrowser](UITour/Cuis05-SystemBrowser.png)

Clicking on World Menu -> Open.. -> Browser  brings up a System Browser, from which you can view all the code in the Cuis environment.

The panes are arranged by Category (upper left), Class, Topic, and Method (the code shown in the lower pane).

![Workspace](UITour/Cuis06-Workspace.png)

Clicking World Menu -> Open.. -> Workspace  brings up a Workspace window for you to type and run code.

As you type, the system does "syntax hilighting" which gives clues to class and method names.  If you start typing a method name, you can hit the Tab key which will usually give you a "select list" of possible message name completions.

Again, you can select code and DoIt (cms-d) or PrintIt (cmd-p) to get results.

![FileList](UITour/Cuis07-FileList.png)

When you click on World Menu -> Open.. -> File List you get a multi-pane file browser.

The upper left pane shows a tree-view of the file system.  You click on the small triangles to show/hide subtrees.

Clicking on a Directory shows File names in the right hand pane.  Clicking on a File entry shows its contents in the lower pane.

The File List is context sensitive.  Viewing a text file or an image file or a file with Smalltalk Package code gives you different option buttons.

You can also "right-click" or "double-click" to get a context sensitive menu in many browser panes.  This works in most browsers.

In the picture above, a Package File has been selected.  Cuis Packages implement system Features.  The file shown implements a Feature named 'Graphics-Files-Additional' and requires the Feature 'Compression" be present.

Clicking on the "installPackage" button has the same effect as running the code in the previous Workspace picture.
''''Smalltalk
    Feature require: #'Graphics-Files-Additional'.
''''

![InstalledPackages](UITour/Cuis08-InstalledPackages.png)

One way of keeping Cuis small and understandable is to use a small core of code and load Package Files to add Features.  Note the Terse Guide topic 'Features'.

World Menu -> Open.. -> Installed Packages shows the packages loaded into your Cuis environment.

You can create your own packages and add/remove requirements so that any packages your package requires will be loaded when you need them.   Note the Terse Guide topic 'Features'.

![MorphMenu-Ellipse](UITour/Cuis09-MorphMenu-Ellipse.png)

Smalltalks which descend from Squeak, like Cuis, have a system in which all graphic entities are objects called Morphs.

You can get morphs directly via World Menu -> New Morph...

This brings up a Morph Menu.

In this case, I selected a Basic Morph called an EllipseMorph.

I then cmd-clicked on the EllipseMorph to bring up a "halo" of "construction handles" (small circles around the Morph) and used the one in the lower right (Change Size) to make it bigger.

![EllipseMorph-Menu](UITour/Cuis10-EllipseMorph-Menu.png)

Clicking on the blue Menu button gives a menu for the morph.

![ObjectInspector](UITour/Cuis11-ObjectInspector.png)

Selecting debug -> inspect gives an Object Inspector tool which allows one to see the inner structure of the morph, its "state".

One can click on a Morph's "instance variables" to see their values, and in turn "inspect" those values.

You can also write code in the lower pane in which "self" is bound to the object clicked on in the upper left pane.  So one can do things like changing the setting of the "color" instance variable.

![Worspace-Code](UITour/Cuis12-Worspace-Code.png)

Another way to change a value is to send a message to an object using the Workspace.

![Workspace-Menu](UITour/Cuis13-Workspace-Menu.png)

To get a reference to a morph, one has to turn on "morphs dropped on me create a variable reference" option in the Workspace.  You do this using the blue triange to select the Workspace Menu and click on the box at the left of the selection.

If you then drag the EllipseMorph onto the workspace (hold down the mouse key, drag the ellipse, let the key up over the Workspace) then a text reference to the ellipse ("ellipsemorph618") is created.  You can then send messages to the ellipse.

![Debugger](UITour/Cuis14-Debugger.png)

We learn by making mistakes and correcting them.

If you can make mistakes faster, you can learn faster!  

We like to make mistakes cheap and easy to fix.

Here I did a silly thing.  I typed the code to add the number 3 to a text string and pressed cmd-d (DoIt).  And guess what?  Things broke!

When this happens I get a textual view of the "code stack" showing what the system was doing when things broke and three options.  "Proceed" means "try this again".  "Abandon" means "forget it, sorry I asked".  "Debug" means "open a Debugger and let me play with this, maybe I can fix it".

![Debugging](UITour/Cuis15-Debugging.png)

I chose the Debug option and clicked on the "DoIt" stack frame which shows the code I was trying to run.

![Debug-Plus](UITour/Cuis16-Debug-Plus.png)

I then clicked on "+" to see what the fuss is about and see the method code for "+" in the String class.

At this point I am just going to close the debugger and ignore this as adding a string and a number really is a silly thing to do.  But I could have written or changes some code and them re-executed the stack frame to continue the computation -- without unwinding the stack! 

Well, this is enough for thie brief introduction to the Cuis User Interface.

We hope you found the tour useful and have fun with Cuis!

