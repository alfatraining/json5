Extended json with json5 flavour for go
================

Copied from yosuke-furukawa's amazing [json5](https://github.com/yosuke-furukawa/json5) github project.
It isn't forked because the repo containes over 38 Megabytes of binary data in it's history.

[JSON5](https://github.com/aseemk/json5) is Yet another JSON.

# HOW TO USE

```
$ json5 -c path/to/test.json5 # output stdout
$ json5 -c path/to/test.json5 -o path/to/test.json # output path/to/test.json
```

# go get
```
$ go get github.com/alfatraining/json5
```

# example

```go
package main

import (
	"encoding/json"
	"fmt"
	"github.com/alfatraining/json5/encoding/json5"
	"os"
)

func main() {
	var data interface{}
	dec := json5.NewDecoder(os.Stdin)
	err := dec.Decode(&data)
	if err != nil {
		fmt.Println(err)
	}
	b, err := json.MarshalIndent(data, "", "    ")
	if err != nil {
		fmt.Println(err)
	}
	fmt.Println(string(b))
}
```

```js
// This is json5 demo
// json5 can write comment in your json
{
  key : "Key does not need double quote",
  // json specific
  "of" : "course we can use json as json5",
  trailing : "trailing comma is ok",
}
```

```
$ json5 -c example.json5
# output
#{
#    "key": "Key does not need double quote",
#    "of": "course we can use json as json5",
#    "trailing": "trailing comma is ok"
#}
```

# TODO
- block comment
- multiline string
- hexadecimal notation



