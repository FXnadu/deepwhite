标题自动编号
已发布
·
2016年6月6日
更新
·
2022年3月1日
作者
·
typora.io
提示：要了解这些 CSS 代码片段应该放在哪里，请参阅“添加自定义 CSS”。

文章中的自动编号
此方法会自动为文章中的所有标题添加编号。

要实现这一点，请将以下内容添加到主题文件夹中的 `base.user.css` 或 `[theme].user.css` 文件中：

/** initialize css counter */
#write {
    counter-reset: h1
}

h1 {
    counter-reset: h2
}

h2 {
    counter-reset: h3
}

h3 {
    counter-reset: h4
}

h4 {
    counter-reset: h5
}

h5 {
    counter-reset: h6
}

/** put counter result into headings */
#write h1:before {
    counter-increment: h1;
    content: counter(h1) ". "
}

#write h2:before {
    counter-increment: h2;
    content: counter(h1) "." counter(h2) ". "
}

#write h3:before,
h3.md-focus.md-heading:before /** override the default style for focused headings */ {
    counter-increment: h3;
    content: counter(h1) "." counter(h2) "." counter(h3) ". "
}

#write h4:before,
h4.md-focus.md-heading:before {
    counter-increment: h4;
    content: counter(h1) "." counter(h2) "." counter(h3) "." counter(h4) ". "
}

#write h5:before,
h5.md-focus.md-heading:before {
    counter-increment: h5;
    content: counter(h1) "." counter(h2) "." counter(h3) "." counter(h4) "." counter(h5) ". "
}

#write h6:before,
h6.md-focus.md-heading:before {
    counter-increment: h6;
    content: counter(h1) "." counter(h2) "." counter(h3) "." counter(h4) "." counter(h5) "." counter(h6) ". "
}

/** override the default style for focused headings */
#write>h3.md-focus:before,
#write>h4.md-focus:before,
#write>h5.md-focus:before,
#write>h6.md-focus:before,
h3.md-focus:before,
h4.md-focus:before,
h5.md-focus:before,
h6.md-focus:before {
    color: inherit;
    border: inherit;
    border-radius: inherit;
    position: inherit;
    left:initial;
    float: none;
    top:initial;
    font-size: inherit;
    padding-left: inherit;
    padding-right: inherit;
    vertical-align: inherit;
    font-weight: inherit;
    line-height: inherit;
}
目录中的自动编号
如果您希望TOC实体自动编号显示，您可以尝试Typora 用户发布的http://pastebin.com/NYugSbXk 。

自动编号大纲面板
要在 Typora 的“大纲”面板中显示自动编号，请在首选项面板中禁用可折叠大纲面板，然后尝试https://pastebin.com/XmYgBbaz。




代码块样式/主题
已发布
·
2016年6月22日
更新
·
2022年4月27日
作者
·
typora.io
日本语 (ja)

提示：要了解这些 CSS 代码片段应该放在哪里，请参阅“添加自定义 CSS”。

Typora 使用 **CodeMirror** 实现代码块的语法高亮显示。Typora 中的代码块使用 CodeMirror 的 `cm-s-inner` 作为其主题类。

### 移植 CodeMirror 主题到 Typora

例如，要将 CodeMirror 主题（例如 `material.css`）移植到 Typora：

1. 复制并粘贴到主题文件夹 `base.user.css` 或其 `[theme].user.css` 下
2. 将它们的 CodeMirror 主题类名替换为 `cm-s-inner`，例如，将原始的 `.cm-s-material` 改为 `.cm-s-inner`
3. 在 CodeMirror 渲染之前，代码围栏具有类似这样的结构 `<pre class="md-fences"></pre>`。因此，请同时将字体、颜色和背景等基本样式应用到 `.md-fences` 选择器中

### 示例代码

最终的 CSS 代码如下：

