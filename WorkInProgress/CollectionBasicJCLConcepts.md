[Todos os produtos](https://www.ibm.com/docs/de/products)[Habilidades básicas do z/OS](https://www.ibm.com/docs/de/zos-basic-skills)



# Conceitos básicos de JCL  Coleção JCL reutilizável  



![img](https://www.ibm.com/docs/de/zosbasics/com.ibm.zos.zjcl/zoshead.gif) **Coleção JCL reutilizável** ![img](https://www.ibm.com/docs/de/zosbasics/com.ibm.zos.zjcl/zosspot.gif)

| [Tópico anterior](https://www.ibm.com/docs/de/zosbasics/com.ibm.zos.zjcl/zjclt_smpldelVSAMclusters.htm) \| [Próximo tópico](https://www.ibm.com/docs/de/zosbasics/com.ibm.zos.zjcl/zjclc_jclJOBstmt.htm) \| [Conteúdo](https://www.ibm.com/docs/de/zosbasics/com.ibm.zos.zjcl/toc.htm) \| [Glossário](https://www.ibm.com/docs/de/zosbasics/com.ibm.zglossary.doc/zglossary.html) \| [Contato z/OS](https://www.ibm.com/docs/de/zosbasics/com.ibm.zcontact.doc/webqs.html) \| [PDF](https://www.ibm.com/docs/de/zosbasics/com.ibm.zos.zjcl/zjcl_book.pdf)  ![img](https://www.ibm.com/docs/de/zosbasics/com.ibm.zaddinfo.doc/c.gif) |
| ------------------------------------------------------------ |
|                                                              |

# 

![img](https://www.ibm.com/docs/de/zosbasics/com.ibm.zaddinfo.doc/dblue_rule.gif)A linguagem de controle de tarefas (JCL) é um conjunto de instruções que você codifica para informar ao sistema operacional z/OS® sobre o trabalho que você deseja que ele execute. Embora esse conjunto de instruções seja bastante grande, a maioria das tarefas pode ser executada usando um subconjunto muito pequeno. Aprenda sobre instruções e parâmetros JCL essenciais e mais frequentemente usados, bem como técnicas de codificação.

As instruções JCL informam ao z/OS onde encontrar a entrada apropriada, como processar essa entrada (ou seja, qual programa ou programas executar) e o que fazer com a saída resultante.

Todos os trabalhos usam três tipos principais de instruções JCL:

Uma declaração JOB para identificar a unidade de trabalho que o sistema operacional deve executar

Uma ou mais instruções EXEC , dependendo do número de etapas do trabalho dentro do trabalho

Uma ou mais instruções DD para identificar os conjuntos de dados de entrada e saída

**[Instruções JCL: O que a instrução JOB faz?](https://www.ibm.com/docs/de/zosbasics/com.ibm.zos.zjcl/zjclc_jclJOBstmt.htm)** 

A instrução JOB é a primeira instrução de controle em um job. Ela marca o início de um job e também especifica o nome do job.

**[Instruções JCL: O que a instrução EXEC faz?](https://www.ibm.com/docs/de/zosbasics/com.ibm.zos.zjcl/zjclc_jclEXECstmt.htm)** 

A instrução EXEC marca o início de uma etapa dentro de uma tarefa e especifica o nome de um programa ou procedimento catalogado a ser executado.

**[Instruções JCL: O que a instrução DD faz?](https://www.ibm.com/docs/de/zosbasics/com.ibm.zos.zjcl/zjclc_jclDDstmt.htm)** 

Instruções de definição de dados (DD) definem os conjuntos de dados que um programa ou procedimento usa quando é executado. Você deve codificar uma instrução DD para cada conjunto de dados usado ou criado em uma etapa de tarefa.

| Cursos de 30 minutos sobre z/OS                              |
| ------------------------------------------------------------ |
| ![img](https://www.ibm.com/docs/de/zosbasics/com.ibm.zaddinfo.doc/dblue_rule.gif)[Aprenda em 30 minutos ou menos](https://www.ibm.com/docs/de/zosbasics/com.ibm.zos.zcourses/zcourses_courseintro.htm) |

[Cursos básicos de hardware de mainframe](https://www.ibm.com/docs/de/zosbasics/com.ibm.zos.zcourses/zcourses_hwintro.htm)

[Cursos do Interactive System Productivity Facility (ISPF)](https://www.ibm.com/docs/de/zosbasics/com.ibm.zos.zcourses/zcourses_ispfintro.htm)

[Curso básico de linguagem de controle de tarefas (JCL)](https://www.ibm.com/docs/de/zosbasics/com.ibm.zos.zcourses/zcourses_jclintro.htm)



### Interactive System Productivity Facility (ISPF) courses

#### 30 minute courses on z/OS

These courses introduce ISPF, a menu-driven interface for user interaction with a z/OS® system. ISPF includes a text editor and browser, and functions for locating and listing files and performing other utility functions. Many z/OS professionals use ISPF exclusively for performing work on z/OS.

Where appropriate, the courses include simulations of basic tasks, so working with ISPF on a live z/OS system is not a requirement for completing the courses.

Each course takes no more than 30 minutes to complete.

- Basics of ISPF and data sets

  - Main features of ISPF

    [Course](http://publibz.boulder.ibm.com/zoslib/books/tutorials/ispfmain/index.htm) | [PDF](https://www.ibm.com/docs/de/zosbasics/com.ibm.zos.zcourses/zcourses_ispfmain_book.pdf)

  - The ISPF PDF Primary Options Menu

    [Course](http://publibz.boulder.ibm.com/zoslib/books/tutorials/ispfpdf/index.htm) | [PDF](https://www.ibm.com/docs/de/zosbasics/com.ibm.zos.zcourses/zcourses_ispfpdf_book.pdf)

  - ISPF data set basics

    [Course](http://publibz.boulder.ibm.com/zoslib/books/tutorials/ispfdsbasics/index.htm) | [PDF](https://www.ibm.com/docs/de/zosbasics/com.ibm.zos.zcourses/zcourses_ispfdsbasics_book.pdf)

  - Working with data sets

    [Course](http://publibz.boulder.ibm.com/zoslib/books/tutorials/ispfworkds/index.htm) | [PDF](https://www.ibm.com/docs/de/zosbasics/com.ibm.zos.zcourses/zcourses_ispfworkds_book.pdf)

- Editing with ISPF

  - Using the ISPF editor

    [Course](http://publibz.boulder.ibm.com/zoslib/books/tutorials/ispfeditor/index.htm) | [PDF](https://www.ibm.com/docs/de/zosbasics/com.ibm.zos.zcourses/zcourses_ispfeditor_book.pdf)

  - Using ISPF editing commands

    [Course](http://publibz.boulder.ibm.com/zoslib/books/tutorials/ispfcommands/index.htm) | [PDF](https://www.ibm.com/docs/de/zosbasics/com.ibm.zos.zcourses/zcourses_ispfcommands_book.pdf)

  - Setting ISPF editing modes

    [Course](http://publibz.boulder.ibm.com/zoslib/books/tutorials/ispfmodes/index.htm) | [PDF](https://www.ibm.com/docs/de/zosbasics/com.ibm.zos.zcourses/zcourses_ispfmodes_book.pdf)

  - Searching data sets with the ISPF editor

    [Course](http://publibz.boulder.ibm.com/zoslib/books/tutorials/ispfsearch/index.htm) | [PDF](https://www.ibm.com/docs/de/zosbasics/com.ibm.zos.zcourses/zcourses_ispfsearch_book.pdf)

- Using ISPF utilities

  - Using the ISPF library utility

    [Course](http://publibz.boulder.ibm.com/zoslib/books/tutorials/ispflibu/index.htm) | [PDF](https://www.ibm.com/docs/de/zosbasics/com.ibm.zos.zcourses/zcourses_ispflibu_book.pdf)

  - Using the ISPF data set utility

    [Course](http://publibz.boulder.ibm.com/zoslib/books/tutorials/ispfdsu/index.htm) | [PDF](https://www.ibm.com/docs/de/zosbasics/com.ibm.zos.zcourses/zcourses_ispfdsu_book.pdf)

  - Using the ISPF move/copy utility

    [Course](http://publibz.boulder.ibm.com/zoslib/books/tutorials/ispfmcu/index.htm) | [PDF](https://www.ibm.com/docs/de/zosbasics/com.ibm.zos.zcourses/zcourses_ispfmcu_book.pdf)

  - Using the ISPF dslist utility

    [Course](http://publibz.boulder.ibm.com/zoslib/books/tutorials/ispfdslu/index.htm) | [PDF](https://www.ibm.com/docs/de/zosbasics/com.ibm.zos.zcourses/zcourses_ispfdslistu_book.pdf)

  - Using the ISPF compare and search utilities

    [Course](http://publibz.boulder.ibm.com/zoslib/books/tutorials/ispfcsu/index.htm) | [PDF](https://www.ibm.com/docs/de/zosbasics/com.ibm.zos.zcourses/zcourses_ispfcsu_book.pdf)

    
