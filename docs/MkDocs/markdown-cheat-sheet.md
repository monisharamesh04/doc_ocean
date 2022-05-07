# Markdown Cheat Sheet

Thanks for visiting [The Markdown Guide](https://www.markdownguide.org)!

This Markdown cheat sheet provides a quick overview of all the Markdown syntax elements. It can’t cover every edge case, so if you need more information about any of these elements, refer to the reference guides for [basic syntax](https://www.markdownguide.org/basic-syntax) and [extended syntax](https://www.markdownguide.org/extended-syntax).

## Basic Syntax

These are the elements outlined in John Gruber’s original design document. All Markdown applications support these elements.

### Heading

```md
# H1
## H2
### H3
```

### Bold

```md
**bold text**
```

### Italic

```md
*italicized text*
```

### Blockquote

```md
> blockquote
```

### Ordered List

```md
1. First item
2. Second item
3. Third item
```

### Unordered List

```md
- First item
- Second item
- Third item
```

### Code

``` md
`code`
```

### Horizontal Rule

```md
---
```

### Link

```md
[Markdown Guide](https://www.markdownguide.org)
```

### Image

```md
![alt text](https://www.markdownguide.org/assets/images/tux.png)
```

## Extended Syntax

These elements extend the basic syntax by adding additional features. Not all Markdown applications support these elements.

### Table

```md
| Syntax | Description |
| ----------- | ----------- |
| Header | Title |
| Paragraph | Text |
```

### Fenced Code Block

```md
{
  "firstName": "John",
  "lastName": "Smith",
  "age": 25
}
```

### Footnote

```md
Here's a sentence with a footnote. [^1]

[^1]: This is the footnote.
```

### Heading ID

```md
### My Great Heading ```{#custom-id}```
```

### Definition List

```md
term
: definition
```

### Strikethrough

```
~~The world is flat.~~
```


### Task List

```
- [x] Write the press release
- [ ] Update the website
- [ ] Contact the media
```

### Emoji

That is so funny! ```:joy:```

(See also [Copying and Pasting Emoji](https://www.markdownguide.org/extended-syntax/#copying-and-pasting-emoji))

### Highlight

I need to highlight these ``` ==very important words== ```.

OR

I need to highlight these ``` <main> very important words== <mark> ```.

### Subscript

```
H~2~O
```

### Superscript

```
X^2^
```