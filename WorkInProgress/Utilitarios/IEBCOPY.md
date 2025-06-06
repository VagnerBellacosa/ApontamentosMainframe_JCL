# JCL - IEBCOPY Utility

------

IEBCOPY is a data set utility that is used to copy or merge members between one or more partitioned data sets or partitioned data sets extended (PDSEs). The copying can be full copy or partial copy.

IEBCOPY used to create a backup of a partitioned data set into a sequential data set and to copy members from the backup into a partitioned data set. IEBCOPY automatically lists the number of unused directory blocks.



More specifically, this utility is commonly used for several purposes:

1. To copy selected (or all) members from one partitioned data set to another.
2. To copy a partitioned data set into a unique sequential format known as an unloaded partitioned data set. As a sequential data set it can be written on tape, sent by FTP, or manipulated as a simple sequential data set.
3. To read an unloaded partitioned data set (which is a sequential file) and recreate the original partitioned data set. Optionally, only selected members might be used.
4. To compress partitioned data sets (in place) to recover lost space.

------

### Example 1:

All members of input data set userid.TEST.DATA.IN are copied to output dataset userid.TEST.DATA.OUT



```
//JOBIBMKS JOB (123),'IBMMAINFRAMER',CLASS=C,MSGCLASS=S,MSGLEVEL=(1,1), //       NOTIFY=&SYSUID //* //STEP001  EXEC  PGM=IEBCOPY //SYSPRINT DD  SYSOUT=A //SYSOUT1  DD  DSNAME=userid.TEST.DATA.IN, //             DISP=SHR,UNIT=DISK, //             VOL=SER=1234 //SYSOUT2  DD  DSNAME=userid.TEST.DATA.OUT, //             DISP=(NEW,KEEP), //             SPACE=(TRK,(10,22,40),RLSE), //             UNIT=DISK,VOL=SER=1234, //SYSIN    DD DUMMY /* 
```

**Explanation:**

- SYSUT1 DD defines a PDS - userid.TEST.DATA.IN that contains 5 members (XXX, YYY, ZZZZ, AAA and BBB).
- SYSUT2 DD defines a new PDS - userid.TEST.DATA.OUT that is to be kept after the copy operation.
- Input and output data sets are identified as SYSUT1 and SYSUT2 DD statements, the SYSIN data set is not needed. So We mentioned as DUMMY dataset since there are no control statements.
- The SYSUT1 data set will be copied to the SYSUT2 data set.
- After copy operation is completed, PDS - userid.TEST.DATA.OUT will contain the all the members that are in PDS - userid.TEST.DATA.OUT

------

For example, if you wanted to copy specific members(for example - XXX and YYY) from input PDS - userid.TEST.DATA.IN. Then instead of using the DUMMY parameter on the SYSIN DD statement, you could substitute this JCL.

```
//SYSIN DD *  COPY OUTDD=SYSUT2,       INDD=SYSUT1  SELECT MEMBER=(XXX,YYY) /*
```

The SELECT statement specifies the member names to be processed, with the OUTDD and INDD parameters specifying the DD names to be used for output and input, respectively. You would have to use this JCL if you used names other than SYSUT1 and SYSUT2 for the input and output DD statements.

Restoring a partitioned data set from an unloaded copy automatically compresses (recovers lost space) the data set.

------

### Example 2: Including members of PDS in a COPY command

```
//JOBIBMKS JOB (123),'IBMMAINFRAMER',CLASS=C,MSGCLASS=S,MSGLEVEL=(1,1), //       NOTIFY=&SYSUID //* //STEP001  EXEC  PGM=IEBCOPY //SYSPRINT DD  SYSOUT=A //SYSOUT1  DD  DSNAME=userid.TEST.DATA.IN, //             DISP=SHR,VOL=SER=1234 //             UNIT=DISK1 //SYSOUT2  DD  DSNAME=userid.TEST.DATA.OUT, //             DISP=(NEW,KEEP),SPACE=(TRK,(50,20,50), RLSE) //             UNIT=DISK1, //             VOL=SER=ABC, //SYSIN    DD  *  COPY  INDD=SYSOUT1,        OUTDD=SYSOUT2  SELECT MEMBER=(XXX,YYY) /* //
```

------

### Example 3: Excluding members of PDS in a COPY command.

```
//JOBIBMKS JOB (123),'IBMMAINFRAMER',CLASS=C,MSGCLASS=S,MSGLEVEL=(1,1), //       NOTIFY=&SYSUID //* //STEP001  EXEC PGM=IEBCOPY //********************************************************* //SYSPRINT DD SYSOUT=A //SYSUT1   DD DSN=userid.JCLTEST.JCL,DISP=SHR //SYSUT2   DD DSN=userid.JCLTEST.JCLS.OTHERS, //          DISP=(NEW,CATLG,DELETE), //          SPACE=(CYL,(10,10,60),RLSE), //          DCB=(LRECL=80,RECFM=FB,BLKSIZE=800) //SYSIN    DD *  COPY INDD=SYSUT1,       OUTDD=SYSUT2  EXCLUDE MEMBER=(PGM1,PGM2,PGM3,PGM4,       PGM5,PGM6) /*
```

------

### Example 4: Renaming a member while copying

```
//JOBIBMKS JOB (123),'IBMMAINFRAMER',CLASS=C,MSGCLASS=S,MSGLEVEL=(1,1), //       NOTIFY=&SYSUID //* //STEP001  EXEC PGM=IEBCOPY //********************************************************* //SYSPRINT DD SYSOUT=A //SYSUT1   DD DSN=userid.JCLTEST.JCL,DISP=SHR //SYSUT2   DD DSN=userid.JCLTEST.JCL.OTHER, //       DISP=(NEW,CATLG,DELETE), //       SPACE=(CYL,(40,50,60),RLSE), //       DCB=(LRECL=80,RECFM=FB,BLKSIZE=800) //SYSIN DD *  COPY INDD=SYSUT1,       OUTDD=SYSUT2  SELECT MEMBER=(PGM1,PGM2,PGM3,PGM4,       PGM5,(PROGRAM6,PGM6)) /*
```

------

### Example 5: Compressing the Datasets

Datasets can be compressed together in order to move efficiently utilize the device space that they are stored on. The JCL that does this is similar to the above examples.

```
//JOBIBMKS JOB (123),'IBMMAINFRAMER',CLASS=C,MSGCLASS=S,MSGLEVEL=(1,1), //       NOTIFY=&SYSUID //* //STEP001  EXEC PGM=IEBCOPY //********************************************************* //SYSPRINT DD SYSOUT=A //SYSUT1   DD DSN=userid.JCLTEST.JCL,DISP=SHR //SYSIN DD *  COPY INDD=SYSUT1,       OUTDD=SYSUT1 /*
```

If you take another look at this JCL, you will realize that the INDD and OUTDD statements reference to the same dataset.

If you executing this job will result in all members of the partioned dataset called userid.JCLTEST.JCL being compressed together, resulting in the relese of wasted space between records and the datset members.

*If you are interested to lean more about JCL utilities, Pleae check check our [JCL Examples](https://www.ibmmainframer.com/reference/jcl-example-sample-reference-code)*