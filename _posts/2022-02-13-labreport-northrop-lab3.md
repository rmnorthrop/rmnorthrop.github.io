---
title: Lab 3 Notebook Entry
tags: Lab-Notebook-Entry
article_header:
  type: cover
  image:
    src: /pumpkinRegEx.jpg
---

## **Completing Lab 3: Regular Expressions Housework**

### "Cleaning" The Sample Dataset

Following the concept of identifying extraneous characters by replacing them with nothing, after removing all quotation marks I decided to remove all brackets and parentheses.

1. RegEx: “<br/>
Sub: null<br/>
Action: remove quotation marks<br/>

2. RegEx: \[<br/>
Sub: null<br/>
Action: remove left brackets (using “escape” syntax so that RegEx doesn’t think the bracket symbol is opening an expression)<br/>

3. RegEx: \]<br/>
Sub: null<br/>
Action: remove right brackets (using “escape” syntax so that RegEx doesn’t think the bracket symbol is closing an expression)<br/>

4. RegEx: \(<br/>
Sub: null<br/>
Action: remove right parentheses (using “escape” syntax so that RegEx doesn’t think the bracket symbol is closing an expression)<br/>

5. RegEx: \)<br/>
Sub: null<br/>
Action: remove left parentheses (using “escape” syntax so that RegEx doesn’t think the bracket symbol is closing an expression)<br/>

For both of these characters, brackets and parentheses, I kept thinking there must be a way to capture both the left and right characters at the same time, but using the asterisk to indicate “anything that’s in between the brackets/parentheses” didn’t work (RegEx then couldn’t match either the left or right facing characters). Adding a space in the expression also didn’t work -- \[ \] because none of the data has a space character following a bracket or parenthese. I also didn’t want to remove the data between the brackets and parentheses, so I just did it one character at time.

6. RegEx: \?<br/>
Sub: null<br/>
Action: remove question marks<br/>

Now that the data looked like this, I wanted to deal with the commas and semicolons to get commas in a position where they will separate the title and location columns to be understood in a .csv format.

```
The Epoch Times, New York ed.; New York NY<br/>
La Voz Bilingüe; Denver, Colo.<br/>
Jewish Advocate; Boston<br/>
Washington Informer; Washington, D.C.<br/>
News from Indian Country; Hayward, WI.<br/>
Afro - American, 5 Star edition; Baltimore, Md.<br/>
Diverse Issues in Higher Education; Fairfax Virginia<br/>
The Gay &amp; Lesbian Review Worldwide; Boston, MA<br/>
The Hispanic Outlook in Higher Education; Paramus N.J<br/>
```

First, I got rid of the semicolon and redundant ampersand characters.

7. RegEx: amp;<br/>
Sub: null<br/>
Action: remove amp; to leave just the ampersand & character<br/>

Given the small size of this dataset, I was able to see that currently the semicolons are in the column separation position (between publication title and location) where we ultimately want commas to be. The commas in the dataset are either between parts of the publication title or between city and state. Those commas can stay in the final .csv, but I wanted to make sure that they would be read as comma characters, not as commands to separate data into new columns. My idea was to replace the existing comma , with an escaped comma \, to indicate "this is a comma character, not an instruction."

8. RegEx: , OR \, I got the same result with both entries<br/>
Sub: \\, because I wanted to add the backslash character and entering just \, was still read as only a comma<br/>
Action: all commas are now replaced preceded by a backslash to appear as escaped commas \,<br/>

Now I can replace all the semicolons with commas and those new commas will appear as commas alone , to be read as column separation instructions when the dataset is migrated to Excel, Google Sheets, or another program that reads .csv files.

9. RegEx: ;<br/>
Sub: ,<br/>
Action: Semicolons are replaced with commas. In the dataset there are now escaped commas that should remain within a column and commas that indicate column separation.<br/>

