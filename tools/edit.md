# edit

Edit a file by replacing an exact text match with new text. The oldText must match exactly (including whitespace).

## Parameters

| Name | Type | Description | Required |
|---|---|---|---|
| `filePath` | `string` | The path of the file to edit | `true` |
| `oldText` | `string` | The exact text to find and replace | `true` |
| `newText` | `string` | The new text to replace the old text with | `true` |

## Implementation

```javascript
const fs = require('fs').promises;

const editFile = async ({ filePath, oldText, newText }) => {
    try {
        const content = await fs.readFile(filePath, 'utf-8');
        if (!content.includes(oldText)) {
            return `Error: oldText not found in ${filePath}`;
        }
        const newContent = content.replace(oldText, newText);
        await fs.writeFile(filePath, newContent, 'utf-8');
        return `Successfully edited ${filePath}`;
    } catch (error) {
        return `Error editing file: ${error.message}`;
    }
};

module.exports = { execute: editFile };
```