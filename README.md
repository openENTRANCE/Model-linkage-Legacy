# openENTRANCE: model linkage mappings and definitions

Copyright 2020 openENTRANCE consortium

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

     http://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.

## Model linkage mappings and definitions <p align="right">
  <img width="195" height="195" src="https://github.com/openENTRANCE/model-linkage/blob/master/assets/Models.png">
</p>

This repository aims to share the mapping of some models to be used in [openENTRANCE](https://openentrance.eu/) is based on these three principles:

* Define the hierarchical relations among the different concepts used for variable and region domains of the **common data format**
* Define a set of consistent names, definitions, and meanings for the different concepts

The first rule is to define a single set of pre-defined reserved words to be used in the data-exchange platform. A reserved word can’t be used for two different concepts in the platform.
The **common data format** are thought to be valid both for dynamic data, changing over time (e.g., hourly data), and static data (e.g., yearly data). Besides, we will need to represent both deterministic data (those for which there is certainty over the evolution of the corresponding data) and stochastic data, which depend on uncertain scenarios. 
Within the **common data format**, there are six dimensions:

1.	Model
2.	Scenario
3.	Region
4.	Variable
5.	Unit
6.	Subannual

Next, we describe in detail the information to be provided in each dimension. This definition must be exhaustive (cover all the data in the models considered) and avoid duplicities that might lead to inconsistencies. That is, all data should be defined once and just once.


|  __Models__  | 
|--------------|
| EMPIRE       |
| e-Transport  |
| EXIOMOD      |
| FanSi        |
| FRESH:COM    |
| GENeSYS-MOD  |
| HERO         |
| openTEPES    |
| OSCARS       |
| Plan4EU      |
| REMES-EU     |
| SCOPE-SD     |
