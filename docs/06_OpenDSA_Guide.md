This is a guide on how to add JFLAP web pages to an OpenDSA textbook.

OpenDSA documentation can be found [here](http://opendsa.readthedocs.io/en/latest/).

## Compile ##

OpenDSA textbooks can be comiled by typing this command in the directory `/OpenDSA/`:

```bash
make JFLAP
```

Where "JFLAP" is the textbook name. But to successfully run this command, you have to first make sure it is configured in the `Makefile`. You can reference how other textbooks are configured in the file and simply copy and paste some lines. The most important ones are:

```bash
JFLAP: min
	python $(CONFIG_SCRIPT) config/JFLAP.json
```

Remember to add a tab at the beginning of the second line.
As you can see, this is requiring that you have a `JFLAP.json` file under the folder `/config/`. You can choose to either edit on what I created or discard my work and configure by yourself. If you prefer the latter, you can copy another configuration file like `test.json` and make changes to the copy.

## Configuration of Textbook ##

The first part of the json file is not too critical to the content that you are going to generate. It's the capter part that matters. You'll see a structure like this:

```javascript
"chapters": {
	"Introduction": {
		"JFLAP/Introduction": {
			"long_name": "Introduction",
			"exercises": {}
		}
	}
}
```

This part of the file configures the chapters of the book. Each key-value pair you add under `chapters` will become a chapter of the book with they key as the title. Pay attention to `JFLAP/Introduction` in the `Introduction` chapter. This string is actually the filepath of the RST file which corresponds to this chapter. We are putting our RST files in `RST/en/JFLAP` folder and hence the filepath. Documentation to RST files can be found in the link I included to the top. 

`long\_name` is the name of the section inside the chapter. You can have multiple sections in a chapter, just like you can have multiple chapters in a book. 

`exercises` configures the OpenDSA exercises attached to the section. We did not make any exercises in OpenDSA format this summer, so if you want to know how to configure them look into files like `/config/test.json`.

## RST files ##

RST files are the raw materials for the contents of the textbook. The way we include an HTML page inside a textbook page is typing this line in the RST file:

```markdown
.. avembed:: AV/FLA/billyu/ui/FAEditor.html ss
```

"ss" stands for "slideshow". If you succeed the page is going to look like [this](http://billyu.me/OpenDSA/Books/JFLAP/html/FAEditor.html).

## Workflow ##

1. Make RST files under `/RST/en/JFLAP/`
2. Include the RST files in the configuration file under `/config/`
3. Include the make target in file `/Makefile`
4. Compile in the root directory
5. Visit (in browser) `Books/(bookname)/`
