**String**  
---

Implementation
---
```java
class Solution {
    public List<String> mostVisitedPattern(String[] username, int[] timestamp, String[] website) {
        int n = username.length;
        Tuple[] tuples = new Tuple[n];
        for (int i = 0; i < n; ++i)
            tuples[i] = new Tuple(username[i], website[i], timestamp[i]);
        Arrays.sort(tuples, (t1, t2)->Integer.compare(t1.timestamp, t2.timestamp));

        Map<String, List<String>> visitMap = new HashMap<>();
        for (int i = 0; i < n; ++i) {
            if (visitMap.containsKey(tuples[i].username))
                visitMap.get(tuples[i].username).add(tuples[i].website);
            else {
                List<String> websiteList = new ArrayList<>();
                websiteList.add(tuples[i].website);
                visitMap.put(tuples[i].username, websiteList);
            }
        }

        Map<String, Set<String>> scoreCount = new HashMap<>();
        int highScore = Integer.MIN_VALUE;
        String highString = "";
        for (String name:visitMap.keySet()) {
            List<String> webs = visitMap.get(name);
            for (int i = 0; i < webs.size() - 2; i++) {
                for (int j = i+1; j < webs.size() - 1; j++) {
                    for (int k = j+1; k < webs.size(); k++) {
                        String current = webs.get(i) + "," + webs.get(j) + "," + webs.get(k);
                        if (scoreCount.containsKey(current) && scoreCount.get(current).contains(name)) {
                            continue;
                        } else if (scoreCount.containsKey(current) && !scoreCount.get(current).contains(name)) {
                            int currentScore = scoreCount.get(current).size() + 1;
                            scoreCount.get(current).add(name);
                            if (currentScore > highScore || (currentScore == highScore && (highString.isEmpty() || highString.compareTo(current) > 0))) {
                                highScore = currentScore;
                                highString = current;
                            }
                        } else {
                            Set<String> nameSet = new HashSet<>();
                            nameSet.add(name);
                            scoreCount.put(current, nameSet);
                            int currentScore = 1;
                            if (currentScore > highScore || (currentScore == highScore && (highString.isEmpty() || highString.compareTo(current) > 0))) {
                                highScore = currentScore;
                                highString = current;
                            }
                        }
                    }
                }
            }
        }

        return Arrays.stream(highString.split(",")).toList();
    }
}

class Tuple {
    String username;
    String website;
    int timestamp;

    public Tuple(String u, String w, int t) {
        username = u;
        website = w;
        timestamp = t;
    }
}
```
**Appendix**
---
None.
