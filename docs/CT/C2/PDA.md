# Pushdown Automata(堆栈自动机，PDA)

## 定义
PDA=NFA+stack

!!! Definition
    PDA 可以被以下6个变量表示，$P=(K,\sum,T,\Delta,s,F)$
    
    * T:stack alphabet
    * $\Delta$: $(K\times (\sum\cup\{e\})\times T^*)\times(K\times T^*)$
        * 第一个$K$：current state
        * $\sum\cup\{e\}$：读取的字符（可为空）
        * $T^*$: 从栈中pop out一个string
        * 第二个$K$: next state
        * $T^*$：push string进栈
    !!! example
        ((p,a,123),(q,45))代表在p状态读入a，且栈顶为123的时候（1在顶），pop 123，状态转移到b，push 45。
    
    * $\sum$: alphabet
    * F: final state
    * s: initial state
    * K: state sets
    （后面四个与NFA相同含义）

由于PDA多了一个栈结构，描述PDA的一个状态要用一个三元组$(p,x,\alpha)$，分别表示（当前状态，剩余字符串，当前栈状态）
类似，移动过程也被写作

$(p,x\alpha)\vdash_p (q,y,\beta)$ ($\vdash_p^*$概念也和前文相同)

而一个PDA 接受一个字符串当且仅当移动的最终状态为

$(q,e,e),q\in F$ (**这里要求栈为空，状态为最终状态**)

我们称被PDA $P$ 接受的language为$L(P)$

!!! danger
    PDA的automata部分为NFA，无法用DFA代替

## PDA与CFG的等价性
    