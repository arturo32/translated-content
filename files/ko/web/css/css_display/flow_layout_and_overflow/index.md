---
title: 대열 레이아웃과 대열이탈
slug: Web/CSS/CSS_display/Flow_layout_and_overflow
original_slug: Web/CSS/CSS_flow_layout/Flow_layout_and_overflow
---

컨테이너에 채울 수 없을 만큼 더 많은 내용물이 있을 때 오버플로 상황이 발생한다. CSS에서 크기 제한이 있는 요소를 다루려면 오버플로의 동작 방식을 이해하는 것이 중요하다. 이 안내서는 일반 플로우에 해당하는 작업 중에 오버플로이 작동하는 방식을 설명한다.

## 오버플로은 무엇인가?

어떤 요소에 고정 높이 및 너비를 부여한 다음, 상자에 상당한 내용물을 추가하면 기본적인 오버플로 사례가 만들어 진다.

{{EmbedGHLiveSample("css-examples/flow/overflow/overflow.html", '100%', 700)}}

내용물이 상자 안으로 들어간다. 상자가 채워지면, 눈에 보이게 오버플로이 계속되면서 상자 밖으로 내용물이 표시되고, 후속 내용물 아래에 표시될 가능성까지 있다. 오버플로 동작 방식을 통제하는 속성은 오버플로 속성으로 초기값은 `visible`로 되어 있다. 그런 까닭에 오버플로한 내용물를 볼 수 있다.

## 오버플로 통제

오버플로된 내용물이 동작하는 방식을 통제하는 그 밖의 값들이 있다. 오버플로된 내용물을 감추려면 `hidden` 값을 사용한다. 이 값은 내용물을 보이지 않게 만들 수도 있다.

{{EmbedGHLiveSample("css-examples/flow/overflow/hidden.html", '100%', 700)}}

`scroll` 값을 사용해서 상자의 내용물을 상자 안에 가둬두고 내용물을 볼 수 있게 스크롤 막대를 추가할 수 있다. 스크롤 막대는 내용물이 상자에 들어맞더라도 추가될 것이다.

{{EmbedGHLiveSample("css-examples/flow/overflow/scroll.html", '100%', 700)}}

`auto` 값을 사용하면 상자안에 내용물이 들어맞을 경우 스크롤 막대 없이 내용물을 표시하게 된다. 만일 내용물이 들어맞지 않는다면 스크롤 막대가 추가되게 된다. 다음 예를 `overflow: scroll` 경우의 예와 비교하면 수직 스크롤 막대가 필요할 경우에도 `overflow scroll`의 예는 수평 및 수직 스크롤 막대가 있음을 알수 있다. 아래 `auto` 예제에서는 우리가 스크롤이 필요한 방향으로만 스크롤 막대를 추가한다.

{{EmbedGHLiveSample("css-examples/flow/overflow/auto.html", '100%', 700)}}

이미 배운 바와 같이 기본값인 `visible` 이외에 살펴본 값 중의 어떤 값을 사용하게 되면 새로운 블록 서식 상황을 생성하게 된다.

