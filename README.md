# Does the compiler or interpreter version influence the energy consumption of programming languages?

[Elisa Jimenez](https://orcid.org/0000-0002-2158-037X)  

[Alberto Gordillo](https://orcid.org/0000-0002-4742-173X)  

[Coral Calero](https://orcid.org/0000-0003-0728-4176)

[Mª Ángeles Moraga](https://orcid.org/0000-0001-9165-7144)

[Félix García](https://orcid.org/0000-0001-6460-0353)



## Abstract
Software plays a crucial role in our daily activities. Virtually all the technology we use contains software components written in a particular programming language. In this context, compilers and interpreters play an important role, as they are needed to convert the software source code into a format that can be executed by a machine. The significant influence of the programming language on the energy consumption of the resulting programs has been highlighted in some research. However, there is almost no research on the impact of the programming language compiler/interpreter version of the programming language on the energy consumption. This paper aims to fill this gap by investigating the impact of the compiler/interpreter version on the energy consumption of programs written in C, Java and Python. To do that we have developed a study that uses a hardware-based energy measurement approach to obtain the energy consumed by eight algorithms written in the three languages and run with different compiler/interpreter versions. The results do not show a trend of improvement between versions within each language, especially in terms of energy consumption. These results suggest that energy efficiency does not seem to be a major factor when developing compilers/interpreters and should therefore be prioritized.

## What is this?

This repository contains the source code of 8 algorithms implemented in 3 programming languages (Java, C and Python), which were obtained from [Computer Language Benchmark Game](https://benchmarksgame-team.pages.debian.net/benchmarksgame/).
The repository also includes the resulting empirical results and some samples of the energy records obtained from the hardware measurement instrument used in the study.


## How is structured?

This folder contains three main folders: code, empirical results and sample logs.

## Code Folder

The code folder contains 17 subfolders, one for each compiler/interpreter.  Its structure is as follows:
```Java

| <compiler/interpreter-1>
	| <algorithm-1>
		| <source>
		| Makefile
	| ...
	| <algorithm-i>
		| <source>
		| Makefile
| ...
| <compiler/interpreter-i>
	| <algorithm-1>
	| ...
	| <algorithm-i>


```

Taking the `Java` compiler as an example, this is how the folder for the `binary-trees` algorithm would look like:

```Java

| Java8
	| binary-trees
		| binarytrees.gcc-3.c
		| Makefile
	| ...

```

#### The Operations

Each algorithm sub-folder, included in a programming language folder, contains a `Makefile`.
TThis is the file which shows how to perform the 2 main operations: *(1)* **compilation** and *(2)* **execution**.

Basically, each `Makefile` **must** contain 2 rules, one for each operations:

| Rule | Description |
| -------- | -------- |
| `compile` | This rule specifies how the algorithm should be compiled in the language under consideration; Interpreted languages do not need it, so it can be left blank in these cases.
| `run` | This rule specifies how the algorithm should be executed; It is used to test whether the algorithm runs with no errors and the output is the expected. 

To illustrate this, an example of the `Makefile` for the `binary-trees` algorithm in the `C` language is:

```Makefile
compile:
	/usr/bin/gcc -pipe -Wall -O3 -fomit-frame-pointer -march=native -fopenmp -D_FILE_OFFSET_BITS=64 -I/usr/include/apr-1.0 binarytrees.gcc-3.c -o binarytrees.gcc-3.gcc_run -lapr-1 -lgomp -lm

run:
	./binarytrees.gcc-3.gcc_run 21

```
## Empirical Results Folder

The empirical results folder includes all the information on the analysis of the energy consumption of the software. The basic terminology used is as follows:
- An entity class or version corresponds to a compiler/interpreter version. 
- The test case is an algorithm implemented in a determined compiler/interpreter.
- Measurement is each of the executions of a testcase.

It is structured as follows:

```Java
|<clusters>
        |<byAlgorithm>
                |<gcc>
		       | <Algorithm>.png
                |<java>
		       | <Algorithm>.png
                |<python>
		       | <Algorithm>.png
        |<byLanguaje>
                |<gcc>
		       | gcc.png
                |<java>
		       | <java.png
                |<python>
		       | python.png
|<report>
	| <EntityClass-1>@<Algorithm-1>.xls
	| ...
	| <EntityClass-i>@<Algorithm-i>.xls
	| <img>
		| <EntityClass-1>@<Algorithm>_<Device-1>.png
		| ...
		| <EntityClass-i>@<Algorithm>_<Device-i>.png
		|
		| <EntityClass-1>@<Algorithm>_dut-1.png
		| ...
		| <EntityClass-i>@<Algorithm>_dut-i.png

| ScatterGraph.pdf
| PowerNormalityC.pdf
| PowerNormalityJava.pdf
| PowerNormalityYthon.pdf
| TimeNormalityC.pdf
| TimeNormalityJava.pdf
| TimeNormalityYthon.pdf
| Statistics_C.pdf
| Statistics_Java.pdf
| Statistics_Python.pdf

| testcases_total.xls

| versions_spearman.xls
| versions_total.xls

```
To facilitate the comparison of information, the file "testcases_total" contains one sheet for each statistical value of all test cases. These statistical values are:
Consumption average without baseline, Consumption average (with baseline), Baseline, Power average without baseline, Power average (with baseline) and Standard deviation among measurments 

![](resources/testcases_total_example.PNG)

In the same way as the "testcase_total" document, the "versions_total" document contains the statistical values for each Entity Class.

![](resources/versions_total_example.PNG)

ScatterGraph.pdf contains the scatter plots of time and energy consumption of the software entities separated by programming language.

Finally, the validation tests of the statistics:
- PowerNormalityC.pdf, PowerNormalityJava.pdf and PowerNormalityPython.pdf, contain the Kolmogorov-Smirnov and Shapiro-Wilk tests for the power of the C, Java and Python test cases respectively.
- TimeNormalityC.pdf, TimeNormalityJava.pdf and TimeNormalityYthon.pdf, contain the Kolmogorov-Smirnov and Shapiro-Wilk tests for the time of the C, Java and Python test cases respectively.
- Statistics_C.pdf, Statistics_Java.pdf and Statistics_Python.pdf contain all test for the energy consumption of the C, Java and Python test cases respectively.

### Clustering folder
Within the clustering folder there are two subfolders containing the cluster images for each algorithm and language. There is also the file scriptR.txt with the R code to to generate the clusters.

### Report Folder
The report folder contains 225 Excel files containing the analysis data. One for each test case named `<EntityClass>@<Algorithm>`. It also contains two files "testcases_total" and "versions_total" with the summary of the test case and version information respectively.
As an example, the following images show the information of a test case.

The first image shows all the information of a measurement.
![](resources/measurement_example.PNG)

The second image shows all the information of a test case.
![](resources/testcase_example.PNG)

#### Img folder
The img folder contains the graphs of the overall consumption in the execution of each measurement performed. It also includes the box plots of each device for each test case and for each version of compiler/interpreter.

## Sample Logs Folder
This folder contains an example of a log, to illustrate the raw data generated by the EET measurement instrument. 
- The json file contains the measurement information of the entity class.
- Each line of 3RunC7_847_EX are the values obtained for id, time, monitor and DUT
- Each line of 3RunC7_847_IN are the values obtained for id, time, HDD(),HDD(2), Graphics card(1), Graphics card(2),Processor(1) and Processor(2).
DUT hardware components have two values because they have two sensors connected, the result of the DUT hardware component is the sum of the two values.

Note: The rest of the logs of this study are not included in the repository for practical reasons, due to their large size.

## Contacts and References

[Green Team Alarcos](https://greenteamalarcos.uclm.es/)

[The Computer Language Benchmark Game](https://benchmarksgame-team.pages.debian.net/benchmarksgame/)

