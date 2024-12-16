`reduce` 메서드는 자신을 호출한 모든 요소를 순회하며 인수로 전달받은 콜백 함수를 반복 호출한다.

그리고 콜백 함수의 반환값을 다음 순회 시에 콜백 함수의 첫 번째 인수로 전달하면서 콜백 함수를 호출하여 하나의 결과값을 만들어 반환한다.

이때, 원본 배열은 변경되지 않는다.

`reduce` 메서드는 첫 번째 인수로 콜백 함수, 두 번째 인수로 초기값을 전달받는다.

```jsx
const arr = [1,2,3,4];

arr.reduce(콜백 함수, 초기값);
```

reduce 메서드의 콜백 함수에는 4개의 인수가 전달된다

- **초기값** 또는 콜백 함수의 **이전 반환값**
- reduce 메서드를 호출한 배열의 **요소값**
- reduce 메서드를 호출한 배열의 **인덱스**
- reduce 메서드를 호출한 **배열 자체** (즉 this)

배열의 모든 요소의 합을 구하는 예제

```jsx
const arr = [1,2,3,4];

// accmulator: 초기값 or 이전 반환값
// currentValue: 배열의 요소값
// index: 배열의 인덱스
// arrary: 배열
const sum = arr.reduce((accmulator, currentValue, index, arrary) => accmulator + currentValue, 0);

console.log(sum); // 10
```

reduce 메서드의 콜백 함수는 4개의 인수를 전달받아 배열의 length 만큼 총 4회 호출된다.

이 때, 콜백함수로 전달되는 인수와 콜백 함수의 반환값은 다음과 같다.


<div align="center">
	<img src="https://github.com/user-attachments/assets/e1216d6a-12c0-4500-bf57-bd147fc4e6b6" width="700">
</div>

이처럼 reduce 메서드는 초기값과 배열의 첫 번째 요소값을 콜 백 함수에게 인수로 전달하면서 호출하고 다음 순회에는 콜백 함수의 반환값과 두 번째 요소값을 콜백 함수의 인수로 전달하면서 호출한다.

이러한 과정을 반복하여 reduce 메서드는 하나의 결과값을 반환한다.

reduce 메서드는 자신을 호출한 배열의 모든 요소를 순회하며 하나의 결과값을 구해야 하는 경우에 사용한다.

## 다양한 예시

### 평균 구하기

```jsx
const values = [1, 2, 3, 4, 5, 6];

const average = values.reduce((acc, cur, i, {length}) => {
	//마지막 순회가 아니면 누적값을 반환, 마지막 순회이면 누적값으로 평균을 구해 반환	
	return i === length - 1 ? (acc + cur) / length : acc + cur
}, 0);
```

### 최대값 구하기

```jsx
const values = [1, 2, 3, 4, 5];

const max = values.reduce((acc, cur) => (acc > cur ? acc : cur) ,0);
console.log(max); // 5
```

- **Math.max**
    
    여기서는 reduce로 최대값을 구했지만, 최대값을 구할 때는 Math.max 메서드를 사용하는게 더 직관적이다
    
    ```jsx
    const values = [1, 2, 3, 4, 5];
    const max = Math.max(...values);
    ```
