This file is located at `/fa/`

Most of the functions are moved form `NPDATest.js` from last year. They are packaged into `NPDA` class to improve code structure. The user interfaces for congurations during a traversal is improved to be similar to what's in JFLAP. See demo section for more details.

## NPDA ##

### Variables ###

- configurations: jQuery object

	configurations jQuery object used to setup view at a step

- configViews: [$]

	configurations view for a step

- step: int
	
	current step of the slideshow the user is at.

### Functions ###

*Only functions added by me are documented here*

- showAccept, removeAccept, showReject, isInitial, isFinal

	same with `TuringMachine`

- updateAlphabet()

	update the alphabet to DOM elements with id `alphabet` and `stackalphabet`

- setupControls()

	bind configurations showing functions to `jsavcontrols`. I did not use JSAV for displaying the configurations during traversal because JSAV apparently does not support DOM element operations, i. e. if you remove/add a DOM elmeent and do
```javascript
jsav.step();
```
You will only see the final result and are not able to go forward/backward.

serialzie to/deserizlize from XML functions are also moved here.
