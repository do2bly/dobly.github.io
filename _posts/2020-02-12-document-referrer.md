---
layout: post
title: document 객체의 referrer 
tags: javascript dom
---

document 객체에 referrer속성을 이용하면 이전 페이지의 URI를 얻을수 있다.

```javascript
document.referrer // "https://www.google.com/"
```
 
하지만 아래와 같은 상황으로 페이지를 접근하는경우 빈 문자열을 반환한다.
* 브라우저의 새창을 띄워서 url을 입력한경우
* 북마크한 페이지를 통해서 이동한 경우
* a태그가 아닌 함수로 페이지를 연결 또는 이동한경우
    * location.href = 'url';
    * window.open('url'); 

```javascript
document.referrer // ""
```

정규식을 사용하여 외부에서 접근한 referrer만 추출하기 위한 조건을 추가하였다. 
```javascript
const URI_REGEX = /^(http(s)?:\/\/)?([a-z0-9\-]*\.)?dobly.net/;
let referrer = document.referrer || "";

if (referrer && URI_REGEX.test(referrer) {
    return;
}
```