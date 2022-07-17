# algo
アルゴリズムに関する個人的なメモ。

### Dijkstra法 (WIP)
```
//
// 説明
//
TODO


//
// 実装
//
#include <climits>
#include <queue>
#include <vector>

class Edge {
public:
  int next;
  int len;
  Edge(int a, int b) : next(a), len(b) {}
};

using Graph = std::vector<std::vector<Edge>>;
using Pair = std::pair<int, int>; // dis[i], i

std::vector<int> dij(Graph &g, int start) {
  int g_size = g.size();
  std::priority_queue<Pair, std::vector<Pair>, std::greater<Pair>> pq;
  std::vector<int> dis;

  dis = std::vector<int>(g_size, INT_MAX);
  dis[0] = 0;
  pq.emplace(dis[start], start);
  while (!pq.empty()) {
    Pair p = pq.top();
    pq.pop();

    int idx = p.second();
    if (dis[idx] < p.first)
      continue;

    //
    // TODO
  }

  return dis;
}

int main(void) {
  Graph g = {
    {Edge(1,5), Edge(2,1), Edge(3,3)},
    {Edge(0,5), Edge(2,2)},
    {Edge(0,1), Edge(1,2)},
    {Edge(0,3), Edge(4,1)},
    {Edge(3,1)}
  };
  int start = 0;
  std::vector<int> dis;

  dij(g, start, dis);
  return 0;
}
```

### Kadane法 (WIP)