## オブジェクトをjson形式で保存する方法

オブジェクトの場合、プロパティがpriveteだとエンコードが上手くいかず、
空オブジェクトとして登録されてしまう為、serializeで一旦文字列にしてから、エンコードしてやる。


```

foreach ($searchData as $key => $value) {
    // オブジェクトの場合、プロパティがpublicでエンコードが上手くいかない場合がある為シリアライズ化する
    if (is_object($value)) {
        $searchData[$key] = serialize($value);
    }
}

$SearchConditions = new SearchConditions;
$SearchConditions->setSearchConditions(json_encode($searchData));

$this->entityManager->persist($SearchConditions);
$this->entityManager->flush();

$SearchConditions = $this->searchConditionsRepository->findOneBy([],['id' => 'DESC']);

//配列にデコード
$searchConditionsArray =  json_decode($searchConditions->getSearchConditions(), true);
foreach ($searchConditionsArray as $key => $value) {
    //serializeでシリアライズ化したオブジェクトをunserializeする
    // reference to the is_serialized：https://developer.wordpress.org/reference/functions/is_serialized/
    if ($this->is_serialized($value)) {
        $searchConditionsArray[$key] = unserialize($value);
    }
}

reference：
https://www.php.net/manual/ja/function.serialize.php
https://www.php.net/manual/ja/function.json-encode.php

