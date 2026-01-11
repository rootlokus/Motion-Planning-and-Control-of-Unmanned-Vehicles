## Instructions

- You are not allowed to use any inbuilt function for graph-search in Matlab.
- Provide a comment for each line of your code.

---

## Problem 1

A binary occupancy grid is a map representation in which each cell has a value **0** if it does not contain an obstacle and value **1** if it contains an obstacle. A Matlab code to generate a binary occupancy grid is given as:

```matlab
clear all
close all
map = binaryOccupancyMap(60, 50, 1, "grid");
% add obstacles
while i <= 200
    x = randi([0, 60]);
    y = randi([0, 50]);
    i = i + 1;
    setOccupancy(map, [x, y], 1)
end
show(map)
```

In a scenario, there are two satellites (Sat1 and Sat2) looking at the grid from the top.

- Sat1 has access to all the grid points with x-coordinates in the range 0–40 (blue).

- Sat2 has access to all the grid points with x-coordinates in the range 30–60 (red).

- Common region is shown in magenta.

<p align="center">
  <img src="figure.png" width="600">
</p>


There is an autonomous vehicle on the ground that has to move from its current initial position to a specified final position. The task of the satellites is to compute the shortest path from the initial point of the ground vehicle to the final point and transmit it to the vehicle.

### (a) Shortest Path Computation by Satellites

Assuming that satellites cannot share the complete maps with each other but can only share the visited nodes from the overlapping part of the grid (points with x-coordinates in the range 30–40), write a Matlab function that computes the shortest path on the grid between a given initial position of the autonomous vehicle and the final position.

Use Dijkstra’s algorithm for both Sat1 and Sat2.

While computing the shortest path, both the satellites assume 8-point connectivity on the grid.

Use the functions described at Matlab help document to obtain the occupancy of a particular grid point.

### (b) Autonomous Vehicle Motion and A-star Planning

The autonomous vehicle has states

<p align="center"><strong>[x, y]<sup>T</sup></strong></p>


and can move only in the forward, backward, left, and right directions.

Write the state space, action space, and the state-transition equation of the autonomous vehicle.

There is a delay in sending the shortest path from the satellite system to the vehicle.

During the delay, the vehicle can move up to the maximum Manhattan distance of 30 units from the initial position that was reported to the satellite.

The vehicle knows:

its current position from the origin of the grid,

the goal position,

and can only sense the obstacles in the neighboring cells.

Using the state-transition equation of the autonomous vehicle, write a Matlab function that implements an A-star algorithm to find the shortest path from the new initial position to the final goal.

Consider the following heuristics:

Manhattan distance to the goal point.

Euclidean distance to the goal point.

A self-designed heuristic that uses:

the Euclidean distance to the shortest path reported by the satellite system, and

the cost-to-reach the goal computed from it.

Additionally:

Explain why each of the above heuristics is valid or invalid.

Report the efficiency of all search algorithms implemented so far.

(c) Plots, Visualization, and Failure Handling

Provide Matlab plots and codes for all the above search algorithms, clearly highlighting:

the computed path by each satellite, and

the shortest path taken by the vehicle.

Your algorithm should also report failure, if no path is found.
