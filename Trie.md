```python
class Trie:
    def __init__(self):
        self.root = {}
    
    def add(self, word):
        curr = self.root
        for ch in word:
            if ch not in curr:
                curr[ch] = {}
            curr = curr[ch]
        curr['#'] = True
    
    def start_with(self, left_part):
        res = []
        curr = self.root
        for ch in left_part:
            if ch not in curr:
                return []
            curr = curr[ch]
        
        def dfs(node, right_part):
            if '#' in node:
                res.append(left_part + right_part)
                return
            for ch in node:
                dfs(node[ch], right_part + ch)
        
        dfs(curr, '')
        return res
```
