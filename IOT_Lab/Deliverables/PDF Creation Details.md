All images embedded into the PDFs are listed, organized, and labeled in PDF Images.zip. Saved as pngs. 

**Program:**
App - Obsidian v1.5.12
Theme - LaTeX by Ben Finch, v1.1.3, [GitHub Repository](https://github.com/benf2004/Obsidian-LaTeX-Theme)

**Plugins** (none of which are required for formatting or editing):
* Pandoc Plugin by Oliver Balfour, v0.4.1, [GitHub Repository](https://github.com/OliverBalfour/obsidian-pandoc)
	* Exporting tool for PDF
* Remotely Save by fyears, v0.4.20, [GitHub Repository](https://github.com/remotely-save/remotely-save)
	* Syncs vaults between devices

**CSS Snippets:**
I used two CSS snippets when making these documents. These are short CSS files that you can use in Obsidian to format things. I'll copy the code here but the CSS source files will also be provided in a separate folder.

imageBorderSnippet - This snippet adds a 2 pixel solid light gray border to all embedded images.
```
.markdown-source-view.mod-cm6 .internal-embed > img, .markdown-preview-view .internal-embed > img {
    border: 2px solid lightgray;
}
```

removeSpaceBeforeList - This snippet removes the built in space padding in between a bullet point list and any text above it.
```
.markdown-rendered ul, .markdown-rendered ol {
    margin-block-start: -15px;
    margin-block-end: 0px;
}
```