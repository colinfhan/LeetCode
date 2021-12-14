**Two pointer**  
---
**Basic idea**  
Double pointer sorting, note the critical points.  

Implementation
---
```java
class Solution {
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        int pc = m-- + n-- -1;
        while (m >= 0 && n >= 0) {
            nums1[pc--] = nums1[m] > nums2[n] ? nums1[m--] : nums2[n--];
        }
        while (n >= 0) {
            nums1[pc--] = nums2[n--];
        }
    }
}
```
**Appendix**
---
Focus on the point of examination of the topic.