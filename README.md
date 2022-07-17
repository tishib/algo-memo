# algo-memo
アルゴリズムに関する個人的な備忘録です。

### Dijkstra法 (WIP)
```
//
// 説明
//
TODO


//
// 実装
//
TDOO
#include <climits>
#include <queue>
#include <vector>

#include <cassert>
#include <iostream>

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
  // 3)
  std::priority_queue<Pair, std::vector<Pair>, std::greater<Pair>> pq;
  std::vector<int> dis;

  // 4)
  dis = std::vector<int>(g_size, INT_MAX);
  // 5)
  dis[start] = 0;
  pq.emplace(dis[start], start);
  while (!pq.empty()) {
    // 6)
    Pair p = pq.top();
    pq.pop();

    int idx = p.second;
    // 7)
    if (dis[idx] < p.first)
      continue;

    // 8) 現在のノードに隣接するノードをキューに追加する
    for (auto &&e : g[idx]) {
      if (dis[e.next] > dis[idx] + e.len) { // もっと短い経路が見つかったら、最短経路の配列dis[]の値を更新
	dis[e.next] = dis[idx] + e.len;
	pq.emplace(dis[e.next], e.next);
      }
    }
  }

  return dis;
}

int main(void) {
  // 1)
  Graph g = {
    {Edge(1,5), Edge(2,1), Edge(3,3)},
    {Edge(0,5), Edge(2,2)},
    {Edge(0,1), Edge(1,2)},
    {Edge(0,3), Edge(4,1)},
    {Edge(3,1)}
  };
  int start = 0;
  std::vector<int> dis;

  // 2)
  dis = dij(g, start);
  assert(dis[1] == 3);
  assert(dis[2] == 1);
  assert(dis[3] == 3);
  assert(dis[4] == 4);

  std::cout << "DONE";
  return 0;
}
```

### Kadane法 (WIP)
