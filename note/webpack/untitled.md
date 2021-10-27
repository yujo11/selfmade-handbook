# maifest 추가하기



#### 1. manifest.json 작성 후 링크 추가 <a href="1-manifestjson" id="1-manifestjson"></a>

* public/manifest.json

```
{
  "short_name": "찜꽁",
  "name": "찜꽁",
  "description": "공간은 한 눈에, 예약은 한 번에! 공간 예약 서비스 제작 플랫폼 찜꽁입니다!",
  "start_url": "/",
  "display": "minimal-ui",
  "theme_color": "#ff7515",
  "background_color": "#ffffff"
}
```

* webpack.config.js

```
plugins: [
  new HtmlWebpackPlugin({
    template: 'public/index.html',
  }),
  new FaviconsWebpackPlugin({
    logo: 'src/assets/images/logo.png',
    manifest: 'public/manifest.json',
  }),
],
```

#### 2. `favicons` 설정 추가 <a href="2-code-classlanguage-textfaviconscode" id="2-code-classlanguage-textfaviconscode"></a>

`FaviconsWebpackPlugin`은 [favicons](https://github.com/itgalaxy/favicons#usage)의 설정들을 사용할 수 있습니다.

* webpack.config.js

```
plugins: [
  new HtmlWebpackPlugin({
    template: 'public/index.html',
  }),
  new FaviconsWebpackPlugin({
    logo: 'src/assets/images/logo.png',
    favicons: {
      appName: '찜꽁',
      appShortName: '찜꽁',
      appDescription: '공간은 한 눈에, 예약은 한 번에! 공간 예약 서비스 제작 플랫폼 찜꽁입니다!',
      theme_color: '#ff7515',
      background: '#fff',
      display: 'minimal-ui',
    }
  }),
],
```
