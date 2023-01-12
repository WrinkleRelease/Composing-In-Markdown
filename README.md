# Composing Fiction & Scripts with Markdown

Markdown files are simply plain text files with flags that a Markdown viewer recognizes as format commands. That's it. Nothing fancy. Being plain text, these files are future-proof and can always be opened by any reader capable of reading plain text, such as Notepad, Notepad++, VIM, etc. Markdown files use the extension `.md` or `.markdown`. 

I've looked at a lot of different Markdown editors (and there are a lot out there, even for fiction writers), but all the truly great ones cost money. The solution presented here gets the job done on the cheap while leaving you immune to any format wars.

You can read more about [Markdown], including a style guide, at the linked website.

## 1. Getting Set Up

### | 1.1.  Installing `winget`

`winget` is a command line package manager for CMD or PowerShell, much like `apt-get` in Linux.

This step is optional, but it's a nice tool that makes some tasks, including application installations, much more convenient.

`winget` comes with Windows 11. If you are on Windows 10, you'll need to install the [App Installer] from the Microsoft Store first.

<br/>

### | 1.2. Installing Fonts

[This link] will give you the pandoc templates and fonts you need. Included are `Courier Prime` and `iA Writer Duo`. Install them both. We'll get to the pandoc template files in [1.4.1](#pandoc).

<br/>

### | 1.3. Visual Studio Code

Install Visual Studio Code 
- With `winget`
    - Hit the Windows key on the keyboard, type `cmd` and open a CMD window
    -  In CMD, type `winget install --id Microsoft.VisualStudioCode -s winget`
    - Hit `Enter`
- Or [download and install][1]

Once inside of VS, go to `View > Extensions`. Search for, and install, the extensions below. I've also included some color themes I find easier to write with:

- Better Fountain
- Markdown Fiction Writing
- Markdown Preview Enhanced
- Spell Right
- Gruvbox Theme
- Gruvbox Material Icon Theme

Lastly, we need to change some information in VS Code's `settings.json` file. 
1.  Open `Settings` by clicking the gear icon in the bottom left of VS Code.
 2. Once inside `Settings` you will see a small icon in the upper right of that window. It looks like a document with a an arrow curving around it. Click that. 
 3. That should open the `settings.json` file. The code below needs to replace what is currently in your file. Highlight and delete what is in your `.json` file. Next, copy the entirety of the code below (including the `{` and `}` at the beginning and end) and paste in. Save by hitting `CTRL-S`. You might need to restart VS Code.

```json
{
    "[markdown]": {
    "editor.fontFamily": "\"IA Writer Duo S\", monospace",
    "editor.fontLigatures": true,
    "editor.fontSize": 14,
    "editor.lineHeight": 26,          
    "editor.wordWrap": "wordWrapColumn",
    "editor.wordWrapColumn": 64,        
    "zenMode.centerLayout": true,
    "editor.lineNumbers": "off",
    "editor.quickSuggestions": false,
    "markdown.PreviewFrontMatter": "show"
    },

    "editor.fontFamily": "Consolas, 'Courier Prime', monospace",
    "workbench.iconTheme": "gruvbox-material-icon-theme",
    "markdown-preview-enhanced.frontMatterRenderingOption": "code block",
    "markdown-fiction-writer.metadata.categories.summaryEnabled": true,
    "markdown-fiction-writer.edit.disableKeybindings": false,
    "markdown-fiction-writer.edit.easyParagraphCreation": "Shift+Enter",
    "markdown-preview-enhanced.enableTypographer": true,
    "workbench.colorTheme": "Gruvbox Dark Hard",
    "editor.minimap.enabled": false,
    "breadcrumbs.enabled": false,
    "editor.cursorStyle": "block",
    

}
```
<br/>

### | 1.4. Final Installations

<a id="pandoc"></a>
#### | | 1.4.1.  Install pandoc

Pandoc is what converts our MD documents into DOCX or PDF. It uses templates to format the MD into manuscript format.
- Install using `winget`
    - In CMD, type `winget install --name Pandoc -e -s winget`
