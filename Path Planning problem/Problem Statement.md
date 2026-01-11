# EE60216: Motion Planning and Control of Unmanned Vehicles  
## Assignment 1

**Course:** EE60216 – Motion Planning and Control of Unmanned Vehicles  
**Department:** Electrical Engineering, Indian Institute of Technology Kharagpur  
**Deadline:** 14:00, Friday 07/02/2025  

---

## Instructions

- You are not allowed to use any inbuilt function for graph-search in Matlab.
- Provide a comment for each line of your code.

---

## Exercise 1

A binary occupancy grid is a map representation in which each cell has a value **0** if it does not contain an obstacle and value **1** if it contains an obstacle. A Matlab code to generate a binary occupancy grid is given as:

```matlab
clear all
close all
map = binaryOccupancyMap(60, 50, 1, "grid");
% add obstacles
while i <= 200
    x = randi([0, 50]);
    y = randi([0, 60]);
    i = i + 1;
    setOccupancy(map, [x, y], 1)
end
show(map)
