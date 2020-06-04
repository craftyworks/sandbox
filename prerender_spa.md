```
npm install --save-dev prerender-spa-plugin
```

### package.json

```javascript

const path = require('path')
const PrerenderSpaPlugin = require('prerender-spa-plugin')

const productionPlugins = [
  new PrerenderSpaPlugin({
    staticDir: path.join(__dirname, 'docs'),
    routes: [
      '/'
    ],
    renderer: new PrerenderSpaPlugin.PuppeteerRenderer({
      renderAfterElementExists: '#app',
      headless: true,
      renderAfterTime: 1000
    })
  })
]

module.exports = {
  configureWebpack: (config) => {
    if (process.env.NODE_ENV === 'production') {
      config.plugins.push(...productionPlugins)
    }
  },
  ...
}
```

### 주의사항

`puppeteer` 를 사용하기 때문에 `npm install` 을 Dos 환경에서 수행해야 한다.