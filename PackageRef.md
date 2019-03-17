# Cuis Package Reference

Also, do a search on GitHub for repositories containing 'Cuis-Smalltalk' . The packages are as follows:



# 'Morphic-ColorEditor'

- https://github.com/KenDickey/Cuis-Smalltalk-ColorEditor
- 
````Smalltalk
description: 

'Color Editor/Picker'
provides: #'Morphic-ColorEditor'

requires: { #'Cuis-Base'. #'Morphic-Misc1'. 
	#'Graphics-Files-Additional'. #'CSS3-NamedColors'.}
````
## Of Interest in 'Morphic-ColorEditor'
- Adds custom Morphs to the Morphic Menu (World Menu -> New Morph..)

- Making use of other packages (Requires Features CSS3-Colors and Morphic-Misc-1)

- Shows Feature "autoload" in code (method #ColorPallet>>useCrayonColorDict)

- Panel creation and usage

- Drag 'n Drop (DropTarget)

- Discussion of Color in Cuis (class comment in ColorPaneMorph)

- Uses Radio Buttons & Slider

- Shows model/view separation (#when:send:to:)

- Adds menu items to World Menu 



# 'ClassCommentBrowser'

- */Cuis-Smalltalk-Dev/Packages/ClassCommentBrowser.pck.st
- 
````Smalltalk
description: 

'Browse class comments for classes with names such as "Pluggable," "Morphic," "Text," or "Morph" which appear in a hierarchical list.'

provides: #'ClassCommentBrowser'

requires: {}
````
## Of Interest in 'ClassCommentBrowser'
- Multipane browser with selection and search

- Popup menu on selected class allows opening browsers

- Class Comment Pane allows evaluation of Smalltalk expressions.



# 'Crypto-NaCl'
- https://github.com/KenDickey/Cuis-Smalltalk-Crypto-NaCl
-

````Smalltalk
description: 

'Smalltalk interface to the NaCl (salt) crypto library'

provides: #'Crypto-NaCl'

requires: { #'FFI. }
````
## Of Interest in 'Crypto-NaCl'
- Simple example of FFI (Foreign Function Interface) usage



# 'Interlingua-English-Lookup'

- https://github.com/KenDickey/Cuis-Smalltalk-Ia-En
- 
````Smalltalk
description: 

'Interlingua<->English Language Lookup'

provides: #'Interlingua-English-Lookup'

requires: { }
````
## Of Interest in 'Interlingua-English-Lookup'

- Shows how to set up a specialized SystemWindow using method #buildMorphicWindow.

- Shows a useful application built with a small amount of code.

- Note IEDictWindow>>fontPreferenceChanged updates sizes when font sizes change.



# 'Morphic-Misc1'

- https://github.com/KenDickey/Cuis-Smalltalk-Morphic-Misc1
- 
````Smalltalk
description: 

'Various basic morphs used by several packages'

provides: #'Morphic-Misc1'

requires: { }
````
## Of Interest in 'Morphic-Misc1'
- AddedCursors - 
Shows how to create and use a custom cursor.
- BorderedImageMorph - 
Morph with a custom #drawOn: method.
- DropColorMorph - 
A "color swatch" with a custom #dropAction: which gathers color setters into a popup selector menu.
- DropTargetMorph - 
Solves the problem of dropping state and behavior changes onto a specific Morph.  One creates a DropTarget and drops Morph updaters on that.  See how items are added to the Morph Menu via the method Morph>>addCustomMenuItems: hand: in the '*morphit-misc1' method category.
- EditPanel - My editModel is a "putty" or "shadow" copy to which all edit operations are applied.  Subclassed by LayoutMorphEditPanel and LayoutSpecEditPanel. 
If the user Update's then the changes are propagated from the editModel to the model.
- FrameMorph - 
Another morph with a custom drawOn: method.  Method morphContainsPoint: is specialized so that mouse clicks are only noticed on the frame itself.
- FramedLayoutMorph - 
Subclass of LayoutMorph which adds a frame.
- ImagePallet -
Used to display a pallet of widgets to grab a copy of to drop on something else.  Examples on the class side.
- LabelMorph - 
A StringMorph used as a label.  Has a few added convenience methods.
- LayoutMorphEditPanel - Useful to edit Layouts.  Selectable from a Morph's menu.
- LayoutSpecEditPanel - Useful to edit LayoutSpecs.  Selectable from a Morph's menu.
- LineMorph - 
A line useful to show a connection between other Morphs.
- PalletLayoutMorph - 
A LayoutMorph which allows grabbing (cloning) its submorphs.
- Panel - 
A very simple window with a label.  Useful when you don't need the full generality of a SystemWindow.
- PluggableScrollBar - 
- RadioButtonMorph - 
- RadioGroup - 
- SignMorph - useful morph to "point to" non-morph objects
- SimpleNumberEntryMorph - 
- WindowTitleMorph - Used in Panels to supply Title and common Buttons
 
### Adding Morphs to the New Morph menu

When the browser category or a Morph starts with 'Morphic-' and the Morph's class answers true to #includeInNewMorphMenu, then the Morph will show up under the category name with the 'Morphic-' prefix removed.  

The New Morph Menu is available via World Menu -> New Morph..

To prevent such morphs from showing up in the New Morph Menu, add a class side method category 'new-morph participation' and add a method #includeInNewMorphMenu which answers false.

You may also wish to add a class method #initializedInstance to return something special when a new Morph is created from the New Morph Menu.  Look at the code in UpdatingStringMorph class>>initializedInstance for an example.

# '... -NamedColors'
* 'XKCD-NamedColors'
* 'NBSISCC-NamedColors'
* 'CSS2-NamedColors'
* 'CSS3-NamedColors'
* 'Crayon-NamedColors'

- https://github.com/KenDickey/Cuis-Smalltalk-NamedColors
- 
````Smalltalk
description: 

'Color Name Dictionaries from various Color "Standards"'

provides: { #'XKCD-NamedColors'. #'NBSISCC-NamedColors'.
	#'CSS2-NamedColors'. #'CSS3-NamedColors'. #'Crayon-NamedColors''. }

requires: { }
````
## Of Interest in '... -NamedColors'
- Create custom color dictionaries

- Make your color dictionary the system color dictionary

- Note method Color>>doesNotUnderstand: which shows how new colors are created by name using the current color dictionary.



# 'Patterns'

- https://github.com/Cuis-Smalltalk/CodeExamples/tree/master/Patterns
-
````Smalltalk
description: 

'Useful Cuis code patterns, intended to help the programmer exploit some of the features of Cuis classes. These examples separate model from view and feature two styles: coupled and decoupled.

The coupled style employs the "dependency mechanism" and exposes the model to changes in the view and to views which were unanticipated. The primary methods of the dependency mechanism are #changed: and #update: .

The decoupled style employs the "observer pattern" which ensures that the model can remain unaffected by changes to the view or by additional views. The primary methods of the observer pattern are #triggerEvent: and #when:send:to: . This is the preferred style for Cuis, although both styles can be found in the base.
'

provides: #'Patterns'

requires: { }
````
## Of Interest in 'Patterns'
- Extensive line comments explaining reason for the code

- How to use PluggableListMorph
 
- Multiple views on a single model
 
- Model is independent of the views

- Examples: 
 
	- updating all views when one view changes

	- changing one view having no effect on other views


- Use of #when:send:to: and #triggerEvent: for communication between view and model (Observer Pattern)

- Contrasting Observer Pattern and Dependency Mechanism 



# 'Ropes'

- https://github.com/KenDickey/Cuis-Smalltalk-Ropes
- 
````Smalltalk
description: 

'Ropes: functional, immutable strings'

provides: #'Ropes'

requires: { #'Compression'. }
````
## Of Interest in 'Ropes'
- Thread-safe functional strings

- RopeFileList, RopeTextEditor show how to subclass/specialize system tools

- Shows a family of related data structures working to support a common abstraction.



# 'Solitaire'

- https://github.com/Cuis-Smalltalk/Games/tree/master/Solitaire
- 
````Smalltalk
description: 

'Freecell and Klondike Solitaire Card Games'

provides: #'Morphic-Games-Solitaire'

requires: { #'Graphics-Files-Additional' }
````
## Of Interest in 'Solitaire'
- Shows the structure of a complex application with a number of classes.

- Drag 'n Drop

- Card Images

- Undo

- Memento Pattern: save/restore game play

- FreeCell and Klondike games share behaviors implemented in their parent class: CardTableMorph

- Rule based interactions, e.g. CardContainerMorph>>okToPickUp: aCard

- Continuation Passing: Card Moves are animated asynchronously, passing in the 'next' action.  See CardTableMorph>>slideto:nSteps:delay:next:

- Dynamic DropShadows: See CardMorph>>setDropShadowMorph

- CardTableMorph class initializes games and causes table setup for Klindike, FreeCell, your-solitaire-game-here.

- FreeCell and Klondike register with the FileList to restore saved game files.

# 'Life'

- https://github.com/Cuis-Smalltalk/Games/tree/master/Life
-
````Smalltalk
description:

'The game of Life is an example of a cellular automaton. It was developed by Prof. John H. Conway at the University of Cambridge. Cells are displayed on a grid, analogous to graph paper, and live or die by the following rules:

- a live cell surrounded by 2 or 3 other live cells will continue to live
- a live cell surrounded by 0 or 1 other live cells will die of loneliness
- a dead cell surrounded by exactly 3 live cells will come alive
- a cell surrounded by 4 or more live cells will die of overcrowding

References:

Gardner, Martin, "Mathematical Games", Scientific American, October 1970, February 1971

"Some Facts of Life", Byte Magazine, December 1978'

````

## Of Interest in 'Life'
- A view creating another view

- Model is independent of the views

- Example of changing one view having no effect on other views

- Use of #when:send:to: and #triggerEvent: for communication between view and model (Observer Pattern)

- Each cell of the grid is a morph

- Need for popup menu signaled by grid morphs

# 'Construction'
- https://github.com/Cuis-Smalltalk/Games/tree/master/Construction
-
````Smalltalk
description: 

'Simulates the Construction Game'

Feature require: #Construction

'World->Open...->File List->Cuis-Smalltalk/Games/Construction'

'installPackage Construction.pck.st'

provides: { #'Construction-Model'. #'Construction-Graphics'. } 

requires: { #'Morphic-Widgets-Extras'. #'Game' }
````

## Of Interest in 'Construction'
- Automatic and interactive board tours
- No limits on equipment quantities
- History of player's progress
- Statistics
- Optional views to assist decision making
- Players automatically informed of doubled state
- Computer is banker, auctioneer, and auditor
- Auditing is continuous
- Rules enforced consistently
- Rudimentary animation of the die and movement of tokens

# 'TrafficLight'
- https://github.com/Cuis-Smalltalk/CodeExamples/tree/master/TrafficLight
-
````Smalltalk
description: 

'Simulates a traffic light'

Feature require: #TrafficLight

'World->Open...->File List->Cuis-Smalltalk/CodeExamples/TrafficLight'

'installPackage TrafficLight.pck.st'

provides: { #'TrafficLight-Model'. #'TrafficLight-Views' } 

````

## Of Interest in 'TrafficLight'
- Compare use of Dependency Mechanism and Observer Pattern
- When one light turns on the others turn off
- Views independent of the model



# More packages to come...
