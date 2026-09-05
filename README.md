# Sugarcane Ontology

## Overview

The **Sugarcane Ontology** is an OWL-based semantic framework for representing, integrating and inferentially assessing global sugarcane bioeconomy systems.

The ontology integrates heterogeneous knowledge relating to sugarcane production, bagasse availability, economic and technological indicators, environmental and geographical factors, and bioeconomy development. It uses **Web Ontology Language (OWL)** and **Resource Description Framework (RDF)** standards to represent explicit facts, relationships and formally defined domain knowledge.

A central functionality of the framework is **deterministic logical inference**. Explicit facts are instantiated as individuals, datatype properties and object-property relationships. Formally defined OWL class axioms are subsequently evaluated by an OWL reasoner to derive additional class memberships and generate new knowledge that has not been explicitly asserted.

The framework currently supports both:

1. **country-level inferential assessment of sugarcane bioeconomies**; and
2. **modular scenario modelling**, demonstrated through a Sudan sugarcane cogeneration case study.

---

## Objectives

The Sugarcane Ontology was developed to:

- provide a structured semantic representation of global sugarcane bioeconomy systems;
- integrate heterogeneous economic, technological, agricultural, environmental and geographical datasets;
- represent explicit domain facts and relationships using OWL/RDF;
- generate new knowledge through deterministic logical inference;
- classify sugarcane bioeconomies using formally defined class axioms;
- support semantic interrogation and querying using SPARQL;
- provide reproducible and explainable knowledge-based assessment;
- enable modular extension of the ontology for scenario-specific applications; and
- provide a semantic foundation for future decision-support and knowledge-graph applications.

---

## Ontology Architecture

The framework follows the general reasoning architecture:

**Explicit Facts → Individuals + Data Properties + Object Properties → Formal OWL Axioms → OWL Reasoner → Inferred Knowledge**

The ontology distinguishes between:

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

The ontology therefore does not simply store country-level observations. It evaluates relationships between instantiated facts and formal class definitions to derive additional semantic knowledge.

---

## Modular Ontology Design

The Sugarcane Ontology has been designed to support **modular extension**.

Domain-specific case-study modules can extend the core semantic framework with additional:

- classes;
- individuals;
- datatype properties;
- object properties; and
- equivalent-class axioms.

This approach enables more granular scenarios to be modelled without reconstructing the core ontology.

The first modular implementation is the **Sudan Cogeneration Case Study**.

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

- `hasSugarcane_Bagasse_Production`
- `has_Cogeneration_Capacity`

Contextual relationships are represented using object properties including:

- `located_In`
- `has_Valorisation_Technology`

The current valorisation technology considered in the scenario is **cogeneration**.

---

## Cogeneration-Potential Inference

The modular ontology introduces an inferential classification hierarchy comprising:

- `High_Cogeneration_Potential`
- `Moderate_Cogeneration_Potential`
- `Low_Cogeneration_Potential`

These classes are formally defined using **Equivalent To** axioms expressed through Manchester OWL Syntax.

Only the source-derived facts are asserted for each mill. Cogeneration-potential classifications are **not manually assigned**.

Instead, the reasoning process follows:

**Published mill facts**

↓

**OWL individuals and property assertions**

↓

**Formal cogeneration-potential class definitions**

↓

**OWL reasoner**

↓

**Inferred cogeneration-potential class membership**

The resulting classification therefore represents **new inferred knowledge derived from explicitly instantiated facts and formally encoded logical relationships**.

---

**OWL reasoning asks:**

> What new semantic knowledge logically follows from the explicitly instantiated facts and formally defined relationships?

PROMETHEE II provides fine-grained numerical discrimination between alternatives, whereas the OWL framework provides semantic representation, deterministic classification and reusable inferential knowledge.

---

## Repository Structure

The repository contains the core Sugarcane Ontology and modular scenario implementations.

Key resources include:

- `sugarcane-ontology.ttl` — core Sugarcane Ontology in Turtle/RDF format;
- Sudan cogeneration ontology module — modular OWL case-study implementation;
- supporting case-study data and documentation;
- `LICENSE` — Apache License 2.0.

---

## Getting Started

### Requirements

The ontology can be explored using:

- **Protégé** or another OWL-compatible ontology editor;
- an OWL-DL reasoner;
- RDF/OWL-compatible tools and libraries; and
- optionally, a SPARQL query engine or RDF knowledge-graph platform.

### 1. Open the ontology

Load the `.ttl` ontology file into Protégé or another OWL-compatible environment.

### 2. Explore the semantic model

Browse:

- classes and class hierarchies;
- individuals;
- datatype properties;
- object properties;
- equivalent-class axioms; and
- asserted and inferred class memberships.

### 3. Run the reasoner

Run an OWL reasoner to evaluate the formally defined class axioms against the instantiated facts.

Reasoning enables the ontology to derive class memberships that have not been explicitly asserted.

### 4. Query the ontology

The ontology can be interrogated using SPARQL.

Example:

```sparql
SELECT ?entity ?property ?value
WHERE {
  ?entity ?property ?value .
}
LIMIT 10