```css

/** ported from https://codemirror.net/theme/material.css **/
/*

    Name:       material
    Author:     Michael Kaminsky (http://github.com/mkaminsky11)

    Original material color scheme by Mattia Astorino (https://github.com/equinusocio/material-theme)

*/

.cm-s-inner {
  background-color: #263238;
  color: rgba(233, 237, 237, 1);
}
.cm-s-inner .CodeMirror-gutters {
  background: #263238;
  color: rgb(83,127,126);
  border: none;
}
.cm-s-inner .CodeMirror-guttermarker, .cm-s-inner .CodeMirror-guttermarker-subtle, .cm-s-inner .CodeMirror-linenumber { color: rgb(83,127,126); }
.cm-s-inner .CodeMirror-cursor { border-left: 1px solid #f8f8f0; }
.cm-s-inner div.CodeMirror-selected { background: rgba(255, 255, 255, 0.15); }
.cm-s-inner.CodeMirror-focused div.CodeMirror-selected { background: rgba(255, 255, 255, 0.10); }
.cm-s-inner .CodeMirror-line::selection, .cm-s-inner .CodeMirror-line > span::selection, .cm-s-inner .CodeMirror-line > span > span::selection { background: rgba(255, 255, 255, 0.10); }
.cm-s-inner .CodeMirror-line::-moz-selection, .cm-s-inner .CodeMirror-line > span::-moz-selection, .cm-s-inner .CodeMirror-line > span > span::-moz-selection { background: rgba(255, 255, 255, 0.10); }

.cm-s-inner .CodeMirror-activeline-background { background: rgba(0, 0, 0, 0); }
.cm-s-inner .cm-keyword { color: rgba(199, 146, 234, 1); }
.cm-s-inner .cm-operator { color: rgba(233, 237, 237, 1); }
.cm-s-inner .cm-variable-2 { color: #80CBC4; }
.cm-s-inner .cm-variable-3 { color: #82B1FF; }
.cm-s-inner .cm-builtin { color: #DECB6B; }
.cm-s-inner .cm-atom { color: #F77669; }
.cm-s-inner .cm-number { color: #F77669; }
.cm-s-inner .cm-def { color: rgba(233, 237, 237, 1); }
.cm-s-inner .cm-string { color: #C3E88D; }
.cm-s-inner .cm-string-2 { color: #80CBC4; }
.cm-s-inner .cm-comment { color: #546E7A; }
.cm-s-inner .cm-variable { color: #82B1FF; }
.cm-s-inner .cm-tag { color: #80CBC4; }
.cm-s-inner .cm-meta { color: #80CBC4; }
.cm-s-inner .cm-attribute { color: #FFCB6B; }
.cm-s-inner .cm-property { color: #80CBAE; }
.cm-s-inner .cm-qualifier { color: #DECB6B; }
.cm-s-inner .cm-variable-3 { color: #DECB6B; }
.cm-s-inner .cm-tag { color: rgba(255, 83, 112, 1); }
.cm-s-inner .cm-error {
  color: rgba(255, 255, 255, 1.0);
  background-color: #EC5F67;
}
.cm-s-inner .CodeMirror-matchingbracket {
  text-decoration: underline;
  color: white !important;
}

/**apply to code fences with plan text**/
.md-fences {
  background-color: #263238;
  color: rgba(233, 237, 237, 1);
  border: none;
}

.md-fences .code-tooltip {
  background-color: #263238;
}
结果是：截图20160623_11

您可以参照上面的示例，编写自己的语法高亮 CSS 样式。

请注意，这cm-s-inner仅适用于代码块：它不会影响源代码模式下的 Markdown 语法。而且，并非所有 CSS 属性都会应用于源代码模式下的代码块。

自定义字体
已发布
·
2016年6月22日
更新
·
2022年4月27日
作者
·
typora.io
日本语 (ja)

提示：要了解这些 CSS 代码片段应该放在哪里，请参阅“添加自定义 CSS”。

更改字体
Typora 中的自定义字体是通过 CSS 设置的。例如，在 `base.user.css` 主题文件夹下添加以下内容：

```css
body {
  font-family: Courier;
}
```

这将覆盖当前主题中的字体设置，并应用系统字体 Courier。

### 使用网页字体

您也可以使用网页字体，例如：

```css

