This file is located at `/fa/`

This file contains the class `TuringMachine`, `Configuration`, `Tape`, and `TMTransition`. It extends the `FiniteAutomaton` class defined in `FA.js`.

## TuringMachine ##

### Variables ###

Variables here are additional to `FA.js`. For a full list of variables refer to the documentation for `FA.js`.

- transitions: [TMTransition]

	store the edges of the Turing Machine as an array of `TMTransition`. *This variable is not used*

### Functions ###

- *initializer*

	use the following code to initialize a `TuringMachine` object

```javascript
var tm = jsav.ds.tm($.extend({width: '90%', height: 440, emptystring: square, editable: true}, opts));
// initialize a TuringMachine object with width and height defined, emptystring equal to `square`. Users are able to drag nodes.
```

- addTransition(start, end, toRead, toWrite, direction)

	add a transition to the Turing Machine, both display on the user interface and store the added transition in `transitions` array as `TMTransition`. *This function is not used*.

- play(inputString)

	show the slideshow of traversing the Turing Machine with `inputString`. This function works along with `onClickTraverse` method in `TMEditor`.

- showAccept(state)

	color the `state` green in the graph.

- removeAccept(state)

	remove the class for green color on `state`

- showReject(state)

	color the `state` red in the graph

- isInitial(state)

	return if `state` is the initial state of the graph

- isFinal(state)

	return if `state` is one of the final nodes of the machine

- traverse(currentStates)

	`currentStates` is an array of `faState`. This function is given an array of current states, and returns the set of next configurations as an array of `Configuration`.

- serializeToXML()

	return the XML format string of the machine. For download, refer to `TMEditor`

- initFromXML(text)

	initialize the machine from `text`, parsing it as XML. Note that this is not a static function, which means you have to have an object first before calling this function.

- updateAlphabet()

	update the input alphabet to DOM element with id `alphabet` and the stack alphabet to DOM elment with id `stackalphabet`.

## Configuration ##

### Variables ###

- state

	The `faState` current state of the configuration.

- tape

	The `Tape` object of the configuration. See class `Tape`.

### Functions ###

- toString()

	return the configuration as an understandable string

- toID()

	return the ID of the configuration. This is used only for removing duplicate configurations in function `traverse`

## TMTransition ##

*This class is not really used, kept here for possible future development.*

### Variables ###

`weight, jsav, start, end, toWrite, toRead, direction`: clear from name

### Functions ###

- getWeight()

	return the weight of the transition

## Tape ##

This class is written by Sung-hoon and has not been changed by me. Please refer to his documentation.

## Other Functions ##

Functions have not been changed, although most computing functions in `TMTest.js` from last year were moved here to improve the strucutre of the code.
