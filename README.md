# HospitalEdgeWeigths
In this repository, we show and explain which are the weights for the edges of the knowledge graph (KG) used in [~~doi: TODO~~](NULL) (DOI: TODO). Specifically, these weights are for the edges related to the spatial dimension of the domain represented with the KG. This KG was used as a basis for the work "_Spatiotemporal Data Modelling for Epidemiological Research in Hospitals_" [10.1109/JBHI.2024.3417224](https://ieeexplore.ieee.org/document/10568325).

To be more specific, the spatial edges are those from a more recent version of the KG that can be found in the following repository: [LorenaPujante/HospitalKG_Changes](https://github.com/LorenaPujante/HospitalKG_Changes). 

In addition, the calculation of the weights is also influenced by the process of our [random hospital generator](https://github.com/LorenaPujante/HospitalGeneratorRDF) ~~[TODO: CAMBIAR ENLACE AL NUEVO]~~ to create the hospital and _Floor_ layouts. The values of the weights are based on the hospital layout, so it is important to consider the hospital generator's principles (creation and organization rules, limitations).   

Here, we present a figure with the spatial dimension of the KG where each type of edge has its weight (in navy blue). 

<p align="center">
  <img src="https://github.com/user-attachments/assets/51c9ed2d-5b85-4a4a-bd9f-4da20275d298" alt="Spatial dimension of the KG where edges have their weight">
</p>


## 0. Basis
As the basis of the process to calculate the generic weight of each type of edge, we have the following facts:
- The weight of the edges represents **metres**.
- We start with the following measurements:
  - The size of a _Bed_ is: 1×2 metres
  - The size of a general _Room_ for hospitalisations is: 3×6.5 metres
- To measure the distance between the _Locations_, we have only used the _General Rooms_. These _Rooms_ are on the upper floors of the hospital. The ground floor (where the emergency rooms, ICU rooms, operating theatres and X-ray rooms are located) will not be taken into account. This is because the layout and size of the rooms on the ground floor are different from those on the other floors.

A schematic representation of a general _Room_ for hospitalisations can be seen in the following figure. The dimensions are in metres. All the _Rooms_ on the upper floor will have this layout.

<p align="center">
  <img src="https://github.com/user-attachments/assets/40b0651c-30c6-480f-a0b2-bc8782ee9140" alt="Schematic representation of a Room">
</p>


## 1. Edges

- [1.1. Bed →<sup>(nextTo)</sup> Bed](https://github.com/LorenaPujante/HospitalEdgeWeigths?tab=readme-ov-file#11-bed-nextto-bed)
- [1.2. Bed →<sup>(opposite)</sup> Bed](https://github.com/LorenaPujante/HospitalEdgeWeigths?tab=readme-ov-file#12-bed-opposite-bed)
- [1.3. Bed →<sup>(placedIn)</sup> Room](https://github.com/LorenaPujante/HospitalEdgeWeigths?tab=readme-ov-file#13-bed-placedin-room)
- [1.4. Room →<sup>(nextTo)</sup> Room](https://github.com/LorenaPujante/HospitalEdgeWeigths?tab=readme-ov-file#14-room-nextto-room)
- [1.5. Room →<sup>(opposite)</sup> Room](https://github.com/LorenaPujante/HospitalEdgeWeigths?tab=readme-ov-file#15-room-opposite-room)
- [1.6. Room →<sup>(placedIn)</sup> Corridor](https://github.com/LorenaPujante/HospitalEdgeWeigths?tab=readme-ov-file#16-room-placedin-corridor)
- [1.7. Corridor →<sup>(nextTo)</sup> Corridor](https://github.com/LorenaPujante/HospitalEdgeWeigths?tab=readme-ov-file#17-corridor-nextto-corridor)
- [1.8. Corridor →<sup>(placedIn)</sup> Area](https://github.com/LorenaPujante/HospitalEdgeWeigths?tab=readme-ov-file#18-corridor-placedin-area)
- [1.9. Area →<sup>(nextTo)</sup> Area](https://github.com/LorenaPujante/HospitalEdgeWeigths?tab=readme-ov-file#19-area-nextto-area)
  
- [1.3. Bed →<sup>(placedIn)</sup> Room](https://github.com/LorenaPujante/HospitalEdgeWeigths?tab=readme-ov-file#13-bed-placedin-room)
- [1.3. Bed →<sup>(placedIn)</sup> Room](https://github.com/LorenaPujante/HospitalEdgeWeigths?tab=readme-ov-file#13-bed-placedin-room)
- [1.3. Bed →<sup>(placedIn)</sup> Room](https://github.com/LorenaPujante/HospitalEdgeWeigths?tab=readme-ov-file#13-bed-placedin-room)
- [1.3. Bed →<sup>(placedIn)</sup> Room](https://github.com/LorenaPujante/HospitalEdgeWeigths?tab=readme-ov-file#13-bed-placedin-room)
- [1.3. Bed →<sup>(placedIn)</sup> Room](https://github.com/LorenaPujante/HospitalEdgeWeigths?tab=readme-ov-file#13-bed-placedin-room)
- [1.3. Bed →<sup>(placedIn)</sup> Room](https://github.com/LorenaPujante/HospitalEdgeWeigths?tab=readme-ov-file#13-bed-placedin-room)


### 1.1. Bed →<sup>(nextTo)</sup> Bed
Two _Beds_ that are next to each other in the same _Room_ will have a separation of 1 metre. We will add two times half the width of a bed to this distance. That's because we assume that both patients are not on the nearest edges of each bed; they would be in the centre of the bed. This extra distance is also useful for rooms with more than two adjacent beds to avoid getting distances that are too small.

So the total distance will be: _1 + 2×0.5_ = **2** metres. 


### 1.2. Bed →<sup>(opposite)</sup> Bed
In our hospital layout, there won't be general _Rooms_ with more than two _Beds_ or where the _Beds_ are opposite. However, if there would be a _Room_ with a _Bed_ opposite another _Bed_, there would be a 1.5 metre-wide corridor between them. Similarly to the distance between two adjacent _Beds_, we will add a small distance to this separation.

So the total distance will be: _1.5 + 1_ = **2.5** metres.


### 1.3. Bed →<sup>(placedIn)</sup> Room
We will consider this weight as the distance you must traverse to get to a _Bed_ from the _Room_ door. That is the distance from the door to the end of the bed.
- _Bed_1_: 1.5 + 1 = 2.5 metres
- _Bed_2_: 1.5 + 1×3 = 4.5 metres
- _Average of the distances_: (2.5 + 4.5)/2 = 7/2 = **3.5** metres

This distance might not correctly represent the fact of having two _Beds_ that are in the same _Room_ but that are neither adjacent nor opposite each other.
- `Bed →(placedIn) Room ←(placedIn) Bed`: 35 + 3.5 = **7.5**

However, we assume that there won't be _Rooms_ with a layout different from the showed previously. In addition, if there were another kind of _Room_ layout, the distance between _Beds_ could be represented by traversing several _nextTo_ and _opposite_ edges. For example:
- `Bed →(nextTo) Bed →(nextTo) Bed`: 2 + 2 = **4** metres
- `Bed →(opposite) Bed →(nextTo) Bed`: 2 + 2.5 = **4.5** metres


### 1.4. Room →<sup>(nextTo)</sup> Room
In our hospital, _Rooms_ are placed in a mirror arrangement. The following figure represents four contiguous _Rooms_ with the distance between them in metres.

<p align="center">
  <img src="https://github.com/user-attachments/assets/16eb6b19-7b24-4215-b8f9-ebba665f6176" alt="Schematic representation of a four contiguous Rooms">
</p>

The average of the distances between the doors of two _Rooms_ is:
<p align="center">
  ((0.5 + 0.5 + 0.5) + (0.5 + 3.5 + 0.5)) / 2 = ((1.5) + (4.5)) / 2 = 6/2 = <b>3</b> metres &emsp; <em>(This is the width of a Room)</em>
</p>

### 1.5. Room →<sup>(opposite)</sup> Room
In our hospitals, between two opposing _Rooms_, there is a 2.5 metre-wide corridor so that two beds can pass through with some clearance. So, the weight of this edge will be **2.5** metres.


### 1.6. Room →<sup>(placedIn)</sup> Corridor
The distance between any two _Rooms_ located in the same _Corridor_ is based on the Weighted average of the maximum number of adjacent _Rooms_ that can be in a _Corridor_.

To get this number of _Corridors_, we have executed several times our generator of random hospital layouts, [HospitalGeneratorRDF](https://github.com/LorenaPujante/HospitalGeneratorRDF), with the params used in [~~doi: TODO~~](NULL). After each execution, we have counted how many _Areas_ have each _area layout_ so we can know how many _Corridors_ will be and how many adjacent _Rooms_ are in each _Corridor_. The following table represents the results:

<p align="center">
  <img src="https://github.com/user-attachments/assets/c2aa0acd-2861-4e7f-a4ad-d9d195c21aef" alt="Table 1">
</p>

Weighted average:
<p align="center">
  (3×10 + 6×40 + 9×15 + 12×15 + 15×20)/100 = 885/100 = 8.85 ≈ <b>9</b> metres
</p>

However, this weight represents the distance of the path `Room →(placedIn) Corridor ←(placedIn) Room`, so the weight of `Room →(placedIn) Corridor` should be:
<p align="center">
  2<em>α</em>= 9 &ensp; → &ensp; <em>α</em> = 9/2 = 4.5 &ensp; → &ensp; <em>Room →<sup>(placedIn)</sup> Corridor</em> = <b>4.5</b> metres
</p>

Since the average distance between two _Rooms_ in a _Corridor_ is 9 metres, there will be adjacent _Rooms_ that are nearer. When executing the shortest path algorithm in these cases, the result will be a concatenation of _nextTo_ edges. For example:
- `Room →(nextTo) Room →(nextTo) Room`: 3 + 3 = **6** metres
- `Room →(nextTo) Room →(nextTo) Room →(nextTo) Room`: 3 + 3 + 3 = **9** metres


### 1.7. Corridor →<sup>(nextTo)</sup> Corridor
If the Weighted average distance between two _Rooms_ in the same _Corridor_, the Weighted average distance between two _Rooms_ in two neighbouring _Corridors_ would be double. That is:
<p align="center">
  9×2 = <b>18</b> metres
</p>

However:
<p align="center">
  18 = <code>Room → Corridor →<sup>(nextTo)</sup> Corridor ← Room</code> = 4.5 + <em>α</em> + 4.5 &ensp; → &ensp; 9 + <em>α</em> = 18 &ensp; → &ensp; <em>α</em> = 9 <br>
  <code>Corridor →<sup>(nextTo)</sup> Corridor</code> = <b>9</b> metres
</p>


### 1.8. Corridor →<sup>(placedIn)</sup> Area
Our hospital layouts have no _Areas_ with _Corridors_ that are not neighbours to any other _Corridor_ of the _Area_. 

Therefore, the average distance between any _Room_ placed in an _Area_ and any other _Room_ of the same _Area_ will be the same as the average distance between _Rooms_ that are on neighbouring _Corridors_. That is, **18** metres.

However:
<p align="center">
  18 = <code>Room → Corridor → Area ← Corridor ← Room</code> = 4.5 + 2<em>α</em> + 4.5 &ensp; → &ensp; 9 + 2<em>α</em> = 18 &ensp; → &ensp; <em>α</em> = 9/2 &ensp; → &ensp; <em>α</em> = 4.5 <br>
  <code>Corridor →<sup>(placedIn)</sup> Area</code> = <b>4.5</b> metres
</p>


### 1.9. Area →<sup>(nextTo)</sup> Area
Before explaining how we got the value for the weight of the _Area →<sup>(nextTo)</sup> Area_ edge, we will show a figure. In this figure, we can see a schematic representation of the layout of a _Floor_. This _Floor_ has 6 _Areas_ organised in 2 rows and 4 columns. In our [random hospital generator](https://github.com/LorenaPujante/HospitalGeneratorRDF) ~~[TODO: CAMBIAR ENLACE AL NUEVO]~~, the _Area_ layout with the maximum number of _Corridors_ has 4 _Corridors_ arranged in a cross. The _Areas_ in the image follow this layout. _Corridors_ are painted in different colours according to the minimum number of _Corridors_ we have to traverse from the _origin corridor_ (it has a wider line in red) to each _Corridor_ (we will call this number of corridors as _number of steps_). The figure shows the different cases that we can find, depending on which is the origin corridor; the rest of the possible positions would coincide with any of those shown.  


