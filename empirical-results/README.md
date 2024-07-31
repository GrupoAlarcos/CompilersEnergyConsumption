## Empirical Results Folder

The empirical results folder includes all the information on the analysis of the energy consumption of the software. The basic terminology used is as follows:
- An entity class or version corresponds to a compiler/interpreter version. 
- The test case is an algorithm implemented in a determined compiler/interpreter.
- Measurement is each of the executions of a testcase.

It is structured as follows:

```Java
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

| coorelations.pdf
| ScatterGraph_of_time_and_consumption.pdf
| testcases_mann-whitney.xls
| testcases_spearman.xls
| testcases_total.xls

| versions_mann-whitney.xls
| versions_spearman.xls
| versions_total.xls

```
To facilitate the comparison of information, the file "testcases_total" contains one sheet for each statistical value of all test cases. These statistical values are:
Consumption average without baseline, Consumption average (with baseline), Baseline, Power average without baseline, Power average (with baseline) and Standard deviation among measurments 

![](resources/testcases_total_example.PNG)

In the same way as the "testcase_total" document, the "versions_total" document contains the statistical values for each Entity Class.

![](resources/versions_total_example.PNG)

Finally, the validation tests of the statistics can be found in testcases__mann-whitney and versions_mann-whitney. It contains the Kolmogorov-Smirnov and Mann-Whitney tests for all comparisons of time, power and consumption.

![](resources/comparison_example.PNG)

### Report Folder
The report folder contains 225 Excel files containing the analysis data. One for each test case named `<EntityClass>@<Algorithm>`. It also contains two files "testcases_total" and "versions_total" with the summary of the test case and version information respectively.
As an example, the following images show the information of a test case.

The first image shows all the information of a measurement.
![](resources/measurement_example.PNG)

The second image shows all the information of a test case.
![](resources/testcase_example.PNG)


#### Img folder
The img folder contains the graphs of the overall consumption in the execution of each measurement performed. It also includes the box plots of each device for each test case and for each version of compiler/interpreter.