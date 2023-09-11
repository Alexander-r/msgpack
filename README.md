# MessagePack encoding for Golang

## Features

- Primitives, arrays, maps, structs, time.Time and interface{}.
- Appengine \*datastore.Key and datastore.Cursor.
- [CustomEncoder]/[CustomDecoder] interfaces for custom encoding.
- [Extensions](https://pkg.go.dev/github.com/Alexander-r/msgpack#example-RegisterExt) to encode
  type information.
- Renaming fields via `msgpack:"my_field_name"` and alias via `msgpack:"alias:another_name"`.
- Omitting individual empty fields via `msgpack:",omitempty"` tag or all
  [empty fields in a struct](https://pkg.go.dev/github.com/Alexander-r/msgpack#example-Marshal-OmitEmpty).
- [Map keys sorting](https://pkg.go.dev/github.com/Alexander-r/msgpack#Encoder.SetSortMapKeys).
- Encoding/decoding all
  [structs as arrays](https://pkg.go.dev/github.com/Alexander-r/msgpack#Encoder.UseArrayEncodedStructs)
  or
  [individual structs](https://pkg.go.dev/github.com/Alexander-r/msgpack#example-Marshal-AsArray).
- [Encoder.SetCustomStructTag] with [Decoder.SetCustomStructTag] can turn msgpack into drop-in
  replacement for any tag.
- Simple but very fast and efficient
  [queries](https://pkg.go.dev/github.com/Alexander-r/msgpack#example-Decoder.Query).

[customencoder]: https://pkg.go.dev/github.com/Alexander-r/msgpack#CustomEncoder
[customdecoder]: https://pkg.go.dev/github.com/Alexander-r/msgpack#CustomDecoder
[encoder.setcustomstructtag]:
  https://pkg.go.dev/github.com/Alexander-r/msgpack#Encoder.SetCustomStructTag
[decoder.setcustomstructtag]:
  https://pkg.go.dev/github.com/Alexander-r/msgpack#Decoder.SetCustomStructTag

## Quickstart

```go
import "github.com/Alexander-r/msgpack"

func ExampleMarshal() {
    type Item struct {
        Foo string
    }

    b, err := msgpack.Marshal(&Item{Foo: "bar"})
    if err != nil {
        panic(err)
    }

    var item Item
    err = msgpack.Unmarshal(b, &item)
    if err != nil {
        panic(err)
    }
    fmt.Println(item.Foo)
    // Output: bar
}
```
