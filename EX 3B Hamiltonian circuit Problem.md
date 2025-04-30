# EX 3B Hamiltonian Circuit Problem
## DATE:
## AIM:
To write a python program to check whether Hamiltonian path exits in the given graph.

## Algorithm
1. Define the Graph class with an initializer that creates an adjacency matrix graph and sets the number of vertices V.
2. Define the function isSafe that checks if a vertex v can be added to the current path at position pos.
  The vertex v should be connected to the last added vertex (graph[path[pos-1]][v] == 1).
  The vertex v should not already exist in the path to avoid revisiting vertices.
3. Define a recursive function hamCycleUtil that tries to find a Hamiltonian cycle.
4. If all vertices have been visited (pos == V), check if the last vertex is connected to the first vertex (graph[path[pos-1]][path[0]] == 1). If true, return True, indicating a valid cycle.
  Otherwise, for each vertex, check if it can be safely added to the path using isSafe. If so, add the vertex and make a recursive call to add the next vertex.
  If adding a vertex leads to a dead end, backtrack by removing the vertex (path[pos] = -1).
5. Define the hamCycle function that initializes the path with -1 and starts the recursive cycle search from vertex 0.
6. If no Hamiltonian cycle is found (hamCycleUtil returns False), print that no solution exists.
7. If a solution exists, print the Hamiltonian cycle by calling the printSolution function, which outputs the path.   

## Program:
```
Program to implement to check whether Hamiltonian path exits in the given graph.
Developed by: Sana Fathima H
Register Number:  212223240145
class Graph():
    def __init__(self, vertices):
        self.graph = [[0 for column in range(vertices)]
                            for row in range(vertices)]
        self.V = vertices
    def isSafe(self, v, pos, path):
        if self.graph[ path[pos-1] ][v] == 0:
            return False
        for vertex in path:
            if vertex == v:
                return False
 
        return True
    def hamCycleUtil(self, path, pos):
        if pos == self.V:
            if self.graph[ path[pos-1] ][ path[0] ] == 1:
                return True
            else:
                return False
        for v in range(1,self.V):
 
            if self.isSafe(v, pos, path) == True:
 
                path[pos] = v
 
                if self.hamCycleUtil(path, pos+1) == True:
                    return True
                path[pos] = -1
 
        return False
 
    def hamCycle(self):
        path = [-1] * self.V
        path[0] = 0
 
        if self.hamCycleUtil(path,1) == False:
            print ("Solution does not exist\n")
            return False
 
        self.printSolution(path)
        return True
 
    def printSolution(self, path):
        print ("Solution Exists: Following",
                 "is one Hamiltonian Cycle")
        for vertex in path:
            print (vertex, end = " ")
        print (path[0], "\n")
g1 = Graph(5)
g1.graph = [ [0, 1, 0, 1, 0], [1, 0, 1, 1, 1],
            [0, 1, 0, 0, 1,],[1, 1, 0, 0, 1],
            [0, 1, 1, 1, 0], ]
g1.hamCycle();
```

## Output:

![image](https://github.com/user-attachments/assets/5d4229c8-1d2b-4a14-9504-38214df624c3)


## Result:
The Hamiltonian path program executed successfully, and it determined whether a Hamiltonian path exists in the given graph.
