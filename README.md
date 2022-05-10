## typescript-study

---

사실 이전부터 했어야 했던 공부였다고 생각하는데,
<br> 뭔가 새로운 것에 접하는 게 두려웠던 것 같다. <br>

시작하기도 전에 겁먹는 건 가오가 없으니 한 번 해보자.

<br>
<br>

### set-up

---

```
node -v 18.1.0
```

<br>

웬만하면 vscode에서 작업하자.

> ms에서 만듦 (타입스크립트, vscode)

<br>
<br>

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

```ts
// 말 그대로 readonly
// 수정 불가
const numbers: readonly number[] = [1, 2, 3, 4];

const names: readonly string[] = ['1', '2'];
```
