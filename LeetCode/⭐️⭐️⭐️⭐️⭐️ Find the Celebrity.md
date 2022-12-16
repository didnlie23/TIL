# ⭐️⭐️⭐️⭐️⭐️ Find the Celebrity.md

```java
/* The knows API is defined in the parent class Relation.
      boolean knows(int a, int b); */

public class Solution extends Relation {
    public int findCelebrity(int n) {
        int candidate = 0;
        for (int i = 0; i < n; i++) {
            if (knows(candidate, i)) {
                candidate = i;
            }
        }
        return isCelebrity(n, candidate) ? candidate : -1;
    }

    public boolean isCelebrity(int n, int candidate) {
        for (int i = 0; i < n; i++) {
            if (i == candidate) continue;
            if (!knows(i, candidate) || knows(candidate, i)) return false;
        }
        return true;
    }
}
```

`knows(A, B)`값이 `true`일 경우 A는 Celebrity 후보에서 탈락,

`false`일 경우 B가 Celebrity 후보에서 탈락

**후보가 될 사람을 찾는 반복문 구현이 어려웠다.**
