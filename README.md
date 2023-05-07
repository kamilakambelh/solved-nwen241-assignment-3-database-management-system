Download Link: https://assignmentchef.com/product/solved-nwen241-assignment-3-database-management-system
<br>
In this assignment, you will implement a simple database management system (DBMS). DBMS is a systems program that performs storage, retrieval, and updating of data in a computer system. DBMS addresses two major problems in conventional file-based systems: data redundancy and data dependence.

<strong>Sample code showing an example on how you can test your code are provided under the files directory in the archive that contains this file. </strong>Full marks is 100.

<strong>Instructions and Submission Guidelines:</strong>

<ul>

 <li>You should provide appropriate comments to make your source codereadable. If your code does not work and there are no comments, you may lose all the marks. See the marking criteria at the end of this document for details about the marks for commenting.</li>

 <li>You should follow a consistent coding style when writing your sourcecode. See the marking criteria at the end of this document for details about the marks for coding style.</li>

 <li>Submit the required files to the Assessment System (<a href="https://apps.ecs.vuw.ac.nz/submit/NWEN241/Programming_Assignment_3">vuw.ac.nz/submit/NWEN241/Programming_Assignment</a><a href="https://apps.ecs.vuw.ac.nz/submit/NWEN241/Programming_Assignment_3">https://apps.</a>_</li>

</ul>

<a href="https://apps.ecs.vuw.ac.nz/submit/NWEN241/Programming_Assignment_3">3</a><a href="https://apps.ecs.vuw.ac.nz/submit/NWEN241/Programming_Assignment_3">)</a> on or before the submission deadline.

<ul>

 <li>Late submissions (up to 48 hours from the submission deadline) willbe accepted but will be penalized. No submissions will be accepted</li>

</ul>

48 hours after the submission deadline.

<strong>Program Design</strong>

A fundamental concept in DBMS is the <em>table</em>. A table consists of zero or more <em>records </em>or entries, and each record can have one or more <em>fields </em>or columns. An example of a table that stores information about music albums is shown below:

<table width="361">

 <tbody>

  <tr>

   <td width="30">id</td>

   <td width="190">title</td>

   <td width="45">year</td>

   <td width="95">artist</td>

  </tr>

  <tr>

   <td width="30">10</td>

   <td width="190">The Dark Side of the Moon</td>

   <td width="45">1973</td>

   <td width="95">Pink Floyd</td>

  </tr>

  <tr>

   <td width="30">14</td>

   <td width="190">Back in Black</td>

   <td width="45">1980</td>

   <td width="95">AC/DC</td>

  </tr>

  <tr>

   <td width="30">23</td>

   <td width="190">Their Greatest Hits</td>

   <td width="45">1976</td>

   <td width="95">Eagles</td>

  </tr>

  <tr>

   <td width="30">37</td>

   <td width="190">Falling into You</td>

   <td width="45">1996</td>

   <td width="95">Celine Dion</td>

  </tr>

  <tr>

   <td width="30">43</td>

   <td width="190">Come Away With Me</td>

   <td width="45">2002</td>

   <td width="95">Norah Jones</td>

  </tr>

  <tr>

   <td width="30">55</td>

   <td width="190">21</td>

   <td width="45">2011</td>

   <td width="95">Adele</td>

  </tr>

 </tbody>

</table>

This table contains 6 records. Each record has 4 fields, namely, id, title, year, and artist.

<strong>In this assignment, you will focus on implementing a single database table with 4 fields (id, title, year, and artist). </strong>To guide you in the implementation, a high-level design of the table is shown below:

The design consists of a C++ class and an array of structures. The C++ class should have the following member variables:

<ul>

 <li>tablecated : a pointer to an array of structures that is dynamically allo-</li>

 <li>rowsTotal: the total number of rows in the array of structures</li>

 <li>rowsUsedtains valid records.: the number of rows in the array of structures that con-</li>

</ul>

The array of structures will hold the records. This array should be dynamically adjusted using the following scheme:

