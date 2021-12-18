**Searching**  
---
**Basic idea**  
DFS+BFS.

Implementation
---
backtracing
```java
class Solution {
    int length = 1000;
    public List<List<String>> findLadders(String beginWord, String endWord, List<String> wordList) {
        wordList.remove(beginWord);
        List<List<String>> ret = new ArrayList<>();
        int n = wordList.size();
        boolean[] tested = new boolean[n];
        Arrays.fill(tested, false);
        List<String> local = new ArrayList<>();
        local.add(beginWord);
        backtracing(beginWord, endWord, wordList, tested, local, ret);
        List<List<String>> ret2 = new ArrayList<>();
        getRet(ret, ret2);
        return ret2;
    }

    public void backtracing(String currentWord, String endWord, List<String> wordList, boolean[] tested, List<String> local,List<List<String>> ret) {
        if (local.size()>length)
            return;
        if (!local.isEmpty() && local.get(local.size()-1).compareTo(endWord) == 0) {
            copyRet(ret, local);
            length = Math.min(local.size(), length);
            return;
        }
        for (int i = 0; i < tested.length; ++i) {
            if (tested[i] == false && oneDiff(currentWord, wordList.get(i))) {
                tested[i] = true;
                local.add(wordList.get(i));
                backtracing(wordList.get(i), endWord, wordList, tested, local, ret);
                tested[i] = false;
                local.remove(wordList.get(i));
            }
        }
    }

    public boolean oneDiff(String str1, String str2) {
        if (str1.length() != str2.length())
            return false;
        int count = 0;
        for (int i = 0; i < str1.length(); ++i) {
            if (str1.charAt(i) != str2.charAt(i))
                ++count;
            if (count > 1)
                break;
        }
        return count<2;
    }

    public void copyRet(List<List<String>> ret, List<String> local) {
        List<String> temp = new ArrayList<>();
        for(String s:local)
            temp.add(s);
        ret.add(temp);
    }

    public void getRet(List<List<String>> ret, List<List<String>> ret2) {
        for (var l:ret)
            if (l.size() == length)
                ret2.add(l);
    }
}
```
BFS
```java
class Solution {

    public List<List<String>> findLadders(String beginWord, String endWord, List<String> wordList) {
        List<List<String>> res = new ArrayList<>();
        Set<String> dict = new HashSet<>(wordList);
        if (!dict.contains(endWord)) {
            return res;
        }

        dict.remove(beginWord);

        Map<String, Integer> steps = new HashMap<>();
        steps.put(beginWord, 0);
        Map<String, List<String>> from = new HashMap<>();
        int step = 1;
        boolean found = false;
        int wordLen = beginWord.length();
        Queue<String> queue = new LinkedList<>();
        queue.offer(beginWord);
        while (!queue.isEmpty()) {
            int size = queue.size();
            for (int i = 0; i < size; i++) {
                String currWord = queue.poll();
                char[] charArray = currWord.toCharArray();
                for (int j = 0; j < wordLen; j++) {
                    char origin = charArray[j];
                    for (char c = 'a'; c <= 'z'; c++) {
                        charArray[j] = c;
                        String nextWord = String.valueOf(charArray);
                        if (steps.containsKey(nextWord) && step == steps.get(nextWord)) {
                            from.get(nextWord).add(currWord);
                        }
                        if (!dict.contains(nextWord)) {
                            continue;
                        }
                        dict.remove(nextWord);
                        queue.offer(nextWord);

                        from.putIfAbsent(nextWord, new ArrayList<>());
                        from.get(nextWord).add(currWord);
                        steps.put(nextWord, step);
                        if (nextWord.equals(endWord)) {
                            found = true;
                        }
                    }
                    charArray[j] = origin;
                }
            }
            step++;
            if (found) {
                break;
            }
        }

        if (found) {
            Deque<String> path = new ArrayDeque<>();
            path.add(endWord);
            dfs(from, path, beginWord, endWord, res);
        }
        return res;
    }

    public void dfs(Map<String, List<String>> from, Deque<String> path, String beginWord, String cur, List<List<String>> res) {
        if (cur.equals(beginWord)) {
            res.add(new ArrayList<>(path));
            return;
        }
        for (String precursor : from.get(cur)) {
            path.addFirst(precursor);
            dfs(from, path, beginWord, precursor, res);
            path.removeFirst();
        }
    }
}
```
**Appendix**
---
None.