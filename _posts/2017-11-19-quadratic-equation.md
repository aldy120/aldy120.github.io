---
layout: default
comments: true
---
# 一元二次方程式 (Quadratic equation)
今天要說的主題是一元二次方程式，以及它的公式解。

一元二次方程式，通常長這個樣子：

$$ ax^2 + bx + c = 0 $$

x 代表未知數，a, b, c 分別代表已知的數字，其中 a 不能等於零。如果 a = 0, 那就會變成一次方程式，就不是二次了。

# 一元二次方程式公式解 (Quadratic formula)
先把等號兩邊都除以a

$$ x^2 + \frac{b}{a} x + \frac{c}{a} = 0 $$

把第三項移動到等號另一邊

$$ x^2 + \frac{b}{a} x = - \frac{c}{a} $$

接下來是配方法 (Completing the square)，兩邊加上第二項一半的平方。

$$ x^2 + \frac{b}{a} x + \left(\frac{b}{2a}\right)^2 = - \frac{c}{a} + \left(\frac{b}{2a}\right)^2 $$

左邊有個平方和可以簡化，右邊可以合併，這樣等等開根號就不會變得過於複雜

$$ \left(x + \frac{b}{2a}\right) ^2 = - \frac{4ac}{4a^2} + \frac{b^2}{4a^2} $$

$$ \left(x + \frac{b}{2a}\right) ^2 = \frac{-4ac + b^2}{4a^2} $$

$$ \left(x + \frac{b}{2a}\right) ^2 = \frac{b^2 - 4ac}{4a^2} $$

兩邊同開根號

$$ \left(x + \frac{b}{2a}\right) = \pm \frac{\sqrt{b^2 - 4ac}}{2a} $$

$$ x = \frac{-b \pm \sqrt{b^2 - 4ac}}{2a} $$

解法不只這一種，更多請見[維基百科](https://en.wikipedia.org/wiki/Quadratic_formula)

# 這有什麼用?
我無法很簡單地告訴你這有什麼用，但不會這個的話，總覺得沒什麼用。

# JavaScript 實作
此函數不支援虛數解
```js
function solveQuadratic(a, b, c) {
  if (a === 0) {
    throw new Error('a = 0')
  }
  return [
    (-b + Math.sqrt(b * b - 4 * a * c)) / (2 * a), 
    (-b - Math.sqrt(b * b - 4 * a * c)) / (2 * a)
  ]
}
```

# 參考
[wikipedia](https://en.wikipedia.org/wiki/Quadratic_equation)