@import url(https://fonts.googleapis.com/css?family=Oxygen);

body {
 font-family: 'Oxygen', sans-serif; 
}
```

> **提示：** 为了加快字体加载速度或在无法访问互联网时使用，我们建议您下载字体并将其放在 Typora 的主题文件夹下。

### 使用本地字体文件

例如，如果您从 Google Fonts 下载 `woff2` 文件并将其放在 `[typora-theme-folder]/fonts` 目录下，则可以使用如下 CSS：

```css

/* latin */
@font-face {
  font-family: 'Oxygen';
  font-style: normal;
  font-weight: 400;
  src: local('Oxygen'), local('Oxygen-Regular'),url('./fonts/Oxygen400.woff2') format('woff2');
}

/* latin */
@font-face {
  font-family: 'Oxygen';
  font-style: normal;
  font-weight: 700;
  src: local('Oxygen Bold'), local('Oxygen-Bold'), url('./fonts/Oxygen700.woff2') format('woff2');
}

body {
 font-family: 'Oxygen', sans-serif; 
}
```

### 更改字体大小
更改字体大小的快捷方法是在系统偏好设置面板中进行设置。在 macOS 系统中，“字体大小”位于系统偏好设置面板的“通用”部分。在 Windows/Linux 系统中，它位于“外观”部分，您也可以使用快捷键Ctrl+F在系统偏好设置面板中搜索它。

此选项需要您使用的主题支持。如果您正在编写主题 CSS，请使用 ` rem<font-unit>` 作为字体单位，以确保此选项生效。

2

更改源代码模式字体
您可以使用

#typora-source {
  font-family: monospace;
  font-size: inherit.
  --monospace: monospace; /* for code blocks and inline code inside source code mode */
}
更改源代码模式下的字体。

更改代码块字体
body {
  --monospace: monospace /* for all code blocks, inline code, and source code mode */
}

// or

#md-fences {
  /* for code block only */
}



更改背景
已发布
·
2016年6月24日
更新
·
2022年3月1日
作者
·
typora.io
注意：以下部分 CSS 样式仅适用于最新版本的 Typora（macOS 上 >= 0.9.9.6，Windows 上 >= 0.9.13）。

提示：要了解这些 CSS 代码片段应该放在哪里，请参阅“添加自定义 CSS”。

我个人不建议用户为文本编辑器设置背景，但如果您仍然想要这样做，请按以下步骤操作。

例如，为 Typora 添加笔记本背景。（这张免费图片来自Fuzzimo，并复制到 Typora 的主题文件夹下。）

使用类似这样的 CSS 代码：

content {
  background: url(./fzm-seamless.notebook.texture-14.png);
  background-repeat: repeat;
}

#write {
  padding-left: 120px; /*adjust writing area position*/
}

body {
  background: #F3F3F3; 
  /* 请将此背景颜色设置为尽可能接近背景图像
     macOS 上无缝窗口的标题栏将使用此背景颜色
     Win/Linux 上的 Typora 将使用此颜色判断是否为深色模式 */
}

/* 可能需要其他 CSS 来调整 UI 组件 */
```

### 示例 2：太空船背景

另一个例子：

```css

content {
  background-image: url(http://localhost:4000/media/background/crashed_ship_by_hiddenvortexdesigns-da57nk8.jpg);
  background-repeat: repeat;
  background-position: -52px;
}

#write {
  margin-top: 24px;
  background-color: rgba(255, 255, 255, 0.68);
  margin-bottom: 24px;
  min-height: calc(100% - 48px);
}

body {
  background-color: #8F9D9A;
}

/* 其他 CSS 来调整 UI 组件 */
```

---

## 添加自定义 CSS

**发布日期：** 2016年6月25日  
**更新日期：** 2022年7月3日  
**作者：** typora.io

> **提示：** 此功能需要 Windows 系统上 Typora 版本高于 0.9.12，macOS 系统上 Typora 版本高于 0.9.9.5.1。

### 打开主题文件夹
要在 Finder/资源管理器中打开 Typora 的主题文件夹，请打开“外观”部分的偏好设置面板，然后点击“外观”部分下的“打开主题文件夹”按钮。

您可以在这里添加自定义主题。如果您想查找、安装或编写主题，请参阅“关于主题”页面。

但您可能只想修改 CSS，例如更改字体或增加书写区域，并将其应用于所有主题或仅应用于当前主题，而无需编写全新的主题文件。本节将向您展示如何实现这一点。

将自定义 CSS 添加到所有主题或其他主题
Typora 将按以下顺序加载 CSS 文件：

Typora 的基本样式
当前主题的 CSS
base.user.css在主题文件夹下
{current-theme}.user.css在主题文件夹下。
如果主题文件夹下不存在，您可以创建base.user.css它们。{current-theme}.user.css

如果您想更改 CSS 样式并将其应用于所有主题，则应修改base.user.css并附加您自己的 CSS，这样无论选择哪个主题，您的 CSS 样式仍将被加载和应用。

如果您想修改特定主题（例如“Newsprint”）的某些 CSS，您可以创建newsprint.user.css并添加所需的 CSS 代码。我们不建议您直接修改主题文件的原因如下：

Typora 安装后提供的默认主题也可能会更新。如果发生这种情况，新版本会直接替换主题文件夹下的现有主题，您所做的修改将会丢失。
其他人开发的主题将来也可能会更改。如果他们更改了 CSS 文件，您可以直接用旧文件替换他们的新文件，而不用担心您的修改会丢失。
（如果您自己编写了 CSS 主题，那么直接修改它是可以的。）

注意：文件名区分大小写。文件{current-theme}名{current-theme}.user.css必须与当前主题的文件名部分相同。例如，“GitHub”主题的 CSS 文件是 `<style>.css.css` github.css，因此文件名部分是“github”而不是“Github”。

调试 CSS
您可以打开 Chrome/Safari 开发者工具来调试元素样式。

在 macOS 上，您可以选中Help->Enable Debug菜单项，然后在 Typora 的混合编辑视图中的任意位置单击鼠标右键，然后从上下文菜单中单击“检查元素”。
View在 Windows/Linux 系统中，您可以从->Toggle DevTools菜单项打开 DevTools 。
通用样式定制
字体
排版
背景
代码块
标题
书写区域宽度
列表样式
任务清单
文本方向（RTL）
图表
对焦模式
目录



Change Styles in Focus Mode
Published
·
July 17, 2016
Updated
·
March 1, 2022
Author
·
typora.io
TL;DR

You can simplify change the text color in unfocused paragraph by adding following css:

:root {
  --blur-text-color: #FFF;
}
```

### 高级配置

如果您想要更高级的样式配置，可以参考以下内容：

```css
/* 以下是 LESS 代码，用于更好的 CSS 结构 */

.on-focus-mode {
  /* under focus mode*/
  
  .md-end-block:not(.md-focus):not(.md-focus-container) {
    
    * {
      /* use color close to background for un-focused block */
      color: #C8C8C8 !important;
    }
    
    img{
      /* make img and element less attractive */
      opacity: 50%;
    }
  }
  
  .task-list-item:not(.md-focus-container)>input {
    /* make the check mark on task list less attractive*/
    opacity: 50%;
  }
  
  .md-fences.md-focus .CodeMirror-code>*:not(.CodeMirror-activeline) *,
  .CodeMirror.cm-s-inner:not(.CodeMirror-focused) * {
      /*lines in unfocused code fences, and unfocused lines in focused code fence*/
    color: #C8C8C8 !important;
  }
  
  li[cid]:not(.md-focus-container) {
    color: #C8C8C8 !important;
  }
  
  #typora-source .CodeMirror-code>*:not(.CodeMirror-activeline) * {
    /*source code mode under focus mode*/
    color: #C8C8C8 !important;
  }
  
  .md-focus,
  .md-focus-container {
    /* for text in current focused block */
    color: #111;
  }
 
}
Please note that when focus mode is enabled, the <body> dom will have class on-focus-mode, and focused block level elements will have class md-focus.

