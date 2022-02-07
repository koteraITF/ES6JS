# ES6JS

## forEach

for文よりも下記のようなforEach文のほうが使われるようになった。
functionとアロー関数の２種類で記述した。
```
var colors = ["red","blue","green"]

colors.forEach(function(color){
  console.log(color); 
  ///red , blue , green
});

colors.forEach( (color) => {
	console.log(color); 
  ///red , blue , green
});
```

下記のように実践的に使うこともできる。
```
var numbers = [1, 2, 3, 4, 5];

var sum = 0;

numbers.forEach((number) => {
  sum += number;
});

console.log(sum); //15
```
今回は、forEachの中にアロー関数を書いたが、forEachとアロー関数を分けることもできる。
```
var numbers = [1,2,3,4,5];

var sum = 0;

const adder = (number) => {
  sum += number;
}

numbers.forEach(adder);

console.log(sum);　//15
```

## map関数

map関数は新しい配列を作り直す。
```
const numbers = [1, 2, 3];

const doubled = numbers.map((number) => {
  return number * 2;
});

console.log(doubled);
```
mapのイメージ  
<img width="624" alt="image" src="https://user-images.githubusercontent.com/97214466/152744119-6b2fa01a-c275-4736-8b99-b015e61e1f5c.png">  

また、map関数は元の配列から抽出したいオブジェクトのみを抽出して、配列化することができる。
```
const cars = [
  { type: "軽自動車", price: "安い" },
  { type: "高級車", price: "高い" }
];

const prices = cars.map((car) => {
  return car.price;
});
console.log(prices); //[安い,高い]
```
