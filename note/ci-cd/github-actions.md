# Github Actions를 통한 테스트 자동화



```text
name: CI

on: [pull_request]

jobs:
  changes:
    runs-on: ubuntu-latest
    outputs:
      frontend: ${{ steps.filter.outputs.frontend }}
    steps:
      - uses: dorny/paths-filter@v2
        id: filter
        with:
          filters: |
            frontend:
              - 'frontend/**'
  FE-Test:
    needs: changes
    if: ${{ needs.changes.outputs.frontend == 'true' }}
    runs-on: ubuntu-latest
    env:
      working-directory: ./frontend

    steps:
      - uses: actions/checkout@v2

      - name: yarn install
        run: yarn install
        working-directory: ${{ env.working-directory }}

      - name: yarn test
        run: yarn test:ci
        working-directory: ${{ env.working-directory }}
```

* `dorny/paths-filter@v2`를 통해 frontend 코드가 변경되었을 때만 실행
* frontend 코드가 변경되지 않았을 때는 아래와 같이 실행되지 않음

![](https://user-images.githubusercontent.com/61097373/127734331-9a26c3cd-708d-434e-ae89-56aae3d99a34.png)

