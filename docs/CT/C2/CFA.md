# Context-free Language(CFL)

既然regular language的表达能力是有限的，有没有其他不同的表达方法，能够表达更丰富的language表达方式呢？

!!! tip
    事实上，学过之前的regular language之后，可以在这里找到很多组概念的对应关系。

    | Context-free Language   | Regular Language   |
    | ----------------------- | ------------------ |
    | Context-free Grammar    | Regular Expression |
    | Pushdown Automata       | Finite Automata    |
    | Pumping Theorem for CFL | Pumping Theorem    |

## Context-free Grammar

Context-free Grammar 描述的是一种递推的字符串生成方式

!!! example "一种CFG"
    * $S\rightarrow aSb$
    * $S\rightarrow A$
    * $S\rightarrow c$
    * $S\rightarrow e$
    
    基于以上规则的一种字符生成方式如下：

    $S\Rightarrow aSb\Rightarrow aaSbb\Rightarrow aaAbb\Rightarrow aabb$
以上每一行称作一根条规则(rule),rule由一下三种字符组成:

* non-terminal: S,A
* start symbol: S
* terminal: a,b,c

!!! attention
    * 字符串的生成首先从start symbol开始
    * non-terminal 只是一种“中间符号”，最后生成的字符串里面是要消失掉的。
    * 每一条规则的箭头左侧只能有一个non-terminal。

其严格定义如下：

!!! note
    一个CFG由如下几种要素组成 $G=(V,\sum,S,R)$

    * V : 有限个symbols的集合
    * $\sum$ : 终止符(terminals)的集合，即$V-\sum$为非终止符
    * $S$ : 起始符，$S\in V-\sum$
    * $R$ : $R\subseteq (V-\sum)\times V^*$ 有限个规则的集合
  
    与Regular Language中的$\vdash$操作相同，在此处，我们有：
    
    $xAy\Rightarrow xuy$表示一步推导(Derive in one step)

    $xAy\Rightarrow^* xuy$表示多步推导（包括0步）

## Context-free Language