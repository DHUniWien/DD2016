XML, XPath, and XQuery hints
====================

This directory contains some example files for the XML lessons that we've had.

* sentence_example.xml - a relatively simple, namespace-free XML document
* tei_example.xml - the famous sonnet of Browning, showing a minimal TEI document
* russell.xml - transcription of a few pages of a book by Bertrand Russell
* merchant_venice.xml - a Shakespeare play from the Oxford Text Archive

(The Browning and Russell texts are taken from [TEI By Example](http://teibyexample.org).)

In the `xquery_examples` folder there are examples, in increasing order of complexity, of how XQuery works.

XPath cheat sheet
-----------------

Here are some examples of XPath that we learned in class, plus a few bonus ones that you will need in order to do the homework. A fuller XPath 2.0 reference [can be found here](http://saxon.sourceforge.net/saxon7.9/expressions.html).

	/	This is the path separator. A / by itself is the whole document.
	
	/TEI - Gets the TEI element at the top of the document.
	/child::TEI - Same as /TEI.
	
	/TEI/teiHeader/fileDesc/titleStmt/title - Gets the 'title' element 
		inside the 'titleStmt' element inside the 'fileDesc' element...etc.
		
	//text - Gets all 'text' elements anywhere in the document.
	/descendant::text - Same as //text.
	
	//text() - Gets all text (i.e. stuff outside of elements) anywhere in 
		the document.
		
	//teiHeader//text() - Gets all text anywhere in the TEI header.
	
	//p[5] - Get the fifth p element in the document.
	
	/lb[@n="5"] - Gets the lb element(s) with the attribute n=5.
	
	/lb/@n - Gets the attribute n of every lb element.
	/lb/attribute::n - Same as /lb/@n.
	
	/TEI/* - Gets all elements inside TEI.
	//* - Gets all elements.
	
	//note/ancestor::p - Gets the p elements that contain note elements anywhere.
	
	//note/ancestor::* - Gets all elements that contain note elements anywhere.
	//note/ancestor::node() - Same as //note/ancestor::*
	
	//note/parent::node() - Gets the element that contains a note element as a 
		direct child, no matter what it's called.
	//note/.. - Same as //note/parent::node()
	
	//stage/following-sibling::sp - Get all sp nodes that are at the same level 
	of a stage node, but after it.
	
	//stage/preceding-sibling::sp - Get all sp nodes that are at the same level 
	of a stage node, but before it.
	
Remember that, if we are dealing with a document that has a namespace set (like all TEI documents), we might have to use a namespace prefix - instead of `//ELEMENT` we say `//tei:ELEMENT`. 
	

