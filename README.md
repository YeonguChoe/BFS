# Breadth-first search

```cpp
struct Node
{
    int val;
    vector<int> adjacent_node; // 인접 노드를 저장하는 vector

    Node(int value) : val(value) {} // 생성자
};

void bfs(Node &node)
{
    int number_of_nodes = node.adjacent_node.size() + 1;
    vector<bool> visited(number_of_nodes, false);
    vector<int> distance(number_of_nodes, -1);

    queue<int> q;
    visited[node.val] = true;
    distance[node.val] = 0;

    q.push(node.val);

    while (!q.empty())
    {
        int s = q.front();
        q.pop();

        for (int u : node.adjacent_node)
        {
            if (visited[u])
            {
                continue;
            }
            visited[u] = true;
            distance[u] = distance[s] + 1;
            q.push(u);
        }
    }
}
```
