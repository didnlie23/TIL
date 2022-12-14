# ⭐️⭐️⭐️ A와 B 2

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;

public class Main {

    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        String S = br.readLine();
        String T = br.readLine();
        System.out.println(dfs(S, T) ? 1 : 0);
    }

    static public boolean dfs(String S, String T) {
        if (S.length() == T.length()) return S.equals(T);
        boolean case1 = false, case2 = false;
        if (T.charAt(0) == 'B') case1 = dfs(S, new StringBuilder(T).reverse().deleteCharAt(T.length() - 1).toString());
        if (T.charAt(T.length() - 1) == 'A') case2 = dfs(S, T.substring(0, T.length() - 1));
        return case1 || case2 || false;
    }
}
```

S에서 T를 만드는 것보다, **조건이 하나 더 추가**되기 때문에 T에서 S를 만드는 것이 더 빠르다.

- 문자열의 길이가 같으면 equals 함수 결과 반환
- 문자열의 뒤에 A를 추가한다. → 문자열의 끝이 A면 맨 뒤 A를 제거한다.
- 문자열의 뒤에 B를 추가하고 문자열을 뒤집는다. → 문자열의 앞이 B면 문자열의 뒤집고, 맨 뒤 B를 제거한다.
- **앞의 두 조건 모두 해당하지 않으면 바로 false 반환**
