# write

Write content to a file. Creates the file if it does not exist, overwrites if it does.

## Parameters

| Name | Type | Description | Required |
|------|------|-------------|----------|
| `filePath` | `string` | The path of the file to write to | `true` |
| `content` | `string` | The content to write to the file | `true` |

## Implementation

```javascript
const fs = require('fs').promises;

const write = async ({ filePath, content }) => {
    try {
        await fs.writeFile(filePath, content, 'utf-8');
        return `Successfully wrote to ${filePath}`;
    } catch (error) {
        return `Error writing file: ${error.message}`;
    }
};

module.exports = { execute: write };
```
