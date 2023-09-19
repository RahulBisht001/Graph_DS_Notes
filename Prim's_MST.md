```java
class Pair {
    int distance;
    int node;
    
    public Pair(int distance,int node){
        this.node = node;
        this.distance = distance;
    }
}


class Solution{
	public int spanningTree(int V,int E,int edges[][]){
	    
	    
	    ArrayList<ArrayList<int[]>>adj = new ArrayList<>();
	    // ***********************************
        //We haven't the prebuilt graph so we need to create is ourselves.
	    for(int i=0;i < V;++i)
	        adj.add(new ArrayList<>());
	        
	    for(int[]edge : edges){
	        adj.get(edge[0]).add(new int[]{edge[1],edge[2]});
	        adj.get(edge[1]).add(new int[]{edge[0],edge[2]});
	    }
	    // ***********************************
	    int[]vis = new int[V];
	    int minTotal = 0;
	    
	    PriorityQueue<Pair>pq = new PriorityQueue<>((a,b)->a.distance-b.distance);
	    pq.add(new Pair(0,0));
	    
	    while(!pq.isEmpty()){
	        
	        int wt = pq.peek().distance;
	        int node = pq.peek().node;
	        
	        pq.poll();
	        
	        if(vis[node] == 1)
	             continue;
	        vis[node] = 1;
	             
	        minTotal += wt;
	        for(int[]a : adj.get(node)){
	            int edw = a[1];
	            int adjNode = a[0];
	            
	            if(vis[adjNode]== 0)
	                pq.add(new Pair(edw,adjNode));
	        }
	    }
	    return minTotal;
	}
}
```
