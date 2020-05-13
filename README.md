# damage-calc
[![CircleCI](https://circleci.com/gh/kunifu-study/damage-calc-4005-v2-yarn-jest.svg?style=svg)](https://circleci.com/gh/kunifu-study/damage-calc-4005-v2-yarn-jest)

このモジュールでは、ダメージ計算を行うことができます。  
ダメージ計算には

- ダメージ
- 防御
- 防御貫通

以上 3 つの整数値が与えられ、結果として実効ダメージが整数値として得られます。

計算アルゴリズムは以下のように定義されます。

- 負の入力値があった場合には0として扱い、2000以上の入力値は2000として扱う。
- 実効防御は、防御 - 防御貫通 で定義され、この実効防御は、0未満にはならない。
- ダメージ減少率は、実効防御 / (100 + 実効防御) で定義され、
  実効ダメージは、ダメージ * (1 - ダメージ減少率) を小数点以下で四捨五入した値となる。

## 使い方

```js
var dc = require('.');
console.log(dc.effectiveDamage(100, 50, 30));
```

以上を実行すると、

```
83
```

と表示されます。

以上の例では、ダメージは 100、防御が 50、防御貫通が30で定義されています。  
実効防御は、 50 - 30 で 20 となります。  
ダメージ減少率は、 20 / (100 + 20) であり、 1 / 6 です。
実効ダメージは、 100 * (1 - (1 / 6)) であり、 
計算すると 83.33333... となり、
小数点以下の四捨五入の結果、実効ダメージの 83 の値が得られます。
