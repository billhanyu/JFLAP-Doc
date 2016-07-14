Files:
1. `createDFAexercise.html`
2. `createDFAexercise.js`
3. `createDFAexercise.css`
all located at `/instructor/`, also see [Demo](!Demo) section for demo links.

## Features ##

In this exercise generator, for each problem instructors can either choose to put in an expression or a description. LaTex is supported for expressions. "Add problem" and "Add test case" buttons are provided for them to add more.

To the top of the page, there are radio buttons "Expression Only" and "With Wrong Graph". If instructors choose the latter, an "edit graph" button will appear for each problem. If clicked, the page will redirect to `FAEditor`, where uses can edit the wrong graphs for students to fix, when they are done, "finish" button will bring them back.

When instructors finish editing the exercise, "generate JSON" button to the bottom will show a download link to a JSON file, which can be used by exercise js files to show exercises.

## Possible Future Development ##

1. delete problem/test case
2. preview of exercises
