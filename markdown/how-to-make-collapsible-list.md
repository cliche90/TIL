# How to make collapsible List in markdown?

> markdown 에서는 기본적으로 html 을 사용할 수 있기 때문에, `<details>` 태그와 `<summary>` 태그를 활용하여 접을 수 있는 리스트를 만들 수 있다.

```html
<details>
	<summary>title</summary>
    
​```go
fmt.Println("Hello Collapsible List!")
​```
</details>
```

- 주의할 점

  - `<summary>` 태그 종료 후에 반드시 1줄의 공백을 넣어주야 정상적으로 markdown 문법이 Github 에서 적용되는 것을 확인할 수 있다.

  - 또한 markdown 의 문법에서 앞에 공백 4칸이 오면 인용구문으로 인식하기 때문에, markdown 이 시작되는 부분의 앞에 공백이 있다면 제거해야 한다.