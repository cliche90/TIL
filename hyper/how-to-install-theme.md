# How to install hyper theme?

> Hyper 터미널에서는 몇가지 테마들을 제공한다. 여기서는 설치 방법과 테마 한가지를 소개한다.



## hyper-pokemon theme

![](./how-to-install-theme/hyper-theme.gif)



```bash
hyper i hyper-pokemon
```

- 단순히 위의 커맨드를 실행하는 것만으로 테마를 변경할 수 있다.

- 포켓몬의 종류 역시 변경할 수 있다. 기본적으로 hyper에 설치된 plugin 들의 설정값들은 `~/.hyper.js` 에 저장되는데, `config` 하위에 `pokemon` 이라는 속성에 값을 줄수 있다. 예를 들어 아래와 같이 `random` 값을 주면 터미널을 열때마다 다른 포켓몬을 볼 수 있다.

	```json
	module.exports = {
	    config: {
	        ....
	        pokemon: 'random',
	        ....
	    },
	    ...
	}
	```