---
layout: post
title: Heuristics Lesson
toc: False
comments: True
---

# Homework

## 1. Another Undecidable Problem: **The Post Correspondence Problem (PCP)**

The **Post Correspondence Problem (PCP)** is a famous example of an undecidable problem.  
In PCP, you are given two lists of strings (say List A and List B). The challenge is to find a sequence of indices so that the strings picked from List A, when concatenated, match exactly the concatenation of strings picked from List B.

**Formally:**  
Given lists
- A = [a₁, a₂, ..., aₙ]  
- B = [b₁, b₂, ..., bₙ],

is there a sequence of indices (i₁, i₂, ..., iₖ) such that:  
aᵢ₁ aᵢ₂ ... aᵢₖ = bᵢ₁ bᵢ₂ ... bᵢₖ?

**Why is it undecidable?**  
There is no general algorithm that can always determine whether a matching sequence exists for any given input. This undecidability was proven by Emil Post in 1946.

---

## 2. Nearest Neighbor Algorithm for the Traveling Salesman Problem (TSP)

Here’s a simple Python implementation:

```python
import math

# Function to calculate distance between two points
def distance(p1, p2):
    return math.hypot(p1[0] - p2[0], p1[1] - p2[1])

# Nearest Neighbor Algorithm
def nearest_neighbor(points):
    unvisited = points.copy()
    path = [unvisited.pop(0)]  # Start at the first point
    
    while unvisited:
        last = path[-1]
        # Find the nearest neighbor
        next_point = min(unvisited, key=lambda point: distance(last, point))
        path.append(next_point)
        unvisited.remove(next_point)
    
    # Return to the start
    path.append(path[0])
    return path

# Example usage
cities = [(0, 0), (1, 5), (5, 2), (6, 6), (8, 3)]
tour = nearest_neighbor(cities)
print("Tour:", tour)
```

**How it works:**
- Start at the first city.
- Repeatedly go to the nearest unvisited city.
- After visiting all cities, return to the starting city.

---

## 3. Real-World Example of Heuristics: **Route Planning for Delivery Trucks**

Companies like **Amazon**, **UPS**, and **FedEx** use heuristics to plan delivery routes because solving the Traveling Salesman Problem exactly (finding the shortest possible route visiting all addresses) becomes *computationally impossible* for hundreds or thousands of locations.

**Why not use an exact solution?**
- The number of possible routes grows factorially with the number of locations (n!), making exact calculations infeasible for large datasets.
- Real-world constraints (traffic, road closures, delivery time windows) complicate things even more.
- A "good enough" heuristic solution (like Nearest Neighbor, Genetic Algorithms, or Simulated Annealing) is much faster and saves time and fuel without needing perfection.