참고: [작업 초안 오버플로 수준 3](https://www.w3.org/TR/css-overflow-3/)을 보면 추가적인 속성 값으로 `overflow: clip`이 있다. 이것은 `overflow: hidden`와 같이 작용하지만, 프로그래밍 방식의 스크롤이 불용되어 스크롤 할 수 상자가 된다. 또한, 이것은 블록 서식 상황을 생성하지 못한다.

오버플로 속성은 실제로는 [`overflow-x`](/ko/docs/Web/CSS/overflow-x)와 [`overflow-y`](/ko/docs/Web/CSS/overflow-y) 속성의 약칭이다. 오버플로 값을 하나만 지정하면 이 값은 가로 세로 양 축에 모두 사용된다. 그러나 두 가지 값 모두를 지정할 수 있다. 첫번 째 경우에는 `overflow-x`를 수평 방향 값으로 두번째 경우에는 `overflow-y`를 수직 방향 값으로 사용하면 된다. 아래 예에서 나는 `overflow-y: scroll`만 지정함으로써 원치 않는 가로 스크롤 막대가 나타나지 않도록 했다.

{{EmbedGHLiveSample("css-examples/flow/overflow/overflow-y.html", '100%', 700)}}

## 상대적 플로우 속성

우리는 [쓰기 모드와 플로우 레이아웃](/ko/docs/Web/CSS/CSS_Flow_Layout/%ED%9D%90%EB%A6%84_%EB%A0%88%EC%9D%B4%EC%95%84%EC%9B%83%EA%B3%BC_%EC%93%B0%EA%B8%B0_%EB%AA%A8%EB%93%9C) 안내서에서 `block-size`와 `inline-size`라는 새로운 속성를 살펴보았는데, 이 속성은 물리적인 화면 크기에 레이아웃을 구속하기보다는 다양한 쓰기 모드에서 작업할 경우에 적합하다. 수준 3 오버플로 모듈에는 플로우에 상대적인 오버플로 속성들[`overflow-block`](/ko/docs/Web/CSS/@media/overflow-block)와 [`overflow-inline`](/ko/docs/Web/CSS/@media/overflow-inline)도 포함되어 있다. 그것들은 `overflow-x`와 `overflow-y`에 대응하지만, 매핑은 문서의 쓰기 모드 여하에 달려 있다.

이들 속성은 현재 브라우저에 구현이 되어 있지 않으므로, 현 시점에는 물리적인 속성을 사용하고 쓰기 모드에 맞게 조정해야 한다.

## 오버플로 표시

수준 3 오버플로 규격에서 우리는 콘텐츠가 오버플로 상황에서 내용물이 보여지는 방식을 개선하도록 도움을 줄 수 있는 몇 가지 속성을 보유하고 있다.

### 인라인축 오버플로

`text-overflow` 속성은 인라인 방향의 텍스트 오버플로을 처리한다. 이 속성에는 두 가지 값 중에서 택일한다. `clip`의 경우는 오버플로하면 내용물이 잘려나간다. 이것이 초기값이므로 기본 동작이다. 또한, `ellipsis`의 경우는 줄임표를 렌더링하는 것인데, 사용 중인 언어와 쓰기 모드에 따라서는 더 나은 문자로 대체될 수도 있다.

{{EmbedGHLiveSample("css-examples/flow/overflow/text-overflow.html", '100%', 500)}}

### 블록축 오버플로

이 글의 작성 시점에 명칭을 두고 아직 논의의 여지가 있지만, `block-overflow`란 속성도 있다. 이 제안으로 텍스트가 블록 크기를 오버플로할 때 줄임표를 추가할 수 있게 된다.

이것은 예를 들어 문서 목록이 있고 제한된 양의 텍스트만 취하는 고정 높이 상자에 목록을 표시하는 경우에 유용하다. 상자나 제목을 클릭할 때 클릭할 내용이 더 많다는 것을 독자들이 인지하지 못할 수도 있다. 줄임표는 더 많은 내용이 있다는 사실을 분명하게 보여준다. 이 규격은 일련의 내용 또는 규칙적인 줄임표를 삽입할 수 있게 한다.

## 요약정리

웹 상의 연속적인 미디어에 있는지 또는 인쇄 또는 EPUB와 같은 페이징 미디어 형식에 있는지 여부는 어떤 레이아웃 메서드를 처리할 때 어떻게 내용물이 오버플로하게 되는지 이해를 돕는데 유용하다. 일반 대열에서 오버플로이 어떻게 작동하는지 이해함으로써 격자나 플렉스박스 같은 레이아웃 방식에 포함된 오버플로 내용물의 파장을 더 쉽게 이해할 수 있어야 한다.

{{QuickLinksWithSubpages("/ko/docs/Web/CSS/CSS_Flow_Layout/")}}
