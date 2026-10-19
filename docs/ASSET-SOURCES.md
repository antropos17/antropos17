# Profile asset sources

## Studio identity

The mastheads, Esc key mark, buttons and small project marks in `assets/identity/`
are original SVG drawings for this profile. The masthead combines a sans-serif
Escape wordmark with an italic Studio wordmark and an open Esc key outline.
It uses a separate narrow composition rather than shrinking a wide banner.
Light and dark variants follow GitHub's picture-element theme support. Buttons
are 124×32, project marks 24×24; project descriptions remain native text.

## Monochrome toolchain strip

`assets/identity/toolchain-light.svg` and `toolchain-dark.svg` contain original
upstream JavaScript, TypeScript, React, Node.js, Electron and Git silhouettes.
They identify tools found in public projects, not proficiency levels or brand
endorsements. Both files are self-contained, transparent 256×24 SVGs with no
background, border, decorative tiles, embedded images or external references.
Each upstream 24×24 path is unchanged. Translation positions the six marks;
the only visual change is a shared gray fill: `59636e` for light mode and
`9da9b4` for dark mode. The strip starts at x=0 with no canvas margin.

All six path definitions were obtained from the official
[Simple Icons repository](https://github.com/simple-icons/simple-icons), pinned to
commit `4d29a35c954699b389a834aacc97dd6e7e74143c` on 2026-10-19:

| Mark       | Exact source                                                                                                                      | Upstream provenance and terms                                                                                                                                                                         |
| ---------- | --------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| JavaScript | [javascript.svg](https://github.com/simple-icons/simple-icons/blob/4d29a35c954699b389a834aacc97dd6e7e74143c/icons/javascript.svg) | [Christopher Williams' logo.js](https://github.com/voodootikigod/logo.js/tree/1544bdeed6d618a6cfe4f0650d04ab8d9cfa76d9); MIT notice below                                                             |
| TypeScript | [typescript.svg](https://github.com/simple-icons/simple-icons/blob/4d29a35c954699b389a834aacc97dd6e7e74143c/icons/typescript.svg) | [Official branding](https://www.typescriptlang.org/branding/), including the single-color cutout variant                                                                                              |
| React      | [react.svg](https://github.com/simple-icons/simple-icons/blob/4d29a35c954699b389a834aacc97dd6e7e74143c/icons/react.svg)           | [Upstream React fixture logo](https://github.com/facebook/create-react-app/blob/282c03f9525fdf8061ffa1ec50dce89296d916bd/test/fixtures/relative-paths/src/logo.svg)                                   |
| Node.js    | [nodedotjs.svg](https://github.com/simple-icons/simple-icons/blob/4d29a35c954699b389a834aacc97dd6e7e74143c/icons/nodedotjs.svg)   | [Official branding](https://nodejs.org/en/about/branding); OpenJS Foundation marks remain subject to its trademark policy                                                                             |
| Electron   | [electron.svg](https://github.com/simple-icons/simple-icons/blob/4d29a35c954699b389a834aacc97dd6e7e74143c/icons/electron.svg)     | [Electron project](https://www.electronjs.org), as recorded by Simple Icons                                                                                                                           |
| Git        | [git.svg](https://github.com/simple-icons/simple-icons/blob/4d29a35c954699b389a834aacc97dd6e7e74143c/icons/git.svg)               | Git logo by **Jason Long**, [CC BY 3.0 Unported](https://creativecommons.org/licenses/by/3.0/), from [Git's official logo page](https://git-scm.com/community/logos); recolored gray for these strips |

Simple Icons' collection is distributed under
[CC0-1.0](https://github.com/simple-icons/simple-icons/blob/4d29a35c954699b389a834aacc97dd6e7e74143c/LICENSE.md).
Its [disclaimer](https://github.com/simple-icons/simple-icons/blob/4d29a35c954699b389a834aacc97dd6e7e74143c/DISCLAIMER.md)
explains that individual marks can have separate licenses and trademark rules.
The collection's CC0 declaration does not replace those terms. The
[pinned icon metadata](https://github.com/simple-icons/simple-icons/blob/4d29a35c954699b389a834aacc97dd6e7e74143c/data/simple-icons.json)
records the sources and the separate JavaScript MIT and Git CC BY 3.0 licenses.
Other listed entries do not specify separate icon-license metadata; no additional
rights or blanket relicensing of their brands is claimed here.

C# is omitted because `csharp.svg` is unavailable at the pinned upstream revision.
Unity is omitted from the recolored strip because its
[official logo rules](https://unity.com/legal/branding-trademarks) prohibit color
changes and restrict promotional logo use. Their absence from this graphic does
not change the public projects' actual use of C# or Unity software.

## JavaScript logo notice

The original [logo.js license](https://github.com/voodootikigod/logo.js/blob/1544bdeed6d618a6cfe4f0650d04ab8d9cfa76d9/LICENSE)
is retained here:

```text
The MIT License (MIT)

Copyright (c) 2011 Christopher Williams <chris@iterativedesigns.com>
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:
The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.
THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
```
