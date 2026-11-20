# AdocFlow

<p align="center">
  <b>An ultra-lightweight AsciiDoc editor for Windows, where the syntax is something you pick rather than memorize.</b>
</p>

<p align="center">
  <a href="https://apps.microsoft.com/detail/9PMJLV750G27">
    <img src="https://get.microsoft.com/images/en-us%20dark.svg" width="200" alt="Get AdocFlow from the Microsoft Store" />
  </a>
</p>

AdocFlow puts AsciiDoc's own constructs behind a block editor. You write on a canvas of blocks, insert any AsciiDoc construct from a slash menu, and watch the compiled HTML update beside you as you type. The file on disk stays an ordinary `.adoc` that Asciidoctor, Antora, GitHub and every other AsciiDoc tool read as usual.

---

## What AdocFlow is

AsciiDoc is the format engineering teams reach for when Markdown runs out: a table of contents, admonitions, tables with merged cells, diagrams, math, cross references between documents, and the ability to assemble one document from many files. That richness has a price. The syntax is larger than Markdown's, and most people write it in a plain text editor with the reference open in another window.

AdocFlow removes that price without changing the format. What changes is how you write it: on a canvas of blocks, with a slash menu that offers exactly the constructs AsciiDoc has, and a live preview that shows the result the moment you type.

The blocks are AsciiDoc's, and they keep AsciiDoc's names. An admonition is an admonition, a sidebar is a sidebar, an include is an include. Nothing is renamed to look like another tool, so what you learn on the canvas is the format itself.

## Who it is for

- **Technical writers**: write reference manuals, guides and release notes in the format your publishing pipeline already consumes, with the comfort of a modern editor.
- **Developers**: keep documentation next to the code, in a text format that diffs and reviews cleanly, without stopping to look up how a table or a cross reference is spelled.
- **Teams new to AsciiDoc**: start writing on the first day. The slash menu shows what exists, the preview shows what it does, and the Source view is one keystroke away when you want to see the text behind a block.

## Two editors, one document

The toolbar separates *what you are editing in* from *how it is laid out*, so either editor pairs with the preview.

| View | What it is |
| :--- | :--- |
| **Canvas** | A full block editor. Type `/` to insert any AsciiDoc construct at the cursor, drag blocks to reorder them, and switch an admonition's kind or a table's frame from a control on the block itself. Attributes the canvas cannot draw are one click away in the block's Options field, and come back on save without losing a character. |
| **Source** | A raw AsciiDoc editor built on Monaco, with a grammar written for AsciiDoc: headings, fences, tables, attribute entries, anchors, macros and inline formatting each get their own color. Completions know the syntax and the workspace, offering the files an `include::` or `xref:` can point at and the attributes the document defines. |
| **Preview** | The HTML Asciidoctor produces, rendered live with the table of contents, section numbers, admonition icons, syntax highlighting, math and every diagram type. Cross references to other documents open those documents in a tab at the anchor named. |
| **Split** | Whichever editor is on screen, side by side with the preview and scroll-synchronized. |

`` Ctrl+` `` switches between the canvas and the source view without leaving the current layout. Whichever you use, the file is the same, and the acceptance test for every save is that Asciidoctor emits the same HTML before and after a round trip.

## What the canvas draws

The canvas has a dedicated block for the constructs that make AsciiDoc worth using.

- **Admonitions**: NOTE, TIP, IMPORTANT, WARNING and CAUTION, switchable on the spot.
- **Inline formatting**: bold, italic and monospace, plus the marks AsciiDoc adds to them (highlight, superscript, subscript and role spans such as `[.lead]#text#`) from the formatting toolbar. Footnotes go in from the `/` menu and open a field to write the note in.
- **Lists**: a description list, `Term:: definition`, is in the `/` menu, because the colons are the part nobody guesses. Bullets, numbers and checkboxes are made by typing their marker.
- **Tables**: a visual cell editor for `|===` tables that preserves merged cells (`2+|`, `.2+|`) and alignment, with a toolbar for frame, grid, stripes, header row and header column.
- **Diagrams**: Mermaid rendered in the browser with no network, and eighteen more kinds (PlantUML, Graphviz, D2, C4, BPMN, ERD, Excalidraw and others) rendered through a Kroki server with nothing extra to install.
- **Math**: `[stem]` and `[latexmath]` blocks and inline formulas, drawn by MathJax.
- **Code**: source blocks with a language picker, plus literal, listing and passthrough blocks.
- **Structure**: sidebars, example blocks, collapsible blocks, quotes with attribution and citation, verse, open blocks and abstracts.
- **Images and media**: `image::` drawn on the canvas at an editable width, plus video and audio.
- **References**: anchors as chips, and a cross-reference picker that lists this document's headings first and then every anchor in the workspace.
- **Includes**: `include::` shown in place, with its target one click away in a new tab.
- **Conditionals**: `ifdef::name[]` … `endif::[]` from the `/` menu. One source, several audiences.
- **Document properties**: `:toc:`, `:icons:`, `:author:`, `:sectnums:` and custom attributes edited in a panel instead of by hand, and a stylesheet picked from the workspace's `stylesheets/` folder, written as `:stylesdir:` and `:stylesheet:`.

