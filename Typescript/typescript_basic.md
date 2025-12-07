# Typescriptの型

## boolean型とnumber型とstring型を使う方法

```ts title="sample.ts"
let hasValue: boolean = true;
let count: number = 10;
let count: number = 3.14;
let negative: number = -0.12;
let single: string = 'hello';
let double: string = "hello";
let back: string = `hello`;
```

## 型注釈、型推論
基本的に型推論。つまり型を付けない。型推論ができないとき型注釈をつける

## オブジェクトに型を付ける方法
型推論
```ts
const person = {
    name: 'Jack',
    age: 21
}
```
型注釈
```ts
const person: {
    name: string;
    age: number;
} = {
    name: 'Jack',
    age: 21
}
```

## 配列に型を付けるArray型はこう使う
```ts
const fruits: string[] = ['Apple', 'Banana', 'Grape']
```

## Tuple型を使用して、決まった内容の配列を作る方法
```ts
const book: [string, number, boolean] = ['business', 1500, true]// 1つ目にstring、2つ目にnumber、3つ目にboolean
```

## Enumを使って、特定のまとまったグループのみを受け入れる列挙型を使う方法
```ts
enum CoffeeSize {
    SHORT = 'SHORT',
    TALL = 'TALL',
    GRANDE = 'GRANDE',
    VENTI = 'VENTI'
}
```
CoffeeSizeという型が作られる。CoffeeSizeはデータと型を作る。使用は以下のように使う
```ts
const coffee = {
    hot: true,
    size: CoffeeSize.TALL
}
```


```ts

```

