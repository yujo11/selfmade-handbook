# Timezone 고정하기

스크립트에 TZ를 명시해주면 된다.

TZ=UTC -> UTC+00

TZ=UTC+0 -> UTC+09 (한국 시간 기준)

```
"test": "TZ=UTC+9 jest --watch --passWithNoTests",
```
