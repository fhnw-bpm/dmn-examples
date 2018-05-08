# BPM DMN Example

[![License](https://img.shields.io/:license-apache-blue.svg)](https//www.apache.org/licenses/LICENSE-2.0.html)
[![Deploy to Heroku](https://img.shields.io/badge/deploy%20to-Heroku-6762a6.svg?longCache=true)](https://heroku.com/deploy)

This example illustrates how how a DMN model, containing a DRD and two decision tables, can be called a business rule task.

#### Contents:
- [Scenario](#scenario)
- [Modelling of DRD and Decision Tables](#modelling-of-drd-and-decision-tables)
- [Modelling and Linking of BPMN and DMN](#modelling-and-linking-of-bpmn-and-dmn)
- [Maintainer](#maintainer)
- [License](#license)

## Scenario

We have a fictive process where an overall grade needs to be assessed, and a decision is made whether the overall grade is sufficient or not. The assessment will be done using two grades A and B, where B consists of two sub-grades part 1 and 2. All grades are based on the Swiss grading scheme.

[![](images/model-references-to-dmn.png)](images/model-references-to-dmn.png)

## Modelling of DRD and Decision Tables

The scenario mentioned above is realized using two decision tables. The association is modelled using DRD:

[![](images/2018-03-14_21h43_22.png)](images/2018-03-14_21h43_22.png)

Decision table one is used to assess the grade B is the preceding table before assessing the overall result:

[![](images/2018-03-14_21h43_02.png)](images/2018-03-14_21h43_02.png)

> Make sure that the variable **names** and **data types** are **consistent** with possible workflow variables (or form fields).

Decision table two does the overall assessment and takes the output (variable `gradeB`) of the preceding decision table as an input:
 
[![](images/2018-03-14_21h43_12.png)](images/2018-03-14_21h43_12.png)

> Make sure that the variable **names** and **data types** are **consistent** with the **preceding decision table** or possible workflow variables (or form fields).

## Modelling and Linking of BPMN and DMN

You may start your process with some form data. In this case, there are variables (input fields) for assessing the grades:

[![](images/2018-03-15_09h00_40.png)](images/2018-03-15_09h00_40.png)

Embed the DMN with a business rule task and reference the overall decision table by `id`. A result variable can be defined, which is, in this case, a single result, to make use of the result (decision recommendation):

[![](images/2018-03-15_09h01_34.png)](images/2018-03-15_09h01_34.png)

Further, you may want to use the decision result variable at a gateway:

[![](images/2018-03-15_09h02_41.png)](images/2018-03-15_09h02_41.png)

And finally, you may want to use the decision result variable in a form as well:

[![](images/2018-03-15_09h03_30.png)](images/2018-03-15_09h03_30.png)

## Maintainer
- [Digitalisation of Business Processes](https://github.com/digibp)

## License

- [Apache License, Version 2.0](https://github.com/DigiBP/digibp-archetype-camunda-boot/blob/master/LICENSE)