#### Usage

JS-Confuser exposes a simple API that allows you to obfuscate your code with just a few lines of code.

##### Example

The provided code example will obfuscate the file `input.js` and write the output to a file named `output.js`.

---{header: "Example"}
import JSConfuser from "js-confuser";
import {readFileSync, writeFileSync} from "fs";

// Read input code
const sourceCode = readFileSync("input.js", "utf8");
const options = {
  target: "node",
  preset: "medium"
};

JSConfuser.obfuscate(sourceCode, options).then((obfuscated)=>{
  // Write output code
  writeFileSync("output.js", obfuscated);
}).catch(err=>{
  // Error occurred
  console.error(err);
});
---

##### API Methods

###### `JSConfuser.obfuscate(sourceCode, options)`

Obfuscates source code. Returns a [Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise) that resolves to a string of the obfuscated code.

| Parameter | Type | Description |
| `sourceCode` | `string` | The JavaScript code to be obfuscated. |
| `options` | `object` | The obfuscator settings. |

---

###### `JSConfuser.obfuscateAST(AST, options)`

Obfuscates an [ESTree](https://github.com/estree/estree) compliant AST. Returns a [Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise).

Note: Mutates the object.

| Parameter | Type | Description |
| `AST` | `object` | The [ESTree](https://github.com/estree/estree) compliant AST. This object will be mutated. |
| `options` |  `object`| The obfuscator settings. |

---

###### API Internals

###### `JSConfuser.presets`

The internal object where JS-Confuser presets are stored. The presets (`"low"`, `"medium"`, and `"high"`) can be accessed through: `JSConfuser.presets["high"]`