<ul>

 <li>Upon instantiation of the class, memory should be dynamically al-located for holding 5 records. <sub>rowsTotal </sub>should be set to 5 and rowsUsed should be set to 0.</li>

 <li>When adding a record and there is unused space in the table (is less than <sub>rowsTotal</sub>), the record is stored in the next unused row,rowsUsed and rowsUsed is updated accordingly.</li>

 <li>When adding a record and there is no space in the table (is equal to <sub>rowsTotal</sub>), additional memory for holding 5 recordsrowsUsed should be allocated. Then, the record is stored in the next unused row, and rowsUsed and rowsTotal are updated accordingly.</li>

 <li>When removing a record, records after the removed record should bemoved up by one row so that there will be no gaps in between used rows. When the number of unused rows reaches 5, the unused rows should be released, and rowsUsed and rowsTotal are updated accordingly. When removing the last remaining record, do not release the remaining unused rows.</li>

 <li>Upon destruction of the class, allocated memory should be freed.</li>

</ul>

<strong>Task 1.</strong>

Basics [15 Marks]

In this task, you will declare a C structure for holding one (1) table record. The structure should have a tag album with the following members:

<ul>

 <li>id: an unsigned long integer</li>

 <li>title: an array of characters with length 100</li>

 <li>year: an unsigned short integer</li>

 <li>artist: an array of characters with length 100</li>

</ul>

The structure should be defined within dbms namespace. Save the structure in a header file named dbms.hh.

<strong>Task 2.</strong>

Basics [15 Marks]

Declare a C++ class for holding information about the table, as well as supporting table operations specified in Tasks 5–7. The class should be named DbTable and should be defined within dbms namespace.

<em>Minimally</em>, the class should have member variables table, rowsTotal, and rowsUsed as described in the <em>Program Design </em>section. These variables should be unsigned integers and should be private.

In addition to the member functions specified in Tasks 5–7, the class should have the following public member functions that are defined inline:

<ul>

 <li>A function named rows() which should return rowsUsed.</li>

 <li>A function named allocated() which should return rowsTotal.</li>

</ul>

You may declare additional member variables and functions needed by your implementations.

Save the class in a header file named dbms.hh.

<strong>Task 3.</strong>

Basics [15 Marks]

Provide an implementation of the default constructor for the DbTable class. As mentioned in the <em>Program Design </em>section, during instantiation, memory should be dynamically allocated for holding 5 records. Use either malloc() or calloc() for this purpose.

Save the implementation in dbms.cc.

<strong>Task 4.</strong>

Completion [15 Marks]

Provide an implementation of a destructor for the DbTable class.

As mentioned in the <em>Program Design </em>section, during destruction, allocated memory should be freed.

Save the implementation in dbms.cc.

<strong>Task 5.</strong>

Completion [15 Marks]

Provide an implementation of a member function for displaying the information stored in a row. You are free to format the print out, but all fields of the row should be displayed. The function should be called show() and should take an unsigned integer as parameter. This parameter indicates the row number of the record to be displayed.

If the record exists, the function should return true, otherwise, it should return false.

<strong>Task 6.</strong>

Completion [15 Marks]

Provide an implementation of a member function for a adding a record into the database table. The function should be called add() and should take a <em>reference </em>to album structure as input parameter. The input parameter contains the record details to be stored in the table. As mentioned in the <em>Program Design </em>section:

<ul>

 <li>When adding a record and there is unused space in the table (is less than <sub>rowsTotal</sub>), the record is stored in the next unused row,rowsUsed and rowsUsed is updated accordingly.</li>

 <li>When adding a record and there is no space in the table (is equal to <sub>rowsTotal</sub>), additional memory for holding 5 recordsrowsUsed should be allocated. Then, the record is stored in the next unused row, and rowsUsed and rowsTotal are updated accordingly.</li>

</ul>

The function should always return true unless the allocation of additional memory (when needed) fails.

<strong>Task 7.</strong>

Challenge [10 Marks]

Provide an implementation of a member function for a removing a record from the database table. The function should be called remove() and should take an unsigned long integer as input parameter. The input parameter specifies the id of the record to be removed. As mentioned in the <em>Program Design </em>section:

<ul>

 <li>When removing a record, records after the removed record should bemoved up by one row so that there will be no gaps in between used rows. When the number of unused rows reaches 5, the unused rows should be released, and rowsUsed and rowsTotal are updated accordingly. When removing the last remaining record, do not release the remaining unused rows.</li>

</ul>

The function should return true if the removal was successful, otherwise, it should return false.