# Program Analysis Note

## Tool

Here are some tools for program analysis. I strongly recommend you to implement algorithms on them.

- `LLVM`: the `Clang Static Analyzer` is a awesome tool to analyze C/C++ from AST level. And `LLVM Pass` provides a more low-level IR to analyze.
- `Soot`: tools for Java program anlysis and optimization
- `BAP`: Binary Analysis Platform. Written in OCaml. We can inspect customize IR `BIL` to analyze different binary.
- `Angr`: Binary Analysis and Symbolic Exectuion

## Project

- [Infer](https://github.com/facebook/infer): Source code static analysis based on OCaml
+ BAP based
  - [CWE-Checker](https://github.com/fkie-cad/cwe_checker): Binary analysis based on BAP
  - [CBAT TOOLS](https://github.com/draperlaboratory/cbat_tools): This project implements some algrotihm on BAP
  - Several papers related to BAP implementation: http://okmij.org/ftp/tagless-final/JFP.pdf http://www.cs.utexas.edu/~wcook/Drafts/2012/ecoop2012.pdf http://okmij.org/ftp/tagless-final/course/optimizations.html
+ LLVM based
  - [Klee](https://github.com/klee/klee): Symbolic Execution based on LLVM
  - [SVF](https://github.com/SVF-tools/SVF): Program Analysis Framework based on LLVM

## Intro

Normally, the basic parts include dataflow analysis frameword (reaching definition, interval analysis, ...), pointer analysis (andreson and steensgaard), and abstract interpretation (sign analysis). You are also encouraged to learn discrete math to understand the notations in text books.

A telegram channel related to PA: `aHR0cHM6Ly90Lm1lL2JhYnliYWJ5cHdu`.

## General Courses

- Static Analysis:
  - [UW CSE 501](https://courses.cs.washington.edu/courses/cse501/15sp/): Personally recommend, the contents are more compacted.
  - [CMU CS17-355](http://www.cs.cmu.edu/~aldrich/courses/17-355-19sp/): Some slides are missing. And the contents focus on security stuff more. Recommend to use notes here and slides from UW
  - https://homepages.dcc.ufmg.br/~fernando/classes/dcc888/ementa/
  - [IOWA CS513X](http://web.cs.iastate.edu/~weile/cs513x/): The topic is about staitc analysis but slighlty more depth.
  - [MIT 16.399](http://web.mit.edu/16.399/www/#schedule): Abstract Interpretation, in a more math way.
- Program Synthesis and Model Checking
  - [UW CSE599](https://courses.cs.washington.edu/courses/cse599a2/15wi/): Advanced Computer-Aided Reasoning for Software
  - [CMU CS15-414](https://www.cs.cmu.edu/~15414/schedule.html): Model Checking
  - [MIT 6.820](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-820-fundamentals-of-program-analysis-fall-2015/): Focused on abstract interpreter and model checking.
- SMT:
  - [UW CSE 507](https://courses.cs.washington.edu/courses/cse507/): SMT solver and apllications
  - [CMU 15816](http://www.cs.cmu.edu/~mheule/15816-f19/): Automated Reasoning and Satisfiability
- Books:
  - [SPA Book](https://cs.au.dk/~amoeller/spa/spa.pdf): Personally recommend. This book is static analysis oriented. It also provied a toy language analyszer. The psedu-code and syntax are better the PPA.
  - Principle of Program Analysis: Old school book. The syntax is abstract. Might be too hard to understand.

## Abstract Interpretation
  - Abstract Interpretation Course: [16.399 by MIT](http://web.mit.edu/16.399/www/)
  - [ABSTRACT INTERPRETATION : ‘A UNIFIED LATTICE MODEL FOR STATIC ANALYSIS OF PROGRAMS BY CONSTRUCTION OR APPROXIMATION OF FIXPOINTS](https://courses.cs.washington.edu/courses/cse501/15sp/papers/cousot.pdf): The original paper

## Dataflow Analysis
  - [Context-, Flow-, and Field-Sensitive Data-Flow Analysis using Synchronized Pushdown Systems](https://dl.acm.org/doi/pdf/10.1145/3290361?download=true): Best paper!
  - [Precise Interprocedural Dataflow Analysis via Graph Reachability](https://research.cs.wisc.edu/wpis/papers/popl95.pdf): The IFDS framework 
  
## Shape Analysis;
  - [Shape Analysis by WISC](https://research.cs.wisc.edu/wpis/papers/cc2000.pdf): Introduce shape analysis for heap
  - [Shape Analysis and Applications by UT](https://personal.utdallas.edu/~zhiqiang.lin/file/f15/shape-analysis-ch12.pdf)
  
## Porgram Slicing:
  - [Program Slicing Handbook](http://www.cs.toronto.edu/~chechik/courses06/csc2125/tip95survey.pdf): For some values your analyzer intereted, we can slice the program to find related part of the program which impacts thos values.

## Binary Analysis

- [Analyzing Memory Accesses in x86 Executables](https://research.cs.wisc.edu/wpis/papers/cc04.pdf): Introduce **value-set analysis**. This analysis uses an abstract domain for representing an over-approximation of the set of values that each data object can hold at each program point.
- [MicroX: Emulator for testing without input](https://patricegodefroid.github.io/public_psfiles/icse2014.pdf): A novel framework to emulate program without input for bug finding.
- Decompile (or Binary Translation):
  - [Reverse Compilation Techniques](http://www.phatcode.net/res/228/files/decompilation_thesis.pdf): This book is awesome, all about decompiling from frontend to backend!!!
  - [TIE: Principled Reverse Engineering of Types in Binary Programs](https://users.ece.cmu.edu/~aavgerin/papers/tie-ndss-2011.pdf): Recover types from a program based on type lattice induction.
  - [Polymorphic Type Inference for Machine Code](https://arxiv.org/pdf/1603.05495.pdf): Another thesis for type infer in binary code.
  - [mcsema](https://github.com/lifting-bits/mcsema/): Translate binary to LLVM bytecode.
  
## Formal Method

- [Software Foundation](https://softwarefoundations.cis.upenn.edu/current/index.html): Formal method all in one
  
## PA + Security

- Safety
  - [Control Flow Intergrity](https://www.microsoft.com/en-us/research/wp-content/uploads/2005/11/ccs05.pdf)
- Taint Analysis:
  - [Saluki Taint Analysis](https://www.cs.cmu.edu/~rvantond/pdfs/saluki-bar-2018.pdf)
  
## Related Stuff

### SMT Solver
- [Programming Z3](https://theory.stanford.edu/~nikolaj/programmingz3.html)
- [SAT Handbook](https://www.ics.uci.edu/%7Edechter/courses/ics-275a/winter-2016/readings/SATHandbook-CDCL.pdf)
- **The Calculus of Computation**: All about SMT foundamental.

### Abstract Machine
  Abstract Machine primarirly discuss about the exact execution of a program.
  - [Abstract machines for programming language implementation] (http://www.inf.ed.ac.uk/teaching/courses/lsi/diehl_abstract_machines.pdf)
  - [Abstracting Abstract Machines](http://matt.might.net/papers/vanhorn2010abstract.pdf): The name is so abstract
  - [Abstracting Definitional Interpreters](https://plum-umd.github.io/abstracting-definitional-interpreters/): Solid foundation of semmantics

## Some ~~Unuseful~~ Cutting-edge Research

- [Unleashing MAYHEM on Binary Code](https://users.ece.cmu.edu/~dbrumley/pdf/Cha%20et%20al._2012_Unleashing%20Mayhem%20on%20Binary%20Code.pdf): How to structure a CRS, and new methods on symbolic execution
