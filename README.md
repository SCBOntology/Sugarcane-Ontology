# Sugarcane Ontology

## Overview

The **Sugarcane Ontology** is an OWL-based semantic framework for representing, integrating and inferentially assessing global sugarcane bioeconomy systems.

The framework integrates heterogeneous knowledge relating to sugarcane production, bagasse availability, economic and technological indicators, environmental and geographical factors, bioeconomy development, and bagasse electricity deployment. It uses **Web Ontology Language (OWL)** and **Resource Description Framework (RDF)** standards to represent explicit facts, relationships and formally defined domain knowledge.

A central functionality of the framework is **deterministic logical inference**. Explicit facts are instantiated as individuals, datatype properties and, where required, object-property relationships. Formally defined OWL class axioms are subsequently evaluated by an OWL reasoner to derive additional class memberships and generate knowledge that has not been explicitly asserted.

The repository currently contains three related ontology implementations:

1. **Core Sugarcane Ontology** — country-level inferential assessment of global sugarcane bioeconomies;
2. **Global Bagasse Electricity Deployment Potential (GBEDP) Ontology** — country-level semantic representation and inference of bagasse electricity deployment and resource–deployment potential; and
3. **Sudan Cogeneration Case-Study Module** — modular facility-level scenario modelling of cogeneration potential.

---

## Objectives

The Sugarcane Ontology framework was developed to:

- provide a structured semantic representation of global sugarcane bioeconomy systems;
- integrate heterogeneous economic, technological, agricultural, environmental and geographical datasets;
- represent explicit domain facts and relationships using OWL/RDF;
- generate new knowledge through deterministic logical inference;
- classify sugarcane bioeconomies and deployment conditions using formally defined class axioms;
- support semantic interrogation and querying using SPARQL;
- provide reproducible and explainable knowledge-based assessment;
- enable modular extension for scenario-specific applications; and
- provide a semantic foundation for future decision-support and knowledge-graph applications.

---

## Ontology Architecture

The framework follows the general reasoning architecture:

**Explicit Facts → Individuals + Data Properties + Object Properties → Formal OWL Axioms → OWL Reasoner → Inferred Knowledge**

The ontologies distinguish between:

- **asserted knowledge** — facts explicitly instantiated from the evidence base; and
- **inferred knowledge** — additional class memberships and relationships logically derived by the reasoner.

This enables the framework to move beyond data representation towards **ontology-driven inferential assessment**.

---

## Core Sugarcane Ontology

The core ontology models global sugarcane bioeconomy systems at country level.

It represents knowledge relating to:

- sugarcane production;
- bagasse feedstock availability;
- economic indicators;
- technological and innovation indicators;
- agricultural resources;
- geographical context;
- bioeconomy development; and
- relevant PESTLE dimensions.

Formal class definitions expressed through OWL axioms enable countries to be inferentially classified into bioeconomy categories based on their explicitly instantiated characteristics.

The ontology therefore does not simply store country-level observations. It evaluates instantiated facts against formal class definitions to derive additional semantic knowledge.

---

## Global Bagasse Electricity Deployment Potential (GBEDP) Ontology

The **Global Bagasse Electricity Deployment Potential (GBEDP) Ontology** extends the country-level semantic approach to the assessment of **sugarcane bagasse electricity deployment**.

The ontology represents **104 sugarcane-producing countries** as named individuals of the `Sugarcane_Producer` class and integrates country-level information concerning:

- sugarcane production;
- estimated bagasse availability;
- installed bagasse electricity capacity;
- bagasse electricity deployment intensity;
- GDP per capita;
- Political Risk Index (PRI);
- Global Innovation Index (GII);
- sugarcane harvested area;
- arable land per capita; and
- CO₂ emissions per capita.

### GBEDP Datatype Properties

Country-level observations are represented using datatype properties including:

- `hasSugarcaneProduction`
- `hasEstimatedBagasse`
- `hasBagasseElectricityCapacity`
- `hasDeploymentIntensity`
- `hasGDPPerCapita`
- `hasPRI`
- `hasGII`
- `hasSugarcaneHarvestedArea`
- `hasArableLandPerCapita`
- `hasCO2EmissionPerCapita`

Missing observations are not represented as zero values.

### Bagasse Electricity Deployment Inference

The GBEDP Ontology uses OWL-DL reasoning to classify countries according to formally defined deployment conditions.

The current inferential classes include:

- `Low_Bagasse_Electricity_Deployment`
- `Moderate_Bagasse_Electricity_Deployment`
- `High_Bagasse_Electricity_Deployment`
- `High_Resource_Low_Deployment`

The deployment classes evaluate country-level deployment intensity, while `High_Resource_Low_Deployment` identifies countries that simultaneously satisfy defined conditions for substantial estimated bagasse availability and comparatively low electricity deployment.

The reasoning process follows:

**Country-level observations**

↓

**OWL country individuals and datatype-property assertions**

↓

**Formal OWL-DL class definitions**

↓

**OWL reasoner**

↓

**Inferred deployment and resource–deployment classifications**

The resulting classifications are not manually assigned. They are logically inferred from the represented country-level facts and formal class axioms.

