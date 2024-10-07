Readme
========

**VerityPy** is a Python library by Technik Interlytics for Better Data = Better Outcomes. 
It is a Data Inspector, Remediator, and Enricher on structured data. 
It combines curated human expertise with Machine Learning (ML) into software 
components to accelerate development and signficantly lower the level of effort needed 
to make data ready for high quality Data Science, Machine Learning, and predictive models.

The libraries contain expert algorithms developed from in-depth investigations, forensic tracing, and specialized remediation on 
large data systems across many fields, always with successful outcomes. Our human experts discovered where to look, 
what to look for, and what to do about problems especially deeply buried ones missed by traditional tools. These were then tuned 
and tested on a variety of data sets to refine their performance and determine the characteristics and statistics most 
useful to enable faster and more accurate data processing.

|

Features
-------------------------

1. Inspect: deep analysis and characterization of data for structural and value consistency, 
   anomalies, and errors especially those deeply buried problems that are 
   not detected by common DataOps tools. Some examples are:

      * data variations (types, formats, encoding) from import/export in different systems especially spreadsheets and legacy mainframes
      * special characters not visible to users causing downstream problems
      * small number of anomalies buried within very large data sets overwhelming tools
      * mismatched joint field values such as geographic location codes and names
      * long strings of digits used as codes (e.g. accounting, ERP) cast into number format stripping digits thereby corrupting codes
      * records broken into multiple lines causing fields to be misaligned, partial records, and incorrect values
      * open source data with embedded information-only records (e.g. IRS USA Migration demographics, Covid disease census) unknown to users

|

2. Remediate: make data accurate for structure (field positions, data types, formats), 
   and values (numeric ranges, codes, lists of allowed values). Detect and fix parsing 
   errors including challenging multi-line records.
   Some examples are:

      * rebuilding records broken into multiple lines
      * adding enrichment fields to annotate pedigree, trust, privacy, increased granularity with conditional logic and controlled vocabulary
      * several levels of conditional testing of multiple fields within single records to correctly encode/decode, transform field values
      * allowing multiple versions of lookup decoding per field based on other field indicators (e.g. time varying encoding schemes)
      * identifying when long values of numeric digits are strings or numbers and handling accordingly
      * lookup dictionary replacements using 1 or multiple fields as well as wildcard tokens and both boolean AND and NOT conditions

|

3. Enrich: add metadata into records as analytic factors 
   and facets for Machine Learning. Enable downstream analytics to easily filter 
   on multiple criteria, generate Pivot tables, and feed drill-down style dashboards. 
   Higher granularity facets can be inserted into data records to power Machine Learning thereby 
   producing more accurate models.
   Some examples from the IRS Migration data used in code samples are:

      * add boolean field useAGI to annotate records that have correct AGI (adjusted gross income) values from those intentionally coded with false values by data owners (actual in source)
      * add boolean field isSubTotal to annotate records that have partial sums of transaction records (actual in source)
      * add string field DestStateAbbr since source records have abbreviation for origin state but not destination
      * add string field DestStateName since source records have name for origin state but not destination

|

Why Use **VerityPy**
---------------------

It was created to solve the need to not just make data accurate, but also provide high visibility into how and why it 
was handled with transforms and codings such that it can be managed like other key business assets with oversight and collaborative review. 
All too often, the actual manipulation of data is handled by proficient engineers but the people who most need to review, understand, and adjust 
what is done are unable to decipher the complicated code, scripts, and technical documentation. Our human experts witnessed this situation in 
many clients and had to solve this challenge before the technical results would be accepted. Doing so led us to develop new data processing and 
reporting approaches that jointly handled complicated data engineering requirements along with visible and easy to understand business reporting. 
**VerityPy** was created to provide this capability to a wide community with the following key concepts:

   * easily reuse and adjust processing parameters for multiple iterations of transforms, codings, rules with reviews of results in end-use applications
   * review data processing steps and intermediate results throughout the entire process (i.e. no black boxes)
   * use processing commands that can be reviewed by business and technical people at both staff and manager levels
   * enable drop-in reporting with summary and detailed charts and tables of data actions, discoveries, and results
   * provide multiple views of data before and after to maximize understanding and discovery among all user types


