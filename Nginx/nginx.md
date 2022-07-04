# nginx


## 設定ファイル

nginx の動作は、設定ファイルによって規定される。
設定ファイルは、デフォルトで以下の場所に配置される。

- /usr/local/nginx/conf/nginx.conf
- /usr/local/etc/nginx/nginx.conf
- /etc/nginx/nginx.conf

## シグナル

`nginx`コマンドで`-s`オプションによってnginプロセスにシグナルを送りnginxにシグナルの動作をさせることができる。

> nginx -s *signal*

- stop — 直ちに終了
- quit — 現在のリクエストが終了次第終了
- reload — コンフィグファイルを再読み込み
- reopen — ログファイルを開き直す

# 参考

- [Beginner's Guide](http://nginx.org/en/docs/beginners_guide.html)
