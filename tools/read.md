# read

Read a file and output its contents as a string.

## Parameters

| Name | Type | Description | Required |
|---|---|---|---|
| `filePath` | `string` | The path of the file to read | `true` |

## Implementation

```javascript
const fs = require('fs').promises;

const readFile = async ({ filePath }) => {
    try {
        const content = await fs.readFile(filePath, 'utf-8');
        return content;
    } catch (error) {
        return `Error reading file: ${error.message}`;
    }
};

module.exports = { execute: readFile };
```
