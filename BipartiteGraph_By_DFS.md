`Bipartite Graph`

  A Bipartite Graph is a graph whose vertices can be divided into two independent sets, U and V such that every edge (u, v) either 
  connects a vertex from U to V or a vertex from V to U. In other words, for every edge (u, v), either u belongs to U and v to V, or u 
  belongs to V and v to U. We can also say that there is no edge that connects vertices of same set.
 The Basic Idea behind is that if you can color the graph with 2 different colors then its called a Bipartite Graph.

`Note:` 

1. Linear Graph with No Cycles are Always Bipartite Graph.
2. Graphs with Even Cycle Length are also Bipartite Graph.

```java
class Solution{
    public boolean isBipartite(int V, ArrayList<ArrayList<Integer>>adj) {
        
        int[]color = new int[V];
        Arrays.fill(color,-1);
        
        Queue<Integer>q = new LinkedList<>();
        
        // This For Loop means that we are also considering Not Connected Components.
        // Basically The whole graph can be in the form of a Forest.
        for(int i=0; i < V;++i){
            if(color[i] == -1){
                q.add(i);
                color[i] = 1;
                
                while(!q.isEmpty()){
                    int node =  q.poll();
                    for(Integer idx : adj.get(node)){
                        // If the idx(curr node) is not colored yet
                        // Fill it with the opposite color of its parent.
                        if(color[idx] == -1){
                           q.add(idx);
                           color[idx] = 1 - color[node];
                        }
                        // If it is already colored and it has the same color as its
                        // parent then its not a Bipartite Graph.
                        else if(color[idx] == color[node])
                           return false;
                   }
                }
            }
        }
        // Or else it is a Bipartite Graph.
        return true;
    }
}
```
