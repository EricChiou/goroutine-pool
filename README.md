# goroutinepool
## How to use
```go
package main

import (
	"fmt"

	"github.com/EricChiou/goroutinepool"
)

func main() {
	pool := goroutinepool.New(5) // new gorotine pool has 5 gorotine
	for i := 0; i < 1000; i++ {
		pool.Add()
		go func(i int) {
			fmt.Println("gorotine ", i)
			pool.Done()
		}(i)
	}
	pool.Wait()
}
```
