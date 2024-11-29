# Tricks

1. 骨牌覆盖类问题优先考虑黑白染色。黑白染色完应当考虑一个强结论：黑白数量相同的图可以被完美覆盖。Source：CF1268B。
2. 满足 $\sum a \le k$ 的序列 $\langle a_1,a_2,\dots,a_t\rangle$ 的 $k + 1 - \sum a$ 之和就等价于：
   - 满足 $x + \sum a \le k + 1$ 的正整数序列 $\langle x,a_1,a_2,\dots,a_t\rangle$ 的数量，又等价于：
      - 满足 $x + y + \sum a = k + 2$ 的正整数序列 $\langle x,y,a_1,a_2,\dots,a_t\rangle$ 的数量。隔板法得到答案为 $\displaystyle\binom{k+1}{t+1}$。

   Source：ARC144D。
3. 图的最大匹配唯一等价于最大匹配就是完美匹配。Source：CF1032F。
4. 维护形如 $\displaystyle\sum_{i=l}^{r}i^ka_i$ 的式子时，可以用 $k$ 次前缀和预处理，然后差分求出答案。Source：YZOJ 5592。
5. 当答案是指数级别的且指数与 $n$ 相关时，可以对 $n$ 使用欧拉定理，减小 $n$ 的规模；当答案中还有非指数的与 $n$ 相关的项，可以将 $n$ 对 $P$ 取模。二者兼有时需要将两个模数相乘。Source：YZOJ 5678。
6. $$\text{lcm}(S)=\prod_{T\subseteq S} \gcd(T)^{(-1)^{|T|+1}}$$
   证明用 $\min-\max$ 反演。
7. [bitset 优化字符串匹配](https://www.cnblogs.com/alex-wei/p/bitset_yyds.html)。
8. 树上随机游走时，$f_u$ 可以表示成 $f_{fa_u}$ 的一次函数。Source：CF802L。
9.  要求选择的若干个值的平均值最大时，应全选最大值。Source：CF1088E。
10. 多手玩。多手玩。多手玩。多手玩。多手玩。多手玩。
    **手玩题意有利于理解题意，也有利于发现关键性质。**
    Source：CF1260E。
11. 扩展域并查集可以解决条件冲突类问题。Source：CF1713E。
12. 在博弈论中的两个状态 $a,b$，如果 $a$ 能转移到 $b$，并且 $a$ 能转移到所有 $b$ 能转移到的状态，那么 $a$ 是必胜态。
    证明分 $b$ 是必胜态还是必败态讨论：
    - 若 $b$ 是必胜态，则 $b$ 一定能转移到一个必败态 $c$，而 $a$ 能直接转移到 $c$；
    - 若 $b$ 是必败态，则 $a$ 可以转移到 $b$。

    因此 $a$ 必然可以转移到一个必败态，则 $a$ 是必胜态。
    Source：ARC137C。
13. $\displaystyle\binom{i}{j} \equiv 1 \pmod{2}$ 当且仅当 $i \operatorname{and} j = j$，其中 $\operatorname{and}$ 为按位与运算。Source：CF1713F。
14. 对长度非 $2^k$ 的序列做 FWT 时，可以不用将 $n$ 补齐至 $2^k$，而是在 FWT 的循环条件中判断当前访问位置是否超界，可以证明这样做 FWT 仍然是正确的。
    
    ```cpp
    void OR(int *f) {
        for (int o = 2, k = 1; o <= m; o <<= 1, k <<= 1)
            for (int i = 0; i < m; i += o)
                for (int j = 0; j < k && i + j + k < n; j++) f[i + j + k] ^= f[i + j];
    }
    ```
    Source：CF1713F。