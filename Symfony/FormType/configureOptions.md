* FormTypeによってはconfigureOptionsを設定しない場合がある。

```
    /**
     * {@inheritdoc}
     */
    public function configureOptions(OptionsResolver $resolver)
    {
        // この設定がない
        $resolver->setDefaults([
            'data_class' => 'Eccube\Entity\Tag',
        ]);
    }
```
configureOptionsにエンティティを指定してやることで（setDefaults）、エンティティクラスのインスタンスに対応したFormTypeを作成することができる。
設定がない場合は、Controllerクラスやservicesクラスでformからデータを一つずつ取り出し、エンティティのインスタンスにsetしている。

```
// カテゴリの登録
// 一度クリア
/* @var $Product \Eccube\Entity\Product */
foreach ($Product->getProductCategories() as $ProductCategory) {
    $Product->removeProductCategory($ProductCategory);
    $this->entityManager->remove($ProductCategory);
}
$this->entityManager->persist($Product);
$this->entityManager->flush();
```

参考：EC-CUBE ProductController.php
https://github.com/EC-CUBE/ec-cube/blob/4.2/src/Eccube/Controller/ProductController.php