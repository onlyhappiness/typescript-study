### function

<br>
<br>

### Call Signatures

---

call signatueres라는 것은 함수의 타입을 미리 지정하는 것

타입을 먼저 생각하고, 코드를 구현

```ts
type Add = (a: number, b: number) => number;

const add: Add = (a, b) => a + b;
```

<br>
<br>

### Overloading

---

오버로딩은 <br>
여러개의 call signatures를 가지고 있을 때 발생

```ts
type Add = {
  (a: number, b: number): number;
  (a: number, b: string): number;
};

const add: Add = (a, b) => {
  if (typeof b === 'string') return a;
  return a + b;
};
```

<br>
<br>

### Polymorphism

---

다형성이란, <br>
여러가지 다른 구조들을 의미

```ts
type SuperPrint = {
  (arr: number[]): void;
  (arr: boolean[]): void;
};

const superPrint: SuperPrint = (arr) => {
  arr.forEach((i) => console.log(i));
};

// true
superPrint([1, 2, 3, 4]);
superPrint([true, false, true]);

// false
// superPrint의 타입이 number와 boolean 배열이기 때문
superPrint(['a', 'b', 'c']);
```

<br>

```ts
type SuperPrint = {
  <TypePlaceholder>(arr: TypePlaceholer[]): TypePlaceholder;
};

const superPrint: SuperPrint = (arr) => arr[0];

// true
// 제네릭을 통해 타입을 유추
superPrint([1, 2, 3, 4]);
superPrint([true, false, true]);
superPrint(['a', 'b', 'c']);
superPrint([1, 2, true, false]);
```

<br>
<br>

### Conclusions

---

```ts
type Player<E> = {
  name: string;
  extraInfo: E;
};

type breadExtra = {
  favFood: string;
};

type breadPlayer = Player<breadExtra>;

const bread: breadPlayer = {
  name: 'bread',
  extraInfo: {
    favFood: 'bread',
  },
};
```
