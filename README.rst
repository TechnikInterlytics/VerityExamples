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

Example Data Files
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
  commonly encountered. Notice that there are some quoted fields while most are not; the line ending in '-Same' is a broken record 
  spanning multiple lines; there are exponential values which should not be present; non-State name 
  text are in fields supposed to be US State names; the last lines end with special characters that many tools 
  do not detect but since they are part of the real data will distort or corrupt processing. Some of the initial lines in the file::
  
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

* IRSMigration_WithErrors_NoBrk_Hdr.csv : This is a comma separated value text file. It has a header line with the titles 
  of the fields. It is the same as the previous source file except that there are no broken records spanning multiple 
  lines. This allows testing tools and code approaches separately for syntax and value errors, and 
  the very difficult challenge of detecting and fixing broken records. Some of the initial lines in the file::

	y2_statefips,y1_statefips,y1_state,y1_state_name,n1,n2,AGI
	01,96,AL,AL Total Migration-US and Foreign,33716,67747,1515297
	01,97,AL,AL Total Migration-US,32868,x65647,1467218
	01,98,AL,"AL Total Migration,Foreign",848,2100,48079
	01,97,AL,AL Total Migration-Same State,46630,95832,1.871804e+6
	01,01,AL,AL Non-migrants,1598458,3579600,96406319
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


* StateAbbrfromFIPS_lookup.dat : text file using pipe ( | ) delimiter that is a lookup of the 
  state code to its standard abbreviation. All codes are 2 digits like 01 and 32. This is used 
  in the examples as a Verity Lookup Dictionary. Example lines::
  
	Code|Abbr
	01|AL
	02|AK
	04|AZ
	05|AR
	06|CA
	08|CO
	09|CT
	10|DE


* StateNamefromFIPS_lookup.dat : text file using pipe ( | ) delimiter that is a lookup of the 
  state code to its standard name. All codes are 2 digits like 01 and 32. This is used 
  in the examples as a Verity Lookup Dictionary. Example lines::

	Code|Name
	01|Alabama
	02|Alaska
	04|Arizona
	05|Arkansas
	06|California
	08|Colorado
	09|Connecticut
	10|Delaware

* FIPS_stateCountyCodes.dat : text file using comma delimiter for a joint code lookup to 
  find a county name given the state and county code. This is used in the Verity library Lookup 
  class and transform function. Example lines::

	stateCode,countyCode,countyName
	01,001,Autauga
	01,003,Baldwin
	01,005,Barbour
	01,007,Bibb
	01,009,Blount
	01,011,Bullock
	01,013,Butler
	01,015,Calhoun
	01,017,Chambers

* USStatesNormalize.dat : text file with a comment line and using pipe delimiter. The 'pattern' 
  value is a search token that can have optional front and/or back wildcard character used 
  to match to a test value and return the 'state' value if a match occurs. This is used in 
  Verity transforms to normalize state names. Note that a proper state name can use as many tokens 
  as needed on separate lines in this file. Example lines::
  
	//key value pairs for US state name normalizing. Each line is defined as pattern|replacement such as tex*|texas where the wildcard * can be used at front or back
	pattern|state
	alab*|Alabama
	*lask*|Alaska
	ariz*|Arizona
	ark*|Arkansas
	cal*|California
	colo*|Colorado
	con*|Connecticut
	del*|Delaware

* lookup_3field_test.dat : a test data file for the Verity Lookup class and transform 
  allowing exploring and debugging a complicated 3 field joint lookup value (i.e. field1_field2_field3), 
  with each containing wildcard ( * ) as well as demarcated boolean operations (e.g. -and- , -not- ). 
  See technical guide for more information. Example lines::
  
	field1|field2|field3|value
	Med*-and-*ary*-and-*-1-not- Sum-not-*#*|BL*-and-*ue*-not-* paper|Me*-and-*ar*-and-*L-1-not-*care |REC0
	Med*-and-*ary*-and-*-1-not- Sum-not-*#1*|BL*-and-*ue*-and-* paper-not-S*-not-*#|123*-and-*9A-not-*care |REC1
	Med*-and-*ary*-and-*-1-not- Sum-not-*#0*|BL*-and-*ue*-and-* paper|123*-and-*9A-not-*care *|REC2

|

License
-----------

VerityX products are not open source software and cannot be included in an open source project as its license will break the open source license. Read the full license file for more information.
