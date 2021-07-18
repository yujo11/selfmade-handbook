# Webpack + React App favicon 추가하기

CRA로 프로젝트를 생성한 경우 `public` 폴더 밑에 있는 `favicon.ico` 파일만 바꿔주면 간단하게 favicon을 변경할 수 있다.

현재 진행중인 팀 프로젝트에서 favicon을 설정하려고 하는데 CRA의 설정을 그대로 따라해도 favicon이 변경되지 않았다. 검색 해보니 webpack plugin을 사용해서 간단하게 해결할 수 있었다. 이 기능을 지원해 주는 플러그인은 다음 두 가지가 있었다.

1.  `html-webpack-plugin` 
2. `favicon-webpack-plugin` 

이미 `html-webpack-plugin` 을 사용중이었고 `favicon-webpack-plugin` 에서 제공해주는 세부 설정들이 필요하지 않아 `html-webpack-plugin` 에 설정을 추가해서 문제를 해결했다.

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
  * [https://www.npmjs.com/package/favicons-webpack-plugin](https://www.npmjs.com/package/favicons-webpack-plugin)

