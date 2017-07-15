# go-whosonfirst-geojson-v2

Go tools for working with Who's On First documents

## Install

You will need to have both `Go` (specifically a version of Go more recent than 1.6 so let's just assume you need [Go 1.8](https://golang.org/dl/) or higher) and the `make` programs installed on your computer. Assuming you do just type:

```
make bin
```

All of this package's dependencies are bundled with the code in the `vendor` directory.

## Important

This is work in progress. It may change (and break your code) still. This package aims to replace the existing [go-whosonfirst-geojson](https://github.com/whosonfirst/go-whosonfirst-geojson) package.

## geojson-v2?

Yeah, I don't really like it either but this package is basically 100% backwards incompatible with `github.com/whosonfirst/go-whosonfirst-geojson` and while I don't _really_ think anyone else is using it I don't like the idea of suddenly breaking everyone's code.

## Interfaces

Unlike the first `go-whosonfirst-geojson` package this one at least attempts to define a simplified interface for working with GeoJSON features.

_Please finish writing me._

### geojson.Feature

```
type Feature interface {
	Type() string
	Id() int64
	Name() string
	Placetype() string
	ToString() string
	ToBytes() []byte
	Bounds() (Bounds, error)
	Polygons() ([]Polygon, error)
}
```

## Usage

### Simple

```
import (
	"github.com/whosonfirst/go-whosonfirst-geojson-v2/whosonfirst"
	"log"
)

func main() {

	path := "/usr/local/data/whosonfirst-data/data/101/736/545/101736545.geojson"
	f, err := whosonfirst.LoadFeatureFromFile(path)

	if err != nil {
		log.Fatal(err)
	}

	// prints "Montreal"
	log.Println("Name is ", f.Name())
}
```

## See also

* https://github.com/whosonfirst/go-whosonfirst-geojson
