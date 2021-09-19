# useMutation은 useEffect를 사용하여 구현되었다.

프로젝트를 진행하면서 알게 된 사실이다.

`useEffect` 내부에서 `useMutation` 의 `mutate` 를 호출하려고 했는데 무한루프에 걸렸다.

`useEffect` 의 dependency array를 비워 놓은 상태인데 무한루프에 빠져버린게 잘 이해가 되지 않아 검색을 했다.

그 결과 `useMutation` 이 `useEffect` 로 구현되어 있다는 사실을 알게 되었다.

내가 사용하려던 코드는 다음과 같다.

```jsx
const tokenValidation = useMutation('postTokenValidation');

useEffect(() => {
  tokenValidation.mutate()
}, []) 
```

이런 코드는 사용할 수 없는 것이다.

`useMutation` 으로 받은 인자를 활용하고 싶다면 다음과 같이 우회하는 방법은 존재한다.

```jsx
const {data: tokenValidtationData} = useMutation('postTokenValidation');

useEffect(() => {
  if (tokenValidationData) {}
}, []) 
```



* [`useMutation` 구현부 링크](https://github.com/tannerlinsley/react-query/blob/ee7ca0bf1e813fd727f25abeb67755f43b636b3f/src/react/useMutation.ts)

