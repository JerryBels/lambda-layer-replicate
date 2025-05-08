# AWS Replicate Layer
This AWS lambda layer contains a latest pre-built vanilla [replicate](https://www.npmjs.com/package/replicate) npm library, so that you could "just use" it in your lambda code:

```javascript
// CommonJS (default or using .cjs extension)
const Replicate = require("replicate");

// ESM (where `"module": true` in package.json or using .mjs extension)
import Replicate from "replicate";
// ...
```

It contains only necessary files to minimize its weight.

# Getting
You can import it into your AWS account throught the Lambda console or with the following command:
```shell
aws lambda publish-layer-version \
    --layer-name replicate \
    --description "Replicate layer" \
    --license-info "Apache License 2.0" \
    --zip-file fileb://dist/replicate-layer.zip \
    --compatible-runtimes nodejs14.x nodejs16.x nodejs18.x nodejs20.x \
    --compatible-architectures x86_64 arm64
```

# Building
Simply run (this will wipe your existing `node_modules/` directory):
```shell
npm ci --arch=x64 --platform=linux
```

Build will be performed automatically upon deps installation.
The resulted lambda layer zip file will be saved to `dist/` directory.

If building in a Linux environment like AWS, simply running `npm i` should do it.