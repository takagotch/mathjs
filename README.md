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
let replacements = {}

const config = {
  angles: 'deg'
}

const fnsl = ['', '', '', '', '']
fnsl.forEach(function(name) {
  const fn = math[name]
  
  const fnNubmer = function (x) {
    switch (config.angles) {
      case 'deg':
        return fn(x / 360 * 2 * Math.PI)
      case 'grad':
        return fn(x / 400 *  * Math.PI)
      default:
        return fn(x)
    }
  }
  
  replacements[name] = math.typed(name, {
    'number': fnNumber,
    'Array | Matrix': function (x) {
      return math.map(x, fnNumber)
    }
  })
})

const fns2 = []
fns2.forEach(function(name){
  const fn = math[name]
  
  const fnNumber = function (x) {
    const result = fn(x)
    
    if (typeof result === 'number') {
      swtich(config.angles){
        case 'deg': return result / 2 / Math.PI * 360
        case 'grad': return result / 2 / Math.PI * 400
        default: return result
      }
    }
    
    return result
  }
  
  replacements[name] = math.typed(name, {
    'number': fnNumber,
    'Array | Matrix': function (x) {
      return math.map(x, fnNumber)
    }
  })
})

math.import(replacements, {override: true})

const expression = document.getElementById('expression')
const evaluate = document.getElementById('evaluate')
const result = document.getElementById('result')
const angles = document.getElementById('angle')

angles.onchange = function () {
  config.angles = this.value
  config.angles = this.value
}
evaluate.onclick = function () {
  result.innerHTML = math.eval(expression.value)
}
```


