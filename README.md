# Maximum-Level-Sum-of-a-Binary-Tree

Given the root of a binary tree, the level of its root is 1, the level of its children is 2, and so on.

Return the smallest level x such that the sum of all the values of nodes at level x is maximal.

class Solution:
    def maxLevelSum(self, root: Optional[TreeNode]) -> int:
        if not root:
            return 0
        max_sum = float('-inf')
        max_level = 1

        q = deque([root])
        level = 1

        while q:
            size = len(q)
            total = 0
            leaf = []

            for _ in range(size):
                node = q.popleft()
                total += node.val

                if not node.left and not node.right:
                    leaf.append(node)
                if node.left:
                    q.append(node.left)
                if node.right:
                    q.append(node.right)
                
            if total > max_sum:
                max_sum = total
                max_level = level

            level += 1
            
        
        return max_level