|

**VerityPy** Functions
--------------------------


Analysis
+++++++++

**VerityPy** analyzes structured source data and generates a thorough assessment of each field's 
actual value space for data types, formats, ranges, special characters, unique values and even coValues 
which are joint field (2 or 3) value distributions. This is a quick way to both profile source 
data, extract its schema, and discover anomalies that can be overlooked by other tools or 
missed by manual Quality Control reviews. A comprehensive report is returned in a Python object 
that can be used in further processing to make tables and charts such as in Jupyter Notebook.

Results are coordinated in a Python class 'QualityAnalysis' allowing concise handling 
of the setup parameters and the breadth and depth of discovered characteristics and 
known/suspected errors. These results include:

   * field unique values: per field unique values with count of instances.
   * field datatype distributions: each field has counts for detected datatypes (int, real, bool, date, string, empty).
   * field quality: each field is assigned a quality factor 0-100 based on discovered characteristics and knowledge-based algorithms.
   * record size distribution: record sizes (byte lengths) to count of instances.
   * record parsing errors: parsing errors (number fields after parsing relative to defined fields) 
     by small1 (1 too few fields), small2 (2 or more missing fields), big (1 or more too many fields). Also, has example records.
   * record parsing distribution: number of parsed fields to count of instances.
   * special character distribution: special characters and their count of instances, as well as example records.
   * coValues: field combinations (2 or 3) unique value information. 
   * error statistics: values such as number records with any kind of error, number records 
     with datatype error, number records with format error and more



Normalize & Enrich
++++++++++++++++++++

**VerityPy's** transforms allow Normalizing and Enriching source data with 
a high level of quality, accuracy, and meaning to support demanding use cases. There are five 
kinds of transforms (see transforms page for details):

   1. Assignment: assigns values to field as a fixed value, reference to another field in record, random number, list of categories via frequencies, lookup dictionaries
   2. Conditional: conditional tests of equality and inequality for numeric, string, and date values
   3. Numeric: numeric calculation functions including using other fields in record by reference
   4. Text: manipulate with slicing, adding, padding, replacing
   5. Date: Change date format to ISO 8601 including from special Excel format 

This is an example of a transform to populate an enrichment field 'useAGI' that denotes whether the record should be used 
in analytics based on the value of a numeric source field 'AGI'.

   1. setToRef("AGI")
   2. ifEq("-1")
   3. setToValue("true")
   4. setToValue("false")

In order to allow chaining of conditional functions, the flow is condition -> [false action] else [true action]. Thus, if step 2 above is False 
then step 3 is done and the chain stops, whereas if step 2 is True then step 3 is skipped and step 4 is done (and any steps after it if they existed). 
The net result is this simple transform fills an enrichment field with boolean value enabling easy filtering downstream in a spreadsheet, database, 
or analytics dashboard.

A slightly more complicated logic flow that includes fixing formatting is the following transform that uses a source field 'y2_statefips' containing a 2 character 
code to lookup the corresponding title in an external lookup dictionary and then assigns that to an enrichment field 'DestStateName' since the 
original source data only had the code making it non-intuitive for users to understand the data records. 

   1. setToRef("y2_statefips")
   2. setLength("2","left","0")
   3. lookup("StateName")

Step 1 gets the value of the field 'y2_statefips' from the current record. Step 2 fixes the string length to 2 characters with changes made 
to the left side of the string if it is too long (characters cut from left) or too short (characters added to left) with the character to 
add set to be '0' (zero). This is critical for code lookups since a very common problem when data is moved among systems is for leading 
zeros to be removed thereby changing a code like '01' into '1' which would not be found in the lookup. This ensures that such an error 
is fixed prior to doing the lookup which occurs in step 3 to a dictionary name 'StateName' (loaded during the setup phase of the job).

|

License
-----------

This is not open source software and cannot be included in an open source project as its license will break the open source license. 
However, there is a license allowing free use for non-commercial, personal applications. 
Read the license file for full details about allowed scope of free use. 
Paid licenses are required for commercial products either distributed or web hosted (e.g. SaaS), as well as enterprise applications with multiple users. 
There are licenses for developers, royalty inclusion in other products, and support.
