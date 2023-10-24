<h1>ExpNo 3 : Implement A* search algorithm for a Graph</h1> 
<h3>Name: Kavinraja D</h3>
<h3>Register Number: 212222240047</h3>

# Aim:
To ImplementA * Search algorithm for a Graph using Python 3.

# Algorithm:
1. Initialize the open list

2. Initialize the closed list
    put the starting node on the open 
    list (you can leave its f at zero)

3. while the open list is not empty
   
   a) find the node with the least f on 
       the open list, call it "q"

   b) pop q off the open list
  
   c) generate q's 8 successors and set their 
       parents to q
   
   d) for each successor
    
     i) if successor is the goal, stop search
        
     ii) else, compute both g and h for successor
          successor.g = q.g + distance between 
                              successor and q
          successor.h = distance from goal to 
          successor (This can be done using many 
          ways, we will discuss three heuristics- 
          Manhattan, Diagonal and Euclidean 
          Heuristics)
          
    successor.f = successor.g + successor.h


        
    iii)  if a node with the same position as 
            successor is in the OPEN list which has a 
           lower f than successor, skip this successor
           

     iV)   if a node with the same position as 
            successor  is in the CLOSED list which has
            a lower f than successor, skip this successor
            otherwise, add  the node to the open list
     end (for loop)

  
e) push q on the closed list
    end (while loop)


# PROGRAM:
```python
from collections import defaultdict
H_dist ={}
def aStarAlgo(start_node, stop_node):
    open_set = set(start_node)
    closed_set = set()
    g = {}              
    parents = {} 
    g[start_node] = 0
    parents[start_node] = start_node
    while len(open_set) > 0:
        n = None
        for v in open_set:
            if n == None or g[v] + heuristic(v) < g[n] + heuristic(n):
                n = v
        if n == stop_node or Graph_nodes[n] == None:
            pass
        else:
            for (m, weight) in get_neighbors(n):
                if m not in open_set and m not in closed_set:
                    open_set.add(m)
                    parents[m] = n
                    g[m] = g[n] + weight
                else:
                    if g[m] > g[n] + weight:
                        g[m] = g[n] + weight
                        parents[m] = n
                        if m in closed_set:
                            closed_set.remove(m)
                            open_set.add(m)
        if n == None:
            print('Path does not exist!')
            return None
        if n == stop_node:
            path = []
            while parents[n] != n:
                path.append(n)
                n = parents[n]
            path.append(start_node)
            path.reverse()
            print('Path found: {}'.format(path))
            return path
        open_set.remove(n)
        closed_set.add(n)
    print('Path does not exist!')
    return None
def get_neighbors(v):
    if v in Graph_nodes:
        return Graph_nodes[v]
    else:
        return None
def heuristic(n):
    return H_dist[n]
graph = defaultdict(list)
n,e = map(int,input().split())
for i in range(e):
    u,v,cost = map(str,input().split())
    t=(v,float(cost))
    graph[u].append(t)
    t1=(u,float(cost))
    graph[v].append(t1)
for i in range(n):
    node,h=map(str,input().split())
    H_dist[node]=float(h)
print(H_dist)

   
Graph_nodes=graph
print(graph)
aStarAlgo('S', 'G')

```

<hr>
<h2>Graph I:</h2>
<hr>

![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/acbb09cb-ed39-48e5-a59b-2f8d61b978a3)


<hr>
<h2>Input:</h2>
<hr>
6 6 <br>
A B 2 <br>
B C 1 <br>
A E 3 <br>
B G 9 <br>
E D 6 <br>
D G 1 <br>
A 11 <br>
B 6 <br>
C 99 <br>
E 7 <br>
D 1 <br>
G 0 <br>
<hr>
<h2>Output:</h2>
<hr>
Path found: ['A', 'E', 'D', 'G']


# RESULT:
Thus,a Graph was constructed and implementation of A* Algorithm for the same graph was done successfully.
