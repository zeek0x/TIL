# echo

- https://echo.labstack.com/

## Echo は context の時点で URL エンコードがデコード済み

```go
package main

import (
	"net/http"

	"github.com/labstack/echo/v4"
)

type User struct {
	ID       int    `query:"id"`
	Name     string `query:"name"`
}

func main() {
	e := echo.New()
	e.GET("/", func(c echo.Context) error {
		u := &User{}
		if err := c.Bind(u); err != nil {
			return c.String(http.StatusBadRequest, "bad request")
		}
		return c.JSON(http.StatusOK, u)
	})
	e.Logger.Fatal(e.Start("127.0.0.1:1323"))
}
```

```console
$ curl -v -G -d 'id=123' --data-urlencode 'name=!@#$%^&*()_+|\=-' 'localhost:1323' | jq
*   Trying ::1:1323...
* connect to ::1 port 1323 failed: Connection refused
*   Trying 127.0.0.1:1323...
* Connected to localhost (127.0.0.1) port 1323 (#0)
> GET /?id=123&name=%21%40%23%24%25%5E%26%2A%28%29_%2B%7C%5C%3D- HTTP/1.1
> Host: localhost:1323
> User-Agent: curl/7.77.0
> Accept: */*
> 
* Mark bundle as not supporting multiuse
< HTTP/1.1 200 OK
< Content-Type: application/json; charset=UTF-8
< Date: Tue, 04 Oct 2022 12:40:41 GMT
< Content-Length: 43
< 
* Connection #0 to host localhost left intact
{
  "ID": 123,
  "Name": "!@#$%^&*()_+|\\=-"
}
```
