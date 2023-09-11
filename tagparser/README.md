# Opinionated Golang tag parser

## Quickstart

```go
func ExampleParse() {
	tag := tagparser.Parse("some_name,key:value,key2:'complex value'")
	fmt.Println(tag.Name)
	fmt.Println(tag.Options)
	// Output: some_name
	// map[key:value key2:'complex value']
}
```
