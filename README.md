# InnerJoins
```sql
mysql> INSERT INTO Table1 (ID, Value)
    -> SELECT 1, 'First'
    -> UNION ALL
    -> SELECT 2, 'Second'
    -> UNION ALL
    -> SELECT 3, 'Third'
    -> UNION ALL
    -> SELECT 4, 'Fourth'
    -> UNION ALL
    -> SELECT 5,'Fifth';
Query OK, 5 rows affected (0.01 sec)
Records: 5  Duplicates: 0  Warnings: 0

mysql> create table table2
    -> (ID INT, Value VARCHAR(10));
Query OK, 0 rows affected (0.03 sec)

mysql> INSERT INTO Table2 (ID, Value)
    -> SELECT 1, 'First'
    -> UNION ALL
    -> SELECT 2, 'Second'
    -> UNION ALL
    -> SELECT 3, 'Third'
    -> UNION ALL
    -> SELECT 6, 'Sixth''
    '> UNION ALL^C
mysql> INSERT INTO Table2 (ID, Value)
    -> SELECT 1, 'First'
    -> UNION ALL
    -> SELECT 2, 'Second'
    -> UNION ALL
    -> SELECT 3, 'Third'
    -> UNION ALL
    -> SELECT 6, 'Sixth'
    -> UNION ALL
    -> SELECT 7, 'Seventh'
    -> UNION ALL
    -> SELECT 7, 'Eighth';
Query OK, 6 rows affected (0.01 sec)
Records: 6  Duplicates: 0  Warnings: 0

mysql> SELECT * FROM Table1;
+------+--------+
| ID   | Value  |
+------+--------+
|    1 | First  |
|    2 | Second |
|    3 | Third  |
|    4 | Fourth |
|    5 | Fifth  |
+------+--------+
5 rows in set (0.00 sec)

mysql> SELECT * FROM Table2;
+------+---------+
| ID   | Value   |
+------+---------+
|    1 | First   |
|    2 | Second  |
|    3 | Third   |
|    6 | Sixth   |
|    7 | Seventh |
|    7 | Eighth  |
+------+---------+
6 rows in set (0.00 sec)

mysql> SELECT t1.*,t2.* FROM Table1 t1 INNER JOIN Table2 t2 ON t1.ID = t2.ID;
+------+--------+------+--------+
| ID   | Value  | ID   | Value  |
+------+--------+------+--------+
|    1 | First  |    1 | First  |
|    2 | Second |    2 | Second |
|    3 | Third  |    3 | Third  |
+------+--------+------+--------+
3 rows in set (0.00 sec)
