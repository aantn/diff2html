# diff2html

[![Codacy Quality Badge](https://api.codacy.com/project/badge/Grade/06412dc3f5a14f568778d0db8a1f7dc8)](https://www.codacy.com/app/rtfpessoa/diff2html?utm_source=github.com&utm_medium=referral&utm_content=rtfpessoa/diff2html&utm_campaign=Badge_Grade)
[![Codacy Coverage Badge](https://api.codacy.com/project/badge/Coverage/06412dc3f5a14f568778d0db8a1f7dc8)](https://www.codacy.com/app/rtfpessoa/diff2html?utm_source=github.com&utm_medium=referral&utm_content=rtfpessoa/diff2html&utm_campaign=Badge_Coverage)
[![GitHub CI](https://github.com/rtfpessoa/diff2html/workflows/CI/badge.svg?branch=master)](https://github.com/rtfpessoa/diff2html/actions?query=branch%3Amaster)

[![npm](https://img.shields.io/npm/v/diff2html.svg)](https://www.npmjs.com/package/diff2html)
[![Dependency Status](https://david-dm.org/rtfpessoa/diff2html.svg)](https://david-dm.org/rtfpessoa/diff2html)
[![devDependency Status](https://david-dm.org/rtfpessoa/diff2html/dev-status.svg)](https://david-dm.org/rtfpessoa/diff2html#info=devDependencies)
[![cdnjs](https://img.shields.io/cdnjs/v/diff2html)](https://cdnjs.com/libraries/diff2html)

[![node](https://img.shields.io/node/v/diff2html.svg)]() [![npm](https://img.shields.io/npm/l/diff2html.svg)]()
[![npm](https://img.shields.io/npm/dm/diff2html.svg)](https://www.npmjs.com/package/diff2html)
[![All Contributors](https://img.shields.io/badge/all_contributors-22-orange.svg?style=flat-square)](#contributors-)
[![Gitter](https://badges.gitter.im/rtfpessoa/diff2html.svg)](https://gitter.im/rtfpessoa/diff2html?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge)

diff2html generates pretty HTML diffs from git diff or unified diff output.

[![NPM](https://nodei.co/npm/diff2html.png?downloads=true&downloadRank=true&stars=true)](https://nodei.co/npm/diff2html/)

## Features

- Supports git and unified diffs

- Line by line and Side by side diff

- New and old line numbers

- Inserted and removed lines

- GitHub like visual style

- Code syntax highlight

- Line similarity matching

- Easy code selection

## Online Example

> Go to [diff2html](https://diff2html.xyz/)

## Distributions

- [WebJar](http://www.webjars.org/)
- [Node Library](https://www.npmjs.org/package/diff2html)
- [NPM CLI](https://www.npmjs.org/package/diff2html-cli)
- Manually download and import:
  - Browser / Bundle
    - Parser and HTML Generator
      - [bundles/js/diff2html.min.js](./bundles/js/diff2html.min.js) - includes the diff parser and html generator
    - Wrapper and helper adding syntax highlight, synchronized scroll, and other nice features
      - [bundles/js/diff2html-ui.min.js](./bundles/js/diff2html-ui.min.js) - includes the wrapper of diff2html with
        highlight for all `highlight.js` supported languages
      - [bundles/js/diff2html-ui-slim.min.js](./bundles/js/diff2html-ui-slim.min.js) - includes the wrapper of diff2html
        with "the most common" `highlight.js` supported languages
      - [bundles/js/diff2html-ui-base.min.js](./bundles/js/diff2html-ui-base.min.js) - includes the wrapper of diff2html
        without including a `highlight.js` implementation. You can use it without syntax highlight or by passing your
        own implementation with the languages you prefer
  - NPM / Node.js library
    - ES5
      - [lib/diff2html.js](./lib/diff2html.js) - includes the diff parser and html generator
      - [lib/ui/js/diff2html-ui.js](./lib/ui/js/diff2html-ui.js) - includes the wrapper of diff2html with highlight for
        all `highlight.js` supported languages
      - [lib/ui/js/diff2html-ui-slim.js](./lib/ui/js/diff2html-ui-slim.js) - includes the wrapper of diff2html with "the
        most common" `highlight.js` supported languages
      - [lib/ui/js/diff2html-ui-base.js](./lib/ui/js/diff2html-ui-base.js)
    - ES6
      - [lib-esm/diff2html.js](./lib-esm/diff2html.js) - includes the diff parser and html generator
      - [lib/ui/js/diff2html-ui.js](./lib/ui/js/diff2html-ui.js) - includes the wrapper of diff2html with highlight for
        all `highlight.js` supported languages
      - [lib/ui/js/diff2html-ui-slim.js](./lib/ui/js/diff2html-ui-slim.js) - includes the wrapper of diff2html with "the
        most common" `highlight.js` supported languages
      - [lib/ui/js/diff2html-ui-base.js](./lib/ui/js/diff2html-ui-base.js) - includes the wrapper of diff2html without
        including a `highlight.js` implementation. You can use it without syntax highlight or by passing your own
        implementation with the languages you prefer

## Diff2Html Usage

To load correctly in the Browser you always need to include the stylesheet in the final HTML.

Import the stylesheet

```html
<!-- CSS -->
<link rel="stylesheet" type="text/css" href="bundles/css/diff2html.min.css" />
```

You can also refer to it from a CDN like [CDNJS](https://cdnjs.com/libraries/diff2html).

### Diff2Html API

> JSON representation of the diff

```ts
function parse(diffInput: string, configuration: Diff2HtmlConfig = {}): DiffFile[];
```

> Pretty HTML representation of the diff

```ts
function html(diffInput: string | DiffFile[], configuration: Diff2HtmlConfig = {}): string;
```

> Check out the [docs/demo.html](./docs/demo.html) for a demo example.

### Diff2Html Configuration

The HTML output accepts a Javascript object with configuration. Possible options:

- `outputFormat`: the format of the output data: `'line-by-line'` or `'side-by-side'`, default is `'line-by-line'`
- `drawFileList`: show a file list before the diff: `true` or `false`, default is `false`
- `diffStyle`: show differences level in each line: `word` or `char`, default is `word`
- `matching`: matching level: `'lines'` for matching lines, `'words'` for matching lines and words or `'none'`, default
  is `none`
- `matchWordsThreshold`: similarity threshold for word matching, default is 0.25
- `matchingMaxComparisons`: perform at most this much comparisons for line matching a block of changes, default is
  `2500`
- `maxLineSizeInBlockForComparison`: maximum number os characters of the bigger line in a block to apply comparison,
  default is `200`
- `maxLineLengthHighlight`: only perform diff changes highlight if lines are smaller than this, default is `10000`
- `renderNothingWhenEmpty`: render nothing if the diff shows no change in its comparison: `true` or `false`, default is
  `false`
- `compiledTemplates`: object with previously compiled templates to replace parts of the html
- `rawTemplates`: object with raw not compiled templates to replace parts of the html
  > For more information regarding the possible templates look into
  > [src/templates](https://github.com/rtfpessoa/diff2html/tree/master/src/templates)

### Diff2Html Browser

Import the stylesheet and the library code

```html
<!-- CSS -->
<link rel="stylesheet" type="text/css" href="bundles/css/diff2html.min.css" />

<!-- Javascripts -->
<script type="text/javascript" src="bundles/js/diff2html.min.js"></script>
```

It will now be available as a global variable named `Diff2Html`.

```js
document.addEventListener('DOMContentLoaded', () => {
  var diffHtml = global.Diff2Html.html('<Unified Diff String>', {
    drawFileList: true,
    matching: 'lines',
    outputFormat: 'side-by-side',
  });
  document.getElementById('destination-elem-id').innerHTML = diffHtml;
});
```

### Diff2Html NPM / Node.js Library

```js
const Diff2html = require('diff2html');
const diffJson = Diff2html.parse('<Unified Diff String>');
const diffHtml = Diff2html.html(diffJson, { drawFileList: true });
document.getElementById('destination-elem-id').innerHTML = diffHtml;
```

### Diff2Html Examples

#### Diff2Html Angular Example

- Typescript

```typescript
import * as Diff2Html from 'diff2html';
import { Component, OnInit } from '@angular/core';

export class AppDiffComponent implements OnInit {
  outputHtml: string;
  constructor() {
    this.init();
  }

  ngOnInit() {}

  init() {
    let strInput =
      '--- a/server/vendor/golang.org/x/sys/unix/zsyscall_linux_mipsle.go\n+++ b/server/vendor/golang.org/x/sys/unix/zsyscall_linux_mipsle.go\n@@ -1035,6 +1035,17 @@ func Prctl(option int, arg2 uintptr, arg3 uintptr, arg4 uintptr, arg5 uintptr) (\n \n // THIS FILE IS GENERATED BY THE COMMAND AT THE TOP; DO NOT EDIT\n \n+func Pselect(nfd int, r *FdSet, w *FdSet, e *FdSet, timeout *Timespec, sigmask *Sigset_t) (n int, err error) {\n+\tr0, _, e1 := Syscall6(SYS_PSELECT6, uintptr(nfd), uintptr(unsafe.Pointer(r)), uintptr(unsafe.Pointer(w)), uintptr(unsafe.Pointer(e)), uintptr(unsafe.Pointer(timeout)), uintptr(unsafe.Pointer(sigmask)))\n+\tn = int(r0)\n+\tif e1 != 0 {\n+\t\terr = errnoErr(e1)\n+\t}\n+\treturn\n+}\n+\n+// THIS FILE IS GENERATED BY THE COMMAND AT THE TOP; DO NOT EDIT\n+\n func read(fd int, p []byte) (n int, err error) {\n \tvar _p0 unsafe.Pointer\n \tif len(p) > 0 {\n';
    let outputHtml = Diff2Html.html(strInput, { drawFileList: true, matching: 'lines' });
    this.outputHtml = outputHtml;
  }
}
```

- HTML

```html
<!DOCTYPE html>
<html>
  <head>
    <title>diff2html</title>
  </head>
  <body>
    <div [innerHtml]="outputHtml"></div>
  </body>
</html>
```

- `.angular-cli.json` - Add styles

```json
"styles": [
  "diff2html.min.css"
]
```

#### Diff2Html Vue.js Example

```vue
<template>
  <div v-html="prettyHtml" />
</template>

<script>
import * as Diff2Html from 'diff2html';
import 'diff2html/bundles/css/diff2html.min.css';

export default {
  data() {
    return {
      diffs:
        '--- a/server/vendor/golang.org/x/sys/unix/zsyscall_linux_mipsle.go\n+++ b/server/vendor/golang.org/x/sys/unix/zsyscall_linux_mipsle.go\n@@ -1035,6 +1035,17 @@ func Prctl(option int, arg2 uintptr, arg3 uintptr, arg4 uintptr, arg5 uintptr) (\n \n // THIS FILE IS GENERATED BY THE COMMAND AT THE TOP; DO NOT EDIT\n \n+func Pselect(nfd int, r *FdSet, w *FdSet, e *FdSet, timeout *Timespec, sigmask *Sigset_t) (n int, err error) {\n+\tr0, _, e1 := Syscall6(SYS_PSELECT6, uintptr(nfd), uintptr(unsafe.Pointer(r)), uintptr(unsafe.Pointer(w)), uintptr(unsafe.Pointer(e)), uintptr(unsafe.Pointer(timeout)), uintptr(unsafe.Pointer(sigmask)))\n+\tn = int(r0)\n+\tif e1 != 0 {\n+\t\terr = errnoErr(e1)\n+\t}\n+\treturn\n+}\n+\n+// THIS FILE IS GENERATED BY THE COMMAND AT THE TOP; DO NOT EDIT\n+\n func read(fd int, p []byte) (n int, err error) {\n \tvar _p0 unsafe.Pointer\n \tif len(p) > 0 {\n',
    };
  },
  computed: {
    prettyHtml() {
      return Diff2Html.html(this.diffs, {
        drawFileList: true,
        matching: 'lines',
        outputFormat: 'side-by-side',
      });
    },
  },
};
</script>
```

## Diff2HtmlUI

> Simple wrapper to ease simple tasks in the browser such as: code highlight and js effects

- Invoke Diff2html
- Inject output in DOM element
- Enable collapsible file summary list
- Enable syntax highlight of the code in the diffs

### Diff2HtmlUI API

> Create a Diff2HtmlUI instance

```ts
constructor(diffInput: string | DiffFile[], target: HTMLElement) // diff2html-ui, diff2html-ui-slim
constructor(diffInput: string | DiffFile[], target: HTMLElement, config: Diff2HtmlUIConfig = {}, hljs?: HighlightJS) // diff2html-ui-base
```

> Generate and inject in the document the Pretty HTML representation of the diff

```ts
draw(): void
```

> Enable extra features

```ts
synchronisedScroll(): void
fileListToggle(startVisible: boolean): void
highlightCode(): void
```

> Check out the [docs/demo.html](./docs/demo.html) for a demo example.

### Diff2HtmlUI Configuration

- `synchronisedScroll`: scroll both panes in side-by-side mode: `true` or `false`, default is `true`
- `highlight`: syntax highlight the code on the diff: `true` or `false`, default is `true`
- `fileListToggle`: allow the file summary list to be toggled: `true` or `false`, default is `true`
- `fileListStartVisible`: choose if the file summary list starts visible: `true` or `false`, default is `false`
- `smartSelection`: allow selection of the code without including line numbers of line prefixes: `true` or `false`,
  default is `true`

> NOTE: All the options from Diff2Html are also valid configurations in Diff2HtmlUI

### Diff2HtmlUI Browser

#### Mandatory HTML resource imports

```html
<!-- CSS -->
<link rel="stylesheet" type="text/css" href="bundles/css/diff2html.min.css" />

<!-- Javascripts -->
<script type="text/javascript" src="bundles/js/diff2html-ui.min.js"></script>
```

#### Init

```js
const targetElement = document.getElementById('destination-elem-id');
const configuration = { drawFileList: true, matching: 'lines' };

const diff2htmlUi = new Diff2HtmlUI(diffString, targetElement, configuration);
// or
const diff2htmlUi = new Diff2HtmlUI(diffJson, targetElement, configuration);
```

#### Draw

```js
diff2htmlUi.draw();
```

#### Syntax Highlight

```html
<!-- Stylesheet -->
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/highlight.js/9.13.1/styles/github.min.css" />
<link rel="stylesheet" type="text/css" href="bundles/css/diff2html.min.css" />

<!-- Javascripts -->
<script type="text/javascript" src="bundles/js/diff2html-ui.min.js"></script>
```

> Pass the option `highlight` with value true or invoke `diff2htmlUi.highlightCode()` after `diff2htmlUi.draw()`.

```js
document.addEventListener('DOMContentLoaded', () => {
  const diffString = `diff --git a/sample.js b/sample.js
index 0000001..0ddf2ba
--- a/sample.js
+++ b/sample.js
@@ -1 +1 @@
-console.log("Hello World!")
+console.log("Hello from Diff2Html!")`;
  const targetElement = document.getElementById('myDiffElement');
  const configuration = { inputFormat: 'json', drawFileList: true, matching: 'lines', highlight: true };
  const diff2htmlUi = new Diff2HtmlUI(diffString, targetElement, configuration);
  diff2htmlUi.draw();
  diff2htmlUi.highlightCode();
});
```

#### Collapsable File Summary List

> Add the dependencies.

```html
<!-- Javascripts -->
<script type="text/javascript" src="bundles/js/diff2html-ui.min.js"></script>
```

> Invoke the Diff2HtmlUI helper Pass the option `fileListToggle` with value true or invoke
> `diff2htmlUi.fileListToggle()` after `diff2htmlUi.draw()`.

```js
document.addEventListener('DOMContentLoaded', () => {
  const targetElement = document.getElementById('myDiffElement');
  var diff2htmlUi = new Diff2HtmlUI(lineDiffExample, targetElement, { drawFileList: true, matching: 'lines' });
  diff2htmlUi.draw();
  diff2htmlUi.fileListToggle(false);
});
```

## Troubleshooting

### 1. Out of memory or Slow execution

#### Causes:

- Big files
- Big lines

#### Fix:

- Disable the line matching algorithm, by setting the option `{"matching": "none"}` when invoking diff2html

## Contributions

This is a developer friendly project, all the contributions are welcome. To contribute just send a pull request with
your changes following the guidelines described in `CONTRIBUTING.md`. I will try to review them as soon as possible.

## Contributors ✨

Thanks goes to these wonderful people ([emoji key](https://allcontributors.org/docs/en/emoji-key)):

<!-- ALL-CONTRIBUTORS-LIST:START - Do not remove or modify this section -->
<!-- prettier-ignore-start -->
<!-- markdownlint-disable -->
<table>
  <tr>
    <td align="center"><a href="https://rtfpessoa.xyz"><img src="https://avatars0.githubusercontent.com/u/902384?v=4" width="100px;" alt="Rodrigo Fernandes"/><br /><sub><b>Rodrigo Fernandes</b></sub></a><br /><a href="https://github.com/rtfpessoa/diff2html/commits?author=rtfpessoa" title="Code">💻</a></td>
    <td align="center"><a href="https://github.com/stockmind"><img src="https://avatars3.githubusercontent.com/u/5653847?v=4" width="100px;" alt="stockmind"/><br /><sub><b>stockmind</b></sub></a><br /><a href="https://github.com/rtfpessoa/diff2html/commits?author=stockmind" title="Code">💻</a></td>
    <td align="center"><a href="https://github.com/lantian"><img src="https://avatars3.githubusercontent.com/u/535545?v=4" width="100px;" alt="Ivan Vorontsov"/><br /><sub><b>Ivan Vorontsov</b></sub></a><br /><a href="https://github.com/rtfpessoa/diff2html/commits?author=lantian" title="Code">💻</a></td>
    <td align="center"><a href="http://www.nick-brewer.com"><img src="https://avatars1.githubusercontent.com/u/129300?v=4" width="100px;" alt="Nick Brewer"/><br /><sub><b>Nick Brewer</b></sub></a><br /><a href="https://github.com/rtfpessoa/diff2html/commits?author=brewern" title="Code">💻</a></td>
    <td align="center"><a href="http://heyitsmattwade.com"><img src="https://avatars0.githubusercontent.com/u/8504000?v=4" width="100px;" alt="Matt Wade"/><br /><sub><b>Matt Wade</b></sub></a><br /><a href="https://github.com/rtfpessoa/diff2html/issues?q=author%3Aromellem" title="Bug reports">🐛</a></td>
    <td align="center"><a href="http://mrfyda.github.io"><img src="https://avatars1.githubusercontent.com/u/593860?v=4" width="100px;" alt="Rafael Cortês"/><br /><sub><b>Rafael Cortês</b></sub></a><br /><a href="https://github.com/rtfpessoa/diff2html/commits?author=mrfyda" title="Code">💻</a></td>
    <td align="center"><a href="https://github.com/nmatpt"><img src="https://avatars2.githubusercontent.com/u/5034733?v=4" width="100px;" alt="Nuno Teixeira"/><br /><sub><b>Nuno Teixeira</b></sub></a><br /><a href="https://github.com/rtfpessoa/diff2html/commits?author=nmatpt" title="Code">💻</a></td>
  </tr>
  <tr>
    <td align="center"><a href="https://saino.me/"><img src="https://avatars0.githubusercontent.com/u/1567423?v=4" width="100px;" alt="Koki Oyatsu"/><br /><sub><b>Koki Oyatsu</b></sub></a><br /><a href="https://github.com/rtfpessoa/diff2html/issues?q=author%3Akaishuu0123" title="Bug reports">🐛</a></td>
    <td align="center"><a href="http://www.jamesmonger.com"><img src="https://avatars2.githubusercontent.com/u/2037007?v=4" width="100px;" alt="James Monger"/><br /><sub><b>James Monger</b></sub></a><br /><a href="https://github.com/rtfpessoa/diff2html/commits?author=Jameskmonger" title="Documentation">📖</a></td>
    <td align="center"><a href="http://wesssel.github.io/"><img src="https://avatars2.githubusercontent.com/u/7767299?v=4" width="100px;" alt="Wessel van der Pal"/><br /><sub><b>Wessel van der Pal</b></sub></a><br /><a href="#security-wesssel" title="Security">🛡️</a></td>
    <td align="center"><a href="https://jung-kim.github.io"><img src="https://avatars2.githubusercontent.com/u/5281068?v=4" width="100px;" alt="jk-kim"/><br /><sub><b>jk-kim</b></sub></a><br /><a href="https://github.com/rtfpessoa/diff2html/commits?author=jung-kim" title="Code">💻</a></td>
    <td align="center"><a href="https://github.com/sss0791"><img src="https://avatars1.githubusercontent.com/u/1446970?v=4" width="100px;" alt="Sergey Semenov"/><br /><sub><b>Sergey Semenov</b></sub></a><br /><a href="https://github.com/rtfpessoa/diff2html/issues?q=author%3Asss0791" title="Bug reports">🐛</a></td>
    <td align="center"><a href="http://researcher.watson.ibm.com/researcher/view.php?person=us-nickm"><img src="https://avatars3.githubusercontent.com/u/4741620?v=4" width="100px;" alt="Nick Mitchell"/><br /><sub><b>Nick Mitchell</b></sub></a><br /><a href="https://github.com/rtfpessoa/diff2html/issues?q=author%3Astarpit" title="Bug reports">🐛</a></td>
    <td align="center"><a href="https://github.com/samiraguiar"><img src="https://avatars0.githubusercontent.com/u/13439135?v=4" width="100px;" alt="Samir Aguiar"/><br /><sub><b>Samir Aguiar</b></sub></a><br /><a href="https://github.com/rtfpessoa/diff2html/commits?author=samiraguiar" title="Documentation">📖</a></td>
  </tr>
  <tr>
    <td align="center"><a href="https://twitter.com/pubkeypubkey"><img src="https://avatars3.githubusercontent.com/u/8926560?v=4" width="100px;" alt="pubkey"/><br /><sub><b>pubkey</b></sub></a><br /><a href="https://github.com/rtfpessoa/diff2html/commits?author=pubkey" title="Documentation">📖</a></td>
    <td align="center"><a href="https://github.com/iliyaZelenko"><img src="https://avatars1.githubusercontent.com/u/13103045?v=4" width="100px;" alt="Илья"/><br /><sub><b>Илья</b></sub></a><br /><a href="https://github.com/rtfpessoa/diff2html/commits?author=iliyaZelenko" title="Documentation">📖</a></td>
    <td align="center"><a href="https://akr.am"><img src="https://avatars0.githubusercontent.com/u/1823771?v=4" width="100px;" alt="Mohamed Akram"/><br /><sub><b>Mohamed Akram</b></sub></a><br /><a href="https://github.com/rtfpessoa/diff2html/issues?q=author%3Amohd-akram" title="Bug reports">🐛</a></td>
    <td align="center"><a href="https://github.com/emarcotte"><img src="https://avatars0.githubusercontent.com/u/249390?v=4" width="100px;" alt="Eugene Marcotte"/><br /><sub><b>Eugene Marcotte</b></sub></a><br /><a href="https://github.com/rtfpessoa/diff2html/commits?author=emarcotte" title="Code">💻</a></td>
    <td align="center"><a href="http://twitter.com/dimasabanin"><img src="https://avatars0.githubusercontent.com/u/8316?v=4" width="100px;" alt="Dima Sabanin"/><br /><sub><b>Dima Sabanin</b></sub></a><br /><a href="#maintenance-dsabanin" title="Maintenance">🚧</a></td>
    <td align="center"><a href="https://github.com/benabbottnz"><img src="https://avatars2.githubusercontent.com/u/2616473?v=4" width="100px;" alt="Ben Abbott"/><br /><sub><b>Ben Abbott</b></sub></a><br /><a href="https://github.com/rtfpessoa/diff2html/commits?author=benabbottnz" title="Documentation">📖</a></td>
    <td align="center"><a href="http://webminer.js.org"><img src="https://avatars1.githubusercontent.com/u/2196373?v=4" width="100px;" alt="弘树@阿里"/><br /><sub><b>弘树@阿里</b></sub></a><br /><a href="https://github.com/rtfpessoa/diff2html/issues?q=author%3Adickeylth" title="Bug reports">🐛</a></td>
  </tr>
  <tr>
    <td align="center"><a href="https://github.com/Rantanen"><img src="https://avatars0.githubusercontent.com/u/385385?v=4" width="100px;" alt="Mikko Rantanen"/><br /><sub><b>Mikko Rantanen</b></sub></a><br /><a href="https://github.com/rtfpessoa/diff2html/issues?q=author%3ARantanen" title="Bug reports">🐛</a></td>
  </tr>
</table>

<!-- markdownlint-enable -->
<!-- prettier-ignore-end -->

<!-- ALL-CONTRIBUTORS-LIST:END -->

This project follows the [all-contributors](https://github.com/all-contributors/all-contributors) specification.
Contributions of any kind welcome!

## License

Copyright 2014-present Rodrigo Fernandes. Released under the terms of the MIT license.

## Thanks

This project is inspired in [pretty-diff](https://github.com/scottgonzalez/pretty-diff) by
[Scott González](https://github.com/scottgonzalez).

---
