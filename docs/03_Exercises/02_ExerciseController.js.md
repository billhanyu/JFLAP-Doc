This file is located at `/exerController/`

This is a class written to implement the exercises feature of FA. It loads the exercise source JSON/XML file from the given `filePath` and displays on the page. Multiple problems are supported, so users can click on the question link to navigate from one question to another. Currently only acception of string is implemented as the testing function: it reads test cases as strings and output if the student's graph matches the expected result. More kinds of exercises can be added to this file.

## Variables ##

- jsav

	The jsav object of the page

- fa: FiniteAutomaton

	The finite autamaton graph on the page (editted by students)

- filePath: String

	The file path of the exercise source file

- dataType: String

	The file type of the exercise source, can be "JSON" or "XML"

- tests: []

	array to hold all problems in the exercise

- currentExercise: int

	The current problem index the user is at, default at 0, meaning the first problem

- testCases: []

	The test cases of one problem as an array

- initGraph: function

	function variable passed as part of `option` from `FAEditor`. Used for initializing wrong graphs for students to fix.

## Functions ##

- load()

	load the exercise source file using a synchronous AJAX call and store problems and test cases into variables.

- startTesting()

	called after the user hit "Test" on the page. Run the student graph on test cases and present the test result at the bottom of the page and scroll automaticly there.

- toExercise(button)

	binded with the problem links on top of the page, call `updateExercise` to show another problem.

- updateExercise()

	present a problem, with wrong graph is there is one, according to `currentExercise` variable. clean up the earlier test results etc.
