---
title: Dataset Abstract
tags: Lab-Notebook-Entry
article_header:
  type: cover
  image:
    src: /abstractart.jpeg
---

### **Dataset Title: 1970s Bibliography of American Books**

### **Dataset Description:**

*Kind of data:* The 1970s Bibliography dataset will be a csv file (expressed initially as a Google sheet) that contains records of books published from 1970-1979 in the United States. Records will contain book titles, author, editor, and editor names, publication year, publisher name, publisher location, book genre, and indication of subject matter.

*Principles of inclusion/exclusion:* The purpose of this dataset is to document printed works that entered circulation in the United States for the first time between 1970-1979. For that reason, the list includes works in translation that were first published in the US during the 1970s and works that were originally published prior to the 1970s in the UK, Canada, the Caribbean, and Australia and were first published and distributed in the US during the 1970s. Republications (second, third, and subsequent printings) of works previously published in English in the US are not included. Books printed and distributed in the US are included even if the author of the work identifies as being “from” or representing another country.

The records in the dataset include works in fiction and nonfiction genres but do not include specialized training manuals, government reports, or other books that were not widely available to the general public. Records do include secondary and post-secondary level textbooks. Records include young adult novels but exclude children’s picture books; anything that might be called a “chapter book” and was printed in black and white rather than full color is included in the dataset. Records include books published by small, independent presses as well as mass market publishing houses but do not include journals, magazines, zines, pamphlets and serial or ephemeral publications. Plays and screenplays that were published for a general audience are included; film and stage scripts that were published exclusively for actors and directors are not included In the case of multi-volume works, each volume is treated as a separate record and indicates volume number.
These criteria have been determined according to the guiding principle of books published in English in the United States for the first time between 1970-1979 that a non-specialist layperson could have accessed commercially or through a public or university lending library. The intent of this principle and its attendant criteria is to document works that entered the shared space of public consciousness during the same decade and potentially could have been read in conversation with one another. In the future, this dataset could be expanded to include works published in the United States in languages other than English during the 1970s; of particular interest would be Chicano literature published in Spanish.

