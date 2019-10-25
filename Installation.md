Ketting can be used in a few different ways

Node.js
-------

If you intend to use Ketting in node.js, all you need to do is run:

    npm i ketting

After running this, you can start using using it like this:

```javascript
const { Ketting } = require('ketting');
```

In typescript, you can use it as follows:

```typescript
import { Ketting } from 'ketting';
```

Webpack builds
--------------

If you are using Ketting in a browser, it's typical for build front-end
applications with Webpack.

If you have a working Webpack setup, the instructions for installing and using
Ketting are identical to Node.js.

Webpack will automatically grab a Ketting build optimized for browsers, which
is much smaller than a regular webpack build. The build currently sits at 33KB.

Manually adding Ketting via Script tags
---------------------------------------

Every ketting release comes with a minified javascript file. The easiest way
to obtain it is with the following command:

    npm pack ketting

This will download a file like `ketting-5.0.0.tgz` in your current directory.
You can unpack the file with:

    tar xfvz ketting*.tgz

After this you can find the minified file in package/browser/ketting.min.js

Place this file wherever you usually have your javascript files and include it
with:

```html
<script src="some/path/ketting.min.js"></script>
```

After this, `Ketting` will be availabe as a global object and you can use it
with:

```javascript
const ketting = new Ketting('https://api.example.org');
```

Next steps
----------

Read [Getting started](Getting started).
