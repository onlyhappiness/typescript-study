### Type

---

#### 타입 추론

```ts
let a = 'hello';

// 타입스크립트가 a의 타입을 추론
```

<br>

#### 타입 명시

```ts
let b: boolean = false;

let c: number[] = [];

let d: string[] = ['a', 'b'];
```

<br>
<br>

### Type1 - 객체 및 함수에 타입 지정

---

name, age가 있는 player 객체

```ts
const player1: {
  name: string;
  age: number;
} = {
  name: 'bread',
  age: 20,
};

const player2: {
  name: string;
  // 만약 age가 없을 수도 있는 경우에는
  // ?를 붙이면 된다.
  age?: number;
} = {
  name: 'bread',
};

// 만약 player의 age를 추출하려면
if (player.age && player.age < 10) {
  return ...
}
```

<br>

여러 객체에서 사용하기

```ts
type Player = {
  name: string;
  age?: number;
};

const bread: Player = {
  name: 'bread',
  age: 20,
};

const ts: Player = {
  name: 'ts',
};
```

<br>

함수에 타입 지정

```ts
type Player = {
  name: string;
  age?: number;
};

function playerMaker1(name: string): Player {
  return {
    name,
  };
}

const playerMaker2 = (name: string): Player => ({ name });

const bread = playerMaker('bread');
```

<br>
<br>

### Type 2

---

#### readonly

```ts
// 말 그대로 readonly
// 수정 불가
const numbers: readonly number[] = [1, 2, 3, 4];

const names: readonly string[] = ['1', '2'];
```

<br>

#### tuply

```ts
// 배열안에 요소들의 타입을 순서대로 지정
const player: readonly [string, number, boolean] = ['bread', 20, true];
```

<br>

#### undefined, null

```ts
let a: undefined = undefined;

let b: null = null;
```

<br>

#### any

```ts
// any => 타입스크립트로부터 빠져나오고 싶을 때 쓰는 타입
// 아무런 타입이 될 수 있음
let a: any[];
```

<br>
<br>

### Type 3

---

#### unknown

```ts
// 먄약 api를 통해 응답을 받는데
// 응답의 타입을 모를 경우 사용 가능
let a: unknown;

if (typeof a === 'number') {
  let b = a + 1;
}
if (typeof a === 'string') {
  let b = a.toUpperCase();
}
```

<br>

#### void

```ts
function hello(): void {
  console.log('hello');
}
```

<br>

#### never

```ts
// never는 함수가 절대 return 하지 않을 때 발생
function hello(): never {
  // 에러 발생
  return 'hello';
}
```

<br>

```ts
function hello(name: string | number) {
  if (typeof name === 'string') {
    name;
  } else if (typeof name === 'number') {
    name;
  } else {
    // 해당 리턴되는 name의 타입은 never다.
    // 타입 지정할 때 name은 string 또는 number로 지정했기 때문에
    // 그 이외 타입이 나올 수 없다.
    name;
  }
}
```
