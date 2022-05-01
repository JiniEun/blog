---
title: "React Hooks : useEffect() 함수"
date: 2022-05-01T14:46:09+09:00
description: "React Hooks : useEffect() 함수"
tags:
- React
- useEffect
categories: 
- React
- useEffect
---

React의 useEffect 함수는 리액트 컴포넌트가 랜더링 될 때마다 특정 작업(side effect)을 실행할 수 있도록 하는 Hook이다.

여기서 특정 작업은 component가 렌더링 된 이후에 비동기로 처리되어야 하는 부수적인 효과들을 말한다. 

이러한 기능으로 인해 함수형 컴포넌트에서도 클래스형 컴포넌트에서 사용했던 생명주기 메서드를 사용할 수 있게 되었다고 한다.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/070f2e0d-fe1f-4aa0-889a-e226d09367ea/Untitled.png)

- componentDidMount: 컴포넌트를 만들고, 첫 렌더링을 다 마친 후 실행.
- componentDidUpdate: 리렌더링을 완료한 후 실행. 즉 render()가 업데이트될 때마다 실행
- compoenntWillUnMount: 컴포넌트를 DOM에서 제거할 때 실행.

useEffect는 component가 mount 됐을 때, component가 unmount 됐을 때, component가 update 됐을 때 특정 작업을 처리할 수 있다.

# useEffect() 사용법

기본형태

```java
useEffect( function, deps )
```

`function`: 수행하고자 하는 작업

`deps`: 배열 형태, function을 실행시킬 조건.

배열 안에는 검사하고자 하는 특정 값 or 빈 배열 / deps = dependency를 의미 / 의존값이 들어있는 배열

deps에 특정값을 넣게 되면 컴포넌트가 mount 될 때, 지정한 값이 업데이트될 때 useEffect를 실행한다.

## **useEffect 함수 불러오는 방법**

import

```jsx
import React, { useEffect } from 'react';
```

## 1. Component가 mount 됐을 때 (처음 나타날 때)

- 컴포넌트가 화면에 가장 처음 렌더링 될 때 한 번만 실행하고 싶을 때는 deps 위치에 빈 배열을 넣는다.

```jsx
useEffect(() => {
	console.log('마운트 될 때만(맨처음 렌더링될 때 한 번) 실행');
}, []);
```

- 배열을 생략한다면 rerendering 될 때마다 실행된다.

```jsx
useEffect(() => {
	console.log('렌더링 될 때 마다 실행');
});
```

## 2. Component가 update 될 경우 (특정 props, state가 변경될 경우)

- 특정값이 업데이트 될 때 실행하고 싶을 경우 deps 위치에 배열 안에 검사하고 싶은 값을 넣는다.

(deps = dependency를 의미 / 의존값이 들어있는 배열)

```jsx
useEffect(() => {
	console.log(name);
	console.log('업데이트 될 때 마다 실행');
}, [name]);
```

- 업데이트될 때만 실행하는 것이 아니라 마운트 될 때도 실행된다. 따라서 업데이트 될 때만 특정함수를 실행하고 싶다면 아래와 같이 할 수 있다.

ex.

```jsx
const mounted = useRef(false);

useEffect(() => {
	if(!mounted.current){
		mounted.current = true;
	} else {
	// ajax 등
	}
}, [변경되는 값]);
```

컴포넌트가 마운트될 때는 if 문에서 아무것도 실행하지 않고 mounted 값만 바꿔주고, else에서 배열 안에 있는 값이 변경되면 ajax 서버 통신, axios 등 원하는 코드를 실행할 수 있게 할 수 있다.

## 3. Component가 unmount될 때(사라질 때) & update 되기 직전에

```jsx
useEffect(() => {
	console.log('effect');
	console.log(name);
	return () => {
		console.log('cleanup');
		console.log(name);
	};
}, []);
```

- cleanup 함수 반환: return 뒤에 나오는 함수, useEffect에 대한 뒷정리 함수라고 한다.
- 언마운트될 때만 cleanup 함수를 실행하고 싶을 때
    
    → 두 번째 파라미터로 빈 배열을 넣는다.
    
- 특정값이 업데이트 되기 직전에 cleanup 함수를 실행하고 싶을 때
    
    → deps 배열 안에 검사하고 싶은 값을 넣어준다.
    

## deps에 특정 값 넣기

deps에 특정값을 넣게 될 경우 컴포넌트가 처음 마운트 될 때, 지정한 값이 변경될 때, 언마운트될 때, 값이 변경되기 직전에 모두 호출된다.

useEffect안에서 사용하는 상태나 props가 있는 경우 

→ useEffect의 deps에 넣어주어야 하는 것이 규칙

만약 사용하는 값을 넣어주지 않는다면, useEffect 안의 함수가 실행될 때 최신 상태, props를 가리키지 않는다.

deps 파라미터를 생략할 경우, component가 rerendering 될 때 마다 useEffect 함수가 호출된다.

# Reference

[https://cocoon1787.tistory.com/796](https://cocoon1787.tistory.com/796)

[https://xiubindev.tistory.com/100](https://xiubindev.tistory.com/100)