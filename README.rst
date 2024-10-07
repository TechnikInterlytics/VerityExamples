Readme
========

**Better Data = Better Outcomes.** 

**VerityPy and VerityDotNet** libraries combine curated human expertise with Machine Learning (ML) 
into software components to accelerate development and signficantly lower the level of effort needed 
to make data ready for high quality Data Science, Machine Learning, and predictive models.

The libraries contain expert algorithms developed from in-depth investigations, forensic tracing, and specialized remediation on 
large data systems across many fields, always with successful outcomes. Our human experts discovered where to look, 
what to look for, and what to do about problems especially deeply buried ones missed by traditional tools. These were then tuned 
and tested on a variety of data sets to refine their performance and determine the characteristics and statistics most 
useful to enable faster and more accurate data processing.

The functions enable coding labor-intensive, complicated tasks to improve data quality, remediate errors, 
normalize data across sources, and enrich data for AI/ML, Data Science, scenario modeling, and database modernization.

|

Examples
-------------------------

These example source data files and VerityX result files are provided as-is as mere demonstrations of the 
type of errors that the libraries handle and which are usually beyond the functionality of traditional data tools. 
These source files can be used to compare different tools and coding methods to identify and characterize errors, 
anomalies, and actual versus documented data syntax and semantics.

**THERE IS NO WARRANTY OR GUARANTEE, IMPLICT OR EXPLICIT, THAT THE DATA IS ACCURATE, USABLE IN YOUR 
DATA SYSTEMS, OR FREE FROM HARMFUL EFFECTS WHETHER UNINTENTIONAL OR INTENTIONAL. USE AT YOUR OWN DISCRETION.**

|

* IRSMigration_WithErrors_Hdr.csv : This is a comma separated value text file. It has a header line with the titles 
of the fields. It has been compiled from the full IRS data into a small sample file that contains the type of errors 
commonly encountered. Some of the initial lines in the file::
  
  y2_statefips,y1_statefips,y1_state,y1_state_name,n1,n2,AGI
  01,96,AL,AL Total Migration-US and Foreign,33716,67747,1515297
  01,97,AL,AL Total Migration-US,32868,x65647,1467218
  01,98,AL,"AL Total Migration,Foreign",848,2100,48079
  01,97,AL,AL Total Migration-Same 
  State,46630,95832,1.871804e+6
  01,01,AL,AL 
  Non-
  migrants,1598458,3579600,96406319
  01,13,GA,Georgia,5972,12269,249108
  01,12,FL,Florida,4489,8446,1.85502e+5
  01,48,TX,Texas,3435,7041,135165
  01,47,TN,Tennessee,2608,5304,124203
  01,28,MS,Mississippi,2212,4562,90723
  01,06,CA,California,1169,2274,55689
  01,37,NC,North Carolina,1056,2158,49972
  01,22,LA,Louisiana,883,1671,40723
  01,57,FR,Foreign,848,$2100,48079
  1,51,VA,Virginia,819,1624,$48796
  01,36,ny,New York,772,1518,(34582)
  01,17,il,Illinois,717,1443,-34167
  01,39,oh,Ohio,713,1430,29911
  01,45,sc,South Carolina,637,1220,31594
  01,26,mi,Michigan,594,1125,22176
  01,21,KY,Kentucky,574,1213,27082ê
  01,08,CO,Colorado,473,932,24958‼
  01,29,MO,Missouri,459,901,20884§
  01,18,IN,Indiana,457,895,21821►




|

License
-----------

VerityX products are not open source software and cannot be included in an open source project as its license will break the open source license. Read the full license file for more information.
