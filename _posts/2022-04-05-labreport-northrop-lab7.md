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

*Collection plan: How I Am Building This* The initial construction of this dataset draws from two currently published datasets, [HathiTrust[(https://view.data.post45.org/index) Fiction by Ted Underwood published on post45.com and [20th-Century American Bestsellers]( http://bestsellers.lib.virginia.edu/decade/1970) initiated by John Unsworth and hosted by the University of Virginia Library website, and from a personally compiled, unpublished list of 1970s publications. The initial construction phase will not involve any collection beyond data currently contained in these three sources. To build the dataset according to the criteria outlined above, I will merge records from the three lists (fractions of the HathiTrust and 20th-Century Bestsellers list and the full content of my personal list) so that the data from disparate sources is readable as a unified set. Rather than thinking of these actions as “cleaning” for standardization, I am thinking of merging for legibility while still leaving a visible trail of how the data originally looked in the place from where I collected it. 
 
<img class="image" src="tab_screenshot.jpg"/>

![](path-to-image)

This “trail” will take the form of seven tabs. The final dataset will appear in the MERGED tab, while the other six tabs will show the construction process: the “raw” or unmodified data copied from the three source datasets and each modified component set prior to merging into the final 1970s Bibliography dataset. 

*Boundaries/scope:* In the merging process, some records from HathiTrust and 20th-Century Bestsellers will be deleted. For example, sets include “false positives” of works published previously and republished in the 70s and duplicate records. These duplicates and reprints will remain visible in the breadcrumb tabs.
### **Dataset Documentation/Codebook: Metadata Fields**
 
<img class="image" src="metadata_fields.jpg"/>

![](src: /metadata_fields.jpg)

The above image shows the metadata fields that will appear in the final, merged dataset in black text (row 1). The purple text shows the column headers (row 3) and a record entry (row 4) from the existing HathiTrust dataset. I have not modified the purple text as it appears; I’ve only deleted columns from the original HathiTrust dataset. The order and content of all three component datasets inform the metadata fields in the new 1970s Bibliography dataset. The HathiTrust dataset has by far the most records of books published in the 1970s (11,000+), and so I have used the order of metadata fields from that dataset as the base for the metadata fields in the new 1970s Bibliography. That way, the process of pre-merge data reformatting involves only the deletion of columns and moving the “Title” column from position M (in the above view) to position A. From there I will use Regular Expressions to break up the information in the “imprint” field to populate the “Publisher,” “Publication Year,” and “Publication Place” columns. 

Component data from the 20th Century Bestsellers database (100 records) and from my personal list (~300 records) will require more manual formatting modification prior to merging, but this is manageable given the lower number of records.

*Codebook draft:*

Title: Book title 
Author: Book author (omitted in the case of an edited collection. See “Editors and Illustrators” field)
Publisher: Book publishing house or press (information currently only available for records in the HathiTrust dataset. Would have to manually look up publisher for titles in 20th-Century and personal datasets.)
Publication Year: Year of publication (for books first published in English in the US, this is the date of first printing. For books first published in English internationally or first translated into English, this is the year of first US publication. Information currently only available for records in the HathiTrust dataset. Would have to manually find for titles in 20th-Century and personal datasets.)
Publication Place: City and country where publisher is located (information currently only available for records in the HathiTrust dataset. Would have to manually find for titles in 20th-Century and personal datasets.)
Editors and Illustrators: Book editor and/or illustrator where applicable (information currently only available for records in the HathiTrust dataset. Would have to manually find for titles in 20th-Century and personal datasets.)
Genre 1: Information currently only available for records in the HathiTrust dataset. Would have to manually assign for titles in 20th-Century and personal datasets. “Genre 1” is broader category than “Genre 2.” Ie “Genre 1” might indicate “Fiction” or “Nonfiction’ and Genre 2 “Juvenile” or “Textbook.”
Genre 2: Narrower category than Genre 1. There is no preset menu of Genre 1 and 2 options. The goal is that they are descriptive rather than standardized (ie they provide further qualitative information when reading a record but are not a standardized filtering field meant to capture all titles in a give genre. This is because I view genre as a fluid interpretive category rather than a standardized field and would like the dataset design to reflect this belief).
Subjects: Information currently only available for some records in the HathiTrust dataset. Includes specific data that could inform completion of Genre 1 and 2 fields, such as “prehistoric peoples,” which likely indicates a work of nonfiction. For biographies and bibliographies, “Subjects” field includes the name of the person. 
Geographics: Information currently only available for some records in the HathiTrust dataset. Indicates the places covered in a given title, ie “Blasket Islands (Ireland).” “Subjects” and “Geographics” fields would likely be left blank in the cases where they do not already have entries. I have elected to include them in the final 1970s Bibliography dataset because they provide qualitative, descriptive information about a record. The fact that many records will have multiple empty fields is part of my thinking about merging data for legibility but not standardizing and cleaning it. This includes not feeling obligated to fill every metadata field for every record.
Volume: Volume number for multi-volume works.
Source: options are HathiTrust Post45 dataset, 20th-Century Bestsellers, or Northrop personal list. In the future event that other component datasets are merged or another researcher manually adds records, there would be additional options.
(20CB Entry) Possibly include this as a yes/no field to indicate whether the 20th-Century Bestsellers database has a full entry for the title. That information would already be visible in the “breadcrumb” 20th-Century Bestsellers unformatted data tab, so I’m not sure if there is a need to also include it in the merged dataset.

### **Audiences:**
Students/student researchers
Academic researchers (scholars of literature, historians, sociologists)
Librarians
Avid readers

### **Questions dataset could help these audiences answer:**
(Question I might answer in the process: are there duplicates between the HathiTrust and 20th C Bestsellers datasets? Ie were the most purchased (and assumingly the most read) books also those digitized by scholarly libraries and ultimately complied in HathiTrust?)
Reading the dataset and going back to HathiTrust to read book (if it’s not protected by copyright laws…) or going looking for a hard copy at a library.

### **Existing related scholarly datasets:**
[Post45 HathiTrust Fiction] https://view.data.post45.org/index
[20th Century American Bestsellers]( http://bestsellers.lib.virginia.edu/decade/1970)

How it is different from these existing datasets
How your dataset offers a unique contribution (~2-3 paragraphs).
