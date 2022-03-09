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

また、filter関数は削除機能にも応用できる.  
例えば、どこかのタグにonClickDeleteイベントをつけた時を考える。
未完了リストの配列incompleteTodosが存在すると仮定して、filter関数を用いる。  
ここで、todoリストの1つがindex番目でないものをreturnしている。  
逆に言うと、index番目のものを削除している
```
  const onClickDelete = (index) => {
    const newTodos = [...incompleteTodos].filter(
      (todo, todoIndex) => todoIndex !== index
    );
    setIncompleteTodos(newTodos);
  };
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

## スプレッド構文
下記のように配列をまとめて扱える。
```
const x = [1,2,3,4,5]
const y = [6,7,8,9]
const z = [...x,...y]

z //[1,2,3,4,5,6,7,8,9]
```

また、下記のようにリバースメソッドを使える。
aに直接リバースメソッドを使うと配列自体が変更するが、  
bにリバースメソッドを使うことで、aの配列を崩すことなく、新しい逆順の配列を作成できる.  
```
const a = [1,2,3]
const b = [...a].reverse();

b //[3,2,1]
```

## 分割代入
従来までは下記のようにshop.typeのようにして記述していたが、これは冗長である。
```
const shop = {
	type:'りんご'
	ammount: '100'
}
 
const type = shop.type
const ammount = shop.ammount

type //りんご
ammount // 100
```
分割代入を用いれば下記のようにコンパクトにかけるようになる。

```
const shop = {
	type:'りんご'
	ammount: '100'
}
 
const {type, ammount} = shop;
type //りんご
ammount // 100
```
下記のように、配列に名前を与えてなくても、分割代入でnameなどの名前を与えることで、配列のそれぞれの要素に名前が自動採番される。  
```
const companies = [
	'Google',
	'Facebook',
	'Uber,
]

const [name, name2, name3] = companies
name //Google
name2 //Facebook
name3 //uber

```
また、下記のようにレスト演算子（スプレッド構文）を用いると、  
一つ目のnameにはGoogleを注入し、他の配列の要素を...restに配列として注入することができる。
```
const companies = [
	'Google',
	'Facebook',
	'Uber,
]

const [name, ...rest] = companies
name //Google
...rest //["Facebook","Uber"]

```

下記のような配列から、locationのマウンテンビューを取りたい場合は、  
`companies[0].location`のようにかいてもいいが、冗長である。  
よって、分割代入をもちいて　 `const [{ location }] = companies`のようにかくことで、効率化できる。
```
const companies = [
	{'Google',location:'マウンテンビュー'}
	{'Facebook',location:'メロンパーク'}
	{'Uber,location: 'サンフランシスコ'}
]

const [{ location }] = companies;

location //マウンテンビュー

```

また、下記のようにこれまで習ったことを応用することで、classesで渡された配列に、subjectやtimeやteacherなどの情報を渡すことができる。
```
const classes = [
  [ '化学', '1時限目', '鈴木先生' ],
  [ '物理', '2時限目', '佐藤先生'],
];

const classesAsObject = classes.map(([subject,time,teacher]) => {
  return(
    {subject,time,teacher}
  )
})

classesAsObject
```

<img width="487" alt="image" src="https://user-images.githubusercontent.com/97214466/153367845-39170203-6323-4d67-9fe9-ec3fd6ae7176.png">

## クラスの継承

```javaScript
class Car {
	constructor({title}){
		this.title = title; }
}

class Toyota extends Car{          //extendsで継承
	constructor(options){
	super(options);　　　　　　　　　　//super()で親クラス（Car）のコンストラクタを呼び出している
	this.color = options.color;
	}
}

```

## Promiseとfetch(非同期処理)

### 前提知識
javaScriptはコードを途中で止める方法がないため、  
下図のように、dataのやりとりに3秒かかっている間、先に`console.log(data)`が出力されてしまい、意図しない結果となる。  
よって、javaScriptにはdataとやりとりしている3秒間の間、コードを止める手段が必要となる。
<img width="524" alt="image" src="https://user-images.githubusercontent.com/97214466/153815652-45efe279-9c8f-49d5-999f-0eefd673243f.png">

Promiseは下図のように3つの状態に分かれる。  
<img width="566" alt="image" src="https://user-images.githubusercontent.com/97214466/153816455-58fd5e0c-a266-4070-83c6-6c0a03942d46.png">  
resolvedで成功した場合は、thenでその後の処理を記述できる.  
rejectedで失敗した場合は、catchでその後のエラー処理を記述できる.  

### thenとfetch

下記コマンドのようにpromiseがresolve()の場合は、thenで書いたものが実行されるので、  
`処理が完了しました`と `処理が完了しました2` は出力されるが、`問題発生`は出力されない  
逆に、rejectの場合は、`問題発生`が出力される。  
```
const promise = new Promise((resolve, reject) => {
  resolve();
});

promise
  .then(() => console.log("処理が完了しました。"))
  .then(() => console.log("処理が完了しました2"))
  .catch(() => console.log("問題発生"));
```

また、下記コマンドのように`setTimeout`関数を用いて、時間差で（今回は3秒）resolve (rejectでもok)を返すことができる。
```
const promise = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve();
  }, 3000);
});

promise
  .then(() => console.log("処理が完了しました。"))
  .then(() => console.log("処理が完了しました2"))
  .catch(() => console.log("問題発生"));

```
また、Promise以外にもasync関数を用いれば非同期関数を呼び出せる。  
async関数はtry~catch文のように記述できる  



## for of 文

下記のように `for (let 新しい配列　of 元の配列)`で配列処理を記述できる。
```
const numbers = [1,2,3]

let total = 0;

for (let number of numbers) {
  total += number; //10
}
```

## generator

generatorとは繰り返し利用できる関数である。  
generatorはこのように、`function* numbers(){}`定義したい関数に * マークをつけることでgeneratorにすることができる。  

### 余談
シンタックスシュガーとは、糖衣構文といわれ、プログラミング言語において、既存の記法を読みやすくするために導入された構文を表す。
