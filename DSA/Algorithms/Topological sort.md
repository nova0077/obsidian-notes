The **_topological sorting_** of a directed acyclic graph is nothing but the linear ordering of vertices such that if there is an edge between node u and v(u -> v), node u appears before v in that ordering.

### Using DFS
```cpp
void dfs(int node, int vis[], stack<int> &st, vector<int> adj[]) {
	vis[node] = 1;
	for (auto it : adj[node]) {
		if (!vis[it]) dfs(it, vis, st, adj);
	}
	st.push(node);
}
vector<int> topoSort(int V, vector<int> adj[])
{
	int vis[V] = {0};
	stack<int> st;
	for (int i = 0; i < V; i++) {
		if (!vis[i]) {
			dfs(i, vis, st, adj);
		}
	}

	vector<int> ans;
	while (!st.empty()) {
		ans.push_back(st.top());
		st.pop();
	}
	return ans;
}
```
TC: O(V+E)

### Using BFS
```cpp
vector<int> topologicalSort(int V, vector<vector<int>>& adj)
{
    vector<int> in_degree(V, 0);
    for (int v = 0; v < V; ++v) {
        for (auto const& w : adj[v])
            in_degree[w]++;
    }

    queue<int> q;
    for (int i = 0; i < V; ++i) {
        if (in_degree[i] == 0)
            q.push(i);
    }

    int count = 0;
    vector<int> top_order;
    while (!q.empty()) {
        int u = q.front();
        q.pop();
        top_order.push_back(u);
        list<int>::iterator itr;
        for (itr = adj[u].begin(); itr != adj[u].end();
             ++itr)
            if (--in_degree[*itr] == 0)
                q.push(*itr);

        count++;
    }
    if (count != V) {
        cout << "Graph contains cycle\n";
        return;
    }
	return top_order;
}
```
TC: O(V + E), where V is the number of vertices and E is the number of edges.