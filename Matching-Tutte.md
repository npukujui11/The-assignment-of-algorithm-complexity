##### 问题：如何判断一棵树T上有完美匹配

* 树$\mathrm{T}$具有完美匹配当且仅当对于每个顶点$\mathrm{v}$，$\mathrm{T\backslash \{v\}}$只有一个奇分量；亦等价于树T有完美匹配的充要条件为对于每个顶点$\mathrm{v}$，$\mathrm{o(G-v)=1}$

* 根据$\mathrm{Tutte}$完美匹配条件，如果我们有一个完美匹配，我们必须有偶数个顶点。

* 对树中的顶点数量进行归纳证明。$\mathrm{n=1}$不满足条件，所以我们从$\mathrm{n=2}$开始，结果为$\mathrm{Trivial}$。

* 对于归纳步骤，我们考虑一个叶子$\ell$和它唯一的邻居$\ell^{\prime}$。因为去掉$\ell^{\prime}$应该只剩下一个奇数分量，所以这个分量必须是由$\ell^{\prime}$组成的。因此，从树中删除$\ell^{\prime}$必须留下一些偶数部件，它们是较小的偶数大小的树。对于这些组件，我们在下面验证从组件中删除一个顶点只会留下一个奇数组件。通过归纳假设，我们就可以完成了，因为我们可以把这些小分量中的所有完美匹配和边$\ell\ell^{\prime}$放在一起得到原始树中的完美匹配。

* 现在考虑$\mathrm{T \backslash \{\ell^{\prime}\}}$中的偶分量$\mathrm{C}$。如果从$\mathrm{C}$中去除$\mathrm{v^{*}}$，则$\mathrm{C}$中至少会留下一个奇分量。假设从$\mathrm{C}$中去除$\mathrm{v^{*}}$，则$\mathrm{C}$中至少会留下两个奇分量。需要注意的是，在$\mathrm{T \backslash \{v^{*}\}}$中，这些分量都是$\mathrm{C}$的分量，只有一个连接到$\mathrm{\ell^{\prime}}$，而且这个分量的大小不会改变奇偶性，因为$\mathrm{V(T) \backslash V (C)}$的大小是偶数。因此，$\mathrm{T\backslash \{v^{*}\}}$也至少有两个奇分量，这与关于$\mathrm{T}$的假设是矛盾的。因此，从$\mathrm{C}$中移除一个顶点只留下一个奇数分量。