Blocks that can contain md-focus class are blocks that cannot contain children blocks and will contain a md-end-block class. For instance, <blockquote> can contain children blocks like <p>, so it does not have md-end-block class, while h1 would have that class. md-focus-container class will apply to li which contains a .md-focus block.


About Themes
Published
·
September 26, 2016
Updated
·
January 17, 2025
Author
·
typora.io
日本語 (ja)

Change Themes
Typora has 6 built-in themes, which can be selected using the Themes menu in the menu bar. You can also download, install, modify or write your own custom theme to stylize Typora.

Typora uses CSS to style everything. Each theme shown in the Themes menu is one .css file under “Typora’s theme folder”. So you can add/modify themes by adding/modifying the corresponding CSS files under “Typora’s theme folder”.

Use Themes Under Light Mode and Dark Mode
You can set separate themes for light mode and dark mode (on macOS / Windows). When the system’s color scheme changes, the corresponding theme you chose will be applied.

Screen Shot 2020-12-05 at 17.01.49

Your theme can also use a media query for prefers color scheme to write a responsive theme for both light mode and dark mode.

Naming Rule
When writing your own theme, you need to use these file naming rules for theme css: do not use capitalized letters or non-alphabet characters except -. Replace any whitespace with - and Typora will convert them to a readable label in the menu item. For example, for my-first-typora-theme.css, Typora will show “My First Typora Theme” under the “Themes” menu.

Get Typora Themes
We have an official website Typora Theme Gallery for designers/developers to share their custom themes with others. You can download themes from there.

Screen Shot 2020-12-05 at 22.09.28

Custom Themes Installation
Open the Theme Folder. (see instructions below)
Copy or move the .css file and related resources, like fonts or images, into the newly opened folder.
Restart Typora, then select it from the Themes menu.
Open Theme Folder
macOS
Open the preference panel and click the “Open Theme Folder” button.

typora-preference-mac

On macOS, it is usually /Users/{username}/Library/Application Support/abnerworks.Typora/themes/.

Windows/Linux
Open the preference panel using File → Preference from the menubar and then click “Open Theme Folder”:

typora-preference-electron

Modify Current Styles
Sometimes you may just want to change the font family for all themes or change the font color for headings of specific themes. In this case, you do not need to copy/modify a whole existing CSS file, using Add Custom CSS is enough.

Writing My Own Theme
Please see Write Custom Theme for Typora.

Debug Theme CSS
You can open Chrome/Safari DevTools to debug element styles. For more details, you can click here.

On macOS, please follow https://support.apple.com/en-hk/guide/safari/sfri20948/mac to enable the Develop menu within Safari, then inspect Typora’s webview from Safari menu → Develop → [your macOS device name] → Typora.
On Windows/Linux, you can open DevTools from the View -> Toggle DevTools menu item.


Task List — Easy Way to Record Todos
Published
·
August 23, 2017
Updated
·
May 11, 2023
Author
·
typora.io
Basic Usage
The following markdown syntax will be rendered as a Task List:

- [ ] This task is incomplete.
- [x] This task is completed.
Quickly Changing Task Status
Simply click on the checkbox of a task list, or —

Select menu items under Paragraph → Task Status;

Follow the Custom Key Binding instructions to assign shortcut keys as needed.

“Erasing” Completed Tasks
You may want to add a strikethrough on completed tasks automatically like this:

Snip20170824_1

This can be achieved by adding the following Custom CSS:

.task-list-done {
    /* styles for completed tasks */
    text-decoration: line-through;
}
.task-list-not-done {
    /* styles for incomplete tasks */
}
If you want a completed task list to display with less contrast, you can add CSS in the format color: #777 to change the text color for selector .task-list-done.

For details on where to put this CSS, please read Add Custom CSS.



Change Width of Writing Area
Published
·
March 8, 2018
Updated
·
March 1, 2022
Author
·
typora.io
Some of following CSS style will work for latest version of Typora (>= 0.9.9.6 on macOS, and >=0.9.13 on Windows).

About where to put those CSS, please follow Add Custom CSS.

Example CSS:

#write {
  max-width: 1800px; /*adjust writing area position*/
}
You could also use other css styles like padding-left or padding-right to adjust the writing area.

To change the width of source code mode:

#typora-source .CodeMirror-lines {
  max-width: auto; /*or 1000px*/
}
width	narrow
Screen Shot 2021-04-19 at 22.57.29	Screen Shot 2021-04-19 at 22.57.58


Whitespace and Line Breaks
Published
·
April 3, 2018
Updated
·
July 29, 2022
Author
·
typora.io
Recommended Practices in Typora
Line breaks are very confusing in Markdown, our recommendations is that:

