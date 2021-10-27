# axios interceptors Header에 Token 추가하기

```typescript
const api = axios.create({
  baseURL: 'https://zzimkkong-proxy.o-r.kr/api',
  headers: {
    'Content-type': 'application/json',
  },
});

api.interceptors.request.use(
  (config) => {
    const token = getLocalStorageItem({
      key: LOCAL_STORAGE_KEY.ACCESS_TOKEN,
      defaultValue: '',
    });

    if (typeof token !== 'string' || !token) return config;

    config.headers = {
      'Content-type': 'application/json',
      Authorization: `Bearer ${token}`,
    };

    return config;
  },

  (error) => {
    return Promise.reject(error);
  }
);
```

1. 토큰을 가져온다.&#x20;
2. 토큰이 있는 경우 request를 보내기 전 config.headers에 토큰을 추가해서 실어 보낸다.

