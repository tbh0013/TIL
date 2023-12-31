# PHPのファイルアップロードサイズを変更する方法

## PHP設定ファイルの優先順位
* php.ini < httpd.conf < .htaccess < ini_set()
    * 右の設定値が後から読み込まれ、左の設定値を上書きする。
    * php.iniに書かれた設定値はMasterValueとなる
    * php.ini以外に書かれた設定値はLocalValueとなる
    * LocalValueの値が優先される（値はphp.infoで確認できる）
## 設定値を変更する
* 上記ファイルに記載されたmemory_limit・post_max_size・upload_max_filesizeの設定値を変更する。
* 上記設定値の優先順位は以下の通り
    * memory_limit　>　post_max_size　> upload_max_filesize
* apacheを再起動する
    * sudo systemctl restart apache2

## 参考
* https://qiita.com/yamadayamada_jp/items/22b358e2c8389d1e31dd
* https://web.syu-u.com/blog/?p=1672
* https://www.php.net/manual/ja/features.file-upload.common-pitfalls.php

test