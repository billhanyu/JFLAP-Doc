This is an exercise for student to create FA according to the problem statement.

Relative files:
`/fa/FA.js`
`/exerController/ExerciseController.js`
`/ui/FAEditor.js`
`/ui/FATester.html`

`FATester.html` includes `FAEditor.js`, and in `FAEditor.js`, the program reads the `id` of `h1` tag to determine the type of html file it is handling. If the `id` is `tester`, `FAEditor` calls `ExerciseController.js` to load the source file and handle the rest. Only the initializing code for the exercise part of `FATester` is in `FAEditor`. `FATester` still uses all editing features provided by `FAEditor`. I really hope I made that clear.

The page can be found in the [Demo](!Demo) section.
