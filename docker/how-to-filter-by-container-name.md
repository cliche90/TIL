# How to filter container by name?

> docker 작업을 하다보면 일괄로 삭제를 하는 등의 일괄 작업이 필요할 때가 있다. 문서에 잘 나와있기는 하지만 귀찮아서 잘 보지 않다보니 해당 내용을 별도로 적어둔다.

- 일반적으로 아래의 커맨드로 container 들을 조회해 가져오는 것이 가능할 때도 있다.

  ```bash
  docker ps -a container-*
  ```

- 그러나 위의 커맨드는 공식적으로 안내되어있지 않고, 환경에 따라 작동하거나, 하지 않거나 한다. docker 의 문서를 살펴보면  `--filter` 라는 플래그를 제공하고 있음을 알 수 있다. 이를 이용하여 아래와 같이 작업할 수 있다. 주의할 점은 ***와 같이 wildcard 로 조건을 주지 않아도, like 로 작동**한다는 것이다.

  ```bash
  docker ps -a --filter "name=container-"
  ```

- 또한 일괄 삭제등을 할 때는 container 의 ID 만 필요할 때가 많으므로 `-q` 옵션을 통해 아래와 같이 일괄삭제를 할 수 있다.

  ```bash
  docker rm $(docker ps -a -q --filter "name=container-")
  ```

  