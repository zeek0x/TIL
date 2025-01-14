# 関数プロローグ

以下のコードは、関数の始まりによく見られる関数プロローグと呼ばれる処理である。

```assembly
    push rbp
    mov rbp, rsp
```

関数呼び出し時に呼び出し元の位置である rbp をスタックに保存し、現在のスタックトップである rsp を rbp とすることでスタックポイントを更新する（rbp, rsp は [register.md](./regsiter.md) を参照）。
