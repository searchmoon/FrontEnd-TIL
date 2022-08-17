# useMemo와 useCallback
## useMemo
useMemo를 알아보기 전에, 메모이제이션(memoization)은 기존에 수행한 연산의 결과값을 어딘가에 저장해두고 동일한 입력이 들어오면 재활용하는 프로그래밍 기법을 말한다.

useMemo는 메모이제이션 된 값을 반환한다. 재랜더링이 일어날 때마다 함수를 계속 호출하여 UI의 지연이 발생되는 것을 막기 위해 사용한다.
```
const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);
```
위의 예시에서 첫번째 인자는, 결과값을 생성해주는 팩토리 함수이고, 두번째 인자는 기존 결과값 재활용 여부의 기준이 되는 입력값 배열이다.

a와 b의 값이 이전에 랜더링 했을때와 같을 경우, 이 전 랜더링때 저장해 두었던 결과값을 재활용한다.
a와 b의 값이 이전에 랜더링 했을때와 달라졌을 경우, () => computeExpensiveValue(a, b) 함수를 호출하여 결과값을 새롭게 구해 memoizedValue에 할당해준다.

useMemo 함수를 남용하면, 컴포넌트의 복잡도가 올라가기 때문에 코드를 읽기도 어려워지고 유지보수성도 떨어질 수 있다. 실제 성능의 이점이 지불하는 대가에 비해서 미미하지 않은지에 대해 따져보고 사용해야 한다.

## useCallback

useCallback 함수는 메모이제이션 된 콜백을 반환한다. useMemo는 함수를 실행하고, useCallback은 함수를 반환한다는 점이 두 hooks의 다른 점이다.
```
const memoizedCallback = useCallback(
  () => {
    doSomething(a, b);
  },
  [a, b],
);
```
위의 예시의 첫번째 인자는 넘어온 함수를, 두번째 인자는 넘어온 배열내의 값이 변경될 때까지 저장해놓고 재사용할 수 있게 해준다.
```
useCallback(fn, deps)은 useMemo(() => fn, deps)와 같다.
```
useCallback 은 함수와는 상관 없는 상태값이 변할 때,
함수 컴포넌트에서 불필요하게 함수를 업데이트 하는 것을 방지해준다.

자식컴포넌트에 함수를 props으로 줄때는 useCallback을 사용하여 리렌더링이 안되도록 하자.
