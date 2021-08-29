# image-minimizer-webpack-plugin 사용 후기

* 손실 압축, 비손실 압축 모두 어느 정도 용량이 감소하는걸 확인할 수 있었다.
* 그러나 압축 알고리즘을 사용하는 시간 때문인지 빌드 시간이 너무~~~ 오래 걸렸다.
* 지금 적용하려는 프로젝트의 경우에는 빌드에 무려 400초 가까이 걸린다.\(ms아님\)
* 이미지를 번들링 과정에서 압축하는게 아니라 애초에 압축 된 이미지를 가지고 있는게 현재는 베스트인거 같다.
* 이런 플러그인이 있는 것만 알아두

![](../../.gitbook/assets/2021-08-29-9.08.53%20%281%29.png)



{% embed url="https://www.npmjs.com/package/image-minimizer-webpack-plugin" caption="npm link" %}

{% embed url="https://webpack.js.org/plugins/image-minimizer-webpack-plugin/" caption="webpack link" %}





