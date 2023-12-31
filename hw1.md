### ФИО: Камаргин Роман Максимович
### Класс: 9Ф

# Golang - основы (ДЗ № 1)
## 1. Линейное уравнение
```golang
package main

import "fmt"

func main() {
	var a, b int
	fmt.Scan(&a, &b)

	if a == 0 && b == 0 {
		fmt.Println("INF")
	} else if a == 0 {
		fmt.Println("NO")
	} else if b % a == 0 {
		fmt.Println(-b / a)
	} else {
		fmt.Println("NO")
	}
}
```

## 2. Часы - 1
```golang
package main

import "fmt"

func main() {
	var k int
	fmt.Scan(&k)

	h := k / 3600
	m := (k % 3600) / 60

	fmt.Printf("It is %d hours %d minutes.", h, m)
}
```

## 3. Часы - 2
```golang
package main

import "fmt"

func main() {
	var h1, m1, s1 int
	var h2, m2, s2 int

	fmt.Scan(&h1, &m1, &s1, &h2, &m2, &s2)

	fmt.Println(3600 * (h2 - h1) + 60 * (m2 - m1) + (s2 - s1))
}
```

## 4. Квадратное уравнение
```golang
package main

import (
	"fmt"
	"math/cmplx"
)

func main() {
	var a, b, c float64

	fmt.Scan(&a, &b, &c)

	if a == 0 {
		if b == 0 && c == 0 {
			fmt.Println("#-1")
		} else if b == 0 {
			fmt.Println("#0")
		} else {
			fmt.Printf("#1: %.3v\n", -c / b)
		}
	} else {
		d  := b * b - 4 * a * c
		x1 := (complex(-b, 0) + cmplx.Sqrt(complex(d, 0))) / complex(2 * a, 0)
		x2 := (complex(-b, 0) - cmplx.Sqrt(complex(d, 0))) / complex(2 * a, 0)
		if d > 0 {
			fmt.Printf("#4: %.3v, %.3v\n", real(x1), real(x2))
		} else if d == 0 {
			fmt.Printf("#3: %.3v\n", real(x1))
		} else {
			fmt.Printf("#5(complex answer): %.3v, %.3v\n", x1, x2)
		}
	}
}
```

## 5. Простой for
```golang
package main

import "fmt"

func main() {
	var n, c int
	fmt.Scan(&n)
	for ; n > 0; n -- {
		var num int
		fmt.Scan(&num)
		if num == 0 {
			c++
		}
	}
	fmt.Println(c)
}
```

## 6. Степени двойки
```golang
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)
	for k := 1; k < n; k *= 2 {
		fmt.Println(k)
	}
}
```

## 7. Количество делителей
```golang
package main

import "fmt"

func main() {
	var n, c int
	fmt.Scan(&n)
	for i := 1; i <= n; i++ {
		if n % i == 0 {
			c++
		}
	}
	fmt.Println(c)
// второй вариант в разы быстрее для больших чисел
// 	var n int
// 	fmt.Scan(&n)
// 	var power = make(map[int]int)
// loop:
// 	for {
// 		for i := 2; ; i++ {
// 			if i <= n {
// 				if n % i == 0 {
// 					power[i]++
// 					n /= i
// 					continue loop
// 				}
// 			} else {
// 				break loop
// 			}
// 		}
// 	}
// 	var c = 1
// 	for _, v := range power {
// 		c *= v + 1
// 	}
// 	fmt.Println(c)
}
```

## 8. Кубическое уравнение
```golang
package main

import "fmt"

func main() {
	var a, b, c, d int
	fmt.Scan(&a, &b, &c, &d)

	for x := 0; x <= 1000; x++ {
		if a * x * x * x + b * x * x + c * x + d == 0 {
			fmt.Println(x)
		}
	}
}
```

## 9. Числа Фибоначчи
```golang
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	a, b := 0, 1
	for i := 0; i < n; i++ {
		a, b = b, a + b
	}
	fmt.Println(a)
}
```

## 10. Часы - 3
```golang
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	n %= 24 * 60 * 60

	fmt.Printf("%d:%02d:%02d", n / 3600, (n % 3600) / 60, n % 60)
}
```

## 11*. Количество членов
```golang
package main

import "fmt"

func main() {
	var max, prev, count int
	for {
		var n int 
		fmt.Scan(&n)

		if n == 0 {
			break
		}

		if n != prev {
			count = 1
		} else {
			count++
		}
		
		if count > max {
			max = count
		}
		prev = n
	}
	fmt.Println(max)
}
```
