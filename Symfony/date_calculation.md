# 日付の取得
## date関数とstrotime関数

```
// 前日
date('Y-m-d 00:00', strtotime('-1 day'));
// 前々日
date('Y-m-d 00:00', strtotime('-2 day'));
// 7日前
date('Y-m-d 00:00', strtotime('-1 week'));
// 当月1日
date('Y-m-d 00:00', strtotime('first day of this month'))
// 前月1日
date('Y-m-d 00:00', strtotime('first day of previous month'));
```
## DateTimeオブジェクトのmodifyメソッド
以下modifyメソッドでも取得可能
```
$today = new DateTime();

// 前日
today->modify("-1 day")->format('Y-m-d 00:00');
```

### 参考サイト
* https://qiita.com/thiagomatsui/items/619775a96dce38bc5060
* https://blog-and-destroy.com/17287
* https://www.php.net/manual/ja/datetime.modify.php
* https://www.php.net/manual/ja/function.strtotime.php