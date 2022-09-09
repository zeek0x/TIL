# Unmarshal v.s. NewDecoder

[encoding/json](https://pkg.go.dev/encoding/json)や[yaml.v3](https://pkg.go.dev/gopkg.in/yaml.v3)パッケージには、ファイルの各データ表現から Go のデータ表現へと適用する方法として、 `Unmarshal` 関数を用いる方法と `NewDecoder` 関数を用いる方法がある。

- `Unmarshal` 関数を用いる方法

```go
func ReadJson[T any](path string) (ret *T, err error) {
	data, err := os.ReadFile(path)

	if err != nil {
		return ret, err
	}

	if err := json.Unmarshal(data, ret); err != nil {
		return ret, err
	}
	return ret, nil
}
```

- `NewDecoder`を用いる方法

```go
func ReadJson[T any](path string) (ret *T, err error) {
	file, err := os.Open(path)
	if err != nil {
		return nil, err
	}
	defer file.Close()

	decoder := json.NewDecoder(file)
	if err := decoder.Decode(&ret); err != nil {
		return nil, err
	}
	return ret, nil
}
```

## どうするべきか？

- データが `io.Reader` ストリームから取得されている、またはデータストリームから複数の値をデコードする必要がある場合は `NewDecoder` 関数を持ちる方法を使用する。
- データが既にメモリ内にある場合 `Unmarshal` 関数を用いる方法を使用する。

# 参考

- [Decoding JSON using json.Unmarshal vs json.NewDecoder.Decode](https://stackoverflow.com/questions/21197239/decoding-json-using-json-unmarshal-vs-json-newdecoder-decode)
