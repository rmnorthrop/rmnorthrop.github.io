---
title: Lab 5 Notebook Entry
tags: Lab-Notebook-Entry
article_header:
  type: cover
  image:
    src: /vert.jpeg
---

## **Completing Lab 5: Python in Jupyter Notebooks**

### Process Questions

Question 1
*What do you notice about how this function has split the string "Okay, okay, ladies, now let's get in formation, cause I slay"? What has it done that isn't quite right, and why has it done this? Write down your response in your notes document.*

division of "let's" into 'let' and 's'

*What does the regular expression "\W+" mean in Python? What does "\W" mean? What does "+" do? What do these symbols mean when used together in a regular expression?*

From re documentation: "\W Matches any character which is not a word character. This is the opposite of \w." From what I understood of the re documentation, backslash uppercase W matches characters that are not defined as part of words, including punctuation marks and spaces. Backslash lowercase w, on the contrary, matches anything that is a word in any language, meaning any string of letters not interrupted by numbers, punctuation, or spaces.

From re documentation: "+ Causes the resulting RE to match 1 or more repetitions of the preceding RE. ab+ will match ‘a’ followed by any non-zero number of ‘b’s; it will not match just ‘a’." I take the addition of a nonzero number of repetitions (one or more) after the \W to mean that the function will look for the pattern of word, nonword as many times as it appears in the string of text to be able to split the string into individual words.

```
def split_into_words(any_chunk_of_text):
# split the string into individual terms and make them all lowercase
words = re.split("\W+", any_chunk_of_text.lower())
return words 
```

Question 2
*What happened? Did it work as you expected? If not, what happened that you didn't expect?*

The cell ran as expected; all words in my string were listed individually in lowercase in the resulting printout. I did, however, have to backspace once to eliminate a line break that was originally in the text I pasted into the string. When I pasted the text, the second line after the break was black not red, cluing me that it might not be read as part of the string. I backspaced to elminate the line break, everything turned red, and the cell ran as expected." I tried it again without eliminating the line break, with the first half of my text in quotes appearing red and the second half appearing black and the cell did not run properly. I got the following error message: "SyntaxError: EOL while scanning string literal." Lesson is that the colors are helpful clues as to whether Python is reading strings or any other part of the input the way I want it to be read.

Question 3
*Describe the output of this script. What is this dataframe showing?*

The dataframe is showing exactly what the function asked it to show: the number of vert* and virt* words per document! Overall, the dataframe shows a list of "hits," documents in the xml file that contain at least one instance of either a vert* or virt* word. The columns match what the function was written to pull from (scrape? find?) in the file with a selection of texts from the EEBO database: author name, title, date, and raw count of vert* and virt* terms. The output of the script is formatted as a table (rather than a dictionary-frequency list in brackets). I think this is made possible by the Panda package/portion of the function, but I'm not sure. I could identify the regular expressions parts of the function and the Python portions of the function, but I couldn't fully "read" the whole thing to understand what instruction each line was giving. I could see how you have to write code in a specific order--define a variable before you use it in a function, define a list/destination before you sent output to it. In that way it does feel almost algebraic in that order of operations matter and the solution to an equation is dependent on the sequence used to solve it.

Question 4
*Look at the lines from the compare_counts_specific function. These lines use regular expressions to do something to the value of the <date> field in an xml file (if the contents of the <date> field meet certain conditions, that is). What are these lines doing?* 

My hunch is that the following lines of code
```
if re.search(r'^20', date):
    date = re.sub('20', '', date)
```
are searching for any dates that begin with "20," ie years 2000 and after, and substituting that date with either " marks or a blank space. This is my guess because the RegEx Python documentation says, "Characters that are not within a range can be matched by complementing the set. If the first character of the set is '^', all the characters that are not in the set will be matched. For example, [^5] will match any character except '5.'" Somehow, these lines of code are telling the function to ignore or skip (ie not to import into the dataframe table) dates in the 2000s, such as a library stamp of when a document was scanned.

### Response

