In this project, the following kinds of FA (Finite Automata) are implemented:

1. Deterministic Finite Automaton (DFA)
2. Non-deterministic Finite Automaton (DFA)
3. Non-deterministic Pushdown Automaton (NPDA)
4. Turing Machine
5. Moore Machine
6. Mealy Machine

All of which are dependent on the file `FA.js` and `serializeableGraph.js` in `/fa/`. Each of these features are built as demo-like pages with HTML and CSS. The HTML files can be accessed in `/ui/` folder. Dependencies can be found in the `head` of the HTML files. During development I have been trying to separate the user interface and the "computing" code. I did this successfully with Turing Machine and NPDA, so they have controller files `TuringMachine.js` and `NPDA.js` in `/fa/`. Both of two are extending `FA.js`.

`FA.js` is worth a lot of attention during development. This file was written by Sung-hoon and Martin last year and modified by me. I mainly added more common features of all finite automata in there and removed some functions unique to certain FA.
