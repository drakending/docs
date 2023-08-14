# CFG性质的进一步探讨
## DFA转CFG
事实上，CFG是比正则表达能力更强的语言，其表达自然也包括正则，那如何把一个DFA转换成CFG的表达方式呢？
!!! tip "DFA 转 CFG"
    对于DFA $M=(K,\sum,\delta,q_0,F)$，要转成CFG $G=(V,\sum,S,R)$，可通过如下步骤：

    * 对于任意$q_i\in K$ 创造中间符$Q_i$
    * $S=Q_0\quad (s=q_0)$ 
    * $Q_i\Rightarrow^* \omega$ 当前仅当 $(q_i,\omega)\vdash^*(q_j,e)\ \And\ q_j\in F$,基于该条总结如下规则：
        * $Q_i\rightarrow e\quad \forall q_i\in F$
        * $\forall q_i\in K\quad Q_i\rightarrow aQ_{i'}\quad if\ \delta(q_i,a)=q_{i'}$
  
## DFA的闭包性质探讨
DFA的闭包性与regular language略有不同，同样分情况讲述
### union
我们采用构造法可以证明拼接闭包性
对于两个语言$G_A,G_B$，我们只需要另设一个起始状态$S$，和一条规则$S\rightarrow S_A|S_B$，就可以通过$S$生成$A\cup B$了，所以$A\cup B$仍然并包 

### concatenation
我们同样可以采用如上构造方法证明闭包性
对于两个语言$G_A,G_B$，我们只需要另设一个起始状态$S$，和一条规则$S\rightarrow S_AS_B$，就可以通过$S$生成$AB$了，所以$AB$仍然并包 

### Kleene star
我们同样可以采用如上构造方法证明闭包性
对于语言$G_A$，我们只需要新增一条规则$S\rightarrow SS_A$，同时为了**包括重复次数为0，空字符串**的情况，再增加一条规则$S\rightarrow e$，所以$A^*$仍然并包 

### interset(交集)
与Regular Language不同，此处intersect是不满足闭包性质的，为了证明这一点，首先我们要学会Pumping Theorem for CFG

## Pumping Theorem for CFL
!!! note "Pumping Therom for CFL"
    对任意一个context free language $L$，存在一个正整数p，使得对于任意一个string $\omega\in L$,$|\omega|\geq p$,他可以被写成$uvxyz$，满足如下性质:

    * $uv^ixy^iz\in L,\ i\geq 0$
    * $|v|+|y|\gt 0$
    * $|vxy|\leq p$