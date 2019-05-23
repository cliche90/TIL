# How to use Selector?

## *Have to Read

> 기본적으로 CouchDB 는 NoSQL DB 이기 때문에 **오해하기가 쉬운 부분은 데이터의 관리 단위가 Column 이 아니라, Row 라는 점**이다. 애초에 Selector를 사용하여 조회를 하더라도 Row 단위로 Key-Value 가 구분되어있지 않으면 원하는 결과를 얻을 수 없을 것이다.

예를 들어 `users` 라는 key 값에 아래와 같은 값을 marshal (serialize) 하여 넣었다고 하자.

```json
{
 	"userList": [
        {
            "userId": "user001",
            "nickname": "A",
            "age": 19,
            "hobbies": ["coding", "reading"]
        },
        {
            "userId": "user002",
            "nickname": "B",
            "age": 22,
            "hobbies": ["fishing"]
        }
	]
}
```

쿼리를 작성하는 사람은 `hobbies` 중에 `coding` 을 가진 사람만을 조회하고 싶었기 때문에, selector 를 활용하여 아래와 같이 조회할 것이다. (문법에 대한 설명은 별도로)

```json
{
	"_id": "users",
	"selector": {
		"userList": {
			"$elemMatch": {
                "hobbies": {
                    "$in": ["coding"]
                }
        	}
		}
	}
}
```

위 쿼리를 단순히 문법에만 비추어 본다면  `users` 라는 key 값에 저장된 value 에서 selector 를 통하여 필터링 한다는 것이다. 이 말을 처음에 생각해보면 아무 문제도 없는 것 같다. 그러나 실제로 쿼리를 수행해보면 `hobbies` 로 `coding` 을 가진 사람이 들어있으면 무조건  `users` 전체 값이 조회가 되어나온다. 

왜일까?

여기서 알아야 할 것은 이 단락의 맨 위에 적어두었듯이 NoSQL DB는 Column 이 아니라 Row 단위로 관리된다는 것이다. 애초에 `users` 라는 키 값에 여러개의 값들을 묶어서 하나의 Value 로 저장하면, 이 값은 하나의 Row로 취급되기 때문에 **selector 를 통해 필터링 된 Value(Row)** 를 리턴하게 된다.

그러니 결국 올바르게 조회가 되면 전체가 리턴되는 것이고, 잘못된 조회를 하게되면 값이 나오지 않는 상황이 되는 것이다. 데이터의 관리는 Document (NoSQL에서의 스키마) 를 작성하는 것부터 시작되니, 유의하여 작성해야 한다.