# api documentation for  [hapi-react-views (v9.2.1)](https://github.com/jedireza/hapi-react-views)  [![npm package](https://img.shields.io/npm/v/npmdoc-hapi-react-views.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-hapi-react-views) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-hapi-react-views.svg)](https://travis-ci.org/npmdoc/node-npmdoc-hapi-react-views)
#### A hapi view engine for React components.

[![NPM](https://nodei.co/npm/hapi-react-views.png?downloads=true)](https://www.npmjs.com/package/hapi-react-views)

[![apidoc](https://npmdoc.github.io/node-npmdoc-hapi-react-views/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-hapi-react-views_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-hapi-react-views/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-hapi-react-views/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-hapi-react-views/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Reza Akhavan",
        "email": "jedireza@gmail.com",
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
            "name": "jedireza",
            "email": "jedireza@gmail.com"
        }
    ],
    "name": "hapi-react-views",
    "optionalDependencies": {},
    "peerDependencies": {
        "react": "15.x.x",
        "react-dom": "15.x.x "
    },
    "readme": "ERROR: No README data found!",
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



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module hapi-react-views](#apidoc.module.hapi-react-views)
1.  [function <span class="apidocSignatureSpan">hapi-react-views.</span>compile (template, compileOpts)](#apidoc.element.hapi-react-views.compile)



# <a name="apidoc.module.hapi-react-views"></a>[module hapi-react-views](#apidoc.module.hapi-react-views)

#### <a name="apidoc.element.hapi-react-views.compile"></a>[function <span class="apidocSignatureSpan">hapi-react-views.</span>compile (template, compileOpts)](#apidoc.element.hapi-react-views.compile)
- description and source-code
```javascript
function compile(template, compileOpts) {

    compileOpts = Hoek.applyToDefaults(DEFAULTS, compileOpts);

    return function runtime(context, renderOpts) {

        renderOpts = Hoek.applyToDefaults(compileOpts, renderOpts);

        let View = require(renderOpts.filename);
        // support for es6 default export semantics
        View = View.default || View;

        const ViewElement = React.createFactory(View);

        let output = renderOpts.doctype;

        let layoutPath;

        if (renderOpts.layout) {
            layoutPath = Path.join(renderOpts.layoutPath, renderOpts.layout);
            let Layout = require(layoutPath);
            // support for es6 default export semantics
            Layout = Layout.default || Layout;

            const LayoutElement = React.createFactory(Layout);

            const viewOutput = ReactDOMServer[renderOpts.renderMethod](ViewElement(context));

            output += ReactDOMServer[renderOpts.layoutRenderMethod](LayoutElement(context, viewOutput));
        }
        else {
            output += ReactDOMServer[renderOpts.renderMethod](ViewElement(context));
        }

<span class="apidocCodeCommentSpan">        /*
         * Transpilers tend to take a while to start up. Here we delete the
         * view and layout modules (and any modules matching the
         * 'removeCacheRegExp' pattern) from the require cache so we don't need
         * to restart the app to see view changes.
         */
</span>        if (renderOpts.removeCache) {
            if (renderOpts.layout) {
                const layoutKey = require.resolve(layoutPath);
                delete require.cache[layoutKey];
            }

            const viewKey = require.resolve(renderOpts.filename);
            delete require.cache[viewKey];

            if (renderOpts.removeCacheRegExp) {
                const regexp = new RegExp(renderOpts.removeCacheRegExp);

                Object.keys(require.cache).forEach((cacheKey) => {

                    if (regexp.test(cacheKey)) {
                        delete require.cache[cacheKey];
                    }
                });
            }
        }

        return output;
    };
}
```
- example usage
```shell
n/a
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
