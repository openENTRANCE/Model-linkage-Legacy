# openENTRANCE: Model linkage mappings and definitions

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

## Model linkage mappings and definitions

<p align="center">
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

## 1. Model
This dictionary of model can be linked through this exchange format. Given the intended openness of the exchange format, models inside and outside the openENTRANCE consortium are welcome. A brief description of the model is provided in the next link. Model name and version will be specified as follows:

> openTEPES|1.6.12

More details could be found [here](Model/ModelDictionary.md).


## 2. Scenario
The analysis/case scenario name describes the type of analysis to be carried out and its context, as used in the openENTRANCE project. For example, scenario **GreenGrowth** or **Distributed PV all over Europe** or **Centralized utility-scale PV in southern Europe** can be possible names of scenarios. ***Any name is valid here***.

This field can be extended to refer to the fact that the scenario considered is stochastic/random to account, for example, for the spatial correlation of wind/solar generation, or demand, in different regions/countries. Stochastic/random data are usually time dependent.
Thus, stochastic/random scenario names can be used. For example, possible names can be:

> Distributed PV all over Europe|Scen001

Where the data given belong to the random scenario **Scen001** of the analysis scenario **Distributed PV all over Europe**.


More details can be found [here](Scenario/ScenarioDictionary.md).


## 3. Region
It refers to the geographical mapping of the variable. For that purpose, a definition of the set of regions is proposed by combining the possible geographical levels, in the order defined next, using pipes (|).
We propose the following levels for the definition of the locations to be considered:

* Continent: Europe
* Region: Continental_Central_East (CCE)
* Country: countries (DE.Germany, FR.France, etc.)
* Area (NUTS 1): large regions inside a country
* Zone (NUTS 2): smaller regions inside a country
* Node (NUTS 3): physical (electrical, gas) nodes or provinces in the corresponding global grid
* District: municipal utility district
* Community: city block
* EndUser: end user
* Circuit: circuit/link of a line (electric or gas)

A **greater than** sign (>) is used to express the direction of links. For example, **node1 > node2 > circuit1** indicates that we refer to circuit1 connecting node1 and node2, from the former to the latter. Bidirectional data must be declared separately for each direction but using only the greater sign.
Names separated by dots (.), as DE.Germany for example, means that they are synonyms, and this is defined in the repository. This allows easier data conversion among the different models and users.
Besides, to enable the geographical aggregation/disaggregation, any value of a certain column must belong to the category defined in the previous one on the left, i.e., all the countries must be included in a region, all the areas in a country, and so on.
For example, possible values can be:

*	Munich where only the city of Munich is defined.
*	DE where only the country is defined
*	Munich>Salzburg>AC01 defines the electrical circuit AC01 between Munich and Salzburg



More details can be found [here](Scenario/ScenarioDictionary.md).
