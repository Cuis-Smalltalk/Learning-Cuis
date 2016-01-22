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

- https://github.com/KenDickey/Cuis-Smalltalk-Ia-En
- https://github.com/KenDickey/Cuis-Smalltalk-Morphic-Misc1
- https://github.com/KenDickey/Cuis-Smalltalk-NamedColors
- https://github.com/dhnorton/Cuis-Smalltalk-patterns
- https://github.com/KenDickey/Cuis-Smalltalk-Ropes
- https://github.com/KenDickey/Cuis-Smalltalk-Solitaire
