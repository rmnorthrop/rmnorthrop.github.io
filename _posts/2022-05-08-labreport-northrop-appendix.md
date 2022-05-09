---
title: Appendix Dataset Construction
tags: Lab-Notebook-Entry
article_header:
  type: cover
  image:
    src: /construction.JPEG
---

## **Building the [1970s Bibliography of American Literature](https://docs.google.com/spreadsheets/d/1eVIzo053ksP9c1OU5n1UARndQ0m0luoW7D4e-IOV4Ls/edit?usp=sharing)**

### **1. [HathiTrust Post 45]( https://view.data.post45.org/index) component list**

Step 1: Copy 11,869 records with Column F “inferreddate” between 1970 and 1979 to “HathiTrust 1970s” tab in Construction sheet.

Step 2: Duplicate “HathiTrust 1970s” tab and rename duplicated tab “HathiTrust 1970s formatted.” All manipulations to HT data will be made within this “formatted” tab.

Step 3: Sort records by Column G “latestcomp” (because this field shows earlier dates, likely copyright or original publication dates).

Step 4: Delete 2,987 records with “latestcomp” years between 1700 and 1969 (because these are reprints of previously published books).

Step 5: Manually migrate data in Column X “parttitle” to be part of Column W “title.” To do this, sort sheet by Column V “volum” to display all records that are multi-volume books (the “parttitle” field contains the title of each volume and the “title” field contains the same title for all volumes). Copy volume title from “parttitle” and past at the end of “title” field. (“parttitle” field will be deleted, “volum” field with numeric volume number will be retained.) 

Step 6: Delete Columns A “id,” B “docid,” C “oldauthor,” F “inferreddate,” G “latestcomp,” H “datetype,” I “startdate,” J “enddate,” Q “locnum,” R “oclc,” S “place,” T “recorded,” X “parttitle,” Y “shorttitle,” Z “instances,” AA “juvenileprob,” AB “nonficprob.” Note that these fields are retained in the “HathiTrust 1970s” tab.

Step 7: Order and rename columns to align with desired 1970s Bibliography field order and field title (see MERGED and CODEBOOK tabs).

Step 8: Sort records by “imprintdate” to delete 10 reprints with imprint dates pre-1970 that were not captured when sorting by the “latestcomp” field. I’ve chosen to retain the xx records with “imprintdate” years of 1980 or later, reflecting reprints of books with an original publication date in the 1970s. Those require a manual check to see if a record for the first/original copy of the book exists. If it does, the reprint entry can be deleted. If not, then a new record can be created for the original 1970s printing of the book. Either leave publisher field blank or confirm publisher, since reprints are often published by a different house.

Step 9: Use Regular Expressions to separate the values in HathiTrust “imprint” field into destination “Publisher” and “Publication Place” fields. To do this, copy/duplicate the values in the “imprint” field so that “Publisher” and “Publication Place” have identical data.

Step 9a: Select “Publisher” Column. Edit > Find and Replace > Select radio box “Search using regular expressions.” In “Find” field enter: ^(.*)\|(.*)\|(.*)  In “Replace” field enter: $2  Select “Find” button and full column with have green dash-line perimeter. Select “Replace All” button. Original “imprint” field values will now return just the publisher name(s), the values in group 2 (between the two pipes).

Step 9b:  Select “Publication Place” Column. Edit > Find and Replace > Select radio box “Search using regular expressions.” In “Find” field enter: ^(.*)\|(.*)\|(.*)  In “Replace” field enter: $1  Select “Find” button and full column with have green dash-line perimeter. Select “Replace All” button. Original “imprint” field values will now return just the publisher location, the values in group 1 (the position before the first pipe).

Step 10: Migrate international publications to “HT International” tab. To do this, sort sheet by “Publication Place” field. Manually copy and paste records with a Publication Place outside of the US into “HT International” tab and then delete those records from the “HathiTrust 1970s formatted” tab. Retain records that include both a US and international place in the case of multiple field values.

NB: The HathiTrust Post45 dataset does not accurately display non-English language characters, including accent marks. Therefore, the records that include special characters display a series of other, incorrect special characters. In terms of readability, separating records with illegible elements into a different dataset makes the 1970s bibliography more readable. It also concentrates the records that would need manual attention to re-enter the correct special characters to make those records more readable.

Step 11: Add “HathiTrust Post45” to “Source” Column.

### **2. [20th-Century Bestsellers](http://bestsellers.lib.virginia.edu/decade/1970) component list**
 
Step 1: Copy and paste records from the 20th-CB site into “20th C Bestsellers 1970s” tab.

Step 2: Duplicate “20th C Bestsellers 1970s” tab and rename “20th C 1970s formatted.” All manipulations to 20th-CB data will be made within this “formatted” tab.

Step 3: Sort records by title to search for duplicates.

Steps 3a-c: For each set of duplicates, confirm that title was published in the 1970s. If not, remove both records. If title was published in the 1970s, check HathiTrust formatted list to see if book record exists there. If so, add rank and year to “rank” Column and remove from 20th C formatted list. If not, merge duplicate records by including multiple years and ranks in “rank” column. Confirm publication year and leave on list.

Step 4: NOT YET COMPLETED. Check remaining records to see if book titles are already included among HathiTrust records. Manually search each title.

Step 4a: If a record exists in the HathiTrust formatted 1970s list, add rank (and year if bestselling year is different from publication year) to “rank” Column. Delete record from 20th-CB list.

Step 4b: If a record for that book does not exist in HathiTrust, leave it on the 20th-CB list and confirm publication year. 

Step 6: Add 20thCB to "source" Column.

Step 6: Copy and paste remaining records into “Dataset” tab of 1970s Bibliography. Sort sheet by publication year to integrate records.

### **3. Northrop personal list**

Step 1: Copy and paste records into “Northrop 1970s” tab of Construction sheet.

Step 2: Duplicate “Northrop 1970s” tab and rename “Northrop 1970s formatted.” All manipulations to Northrop data will be made within this “formatted” tab.

Step 3: Remove foreign language and international publications.

Step 4: NOT YET COMPLETED. Search each record to see book title it exists in “Dataset” tab of 1970s Bibliography (containing HathiTrust and 20th-CB records). If so, remove record from list.

Step 5: Manually reenter “author” field values to read “Lastname, Firstname” and “Lastname, Firstname ; Lastname, Firstname” in the case of multiple authors or editors.

Step 6: Add "Northrop" to "source" Column.

Step 7: Copy and paste records into “Dataset” tab of 1970s Bibliography. Sort sheet by publication year to integrate records.


Photo: Old school tools. (None of which were used in the construction of this dataset but which remain helpful for other household projects.)
