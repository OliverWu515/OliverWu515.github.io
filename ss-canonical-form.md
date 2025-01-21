---
layout: default
updateTime: 2024.11.8
title: 线性系统理论补充 1：状态空间标准型
mathjax: true
---

[返回首页](./)  |   [转到第二部分](https://oliverwu.top/ss-canonical-form.html#conjugate) | <a href="https://oliverwu.top/file/ss-canonical-form.pdf" target="_blank">PDF 文档</a>

<h2 id="controllable">可控标准型的一般形式推导</h2>
<p>对于一单输入单输出的传递函数 <span
class="math display">\[\label{tf}\tag{1}
    G(s)=\frac{Y(s)}{U(s)}=\frac{b_{n-1}s^{n-1}+\cdots+b_1s+b_0}{s^n+a_{n-1}s^{n-1}+\cdots+a_1s+a_0}+d\]</span>
将上式改写成 <span class="math display">\[\begin{align}
    Y(s)&amp;=\frac{b_{n-1}s^{n-1}+\cdots+b_1s+b_0}{s^n+a_{n-1}s^{n-1}+\cdots+a_1s+a_0}U(s)+dU(s)
\nonumber \\
        &amp;=(b_{n-1}s^{n-1}+\cdots+b_1s+b_0)\frac{U(s)}{s^n+a_{n-1}s^{n-1}+\cdots+a_1s+a_0}+dU(s)\label{sigma}\tag{2}
\end{align}\]</span> 定义<span class="math display">\[\begin{align}
\label{Xs}\tag{3}
    X(s)=\frac{U(s)}{s^n+a_{n-1}s^{n-1}+\cdots+a_1s+a_0}
\end{align}\]</span> 则 <span
class="math inline">\(\eqref{sigma}\)</span> 可写为 <span
class="math display">\[\begin{align}
\label{Ysadapt}\tag{4}
    Y(s) = (b_{n-1}s^{n-1}+\cdots+b_1s+b_0)X(s)+dU(s)
\end{align}\]</span></p>
<p>现在来考虑 <span
class="math inline">\(\eqref{Xs}\)</span>。将其化为<span
class="math display">\[(s^n+a_{n-1}s^{n-1}+\cdots+a_1s+a_0)X(s)=U(s)\]</span>
作拉氏反变换得<span class="math display">\[\label{ilaplasex}\tag{5}
    x^{(n)}(t)+a_{n-1}x^{(n-1)}(t)+\cdots+a_1\dot{x}(t)+a_0x(t)=u(t)\]</span>
定义状态变量<span
class="math display">\[x_1=x(t),x_2=\dot{x}(t),\dots,x_n=x^{(n-1)}(t)\]</span>
则各状态变量导数是<span class="math display">\[\begin{align}
    \dot{x}_1&amp;=\dot{x}(t)=x_2\nonumber\\
    \dot{x}_2&amp;=x^{(2)}(t)=x_3\nonumber\\
    \vdots\nonumber\\
    \dot{x}_{n-1}&amp;=x^{(n-1)}(t)=x_n\nonumber\\
    \dot{x}_{n}&amp;=x^{(n)}(t)=u(t)-a_0x(t)-a_1\dot{x}(t)-\cdots-a_{n-1}x^{(n-1)}(t)\label{gamma}\tag{6}\\
    &amp;=u(t)-a_0x_1-a_1x_2-\cdots-a_{n-1}x_n\nonumber
\end{align}\]</span> 其中 <span
class="math inline">\(\eqref{gamma}\)</span> 源于 <span
class="math inline">\(\eqref{ilaplasex}\)</span>。将上面式子组合成矩阵形式即为
<span class="math display">\[\label{state}\tag{7}
    \dot{\mathbf{x}}=\begin{bmatrix}
        \dot{x}_1\\\dot{x}_2\\\vdots\\\dot{x}_{n-1}\\\dot{x}_n
    \end{bmatrix}=\underbrace{\begin{bmatrix}
        0&amp;\textcolor{red}{1}&amp;0&amp;\cdots&amp;0\\
        0&amp;0&amp;\textcolor{red}{1}&amp;\cdots&amp;0\\
        0&amp;0&amp;0&amp;\textcolor{red}{\ddots}&amp;\\
        &amp;\vdots&amp;&amp;&amp;\textcolor{red}{1}\\
        -a_0&amp;-a_1&amp;-a_2&amp;\cdots&amp;-a_{n-1}
    \end{bmatrix}}_A\begin{bmatrix}
        {x}_1\\{x}_2\\\vdots\\{x}_{n-1}\\{x}_n
    \end{bmatrix}
    +\underbrace{\begin{bmatrix}
        0\\0\\\vdots\\0\\1
    \end{bmatrix}}_bu\]</span> 这就是系统的状态方程。</p>
<p>现在来考虑 <span
class="math inline">\(\eqref{Ysadapt}\)</span>。同样作拉氏反变换得 <span
class="math display">\[y(t)=b_{n-1}x^{(n-1)}(t)+\cdots+b_1\dot{x}(t)+b_0x(t)+du(t)\]</span>
利用上面定义的状态将其改写成 <span
class="math display">\[y(t)=b_{n-1}x_n+\cdots+b_1x_2+b_0x_1+du(t)\]</span>
写成矩阵形式就是 <span class="math display">\[\label{output}\tag{8}
    y=\underbrace{\begin{bmatrix}
        b_0&amp;\cdots&amp;b_{n-2}&amp;b_{n-1}
    \end{bmatrix}}_c{\mathbf{x}}+[d]u\]</span>
这就是系统的输出方程。<span class="math inline">\(\eqref{state}\)</span>
与 <span class="math inline">\(\eqref{output}\)</span>
共同构成了系统的状态空间描述。</p>
<h2 id="conjugate">有共轭复数极点的系统之实现</h2>

[回第一部分](https://oliverwu.top/ss-canonical-form.html#controllable)

<p>考虑传递函数<span
class="math display">\[G(s)=\frac{as+b}{(s-\sigma)^2+\omega^2}\]</span>
其中各系数均为实数。 考虑将其按两个单极点进行部分分式展开 <span
class="math display">\[G(s)=\frac{k_1}{s-(\sigma+\mathrm{j}\omega)}+\frac{k_2}{s-(\sigma-\mathrm{j}\omega)}\]</span>
<span
class="math inline">\(k_1,k_2\)</span>两个系数均为复数，需要满足<span
class="math display">\[\begin{cases}
    a=k_1+k_2=(\operatorname{Re}k_1+\operatorname{Re}k_2)+\mathrm{j}(\operatorname{Im}k_1+\operatorname{Im}k_2)\\
    b=-k_1(\sigma-\mathrm{j}\omega)-k_2(\sigma+\mathrm{j}\omega)
\end{cases}\]</span> 由<span
class="math inline">\(a\in\mathbf{R}\)</span>，可知<span
class="math inline">\(\operatorname{Im}k_1+\operatorname{Im}k_2=0\)</span>，即<span
class="math inline">\(k_2=k_1^\ast\)</span>（互为复共轭）。令<span
class="math inline">\(k_1=k\)</span>，上式改写成 <span
class="math display">\[\begin{cases}
    a&amp;=2\operatorname{Re}k\\
    b&amp;=-k(\sigma-\mathrm{j}\omega)-k^\ast(\sigma+\mathrm{j}\omega)=-k(\sigma-\mathrm{j}\omega)-(k(\sigma-\mathrm{j}\omega))^\ast\\
    &amp;=-2\operatorname{Re}(k(\sigma-\mathrm{j}\omega))=-2(\operatorname{Re}k\cdot\sigma+\operatorname{Im}k\cdot\omega)
\end{cases}\]</span> 将上面第一式代入第二式，再整理得<span
class="math display">\[\begin{cases}
    \operatorname{Re}k=\frac{1}{2}a\\
    \operatorname{Im}k=-\frac{1}{2}\frac{a\sigma+b}{\omega}
\end{cases}\]</span> 则 <span
class="math display">\[G(s)=\frac{\frac{1}{2}\left(a-\mathrm{j}\frac{a\sigma+b}{\omega}\right)}{s-(\sigma+\mathrm{j}\omega)}+\frac{\frac{1}{2}\left(a+\mathrm{j}\frac{a\sigma+b}{\omega}\right)}{s-(\sigma-\mathrm{j}\omega)}\]</span>
即 <span
class="math display">\[Y(s)=\frac{\frac{1}{2}\left(a-\mathrm{j}\frac{a\sigma+b}{\omega}\right)}{s-(\sigma+\mathrm{j}\omega)}U(s)+\frac{\frac{1}{2}\left(a+\mathrm{j}\frac{a\sigma+b}{\omega}\right)}{s-(\sigma-\mathrm{j}\omega)}U(s)\]</span>
令<span
class="math display">\[Z_1(s)=\frac{1}{2}\frac{U(s)}{s-(\sigma+\mathrm{j}\omega)},Z_2(s)=\frac{1}{2}\frac{U(s)}{s-(\sigma-\mathrm{j}\omega)}\]</span>
则可写出状态空间实现为（提出<span
class="math inline">\(\frac12\)</span>是为了最终的形式简单起见，没有本质影响）
<span class="math display">\[\dot{\mathbf{z}}=\begin{bmatrix}
        \dot{z}_1\\\dot{z}_2
    \end{bmatrix}=\underbrace{\begin{bmatrix}
        \sigma+\mathrm{j}\omega&amp;0\\
        0&amp;\sigma-\mathrm{j}\omega
    \end{bmatrix}}_A\begin{bmatrix}
        {z}_1\\{z}_2
    \end{bmatrix}
    +\underbrace{\begin{bmatrix}
        1/2\\1/2
    \end{bmatrix}}_bu\]</span> <span
class="math display">\[y=\underbrace{\begin{bmatrix}
        a-\mathrm{j}\frac{a\sigma+b}{\omega}&amp;a+\mathrm{j}\frac{a\sigma+b}{\omega}
    \end{bmatrix}}_c{\mathbf{z}}\]</span>
矩阵中含有复数值。为将其变为实数，考虑使用变换矩阵。</p>
<p>观察<span class="math inline">\(y\)</span>的形式，会发现<span
class="math inline">\(y\)</span>等于一个系数乘以一个状态变量，再加上同一个系数的共轭乘以另一个状态变量。
因为<span
class="math inline">\(y\)</span>是实的，可以认为两个状态变量是“共轭”的。从状态方程中，两个状态相应于共轭的特征根也可以感受到这一点。
<span
class="math inline">\(y\)</span>的现有形式，其实等于系数的实部乘以状态变量的“实部”加上系数的虚部乘以状态变量的“虚部”（的两倍）。
如果能写成这样的形式，那么系数就都是实的了。因此，为了提取两个状态变量的“实部”和“虚部”，可以令新状态是
<span class="math display">\[\begin{align}
    x_1&amp;=z_1+z_2\\
    x_2&amp;=\mathrm{j}(z_1-z_2)
\end{align}\]</span> 那么变换就是 <span
class="math display">\[\mathbf{x}=\begin{bmatrix}
    x_1\\x_2
\end{bmatrix}=\begin{bmatrix}
    1&amp;1\\\mathrm{j}&amp;-\mathrm{j}
\end{bmatrix}\mathbf{z}\]</span> 将变换矩阵记为<span
class="math inline">\(P\)</span>并作用于原系统得到 <span
class="math display">\[\bar{A}=PAP^{-1}=\begin{bmatrix}
    1&amp;1\\\mathrm{j}&amp;-\mathrm{j}
\end{bmatrix}\begin{bmatrix}
    \sigma+\mathrm{j}\omega&amp;0\\
    0&amp;\sigma-\mathrm{j}\omega
\end{bmatrix}\begin{bmatrix}
    \frac12&amp;-\frac12\mathrm{j}\\\frac12&amp;\frac12\mathrm{j}
\end{bmatrix}=\begin{bmatrix}
    \sigma+\mathrm{j}\omega&amp;\sigma-\mathrm{j}\omega\\
    \sigma\mathrm{j}-\omega&amp;-\sigma\mathrm{j}-\omega
\end{bmatrix}\begin{bmatrix}
    \frac12&amp;-\frac12\mathrm{j}\\\frac12&amp;\frac12\mathrm{j}
\end{bmatrix}=\begin{bmatrix}
    \sigma&amp;\omega\\
    -\omega&amp;\sigma
\end{bmatrix}\]</span> <span
class="math display">\[\bar{b}=Pb=\begin{bmatrix}
    1&amp;1\\\mathrm{j}&amp;-\mathrm{j}
\end{bmatrix}\begin{bmatrix}
    1/2\\1/2
\end{bmatrix}=\begin{bmatrix}
    1\\0
\end{bmatrix}\]</span> <span
class="math display">\[\bar{c}=cP^{-1}=\begin{bmatrix}
    a-\mathrm{j}\frac{a\sigma+b}{\omega}&amp;a+\mathrm{j}\frac{a\sigma+b}{\omega}
\end{bmatrix}\begin{bmatrix}
    \frac12&amp;-\frac12\mathrm{j}\\\frac12&amp;\frac12\mathrm{j}
\end{bmatrix}=\begin{bmatrix}
    a&amp;-\frac{a\sigma+b}{\omega}
\end{bmatrix}\]</span> 这样各矩阵就都是实矩阵了，便于分析。注意到<span
class="math inline">\(\bar c\)</span>（记录了两个状态加权得到<span
class="math inline">\(y\)</span>的系数）的确由原来系数的实部和虚部构成。</p>
<p>当然状态的变换还有别的取法。为了得到讲义上面的形式，取 <span
class="math display">\[\begin{align}
    x_1&amp;=\mathrm{j}(z_2-z_1)\\
    x_2&amp;=z_1+z_2
\end{align}\]</span> 那么变换后各矩阵是 <span
class="math display">\[\bar{A}=PAP^{-1}=\begin{bmatrix}
    -\mathrm{j}&amp;\mathrm{j}\\1&amp;1
\end{bmatrix}\begin{bmatrix}
    \sigma+\mathrm{j}\omega&amp;0\\
    0&amp;\sigma-\mathrm{j}\omega
\end{bmatrix}\begin{bmatrix}
    \frac12\mathrm{j}&amp;\frac12\\-\frac12\mathrm{j}&amp;\frac12
\end{bmatrix}=\begin{bmatrix}
    -\sigma\mathrm{j}+\omega&amp;\sigma\mathrm{j}+\omega\\
    \sigma+\mathrm{j}\omega&amp;\sigma-\mathrm{j}\omega
\end{bmatrix}\begin{bmatrix}
    \frac12\mathrm{j}&amp;\frac12\\-\frac12\mathrm{j}&amp;\frac12
\end{bmatrix}=\begin{bmatrix}
    \sigma&amp;\omega\\
    -\omega&amp;\sigma
\end{bmatrix}\]</span> <span
class="math display">\[\bar{b}=Pb=\begin{bmatrix}
    -\mathrm{j}&amp;\mathrm{j}\\1&amp;1
\end{bmatrix}\begin{bmatrix}
    1/2\\1/2
\end{bmatrix}=\begin{bmatrix}
    0\\1
\end{bmatrix}\]</span> <span
class="math display">\[\bar{c}=cP^{-1}=\begin{bmatrix}
    a-\mathrm{j}\frac{a\sigma+b}{\omega}&amp;a+\mathrm{j}\frac{a\sigma+b}{\omega}
\end{bmatrix}\begin{bmatrix}
    \frac12\mathrm{j}&amp;\frac12\\-\frac12\mathrm{j}&amp;\frac12
\end{bmatrix}=\begin{bmatrix}
    \frac{a\sigma+b}{\omega}&amp;a
\end{bmatrix}\]</span> 同样各矩阵都化为实矩阵。</p>