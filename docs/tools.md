# `tools` package

This package contains tools that are used in the development of the project. 

## `go:build tools`
This build tag is used to mark dependencies in the `tools.go` file.

## `+build tools`
This build tag is used to enable building of packages with the `tools` tag.

## Imported package

### `github.com/99designs/gqlgen`

This package is used for GraphQL server implementation.

Example usage:

```go
import (
  "github.com/99designs/gqlgen"
)
```

Note: The above code is just an import example, and can't be used. Please refer to the documentation of the respective library for usage examples.