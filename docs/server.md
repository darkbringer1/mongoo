## Package `main`

The `main` package is the entry point for the executable program. In this case, the program creates a GraphQL server using the `github.com/99designs/gqlgen` and `github.com/darkbringer1/mongoo/graph` packages.

### Function `main()`

This function sets up the server and starts listening for incoming requests.

#### Parameters

None.

#### Returns

None.

#### Example

```go
package main

import (
	"log"
	"github.com/darkbringer1/mongoo/graph"
	"net/http"
	"os"

	"github.com/99designs/gqlgen/graphql/handler"
	"github.com/99designs/gqlgen/graphql/playground"
)

const defaultPort = "8080"

func main() {
	port := os.Getenv("PORT")
	if port == "" {
		port = defaultPort
	}

	srv := handler.NewDefaultServer(graph.NewExecutableSchema(graph.Config{Resolvers: &graph.Resolver{}}))

	http.Handle("/", playground.Handler("GraphQL playground", "/query"))
	http.Handle("/query", srv)

	log.Printf("connect to http://localhost:%s/ for GraphQL playground", port)
	log.Fatal(http.ListenAndServe(":"+port, nil))
}
``` 

In this example, the main function sets up a GraphQL server and starts listening for incoming requests on the default port 8080.