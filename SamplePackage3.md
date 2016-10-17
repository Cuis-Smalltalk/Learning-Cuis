Making a Simple Package for Cuis -- Part 3
================================

This is a continuation of
- https://github.com/Cuis-Smalltalk-Learning/Learning-Cuis/blob/master/SamplePackage2.md

### Context

To review: 
- We are about to put together a SystemWindow.
- To do this we are writing the method IEDictWindow>>buildMorphicWindow
- The Window should look something like
![Cuis Window](SamplePkg/Sample-Package-009.png)

We will use Layouts as described in the Layout Tutorial
- https://github.com/Cuis-Smalltalk-Learning/Learning-Cuis/blob/master/LayoutTour.md

### buildMorphicWindow

Looking at the desired result, I see a column of
- Prompt and Text Entry
- Buttons
- List of Results

So let's write this down.

![Cuis Window](SamplePkg/Sample-Package-042.png)

Note that when I Accept this method, I get repeated warnings about undefined methods and options to change the text to known methods.

I just select the top line of the menu (the original text) to confirm that this is the choice I want.

OK.  Let's define all those methods.

### makeEntryArea

I'll start with the most complex one: `makeEntryArea`

The LayoutMorph returned is a row with the prompt ('Enter text: ') and a OneLineEditorMorph where the user can type words to be matched.

````Smalltalk
makeEntryArea
	"Answer a LayoutMoph containing the prompt and text entry area"
	
	| entryLayout entryHeigth |
	entryHeigth := self defaultSeparation * 2 + self textSizeUnit.
	
	entryLayout := LayoutMorph newRow.
	
	promptMorph := (StringMorph contents: 'Enter Text: ') 
					emphasis: AbstractFont boldCode; 
					yourself.
	promptMorph  layoutSpec: 
		(LayoutSpec fixedWidth: (promptMorph measureContents x)).
			
	entryTextMorph := (OneLineEditorMorph contents: 'salute'). "initial text"
	entryTextMorph 
		crAction: [self interlinguaContainsClick]; "Same action as IA-Contains button"
		layoutSpec: 
			(LayoutSpec proportionalWidth: 0.9).
			
	^ entryLayout 
		separation: self defaultSeparation;
		layoutSpec: (LayoutSpec proportionalWidth: 1 fixedHeight: entryHeigth);
		addMorph: promptMorph;
		addMorph: entryTextMorph;
		padding: #left
		yourself
````

The height of this LayoutMorph is calculated based on the text size.  One can change the text size via World menu-->Preferences-->Font Sizes.  Don't worry about this for now.  It takes some experinenting to get it right.  More on this later..

We have to set up how the window fields change when resized.  Part of this is by using LayoutSpec's.  We actually measure the size of the promptMorph's string to set this here.

We want the entryTextMorph to extend across the window and so we give it a proportional width of 0.9.  This means to take up 90% of the width of its layout.

We also set the `crAction` for the morph.  This code in invoked when the user types a carriage return / enter key.  As I said above, we want the same action as when a user clicks on the 'Interlingua Contains' button.

We want the prompt string to stick to the left of the layout, so we set the entryLayout's padding to `#left`.

We will see how this works when we actually build and return a window.

In the mean time, we need to Accept this code.

Here is what the text above looks like when pasted in the code editor (just select the buildMorphicWindow text with Cmd-a and replace).

![Cuis Window](SamplePkg/Sample-Package-043.png)

When I Cmd-s (Accept), I find that I have some fixes to make.

![Cuis Window](SamplePkg/Sample-Package-044.png)

I forgot to define `promptMorph` as an instance variable.

No worries.  I can select 'declare instance' and the code is added to the class definition for me.  Nice this!

![Cuis Window](SamplePkg/Sample-Package-045.png)

Ah! The OneLineEditorMorph class is missing.

This is a more serious problem.

Time to bail out (cancel) and load the required code!

What has happened is this.  Cuis keeps a small kernel by moving optional code into packages.  This means that the core is smaller and easier to understand.  It also means that we can learn each package Feature incrementally as we need them.

As Cuis gets simpler sometimes code we use and rely on gets moved somewhere else!  That happened to me here.  The OneLineEditorMorph was moved into a package in the Packages directory with a Feature name of `#'Morphic-Widgets-Extras`.

You can do a text search to find such classes.  In a Linux shell this would be `grep OneLineEd --files-with-matches */*.st` but each OS has some text search method. 

![Cuis Window](SamplePkg/Sample-Package-046.png)

After loading the Morphic-Widgets-Extras feature, we can Accept the code.  Note that the word `OneLineEditorMorph` turns from red to bold and black to indicate it is a known class name.

Also, you can use a FileList to open a Package Browser to view code in a package without loading it into you image.

This sometimes helps me decide if a package has something I want.

![Cuis Window](SamplePkg/Sample-Package-047.png)

When using something from another package, we say that other package is _required_ for our package to work.  The system does not know this. We need to open an Installed Packages browser and click on the 'add requirement' button.

Note that we only get to select from loaded packages.

The Cuis-Base selection requires a particular version/revision of the base image.  You can delete a previous requirement and select this again to get a new Cuis-Base revision requirement if you need the something provided in the latest Cuis release.

![Cuis Window](SamplePkg/Sample-Package-048.png)

In any case, after adding a Feature Requirement, you need to save your package.  

Of course, after you do this it would be a good idea to do a "git commit" "git push" as well!  (not shown)

![Cuis Window](SamplePkg/Sample-Package-049.png)

### makeButtonArea

````Smelltalk
makeButtonArea
	"Answer a LayoutMorph with our four buttons -- a column of two rows"
	
	|  buttonHeight buttonLayout interlinguaButtonLayout englishButtonLayout buttonArea |
	buttonHeight := self textSizeUnit * 2.
	buttonLayout := LayoutSpec proportionalWidth: 0.3 fixedHeight: buttonHeight.
	
	interlinguaButtonLayout := LayoutMorph newRow. "a row of two buttons"

	interlinguaButtonLayout 
		padding: #center; 
		separation: 2;
		addMorph: 
			(PluggableButtonMorph 
				model: self 
				action: #interlinguaContainsClick  
				label: 'Interlingua Contains')  layoutSpec: buttonLayout;
		addMorph: 
			(PluggableButtonMorph 
				model: self 
				action: #interlinguaStartsClick  
				label: 'Interlingua Starts') layoutSpec: buttonLayout.

	englishButtonLayout := LayoutMorph newRow. "a row of two buttons"
									.
	englishButtonLayout 
		padding: #center; 
		separation: 2;
		addMorph: 
			(PluggableButtonMorph 
				model: self 
				action: #englishContainsClick  
				label: 'English Contains') layoutSpec: buttonLayout;				
		addMorph: 
			(PluggableButtonMorph 
				model: self
				action: #englishStartsClick  
				label: 'English Starts') layoutSpec: buttonLayout.

	buttonArea := LayoutMorph newColumn.
	^ buttonArea 
			layoutSpec: (LayoutSpec proportionalWidth: 1; fixedHeight: 4 * self textSizeUnit);
			addMorph: interlinguaButtonLayout ;
			addMorph: englishButtonLayout ;
			yourself
````


@@@
