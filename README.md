# HospitalEdgeWeigths
In this repository, we show and explain which are the weights for the edges of the knowledge graph (KG) used in [~~doi: TODO~~](NULL). Specifically, these weights are for the edges related to the spatial dimension of the domain represented with the KG. This KG was used as a basis for the work "_Spatiotemporal Data Modelling for Epidemiological Research in Hospitals_" [10.1109/JBHI.2024.3417224](https://ieeexplore.ieee.org/document/10568325).

To be more specific, the spatial edges are those from a more recent version of the KG that can be found in the following repository: [LorenaPujante/HospitalKG_Changes](https://github.com/LorenaPujante/HospitalKG_Changes).

Here, we present a figure with the spatial dimension of the KG where each type of edge has its weight (in navy blue). 

![Spatial dimension of the KG where edges have their weight](https://github.com/user-attachments/assets/ac00ccbf-f243-482d-9695-dbccee1ad79e)

## 0. Basis
As the basis of the process to calculate the generic weight of each type of edge, we have the following facts:
- The weight of the edges represents **metres**.
- We start with the following measurements:
  - The size of a _Bed_ is: 1×2 metres
  - The size of a general _Room_ for hospitalisations is: 3×6.5 metres
- To measure the distance between the _Locations_, we have only used the _General Rooms_. These _Rooms_ are on the upper floors of the hospital. The ground floor (where the emergency rooms, ICU rooms, operating theatres and X-ray rooms are located) will not be taken into account. This is because the layout and size of the rooms on the ground floor are different from those on the other floors.

A schematic representation of a general _Room_ for hospitalisations can be seen in the following figure. The dimensions are in metres.

<p align="center">
  <img src="https://github.com/user-attachments/assets/6fb6e8cd-bbb5-4c8c-aa1d-cd8e8d0a12fb" alt="Schematic representation of a Room">
</p>


## 1. Edges

### 1.1. Bed →<sup>(nextTo)</sup> Bed


### 1.2. Bed →<sup>(opposite)</sup> Bed


### 1.3. Bed →<sup>(placedIn)</sup> Room
