# Solution_1
Question:
Design the feature similar to the one in LinkedIn where it computes how many hops there are between you and another person? The hops are based on the connections. E.g, if ‘A’ is a direct connection of  ‘B’ the number of hops between ‘A’ and ‘B’ is 0. However, if ‘B’ has another connection, say ‘C’ then the number of hops between ‘A’ and ‘C’ is 1.


Answer:

We will implemet the links in undirected Graph Where a person is a vertex and edge is a connection between two persons. 
Here is the java implementation of a undirected Graph. 

Assumptions:
The Data structure Bag is taken to implement the graph which is essentially nothing but an array of integers
Each vertex, that is each person is defined by an integer between 0 and V-1. 
We can convert name and integers with the symbol table

public class Graph
{
	private final int  V;
	private Bag<Integer>[] adj;
	
	public Graph(int V)
	{
		this.V = V;
		adj = (Bag<Integer>[]) new Bag[V];
		for(int v= 0; v<V; v++)
		{
			adj[v] = new Bag<Integer>();

		} 
	}
	public void addedge(int v, int w)
	{
	  adj[v].add(w);
	  adj[w].add(v);
	}
	public Iterable<Integer> adj(int v)
	{
		return adj[v];
	}
}


Now once the Graph is implemented. We will do a breadh First Search which will ensure that the shortest path is found between you and another person. 
The method hopTo(int v) will return the minimum hop between you (Source Vertex s in the graph) and any other person (vertex v)

public class BreadhFirstPath
{
	private boolean[] marked;
	private boolean[] edgeTo[];
	private final int s;
	
	private void bfs(Graph G, int s)
	{
		Queue<integer> q  = new Queue<integer>();
		q.enqueue(s);
		marked[s] = true;
		while (!q.isempty())
		{
			int v = q.dequeue();
			for(int w : G.adj(v)
			{
				if(!marked[w])
				{
					q.enqueue(w);
					marked[w] = true;
					edgeTo[w] = true;
				}
			}
		}
	}

	public boolean hasPathTo(int v)
	{ 
		return marked[v];
	}

	public int hopTo(int v)
	{
		int hop= -1;
		if(!haspathTo(v)) return 0;
		Stack<integer> path = new Stack<integer>();
		for (int x = v ; x!=s x = edgeTo[x])
			{
				hop++;
			}
		return hop; 
	}

	A sample client would look like this

	public static void main( int arg[])
	{
		int hops = -1;
		Graph G = new Graph(10); 
		G.add(0,1);
		G.add(0,2);
		G.add(2,7);
		....
		...
		
		BreadhFirstPath BFP = new BreadhFirstPath();
		BFP.bfs(G,0);
		hops = BFP.hopTo(0,7);
		
	}
}