*Collection plan: How I Am Building This* The initial construction of this dataset draws from two currently published datasets, [HathiTrust](https://view.data.post45.org/index) Fiction by Ted Underwood published on post45.com and [20th-Century American Bestsellers]( http://bestsellers.lib.virginia.edu/decade/1970) initiated by John Unsworth and hosted by the University of Virginia Library website, and from a personally compiled, unpublished list of 1970s publications. The initial construction phase will not involve any collection beyond data currently contained in these three sources. To build the dataset according to the criteria outlined above, I will merge records from the three lists (fractions of the HathiTrust and 20th-Century Bestsellers list and the full content of my personal list) so that the data from disparate sources is readable as a unified set. Rather than thinking of these actions as “cleaning” for standardization, I am thinking of merging for legibility while still leaving a visible trail of how the data originally looked in the place from where I collected it. 
 
<img class="image image--md" src="tabscreenshot.jpeg"/>

![](https://raw.githubusercontent.com/rmnorthrop/rmnorthrop.github.io/master/tabscreenshot.jpeg)

This “trail” will take the form of seven tabs. The final dataset will appear in the MERGED tab, while the other six tabs will show the construction process: the “raw” or unmodified data copied from the three source datasets and each modified component set prior to merging into the final 1970s Bibliography dataset. 

*Boundaries/scope:* In the merging process, some records from HathiTrust and 20th-Century Bestsellers will be deleted (tbd exactly how). For example, sets include “false positives” of works published previously and republished in the 70s and duplicate records. These duplicates and reprints will remain visible in the breadcrumb tabs.
### **Dataset Documentation/Codebook: Metadata Fields**
 
<img class="image image--md" src="metadatafields.jpeg"/>

The above image shows the metadata fields that will appear in the final, merged dataset in black text (row 1). The purple text shows the column headers (row 3) and a record entry (row 4) from the existing HathiTrust dataset. I have not modified the purple text as it appears; I’ve only deleted columns from the original HathiTrust dataset. The order and content of all three component datasets inform the metadata fields in the new 1970s Bibliography dataset. The HathiTrust dataset has by far the most records of books published in the 1970s (11,000+), and so I have used the order of metadata fields from that dataset as the base for the metadata fields in the new 1970s Bibliography. That way, the process of pre-merge data reformatting involves only the deletion of columns and moving the “Title” column from position M (in the above view) to position A. From there I will use Regular Expressions to break up the information in the “imprint” field to populate the “Publisher,” “Publication Year,” and “Publication Place” columns. 

Component data from the 20th Century Bestsellers database (100 records) and from my personal list (~300 records) will require more manual formatting modification prior to merging, but this is manageable given the lower number of records.

*Codebook draft:*

**Title:** Book title 

**Author:** Book author (omitted in the case of an edited collection. See “Editors and Illustrators” field)

**Publisher:** Book publishing house or press (information currently only available for records in the HathiTrust dataset. Would have to manually look up publisher for titles in 20th-Century and personal datasets.)

**Publication Year:** Year of publication (for books first published in English in the US, this is the date of first printing. For books first published in English internationally or first translated into English, this is the year of first US publication. Information currently only available for records in the HathiTrust dataset. Would have to manually find for titles in 20th-Century and personal datasets.)

**Publication Place:** City and country where publisher is located (information currently only available for records in the HathiTrust dataset. Would have to manually find for titles in 20th-Century and personal datasets.)

**Editors and Illustrators:** Book editor and/or illustrator where applicable (information currently only available for records in the HathiTrust dataset. Would have to manually find for titles in 20th-Century and personal datasets.)

**Genre 1:** Information currently only available for records in the HathiTrust dataset. Would have to manually assign for titles in 20th-Century and personal datasets. “Genre 1” is broader category than “Genre 2.” Ie “Genre 1” might indicate “Fiction” or “Nonfiction’ and Genre 2 “Juvenile” or “Textbook.”

**Genre 2:** Narrower category than Genre 1. There is no preset menu of Genre 1 and 2 options. The goal is that they are descriptive rather than standardized (ie they provide further qualitative information when reading a record but are not a standardized filtering field meant to capture all titles in a give genre. This is because I view genre as a fluid interpretive category rather than a standardized field and would like the dataset design to reflect this belief).

**Subjects:** Information currently only available for some records in the HathiTrust dataset. Includes specific data that could inform completion of Genre 1 and 2 fields, such as “prehistoric peoples,” which likely indicates a work of nonfiction. For biographies and bibliographies, “Subjects” field includes the name of the person. 

**Geographics:** Information currently only available for some records in the HathiTrust dataset. Indicates the places covered in a given title, ie “Blasket Islands (Ireland).” “Subjects” and “Geographics” fields would likely be left blank in the cases where they do not already have entries. I have elected to include them in the final 1970s Bibliography dataset because they provide qualitative, descriptive information about a record. The fact that many records will have multiple empty fields is part of my thinking about merging data for legibility but not standardizing and cleaning it. This includes not feeling obligated to fill every metadata field for every record.

**Volume:** Volume number for multi-volume works.

**Bestseller Rank:** Information available for the top ten bestselling works of fiction, as collected by 20th Century Bestsellers list from New York Times bestsellers list. (missing from screenshot)

**Source:** Options are HathiTrust Post45 dataset, 20th-Century Bestsellers, or Northrop personal list. In the future event that other component datasets are merged or another researcher manually adds records, there would be additional options for this field. In the case that a title occurs in more than one component dataset, multiple sources will be listed in this field.

(20CB Entry) Possibly include this as a yes/no field to indicate whether the 20th-Century Bestsellers database has a full entry for the title. That information would already be visible in the “breadcrumb” 20th-Century Bestsellers unformatted data tab, so I’m not sure if there is a need to also include it in the merged dataset.

(Translation) I might add a field to reflect that a work has been translated, and if so from which language and note the original year of publication. However, since the majority of works are not translated, I might be able to fit that information, where available, into the “Genre 2” and/or “Subjects” fields.

### **Audiences:**

Potential audiences for and users of the 1970s Bibliography dataset include secondary and post-secondary students, student researchers, academic researchers (including scholars of literature, historians, and sociologists), librarians, and avid readers who might find the records interesting. Book historians might or sociologists want more granular data about authors (such as gender, race/ethnicity, or age), reprints beyond the 70s, or genre and subject matter. I like the idea of reading a dataset rather than using it to run statistical analysis, so part of my thinking in leaving “holes” or empty fields in some records is that the entries will not be comparable apples to apples and therefore lend themselves more to reading than to computational analysis. 
All audiences could filter the data to see works by the same author, by the same publisher, and run a keyword search to find titles that contain words of interest. All audiences could also see a title in the database and then find that title to read. The dataset is not meant to be an endpoint but rather a starting point for further reading, investigation, and inquiry.
The final 1970s Bibliography will be organized primarily by year and then by author last name within each year.

### **Questions dataset could help these audiences answer:**

First, one question I might answer in the assembly process: are there duplicates between the HathiTrust and 20th-Century Bestsellers datasets? Were the most purchased (and assumingly the most read) books also those digitized by scholarly libraries and ultimately complied in HathiTrust?

Further, what kinds of books were published in the 1970s? What were common or recurring terms in book titles?
Which authors were prolific publishers in the 1970s?
Which works from the 1970s are held by university libraries (and ultimately by HathiTrust)?
Which publishers were prolific publishers in the 1970s? Are those publishers still around? Is it possible to discern author-publisher configurations, ie are there any authors who visibly “migrate” from one publisher to another?
Within the decade, are there any trends in titles? For example, in my research I’ve found that there were lots of books written in the early 1970s about WWII, as though controversies around the Vietnam War prompted writers and readers to rethink America’s involvement in a previous war. This is just a casual observation I’ve made, but I wonder if the dataset could help me formulate a more specific research question related to fiction and nonfiction titles about war within the decade of the 1970s.

### **Existing related scholarly datasets:**

[Post45 HathiTrust Fiction](https://view.data.post45.org/index)

[20th Century American Bestsellers]( http://bestsellers.lib.virginia.edu/decade/1970)

My ideal 1970s Bibliography is different that each of its component datasets in the way it merges both the content of records and the content of metadata fields. At the individual record level, merging information from multiple sources can help complete the information visible about a single book. Because the dataset both aggregates data from different sources and reduces data from those sources to consider only a decade, the resulting 1970s bibliography serves both to expand and to hone. It provides a currently unavailable temporally specific view of existing data. 
Finally, I’m excited that my personal list of 1970s publications includes titles that appear neither in HathiTrust or on the bestsellers list. Many of these works are by Black and Indigenous women writers published by small presses. While they were neither bestsellers nor added to university library collections thus far, they are an important component of 1970s literature. Maybe librarians can find first or single printing copies with used booksellers and enter them into the collections now.

*Image: Abstract Art* Eulaia *by Ema Ri “Red ginger flowers, bangkok roses, mexican petunias, hibiscus, pink silk floss, peacock flowers, king of ixoras flowers, weeping gold shower, queen crepe myrtle, fraginani, bugambilia, blue jacaranda, yellow flame flowers, royal ponciana flowers. Dimension variable.” Part of the* A landscape longed for: the garden as disturbance *at locustprojects gallery in Miami. Piece performed by Ri and photographed by Northrop February 2, 2022.*
