All grammar related computations are handled by the single file `/ui/grammarEditor.js`. This giant file serves the grammar editing functions, LL/SLR parsing, and many other functions, which make it more than 3000 lines. I tried to refactor this file by separating the functions and put them in different files, but due to historical reasons the functions and variables are so twisted together that it is not possible to disseminate them without introducing new bugs. I apologize to future developers.

Though the file is still tremendously long, I did my best renaming variables and structuring functions so that it is not very difficult to understand each one's job. Here I will talk about the variables and functions that I added/edited.

As for the exercise part of grammar, we have not come up with an adequate pattern for exercises. For now, I added multiple problem feature to exercises such as `BFParse` and `LLParse`, but the actual exercise is no different from the parsing proofs in `grammarEditor`. Future development could possibly focus on developing exercises for these parsing algorithms.

## Variables ##

- derivationTable: jsav matrix
	
	the derivation table shown during brute-force parsing

- parseTableDisplay: jsav matrix

	the parse table displayed to the user as a table, used by both LL and SLR parsing.

- parseTable: [[]]
	
	the parse table used by the algorithm of LL and SLR when parsing. `parseTable` is the data structure used for parsing, while `parseTableDisplay` is a UI element that is for the user to look at.

- parseTree: jsav tree

	the parse tree shown to the user during the slideshows

- conflictTable: [[]]

	the conflict table used by SLR for resolving conflicts (shift-reduce or shift-shift)

- ffTable: jsav matrix

	the table for FIRST and FOLLOW sets, displayed to the user and handle clicks

- selectedNode: faState

	store the current selectedNode, used for finite automaton editing.

- type: String

	an identifier of the type of the parsing algorithm

- grammars: [String]

	an XML String array that stores the grammars retrieved from a file.

- currentExercise: int

	current index of the exercise

- multiple: boolean

	a marker that records if the `multiple` feature of grammar editing is enabled. If it is, users can pick the index of the grammar that they want to edit and save multiple grammars to one file.

- fi: DOM

	the input box used in many places

- row: int

	current row number for the input box

- col: int

	current column number for the input box

## Functions ##

- focus(index: int, index2: int)

	`index` is the row clicked in the grammar matrix, and `index2` is the column clicked.
	present the input box at row `index` and column `index2` of the grammar table and remove any other input box existing.
	handle keyboard press events: arrow keys, enter and esc

- defocus(e)

	this function is binded to click events on the document.
	remove the appearing input box and save its value to the grammar table.

- updateSLRDisplay(remainingInput, stack)

	update the display of remaining input and the stack on top of the page.

- checkslrParseTable(parseTableDisplay, parseTable)

	check if the parse table of SLR parsing from user is correct. If user inputs one of the options for an entry when there is a conflict, the user will pass.

- checkllParseTable(parseTableDisplay, parseTable)

	check if the user input LL parse table is correct. This function is renamed from `checkParseTable` since conflict resolving feature was added to SLR parsing.

- choiceClickHandler()

	click handler for conflict option button. After the user clicks on some option to resolve the conflict this function will update the display and save the choice to `parseTable`

### Exercises ###

- initQuestionLinks()

	initialize the question links on top of the page based on the number of grammars from the file loaded. Used for exercises.

- updateQuestionLinks()

	update the appearance of the links. The user selected link will have a border while all others do not

- updateExercise(index)

	called after the user clicks on some question link. Present the grammar stored at `index`.

- toExercise()

	binded to the question links. This function is a bridge between the link and `updateExercise`

- toggleMultiple()

	binded to the `multiple` button on top of the page. Toggle the multiple mode which allows users to input multiple grammars.

- addExercise()

	binded to the button "add", add a new grammar to current editor.
