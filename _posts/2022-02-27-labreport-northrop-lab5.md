---
title: Lab 5 Notebook Entry
tags: Lab-Notebook-Entry
article_header:
  type: cover
  image:
    src: /vert.JPEG
---

## **Completing Lab 5: Python in Jupyter Notebooks**

### Process Questions

Question 1
*What do you notice about how this function has split the string "Okay, okay, ladies, now let's get in formation, cause I slay"? What has it done that isn't quite right, and why has it done this? Write down your response in your notes document.*

division of "let's" into 'let' and 's'

*What does the regular expression "\W+" mean in Python? What does "\W" mean? What does "+" do? What do these symbols mean when used together in a regular expression?*

From re documentation: "\W Matches any character which is not a word character. This is the opposite of \w." From what I understood of the re documentation, backslash uppercase W matches characters that are not defined as part of words, including punctuation marks and spaces. Backslash lowercase w, on the contrary, matches anything that is a word in any language, meaning any string of letters not interrupted by numbers, punctuation, or spaces.
From re documentation: "+ Causes the resulting RE to match 1 or more repetitions of the preceding RE. ab+ will match ‘a’ followed by any non-zero number of ‘b’s; it will not match just ‘a’." I take the addition of a nonzero number of repetitions (one or more) after the \W to mean that the function will look for the pattern of word, nonword as many times as it appears in the string of text to be able to split the string into individual words.

'''
def split_into_words(any_chunk_of_text):
# split the string into individual terms and make them all lowercase
words = re.split("\W+", any_chunk_of_text.lower())
return words 
'''
