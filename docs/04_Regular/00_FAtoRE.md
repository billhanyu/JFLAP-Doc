Relative files:

- `/fa/FA.js`
- `/ui/FAEditor.*`
- `/regular/FAtoREController`

I will talk about `FAtoREController` here, which is mainly about the computational process. For UI handling, you would have to read the code.

## Variables ##

- jsav

	the jsav object, no surprise

- fa: FiniteAutomaton

	the finite automaton graph object passed in from `FAEditor`

## Functions ##

- checkForTransitions()

check if the graph is a complete graph with transitions between any pair (including a node and itself) of nodes. If so, prompt the user to use the collapse state tool to start collapsing.

- collapseState(node: faState?)

collapse a node clicked. If no parameter is passed in, initialize the collapse state tool. After collapsing, present the transition table as a floating dialog. 

- completeTransitions() 

automatically add empty transitions between pairs of nodes that have no transition between them. This function is called after the user hits "Do it" button.

- finalizeRE()

this function is binded to the "finalize" button at the bottom of the transition table. After this button is clicked, the function removes the node collapsed and edges connected to it, and update the other edge weights. 

- generateExpression()

this function can only be called when there are only two states left in the graph. generate the regular expression based on the two states and display on the page.

## Other Functions (defined not as part of class) ##

- normalizeTransitionToRE(transition: String, last: Bool) -> String

change the weights of edge in form "...\<br\>..." to "..+.." and add parentheses if needed. Prepare for conversion to regular expression.

- transitionsTableHandler(row: int, col: int, e: event)

handles the click on the transition table shown when the collapse state tool is used. When user clicks on a row of table, transitions that generate the row are highlighted.

- exportToRE()

first save the regular expression generated into `localStorage`, then open `REtoFA.html` to export.

- addStar(transition: String) -> String

a helper function to add "\*" to the end of the transition string, parentheses wrapping the transition string are added if needed.