Use Typora’s default setting.
Write in Typora’s hybrid view.
Press Enter key to insert new paragraphs and avoid insert new lines.
If you do need single hard line break, use the syntax: <br/>.
Single Line Breaks
Single line break is parsed differently across different Markdown engines, CommonMark will just ignore it, in other words, if you write:

line 1
line 2
it will be rendered as

line 1 line 2

But other markdown engines may choose to keep it (like input box for issues in GitHub), or provide options whether to preserve it or not.

In Typora, we provide options whether to preserve it or not in preference panel, and you would choose the behavior when writing from menu bar quickly. By default, Typora will Preserve line breaks in editing view and ignore them when print or export. You could change this option in preference panel.

Whitespace
Sequential whitespace are similar to Single Line Breaks, most Markdown engines will ignore them, for example, in CommonMark,

Four    whitespace in between
will be converted to

<p>Four    whitespace in between</p>
and you will only see

Four whitespace in between

By default, Typora will Preserve sequential whitespace in editing view and ignore them when print or export. You could change this option in preference panel.

If you do want to insert sequential whitespace that Other markdown engines support, you could

Use HTML entity &nbsp;.
Or, add css whitespace:pre-line; for the 3rd markdown engine output.
Enter key in Typora
In Markdown, two line break means create a new paragraph, in Typora, when you press Enter key, a new paragraph is created, and if you switch to source code mode, two line breaks are inserted, for example, source of

Paragraph 1

Paragraph 2

is

paragraph 1
(empty line)
paragraph 2
You could explicitly insert a single line break in editing view by pressing Shift+Enter key.

Markdown Line Break
Markdown provides ways to insert single hard line break:

Insert two whitespace and a line break.
Insert HTML tag <br/> directly.
Almost all Markdown engines will parse them as hard line break in the output.

Change Related Settings in Typora
We provide related settings in Preference Panel → Markdown → Whitespace / LineBreak, or Edit -> Whitespace and Line Breaks from menu bar.

Screen Shot 2021-12-11 at 16.03.29




Typesetting with CSS
Published
·
March 20, 2021
Updated
·
July 3, 2022
Author
·
typora.io
日本語 (ja)

This article explains common style preferences for your typesetting based on Custom CSS.

To use this, please read Custom CSS first.

Outline

Page Setting
Change Background
Change Width of Writing Area
Text & Font
Change Font
Uppercase Headers
Small-cap Headers
Ligature
Paragraph & Alignment
Justify Alignment
Center alignment
Right to Left Writing
Vertical Writing
Center / Do not Center Image
Components
List Styles
Auto Numbering for Headings / Outline / TOC
Control TOC Levels
Change Color Themes for Code Fences / Source Code Mode
“Erase” Completed Tasks
Styles for Diagrams
Editing
Change Styles for Focused / Unfocused Text in Focus Mode
Change Writing Direction
Do not Hide Markdown Syntax
Page Setting
Change Background
To change the background of your writing area, see https://support.typora.io/Backgound/.

Change Width of Writing Area
To change the width of your writing area, see https://support.typora.io/Width-of-Writing-Area/.

Text & Font
Change Font
To change font color, font family and font size, see https://support.typora.io/Custom-Font/.

Uppercase Headers
For example, to make Heading 1 uppercased, you can use:

h1 {
  text-transform: uppercase;
}
You can partially make some text uppercased by inputting HTML directly in Typora:

<span style="text-transform: uppercase;">This text will be in uppercase</span>
Small-cap Headers
For example, to make Heading 4 small-caped, you can use:

h4 {
  font-variant: small-caps;
}
You can partially make some text in small-caps by inputting HTML directly in Typora:

<span style="font-variant: small-caps;">This text will be in small-caps</span>
Ligature
You can change font ligatures by

#write {
  /* Keyword values */
  font-variant-ligatures: normal;
  font-variant-ligatures: none;
  font-variant-ligatures: common-ligatures;           /* <common-lig-values> */
  font-variant-ligatures: no-common-ligatures;        /* <common-lig-values> */
  font-variant-ligatures: discretionary-ligatures;    /* <discretionary-lig-values> */
  font-variant-ligatures: no-discretionary-ligatures; /* <discretionary-lig-values> */
  font-variant-ligatures: historical-ligatures;       /* <historical-lig-values> */
  font-variant-ligatures: no-historical-ligatures;    /* <historical-lig-values> */
  font-variant-ligatures: contextual;                 /* <contextual-alt-values> */
  font-variant-ligatures: no-contextual;              /* <contextual-alt-values> */
  font-variant-ligatures: contextual;                 /* <no-historical-ligatures> <common-ligatures> */
}
Paragraph & Alignment
Justify Alignment
#write {
  text-align: justify;
}
Center alignment
For example, center align Heading 4, you can use

h4 {
  text-align:center;
}
You can partially make a paragraph with centered texts by inputting HTML directly in Typora:

<center>This text will be center aligned</center>
Right to Left Writing
RTL (right-to-left) support is limited, see https://support.typora.io/RTL/.

Vertical Writing
Vertical writing support is limited.

#write {
   writing-mode: vertical-rl; /*make it vertical rendering*/
   -webkit-writing-mode: vertical-rl;
  text-orientation: mixed;
  overflow-x: auto; /* This enables horizontal scrolling */
}

