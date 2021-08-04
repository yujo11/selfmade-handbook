---
description: 자주 쓰는 정규식 모아두기
---

# 정규 표현식

```javascript
// 영어와 숫자를 반드시 포함, 8자 이상 20자 이하
const reg = /^(?=.*[a-zA-Z])(?=.*[0-9]).{8,20}$/ 

reg.test("password123"); true
reg.test("thisispassword); false

// 영어 대소문자, 한글, 특수문자가 포함 1글자 이상
const reg2 = /^[a-zA-Z0-9ㄱ-ㅎ가-힣ㅏ-ㅣ-_!?.,\s]{1,}$/

reg2.test('한글'); true
reg2.test('@포함되지 않은 특수문자'); false
```



