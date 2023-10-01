## CASE文を使ってソートでnullの位置を調整するクエリ（nullを先に表示したい）
* 新たにhoge_null_sortカラムを追加し、hogeがnullの場合は「1」、nullでない場合は「0」を持たせる
* あとはhoge_null_sortをDESCでソートしてやる。


```
$qb->addSelect('(CASE WHEN n.hoge IS NULL THEN 1 ELSE 0 END) AS HIDDEN hoge_null_sort')
   ->addOrderBy('hoge_null_sort', 'DESC')`
```