/* remove the default margin top */
#write > p:first-child, #write > ul:first-child, #write > ol:first-child, #write > pre:first-child, #write > blockquote:first-child, #write > div:first-child, #write > table:first-child {
    margin-top: 0;
}
For known issues, see https://github.com/typora/typora-issues/issues/1121.

Center / Do not Center Image
In default theme, if one paragraph it nothing but one image, Typora will center align it.

To change this behavior, or center align multiple images, see https://support.typora.io/Images/#align-images.

Components
List Styles
See https://support.typora.io/List-Style/

Auto Numbering for Headings / Outline / TOC
See https://support.typora.io/Auto-Numbering/.

Control TOC Levels
See https://support.typora.io/TOC-levels/.

Change Color Themes for Code Fences / Source Code Mode
See https://support.typora.io/Code-Block-Styles/.

“Erase” Completed Tasks
See https://support.typora.io/Task-List/#erase-completed-tasks.

Styles for Diagrams
See https://support.typora.io/Draw-Diagrams-With-Markdown/#sequence-diagrams-options and https://support.typora.io/Draw-Diagrams-With-Markdown/#mermaid-options.

Editing
Change Styles for Focused / Unfocused Text in Focus Mode
See https://support.typora.io/Change-Styles-in-Focus-Mode/.

Change Writing Direction
See https://support.typora.io/RTL/.

Do not Hide Markdown Syntax
You could check the https://theme.typora.io/theme/Monospace/ theme.

In short, it uses CSS to prevent markdown syntax from hiding:

.md-meta,
.md-content {
  display: inline;
}


Customize List Styles
Published
·
July 3, 2022
Author
·
typora.io
You can add following custom CSS to customize the styles of lists.

Ordered List Styles
Type	Output	CSS
Numbers (default style)	Screen Shot 2022-07-03 at 17.09.16	ol {list-style-type: decimal;}
Numbers (with leading 0)	Screen Shot 2022-07-03 at 17.09.38	ol {list-style-type: decimal-leading-zero;}
Chinese Numbers	Screen Shot 2022-07-03 at 17.10.23	ol {list-style-type: cjk-ideographic;}
Hiragana	Screen Shot 2022-07-03 at 17.10.49	ol {list-style-type: hiragana;}
Katakana	Screen Shot 2022-07-03 at 17.11.12	ol {list-style-type: katakana;}
Alphabet	Screen Shot 2022-07-03 at 17.11.46	ol {list-style-type: lower-alpha;}
Alphabet (uppercase)	Screen Shot 2022-07-03 at 17.12.01	ol {list-style-type: upper-alpha;}
Greek	Screen Shot 2022-07-03 at 17.12.20	ol {list-style-type: lower-greek;}
Roman numerals (lowercase)	Screen Shot 2022-07-03 at 17.12.34	ol {list-style-type: lower-roman;}
Roman numerals (uppercase)	Screen Shot 2022-07-03 at 17.12.51	ol {list-style-type: upper-roman;}
Unordered List Styles
Type	Output	CSS
circle	Screen Shot 2022-07-03 at 17.22.26	ul {list-style-type: circle;}
disc	Screen Shot 2022-07-03 at 17.22.37	ul {list-style-type: disc;}
square	Screen Shot 2022-07-03 at 17.22.50	ul {list-style-type: square;}
Custom Contents	Screen Shot 2022-07-03 at 17.25.15	ul {list-style-type: "* ";}
Custom Contents	Screen Shot 2022-07-03 at 17.25.27	ul {list-style-type: "😎 ";}
Nested Lists
You can also change styles for nested lists using CSS selector, for example:

ol {
  list-style-type: decimal;
}

ol ol {
 list-style-type: lower-alpha;
}

ol ol ol{
 list-style-type: lower-roman;
}
Which will render lists like this:

Screen Shot 2022-07-03 at 17.19.31

Task Lists
Please check document here

More Styles
You can find more listing styles at here.




Write Custom Theme for Typora
July 16, 2016 by typora.io
Translations
简体中文, 繁體中文, 日本語

Update – CSS Variables
Overwriting existing CSS Variables is more recommended if you want to define fonts, colors, backgrounds. Earlier versions of macOS/Safari does not support this, but it is still much easier to use. Common used ones are:

:root {
   --bg-color:  #ffffff; /*change background*/
   --text-color: #333333; /*change text color*/
   --md-char-color: #C7C5C5; /*change color of meta characetrs like `*` in markdown */
   --meta-content-color: #5b808d; /*change color of meta contents like image text or link address in markdown */

   --primary-color: #428bca; /* color of primary buttons */
   --primary-btn-border-color: #285e8e;
   --primary-btn-text-color: #fff;

   --window-border: 1px solid #eee; /*border for sidebar, etc*/

   --active-file-bg-color: #eee; /*background color if list item in file tree or file list*/
   --active-file-text-color: inherit;
   --active-file-border-color: #777;

   --side-bar-bg-color: var(--bg-color); /*change background of sidebar*/
   --item-hover-bg-color: rgba(229, 229, 229, 0.59); /*background of control items when hover, like menu in sidebar*/
   --item-hover-text-color: inherit;
   --monospace: monospace; /*monospace font for codes, fences*/
}
The variables may change in future, so you could use DevTools in Typora to confirm it.