- Or [download and install][2]

 Once installed, open Windows Explorer and traverse to `C:\users\[username]\AppData\Roaming\` and create the folders `\pandoc\templates` if they do not exist.
- Place `reference.docx` and `references.odt` inside of `\Roaming\pandoc`. 
- Place `story.latex` inside `\Romaing\pandoc\templates\`
  
#### | | 1.4.2. Install MikTeX

MiKTeX is a LaTeX text setting system for Windows. It runs the modules pandoc needs.

- Install using `winget`
    - In CMD, type `winget install --name MiKTeX -e -s winget`
- Or [download and install][3]

 Once installed, run MiKTeX Console (you can find it in the Start Menu), check for updates and install them.

<br/> 

## 2. Using Visual Studio Code

1. You can open a *file* or a *folder*. The folder option is nice since all the documents you have in it will be available. This is helpful if you're writing many short stories or a book with chapters. When a folder is open it is called a *workspace*. You can even save a workspace out as a file for the future.

<br/>

2. You an always preview the document you are currently working on by hitting `CTRL-K V`. Keep in mind, this notation means you hit `CTRL-K`, let go, then hit `V` (if the notation reads `CTRL+K+V` or `CTRL-K-V` then you hit them all together).

<br/>

3. Go to Zen Mode by hitting `CTRL-K Z`.

<br/>

4. `Markdown Fiction Writing` features a Writing Mode. It dims all your text except the paragraph you are currently working on. You toggle it on and off using the lightning bolt icon on the bottom bar of VSC.

<br/>

### | 2.1. Writing & Printing a Script

`Better Fountain` is very easy to use for script writing. When starting a file, simply choose the language as `Fountain`. This extension even prints to PDF from inside VSC in the proper format. Following the syntax examples on their website will give you a good start. 

Make sure to give your script the proper `Front Matter`. This is information that exists at the very top of the document and provides metadata. The printing engine will use this for title pages, headers, etc. Here example `Front Matter` for `Fountain`:
```yaml
Title: 
    _BIG PROJECT_
    Episode 1
    _"Say Stuff"_
Credit: Written by
Author: Jack Lance & Ken Hark
Revision: 
    DRAFT #5
    2/28/2022
BL: 
    (555) 222-2222
    444 Gunsmoke Rd..
    City, ST 00000
====
```
In `Fountain` syntax, the `===` immediately following the relevant text indicates the end of the `Front Matter` and beginning of the document proper.

<br/>

### | 2.2. Writing & Printing Manuscripts

Writing prose in Markdown is easy. There is very little we need to format as all of that is done upon export. the `Front Matter` for Markdown is slightly different. Below is an example. Notice that it begins and ends with `---`.

```yaml
---
title: AWESOME TITLE
author: Jack Lance
runningtitle: AWESOME
forename: Jack
surname: Lance
date: 2/28/2022
wordcount: about 4,000
street: 444 Gunsmoke Rd.
location: City, ST 00000
phone: (555) 222-2222
email: example@email.com
revision: Fourth Draft
output: 
    pdf_document: 
        path: /Stories/Shorts/Awesome Title/at-test.pdf
        pdf_engine: xelatex
        template: story.latex
---
```
Some of the information here is for `pandoc` to use upon PDF render and some is for me (such as revision number). 

<br/>

#### | | 2.2.1.  Printing to PDF
The `Markdown Preview Enhanced` extension allows us to call `pandoc` without having to use the command line. Right clicking on the preview window shows output options. We'll be using the `Pandoc` option. We tell `Pandoc` what type of document to make in the `Front Matter` of our MD file.

Since you put `story.latex` in the `\templates` folder, we can tell `Pandoc` to use that as our PDF reference file. It is set up to use all the information in our `Front Matter` and inject it into the document where it needs to be. So, to print to a PDF we put this in our `Front Matter`
```yaml
output: 
  pdf_document:
    pdf_engine: xeletex
    template: story.latex
```
`Pandoc` will output a PDF using that template to the same directory as your Workspace. In my case, I wanted the PDF to end up in the same directory as the story file itself, so I added a `path` argument to the `Front Matter`. When you first run a PDF print job, MiKTeX will download and install all the packages it needs, so be prepared for it to pop up a lot of windows needing your input.

This solution works nicely, but it has one small hiccup: I sometimes get widows and orphans upon export. 

The only way I have found to solve this, if it happens, is to export to a DOCX file and *then* make the PDF from that inside of Word.

<br/>

#### | | 2.2.2. Printing to DOCX
Remember the `reference.docx` file you put inside of the `Roaming\pandoc` folder? Open it and change the header information on the title page to your information.

Change your `output` flag in the `Front Matter` to the following:
```yaml
output: word_document
```
Now, when you call `Pandoc` from the `Markdown Preview Enhanced` extension, it will generate a DOCX file. Go into the file, correct your word count, make sure everything is in `Courier Prime`, check the formatting situation, and change what needs changing. Output to PDF and you're done.

<br/>

## 3. Links
- [Better Fountain] features
- Fountain screenplay [syntax guide]
- [Markdown Fiction Writing] guide

[Markdown]: https://www.markdownguide.org/
[App Installer]: https://www.microsoft.com/en-us/p/app-installer/9nblggh4nns1?activetab=pivot:overviewtab
[This link]: https://drive.google.com/drive/folders/1Wu5dsovAlW5dyiiXrWgIjjYLrN1lncJ9?usp=sharing
[1]: https://code.visualstudio.com
[Better Fountain]: https://marketplace.visualstudio.com/items?itemName=piersdeseilligny.betterfountain
[syntax guide]: https://www.fountain.io/syntax
[Markdown Fiction Writing]: https://zoctarine.github.io/vscode-fiction-writer/
[2]: https://pandoc.org/installing.html
[3]: https://miktex.org/download
