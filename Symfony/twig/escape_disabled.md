# twigで自動エスケープを無効化する
* twigはautoescapeが有効になっている為、以下rawフィルターを使用して、自動エスケープを無効化する。

```
{{ hoge|raw }}

自動改行<br>を入れたい場合はnl2brフィルダーを使用する。

{{ hoge|raw|nl2br }}
```

# 参考サイト
https://noveblo.com/eccube-twig-filter/