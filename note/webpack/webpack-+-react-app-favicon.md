# favicon 추가하기

CRA로 프로젝트를 생성한 경우 `public` 폴더 밑에 있는 `favicon.ico` 파일만 바꿔주면 간단하게 favicon을 변경할 수 있다.

현재 진행중인 팀 프로젝트에서 favicon을 설정하려고 하는데 CRA의 설정을 그대로 따라해도 favicon이 변경되지 않았다. 검색 해보니 `favicon-webpack-plugin` 을 사용해서 간단하게 해결할 수 있었다.&#x20;

프로젝트에서 사용중인 `html-webpack-plugin`은 통합 플러그인으로 이미 `favicon-webpack-plugin`을 포함하고 있어 `html-webpack-plugin` 에 설정을 추가해서 문제를 해결할 수 있다.

```javascript
new HtmlWebpackPlugin({
  template: 'public/index.html',
  favicon: 'src/assets/images/logo.png',
}),
```

* 적용된 모습

![](<../../.gitbook/assets/스크린샷 2021-07-18 오후 12.48.07.png>)

* 참고자료
  * [https://github.com/jantimon/html-webpack-plugin#options](https://github.com/jantimon/html-webpack-plugin#options)
  * [https://www.npmjs.com/package/favicons-webpack-plugin](https://www.npmjs.com/package/favicons-webpack-plugin)

\+ 7월 21일 추가

`html-webpack-plugin`만 사용하면 자동으로 html 파일에 주입이 되지 않고 등록한 이미지만을 표시한다. 따라서 HTML에 주입까지 하려면 `favicons-webpack-pugin` 을 사용해야 한다.

```javascript
plugins: [
  new HtmlWebpackPlugin({
    template: 'public/index.html',
  }),
  new FaviconsWebpackPlugin('src/assets/images/logo.png'),
],
```

* 적용한 후 빌드 한 HTML 파일의 모습

![](<../../.gitbook/assets/image (2).png>)
