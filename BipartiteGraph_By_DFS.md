```java

class Solution{
    public boolean isBipartite(int V, ArrayList<ArrayList<Integer>>adj) {
        
        int[]color = new int[V];
        Arrays.fill(color, -1);
        
        // loop for case of distinct components.
        for(int i=0; i < V;++i){
            if(color[i] == -1){
                if(checkByDFS(i,1,color,adj) == false){
                    return false;
                }
            }
        }
        return true;
    }
    
    public boolean checkByDFS(int src,int col,int[]color,
        ArrayList<ArrayList<Integer>>adj){
        
        color[src] = col;
        
        for(Integer idx : adj.get(src)){
            if(color[idx] == -1){
                if(checkByDFS(idx,1-col,color,adj)== false)
                   return false;
            }
            else if(color[idx] == color[src])
                return false;
        }
        return true;
    }
}

```
