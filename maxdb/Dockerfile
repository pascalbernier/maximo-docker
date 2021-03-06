# (C) Copyright IBM Corporation 2015.
# (C) Copyright Yasutaka Nishimura 2015.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#      http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
FROM ibmcom/db2express-c

RUN su - db2inst1 -c "db2start && db2 create db 'maxdb76' ALIAS 'maxdb76' using codeset UTF-8 territory US pagesize 32 K"
RUN su - db2inst1 -c "db2start && db2 update db cfg for maxdb76 using SELF_TUNING_MEM ON"
RUN su - db2inst1 -c "db2start && db2 update db cfg for maxdb76 using APPGROUP_MEM_SZ 16384 DEFERRED"
RUN su - db2inst1 -c "db2start && db2 update db cfg for maxdb76 using APPLHEAPSZ 2048 AUTOMATIC DEFERRED"
RUN su - db2inst1 -c "db2start && db2 update db cfg for maxdb76 using AUTO_MAINT ON DEFERRED"
RUN su - db2inst1 -c "db2start && db2 update db cfg for maxdb76 using AUTO_TBL_MAINT ON DEFERRED"
RUN su - db2inst1 -c "db2start && db2 update db cfg for maxdb76 using AUTO_RUNSTATS ON DEFERRED"
RUN su - db2inst1 -c "db2start && db2 update db cfg for maxdb76 using AUTO_REORG ON DEFERRED"
RUN su - db2inst1 -c "db2start && db2 update db cfg for maxdb76 using AUTO_DB_BACKUP ON DEFERRED"
RUN su - db2inst1 -c "db2start && db2 update db cfg for maxdb76 using CATALOGCACHE_SZ 800 DEFERRED"
RUN su - db2inst1 -c "db2start && db2 update db cfg for maxdb76 using CHNGPGS_THRESH 40 DEFERRED"
RUN su - db2inst1 -c "db2start && db2 update db cfg for maxdb76 using DBHEAP AUTOMATIC"
RUN su - db2inst1 -c "db2start && db2 update db cfg for maxdb76 using MAXLOCKS AUTOMATIC DEFERRED"
RUN su - db2inst1 -c "db2start && db2 update db cfg for maxdb76 using LOCKLIST AUTOMATIC DEFERRED"
RUN su - db2inst1 -c "db2start && db2 update db cfg for maxdb76 using LOGBUFSZ 1024 DEFERRED"
RUN su - db2inst1 -c "db2start && db2 update db cfg for maxdb76 using LOCKTIMEOUT 300 DEFERRED"
RUN su - db2inst1 -c "db2start && db2 update db cfg for maxdb76 using LOGPRIMARY 20 DEFERRED"
RUN su - db2inst1 -c "db2start && db2 update db cfg for maxdb76 using LOGSECOND 100 DEFERRED"
RUN su - db2inst1 -c "db2start && db2 update db cfg for maxdb76 using LOGFILSIZ 8192 DEFERRED"
RUN su - db2inst1 -c "db2start && db2 update db cfg for maxdb76 using SOFTMAX 1000 DEFERRED"
RUN su - db2inst1 -c "db2start && db2 update db cfg for maxdb76 using MAXFILOP 61440 DEFERRED"
RUN su - db2inst1 -c "db2start && db2 update db cfg for maxdb76 using PCKCACHESZ AUTOMATIC DEFERRED"
RUN su - db2inst1 -c "db2start && db2 update db cfg for maxdb76 using STAT_HEAP_SZ AUTOMATIC DEFERRED"
RUN su - db2inst1 -c "db2start && db2 update db cfg for maxdb76 using STMTHEAP AUTOMATIC DEFERRED"
RUN su - db2inst1 -c "db2start && db2 update db cfg for maxdb76 using UTIL_HEAP_SZ 10000 DEFERRED"
RUN su - db2inst1 -c "db2start && db2 update db cfg for maxdb76 using DATABASE_MEMORY AUTOMATIC DEFERRED"
RUN su - db2inst1 -c "db2start && db2 update db cfg for maxdb76 using AUTO_STMT_STATS OFF DEFERRED"
RUN su - db2inst1 -c "db2start && db2 update db cfg for maxdb76 using STMT_CONC LITERALS DEFERRED"
RUN su - db2inst1 -c "db2start && db2 update alert cfg for database on maxdb76 using db.db_backup_req SET THRESHOLDSCHECKED YES"
RUN su - db2inst1 -c "db2start && db2 update alert cfg for database on maxdb76 using db.tb_reorg_req SET THRESHOLDSCHECKED YES"
RUN su - db2inst1 -c "db2start && db2 update alert cfg for database on maxdb76 using db.tb_runstats_req SET THRESHOLDSCHECKED YES"
RUN su - db2inst1 -c "db2start && db2 update dbm cfg using PRIV_MEM_THRESH 32767 DEFERRED"
RUN su - db2inst1 -c "db2start && db2 update dbm cfg using KEEPFENCED NO DEFERRED"
RUN su - db2inst1 -c "db2start && db2 update dbm cfg using NUMDB 2 DEFERRED"
RUN su - db2inst1 -c "db2start && db2 update dbm cfg using RQRIOBLK 65535 DEFERRED"
RUN su - db2inst1 -c "db2start && db2 update dbm cfg using HEALTH_MON OFF DEFERRED"
RUN su - db2inst1 -c "db2start && db2 update dbm cfg using AGENT_STACK_SZ 1000 DEFERRED"
RUN su - db2inst1 -c "db2start && db2 update dbm cfg using MON_HEAP_SZ AUTOMATIC DEFERRED"
RUN su - db2inst1 -c "db2set DB2_SKIPINSERTED=ON"
RUN su - db2inst1 -c "db2set DB2_INLIST_TO_NLJN=YES"
RUN su - db2inst1 -c "db2set DB2_MINIMIZE_LISTPREFETCH=Y"
RUN su - db2inst1 -c "db2set DB2_EVALUNCOMMITTED=YES"
RUN su - db2inst1 -c "db2set DB2_FMP_COMM_HEAPSZ=65536"
RUN su - db2inst1 -c "db2set DB2_SKIPDELETED=ON"
RUN su - db2inst1 -c "db2set DB2_USE_ALTERNATE_PAGE_CLEANING=ON"

RUN su - db2inst1 -c "db2start && db2 connect to 'maxdb76' && db2 CREATE BUFFERPOOL MAXBUFPOOL IMMEDIATE SIZE 4096 AUTOMATIC PAGESIZE 32 K && db2 connect reset"
RUN su - db2inst1 -c "db2start && db2 connect to 'maxdb76' && db2 CREATE REGULAR TABLESPACE MAXDATA PAGESIZE 32 K MANAGED BY AUTOMATIC STORAGE INITIALSIZE 5000 M BUFFERPOOL MAXBUFPOOL && db2 connect reset"
RUN su - db2inst1 -c "db2start && db2 connect to 'maxdb76' && db2 CREATE TEMPORARY TABLESPACE MAXTEMP PAGESIZE 32 K MANAGED BY AUTOMATIC STORAGE BUFFERPOOL MAXBUFPOOL && db2 connect reset"
RUN su - db2inst1 -c "db2start && db2 connect to 'maxdb76' && db2 CREATE REGULAR TABLESPACE MAXINDEX PAGESIZE 32 K MANAGED BY AUTOMATIC STORAGE INITIALSIZE 5000 M BUFFERPOOL MAXBUFPOOL && db2 connect reset"
RUN su - db2inst1 -c "db2start && db2 connect to 'maxdb76' && db2 create schema maximo authorization maximo && db2 connect reset"
