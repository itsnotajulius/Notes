# **MYSQLNOTES:**

## Sections

- [Database and Tables](#database-and-tables)

  - <a href = "#datatype">DataTYPE</a>
  - <a href = "#constraints">Constraints</a>
  - <a href = "#mysql-commandline">MySQL CommandLine</a>

- [Functions](#functions)
  - [String Functions](#a-id"string-functions"-href--"httpsdevmysqlcomdocrefman80enstring-functionshtml"string-functionsa)

</br>
</br>
</br>
</br>

## Database and Tables

### [DataTYPE](https://dev.mysql.com/doc/refman/8.0/en/data-types.html)

```sql
Number_:       					INT
								int(#)
								DECIMAL(digits#,deci#)
								FLOAT                  			7 digits issues
								DOUBLE                 			Bigger float, issues bigger than 15 digits
String:							VARCHAR(#)
								CHAR(#)							Fix length stored with spaces of set size can be 0 to 255
Date_and_Time:					DATE							Format YYYY-MM-DD
								YEAR(4 or 2)
								TIME							Format HH:MM:SS
								DATETIME						Format YYYY-MM-DD HH:MM:SS
								TIMESTAMP						Same DATETIME but smaller
Logical:						BOOL
								BOOLEAN

```

### [Constraints](https://www.w3schools.com/sql/sql_constraints.asp)

    Null:
    	Setting Null:			Mean not defined do nothing
    	No Null:				NOT NULL

    Default:
    	Setting Defailt:		DEFAULT datatypeDefault

    Key:
    	Primary Key:			PRIMARY KEY (<coulumn_name>)
    							PRIMARY KEY (<coulumn_name>,<coulumn_name>)													(Kinda works like Unique)
    	Foreign Key:			FOREIGN KEY (<coulumn_nameThisTable>) REFERENCES table(<coulumn_nameOtherTable>) ?CASCADE?


    Extra:
    	Increment:				AUTO_INCREMENT
    	Update:					ON UPDATE updateTo#
    	Cascade:
    	Unique:					UNIQUE (<coulumn_name>)																		(So can only be one of them)
    							UNIQUE (<coulumn_name>,<coulumn_name>) 														(Used with constraint)
    	Check/Limit:			CHECK (expression)

### MySQL Commandline

```sql
    Run query files:			source filename.sql; - If in same directory
    							source path/<filename>.sql
    List DB:					SHOW databases;
    Create DB:					CREATE DATATBASE <db_name>;
    Detele DB:					DROP DATABASE <db_name>;
    Open DB:					Use <db_name>;
    Currect DB:					SELECT database();
    Exit DB:					exit
	SubQueries:					SELECT subQuery
```

### Table:

```sql
	Create Tables: 				CREATE TABLE tablenames
								(
										<coulumn_name> <data_type> ?Constraints? ?Constraints?,
										<coulumn_name> <data_type>
										?Constraints?
								);
	Delete tables: 				DROP TABLE tablename,tablename,..;
	List Tables: 				SHOW TABLES;
	Show Columns 				SHOW COLUMNS FROM <tablename;
								DESC <tablename;
```

### ALTER Table:

```sql
Rename_Table: 					ALTER TABLE <tablename> CHANGE <coulumn_name> <new_table_name> dataType;
Add_Columns: 					ALTER TABLE <tablename ADD <coulumn_name> dataType;
Add_Constraint: 				ALTER TABLE <tablename ADD ?Constraint?
Drop_Columns: 					ALTER TABLE <tablename DROP <coulumn_name>;
Drop_Constraint: 				ALTER TABLE <tablename DROP ?Constraint?
Modify_Col: 					ALTER TABLE <tablename MODIFY <coulumn_name> dataType;
Modify_Col: 					ALTER TABLE <tablename ALTER <coulumn_name> dataType;
```

###

```sql
Insert_: 						INSERT INTO table_name(column_name, column_name,..) VALUES (data,data,..);
								INSERT INTO table_name(column_name, column_name,..) VALUES (data/dateTimeFunc, data/dateTimeFunc,..);
Multiple_Insert: 				INSERT INTO table_name(column_name, column_name,..) VALUES (data,data,..), (data,data,..), (data,data,..);

Show_Table: 					SELECT * FROM <tablename> ?WHERE?;
Show columns: 					SELECT <coulumn_name> ?AS?, <coulumn_name> ?AS?,.. FROM <tablename ?WHERE?;
								SELECT ?StrFUNC? ?AS?, <coulumn_name ?AS?, FROM <tablename ?WHERE?;
								SELECT ?RefineSel? ?AS?, <coulumn_name> ?AS?, FROM <tablename> ?RefineSel? ?WHERE? ?RefineSel?;
								SELECT ?AggFunc? ?AS?, <coulumn_name> ?AS?, FROM <tablename> ?AggFunc? ?RefineSel?;
								SELECT <tablename>.<coulumn_name> ?AS?, FROM ?Joins? ?AggFunc? ;

Update_: 						UPDATE <tablename SET <coulumn_name>=newValue, <coulumn_name>=newValue,... WHERE <coulumn_name>=searchValue;

Delete_: 						DELETE FROM <tablename WHERE <coulumn_name>=searchValue;
Delete_all: 					DELETE FROM cats;
Warnings: 						SHOW WARNINGS;
```

---

## Functions

### <a id="String Functions" href = "https://dev.mysql.com/doc/refman/8.0/en/string-functions.html">String Functions:</a>

NOTE: Cause they are functions they can be used by each other.

```sql
LowCase:									LOWER(<coulumn_name>/StrFUNC/Text)
UpperCase:									UPPER(<coulumn_name>/StrFUNC/Text)
CONCAT_: 									CONCAT(<coulumn_name, StrFUNC , text, number,....)
CONCAT_WS: 									CONCAT(seperate,<coulumn_name>, StrFUNC, text, number,....)
Left_:										LEFT(text,#);
SUBSTRING_: 								SUBSTRING(<coulumn_name>/StrFUNC/Text, start#, end#)
											SUBSTRING(<coulumn_name>/StrFUNC/Text, start#)
											SUBSTRING(<coulumn_name>/StrFUNC/Text, -start#) Begins back
REPLACE_: 									REPLACE(<coulumn_name>/StrFUNC/Text, searchValue, replaceValue)
REVERSE_: 									REVERSE(<coulumn_name>/StrFUNC/Text)
Length_: 									CHAR_LENGTH(<coulumn_name>/StrFUNC/Text)
											LENGTH(<coulumn_name>/StrFUNC/Text)
LOCATE_:									LOCATE('searchText', 'Text');
											LOCATE('searchText', 'Text', start#);
```

> LOWER() and UPPER() needs to convert binary Strings

### Refining Select:

```sql
WHERE__: 									WHERE <coulumn_name>/NumFunc ?LogOP? <coulumn_name>/#/'Text'/ (subQuery) (SubQuery mustnt have \*)
DISTINCT_: 									SELECT DISTINCT <coulumn_name>/StrFUNC
ORDER_: 									ORDER BY <coulumn_name>/StrFUNC/selectParameterNumber ?DESC?, <coulumn_name>/StrFUNC/selectParameterNumber ?DESC?
LIMIT_: 									LIMIT #;
LIKE_: 										WHERE <coulumn_name>/StrFUNC LIKE '%inText%'/'startText%'/'%endText'/'**'/'%\%%'/'%\_%'
Not_LIKE: 									WHERE <coulumn_name>/StrFUNC NOT LIKE '%inText%'/'startText%'/'%endText'/'**'/'%\%%'/'%\_%'
```

### [Aggregate Functions:](https://dev.mysql.com/doc/refman/8.0/en/aggregate-functions-and-modifiers.html)

```sql
COUNT_: 									COUNT(?RefineSel? <coulumn_name>/StrFUNC,<coulumn_name>/StrFUNC,...)
GROUP_BY: 									GROUP BY <coulumn_name>, <coulumn_name> Makes groups unseen
MIN_: 										MIN(<coulumn_name>)
MAX_: 										MAX(<coulumn_name>)
SUM_: 										SUM(<coulumn_name>)
AVG_: 										AVG(<coulumn_name>)
```

</br></br></br>

### [Date Time Functions:](https://dev.mysql.com/doc/refman/8.0/en/date-and-time-functions.html)

```sql
Current_Date:								CURDATE()
CurrentTime: 								CURTIME()
Now_: 										NOW()
MINUTE: 									MINUTE(<coulumn_name>/'dateTimeFormat')
HOUR: 										HOUR(<coulumn_name>/'dateTimeFormat')
DAY_: 										DAY(<coulumn_name>/'dateTimeFormat')
DAY_NAME: 									DAYNAME(<coulumn_name>/'dateTimeFormat')
DAY_OF_WEEK: 								DAYOFWEEK(<coulumn_name>/'dateTimeFormat')
DAY_OF_YEAR 								DAYOFYEAR(<coulumn_name>/'dateTimeFormat')
MONTH_: 									MONTH(<coulumn_name>/'dateTimeFormat')
MONTH_NAME: 								MONTHNAME(<coulumn_name>/'dateTimeFormat')
DATEFORMAT_: 								DATE_FORMAT(<coulumn_name>/'dateTimeFormat', 'TEXT$Format$Format....') [Website](https://dev.mysql.com/doc/refman/8.0/en/date-and-time-functions.html#function_date-format)
Date_Difference: 							DATEDIFF(<coulumn_name>/'dateTimeFormat', dateTimeFunc/'dateTimeFormat') [Website](https://dev.mysql.com/doc/refman/8.0/en/date-and-time-functions.html#function_date-add)
Date_Add: 									DATE_ADD(<coulumn_name>/'dateTimeFormat'/dateTimeFunc, INTERVAL #/'dateTimeFormat' unit) https://dev.mysql.com/doc/refman/8.0/en/date-and-time-functions.html#function_date-add
Date_Sub: 									DATE_SUB(<coulumn_name>/'dateTimeFormat'/dateTimeFunc, INTERVAL #/'dateTimeFormat' unit) https://dev.mysql.com/doc/refman/8.0/en/date-and-time-functions.html#function_date-add
											Use +- <coulumn_name>/'dateTimeFormat'/dateTimeFunc +- INTERVAL #/'dateTimeFormat' unit +/....

```

</br></br></br>

### Operators:

```sql
Equal 										=
Not_Equal 									!=
Greater Than: 								>
											>=
Less Than: 									<
											<=
LIKE_: 										WHERE <coulumn_name>/StrFUNC LIKE '%inText%'/'startText%'/'%endText'/'**'/'%\%%'/'%\_%'
Not_LIKE: 									WHERE <coulumn_name>/StrFUNC NOT LIKE '%inText%'/'startText%'/'%endText'/'**'/'%\%%'/'%\_%'
AND_: 										?LogOp? AND ?LogOp? ....
OR_: 										?LogOp? OR ?LogOp? ....
IN_: 										IN(x,y,....) (Lets you do multiple OR searches on column but with Logic of Equal)(x,y can be different datatypes)
IN_: 										NOT IN(x,y,....) (Lets you do multiple OR searches on column but with Logic of Not Equal)(x,y can be different datatypes)
BETWEEN_: 									BETWEEN x AND y (>=x AND <=y)(Use CAST('' AS DATATYPE))
If_NUll:									<coulumn_name>/AggFunc IS NULL
```

</br></br></br>

### [Flow Control Functions:](https://dev.mysql.com/doc/refman/8.0/en/flow-control-functions.html)

```sql
	If_Statments: 							If(equation,trueAns,falseAns)
    IfNul_l: 								IFNULL(checkIfNull, answerIfNull)
	Cases: 									CASE
												WHEN Logical THEN 'answer'
												ELSE 'falseAnswer'
											END ?AS?
```

</br></br></br>

### [Numeric Functions And Operators:](https://dev.mysql.com/doc/refman/8.0/en/numeric-functions.html)

```sql
 	Plus: 									#+#
    Minus: 									#-#
	Multiply: 								#\*#
	Divide: 								#/# (Calculed with BIGINT)
											DIV(3,Div#) (Converted to DECIMAL to Cal and Converted to BIGINT)
	Remainder: 								MOD(#,Div#)
```

</br>
</br></br>

### Relationships/Joins:

All below is to do with relationships between tables and ways of Selecting data where they have relationships.
Setting up relationships is set when creating a table or altering the column. There are 3 types of relationships:

> One_to_One

EG: PERSON has one ID and one ID belongs to one PERSON

> One_to_Many

EG: CUSTOMER can have many ORDERS but ORDER belongs to one CUSTOMER

> Many_to_Many

EG: AUTHORS can have many BOOKS and BOOKS can have many AUTHORS

</br>

```sql
Cross_Joins: 								FROM <tablename,<tablename; (Just joins everything)
Implicit_Join:	 							FROM <tablename,<tablename WHERE table1.primeCol = table2.ForgiegnCol;
Explicit_Join:	 							FROM <tablename JOIN <tablename ON table1.primeCol = table2.ForgiegnCol;
Left_Join: 									FROM <tablename LEFT JOIN <tablename ON table1.primeCol = table2.ForgiegnCol;
Right_Join: 								FROM <tablename RIGHT JOIN <tablename ON table1.primeCol = table2.ForgiegnCol;
Cascade: 									ON DELETE CASCADE (Add on foriegn key will delete entry if primary key of other table entry is deleted)
```

</br></br></br>

# THOERY

</br>

| <h2>Definitions:</h2> |     |                                                                                                    |
| --------------------- | --- | -------------------------------------------------------------------------------------------------: |
| **CRUD:**             |     |                                                                          Create Read Update Delete |
| **SQL**               |     |                                                                       Language to talk to database |
| **MySQL**             |     |                                                 Uses SQL just has different features to other DBMS |
| **Database:**         |     |                                                                      Collection of Data (Database) |
| **MySQL use**         |     | Method of accessing and manipulating data (DBMS) Relational Database eg. MYSQL, PstgreSQL, SQLite, |
| **Columns**           |     |                                                                      Headers / Col_Name / Variable |
| **Rows**              |     |                                                                                               Data |
