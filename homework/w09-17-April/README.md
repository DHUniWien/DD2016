Homework for Week 9
==============

This week's homework has two parts; first you will be revisiting the SQL schemas you made a few weeks ago, and then you will be practicing your XPath and XQuery skills.

Part 1: Data management with SQL
---------

Choose any **TWO** of the three database design scenarios that you provided a schema for. You will find that I have turned your design documents into a full MySQL schema. You can *instantiate* a database from each schema (that is, get it up and running in MySQL) with the following command at the mysql prompt:

	mysql> \. path/to/your/schema.sql
	
(You should replace the `path/to/your/schema` with the real path to the schema file.)

Now add a record to the database you have made, as specified according to the list below. If you find you need to change your schema, then you should edit the schema file directly in your text editor (SublimeText, Notepad++, TextMate, etc.) and reload the database. When you are done, then dump your database by running the following command from the command line if you are on a Mac:

	$ mysqldump -u root -p YOUR_DATABASE_NAME > YOUR_DATABASE_NAME.sql
	
and save the resulting file in a folder called Homework5 in your class Github repository. **Don't forget to push this to Github!**

<hr>

Problem #1: Library lending records

Add a record for John Smith, who borrowed 'Pride and Prejudice', and it is
due back on 26 February 2013.

Problem #2: Teaching a class

Add a record for a class called "English Composition" with three students
(you can name them whatever you like).

Problem #3: Music reception 

Add a record for a playbill that announces a series of performances of
Beethoven's Fifth Symphony by the Boston Symphony Orchestra (conducted by
Marcelo Lehninger) on 18-20 September 2014.

Problem #4: Journal articles

Add a record for the following article that was published in your journal:
Steinhauser, G. "The nature of navel fluff". Your Journal, vol. 72, issue
6. You had three reviews (feel free to make up names of reviewers), two of
which strongly recommended publication and one which recommended rejection.


Problem #5: English plays

Add a record for the following snippet of a Shakespeare play:

	First Clown:
	A pestilence on him for a mad rogue! 'a pour'd a flagon
	of Rhenish on my head once. This same skull, sir, was, sir,
	Yorick's skull, the King's jester.

	Hamlet:
	This? [Takes the skull]

	First Clown:
	E'en that.

	Hamlet:
	Alas, poor Yorick! I knew him, Horatio, a fellow of infinite
	jest, of most excellent fancy. He hath bore me on his back a
	thousand times, and now how abhorr'd in my imagination it is!
	My gorge rises at it.

	Hamlet Act 5, scene 1, 179–188
	
	
Part 2: XQuery and eXist
------------------------

Your assignment is to get comfortable with XQuery in eXist, by both reading XML data and updating it. In order to solve these problems you will want to look at the XQuery examples I gave you last week.

Step 1
------
Make me a list of all the play titles in your Shakespeare collection,
wrapped in a `<title>` element inside a `<play>` element.

Step 2
------
Now get the list of characters in each play. The characters appear in the
plays as the text of the `<speaker>` element. Put each of them in your own
`<speaker>` element, after the `<title>` inside your `<play>`.

Step 3
------
You'll have a huge list from the above! You can make it smaller with the
XPath/XQuery function distinct-values(). So, for example,

	for $part in distinct-values($play//tei:speaker)
		
Change your XQuery so that you are listing only the distinct speakers.

Step 4
------
Now you'll probably start to see examples of the same speaker spelled in
different ways. You can make this more obvious using an 'order by'
statement, which is the O in FLWOR. Just put a line

	order by $speaker
	
directly underneath the for statement from the last step.

Step 5
------
It's time to start cleaning your data! Save the XQuery file as you have it so far to your 'Homework5' folder in your personal Github directory, and commit and push it. 

Now have a look at the file `xml_examples/xquery_examples/example_9.xquery` This is our example in class of how to update files in eXist. Use this as a template to do your own data cleanup on your choice of play. Look for the different variants of a single name and put them in $variants, and put the canonical form of the name in $correct_name. Let loose your perfectionist tendencies! (Or borrow some perfectionist tendencies from a friend.)

Step 6
------
Look for other things to update in the same way, in the plays. For example,
you could add a 'type' attribute to distinguish the headers for acts from
the headers for scenes. Or else you could number them with an 'n'
attribute. Here's how you add an attribute to an element in eXist XQuery:

	update insert attribute name {'value'} into $element
	
where `name` is the attribute name, `value` is the attribute value, and the variable called `$element` contains the element that you want to add the attribute to.