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

More details can be found [here](Model/README.md).


## 2. Scenario
The analysis/case scenario name describes the type of analysis to be carried out and its context, as used in the openENTRANCE project. For example, analysis/case scenario **GreenGrowth** or **Distributed PV all over Europe** or **Centralized utility-scale PV in southern Europe** can be possible names. ***Any name is valid here***.

This field can be extended to refer to the fact that the analysis/case scenario considered is stochastic/random to account, for example, for the spatial correlation of wind/solar generation, or demand, in different regions/countries. Stochastic/random data are usually time dependent.
Thus, stochastic/random scenario names can be used. For example, possible forms can be used:

> Distributed PV all over Europe|Scen001

Where the data given belong to the random scenario **Scen001** of the analysis/case scenario **Distributed PV all over Europe**.


More details can be found [here](Scenario/README.md).


## 3. Region
It refers to the geographical mapping of the variable. For that purpose, a definition of the set of regions is proposed by combining the possible geographical levels, in the order defined next, using pipes (**|**). Note that the [NUTS 2021 Nomenclature](https://ec.europa.eu/eurostat/web/nuts/background) is considered.
We propose the following levels for the definition of the locations to be considered:

* Continent: Europe
* Region: Continental-Central-East (CCE)
* Country: countries (Germany, France, etc.)
* Area (NUTS 1): large regions inside a country
* Zone (NUTS 2): smaller regions inside a country
* Node (NUTS 3): physical (electrical, gas) nodes or provinces in the corresponding global grid
* District: municipal utility district
* Community: city block
* EndUser: end user
* Circuit: circuit/link of a line (electric or gas)

A **greater than** sign (>) is used to express the direction of links. For example, **node1 > node2 | circuit1** indicates that we refer to circuit1 connecting node1 and node2, from the former to the latter. Bidirectional data must be declared separately for each direction but using only the greater sign.
For example, possible values can be:

>	Germany|DE21H|Node001

Where only the **Node001** that belongs to the city of **München** through the code *DE21H* (and München is located in the zone of **Oberbayern**) is defined.

>	Germany|DE21

Where only the zone of **Oberbayern** is defined through the code *DE21*.

>	Germany|DE2

Where only the area of **Bayern** is defined through the code *De2*.
<!--
>	CCE|DE

Where only the country is defined

>	CCE

Where only the region is defined -->

>	DE21H>AT323|AC01

Defines the electrical circuit **AC01** between **Munich** (NUTS code: *DE21H*) and **Salzburg-und-Umgebung** (NUTS code: *AT323*).
For the geographical links (such as electrical circuits), it is important to connect locations at the same level. I.e. NUTS 1 with NUTS 1 or district with district.



More details can be found [here](Region/README.md).

## 4. Variable
It defines the nature/features of the variable whose value is provided. For that purpose, we propose to set up the **Variable** by specifying values related to the following data types and combining these, in the order provided next, using pipes (|).
We propose to consider the following levels of variables:

*	Category: Agriculture, Demography, Economy, Emissions, Employment, Energy, EnergyService, GDP, Investment, Land, Trade, Price, ValueAdded
*	NonEnergy: Crops, Livestock, Forest, Pasture, BuiltUpArea, OtherLand, Residues
*	Energy: FinalEnergy, PrimaryEnergy, SecondaryEnergy
*	TypeOfSecondaryEnergy: Electricity, Heat, Transport
*	TypeOfFinalEnergy: Commercial, Industry, Other, Residential, TransportationFreight, TransportationPassenger
*	Technology: The list of **technologies** to consider will be easily accessible to modelers, who could develop their data processing tools taking it into account.
*	Generator: name of the generator
*	Variable: The list of **variables** to consider will be easily accessible to modelers, who could develop their data processing tools taking it into account. Each variable can be mapped to those models that can use the former as an input or output.

<!-- Names separated by dots (.), as Agriculture.AFOLU.AFOFI for example, mean that all these names are synonyms. This is to be defined in the repository. -->
We set here some guidelines to ensure consistency across the variable names to be defined:

* Do not include spaces before and after a (**|**) sign, but add a space between words
* All words must be capitalized (except for **and**,**w/**, **w/o**)
* Do not use abbreviations (e.g, **PHEV**) unless strictly necessary
 add hierarchy levels where it might be useful in the future, e.g, rather than having **Plugin-Hybrid Electric Vehicle**, use **Electric Vehicle|Plugin-Hybrid**
* Do not use statistical-operation-abbreviations (**min**, **max**, **avg**) but always spell out the word
* Do not include words like **level** or **quantity** in the variable (it should be clear anyway from the context)



Some examples of variables to be considered follow:

>	 PowerCapacity|GasTurbine|CombinedCycle|Arcos3

It refers to the capacity of a generating unit.
This example introduces 1) The association of **Arcos3** (a Spanish combined cycle gas turbine - technology level 3) to the technology level 1 (Gas Turbine) and technology level 2 (combined cycle), and, 2) To define its power capacity (e.g., 480 MW).
The order defined above:

> Variable|Technology Level 1|Technology Level 2|Technology Level 3

First, the variable (e.g., Capacity, EmissionRate, LinearVariableCost, etc.) is defined. After that, the order goes from wider (technology level 1) to smaller (technology level 3).
The following expression could be used to define the entire **combined cycle gas turbine**:

>	 PowerCapacity|GasTurbine|CombinedCycle

The following expression could be used to define the total **combined cycle gas turbine** plus **open cycle gas turbine**:

>	 PowerCapacity|GasTurbine

And, the total power plant capacity of the power system (assuming this is an electricity-only model - to be generic in a multi-commodity setting)

>	 PowerCapacity

In addition, electricity demand can be defined as follows:

> PowerDemand

But it has to be in a companion of a definition of the region.
For example:

>	Germany|DE21H|Node001

More details can be found [here](Variable/README.md).