Summary
If you want to write a custom CSS theme for Typora, all you need to do is:

Create a new css file. The file name should not include capitalised characters or whitespace, for example: my-typora-theme is a valid file name.

Write the css file.

We prepared a toolkit for you to get started or to do simple testing.

If you want to write one from scratch, pick the template.less, and fill it.

If you want to convert existing css files (from Wordpress or Jekyll theme), just copy the content, and then add styles those css files did not cover, like styles for “toc” or for UI components.

Tweak/Debug css classes and styles.

You could also follow how to install custom theme to install and use the theme and test it with Typora.

To debug CSS in Typora like in Safari or Chrome, you could enable debug mode from help menu (macOS) or from preferences panel (macOS/Linux/Windows) and find & click “Inspect Elements” from context menu, which will pop up the DevTools like Safari or Chrome browser. On Linux/Windows version, you could toggle it from View menu or just press F12.

You could also put the css file you created into toolkit/theme/test.css along with resources like image or font it uses. And open html files under toolkit/core and toolkit/electron to preview your css. Please preview the html files using Safari on Mac or Chrome on Linux/Windows.

If you want to share your theme, just make a fork and make a pull request to Typora Theme Gallery.

Basic Rules
File naming rule for theme css: Do not use capitalized letters, and please replace whitespace with -, and Typora will convert them to readable label in menu item. For example, for my-first-typora-theme.css, Typora will put an menu item “My First Typora Theme” under “Themes” menu.
Put default font size into html, then for elements like h1 or p, use rem for their font-size property, or else custom font size in preference panel will not work.
Use tag as selectors if possible. For example, for ### heading 3, use h3 instead of h3.md-header, because for any markdown render, “### heading 3” will be converted to h3 tag. And for typora, we will keep as less html attributes (including class) as possible just like other markdown convertors. You could limit h3 in writing area by #write h3 selector.
Typora is created upon Webkit (on macOS) or Chromium (on Windows/Linux), so please use css properties supported by Chrome or Safari (aka Webkit).
Some modifications of CSS may cause Typora not to work as expected, for example, adding white-space: pre-wrap; to selector #write will make \t cannot be inserted by pressing Tab key, so please overwrite default css styles as less as possible, test it out.
Table of Contents:

Translations
Update – CSS Variables
Summary
Basic Rules
Changes and Updates
Which CSS selector should I use?
General
Block Elements
Lines
Code Fences
Mermaid
Inline Elements
Source Code Mode
Focus Mode
Custom Font
Background
Controller UI
Additional UI for Windows/Linux
Print
Debug and Test
Test in Browser
Test in Typora
Tips and References on custom style
Changes and Updates
None

Which CSS selector should I use?
General
The window content of Typora is a webpage, so please put background, font-family or other general properties into the html tag. On mac, if seamless window style is used, then the background color of the toolbar is defined by the background-color style of the html.

The writing area is a div with id #write, change the width, height, padding will adjust the size of the writing area. The properties you set, for example, color for html, will apply to whole window content, including UI parts, like the font-color in insert table dialog, so if you just want to change the style of the writing content not the UI controller part, you could put them under #write selector.

/** example **/
html, body {
  background-color: #fefefe; /*background color of the window and titlebar*/
  font-family: helvetica, sans-serif; /*custom font*/
  ...
}

html {
  font-size: 14px; /*default font size*/
}

#write {
  max-width: 90%; /*adjust size of the wriring area*/
  font-size: 1rem; /*basic font size*/
  color: #555; /*basic font color*/
  ...
}
Typora will try to render all elements as other output, so, paragraphs are wrapped by <p> tag, lists are wrapped by <ul> or <ol> just like they are parsed by other Markdown processors, so you could change their styles by applying css styles to those HTML tags. Also, because of these, css files created for Wordpress or other static sites would also affect most styles in typora, therefore you would direct “borrow” css rules from them, and add missing part or do some adjustment.

Block Elements
As I wrote, Typora will try to render all elements as other output, for instance, <p> for paragraph, <table> for tables, <h1> for 1st level headings, etc, so you could change most typesetting by writing styles like:

p {...}
h1 {...}
table {...}
table th td {...}
table tr:nth-child(2n) td {...}
...
You could add #write as ancestor selector to make the style only apply to the writing area, without affecting control component (For instance, title in some dialogs may also be wrapped by h4 tag).

/*this will only aplly to h4 in dialogs popped up by typora (just an example)*/
.dialog h4 {...} 

/*this will only apply to h4 inside writing area, which is generated after user input "#### " */
#write h4 {...} 
Aslo, all block elements has a mdtype attribute. For example, you could also select headings by selector [mdtype="heading"]. Possible type includes paragraph, heading, blockquote, fences, hr, def_link, def_footnote, table, meta_block, math_block, list, toc, list_item, table_row, table_cell, line. But in most cases, tag selector is enough.

