# simple-database-engine
Overview
You are going to build the first component of a simple database engine in Java. The required functionalities are creating tables, building indices, storing data, deleting data, and querying. Follow the below description
Tables
1) Each table/relation will be stored as pages on disk (each page is a separate file). 
2) A page has a predetermined fixed maximum number of rows (N). For example, if a 
table has 40000 tuples, and if N=200, the table will be stored in 200 files. 
4) You are required to use Java’s binary object file (.class) for emulating a page (to avoid 
having you work with file system pages, which is not the scope of this course). A single 
page must be stored as a serialized Vector (java.util.Vector) , because Vectors are thread 
safe). Note that you can save/load any Java object to/from disk by implementing the 
java.io.Serializable interface. You don’t actually need to add any code to your class to 
save it the hard disk.
5) A single tuple should be stored in a separate object inside the binary file.  
6) If all the rows in a page are deleted, then you are required to delete that page. Do not 
keep around completely empty pages. In the case of insert, if you are trying to insert in a 
full page, shift one row down to the following page. Do not create a new page unless you 
are in the last page of the table and that last one was full. 
7) Each user table has meta data associated with it; number of columns, data type of 
columns, which columns have indices built on them. 
10) You will need to store the meta-data in a text file. This should have the following 
layout: 
TableName,ColumnName, ColumnType, ClusteringKey, IndexName, IndexType, min, max 
- ClusteringKey is set true if the column is the primary key.  you will 
always sort the rows in the table according to the primary key. 
- min and max refer to the minimum and maximum values possible for that column. 
11) You are required to use an Octree to support creating indices
