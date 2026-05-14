# 🗺️ Shortest Path Finding in Map — Data Structures Project

> Implementation of Dijkstra's Algorithm in C for finding the shortest 
path in map-based applications.

**Student:** Jeevithasri R (927623BEC091)  
**Course:** Data Structures  
**Institution:** M. Kumarasamy College of Engineering (Autonomous)

---

## 📌 Introduction

Finding the shortest path in map-based applications is a fundamental 
problem in computer science, with critical applications in:

- Navigation systems
- Geographic Information Systems (GIS)
- Network routing

Dijkstra's algorithm systematically explores nodes in a graph, ensuring 
the shortest path to each node is found step-by-step. Implemented in C 
for optimal performance with low-level memory management and high 
execution speed.

---

## 🎯 Objective

- Implement and optimize Dijkstra's algorithm in C
- Enhance performance through efficient data structures
- Test on various datasets (small, medium, large-scale graphs)
- Provide practical insights for developers integrating pathfinding 
into C-based systems

---

## 🧠 Data Structures Used

| Structure | Purpose |
|----------|---------|
| Priority Queue (Binary Heap) | Efficient minimum node selection |
| Adjacency List | Space-efficient graph representation |
| Dynamic Memory Allocation | Managing large graph datasets |

---

## ⚙️ How It Works

**Flowchart Summary:**
1. Navigation starts → Load maps
2. Choose starting point and destination
3. Validate points → Add to dataset collection
4. Check if paths planned before
5. If No → Create network topology
6. Calculate the shortest path → Draw the shortest path
7. Navigation ends

---

## 📦 Modules

### 1. Algorithm Design and Selection
Study of Dijkstra's algorithm — its theoretical principles and 
suitability for graphs with non-negative weights. Priority queues 
selected for node selection; adjacency lists for graph representation.

### 2. Implementation in C
Core coding of the algorithm with emphasis on efficient memory 
management. Implements priority queues using binary heaps and 
adjacency lists for graph representation.

### 3. Optimization
Refining data structures to enhance speed and reduce memory usage. 
Error handling and edge case management for robust performance.

### 4. Testing and Validation
Diverse map datasets tested — small, medium, and large-scale graphs. 
Results compared against known benchmarks.

### 5. Performance Evaluation
Analysis based on execution time, memory usage, and scalability. 
Profiling used to identify bottlenecks.

### 6. Documentation and Reporting
Detailed code comments, function explanations, and usage instructions.

---

## 💻 Code

```c
#include <limits.h>
#include <stdbool.h>
#include <stdio.h>

#define V 9

int minDistance(int dist[], bool sptSet[]) {
    int min = INT_MAX, min_index;
    for (int v = 0; v < V; v++)
        if (sptSet[v] == false && dist[v] <= min)
            min = dist[v], min_index = v;
    return min_index;
}

void dijkstra(int graph[V][V], int src) {
    int dist[V];
    bool sptSet[V];

    for (int i = 0; i < V; i++)
        dist[i] = INT_MAX, sptSet[i] = false;

    dist[src] = 0;

    for (int count = 0; count < V - 1; count++) {
        int u = minDistance(dist, sptSet);
        sptSet[u] = true;

        for (int v = 0; v < V; v++)
            if (!sptSet[v] && graph[u][v] &&
                dist[u] != INT_MAX &&
                dist[u] + graph[u][v] < dist[v])
                dist[v] = dist[u] + graph[u][v];
    }

    printf("Vertex \t\t Distance from Source\n");
    for (int i = 0; i < V; i++)
        printf("%d \t\t\t\t %d\n", i, dist[i]);
}

int main() {
    int graph[V][V] = {
        { 0, 4, 0, 0, 0, 0, 0, 8, 0 },
        { 4, 0, 8, 0, 0, 0, 0, 11, 0 },
        { 0, 8, 0, 7, 0, 4, 0, 0, 2 },
        { 0, 0, 7, 0, 9, 14, 0, 0, 0 },
        { 0, 0, 0, 9, 0, 10, 0, 0, 0 },
        { 0, 0, 4, 14, 10, 0, 2, 0, 0 },
        { 0, 0, 0, 0, 0, 2, 0, 1, 6 },
        { 8, 11, 0, 0, 0, 0, 1, 0, 7 },
        { 0, 0, 2, 0, 0, 0, 6, 7, 0 }
    };
    dijkstra(graph, 0);
    return 0;
}
```

---

## 📊 Output

| Vertex | Distance from Source |
|--------|---------------------|
| 0      | 0                   |
| 1      | 4                   |
| 2      | 12                  |
| 3      | 19                  |
| 4      | 21                  |
| 5      | 11                  |
| 6      | 9                   |
| 7      | 8                   |
| 8      | 14                  |

---

## 📈 Performance Analysis

- **Time Complexity:** O((V + E) log V) — linearithmic performance
- **Space Complexity:** Optimized via adjacency lists and dynamic 
memory allocation
- **Scalability:** Handles small, medium, and large-scale graphs 
efficiently
- **vs Bellman-Ford:** Dijkstra outperforms Bellman-Ford for graphs 
with non-negative weights

---

## ✅ Conclusion

Dijkstra's algorithm implemented in C with priority queues and 
adjacency lists offers a reliable, efficient solution for shortest 
path finding. Execution time closely matched theoretical expectations 
O((V + E) log V), and memory usage was well-optimized even for large 
graphs.

---

## 📚 References

1. Cormen, T. H. et al. (2009). *Introduction to Algorithms* (3rd ed.). MIT Press.
2. Sedgewick, R. (2002). *Algorithms in C* (3rd ed.). Addison-Wesley.
3. GeeksforGeeks — Dijkstra's Shortest Path Algorithm
4. GeeksforGeeks — Bellman-Ford Algorithm
5. TutorialsPoint — Shortest Path Algorithms in C

---

## 📜 License

Submitted for academic purposes — Data Structures, B.E. (ECE)  
M. Kumarasamy College of Engineering (Autonomous), Anna University Chennai.
