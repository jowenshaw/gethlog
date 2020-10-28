# Example

```golang
package main

import (
	"os"

	log "github.com/jowenshaw/gethlog"
)

func main() {
	mlog := log.New("module", "testlog")
	// the log has two output:
	// 1. to stderr with colored format
	// 2. to file with json format
	mlog.SetHandler(log.MultiHandler(
		log.StreamHandler(os.Stderr, log.TerminalFormat(true)),
		log.LvlFilterHandler(
			log.LvlInfo,
			log.Must.FileHandler("testlog.log", log.JSONFormat()))))

	mlog.Info("subject contest", "key1", "value1", "key2", "value2")

	m, n := 1, 2
	mlog.Info("print values", "m", m, "n", n)
}
```
