`Breadth First Search`

`Note :-`  

  Here we have used a code which is not including the distinct components of the graph. But if we want to achieve it we just 
  need to wrap the whole code with a loop.

`Time Complexity :`  O(N) time to traverse the whole graph as we are accessing each node once.

and O(2E ) for neigh bours. hence `time complexity is O(N) + O(2E)`

`Space Complexity :` O(N) for queue + O(N) visited array : Hence `space complexity is O(2N)`


```java
class Solution {
    ArrayList<Integer>res = new ArrayList<>();
    
    public ArrayList<Integer>bfsOfGraph(int V,ArrayList<ArrayList<Integer>>adj){
       
        boolean[]visited = new boolean[V+1];
        // add loop here for including the connected components in the BFS
        // for(int i = 0; i< v;++i){
        //    if(visited[i] == false){
        Queue<Integer>q = new LinkedList<>();
       
        q.add(0);
        visited[0] = true;
       
        while(!q.isEmpty()){
           int node = q.poll();
           res.add(node);
           
           for(Integer idx : adj.get(node)){
               if(visited[idx] == false){
                   visited[idx] = true;
                   q.add(idx);
               }
           }
        }
        // End loop here
        //    }
        // }
        return res;
    }
}
```
