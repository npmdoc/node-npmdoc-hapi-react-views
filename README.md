# npmdoc-hapi-react-views

#### api documentation for  [hapi-react-views (v9.2.1)](https://github.com/jedireza/hapi-react-views)  [![npm package](https://img.shields.io/npm/v/npmdoc-hapi-react-views.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-hapi-react-views) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-hapi-react-views.svg)](https://travis-ci.org/npmdoc/node-npmdoc-hapi-react-views)

#### A hapi view engine for React components.

[![NPM](https://nodei.co/npm/hapi-react-views.png?downloads=true&downloadRank=true&stars=true)](https://www.npmjs.com/package/hapi-react-views)

- [https://npmdoc.github.io/node-npmdoc-hapi-react-views/build/apidoc.html](https://npmdoc.github.io/node-npmdoc-hapi-react-views/build/apidoc.html)

[![apidoc](https://npmdoc.github.io/node-npmdoc-hapi-react-views/build/screenCapture.buildCi.browser.%252Ftmp%252Fbuild%252Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-hapi-react-views/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-hapi-react-views/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-hapi-react-views/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Reza Akhavan",
        "url": "http://reza.akhavan.me/"
    },
    "bugs": {
        "url": "https://github.com/jedireza/hapi-react-views/issues"
    },
    "dependencies": {
        "hoek": "4.x.x"
    },
    "description": "A hapi view engine for React components.",
    "devDependencies": {
        "babel": "6.x.x",
        "babel-core": "6.x.x",
        "babel-loader": "6.x.x",
        "babel-preset-es2015": "6.x.x",
        "babel-preset-react": "6.x.x",
        "code": "4.x.x",
        "hapi": "15.x.x",
        "inert": "4.x.x",
        "lab": "11.x.x",
        "react": "15.x.x",
        "react-dom": "15.x.x",
        "vision": "4.x.x",
        "webpack": "1.x.x"
    },
    "directories": {},
    "dist": {
        "shasum": "3f35aa685ca10174769253dc3276f7e3961cdd87",
        "tarball": "https://registry.npmjs.org/hapi-react-views/-/hapi-react-views-9.2.1.tgz"
    },
    "gitHead": "14bce9187d3276ed5a4da6d0e39f025ddea0a59c",
    "homepage": "https://github.com/jedireza/hapi-react-views",
    "keywords": [
        "hapi",
        "react",
        "views",
        "universal",
        "isomorphic"
    ],
    "license": "MIT",
    "main": "index.js",
    "maintainers": [
        {
            "name": "jedireza"
        }
    ],
    "name": "hapi-react-views",
    "optionalDependencies": {},
    "peerDependencies": {
        "react": "15.x.x",
        "react-dom": "15.x.x "
    },
    "repository": {
        "type": "git",
        "url": "git+https://github.com/jedireza/hapi-react-views.git"
    },
    "scripts": {
        "layout-component-example": "node examples/layout-component/server",
        "layout-example": "node examples/layout/server",
        "remount-example": "webpack --config examples/remount/webpack.js && node examples/remount/server",
        "simple-example": "node examples/simple/server",
        "test": "lab -t 100 -c -L -I 'Reflect,core,_babelPolyfill,regeneratorRuntime,__core-js_shared__'",
        "test-cover": "lab -t 100 -c -r html -o test/artifacts/coverage.html && open test/artifacts/coverage.html"
    },
    "version": "9.2.1"
}
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
