# Symfony FormEventsについて
## POST_SET_DATA

以下Controllerクラス内にdumpを仕込んで、
POST_SET_DATAイベントがどのタイミングで処理されているか確認。
POST_SET_DATAの処理は、ContactTypeクラス内に記述。

```
dump('createBuilder前');
$builder = $this->formFactory
    ->createBuilder(ContactType::class, $Contact);
dump('createBuilder後');

dump('getForm前');
$form = $builder->getForm();
dump('getForm後');

dump('handleRequest前');
$form->handleRequest($request);
dump('handleRequest後');
```

結果、getForm後の前に実行されていた。
getForm内でsetDataが呼び出される処理があり、
そのsetDataにより、POST_SET_DATAイベントが呼び出されているよう。（form生成時に呼び出される。）

以下referrences参考。

references
* https://symfony.com/doc/current/form/events.html#1-pre-populating-the-form-formevents-pre-set-data-and-formevents-post-set-data
* https://github.com/symfony/symfony/blob/6.3/src/Symfony/Component/Form/Form.php#L334
* https://qiita.com/yutachaos/items/a5d2ee34fdf40c2b701f