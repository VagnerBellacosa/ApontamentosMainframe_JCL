# JCL - IDCAMS Utility

------

IDCAMS stands for Integrated Data Cluster Access Method Services. IDCAMS utility is used to create, modify and delete the VSAM datasets.

IDCAMS Utility is very useful utility to manipulate VSAM datasets

A typical example of a simple use of IDCAMS is as follows:

------

**Example 1:** Allocating and Loading Data Into VSAM

```
//JOBIBMKS JOB (123),'IBMMAINFRAMER',CLASS=C,MSGCLASS=S,MSGLEVEL=(1,1), //       NOTIFY=&SYSUID //* //STEP001  EXEC PGM=IDCAMS //SYSPRINT DD * //DATAIN   DD DISP=OLD,DSN=userid.TEST.INPUT //SYSIN    DD *  DEFINE CLUSTER (           NAME (userid.TEST.VSAM) -           VOLUMES(WORK02) -           CYLINDERS(1 1) -           RECORDSIZE(72 100) -           KEYS(9 8) -           INDEXED)  REPRO INFILE(DATAIN) -        OUTDATASET(userid.DATA.VSAM) -        ELIMIT(200) /*
```

------

**Example 2:** Deleting a VSAM dataset

```
//JOBIBMKS JOB (123),'IBMMAINFRAMER',CLASS=C,MSGCLASS=S,MSGLEVEL=(1,1), //       NOTIFY=&SYSUID //* //STEP001  EXEC PGM=IDCAMS //SYSPRINT DD SYSOUT=* //SYSIN    DD *   DELETE useird.DATA.VSAM CLUSTER /*
```

*To learn more about VSAM, Go to our [VSAM Tutorial.](https://www.ibmmainframer.com/vsam-tutorial/)*

*If you are interested to lean more about JCL utilities, Pleae check check our [JCL Examples](https://www.ibmmainframer.com/reference/jcl-example-sample-reference-code)*