mdtype	Output Css Selector	Explanation
paragraph	p	 
line	.md-line	A paragraph can contain one or more .md-line
heading	h1~h6	 
blockquote	blockquote	 
list (unordered list)	ul li	 
list (ordered list)	ol li	 
list (task)	ul.task-list li. task-list-item	 
toc	.md-toc	Also refer to [this doc][toc]
fences (before codemirror is initialized)	pre.md-fences.mock-cm	 
fences	pre.md-fences	please refer to “Code Fences” section
diagrams	pre[lang=’sequence’], pre[lang=’flow’], pre[lang=’mermaid’]	They are special code fences with certain code language.
hr	hr	 
def_link	.md-def-link	with children .md-def-name, .md-def-content, .md-def-title
def_footnote	.md-def-footnote	with children .md-def-name, .md-def-content
meta_block	pre.md-meta-block	content for YAML front matters
math_block	[mdtype=”math_block”]	preview part is .mathjax-block, html content is generated via MathJax. TeX editor is powered by CodeMirror, please refer to “Code Fences” section
table	table thead tbody th tr td	 
Lines
Typora will render hard line break as-is. Therefore, a paragraph may contain multiple lines split by \n, and .md-line selector is used for each “line” inside a <p>.

Code Fences
Syntax highlight is enabled by CodeMirror’s feature. Please refer to this doc for detail.

Mermaid
Examples: mermaid.css, mermaid.dark.css, mermaid.forest.css.

Inline Elements
Inline elements are also rendered as it is rendered by most markdown parsers. So following could work:

strong {
  font-weight: bold;
}
em {..}
code {..}
a {..}
img {..}
mark {..} /*highlight*/
An inline elements usually includes a wrapper span, meta syntax, and output inline element, for example **strong** will be rendered as

<!--wrapper for strong element-->
<span md-inline="strong" class=""> 
  
  <!--meta syntax for strong element-->
  <span class="md-meta md-before">**</span> 
  
    <!--output for strong element-->
    <strong>
      <!--inner output-->
      <span md-inline="plain">strong</span> 
    </strong>
  
   <!--meta syntax for strong element-->
  <span class="md-meta md-after">**</span>
</span>
As you can see, the full part of an inline element is wrapped by a span with an md-inline attribute indicates the type info of the parse result. Possible attribute includes (some inline syntax need to be enabled from preference panel):

md-inline	syntax	Output Tag
plain	plain	span
strong	**strong**	strong
em	*em*	em
code	`code`	code
underline	<u>underline</u>	u
escape	\(	span
tag	<button>	 
del	~~del~~	del
footnote	^1	sup
emoji	:smile:	span
inline_math	$x^2$	span
subscript	~sub~	sub
superscript	^sup^	sup
linebreak	(two whitespace at end of a line)	 
highlight	==highlight==	mark
url	http://typora.io	a
autolink	<http://typora.io>	a
link	[link](href)	a
reflink	[link][ref]	a
image	![img](src)	img
refimg	![img][ref]	img
Following are explanations about how Typora style inline markdown syntax such as * or _, which is hidden in most cases in Typora. Usually you do not need to set CSS rules for them specifically.

Meta syntax like ** or == of those inline elements will disappear when you convert a markdown file to HTML. So they are wrapped by class md-meta and has style display:none by default. Some syntax like the markdown syntax for image will also be hidden by default, and they are wrapped by md-content class. When the cursor is inside those inline elements, the focused one will be wrapped by md-expand class, then .md-meta and .md-content will become visible. So, apply styles to .md-meta and .md-content if you want to modify the style of those meta syntax.

Source Code Mode
SourceCode Mode is also powered by CodeMirror, so the class it uses for syntax highlight is same as code fences (detail here). Please note that code fences use codemirror theme .cm-s-inner, while in source code mode, codemirror theme is .cm-s-typora-default. So the CSS is like:

.cm-s-typora-default .cm-header {
  /*styles for h1~h6 in source code mode*/
}
Focus Mode
For this topic, please refer to this doc

Custom Font
For this topic, please refer to this doc.

Background
For this topic, please refer to this doc.

Controller UI
Most UI components including tooltip, dialog and buttons are painted by HTML. And you only need to change those part when you find the UI components are incompatible with your editor theme after finishing steps above. HTML files from the toolkit includes most common UI components for you to easily debug.

Additional UI for Windows/Linux
The Windows/Linux version of typora use much more HTML-powered components than macOS version, including context menu, preference panel, and even window frame itself if you use “unibody” window style on Windows.

HTML files from the toolkit could include most common UI components for you to easily debug.

Print
Write css inside following block will make them only change the style of printed one or exported PDF.

@media print {
    /* for example: */
    .typora-export * {
        -webkit-print-color-adjust: exact;
    }
    /* add styles here */
}
Debug and Test
Test in Browser
We provide some html files under html-preview folder from the toolkit to preview your theme from Safari or Chrome. To use them, please rename and put your css file into html-preview/theme/test.css.

Test in Typora
Follow this doc to learn about how to install a theme into Typora.

Then for mac users, check enable debug mode from help menu, then click “Inspect Element” from context menu to pop up DevTools.

For Windows/Linux users, you could pop up the DevTools from Toggle DevTools from view menu.

Tips and References on custom style
Related documents are here.

Please make a pull request to typora-wiki-site if you have some tips to share.