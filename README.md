## Introduction
In Houston, TX, we are facing a challenge with flooding in an urban area. To tackle this issue, we are looking to 
develop a machine learning model capable of predicting the outcome of flood events based on their initial 
conditions. We have a collection of 3,000 simulated flood incidents (training set), each serving as a historical data 
point to train our model.
The assignment's goal is to build a data-driven model to capture the simulator's logic that generated these incidents 
and to replicate its predictions. Each simulated incident is unique, starting with different initial conditions, leading 
to varied outcomes. However, the geographical layout, including the street network and the location coordinates of 
each street segment, remains unchanged throughout all simulations. This consistent geographic data is available in 
the ‘edge_info.csv’ file.
Additionally, specific parameters that influence how the flood unfolds in each simulation are set at the beginning 
and differ from one incident to another. These parameters are detailed in the ‘training_parameters.csv’ and 
‘test_parameters.csv’ files for the training and testing datasets, respectively.
Some basic definitions:
* Nodes: Intersections or endpoints of streets. Each node has a unique 9-digit identifier. Like: 152356047
* Edges: Street segments linking two nodes, defined by 'head_id' and 'tail_id'.

The selected urban area is composed of 191 edges.

## DATASET OVERVIEW
You received 3,000 observations, each detailing the initial and final states of separate observations. These 
observations represent flood progression in a hypothetical urban layout, determined by street connectivity, 
elevation, and infrastructure.
Simulation parameters for each observation are retrievable from `./training_parameters.csv` and `./test_parameters.csv`. These parameters include:
* ObservationIndex: an identifier for the observation.
* SurfaceType: Type of urban surface.
* Waterflow: Intensity and duration of water flow.
* InitialWaterLevels: Pre-simulation underground water level.
* DrainageSystemCapacity: Indicator of drainage efficiency.
* GreenSpaceRatio: Proportion of greenery in the urban area.

Within the `./training` and `./test` directories, CSV files correspond to the observations. Each file, named after 
the observation index, records various edges with attributes:
* head_id: ID of the head node.
* tail_id: ID of the tail node.
* flooded_init: Whether the edge was initially flooded.
* flooded_final: Whether the edge was flooded after the simulation (this is the target variable!).

Extra information about the edges can be found inside `edge_info.csv`:
* longitude: Longitude of the edge's center.
* latitude: Latitude of the edge's center.
* altitude: the elevation of the edge’s center.

## OBJECTIVE
Your task is to devise a predictive model that uses this data to predict the flooded_final column for each sample in 
the test set (`./test`).
