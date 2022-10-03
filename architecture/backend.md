# サーバポート構成

一般的な HTTP サーバではサービスのエンドポイント以外にもメトリクスの監視やヘルスチェック、管理用のエンドポイントがあったりする。
これらのエンドポイントは、ユーザに見られたくないケースが多いためアクセス制御が行われることが多い。
アクセス制御の方法として、サービスのエンドポイントとはポートを分ける方法がある。
この方法のいいところは、サーバの前段にL４LBがあった時にアクセス制御がやりやすいということにある。
もし同一ポートである場合、パスによってアクセスを振り分けるL7LBを使用したり、サーバ側で認証を行う必要があったりする。

Go の Web Framework である [echo](https://echo.labstack.com/)　で Prometheus によるメトリクス提供をサービスと分ける例を示す。
コード引用元：　https://echo.labstack.com/middleware/prometheus/#complex-scenarios

```go
package main

import (
	"net/http"

	"github.com/labstack/echo-contrib/prometheus"
	"github.com/labstack/echo/v4"
	"github.com/labstack/echo/v4/middleware"
)

func main() {
	// Setup Main Server
	echoMainServer := echo.New()
	echoMainServer.HideBanner = true
	echoMainServer.Use(middleware.Logger())
	echoMainServer.GET("/", hello)

	// Create Prometheus server and Middleware
	echoPrometheus := echo.New()
	echoPrometheus.HideBanner = true
	prom := prometheus.NewPrometheus("echo", nil)

	// Scrape metrics from Main Server
	echoMainServer.Use(prom.HandlerFunc)
	// Setup metrics endpoint at another server
	prom.SetMetricsPath(echoPrometheus)

	go func() { echoPrometheus.Logger.Fatal(echoPrometheus.Start(":9360")) }()

	echoMainServer.Logger.Fatal(echoMainServer.Start(":8080"))
}

func hello(c echo.Context) error {
	return c.String(http.StatusOK, "Hello, World!")
}

```

# 参考

- [do_you_use_a_different_port_for_exposing_metrics](https://www.reddit.com/r/microservices/comments/c5qpov/do_you_use_a_different_port_for_exposing_metrics)
