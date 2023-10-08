### コンストラクタインジェクションについて

PersonControllerクラスの処理の中で、PersonRepositoryクラスをnew(インスタンス化)していない。
constructの引数にPersonRepositoryを指定することで、PersonRepositoryのインスタンスを受け取る為、newは不要と理解
。
```
class PersonController extends AbstractController
{
    /**
     * @var PersonRepository
     */
    protected $personRepository;

    public function __construct(PersonRepository $personRepository)
    {
        $this->personRepository = $personRepository;
    }

    public function index()
    {
        $Persons = $this->personRepository->getList();
    }
```

参考記事：https://zenn.dev/miya_tech/articles/ed6570097d7673


