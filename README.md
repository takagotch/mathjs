### mathjs
---
https://github.com/josdejong/mathjs

http://mathjs.org/

```
npm install mathjs

npm install
npm run build
npm test
npm run test: browser
npm run test:browserstack
npm run coverage
```

```js
const math = require('mathjs')

math.round(math.e, 3)
math.atan2(3, -3)
math.log(10000, 10)
math.sqrt(-4)
math.pow([[-1, 2], [3, 1]], 2)
math.deribative('x^2 + x', 'x')

math.eval('12 / (2.3 + 0.7)')
math.eval('12.7 cm to inch')
math.eval('sin(45 deg) ^ 2')
math.eval('9 / 3 + 2i')
math.eval('det([-1, 2 3, 1])')

math.chain(3)
  .add(4)
  .multiply(2)
  .done()
```

```js
```