Reading Python is like reading a new language. I've always found learning to read a new language is like a puzzle--there are patterns and exceptions to the patterns. The more you identify patterns and exceptions, the more what starts as a sea of characters clicks into focus as discrete words, sentences, ideas, expressions, and eventually tone, humor, and intent. One thing that makes learning to read, and maybe eventually write a "computer language" is that they are much, much more literal than verbal languages. The languages we speak all began as spoken languages that were latter written down. Python, and all computer code, began its life as a "dead" language in the sense that it is only ever meant to be written and read, never spoken and heard. Often, it is the connection between the sound of the words we hear, turns of phrase, or common exclamations that make it possible to learn to read a new language by sort of "matching" it to its spoken version. There are those "aha!" moments of connecting a string of letters to something you have heard someone say.

This element of matching written code to spoken language is absent when working with Python. There is no possibility to "overhear" someone speaking Python and then translate that aural information into context clues for reading code. (Although I can definitely imagine that at a programming conference people do sort of end up speaking in Python, R, RegEx, C++, Java etc. when they are discussing code they have written, hacked, or troubleshot.) The literalness of computer languages is counterintuitive when compared to human spoken languages, which always have layers of multiple meaning, nuance, puns, taboos, and oddities--even in the case of languages with rigidly rule-abiding grammars. I think the literality of computer languages underpins Jo Guldi's argument in "Critical Search: A Procedure for Reading in Large Scale Textual Corpora." If we were to tell a colleague, "oh, I spent the summer at the British Library's archives reading seventeenth-century women's diaries," our colleage might imagine that somehow we looked through a lot more documents to determine which were diaries from the seventeenth century and authored by women. However, if we were to look through a large database of digitized files for the same, we could not simply say "I searched for seventeenth-century women's diaries." Guldi's argument is that we would need to explicitly state the seed and search terms we used. How are we defining the seventeenth century? Diaries? Women? While our physical presence in the archives might indicate that our knowledge of penmenship, binding and paper quality, and names might allow us to make informed scholarly decision about what is and what is not a women's diary from the seventeenth-century, a function querying a database of scanned documents cannot tell the difference between a diary and ship manifest, between a recipe book and double entry bookeeping unless we give it very explicit instructions of what to look for.

Prior to reading Guldi's paper, I'll admit that I did not know what a topic model was. I've heard the term used but I did not realize that it was so completely "machine made" in that a computer does the distant reading to determine clusters of terms in a corpus. I thought it was more of a manuel process starting with Voyant-like word clouds that indicated what the top (rawly frequent) terms in a corpus were and then manually assembling those recurring terms into clusters. (Now that I know that is not what a topic  model, it might be interesting to use Voyant's raw and relative frequency and collocation counting tools to create clusters of "top terms." Although I don't know what that would actually reveal about the corpus.) Topic modelling seems to rely heavily on the computer telling the researcher what is there, whereas keyword searching seems to rely heavily on the researcher knowing ahead of time what to query. Searching through archival documents is essentially analog reading, either all the words or skimming most of of the words. Searching through a digitized corpus is very much speaking in computer: the process is much more of an alebraic equation where all the terms (variables and constants) must be defined ahead of time and the order of operations must be observed so as to make solving the equation a repeatable process. This holds up even from internet search experience; searching "beyonce" + "formation lyrics" in google starts to look like an equation. 

On page 5 of her paper Guldi writes that "This article calls for a critically-informed strategy for negotiating **digital archives** that is aligned with an understanding of how different algorithms determine particular perspectives on textual corpora from the past." The emphasis on "digital archives" is mine because I think her article stresses the difference between the methods humanities scholars use when "searching" through analog versus digital collections of texts. In both cases we might feel like we are looking for data/information/evidence that relates to our field or research question, but the process of reading and skimming thorugh a bunch of stuff to see what we find--and using our knowledge of human spoken/written languages to do so--is fundamentally a different process from giving a computer a set of commands to query a large set of digitized data. I think it makes sense, then that the ways in which we write about information/data/evidence that we found using analog versus digital research methods can and should be very different. It might feel clunky to list search terms or define a topic model's codic architecture in a literary paper, but the same way we identify when and who translated something, I think it is productive to indicate where and how we wrote to the computer and the machine wrote (printed) back in our research process.