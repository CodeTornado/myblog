```js
devServer: {
    disableHostCheck: true,
    proxy: {
      '/api': {
        target: 'http://xxxxxqi.com',
        ws: true,
        changeOrigin: true,
        pathRewrite: {
          '^/api': ''
        }
      },
      '/content': {
        target: 'http://chxxxxxnqi.com',
        changeOrigin: true,
        ws: true,
        pathRewrite: {
          '^/content': ''
        }
      }
    }
  }

```

在 vue.config.js 直接配置即可跨域