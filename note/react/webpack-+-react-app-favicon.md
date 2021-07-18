# Webpack + React App favicon 추가하기

CRA로 프로젝트를 생성한 경우 `public` 폴더 밑에 있는 `favicon.ico` 파일만 바꿔주면 간단하게 favicon을 변경할 수 있다.

현재 진행중인 팀 프로젝트에서 favicon을 설정하려고 하는데 CRA의 설정을 그대로 따라해도 favicon이 변경되지 않았다. 검색을 해서 찾아보니 webpack의 `html-webpack-plugin` 를 사용하는 방법이 있어 플러그인을 통해 favicon 경로를 잡아서 변경 했다.

```javascript
new HtmlWebpackPlugin({
  template: 'public/index.html',
  favicon: 'src/assets/images/logo.png',
}),
```

* 적용된 모습

![](../../.gitbook/assets/2021-07-18-12.48.07.png)

* 참고자료
  * [https://github.com/jantimon/html-webpack-plugin\#options](https://github.com/jantimon/html-webpack-plugin#options)

