# axios intercpetors 리다이렉션

```typescript
import { history } from 'App';

const api = axios.create({
  baseURL: 'https://zzimkkong-proxy.o-r.kr/api',
  headers: {
    'Content-type': 'application/json',
  },
});

api.interceptors.response.use(
  (response) => {
    return response;
  },

  (error: AxiosError<ErrorResponse>) => {
    if (error?.response?.status === 401) {
      localStorage.removeItem(LOCAL_STORAGE_KEY.ACCESS_TOKEN);

      history.push(PATH.MANAGER_LOGIN);
    }

    return Promise.reject(error);
  }
);

export default api;
```

1. axios interceptos에서 response의 status를 확인한다.
2. status가 401(Unautorized)일 경우에는 history를 통해 redirection 한다.

그런데, `react-router-dom` 의 `BrowserRouter` 등을 사용하다 보면 Custom History 객체를 모든 App에서 공유하지 못하는 상황이 생길 수도 있다. 그럴 때는 아래 글을 참고해 `Router` 에 Custom History 객체를 등록해서 사용하자.

* BrowserRouter와 Router([https://app.gitbook.com/@yujo/s/selfmade-handbook/\~/drafts/-MhX9owXwNFDI9kI07wh/note/react-router/browserrouter-router](https://app.gitbook.com/@yujo/s/selfmade-handbook/\~/drafts/-MhX9owXwNFDI9kI07wh/note/react-router/browserrouter-router))

