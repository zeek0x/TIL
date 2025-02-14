# 命令

| 命令 | 名称 | 構文 | 説明 |
| --- | --- | --- | --- |
| lea | Load Effective Address | `lea dst src` | src のメモリアドレス式（有効アドレス、Effective Address）の計算結果を、 dst のレジスタにロードする |
| in  |	Input | `in reg port` | I/Oポート(port で指定されるアドレス) からデータを読み込み、reg で指定されたレジスタに格納する。読み込むデータサイズはレジスタに依存（例: al=8bit, ax=16bit, eax=32bit）する|
| out | Output | `out port reg` | reg で指定されたレジスタの内容を、I/Oポート（port で指定されるアドレス）に書き出す。書き出すデータサイズはレジスタに依存する |

# 関数プロローグ

以下のコードは、関数の始まりによく見られる関数プロローグと呼ばれる処理である。

```assembly
    push rbp
    mov rbp, rsp
```

関数呼び出し時に呼び出し元の位置である rbp をスタックに保存し、現在のスタックトップである rsp を rbp とすることでスタックポイントを更新する（rbp, rsp は [register.md](./register.md) を参照）。
