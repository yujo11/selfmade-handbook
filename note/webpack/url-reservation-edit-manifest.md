# 중첩된 URL(/reservation/edit)에서 새로고침시 manifest를 불러오지 못 하는 오류



### 오류 상

* 중첩 된 URL ex) /reservation/edit 에서 새로고침 했을 때 manifest를 불러오지 못 한다.



* URL/guest/reservation 로 접속 후 새로고침 했을 때 발생하는 오류 메세

![](<../../.gitbook/assets/image (4).png>)



### 오류 원인

* 번들 된 파일의 `assets/manifest.json`  을 불러와야 하는데 `guest/assets/mainfest.json` 을 찾으려고 해서 오류가 발생

### 해결 방법

* `webpack.config.js` 파일의 `publicPath` 옵션을 추가한다.

```javascript
{
    ...
    
    output: {
      publicPath: '/', // <------------------------ 추가
      filename: 'bundle.js',
      path: path.resolve(__dirname, 'dist'),
      clean: true,
    },
      
    ...  
    
    plugins: [
      new FaviconsWebpackPlugin({
        logo: 'src/assets/images/logo.png',
        publicPath: '/', // <------------------------ 추가
        manifest: 'public/manifest.json',
      }),
    ],
  };
```