The Epoch Times\, New York ed., New York NY<br/>
La Voz Bilingüe, Denver\, Colo.<br/>
Jewish Advocate, Boston<br/>
Washington Informer, Washington\, D.C.<br/>
News from Indian Country, Hayward\, WI.<br/>
Afro - American\, 5 Star edition, Baltimore\, Md.<br/>
Diverse Issues in Higher Education, Fairfax Virginia<br/>
The Gay & Lesbian Review Worldwide, Boston\, MA<br/>
The Hispanic Outlook in Higher Education, Paramus N.J<br/>

## Response

I often find that readings from multiple classes overlap in serendipitous ways, as though the gods of graduate shool have a sense of humor, or at least an impeccable sense of timing. For Dr. Moore's theory class I'm reading a monograph about Black LGBT Ballroom culture in Detroit. The author, Marlon Bailey, describes the kind of "kinship labor" that members of a Ballroom "House," or family unit, do to care for each other as "housework" (itself a play on the term "werk," an exclamation of encouragement and praise given during Ballroom performances). I find it productive to think of this notion of alternative family kinship labor together with *Data Feminism*'s discussion of the term "janitor" used to describe those who work work to "clean" data and Rawson and Munoz's critique of the "oddly domestic image" the term "data cleaning" evokes. 

Picturing the "corn straw broom" evoked by Rawson and Munoz together with the behind-the-scenes labor involved in producing a Ball make working with RegEx feel much more approachable. I think the kind of "cleaning" we were doing to organize the publication and location data into a .csv readable format is a good example of the sort of cleaning that does not "inscribe a normative order by wiping away what is different," a pitfall of Rawson and Munoz caution against, but instead make what is there easier to understand by taking away characters that could make it confusing. We did not standardize or "order" the data in the location column, for example, into a uniform format of city and state or state by two letter abbreviation. Instead, we left the content as messy as it came and swept the dust bunnies of brackets, parentheses, question marks, quotatio marks and amp; away to make it easier to read the content of the dataset. In one way we did suppose that the publication title and the publication location each had a "rightful place" in a separate column, but we did not attempt to normalize the data that we moved into those two fields. I think this exercise was a good example of the insight a human brings to the "cleaning" process; a quick read of the data allows us to indentify what are essentially extraneous characters compared to what is the unique fingerprint of a given publication. If we have in mind the goal of tidying up to remove the dust around the furniture, then we can identify our task as eliminating punctuation marks rather than preoccupying ourselves with sawing legs off chairs and repainting to make every entry in the location column look the same.

While there are perhaps problematic gendered associations with this analogy, I actually do like the idea of thinking of maintaining a dataset as akin to maintaining a domestic space. The goal is to make it a space that is comfortable to move around in. Often, this requires more "kinship labor" of collaboration and teamwork--or Housework--than it does imposition of obsessive order. The Data-Sitters Club is a good example of an alternative (academic) family that cares for their corpus together. They collectively engage in a kind of data maintenance housework that is based around a care for and about the content of the corpus they are nurturing. The housework of caring for a textual corpus is different than managing a dataset made up of individual records that can be expressed in .csv format and tidied by Regular Expressions, but I think the framing can be similar. Caring for a dataset or corpus is different than wrangling it into standardization. The "regular" in Regular Expressions refers to patterns. There are often patterns within the mess. To identify patterns does not necessarily require eliminating the mess. It might, however, require collaborative care work.

The resulting dataset generated after multiple rounds of "cleaning" in the form of eliminating punctation characters that did not add meaning still showed the diversity between the entries but is, I think, easier to read because there is some sort of pattern in the remaining punctuation. All language follows patterns and so I do think data, if it is to be machine readable *or* human readable, needs to follow some sort of pattern. While there is something poetic about OCR generating a pattern of <BZZT!>, as though there were an agitated honeybee in the machine, these computer-injected abberations disrupt the patterns that make languge readable. The same way that housework makes a home, or an alternative family unit, a livable space, data cleaning should make data more readable to both code and people. The more that people are ok with the diversity expressed in messiness the more we can teach our code to read it, too.