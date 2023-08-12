# 常用的markdown操作

## 文内注释篇

### 缩写

采用 `*[]` 的方式在任何位置对任何 字词 单独添加缩写内容，需要在markdown_extensions中添加`abbr`
*[字词]:我只是一个示例而已~

### admonition(警告)

[官方链接](https://squidfunk.github.io/mkdocs-material/reference/admonitions/#usage)

我最喜欢的，加个方格出来！大致有如下几种

!!! note "这里放标题"
    这是一个笔记`!!! note`

!!! note ""
    这是没有标题的笔记 `!!! note ""`

??? note 
    这是可展开，默认不展开的笔记 `??? note`
???+ note
    这是可展开，默认展开的笔记  `???+ note`
!!! info inline end "side block"
    inline的边栏要写成`info inline (end)` 有end的会悬浮在右侧，注意要把和block并列的文字放在block的下方，才可以达到并排的效果
还有其他样式如
!!! Abstract
!!! info
!!! Tip
具体看上文链接

### Definition Lists
突然发现[官网](https://squidfunk.github.io/mkdocs-material/setup/extensions/python-markdown/)记载的很详细，慢慢学吧x

=== "DFA"
    这个地方就是一个试验场

=== "Tab 2"
    这个功能好神奇啊
