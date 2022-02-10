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
また、map関数は第二引数ととることができる。  
「value」は、配列の値  
「index」は、配列のインデックス番号  
「array」は、現在処理している配列  

```
var foodList = {
  'オムライス': 450,
  '焼きそば': 500,
  'お好み焼き': 600,
  '焼き飯': 400
};
 
//任意のキーワードを指定する
var order = ['焼き飯', 'お好み焼き'];
 
var result = order.map( function( value, index, array ) {
 
//配列のキーワードを使ってオブジェクト内の値を取得する
    return this[value];
 
}, foodList );
 
console.log( result ); //[400, 600]
 
```
## filter関数

filter関数は下記のように配列の要素を絞ることができる
```
const products = [
  { name: "きゅうり", type: "野菜" },
  { name: "オレンジ", type: "フルーツ" }
];


const x = products.filter((product) => {
  return product.type === "フルーツ";
  
}); 

x //[{"name":"オレンジ","type":"フルーツ"}]

```

## find関数

下記のように配列の中から特定のものを取り出すときに利用できる。
```
const accounts = [{ balance: -10 }, { balance: 12 }, { balance: 0 }];

const account = accounts.find((account) => {
  return (account.balance = 12);
});

console.log(account);

```

## everyとsome
everyは論理積を返す、someは論理和を返す。

## オブジェクトリテラル

下記コマンドのred: red と　blue: blue はプロパティとキーの値と変数名が等しい場合は省略記法が使える。  
const x = { object:key }  
```
const red = '#ff0000';
const blue = '#0000ff';

const COLORS = { red: red, blue: blue };
```

下記コマンドが省略記法である。
```
const red = '#ff0000';
const blue = '#0000ff';

const COLORS = { red, blue};
```

## デフォルト引数
下記のような関数があった場合、デフォルト引数を利用すれば、省略可できる。

```
function sum(a, b) {
  if (a === undefined) {
    a = 0; 
  }
  
  if (b === undefined) {
    b = 0; 
  }
  
  return a + b;
}
```
下記のようにa=0とb=0をデフォルトとして設定できる。
```
function sum(a=0, b=0) {
  if (a === undefined) {
  }
  
  if (b === undefined) {
  }
  
  return a + b;
}
```

reduce関数
reduce関数は引数をふたつとり、１つ目は今まで通りの配列などの処理を書くが、２つ目は初期値をかく。  
下記のように合計を求めるときに便利

```
const trips = [{ distance: 34 }, { distance: 12 } , { distance: 1 }];

const totalDistance = trips.reduce(function(sum, trip) {
  return trip.distance + sum;
}, 0); //初期値0

totalDistance //47

```


