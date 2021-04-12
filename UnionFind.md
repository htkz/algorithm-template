### Union Find
```python
class UnionFind:
    def __init__(self):
        self.groups = {}
        self.ranks = {}
    
    def find(self, x):
        self.groups.setdefault(x, x)
        self.ranks.setdefault(x, 1)
        
        while self.groups[x] != x:
            x = self.groups[x]
        return x
    
    def union(self, x, y):
        px, py = self.find(x), self.find(y)
        if px != py:
            if self.ranks[px] < self.ranks[py]:
                px, py = py, px
            self.groups[py] = px
            self.ranks[px] += self.ranks[py]
```
