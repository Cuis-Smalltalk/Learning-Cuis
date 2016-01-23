# Cuis Package Reference

Also, do a search on GitHub repositories containing 'Cuis-Smalltalk'


#'Morphic-ColorEditor'

- https://github.com/KenDickey/Cuis-Smalltalk-ColorEditor
````Smalltalk
description: 'Color Editor/Picker'
provides: #'Morphic-ColorEditor'
requires: { #'Cuis-Base'. #'Morphic-Misc1'. 
	#'Graphics-Files-Additional'. #'CSS3-NamedColors'.}
````
## Of Interest
- Adds custom Morphs to the Morphic Menu (World Menu -> New Morph..)

- Making use of other packages (Requires Features CSS3-Colors and Morphic-Misc-1)

- Shows Feature "autoload" in code (method #ColorPallet>>useCrayonColorDict)

- Panel creation and usage

- Drag 'n Drop (DropTarget)

- Discussion of Color in Cuis (class comment in ColorPaneMorph)

- Uses Radio Buttons & Slider

- Shows model/view separation (#when:send:to:)

- Adds menu items to World Menu 


#'ClassCommentBrowser'

- https://github.com/dhnorton/Cuis-Smalltalk-comments
````Smalltalk
description: 'Browse class comments for classes with names such as "Pluggable," "Morphic," "Text," or "Morph" which appear in a hierarchical list.'
provides: #'ClassCommentBrowser'
requires: {}
````
## Of Interest
- Multipane browser with selection and search

- Popup menu on selected class allows opening browsers

- Class Comment Pane allows evaluation of Smalltalk expressions.


#'Crypto-NaCl'

- https://github.com/KenDickey/Cuis-Smalltalk-Crypto-NaCl
````Smalltalk
description: 'Smalltalk interface to the NaCl (salt) crypto library'
provides: #'Crypto-NaCl'
requires: { #'FFI. }
````
## Of Interest
- Simple example of FFI (Foreign Function Interface) usage


#'Interlingua-English-Lookup'

- https://github.com/KenDickey/Cuis-Smalltalk-Ia-En
````Smalltalk
description: 'Interlingua<->English Language Lookup'
provides: #'Interlingua-English-Lookup'
requires: { }
````
## Of Interest

- Shows how to set up a specialized SystemWindow using method #buildMorphicWindow.

- Shows a useful application built with a small amount of code.

- Note IEDictWindow>>fontPreferenceChanged updates sizes when font sizes change.

#'Morphic-Misc1'

- https://github.com/KenDickey/Cuis-Smalltalk-Morphic-Misc1
````Smalltalk
description: 'Various basic morphs used by several packages'
provides: #'Morphic-Misc1'
requires: { }
````
## Of Interest
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
 
# Adding Morphs to the New Morph menu

When the browser category or a Morph starts with 'Morphic-' and the Morph's class answers true to #includeInNewMorphMenu, then the Morph will show up under the category name with the 'Morphic-' prefix removed.  

The New Morph Menu is available via World Menu -> New Morph..

To prevent such morphs from showing up in the New Morph Menu, add a class side method category 'new-morph participation' and add a method #includeInNewMorphMenu which answers false.

You may also wish to add a class method #initializedInstance to return something special when a new Morph is created from the New Morph Menu.  Look at the code in UpdatingStringMorph class>>initializedInstance for an example.


- https://github.com/KenDickey/Cuis-Smalltalk-NamedColors
- https://github.com/dhnorton/Cuis-Smalltalk-patterns
- https://github.com/KenDickey/Cuis-Smalltalk-Ropes
- https://github.com/KenDickey/Cuis-Smalltalk-Solitaire
