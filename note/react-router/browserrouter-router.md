# BrowserRouter와 Router



#### `BrowserRouter` 대신 `Router`를 적용한 이유

* 아래는 `BrowserRouter`의 구현체입니다.

```javascript
import React from "react";
import { Router } from "react-router";
import { createBrowserHistory as createHistory } from "history";
import PropTypes from "prop-types";
import warning from "tiny-warning";

/**
 * The public API for a <Router> that uses HTML5 history.
 */
class BrowserRouter extends React.Component {
  history = createHistory(this.props);

  render() {
    return <Router history={this.history} children={this.props.children} />;
  }
}

if (__DEV__) {
  BrowserRouter.propTypes = {
    basename: PropTypes.string,
    children: PropTypes.node,
    forceRefresh: PropTypes.bool,
    getUserConfirmation: PropTypes.func,
    keyLength: PropTypes.number
  };

  BrowserRouter.prototype.componentDidMount = function() {
    warning(
      !this.props.history,
      "<BrowserRouter> ignores the history prop. To use a custom history, " +
        "use `import { Router }` instead of `import { BrowserRouter as Router }`."
    );
  };
}

export default BrowserRouter;
```

* 위 구현체를 확인해 보면 `Router`에 `history`를 주입한 게 `BrowserRoutesr`인 것을 확인할 수 있습니다.
* 기존까지는 주입 받은 `history`만으로도 전혀 문제가 없었으나 이번 버그 같은 경우는 `Component`와 다른 파일들이 같은 `history`객체를 공유하지 못 해 문제가 생겼습니다.
* 위 구현체의 하단을 보면 아래와 같은 문구가 들어 있습니다.

  > ignores the history prop. To use a custom history,use `import { Router }` instead of `import { BrowserRouter as Router }`

* 저희가 Custom History 객체를 만들어서 저희 App의 모든 부분\(Component 내부 로직과 바깥 로직 모두\)에서 같은 hisotory 객체를 사용하기 위해서는 Router를 사용해야 하는 것을 확인할 수 있었습니다.
* 이에 따라 기존 사용하던 `BrowserRouter` 대신 `Router`를 적용하였고, 아래와 같이 정상적으로 작동하는 것을 확인할 수 있습니다.

#### 이전 동작과 현재 동작

* 이전 동작 \(버그\)

![Aug-13-2021 13-46-12](https://user-images.githubusercontent.com/61097373/129307462-4580286b-3cc6-4d76-8b2b-5c3e85a866f6.gif)

* 현재 동작

  ![Aug-13-2021 13-46-59](https://user-images.githubusercontent.com/61097373/129307482-f255ee3d-e139-45a4-b4e8-0c7fde184005.gif)

