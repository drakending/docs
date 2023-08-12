# 计算理论———最基本的定义
一门关于字符串的课（bushi）

简单来说，可以把问题进行一定程度的抽象，比如用二进制或者其他方式的字符串来表述一个问题，我们从一个最基本的角度来审查，图灵机是怎么解决问题（字符串）的。

## 1.Alphabet

a **finite** set of symbols. represented by $\sum$

$$\sum = \{a,...,z\},\{0,1\},\emptyset$$

一个表示手段而已，不难理解

## 2.String

a **finite** sequence of symbols from some alphabet.

该门课里面，对问题的抽象，也是我们关心和研究的东西。

### properties and operation on string

* length:symbols' number in string
* empty string:长度为0的string
* $\sum^i$:在字符集$\sum$上，长度为i的字符串的集合
* concatenation: 拼接，$a=123，b=456，ab=123456$
* exponentiation：重复 $a=12,a^2=1212$
* reversal: 翻转 $a=12,a^R=21$

## 3.Language

Any $L\subseteq\sum^*$ is called a language over $\sum$

简单来说，语言就是在某个字符集上部分字符串的集合，他们能被归类为一个集合也就有其对应的性质，所以我们在研究language的同时，也是在研究问题本身。

某个问题的解=某个问题解集具有相同性质=该解集类的字符串有某种相同性质=一种language

研究怎么区分不同的language=研究问题的可解性

## 4.Regular expression [^1]

[^1]: 这部分myc上课好像跳过了但是我觉得还是有必要讲一下的。

基于上文，我们要研究的是language的性质，那如何来表达这种性质呢？
常规的方法是用集合或者自然语言，如，包含1的数量大于3的01字符串，前三个字符是000的01字符串....,而将这些表达书面化，即成为了Regular expression。

关于regular expression有以下规则:

!!! note inline end
    * $\alpha^*$代表$\alpha$重复任意多次(**包括0**)
    * $\alpha\cup\beta$代表$\alpha$或$\beta$
* $\emptyset$ 和 任一alphabet中的字母均属于regular expression
* 如果$\alpha$和$\beta$均为regular expression，则$\alpha\beta,\alpha\cup\beta,\alpha^*$均为regular expression.

而基于某个regular expression生成的字符串我们可以把它写作$\mathcal{L}(\alpha)$，对于复合的regular expression，很容易发现以下规则。

* $\mathcal{L}(\emptyset)=\emptyset,\mathcal{L}(\alpha)=\{\alpha\}$
* $\mathcal{L}(\alpha\cup\beta)=\mathcal{L}(\alpha)\cup\mathcal{L}(\beta)$
* $\mathcal{L}(\alpha\beta)=\mathcal{L}(\alpha)\mathcal{L}(\beta)$
* $\mathcal{L}(\alpha^*)=\mathcal{L}(\alpha)^*$

!!! note
    上面这些定理看起来十分简单明了（稍微想几个例子大概就懂了），理解的难度大概在概念上，事实上，只要理解清楚等式左边代表着“规则”的复合，等式右边代表着由“规则生成的字符串”的复合，其实没有什么特别难理解的地方。

以下为一些alphabet为01的regular expression的例子。

=== "Example 1"
    以1结尾的字符串的Regular Expression
    ??? answer
        $(0\cup1)^*1$

=== "Example 2"
    包含111的字符串的Regular Expression
    ??? answer
        $0^*\cup(((0^*(1\cup(11)))((00^*)(1\cup(11)))^*))$
        
        真的有必要搞懂吗x，其实没必要，学到后面有一些标准的方法能按部就班完成自然语言与Regular Expression的转换。

既然有了定义，接下来的问题是，我们如何确定一个字符串是否属于某一Regular Expression呢（等价于，我们如何知道一个解是不是属于某问题的解集），为了解决这个问题，我们引入了图灵机。

## regular language
language的集合，符合某一regular expression的language 都可以被称为regular language.