`Depth First Search`

`Note :-`   

  Here we have used the code which is applicable for connected components. Means all the distinct parts of a graph are also part of this DFS . 
  It is done by the for loop in the `dfsOfGraph` function.  If we don’t want connected components in our graph we just need to remove this loop that’s all.

`Space Complexity` : O(N) for recursion stack space + O(N) visited array.

Hence in total the `space complexity is O(N)`

`Time Complexity` :  O(N) as we call DFS function only once in recursive  function for a node + (2* E) number of Neigh bours. `time complexity is O(V+ E)`

```java
class Solution {
    
    public ArrayList<Integer>dfsOfGraph(int V,ArrayList<ArrayList<Integer>>adj){
        
        ArrayList<Integer>res = new ArrayList<>();
        boolean[] visited = new boolean[V+1];
        
        for(int i = 0; i < V;++i){
            if(visited[i] == false)
                 DFS(i,visited,res, adj);
        }
        return res;
    }
    
    public void DFS(int node,boolean[]visited,ArrayList<Integer>res,
        ArrayList<ArrayList<Integer>>adj){
              
            visited[node] = true;
            res.add(node);
            
            for(Integer idx : adj.get(node)){
                if(visited[idx] == false)
                    DFS(idx,visited,res,adj);
            }
    }
}
```
