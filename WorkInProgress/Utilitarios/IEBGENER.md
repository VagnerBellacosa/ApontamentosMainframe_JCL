# JCL - IEBGENER Utility

------

The IEBGENER utility is a copy program. One of its many uses is to copy a sequential data set, a member of a partitioned data set (PDS) or PDSE.

IEBGENER also can filter data, change a data set's logical record length (LRECL) and block size (BLKSIZE), and generate records.

This is most commonly used utility programs. It is used to copy one sequential file to another.

------

### Rules for Coding:



- Original dataset name must be specified.
- Destination dateset name must be specified.
- Attributes of both datasets(such as record format and logic record length), must be the same



------

A following JCL executes the IEBGENER program.

**Example 1:** COPY PS dataset.

```
//JOBIBMKS JOB (123),'IBMMAINFRAMER',CLASS=C,MSGCLASS=S,MSGLEVEL=(1,1), //       NOTIFY=&SYSUID //STEP001  EXEC PGM=IEBGENER //SYSPRINT DD SYSOUT=A //SYSUT1   DD DSN=userid.FILE1.INPUT,DISP=SHR //SYSUT2   DD DSN=userid.FILE2.OUTPUT, //        DISP=(NEW,CATLG,DELETE),UNIT=DISK1, //        SPACE=(TRK,20,10),RLSE), //SYSIN    DD DUMMY //
```

The utility IEBGENER is exeuted and the output if directed to the device destinated by A. Traditionally, this the line printer.

IEBGENER requires four DD(data definition) statements with the DD names shown in the above example,

**Explanation:**

- The SYSIN DD statement is used as a DUMMY dataset since there are no control statements. When IEBGENER encounters this SYSIN statment, it immediately gives an end-of-file indication
- The SYSPRINT statement is for messages from IEBGENER.
- The SYSUT1 statement is for input file. The name of the file to be copied is userid.FILE1.INPUT.
- The SYSUT2 statement is for output file, which will be a copy of the file identified in SYSUT1. This file is called userid.FILE2.OUTPUT.

*If you are interested to lean more about JCL utilities, Pleae check check our [JCL Examples](https://www.ibmmainframer.com/reference/jcl-example-sample-reference-code)*