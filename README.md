# DNDP Road Network Datasets

Road-network datasets used to investigate how a small number of strategically selected new links can improve the structural properties of existing transport networks.

This repository contains the **`Networks/` dataset directory only**. Optimization outputs and analysis code are not included.

## Dataset Overview

The collection consists of **81 OpenStreetMap-derived road-network extracts** spanning **53 countries and territories**. The extracts represent cities, towns, or urban districts; a folder name does not necessarily represent an entire municipal road system.

In the associated research, the processed networks are modeled as simple, undirected, unweighted graphs. The analyzed graphs contain approximately:

- **372–947 nodes**
- **502–1,317 undirected links**
- **1,687–5,810 candidate link additions**

The networks provide a geographically diverse dataset for investigating structural network improvements through discrete network design.

## Repository Structure

```text
DNDP-Networks/
└── Networks/
    ├── Abilene/
    ├── Acatlan/
    ├── Andorra_la_Vella/
    ├── Baños_de_Agua_Santa/
    ├── Banska_Štiavnica/
    ├── Bar_Harbor/
    ├── Bardejov/
    ├── Barichara/
    ├── Bayeux/
    ├── Berat/
    ├── ...
    └── Xizhou/
```

Each location has its own subdirectory under `Networks/`.

Original folder names, including accented characters, are preserved.

## Research Background

Road-network resilience depends partly on the availability of alternative routes, accessibility between locations, and the structural connectivity of the network.

Traditional road-network design approaches frequently emphasize transportation efficiency, capacity expansion, or construction costs. This research investigates whether relatively small structural interventions can simultaneously strengthen multiple network properties.

The central research question is:

**To what extent can limited, strategically selected link additions improve multiple structural indicators of road-network resilience?**

The analysis considers 81 geographically diverse road networks under a consistent optimization framework.

## Methodology

### 1. Network Representation

Each road network is represented as an undirected graph:

\[
G = (V,E)
\]

where:

- \(V\) represents the set of nodes.
- \(E\) represents the existing road links.
- \(n = |V|\) is the number of nodes.
- \(m = |E|\) is the number of existing undirected links.

The analysis focuses on topological connectivity rather than traffic assignment or link-capacity constraints.

### 2. Candidate Link Generation

Potential additions are restricted to pairs of previously unconnected nodes separated by two or three hops in the original network.

The candidate set is:

\[
\mathcal{C} =
\left\{
\{u,v\} \notin E :
d_G(u,v) \in \{2,3\}
\right\}
\]

This restriction provides a consistent definition of local network augmentation across all analyzed networks.

Candidate links are evaluated using the baseline network topology.

### 3. Link Addition Budget

The number of permitted additions is approximately **0.5% of the existing undirected links**, rounded to the nearest integer.

\[
K = \operatorname{round}(0.005|E|)
\]

For the analyzed networks, this corresponds to budgets of:

\[
K \in \{3,4,5,6,7\}
\]

Larger networks consequently receive larger absolute link-addition budgets.

This standardized rule permits comparisons across networks of different sizes.

### 4. Structural Performance Indicators

Four complementary indicators are considered.

**Aggregate Shortest-Path Distance**

Measures the total shortest-path distance between all node pairs.

Reducing this indicator represents an improvement in overall structural accessibility.

**Closeness-Weighted Accessibility**

Measures shortest-path costs while assigning greater importance to destinations with higher baseline closeness centrality.

Reducing this indicator improves weighted structural accessibility.

**Worst-Origin Accessibility**

Measures the maximum weighted accessibility cost experienced by any origin node.

Reducing this indicator improves the largest origin-level accessibility burden.

**Triangle-Based Local Redundancy**

Measures the number of distinct triangles within the network.

Increasing this indicator strengthens local connectivity and short alternative-route structures.

### 5. Optimization Objective

The research employs a max–min optimization objective.

The objective is to select a limited set of new links that maximizes the smallest percentage improvement among the four indicators.

\[
\max_{S \subseteq \mathcal{C},\, |S|=K}
\min_{q \in \mathcal{I}}
\Delta_q(S)
\]

where:

- \(S\) is the selected set of link additions.
- \(\mathcal{C}\) is the set of eligible candidate links.
- \(K\) is the permitted number of additions.
- \(\mathcal{I}\) is the set of structural indicators.
- \(\Delta_q(S)\) is the baseline-relative percentage improvement in indicator \(q\).

This formulation prevents improvements in one indicator from compensating for insufficient improvements in another.

### 6. Solution Procedure

The computational framework combines:

1. Greedy construction of candidate solutions.
2. Local search and single-link exchanges.
3. Randomized reconstruction procedures.
4. Exact enumeration for eligible three-link instances.
5. Benders-based optimization bounds for larger instances.

Selected link sets are evaluated using the defined structural indicators.

The computational bounds distinguish achieved improvements from improvements that may remain attainable.

## Dataset Applications

The datasets can support research involving:

- Discrete network design problems
- Road-network augmentation
- Graph-theoretic resilience analysis
- Structural accessibility
- Network redundancy
- Shortest-path optimization
- Transportation network topology
- Comparative network analysis
- Combinatorial optimization

Researchers may also use the collection to benchmark alternative link-selection methods or examine relationships between baseline network structure and attainable improvements.

## Getting Started

### Clone the Repository

```bash
git clone https://github.com/Todai-ops/DNDP-Networks.git
```

Navigate to the repository:

```bash
cd DNDP-Networks
```

The network datasets are available within:

```text
Networks/
```

Each location has an individual subdirectory.

The data can be examined using suitable graph-analysis tools, depending on the file formats contained in each network directory.

## Scope and Limitations

The repository supports the analysis of structural network properties.

Several important limitations should be recognized:

1. The network representations emphasize topology rather than detailed traffic conditions.
2. Candidate links are identified through graph distance rather than physical construction feasibility.
3. Improvements in structural indicators do not automatically demonstrate improvements in disruption-specific transportation performance.
4. The analysis does not directly incorporate travel demand, congestion, construction costs, or geographical obstacles.
5. Network extracts do not necessarily correspond to complete municipal transportation systems.

Consequently, the datasets are particularly suitable for studying the structural foundations of network resilience.

Detailed engineering and transportation analyses are necessary before interpreting candidate links as practical construction recommendations.

## Associated Research

The datasets are associated with the research manuscript:

**Strengthening the Structural Foundations of Road Network Resilience through Limited Link Additions**

**Authors:**
- Adhar Sharma
- Srijith Balakrishnan
- Riki Honda

The study investigates limited structural augmentation across 81 road networks and evaluates improvements in accessibility, aggregate distance, worst-origin performance, and local redundancy.

## Data Provenance and Attribution

The network collection is derived from OpenStreetMap-related road-network data.

Users should consult the originating dataset and applicable OpenStreetMap attribution and licensing requirements before redistribution or reuse.

No additional data license is asserted by this README.

## Repository Scope

This repository currently contains the **road-network datasets only**.

Optimization outputs, selected link sets, computational scripts, and numerical result tables are not included.

---

**Repository maintained by:** Adhar Sharma  
**Research area:** Transportation Networks, Discrete Network Design, Network Resilience, Graph Optimization
