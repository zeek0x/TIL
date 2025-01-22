# Context の Err ハンドリング

- cancel() が呼ばれると `context.Canceld` が `Err` に入る

```go
  ctx := context.Background()
  ctx, cancel := context.WithTimeout(ctx, time.Second)
  cancel()
  errors.Is(ctx.Err(), context.Canceled) -> // false
  errors.Is(ctx.Err(), context.DeadlineExceeded) // true
```

- タイムアウトすると `context.DeadlineExceeded` が `Err` に入る

```go
  ctx := context.Background()
  ctx, cancel := context.WithTimeout(ctx, time.Second)
  time.Sleep(2 * time.Second)
  errors.Is(ctx.Err(), context.Canceled) // false
  errors.Is(ctx.Err(), context.DeadlineExceeded) // true
```
