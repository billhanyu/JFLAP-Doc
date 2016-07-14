Relative files:

- `/fa/FA.js`
- `/ui/REtoFA.*`
- `/regular/REtoFAController.js`
- `/regular/Discretizer.js`

## REtoFAController.js ##

To properly lay out the edges so that they spread out in some way, I introduced [paper.js](http://paperjs.org) to use AffineTransform in order to lay out better. The good thing is the API of AffineTransform provided by paper.js is almost exactly the same with the one from Java library.

### 'Class' Variables ###

- toDo: []

> The array of transitions that still require expansion.

- toDoTransitions: []

> The set of lambda-transitions still unborn!

- action: int

the current action, 0 means no action. Other actions: DEOR, DECAT, DESTAR, DEPARENS, NOTRECOGNIZED are 1,2,3,4,5 respectively.

- transition 

the transition being replaced.

- transitionNeeded

> The number of transitions needed for the current step

- replacements: []

> The replacement transitions

- catBeinMade, catEndMade: Bool

helper boolean variables for concatenation.

### Variables ###

- jsav, fa: obvious from name

- start, end: faState

The start and end nodes to start with.

- transition: faTransition

The current transition being dealt with.

### Functions ###

- clear()

clear the finite automaton graph and delete the DOM element.

- requiredAction(expression: String) -> int

find out the next action needed based on the expression and return.

- lambda(from: faState, to: faState)

add a transition with weight of lambda from `from` to `to`.

- transitionCheck(transition: faTransition)

check if the current transition needs an action. If so, compute its replacements and call `nextStep` function.

- completeStep()

complete a step by replacing a transition with calculated replacements.

- nextStep()

update the UI about remaining step counts and prompt the user if the process is complete.

- exportToFA()

save the generated FA to local storage and export to `FAEditor`

- completeAll()

finish all steps immediately. This is done by calling `completeStep` whenever there is a pending action

- replaceTransition(transition: faTransition, exps: [String])

given a transition and transition weights to replace it, replace the transition. Paper.js library is used here to lay out the new edges.

## Discretizer.js ##

### Functions ###

- or(expression: String) -> [String]

given the expression, return the array of strings that when ORed (+) together, would be the expression.

- cat(expression: String) -> [String]

given the expression, return the array of strings that when concatenated (\*) together, would be the expression.

- delambda(string: String) -> String

given a string, return the empty string if the string is lambda, else return the string itself.
