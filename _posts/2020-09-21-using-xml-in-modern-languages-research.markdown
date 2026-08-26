---
layout: post
title:  "Mark my words: using XML in Modern Languages research"
date:   2020-09-21 00:00:00 +0000
categories: 
---
> *This post was originally published on the now-defunct Modern Languages and Cultures blog at the University of Exeter.*

The critical edition has been a central part of scholarship in the humanities for centuries. The primary output of an editing project remains the printed book, and staff in Modern Languages and Cultures at Exeter have been at the forefront of ensuring that primary material receives appropriate critical treatment and is made available to a wider audience: Hugh Roberts has recently collaborated on an edition of the Renaissance  compilation, *Les Muses incognues*, while Jonathan Bradbury has recently edited the 17th-century Spanish *Filósofo del aldea*. This vital work is increasingly being supplemented by new technologies, which allow the text to be made available in a digital-first or digital-only format. Following several early success stories, among them the [*Electronic Beowulf*](https://ebeowulf.uky.edu) project in 1993, increasing numbers of new editions have benefited from the greater interactivity, availability, and flexibility that ‘going digital’ can offer.

Here in Modern Languages and Cultures, we’re currently engaged in our own digital editing project, working to produce a new edition of an intriguing 13th-century rhymed French vocabulary known as the *Tretiz*. The most recent edition of the *Tretiz* is available online; however, its fairly inflexible PDF format means that it's more accurate to describe it as a digitised edition, rather than as a digital one. In producing our own edition of the *Tretiz*, we want to give users the ability to compare two manuscripts side-by-side and make complex queries, which means that our edition will have to be built from the ground up as a digital-only (or, at least, digital-first) resource. In order to do that, we need to be able to make the text machine-readable: that is, make it possible for a computer to recognise elements of the text (such as topic divisions, glosses, and abbreviations) in the same way that humans can when we read a manuscript or print edition. This is where XML comes in.

As we edit the *Tretiz*, we're writing a form of code known as **XML**: e**X**tensible **M**arkup **L**anguage. Some readers may feel XML looks quite a lot like HTML, the language that most webpages are written in; this is because both languages (XML and HTML) use a system of 'tags'. Where XML differs, though, is that its tags don't indicate how the document should look on a webpage, like HTML does. Instead of telling the computer to display text as 'italic' or 'bold', XML instead tells the computer what the material between tags actually is. By way of an example, let's look at a line from one manuscript of the *Tretiz*: New Haven, Beinecke Library, MS Osborn a56. (This is line 5 of the text, and found on folio 1v, for those of you taking notes. The entire manuscript can be viewed online on the Beinecke Library's [website](https://brbl-dl.library.yale.edu/vufind/Record/4183847).)

Exactly how this would look in a print edition would depend on a whole set of transcription norms, but no-one would be too surprised to see something like this: *L'enfaunt comence chatouner* ('The child begins to crawl'). Now let's take a look at that same line in our XML file:

![IMAGE](/assets/images/blogposts/2020-09-21-using-xml-in-modern-languages-research/1-base.png)

You’d be forgiven for thinking that this looks as much like gibberish as a paragraph of text in French might to a non-French-speaker, and to an extent, you’d be right. XML may not be a ‘natural’ language in the same way as French or German, but like any language, it has its own grammar and rules, and these need to be followed in order to make the text comprehensible to its audience. The audience here, of course, is not human, but rather a computer; nevertheless, the need for grammatical accuracy – or, rather, ‘validity’ and ‘well-formedness’ – remains.

So, what does each bit of this language tell the computer? Let’s indulge in a spot of XML grammar …

![IMAGE](/assets/images/blogposts/2020-09-21-using-xml-in-modern-languages-research/2-line.png)

**Line numbers.** The first and last parts of each line do what it says on the tin: namely, telling the computer that everything within them is a line. Just as natural languages have parts of speech, XML is built around ‘tags’, and everything is enclosed within tags – here, the ```<l>``` and ```</l>``` tags enclose a single line of text. The ```n ="5"``` attribute, meanwhile, simply indicates that this is line 5 in our text.

![IMAGE](/assets/images/blogposts/2020-09-21-using-xml-in-modern-languages-research/3-choice.png)

**Choices galore!** Here we have what's known as a 'choice' tag, one of the major benefits of a digital edition. It allows us to do something that print editions can't do: specifically, encode two different versions of a text, which the reader will be able to switch between in the digital edition itself. While modern French punctuation requires the apostrophe to indicate elision in the noun phrase *L’enfant* (*le + enfant*), this wasn’t the case in medieval French script, and so the manuscript simply has Lenfaunt. The ```<choice>``` tag (within which we have further tags ```<orig>``` for ‘original’ and ```<reg>``` for ‘regularised’) saves us having to choose between fidelity to the manuscript and ease of reading: instead, we simply offer both, and let the reader choose what they want to see.

![IMAGE](/assets/images/blogposts/2020-09-21-using-xml-in-modern-languages-research/4-comence.png)

**Abbreviations.** This is perhaps the simplest part of the entire line, as the only tag is ‘abbreviation marker’ (```<am>```). This tag reflects the common practice in manuscripts of using a suite of abbreviations, including this one, known as the macron. In the ‘diplomatic’ version of our edition, the ‘n’ will be in italics; in the modernised version, it will simply appear normally. 

![IMAGE](/assets/images/blogposts/2020-09-21-using-xml-in-modern-languages-research/5-chatouner.png)

**Text and gloss (1).** One of the features that makes the *Tretiz* so exciting to edit is its frequent glossing of terms into Middle English. In our edition, we’re keen to highlight these glosses, so we’ve gone to the trouble of marking up any text that’s the subject of a gloss with a ```<term>``` tag, as well as giving it a unique XML-id. Here, it’s ```Y``` (the siglum or identifying letter for the manuscript), ```chatouner``` (the word), and ```001``` (its numbered occurrence in the text).

![IMAGE](/assets/images/blogposts/2020-09-21-using-xml-in-modern-languages-research/6-gloss.png)

**Text and gloss (2).** The gloss to *chatouner*, 'for to creope' (to crawl), is the longest element in the line, but for good reason. We’re encoding plenty of information, which users of the digital edition will be able to interrogate: the language (Middle English), the place (at the end of the line, rather than above the French), and the precise term to which it refers.

We hope that this quick introduction to XML has given you a sense of some of the connections between modern languages and digital ones. If you’re interested in finding out more about the project, you can find us on Twitter at @medievalfrench, or visit our [website](tretiz.exeter.ac.uk). We hope to return to the Modern Languages blog before the end of the project, when we’ll update our readers on the trials and tribulations of all things encoding.