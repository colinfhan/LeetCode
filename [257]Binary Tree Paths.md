**Searching**  
---
**Basic idea**  
BackTracking.

Implementation
---
```java
class Solution {
    public List<String> binaryTreePaths(TreeNode root) {
        List<Integer> currentPath = new ArrayList<>();
        List<String> ret = new ArrayList<>();
        findPath(root, currentPath, ret);
        return ret;
    }

    public void findPath(TreeNode node, List<Integer> currentPath, List<String> ret) {
        if (node==null)
            return;
        if (node.left==null && node.right==null) {
            currentPath.add(node.val);
            ret.add(composePath(currentPath));
            currentPath.remove(currentPath.size()-1);
            return;
        }
        currentPath.add(node.val);
        findPath(node.left, currentPath, ret);
        findPath(node.right, currentPath, ret);
        currentPath.remove(currentPath.size()-1);
    }

    public String composePath(List<Integer> currentPath) {
        if (currentPath.size() < 1)
            return "";
        if (currentPath.size() == 1)
            return currentPath.get(0).toString();
        StringBuilder sb = new StringBuilder();
        for (int i = 0; i < currentPath.size() - 1; ++i) {
            sb.append(currentPath.get(i).toString());
            sb.append("->");
        }
        sb.append(currentPath.get(currentPath.size()-1).toString());
        return sb.toString();
    }
}
```
**Appendix**
---
None.