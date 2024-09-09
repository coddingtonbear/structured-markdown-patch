# Markdown Patch

Markdown Patch is a patch format and tool that allows you to make
systematic changes to Markdown documents by allowing you to
alter the content of a Markdown document relative to elements
of that document's structure like headings or block references.

Have you ever needed to set up a script for modifying a markdown document and found yourself using arcane tools like `sed` before giving up entirely?  This tool might be for you!

See docs at https://coddingtonbear.github.io/markdown-patch/.

## Use as a library

```ts
import {PatchInstruction, applyPatch} from "markdown-patch"

const myDocument = `
# Noise Floor

- Some content

# Discoveries

# Events

- Checked out of my hotel
- Caught the flight home

`

const instruction: PatchInstruction {
    operation: "append",
    targetType: "heading",
    target: "Discoveries",
    content: "\n## My discovery\nI discovered a thing\n",
}

console.log(
    applyPatch(myDocument, instruction)
)
```

and you'll see the output:

```markdown
# Noise Floor

- Some content

# Discoveries

## My discovery
I discovered a thing

# Events

- Checked out of my hotel
- Caught the flight home

```
