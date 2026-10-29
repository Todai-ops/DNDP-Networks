DNDP Road Network Datasets
Road-network datasets used to investigate how a small number of strategically selected new links can improve the structural properties of existing transport networks.

This repository contains the Networks/ dataset directory only. Optimization outputs and analysis code are not included.
Dataset overview
The collection consists of 81 OpenStreetMap-derived road-network extracts spanning 53 countries and territories. The extracts represent cities, towns, or urban districts; a folder name does not necessarily represent an entire municipal road system.

In the associated research, the processed networks are modeled as simple, undirected, unweighted graphs. The analyzed graphs contain approximately 372–947 nodes and 502–1,317 undirected links.
Repository structure
DNDP-Networks/
└── Networks/
    ├── Abilene/
    ├── Acatlan/
    ├── Andorra_la_Vella/
    ├── Baños_de_Agua_Santa/
    ├── Banska_Štiavnica/
    ├── ...
    └── Xizhou/
Each location has its own subdirectory under Networks/. The original folder names, including accented characters, are preserved. The contents of individual location folders should be inspected for the available data files and their formats; this README does not assume a single file schema across all folders.
Research context
The datasets support a discrete network design problem (DNDP) that studies limited link additions to an intact road network. In the associated study:
1. Candidate links connect previously unconnected node pairs separated by two or three hops in the baseline network.
2. The addition budget is approximately 0.5% of the baseline number of undirected links, rounded to the nearest integer (three to seven additions for the analyzed networks).
3. The objective maximizes the minimum baseline-relative percentage improvement across four topological indicators:
   - Aggregate shortest-path distance
   - Closeness-weighted accessibility cost
   - Worst-origin weighted accessibility cost
   - Triangle-based local redundancy
This is a topological assessment. Improvements in these indicators should not be interpreted as direct evidence of reduced travel times during disasters, construction feasibility, or faster post-disruption recovery. Those questions require additional geographic, traffic, cost, and disruption data.
Getting the data
Clone the repository:
git clone https://github.com/Todai-ops/DNDP-Networks.git
The location-specific files will be available under DNDP-Networks/Networks/.
Associated manuscript
Sharma, A., Balakrishnan, S., & Honda, R. Strengthening the Structural Foundations of Road Network Resilience through Limited Link Additions. Research manuscript.
Data provenance and reuse
The network collection is derived from OpenStreetMap-related road-network data. Users should consult the original dataset and OpenStreetMap attribution and licensing requirements before redistribution or reuse. No additional data license is asserted by this README.
Scope
This repository currently hosts network datasets only. Optimization outputs, selected link sets, numerical results, and source code are outside its present scope.
