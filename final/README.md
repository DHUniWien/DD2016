Management of Digital Research Data 
===================================
Final Exam FS2016
-----------------

The exam consists of three sections, testing your understanding of relational (SQL) databases, XML databases, and graph databases. Please answer as many of the questions as you can, as completely as you can, and record your answers using your text editor in a file called `final_exam.txt`. Your final_exam document must be emailed to me by **SUNDAY 5 JUNE at 11:59PM**. 

You should be able to answer all the questions without seeking outside help, based on what we covered in class over the course of the term (although you are perfectly welcome to use any online guide or documentation that you can find.) However, as collaboration is part of life inside and outside academia, if you do get help from another person, please make a note of who helped you to do what, and how far you got before seeking help. 

If you have any questions or unexpected problems, please do ask! (Remember that you are the second set of students who have ever taken an exam for this class, so that means that if there are any difficulties I've overlooked, I need you to alert me to them.) You will need to figure out the answers to the test questions yourselves, but don't let an unexpected problem or error prevent you from getting to the questions in the first place. I'm here to help!


Part 1. Relational databases
----------------------------

In order to complete these questions, you will need the `world` database that we loaded long ago in the beginning of term. In case you do not have this database, you can load it from the .sql file in this directory.

For each of these problems, write an SQL statement that answers it and paste the SQL into your `final_exam` document, numbered accordingly. You can find a handy guide to SQL syntax [here](http://cse.unl.edu/~sscott/ShowFiles/SQL/CheatSheet/SQLCheatSheet.html).

*Instructions*

1. What tables are there in this database?

2. How are they related to each other?

3. What are the names of the countries in South America?

4. How many cities have a population greater than 1 million?

5. What is the most populous country? What is its population?

6. How many official languages are there in the world?

7. In which countries is Italian spoken?

8. In what district is the capital city of South Africa?

9. In which countries is French an official lanugage?

10. What is the total population of countries with English as an official language? (Hint: you can use the `sum` function, which works a lot like `count`, to add up a column of numbers.)

11. According to the CIA World Factbook, 4.2% of the Swiss population are English speakers. Add a record to the CountryLanguage table to indicate this.

12. Who is the head of state in the countries where Dutch is spoken?

13. Hm, some of those are a bit out of date - Queen Beatrix abdicated in 2013! Update the relevant records to reflect that the head of state is now Willem-Alexander.

14. In what country and district is Sevastopol?

15. Oops, that has been a subject of contention too since this database was made. Change the records for all Crimean cities to reflect that they are currently governed by Russia.

16. Let's say that we want to start tracking the religions of the world. Create a table to hold the following information;
  * Country
  * Religion name
  * Adherents, by percentage of population
  * Whether the religion is an established one in the country.
  
  For extra credit, do this with two tables, where one is a table to list basic facts about the religion and the other is a junction table between religion and country.
  
  
Part 2. Database design
-----------------------

You come into possession of a set of postcards from the turn of the twentieth century. You want to capture information about these postcards in a database, so that other people can have virtual access to the collection without coming to your doorstep.

*Instructions*

1. Make a list of the features of the postcards that someone might care about, as well as ways in which the postcards might be related to each other. Draw a picture if you like.

2. Write the CREATE statements for a database that captures all of these interesting attributes.

3. Look at the records at the following links, and write the SQL INSERT statements that will capture the interesting information about these postcards into your own database. (If you want to capture text on the postcard but find the handwriting too difficult to read, then feel free to use placeholder text. I won't be checking!)
  
  - http://digital.lib.umd.edu/image?pid=umd:62178&skin=ntl
  - http://digital.lib.umd.edu/image?pid=umd:84746&skin=ntl
  - http://digital.lib.umd.edu/image?pid=umd:259908&skin=ntl
  - http://digital.lib.umd.edu/image?pid=umd:65698&skin=ntl
  - http://digital.lib.umd.edu/image?pid=umd:96800&skin=ntl
  
  
Part 3. XML databases
---------------------

In order to complete these questions, you will need the set of XML files in the `archimedes` directory, as well as the file `archie-tei.rng`. (You won't do anything with that file, but oXygen needs it in order to validate the XML.) You have two options for loading them into oXygen:

* Make a new collection (alongside the 'shakespeare' collection; you might call it 'archimedes') in your eXist-DB on your computer, and use the eXist-db XQuery transformer to run your queries, as we did with the Shakespeare files. (If you are unable to make the new collection via the web dashboard - some people, including me, have had this problem! - try opening the Java Admin Client instead and make the collection there.)
* Use the default Saxon-PE XQuery transformer, and refer to the collection with the full path of the directory they are in on your computer, e.g. 
		/PATH/TO/DD2016/final/archimedes


These files are TEI XML transcriptions of the pages of the [Archimedes Palimpsest](http://archimedespalimpsest.org), taken from their website. Take a quick look at one of the XML files to see its structure - you will find the familiar `teiHeader` element with information about the document, and then a `facsimile` element that would link this transcription to pictures of the palimpsest if we had downloaded them, and finally the `text` element that contains the transcription. If you like, you can look for the pictures of the manuscript on their website, but palimpsests are by their nature very difficult to read! Fortunately, someone else has made these transcriptions for us.

For each of these problems, write EITHER an XQuery document OR an IPython cell that answers it and paste this into your `final_exam` document, numbered accordingly.

  * A guide to XQuery syntax can be found [here](http://edutechwiki.unige.ch/en/XQuery_tutorial_-_basics).
  * The Python lxml.etree library can be found [here](http://lxml.de/tutorial.html).

*Instructions*

1. **EITHER** Create a new XQuery document and set up a transformation scenario for it, either with or without eXist. **OR** Write an IPython cell that parses each XML document in the directory into an ElementTree object.

2. Start to investigate what you have - write the logic that lists out the titles of all the documents. Don't forget to deal with the namespace of the TEI document!

4. Look at the teiHeader of one of the documents - you can see that there is a list of contributors. 
  * First list out the contributors - there are a lot of repeats! 
  * Now remove the duplicates. HINT: In Python you probably want to use a `set`; in XQuery you'll want to use `distinct-values()`. 

5. Now let's make a simple XML document that contains the title of each document - which represents a page - and a count of the number of lines on the page. It should look something like this:

		<doc>
		   <page>
			  <title>Transcription of folios 0000-100r of the Archimedes Palimpsest. (= Archimedes folio Arch53v,
							Sphere and Cylinder)</title>
			  <lines>31</lines>
		   </page>
		   <page>
			  <title>Transcription of folios 0000-100v of the Archimedes Palimpsest. (= Archimedes folio Arch53r,
							Sphere and Cylinder)</title>
			  <lines>33</lines>
		   </page>
		   <!-- carry on for the rest of the pages! -->
		</doc>
   
3. Pick one of the files - it doesn't matter which one - and extract all of its Greek text. It's okay if the text isn't formatted very nicely.

4. Look more closely at the file - you will see that the text is represented with a fairly dense combination of elements such as:
	* `w` (word), 
	* `supplied` (illegible but guessed at by the editor), 
	* `unclear` (semi-legible and the editor's best guess), 
	* `pc` (punctuation character), 
	* `gap` (missing or illegible and the editor has no idea)
 
   and so on. All of this is inside an `ab` (anonymous block) element. 
   
   Extract all the child elements of that anonymous block to see what they are.
 
7. Choose the elements that look like they contain words (hint: `lb` isn't going to be one of them) and write some logic to select only those elements. Extract all the text from each element in turn and return it like this in XQuery:

		return string-join($text, ' ')
		
   or like this in IPython:
   
   		' '.join(text)

   so that the words are space-separated.
   
8. Now put that together with your answer to #5. Make a document that looks like this:

		<doc xmlns="http://www.tei-c.org/ns/1.0">
		   <page>
			  <title>Transcription of folios 0000-100r of the Archimedes Palimpsest. (= Archimedes folio Arch53v,
							Sphere and Cylinder)</title>
			  <lines>31</lines>
			  <words>κῶνος κώνωι κώνου κώ νου ὕψος ῥόμ βωι Β ἐπι φανείας τμηθῆι κο ρυφὴν ἑ τέρωι ῥόμ βου ἀφαι ρεθῆ τῶι περιλείμματι τῆι ἐπιφανείαι μεταξὺ ἐπι πέδων ὕψος ἴσον </words>
		   </page>
		   <page>
			  <title>Transcription of folios 0000-100v of the Archimedes Palimpsest. (= Archimedes folio Arch53r,
							Sphere and Cylinder)</title>
			  <lines>33</lines>
			  <words>ὕψος αὐτοῦ τὸ ΝΟ ἐπεὶ οὖν ἡ ΝΟ κῶ νον κῶνον κῶνον ἐπιφά νεια ἰδίαν βάσις Μ Ξ ἐπι φάνεια κῶ νος γενόμε νος παραλλή λων </words>
		   </page>
   		   <!-- carry on for the rest of the pages! -->
		</doc>


Part 4. Graph databases
-----------------------

For this section you will turn the SQL databases you made as homework into graph databases. You will need a running Neo4J instance, and you will be trying out some Cypher commands. This is a more free-form section than the previous two - as long as you have a graph at the end that represents the scenario you are trying to model, then you will get credit.

*Instructions*

1. Pick TWO scenarios from [Homework 2](https://github.com/DHBern/DD2016/blob/master/homework/w03-7-March/Homework%202.md), but DO NOT choose the library one! Record in your `final_exam` document which scenarios you picked.

2. Write down ten concrete examples of the scenario described (e.g., for the library problem, a concrete scenario would be "John Brown has borrowed the book *The Grapes of Wrath*, and it is due back on 24 June." Ideally there will be some overlap between the examples, e.g. the same person borrowing multiple books. Record these examples in your `final_exam` document.

3. From the concrete examples in #2, decide what your entities (nodes) are, what their labels should be, and what properties they might have (e.g. John Brown, a person, with an address and a library membership that expires at the end of 2017). Write down the list of entities in Cypher pattern syntax, for example:

	 	(john:Patron {name: 'John Brown', address: '123 Main Street', membership_expires: '2017-12-31'})
	 	
4. From the concrete examples in #2, decide what your relationships (edges) are, what their types should be, and what properties they might have (e.g. John BORROWED the book, with a due date of 24 June.) Write down the relationships in Cypher pattern syntax, for example:

		(john)-[:BORROWED {due:'2015-06-24'}]->(thebook)
		
5. Now take all your entities and all your relationships and create them in Neo4J. You can use the CREATE command for this, and if you have given your entities unique names, then you can simply join together all of your patterns like this, listing the entities BEFORE the relationships:

		CREATE 
			(john:Patron {name: 'John Brown', address: '123 Main Street', membership_expires: 20171231}),
			(thebook:Book {title: 'The Grapes of Wrath', callno: '123ABC', published: 19390414}), 
			(john)-[:BORROWED {due: 20160625}]->(thebook),
			AND SO ON WITH EVERYTHING ELSE
			
6. Now write a Cypher MATCH statement to answer one of the following sets of questions, depending on which scenarios you have chosen:

	Problem 2. 
	  - What were the student scores on the last test that was given?
	  - How many students dropped the class before the end?
	
	Problem 3. 
	  - What pieces of music were played at performances that were reviewed in a newspaper?
	  - What pairs of pieces were played at the same performance?
	
	Problem 4. 
	  - What journal articles were NOT accepted for publication?
	  - Which reviewers reject journal articles most often?
	
	Problem 5. 
	  - What characters (if any) appear in more than one play?
	  - What genre of plays has the highest number of acts?


You're finished! Enjoy the summer.
----------------------------------
