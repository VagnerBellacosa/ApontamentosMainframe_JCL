| Reusable JCL collection |
| ----------------------- |
|                         |

![img](https://www.ibm.com/docs/de/zosbasics/com.ibm.zaddinfo.doc/dblue_rule.gif)The JOB statement is the first control statement in a job. It marks the beginning of a job and also specifies the name of the job.

The JOB statement also might provide details and parameters that apply to all job steps within the job, such as accounting information and conditions for job termination. It also may contain any comments that help describe the statement.



## This JCL example contains one JOB statement:



//JOBNUM1 JOB  504,SMITH  PAYROLL 

`//STEP1   EXEC PGM=PROGRAM1` 

`//DD1     DD   DSN=HLQ.OUTPUT` 

`//``

The name field contains the job name "JOBNUM1". In every JOB statement, the name field contains a one- through eight-character name that identifies the job so that other JCL statements or the operating system can refer to it. Be sure to assign a unique name for each job.

The parameter field defines information that applies to the entire job, contains an accounting number (504) and the programmer's name (SMITH). These parameters are positional and must appear in the order shown.

The comment field contains PAYROLL.

The end of a job is indicated by a null statement, which consists of only two forward slashes (//), or is marked by the beginning of another JOB statement. In this sample, JOBNUM1 ends with a null statement



.**[JCL JOB statements: Positional and frequently used parameters](https://www.ibm.com/docs/de/zosbasics/com.ibm.zos.zjcl/zjclc_jclJOBstmtfreqused.htm)** 

In addition to the two positional parameters (job accounting information and programmer name), the JOB statement also may contain over 20 keyword parameters. But you'll most often use only this handful.

**Parent topic:**

[Basic JCL concepts](https://www.ibm.com/docs/de/zosbasics/com.ibm.zos.zjcl/zjclc_basicjclconcepts.htm)

**Related concepts**

 [JCL DD statements: Identify program libraries with JOBLIB or STEPLIB](https://www.ibm.com/docs/de/zosbasics/com.ibm.zos.zjcl/zjclc_jclxxxlibDDstmts.htm)