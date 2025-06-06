# JCL - IEFBR14 Utility

------

The IEFBR14 program is nothing more than a null program. Its name is derived from an assemble language instruction that is used to exit a procedure or program. and this is exactly what is does. It executed a single statment which specifies the end of the program.

The utility program IEFBR14 performs no action other than return a completion code of 0; however, "running" this utility invokes other system components that perform useful tasks.

1. Allocate/create datasets
2. Delete datasets
3. Uncatlog Datasets
4. Catalog Datasets
5. Setting return code to zero

The IEFBR14 program is not connsidered by IBM to be a utility program. However, it is used like a utility in that not do anything by itself.

Since IEFBR14 is a do nothing program, it can also be used to check the syntax of your JCL without affecting any datasets.

We mostly use IEFBR14 utility to create or delete the PS(partition dataset) file.

Let us see few examples below.

------

**Example 1:** Allocate/Create empty PS dataset.

```
//JOBIBMKS  JOB (123),'IBMMAINFRAMER',CLASS=C,MSGCLASS=S,MSGLEVEL=(1,1), //       NOTIFY=&SYSUID //* //STEP001  EXEC PGM=IEFBR14 //SYSPRINT DD SYSOUT=* //SYSOUT   DD SYSOUT=* //SYSDUMP  DD SYSOUT=* //DD01     DD DSN=userid.TEST.PSFILE, //            DISP=(NEW,CATLG,DELETE), //            SPACE=(TRK,(12,33),RLSE),UNIT=SYSDA, //            DCB=(DSORG=PS,RECFM=FB,LRECL=80,BLKSIZE=800) //*
```

**OUTPUT:** This job will create the PS(userid.TEST.PSFILE) with defined parameter value.

**Explanation:**

- **SYSPRINT** - This is optional DD statement. It is used by utility programs for their output.
- **SYSOUT** - This is optional DD statement. This specifies system defined dd name used for file status codes, system abend codes information and output of the display statement.
- **SYSDUMP** - This is optional DD statement. It is used by the system for dumping when an abend occurs that causes a system dump.
- **DD01** - This DD statment specifies PS dataset attributes for creation.

Mostly we don't add optional DD statment in the JCL. See below JCL without optional DD statement.

```
//JOBIBMKS  JOB (123),'IBMMAINFRAMER',CLASS=C,MSGCLASS=S,MSGLEVEL=(1,1), //       NOTIFY=&SYSUID //* //STEP001  EXEC PGM=IEFBR14 //DD01     DD DSN=userid.TEST.PSFILE, //            DISP=(NEW,CATLG), //            SPACE=(TRK,(12,33),RLSE),UNIT=SYSDA, //            DCB=(DSORG=PS,RECFM=FB,LRECL=80,BLKSIZE=800) //*
```

------

**Example 2:** Delete PS dataset.

```
//JOBIBMKS JOB (123),'IBMMAINFRAMER',CLASS=C,MSGCLASS=S,MSGLEVEL=(1,1), //       NOTIFY=&SYSUID //* //STEP001  EXEC PGM=IEFBR14 //SYSPRINT DD SYSOUT=* //SYSOUT   DD SYSOUT=* //SYSDUMP  DD SYSOUT=* //DD01     DD DSN=userid.TEST.PSFILE, //            DISP=(OLD,DELETE,DELETE) //*
```

**OUTPUT:** This job will delete the PS(userid.TEST.PSFILE) dataset.

**Explanation:**

- **SYSPRINT** - This is optional DD statement. It is used by utility programs for their output.
- **SYSOUT** - This is optional DD statement. This specifies system defined dd name used for file status codes, system abend codes information and output of the display statement.
- **SYSDUMP** - This is optional DD statement. It is used by the system for dumping when an abend occurs that causes a system dump.
- **DD01 DD** - This is optional DD statement. This specifies PS dataset with DISP for deletion (DISP=(OLD,DELETE,DELETE)).

As discussed above, Mostly we don't add optional DD statment in the JCL. See below JCL without optional DD statement.

```
//JOBIBMKS JOB (123),'IBMMAINFRAMER',CLASS=C,MSGCLASS=S,MSGLEVEL=(1,1), //       NOTIFY=&SYSUID //* //STEP001  EXEC PGM=IEFBR14 //DD01     DD DSN=userid.TEST.PSFILE, //            DISP=(OLD,DELETE) //*
```

------

**Example 3:** Uncatalog dataset.

```
//JOBIBMKS JOB (123),'IBMMAINFRAMER',CLASS=C,MSGCLASS=S,MSGLEVEL=(1,1), //       NOTIFY=&SYSUID //* //STEP001  EXEC PGM=IEFBR14 //DD01     DD DSN=userid.TEST.PSFILE, //            DISP=(OLD,UNCATLG) //*
```

In this example, the IEFBR14 program is used to uncatalog the dataset called userid.TEST.PSFILE

------

**Example 4:** Catalog dataset.

```
//JOBIBMKS JOB (123),'IBMMAINFRAMER',CLASS=C,MSGCLASS=S,MSGLEVEL=(1,1), //       NOTIFY=&SYSUID //* //STEP001  EXEC PGM=IEFBR14 //DD01     DD DSN=userid.TEST.PSFILE, //            DISP=(OLD,CATLG) //*
```

In this example, the IEFBR14 program is used to catalog the dataset called userid.TEST.PSFILE