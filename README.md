# autopilot-blog-assets

기술 블로그 글에 실리는 도식 파일만 담는다. **공개 리포다.**

원고는 여기 없다. [`autopilot-blog`](https://github.com/shakystar/autopilot-blog)(비공개)에 있다.

## 왜 따로 있나

Blogger 는 본문에 넣은 인라인 SVG 를 렌더하지 못한다. 본문을 HTML 파서로 다시 쓰면서
`viewBox` 를 `viewbox` 로 소문자화하고 `<rect ... />` 의 슬래시를 떼어내기 때문이다.
SVG 속성은 대소문자를 구분하므로 좌표계가 사라지고, 닫히지 않은 요소 뒤로 나머지가
전부 중첩된다. 화면에는 도식 대신 글자만 이어져 나온다.

`<img src="https://...">` 는 평범한 HTML 태그라 그 정규화를 그대로 통과한다. 그래서
도식을 파일로 두고 URL 로 참조한다. `raw.githubusercontent.com` 이 `.svg` 를
`image/svg+xml` 로 내려주므로 PNG 로 구울 필요는 없다. 다만 인증 없이 받으려면
리포가 공개여야 한다. 그것이 이 리포가 따로 있는 이유다.

## 무엇이 언제 들어오나

**사람이 초고 PR 을 머지한 뒤에만 들어온다.** 발행 워크플로가 `autopilot-blog` 의
`assets/` 에서 여기로 복사한 다음 Blogger 에 글을 올린다. 순서가 반대면 발행된 글에
깨진 이미지가 실린다.

에이전트는 이 리포에 쓰지 않는다. 쓸 수 있게 하면 검토 전에 공개되므로,
"사람의 승인 전에는 아무것도 공개되지 않는다"가 깨진다.

## 경로

```
autopilot-blog (비공개)          autopilot-blog-assets (공개)
  assets/<slug>/<name>.svg   ->    <slug>/<name>.svg
```

본문에서 참조하는 주소:

```
https://raw.githubusercontent.com/shakystar/autopilot-blog-assets/main/<slug>/<name>.svg
```

## 손대지 말 것

여기 파일을 직접 고치지 마라. 원본은 `autopilot-blog` 의 `assets/` 이고 여기는 사본이다.
고치려면 원고 리포에서 고쳐 다시 발행한다.
