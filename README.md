## gooorm

gooorm is a simple orm framework written in Go (Golang). Used to learn and understand the principles of orm, the code comes from [geektutu/7days-golang](https://github.com/geektutu/7days-golang)

## Usage

```go
package main

import (
	"fmt"
	_ "github.com/mattn/go-sqlite3"
	"gooorm/gooorm"
)

func main() {
	engine, _ := gooorm.NewEngine("sqlite3", "gooorm.db")
	defer engine.Close()
	s := engine.NewSession()
	_, _ = s.Raw("DROP TABLE IF EXISTS User;").Exec()
	_, _ = s.Raw("CREATE TABLE User(Name text);").Exec()
	_, _ = s.Raw("CREATE TABLE User(Name text);").Exec()
	result, _ := s.Raw("INSERT INTO User(`Name`) values (?), (?)", "Tom", "Sam").Exec()
	count, _ := result.RowsAffected()
	fmt.Printf("Exec success, %d affected\n", count)
}
```
