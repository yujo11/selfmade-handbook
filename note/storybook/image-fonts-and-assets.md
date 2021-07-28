# 정적 파일 렌더 및 배포\(image, fonts, and assets\) 오류

## 문제 상황

### 에러 메세지 

* Module not found: Error: Can't resolve 'assets/svg/luther.png' in '/Users/yujo/2021-zzimkkong/frontend/src/components/SpaceListItem'

### 에러 상황 

* 컴포넌트를 구현하면서 Image의 src를 불러와서 Storybook에서 확인하고 싶었으나 경로를 찾지 못하는 문제 발생

![Error Message](../../.gitbook/assets/image%20%281%29.png)

## 해결 방법 

* 렌더, 배포 시 정적 파일을 함께 렌더, 배포 하도록 npm script 변경

```text
// 기존
"scripts": {
    "storybook": "start-storybook -p 6006",
    "build-storybook": "build-storybook"
}

// 변경
"scripts": {
"storybook": "start-storybook -s ./src/assets -p 6006",
    "build-storybook": "build-storybook -s ./src/assets"
}

```

## 참고 자료

* [https://storybook.js.org/docs/react/configure/images-and-assets](https://storybook.js.org/docs/react/configure/images-and-assets)



