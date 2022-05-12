# **MYSQLNOTES:**

## Sections

[Database and Tables](#database-and-tables)

--

## Database and Tables

### DataTYPE:

    Number:						INT
                      			int(#)
                      			DECIMAL(digits#,deci#)
                      			FLOAT							7 digits issues
                      			DOUBLE							Bigger float issues bigger than 15 digits
    String:						VARCHAR(#)
    							CHAR(#)							Fix length stored with spaces of set size can be 0 to 255
    Date and Time:				DATE							Format YYYY-MM-DD
    							TIME							Format HH:MM:SS
    							DATETIME						Format YYYY-MM-DD HH:MM:SS
    							TIMESTAMP						Same as DATETIME but smaller

### Constraints:

    Null:
    	Setting Null:			Mean not defined do nothing
    	No Null:				NOT NULL

    Default:
    	Setting Defailt:		DEFAULT datatypeDefault

    Key:
    	Primary Key:			PRIMARY KEY (<coulumn_name>)
    	Foreign Key:			FOREIGN KEY (<coulumn_nameThisTable>) REFERENCES table(<coulumn_nameOtherTable>) ?CASCADE?


    Extra:
    	Increment:				AUTO_INCREMENT
    	Update:					ON UPDATE updateTo#
    	Cascade:
    	Unique:					UNIQUE (<coulumn_name>)
    							UNIQUE (<coulumn_name>,<coulumn_name>) 														(Used with constraint)
    	Check/Limit:			CHECK (expression)

### MySQL:

```sql
    Run query:					source filename.sql; - If in same directory
    							source path/<filename>.sql
    List DB:					SHOW databases;
    Create DB:					CREATE DATATBASE <db_name>;
    Detele DB:					DROP DATABASE <db_name>;
    Open DB:					Use <db_name>;
    Currect DB:					SELECT database();
    Exit DB:					exit
```

### Table:

```sql
	Crete Tables: 				CREATE TABLE tablenames
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
Rename Table: 					ALTER TABLE <tablename> RENAME TO <new_table_name>;
Add Columns: 					ALTER TABLE <tablename ADD <coulumn_name dataType;
Add Constraint: 				ALTER TABLE <tablename ADD ?Constraint?
Drop Columns: 					ALTER TABLE <tablename DROP <coulumn_name>;
Drop Constraint: 				ALTER TABLE <tablename DROP ?Constraint?
Modify Col: 					ALTER TABLE <tablename MODIFY <coulumn_name> dataType;
Modify Col: 					ALTER TABLE <tablename ALTER <coulumn_name> dataType;



Insert: 						INSERT INTO table_name(column_name, column_name,..) VALUES (data,data,..);
								INSERT INTO table_name(column_name, column_name,..) VALUES (data/dateTimeFunc, data/dateTimeFunc,..);
Multiple Insert: 				INSERT INTO table_name(column_name, column_name,..) VALUES (data,data,..), (data,data,..), (data,data,..);

Show Table: SELECT \* FROM <tablename ?WHERE?;
Show columns: SELECT <coulumn_name> ?AS?, <coulumn_name> ?AS?,.. FROM <tablename ?WHERE?;
SELECT ?StrFUNC? ?AS?, <coulumn_name ?AS?, FROM <tablename ?WHERE?;
SELECT ?RefineSel? ?AS?, <coulumn_name> ?AS?, FROM <tablename> ?RefineSel? ?WHERE? ?RefineSel?;
SELECT ?AggFunc? ?AS?, <coulumn_name> ?AS?, FROM <tablename> ?AggFunc? ?RefineSel?;
SELECT <coulumn_name> ?AS?, FROM ?Joins? ?AggFunc? ;

Update: UPDATE <tablename SET <coulumn_name>=newValue, <coulumn_name>=newValue,... WHERE <coulumn_name>=searchValue;

Delete: DELETE FROM <tablename WHERE <coulumn_name>=searchValue;
Delete all: DELETE FROM cats;
Warnings: SHOW WARNINGS;
```

---

## Functions

### [String Functions:](https://dev.mysql.com/doc/refman/8.0/en/string-functions.html)

```sql
NOTE: Cause they are functions they can be used by each other.

CONCAT: 							CONCAT(<coulumn_name, StrFUNC , text, number,....)
CONCAT_WS: 							CONCAT(seperate,<coulumn_name>, StrFUNC, text, number,....)
SUBSTRING: 							SUBSTRING(<coulumn_name>/StrFUNC/Text, start#, end#)
									SUBSTRING(<coulumn_name>/StrFUNC/Text, start#)
									SUBSTRING(<coulumn_name>/StrFUNC/Text, -start#) Begins back
REPLACE: 							REPLACE(<coulumn_name>/StrFUNC/Text, searchValue, replaceValue)
REVERSE: 							REVERSE(<coulumn_name>/StrFUNC/Text)
Row_Data_LENGTH: 					CHAR_LENGTH(<coulumn_name>/StrFUNC/Text)
```

### Refining Select:

```sql
WHERE: 									WHERE <coulumn_name>/NumFunc ?LogOP? <coulumn_name>/#/'Text'/ (subQuery) (SubQuery mustnt have \*)
DISTINCT: 								SELECT DISTINCT <coulumn_name>/StrFUNC
ORDER: 									ORDER BY <coulumn_name>/StrFUNC/selectParameterNumber ?DESC?, <coulumn_name>/StrFUNC/selectParameterNumber ?DESC?
LIMIT: 									LIMIT #;
LIKE: 									WHERE <coulumn_name>/StrFUNC LIKE '%inText%'/'startText%'/'%endText'/'**'/'%\%%'/'%\_%'
Not LIKE: 								WHERE <coulumn_name>/StrFUNC NOT LIKE '%inText%'/'startText%'/'%endText'/'**'/'%\%%'/'%\_%'
```

### [Aggregate Functions:](https://dev.mysql.com/doc/refman/8.0/en/aggregate-functions-and-modifiers.html)

```sql
  COUNT: 								COUNT(?RefineSel? <coulumn_name>/StrFUNC,<coulumn_name>/StrFUNC,...)
  GROUP_BY: 							GROUP BY <coulumn_name>, <coulumn_name> Makes groups unseen
  MIN: 									MIN(<coulumn_name>)
  MAX: 									MAX(<coulumn_name>)
  SUM: 									SUM(<coulumn_name>)
  AVG: 									AVG(<coulumn_name>)
```

### [Date Time Functions:](https://dev.mysql.com/doc/refman/8.0/en/date-and-time-functions.html)

```sql
Current Date: CURDATE()
Current time: CURTIME()
Now: NOW()
MINUTE: MINUTE(<coulumn_name>/'dateTimeFormat')
HOUR: HOUR(<coulumn_name>/'dateTimeFormat')
DAY: DAY(<coulumn_name>/'dateTimeFormat')
DAY NAME: DAYNAME(<coulumn_name>/'dateTimeFormat')
DAY OF WEEK: DAYOFWEEK(<coulumn_name>/'dateTimeFormat')
DAY OF YEAR DAYOFYEAR(<coulumn_name>/'dateTimeFormat')
MONTH: MONTH(<coulumn_name>/'dateTimeFormat')
MONTH NAME: MONTHNAME(<coulumn_name>/'dateTimeFormat')
DATE FORMAT: DATE_FORMAT(<coulumn_name>/'dateTimeFormat', 'TEXT$Format$Format....') [Website](https://dev.mysql.com/doc/refman/8.0/en/date-and-time-functions.html#function_date-format)
Date Difference: DATEDIFF(<coulumn_name>/'dateTimeFormat', dateTimeFunc/'dateTimeFormat') [Website](https://dev.mysql.com/doc/refman/8.0/en/date-and-time-functions.html#function_date-add)

      Date Add: DATE_ADD(<coulumn_name>/'dateTimeFormat'/dateTimeFunc, INTERVAL #/'dateTimeFormat' unit) https://dev.mysql.com/doc/refman/8.0/en/date-and-time-functions.html#function_date-add
      Date Sub: DATE_SUB(<coulumn_name>/'dateTimeFormat'/dateTimeFunc, INTERVAL #/'dateTimeFormat' unit) https://dev.mysql.com/doc/refman/8.0/en/date-and-time-functions.html#function_date-add
      Use +- <coulumn_name>/'dateTimeFormat'/dateTimeFunc +- INTERVAL #/'dateTimeFormat' unit +/....

```

## Operators:

```sql
  1.  Equal 							=
      Not Equal !=
      Greater Than: > >=
      Less Than: <
      <=
      LIKE: WHERE <coulumn_name>/StrFUNC LIKE '%inText%'/'startText%'/'%endText'/'**'/'%\%%'/'%\_%'
      Not LIKE: WHERE <coulumn_name>/StrFUNC NOT LIKE '%inText%'/'startText%'/'%endText'/'**'/'%\%%'/'%\_%'
      AND: ?LogOp? AND ?LogOp? ....
      OR: ?LogOp? OR ?LogOp? ....
      IN: IN(x,y,....) (Lets you do multiple OR searches on column but with Logic of Equal)(x,y can be different datatypes)
      IN: NOT IN(x,y,....) (Lets you do multiple OR searches on column but with Logic of Not Equal)(x,y can be different datatypes)
      BETWEEN: BETWEEN x AND y (>=x AND <=y)(Use CAST('' AS DATATYPE))
```

### [Flow Control Functions:](https://dev.mysql.com/doc/refman/8.0/en/flow-control-functions.html)

```sql
	If_Statments: 						If(equation,trueAns,falseAns)
    IfNull: 							IFNULL(checkIfNull, answerIfNull)
	Cases: 								CASE
											WHEN Logical THEN 'answer'
											ELSE 'falseAnswer'
										END ?AS?
```

### [Numeric Functions And Operators:](https://dev.mysql.com/doc/refman/8.0/en/numeric-functions.html)

```sql
 	Plus: 							#+#
    Minus: 							#-#
	Multiply: 						#\*#
	Divide: 							#/# (Calculed with BIGINT)
									DIV(3,Div#) (Converted to DECIMAL to Cal and Converted to BIGINT)
	Remainder: 						MOD(#,Div#)
```

### Relationships/Joins:

All below is to do with relationships between tables and ways of Selecting data where they have relationships.
Setting up relationships is set when creating a table or altering the column.

```sql
    One_to_One
	One_to_Many
	Many_to_Many
	Cross_Joins: 					FROM <tablename,<tablename; (Just joins everything)
	Implicit_Join: 					FROM <tablename,<tablename WHERE table1.primeCol = table2.ForgiegnCol;
	Explicit_Join: 					FROM <tablename JOIN <tablename ON table1.primeCol = table2.ForgiegnCol;
	Left_Join: 						FROM <tablename LEFT JOIN <tablename ON table1.primeCol = table2.ForgiegnCol;
	Right_Join: 					FROM <tablename RIGHT JOIN <tablename ON table1.primeCol = table2.ForgiegnCol;
	Cascade: 						ON DELETE CASCADE (Add on foriegn key will delete entry if primary key of other table entry is deleted)
```

# THOERY

| <h2>Definitions:</h2> |     |                                                                                                    |
| --------------------- | --- | -------------------------------------------------------------------------------------------------: |
| **CRUD:**             |     |                                                                          Create Read Update Delete |
| SQL                   |     |                                                                       Language to talk to database |
| MySQL                 |     |                                                 Uses SQL just has different features to other DBMS |
| Database:             |     |                                                                      Collection of Data (Database) |
| MySQL use             |     | Method of accessing and manipulating data (DBMS) Relational Database eg. MYSQL, PstgreSQL, SQLite, |
| Columns               |     |                                                                      Headers / Col_Name / Variable |
| Rows                  |     |                                                                                               Data |
