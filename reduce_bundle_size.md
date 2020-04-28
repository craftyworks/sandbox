## About

별것도 없는데 번들 사이즈가 300KB 를 넘어섰다. 빌드 할때마다 warning 이 떠서 사이즈를 줄여보기로 했다. 이 문서는 그 과정에서의 삽질의 기록이다.

### 범인 찾기

`webpack` 은 import 된 모듈 내에서 실제로 쓰이는 스크립트만 골라서 번들링을 해준다고 한다. 그러나 세상에 공짜는 없다.

번들 사이즈가 크다면 일단 범인을 찾아보자. `webpack-bundle-analyzer` 를 사용하면 번들내의 각 모듈들을 사이즈 별로 treemap 을 만들어서 보여준다.

```
npm i --save-dev webpack-bundle-analyzer
```

`vue.confi.js` 파일에 플러그인 설정을 추가한다.

```javascript
const BundleAnalyzerPlugin = require('webpack-bundle-analyzer').BundleAnalyzerPlugin

module.exports = {

  configureWebpack: (config) => {
   if (process.env.NODE_ENV === 'production') {
      config.plugins.push(new BundleAnalyzerPlugin())
    }
  }
```

이제 빌드를 실행하면 번들 어날라이저가 분석을 실행하고 그 결과를 브라우저에서 확인할 수 있다.

아래 옵션을 설정하면 브라우저가 자동으로 실행되지 않는다. 그리고 결과는 docs/report.html 파일로 생성된다.

```javascript
      config.plugins.push(new BundleAnalyzerPlugin({ analyzerMode: 'static', openAnalyzer: false }))
```

### lodast -> underscore

범인은 `lodash` 와 `d3` 였다. 일단 `lodash` 를 `underscore` 로 교체하자.

`lodash` 는 `underscore` 의 슈퍼셋이라 그런지 사이즈가 더 크다.

```javascript
// import debounce from 'lodash/fp/debounce'
import debounce from 'underscore/modules'
export default {
  install (Vue) {
    Vue.set(Vue.prototype, '_', { debounce })
  }
}
```

### d3

rollup 을 이용해서 d3 의 사이즈를 확 줄인 커스텀 번들 js 파일을 생성할 수 있다.

* https://bl.ocks.org/mbostock/bb09af4c39c79cffcde4

#### package.json - dependency

```json
  "devDependencies": {
    "rollup": "^2.7.3",
    "rollup-plugin-node-resolve": "^5.2.0",
    "uglify-js": "^3.9.1",
  }
```
#### input d3.js

```javascript
import { select } from 'd3-selection'
import { nest } from 'd3-collection'
import { range } from 'd3-array'
import { scaleLinear } from 'd3-scale'
import { format } from 'd3-format'
import { line, curveBasis } from 'd3-shape'

export default {
  select: select, nest: nest, range: range, scaleLinear: scaleLinear, format: format, line: line, curveBasis: curveBasis
}

```

#### rollup.config.js

```javascript
import npm from 'rollup-plugin-node-resolve'

export default {
  input: 'src/rollup/d3.js',
  output: {
    name: 'd3',
    file: 'd3.js',
    format: 'umd',
  },
  plugins: [npm({ jsnext: true })]
}
```

#### package.json - script

```json
  "scripts": {
    "rollup": "rollup -c && uglifyjs d3.js -c -m -o d3.min.js",
  }
```

#### import assets

생성된 `d3.min.js` 파일을 src/assets 폴더로 복사 한다. 

다음과 같이 플러그인 형태로 import 한다.

```javascript
import * as d3 from '@/assets/d3.min.js'

export default {
  install (Vue) {
    Vue.set(Vue.prototype, 'd3', d3)
  }
}
```

#### rollup 하지마라

> 결과를 이야기 하자면 rollup 하지 마라. 걍 webpack 을 믿어라. 실제로 `d3` 는 아래처럼 임포트해서 사용했을 때 오히려 번들 사이즈가 더 줄어 들었다.

```javascript
import { select } from 'd3-selection'
import { nest } from 'd3-collection'
import { range } from 'd3-array'
import { scaleLinear } from 'd3-scale'
import { format } from 'd3-format'
import { curveBasis, line } from 'd3-shape'

export default {
  install (Vue) {
    const d3 = Object.assign({}, { select, nest, range, scaleLinear, format, line, curveBasis })
    Vue.set(Vue.prototype, 'd3', d3)
  }
}
```
