# Lighthouse의 6가지 평가 지표



#### 1. FCP(First Contentful Paint) - 15%

* FCP는 사용자가 페이지를 탐색 한 후 브라우저가 DOM 콘텐츠의 첫 번째 부분을 렌더링하는 데 걸리는 시간을 측정합니다. 페이지의 이미지, 흰색이 아닌 `<canvas>` 요소 및 SVG는 DOM 콘텐츠로 간주됩니다. iframe 내부의 내용은 포함되지 않는다.
* [https://web.dev/first-contentful-paint/](https://web.dev/first-contentful-paint/)

#### 2. Speed Index - 15%

* Speed Index는 페이지로드 중 콘텐츠가 시각적으로 표시되는 속도를 측정한다.
* Lighthouse는 먼저 브라우저에서로드되는 페이지의 비디오를 캡처하고 프레임 간의 시각적 진행을 계산합니다. Lighthouse는 Speedline Node.js 모듈 을 사용하여 Speed Index 점수를 생성한다.
* [https://web.dev/speed-index](https://web.dev/speed-index)

#### 3. LCP(Largest Contentful Paint) - 25%

* LCP는 페이지가 처음 로드 되기 시작한 시점을 기준으로 뷰포트 내에 표시되는 가장 큰 이미지 또는 텍스트 블록의 렌더링 시간을 측정한다.
* [https://web.dev/lcp/](https://web.dev/lcp/)

#### 4. TTI(Time to Interactive) - 15%

* TTI는 페이지가 완전히 상호 작용하는 데 걸리는 시간을 측정한다.&#x20;
* 페이지는 다음과 같은 경우 완전한 대화 형으로 간주됩니다.
* [https://web.dev/interactive/](https://web.dev/interactive/)

#### 5. TBT(Total Blocking Time) - 25%

* TBT는 페이지가 마우스 클릭, 화면 탭 또는 키보드 누름과 같은 사용자 입력에 응답하지 못하도록 차단 된 총 시간을 측정한다.&#x20;
* 합계는 First Contentful Paint와 Time to Interactive 사이의 모든 긴 작업의 차단 부분을 추가하여 계산된다.&#x20;
* 50ms 이상 실행되는 모든 작업은 긴 작업으로 간주 된다. 50ms 이후의 시간이 차단 부분이다.&#x20;
* 예를 들어 Lighthouse가 70ms의 긴 작업을 감지하면 차단 부분은 20ms가 된다.
* [https://web.dev/lighthouse-total-blocking-time/](https://web.dev/lighthouse-total-blocking-time/)

#### 6. CLS(Cumulative Layout Shift) - 5%

* CLS는 페이지의 전체 수명 동안 발생하는 모든 예기치 않은 레이아웃 이동에 대한 모든 개별 레이아웃 이동 점수의 합계를 측정한다.&#x20;
* 레이아웃 이동은 표시되는 요소가 렌더링 된 프레임에서 다음 프레임으로 위치를 변경할 때마다 발생한다.
* [https://web.dev/cls/](https://web.dev/cls/)
