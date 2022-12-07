# Hello World

hello-world.go

```golang
package main

import "fmt"

func main() {
	fmt.Println("hello world")
}
```

**go run** hello-world.go 명령어를 통해 프로그램 실행 가능

**go build** hello-world.go 명령어를 통해 바이너리 파일로 빌드 가능

# Values

```golang
package main

import "fmt"

func main() {
	fmt.Println("go" + "lang")

	fmt.Println("1+1 =", 1+1)
	fmt.Println("7.0/3.0 =", 7.0/3.0)

	fmt.Println(true && false)
	fmt.Println(true || false)
	fmt.Println(!true)
}
```

```golang
golang
1+1 = 2
7.0/3.0 = 2.3333333333333335
false
true
false
```

# Variables

```golang
package main

import (
	"fmt"
	"reflect"
)

func main() {
	var a = "initial"
	fmt.Println(reflect.TypeOf(a))

	var b, c int = 1, 2
	fmt.Println(b, c)

	var d = true
	fmt.Println(d)

	var e int
	fmt.Println(e)

	f := "apple"
	fmt.Println(f)
}
```

```golang
string
1 2
true
0
apple
```

**var** 키워드를 사용해 변수 선언

선언과 동시에 초기화할 때, 타입 명시 안해도 유추해서 타입 지정해준다.

여러 개의 변수 한 번에 초기화 가능

**:=** 키워드는 shortcut

# Constants

```golang
package main

import (
	"fmt"
	"math"
)

const s string = "constant"

func main() {
	fmt.Println(s)

	const n = 500000000000000

	const d = 3e20 / n
	fmt.Println(d)

	fmt.Println(int64(d))

	fmt.Println(math.Sin(n))
}
```

```
constant
600000
600000
-0.869825769274218
```

```golang
package main

import "fmt"

func main() {
	const Huge = 1e1000
	fmt.Println(Huge / 1e999)
}
```

```
10
```

**const** 키워드 사용해 상수 선언

**[Numeric constants represent exact values of arbitrary precision and do not overflow.](https://stackoverflow.com/questions/38982278/how-does-go-perform-arithmetic-on-constants)**

타입을 명시해주기 전까지는 타입 X

변수 선언 혹은 함수 호출 등의 상황에서 문맥에 따라 타입을 부여받을 수 있다.
