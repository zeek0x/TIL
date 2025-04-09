# 命令

| 命令 | 名称 | 構文 | 説明 |
|------|------|------|------|
| hlt | Halt                  | `hlt`          | CPUを停止（アイドル）状態にし、割り込みが発生するまで待機する |
| lea | Load Effective Address | `lea dst, src` | src のメモリアドレス式（有効アドレス）を計算して、dst レジスタに格納する |
| in  | Input                 | `in dst, port` | 指定されたI/Oポート（port）から dst レジスタへ値を入力する |
| out | Output                | `out port, src`| 指定されたI/Oポートに src レジスタの値を書き込む |
| cli | Clear Interrupt       | `cli`          | 割り込みを禁止する（割り込みフラグをクリア）|
| sti | Set Interrupt         | `sti`          | 割り込みを許可する（割り込みフラグをセット）|
| call| Call Procedure        | `call target`  | 指定されたアドレス (target) にジャンプし、戻りアドレスをスタックに格納する（関数呼び出しに使用）|
| ret | Return                | `ret`          | スタックに保存された戻りアドレスを取り出し、そのアドレスへ制御を戻す（関数からの戻りに使用）|

# 関数プロローグ

以下のコードは、関数の始まりによく見られる関数プロローグと呼ばれる処理である。

```assembly
    push rbp
    mov rbp, rsp
```

関数呼び出し時に呼び出し元の位置である rbp をスタックに保存し、現在のスタックトップである rsp を rbp とすることでスタックポイントを更新する（rbp, rsp は [register.md](./register.md) を参照）。