The `High_Resource_Low_Deployment` class should be interpreted as a **screening condition** identifying a resource–deployment configuration for further investigation. It does not imply that additional electricity generation is necessarily the preferred use of the available bagasse.

---

## Modular Ontology Design

The Sugarcane Ontology framework has been designed to support **modular extension**.

Domain-specific case-study modules can extend the semantic framework with additional:

- classes;
- individuals;
- datatype properties;
- object properties; and
- equivalent-class axioms.

This enables more granular scenarios to be modelled without reconstructing the wider semantic framework.

The first facility-level modular implementation is the **Sudan Cogeneration Case Study**.

---

## Sudan Cogeneration Case-Study Module

The Sudan case study demonstrates how the Sugarcane Ontology can be extended from **country-level bioeconomy assessment to sugar-processing-facility-level inferential assessment**.

Sudan was selected because it had previously been inferred by the core Sugarcane Ontology as a **High-Potential Sugarcane Bioeconomy**. The modular case study investigates this potential at a more granular processing-mill level using published data on Sudanese sugar-processing facilities.

### Scenario

Six Sudanese sugar-processing mills are represented as individuals:

- White Nile
- Kenana
- Assalaya
- Sennar
- New Halfa
- El Guneid

The module introduces `Sudanese_Sugar_Processing_Mill` within the sugar-processing-facility hierarchy.

Published mill-level facts are represented through datatype properties including:

- `has_Sugarcane_Bagasse_Production`
- `has_Cogeneration_Capacity`

Contextual relationships are represented using object properties including:

- `located_In`
- `has_Valorisation_Technology`

The current valorisation technology considered in the scenario is **cogeneration**.

---

## Cogeneration-Potential Inference

The Sudan module introduces an inferential classification hierarchy comprising:

- `High_Cogeneration_Potential`
- `Moderate_Cogeneration_Potential`
- `Low_Cogeneration_Potential`

These classes are formally defined using **Equivalent To** axioms expressed through Manchester OWL Syntax.

Only source-derived facts are asserted for each mill. Cogeneration-potential classifications are **not manually assigned**.

The reasoning process follows:

**Published mill facts**

↓

**OWL individuals and property assertions**

↓

**Formal cogeneration-potential class definitions**

↓

**OWL reasoner**

↓

**Inferred cogeneration-potential class membership**

The resulting classifications therefore represent **new inferred knowledge derived from explicitly instantiated facts and formally encoded logical relationships**.

---

## Repository Structure

The repository contains the core ontology, the GBEDP ontology and modular scenario implementations.

Key resources include:

- `sugarcane-ontology.ttl` — core Sugarcane Ontology;
- **GBEDP `.ttl` file** — Global Bagasse Electricity Deployment Potential Ontology;
- **Sudan cogeneration `.ttl` file** — facility-level cogeneration case-study module;
- supporting case-study data and documentation; and
- `LICENSE` — Apache License 2.0.

---

## Getting Started

### Requirements

The ontologies can be explored using:

- **Protégé** or another OWL-compatible ontology editor;
- an OWL-DL reasoner;
- RDF/OWL-compatible tools and libraries; and
- optionally, a SPARQL query engine or RDF knowledge-graph platform.

### 1. Open an ontology

Load the required `.ttl` file into Protégé or another OWL-compatible environment.

### 2. Explore the semantic model

Browse:

- classes and class hierarchies;
- individuals;
- datatype properties;
- object properties, where present;
- equivalent-class axioms; and
- asserted and inferred class memberships.

### 3. Run the reasoner

Run an OWL-DL reasoner to evaluate the formally defined class axioms against the instantiated facts.

Reasoning enables the ontology to derive class memberships that have not been explicitly asserted.

### 4. Query the ontology

The ontologies can be interrogated using SPARQL.

Example:

```sparql
SELECT ?entity ?property ?value
WHERE {
  ?entity ?property ?value .
}
LIMIT 10
```

### Example: Query GBEDP country data

```sparql
SELECT ?country ?bagasse ?capacity ?deploymentIntensity
WHERE {
  ?country a :Sugarcane_Producer .
  OPTIONAL { ?country :hasEstimatedBagasse ?bagasse . }
  OPTIONAL { ?country :hasBagasseElectricityCapacity ?capacity . }
  OPTIONAL { ?country :hasDeploymentIntensity ?deploymentIntensity . }
}
ORDER BY DESC(?deploymentIntensity)
```

---

## Research Applications

The framework supports research involving:

- global sugarcane bioeconomy assessment;
- sugarcane bagasse resource assessment;
- bagasse electricity deployment analysis;
- country-level macro-factor assessment;
- PESTLE-informed semantic modelling;
- resource–deployment opportunity screening;
- facility-level cogeneration assessment;
- explainable OWL-DL reasoning;
- semantic querying and knowledge graphs; and
- extension towards alternative bagasse valorisation pathways.

The GBEDP Ontology currently uses **bagasse electricity as a reference deployment pathway**. Future extensions can incorporate additional SCB valorisation pathways, including fermentation, advanced biofuels, chemicals, materials and integrated biorefinery configurations.

---

## Licence

This repository is distributed under the **Apache License 2.0**. See the `LICENSE` file for details.
