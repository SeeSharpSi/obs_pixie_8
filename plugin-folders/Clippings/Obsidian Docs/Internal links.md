---
title: "Internal links"
source: "https://obsidian.md/help/links"
author:
published:
created: 2026-05-21
description: "Internal links - Obsidian Help"
tags:
  - "clippings"
---
Learn how to link to notes, attachments, and other files from your notes, using *internal links*. By linking notes, you can create a network of knowledge.

Obsidian can automatically update internal links in your vault when you rename a file. If you want to be prompted instead, you can disable it under:

## Supported formats for internal links

Obsidian supports the following link formats:

- Wikilink: `[[Three laws of motion]]` or `[[Three laws of motion.md]]`
- Markdown: `[Three laws of motion](Three%20laws%20of%20motion)` or `[Three laws of motion](Three%20laws%20of%20motion.md)`

The examples above are equivalent, and they appear the same way in the editor and links to the same note.

> [!note] Note
> When using the Markdown format, make sure to [URL encode](https://en.wikipedia.org/wiki/Percent-encoding) the link destination. For example, blank spaces become `%20`.

By default, due to its more compact format, Obsidian generates links using the Wikilink format. If interoperability is important to you, you can disable Wikilinks and use Markdown links instead.

To use the Markdown format:

1. Open **[Settings](https://obsidian.md/help/settings)**.
2. Under **Files and Links**, disable **Use \[\[Wikilinks\]\]**.

Even if you disable the Wikilink format, you can still autocomplete links by typing two square brackets `[[`. When you select one of the suggested files, Obsidian instead generates a Markdown link.

> [!note] Invalid characters
> A string which contains the following characters may not work as a link: `# | ^ : %% [[ ]]`.
> 
> We recommend avoiding using those characters and practicing [safe filename practices](https://stackoverflow.com/questions/1976007/what-characters-are-forbidden-in-windows-and-linux-directory-names).

## Link to a file

To create a link while in Editing view, use either of the following ways:

- Type `[[` in the editor and then select the file you want to create a link to.
- Select text in the editor and then type `[[`.
- Open the [Command palette](https://obsidian.md/help/plugins/command-palette) and then select Add internal link.

> [!info] Info
> Autocomplete functionality switches to a simpler result algorithm when the vault reaches 10,000 items to maintain optimal application performance.

While you can link to any of the [Accepted file formats](https://obsidian.md/help/file-formats), links to file formats other than Markdown needs to include a file extension, such as `[[Figure 1.png]]`.

> [!tip] Prefixing an internal link with an exclamation mark (!) allows you to embed the linked content. For more details, see Embed Files.
> 

> [!info] Excluded files
> Files matching your [Excluded files](https://obsidian.md/help/settings#Excluded%20files) patterns are deprioritized in link suggestions when creating internal links.

## Link to a heading in a note

You can link to specific headings in notes, also known as *anchor links*.

**Linking to a heading within the same note**

To link to a heading within the same note, type `[[#` to get a list of headings within the note to link to.

For example, `[[#Preview a linked file]]` will create a link to [Preview a linked file](https://obsidian.md/help/links#Preview%20a%20linked%20file).

**Linking to a heading in another note**

To link to a heading in another note, add a hash (`#`) at the end of the link destination, followed by the heading text.

For example, `[[About Obsidian#Links are first-class citizens]]` will create a link to [About Obsidian > Links are first-class citizens](https://obsidian.md/help/obsidian#Links%20are%20first-class%20citizens).

**Linking to subheadings**

You can add multiple hash symbols for each subheading.

For example, `[[Help and support#Questions and advice#Report bugs and request features]]` will create a link to [Help and support > Questions and advice > Report bugs and request features](https://obsidian.md/help/resources#Questions%20and%20advice#Report%20bugs%20and%20request%20features).

**Searching for headers across the vault**

To search for headers across the entire vault, use the `[[## header]]` syntax.

For example, `[[##` will search generically across the vault, whereas `[[## team]]` will search for all headers that contain the word *team*.

> [!info]- Screenshot of searching for a heading link
> ![[internal-links-header.png|internal-links-header.png > interface]]
> 
> internal-links-header.png > interface

## Link to a block in a note

A block is a unit of text in your note, such as a paragraph, block quote, or list item.

You can link to a block by adding `#^` at the end of your link destination, followed by a unique block identifier. For example: `[[2023-01-01#^37066d]]`. Fortunately, you don't need to manually find the identifier—when you type the caret (`^`), a list of suggestions will appear, allowing you to select the correct block.

For *simple paragraphs*, place a blank space followed by a caret `^` and the block identifier at the end of the line:

```md
The quick purple gem dashes through the paragraph with blazing speed. Pen in hand and a paperclip in the other, Gemmy works toward her goal of making the world of note-taking a happier place. ^37066d
```

For *structured blocks* (lists, quotations, callouts, tables), the block identifier should be on a separate line, with a blank line before and after:

```md
> The quick purple gem dashes through the paragraph with blazing speed. Pen in hand and a paperclip in the other, Gemmy works toward her goal of making the world of note-taking a happier place.

^37066f

This is the tale of Gemmy, the Unhelpful assistant.
```

For *specific lines within a list*, the block identifier can be placed directly on a bullet point:

```
- Gemmy
    $$Paperclip / Pen$$ 
    ^37006f
- Unhelpful assistant
```

> [!warning] We do not support links to specific parts of quotations, callouts, and tables.
> 

**Searching for blocks across the vault**

You can also search for blocks to link to from across your vault using the `[[^^block]]` syntax. However, more items qualify as blocks compared to [heading links](https://obsidian.md/help/links#Link%20to%20a%20heading%20in%20a%20note), so this list will be much longer.

> [!info]- Screenshot of searching for a block link
> ![[link-block-heading.png|link-block-heading.png > interface]]
> 
> link-block-heading.png > interface

You can also create human-readable block identifiers by adding a blank space followed by a caret (`^`) and the identifier. Block identifiers can only consist of Latin letters, numbers, and dashes.

For example, add `^quote-of-the-day` at the end of a block:

```md
"You do not rise to the level of your goals. You fall to the level of your systems." by James Clear ^quote-of-the-day
```

Now you can link to the block by typing `[[2023-01-01#^quote-of-the-day]]`.

> [!warning] Interoperability
> Block references are specific to Obsidian and not part of the standard Markdown format. Links containing block references won't work outside of Obsidian.

## Change the link display text

By default, Obsidian will show the link text as it appears. For example:

- `[[Example]]` displays as [Example](https://obsidian.md/help/Example)
- `[[Example#Details]]` displays as [Example > Details](https://obsidian.md/help/Example#Details)

You can change how a link is displayed by customizing its link text:

**Wikilink format**:  
Use a vertical bar (`|`) to change the display text.

- `[[Example|Custom name]]` appears as [Custom name](https://obsidian.md/help/Example)
- `[[Example#Details|Section name]]` appears as [Section name](https://obsidian.md/help/Example#Details)

**Markdown format**:  
Use `[Display text](Link URL)` to customize how the link appears.

- `[Custom name](Example.md)` appears as [Custom name](https://obsidian.md/help/Example)
- `[Section name](Example.md#Details)` appears as [Section name](https://obsidian.md/help/Example#Details)

This method is helpful for one-off situations where you want to change how a link looks in a specific context. If you want to set up an alternate link name that you can reuse throughout your vault, consider using an [alias](https://obsidian.md/help/aliases) instead.

For example, if you regularly refer to `[[Three laws of motion]]` as `[[The 3 laws]]`, adding "3 laws" as an alias lets you type just that — no need to add custom display text each time.

> [!tip] Tip
> Use [link display text](https://obsidian.md/help/links#Change%20the%20link%20display%20text) when you want to customize how a link looks *in a specific place*.
> 
> Use [aliases](https://obsidian.md/help/aliases) when you want to refer to the same note using *different names* throughout your vault.

## Preview a linked file

> [!note] Note
> To preview linked files, you first need to enable [Page preview](https://obsidian.md/help/plugins/page-preview).

To preview a linked file, hover over an internal link. While in editing mode, press `Ctrl` (or `Cmd` on macOS) while hovering the cursor over the link. A preview of the file content appears next to the cursor.