Constructs the canvas has no block for are never mangled. They are kept verbatim as source, shown as such, and editable in the Source view. The ones that would otherwise read as ordinary prose say what they are instead: a comment, a conditional directive and a page break each carry a small label, because each is a line that changes the document without appearing in it.

## Finding your way around a workspace

Open a folder and it becomes the workspace: a file tree, tabs for open documents, and a session that comes back on the next launch. Past a screenful of documents, three tools take over, all built on one indexing pass.

- **Quick switcher (`Ctrl+O`)**: jump to any file by typing part of its name. Matching is fuzzy, so `chone` finds `chapters/one.adoc`.
- **Workspace search (`Ctrl+Shift+F`)**: search every document's text with operators: exclude a word, match a regular expression, filter by path or extension, search only under a heading, or require every term on one line.
- **Links panel (`Ctrl+Shift+B`)**: AsciiDoc references only run forwards. The panel inverts them, listing every `include::`, `xref:` and `link:` that points at the current document, every target it points at (with missing ones struck through), and documents that mention it without linking.

## Sharing the result

- **HTML export**: one self-contained file, with the stylesheet inlined, images as data URLs and diagrams as SVG. It opens anywhere with no AdocFlow and no network.
- **PDF export**: the same document printed straight through WebView2, with no print dialog and none of the app's own interface in the file.

The preview's stylesheet (Asciidoctor default, GitHub or Compact), its light or dark theme, the code highlighting theme and any custom CSS of your own are chosen in Settings and carried into both exports. A document that names its own stylesheet with `:stylesheet:` and `:stylesdir:` is shown with that sheet, exactly as `asciidoctor` would write it. `:icons: font` draws from Font Awesome, bundled with the app, so admonition icons and `icon:` macros look as they do on a published page.

## Light, private, yours

- **Roughly 10 MB on disk and about 50 MB in memory.** AdocFlow runs on the WebView2 engine already built into Windows instead of shipping a browser of its own.
- **Nothing leaves your machine unless you ask.** There are no accounts and no analytics. The app reaches the network for two things only: rendering non-Mermaid diagrams through the Kroki server you configure, and, in installer builds, checking for updates. Point the Kroki setting at a server inside your network and diagram source never leaves it.
- **Nothing is read outside the workspace.** Every file the app touches, whether a document, an image or an include target, is checked against the open folder by a single guard, and the preview renders in a sandboxed frame that cannot reach the disk or the network on its own.
- **Your files stay plain text.** There is no proprietary project format and no lock-in. Close AdocFlow and the `.adoc` files are exactly where you left them, readable by any tool.

Read the full [privacy policy](https://jaehyuk-codes.github.io/AdocFlowPublic/privacy.html).

## Requirements and availability

| | |
| :--- | :--- |
| **Operating system** | Windows 10 version 1809 or later, or Windows 11 |
| **Architecture** | x64 |
| **Runtime** | Microsoft Edge WebView2 (included with Windows 11, installed on demand on Windows 10) |
| **Network** | Not required, except for Kroki diagrams and update checks |

AdocFlow is distributed through the [Microsoft Store](https://apps.microsoft.com/detail/9PMJLV750G27) and as a signed Windows installer. The Store edition is kept up to date by the Store; the installer edition checks for signed updates and asks before downloading or applying one.

## Keyboard shortcuts

The full list, view by view, is in the app: the keyboard button at the bottom of the activity bar, or `Ctrl+Shift+/`. The main ones:

| Shortcut | Action |
| :--- | :--- |
| `Ctrl+S` | Save the active document |
| `Ctrl+W` | Close the active tab |
| `Ctrl+O` | Quick switcher |
| `Ctrl+Shift+F` | Workspace search |
| `Ctrl+Shift+B` | Links panel |
| `Ctrl+Shift+E` | Show only the open document's folder in the file tree, and back |
| `` Ctrl+` `` | Switch between canvas and source |
| `Alt+←` / `Alt+→` | Back / forward through the documents |
| `Ctrl+Enter` / `Ctrl+Shift+Enter` | Insert a block below / above (canvas) |
| `Alt+↑` / `Alt+↓` | Move the current block (canvas) or line (source) up / down |
| `Shift+Enter` | Line break inside a paragraph, written as a trailing ` +` (canvas) |
| `Ctrl+B` / `Ctrl+I` / `Ctrl+Shift+C` | Bold / italic / code around the selection (source) |
| `Ctrl+K` | Link around the selection (source) |
| `Ctrl+/` | Toggle a `//` comment (source) |
| `Ctrl+Shift+J` | Scroll the preview to the caret |
| `Ctrl+=` / `Ctrl+-` / `Ctrl+0` | Zoom the preview |
| `Ctrl+Shift+/` | All shortcuts |

## Feedback

Bug reports and feature requests are welcome in this repository's [issues](https://github.com/jaehyuk-codes/AdocFlowPublic/issues).
