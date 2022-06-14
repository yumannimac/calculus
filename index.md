<script src="main.js"></script>
  <script type="text/javascript" id="MathJax-script" async
    src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
    </script>
  <script>
    MathJax = {
      loader: { load: ['[tex]/physics','[tex]/newcommand','[tex]/mathtools'] },
      tex: {
        inlineMath: [['$', '$'], ['\\(', '\\)']],
        packages: { '[+]': ['physics', 'newcommand','mathtools'] },
      },
      chtml: {
        matchFontHeight: false
      }
    };
  </script>

$$
\newcommand{\la}{\lambda}
\newcommand{\e}{\varepsilon}
\renewcommand{\l}{\left}
\renewcommand{\r}{\right}
\newcommand{\del}{\partial}
\newcommand{\q}{\quad}
\newcommand{\qq}{\qquad}
\newcommand{\dis}{\displaystyle}
\newcommand{\dc}{\Leftrightarrow}
\def\rank{\mathrm{rank}}
\newcommand{\hr}{\hrulefill}
\newcommand{\m}{\item}
\newcommand{\drac}[2]{\dfrac{#1}{#2}}
\newcommand{\delu}[3][]{\drac{\partial^{#1} {#2}}{\partial {#3}^{#1}}}
\newcommand{\bm}[1]{\boldsymbol{#1}}
$$



# 微分積分学

### 一様収束

::: theorem
[]{#項別積分可能性
label="項別積分可能性"}（項別積分可能性）$f_n\left(x\right)$を$[a,b]$上の連続関数の列で$f\left(x\right)$に一様収束するものとする。$a \leq c \leq x\leq b$なる$\forall c,x$に対し$F_n\left(x\right) =\int_{c}^{x} f_n\left(t\right) \, dt$も
$F\left(x\right) =\int_{c}^{x} f\left(t\right) \, dt$に一様収束する。
:::

::: proof
*Proof.*

$$
\begin{aligned}
 \left|F_n\left(x\right) -F\left(x\right) \right| 
 &=\, \left|\int_{c}^{x} f_n\left(t\right) \, dt -\int_{c}^{x} f\left(t\right) \, d t \right| \\
 &\leq\, 
  \int_{c}^{x} \left|f_n\left(t\right) -f\left(t\right) \right| \, d t 
 \leq \int_{c}^{x} \sup_{c\leq t \leq x}\left|f_n\left(t\right) -f\left(t\right) \right|\, d t 
 \end{aligned}
$$

より

$$
\begin{aligned}
 0 \leq \sup_{a\leq x\leq b}\left|F_n\left(x\right) -F\left(x\right) \right| \leq 
 \sup_{a\leq x\leq b}\left(x-c\right) \sup_{c\leq t\leq x}\left|f_n\left(t\right) -f\left(t\right) \right| 
 \end{aligned}
$$

一様収束性より

$$
\begin{aligned}
  \lim_{n \to \infty} \sup_{c\leq t\leq x}\left|f_n\left(t\right) -f\left(t\right) \right| =0
 \end{aligned}
$$

であるからはさみうちの原理より

$$
\begin{aligned}
 \lim_{n \to \infty} \sup_{a\leq x\leq b}\left|F_n\left(x\right) -F\left(x\right) \right| =0
 \end{aligned}
$$

すなわちa

$$
\int_{c}^{x} \lim_{n \to \infty}f_n\left(t\right) \, d t
 =\lim_{n \to \infty}  \int_{c}^{x} f_n\left(t\right) \, d t
$$

であるから一様収束するときは項別積分可能であることが示された。 ◻
:::

#### 整級数の一様収束性の例

たとえば$f_n\left(x\right) =\displaystyle \sum_{i=0}^{n} (-x)^i$，$f\left(x\right) =\dfrac{1}{1+x}$とする。$0<t<1$とすると
$-t<x<t$において

$$
\begin{aligned}
\left|f_n\left(x\right) -f\left(x\right) \right| =\left|\dfrac{1-\left(-x\right)^n }{1-\left(-x\right) }-\dfrac{1}{1+x} \right| =\dfrac{\left|x\right| ^n}{1+x}<\dfrac{t^n}{1-t}\end{aligned}
$$

である。よって

$$
\begin{aligned}
0\leq \sup_{-t<x<t}\left|f_n\left(x\right) -f\left(x\right) \right|<\dfrac{t^n}{1-t}\end{aligned}
$$

であり最右辺は$n \to \infty$で$0$に収束するのではさみうちの原理より

$$
\begin{aligned}
\lim_{n \to \infty}\sup_{-t<x<t}\left|f_n\left(x\right) -f\left(x\right) \right|=0 \end{aligned}
$$

したがって$-t<x<t$において$f_n\left(x\right)$は$f\left(x\right)$に一様収束する。$\left[0,x\right]$において項別積分すると

$$
\begin{aligned}
\lim_{n \to \infty} \int_{0}^{x} \sum_{i=0}^{n} \left(-s\right) ^i \, d s=
 \int_{0}^{x} \dfrac{1}{1+s}\, ds \end{aligned}
$$

$t$は自由に動かせることに注意して$-1<x<1$において

$$
\begin{aligned}
\log \left(1+x\right) =\sum_{i=0}^{\infty} \left(-1\right) ^i\dfrac{x^{i+1}}{i+1}=x-\dfrac{1}{2}x^2+\dfrac{1}{3}x^3-\dots\end{aligned}
$$

である。

::: theorem
[]{#項別微分可能性 label="項別微分可能性"}（項別微分可能性）
$F_n\left(x\right)$を$\left[a,b\right]$上の連続関数の列で$F\left(x\right)$に収束するものとする。$F_{n}'\left(x\right)$が$f\left(x\right)$に一様収束するならば$F'\left(x\right)=f\left(x\right)$である。
:::

::: proof
*Proof.*

$$
\begin{aligned}
 F\left(x\right) -F\left(c\right) 
 &=\, \lim_{n \to \infty} \left\{ F_n\left(x\right) -F_n\left(c\right) \right\} =\lim_{n \to \infty} \int_{c}^{x} F_n'\left(t\right) \, d t=\int_{c}^{x} \lim_{n \to \infty} F_n'\left(t\right) \, d t \\
 &=\, \int_{c}^{x} f\left(t\right) \, d t 
 \end{aligned}
$$

の両辺を微分するだけ。 ◻
:::

::: theorem
[]{#絶対収束する級数の収束性
label="絶対収束する級数の収束性"}（絶対収束する級数の収束性）
$\displaystyle \sum_{n=0}^{\infty} \left|a_n\right|$が収束するならば$\displaystyle \sum_{n=0}^{\infty} a_n$も収束する。
:::

::: proof
*Proof.* $a_{n}^{+}=
 \begin{dcases}
 a_n &\left(a_n\geq 0\right) 
 \\ 0&\left(a_n<0\right) 
 \end{dcases}$ ， $a_{n}^{-}=
 \begin{dcases}
 0 &\left(a_n\geq 0\right) 
 \\ -a_n&\left(a_n<0\right) 
 \end{dcases}$ とする。\
$a_{n}^{+}，a_{n}^{-}\geq 0$であり$a_n=a_n^+-a_n^-,|a_n|=a_n^++a_n^-$である。$\displaystyle \sum_{n=0}^{\infty} \left|a_n\right| =S$とする。

$$
S=\sum_{n=0}^{\infty} \left|a_n\right| =\sum_{n=0}^{\infty} a_n^+
 +\sum_{n=0}^{\infty} a_n^-\geq \sum_{n=0}^{\infty} a_n^+
$$

より$\sum_{}^{} a_n^+$は有界な正項級数であるから収束する。同様に$\sum_{}^{} a_n^-$も収束する。収束値をそれぞれ$S^+,S^-$とおくと

$$
\sum_{n=0}^{\infty} a_n=\sum_{n=0}^{\infty} \left(a_n^+-a_n^-\right) =S^+-S^-
$$

であるから収束する。よって示された。 ◻
:::

### 収束判定法

::: theorem
[]{#コーシーの収束判定法 label="コーシーの収束判定法"}
（コーシーの収束判定法）

$$
\lim_{n \to \infty}\sup_{m>n}\sqrt[m]{\left|a_m\right| } =l\text{が存在するとき} \sum_{n=0}^{\infty} a_n\text{は}
 \begin{dcases}
 \text{収束する}&\left(0<l<1\text{のとき}\right) \\ 
 \text{発散する}&\left(l>1\text{のとき}\right) 
 \end{dcases}
$$

:::

::: proof
*Proof.* 　

(i) $0<l<1$のとき\
極限の定義より$l<t<1$となる$t$を考えると$n\geq N_0$ならば$\sqrt[n]{\left|a_n\right| }<t$すなわち$\left|a_n\right| <t^n$となる$N_0\in \mathbb{Z}_{\geq 0}$が存在する。$N>N_0$として


$$
\begin{aligned}
 \sum_{n=0}^{N} \left|a_n\right| =
 \sum_{n=0}^{N_0-1} \left|a_n\right| 
 +\sum_{n=N_0}^{N} \left|a_n\right| <
 \sum_{n=0}^{N_0-1} \left|a_n\right| 
 +\sum_{n=N_0}^{N}t^n<\sum_{n=0}^{N_0-1} \left|a_n\right| +t^{N_0}\dfrac{1}{1-t}
 \end{aligned}
$$

より$\sum_{}^{} |a_n|$は有界な正項級数なので収束する。よって$\sum_{}^{} a_n$は絶対収束するので収束する。

(ii) $l>1$のとき\
 $1<t<l$なる$t$を考えると$n\geq N_0$ならば$\sqrt[n]{\left|a_n\right| }>t$すなわち$\left|a_n\right| >t^n$となる$N_0\in \mathbb{Z}_{\geq 0}$が存在する。$n \to \infty$で$t^n$は発散するので追い出しの原理より$\left|a_n\right|$も発散。よって$a_n$も発散するので$\sum_{}^{} a_n$は発散する。

 ◻
:::

::: theorem
[]{#ダランベールの収束判定法
label="ダランベールの収束判定法"}（ダランベールの収束判定法）

$$
\lim_{n \to \infty}\left|\dfrac{a_{n+1}}{a_n}\right| =l\text{が存在するならば} \sum_{n=0}^{\infty} a_n\text{は}
 \begin{dcases}
 \text{収束する}&\left(0<l<1\text{のとき}\right) \\ 
 \text{発散する}&\left(l>1\text{のとき}\right) 
 \end{dcases}
$$

:::

::: proof
*Proof.* 　

(i) $0<l<1$のとき\
極限の定義より$l<t<1$となる$t$を考えると$n\geq N_0$ならば$\left|\dfrac{a_{n+1}}{a_n}\right| <t$すなわち$\left|a_{n+1}\right| <t\left|a_{n}\right|$となる$N_0\in \mathbb{Z}_{\geq 0}$が存在する。$\left|a_n\right|<t\left|a_{n-1}\right| <\dots<\left|a_{N_0}\right| t^{n-N_0}$
である。 $N>N_0$として

$$
\begin{aligned}
 \sum_{n=0}^{N} \left|a_n\right| =
 \sum_{n=0}^{N_0-1} \left|a_n\right| 
 +\sum_{n=N_0}^{N} \left|a_n\right| 
 <\sum_{n=0}^{N_0-1} \left|a_n\right| 
 +\left|a_{N_0}\right| \sum_{n=N_0}^{N}t^{n-N_0}
 <\sum_{n=0}^{N_0-1} \left|a_n\right| +\dfrac{|a_{N_0}|}{1-t}
 \end{aligned}
$$

より$\sum_{}^{} |a_n|$は有界な正項級数なので収束する。よって$\sum_{}^{} a_n$は絶対収束するので収束する。

(ii) $l>1$のとき\
 $1<t<l$なる$t$を考えると$n\geq N_0$ならば$\left|\dfrac{a_{n+1}}{a_n}\right| >t$となる$N_0\in \mathbb{Z}_{\geq 0}$が存在する。
 $\left|a_n\right|>t\left|a_{n-1}\right| >\dots>\left|a_{N_0}\right| t^{n-N_0}$である
 $n \to \infty$で$t^n$は発散するので追い出しの原理より$\left|a_n\right|$も発散。よって$a_n$も発散するので$\sum_{}^{} a_n$は発散する。

 ◻
:::

::: theorem
[]{#コーシーの収束半径 label="コーシーの収束半径"}（コーシーの収束半径）
$\sum_{}^{} a_nx^n$の収束半径$r$は
$\displaystyle \lim_{n \to \infty}\displaystyle \sup_{m>n}\sqrt[m]{\left|a_m\right| } =l$として$r=\dfrac{1}{l}$である。
:::

::: proof
*Proof.* 　

(i) $\left|x\right| <r$のとき\
$x=0$では自明に収束。$0<\left|x\right|<r$とする。$0<l<\dfrac{1}{\left|x\right| }$である。$n\geq N_0$ならば$\sqrt[n]{\left|a_n\right| }<\dfrac{1}{2}\left(l+\dfrac{1}{\left|x\right| }\right)$となる$N_0\in \mathbb{Z}_{\geq 0}$が存在する。このもとで


$$
\begin{aligned}
 \sum_{n=0}^{N} \left|a_nx^n\right| 
 &=\, \sum_{n=0}^{N_0-1} \left|a_nx^n\right| 
 +\sum_{n=N_0}^{N} (\sqrt[n]{\left|a_n\right|  }\left| x\right|)^n
 \\
 &\leq\, \sum_{n=0}^{N_0-1} \left|a_nx^n\right| +\sum_{n=N_0}^{N} 
 \left(\dfrac{1}{2}\left(l+\dfrac{1}{\left|x\right| }\right) \bigg/\dfrac{1}{\left|x\right| }\right)
 ^n
 \end{aligned}
$$

であり$\left(\dfrac{1}{2}\left(l+\dfrac{1}{\left|x\right| }\right) \bigg/\dfrac{1}{\left|x\right| }\right)<1$より$\sum_{}^{}a_nx^n$は絶対収束するので収束する。

(ii) $\left|x\right| >r$のとき\
 $0<\dfrac{1}{\left|x\right| }<l$である。任意の$N_0\in \mathbb{Z}_{\geq 0}$に対して$n>N_0$かつ$\sqrt[n]{\left|a_n\right| }>\dfrac{1}{2}\left(l+\dfrac{1}{\left|x\right| }\right)$となる$n$が存在する。すなわち$\left|a_nx^n\right| =(\sqrt[n]{\left|a_n\right|  }\left| x\right|)^n=\left(\dfrac{1}{2}\left(l+\dfrac{1}{\left|x\right| }\right) \bigg/\dfrac{1}{\left|x\right| }\right)
  ^n>1$になるような$n>N_0$が任意の$N_0\in \mathbb{Z}_{\geq 0}$に対して存在するので数列$\left\{ a_nx^n \right\}$は$0$に収束しない。したがって級数も発散する。

 ◻
:::

::: theorem
[]{#ダランベールの収束半径
label="ダランベールの収束半径"}（ダランベールの収束半径）
$\sum a_nx^n$の収束半径$r$は存在するならば$r=\displaystyle \lim_{n \to \infty}\left|\dfrac{a_n}{a_{n+1}}\right|$である。
:::

::: proof
*Proof.* 　

(i) $0 \leq x< r$のとき\
$n\geq \exists N_0 \Rightarrow \left|\dfrac{a_n}{a_{n+1}}\right| >\dfrac{\left|x\right| +r}{2} \Leftrightarrow \left|a_{n+1}\right| <\left( 1\bigg/\dfrac{\left|x\right| +r}{2} \right)\left|a_n\right|$よりこれを繰り返し用いて$\left|a_n\right| <\left( 1\bigg/\dfrac{\left|x\right| +r}{2} \right)^{n-N_0}\left|a_{N_0}\right|$が得られる。


$$
\begin{aligned}
 \sum_{n=0}^{N} \left|a_nx^n\right| <\sum_{n=0}^{N_0-1} \left|a_nx^n\right|+\sum_{n=N_0}^{N} \left( |x|\bigg/\dfrac{\left|x\right| +r}{2} \right)^{n-N_0}\left|a_{N_0}\right|
 \end{aligned}
$$

であり$\left( |x|\bigg/\dfrac{\left|x\right| +r}{2} \right)<1$より$\sum_{}^{}a_nx^n$は絶対収束するので収束する。

(ii) $|x|>r$のとき\
 $n\geq \exists N_0 \Rightarrow \left|\dfrac{a_n}{a_{n+1}}\right| <\dfrac{\left|x\right| +r}{2} \Leftrightarrow \left|a_{n+1}\right| >\left( 1\bigg/\dfrac{\left|x\right| +r}{2} \right)\left|a_n\right|$よりこれを繰り返し用いて$\left|a_n\right| >\left( 1\bigg/\dfrac{\left|x\right| +r}{2} \right)^{n-N_0}\left|a_{N_0}\right|$が得られる。よって


$$
\begin{aligned}
  \left|a_nx^n\right| >\left( |x|\bigg/\dfrac{\left|x\right| +r}{2} \right)^{n-N_0}\left|a_{N_0}\right| 
  \end{aligned}
$$

 であり$|x|\bigg/\dfrac{\left|x\right| +r}{2}>1$より左辺は発散する。追い出しの原理より$a_nx^n$が$0$に収束することはないので発散する。

 ◻
:::

### $e$の導入

::: theorem
[]{#eの存在 label="eの存在"}（$e$の存在）
$e:=\displaystyle \lim_{n \to \infty}\left(1+\dfrac{1}{n}\right) ^n$が存在することを示す。
:::

::: proof
*Proof.* $a_n=\left(1+\dfrac{1}{n}\right) ^n$とする。\
単調増加性\
二項定理より

$$
\begin{aligned}
 a_n 
 &=\, \sum_{k=0}^{n} \binom{n}{k}\dfrac{1}{n^k}
 =\sum_{k=0}^{n} \dfrac{n\left(n-1\right)\left(n-2\right) \dots\left(n-k+1\right) }{k!n^k} \\
 &=\, \sum_{k=0}^{n} \dfrac{1}{k!}\left(1-\dfrac{1}{n}\right) \left(1-\dfrac{2}{n}\right) \dots\left(1-\dfrac{k-1}{n}\right) \\
 &=\, 2+\dfrac{1}{2!}\left(1-\dfrac{1}{n}\right) +\dfrac{1}{3!}\left(1-\dfrac{1}{n}\right) \left(1-\dfrac{2}{n}\right) +\dots+\dfrac{1}{n!}\left(1-\dfrac{1}{n}\right) \dots\left(1-\dfrac{n-1}{n}\right) 
 \\
 a_{n+1}
 &=\, \sum_{k=0}^{n+1} \dfrac{1}{k!}\left(1-\dfrac{1}{n+1}\right) \left(1-\dfrac{2}{n+1}\right) \dots\left(1-\dfrac{k-1}{n+1}\right) \\
 &>\, \sum_{k=0}^{n}\dfrac{1}{k!} \left(1-\dfrac{1}{n+1}\right) \left(1-\dfrac{2}{n+1}\right) \dots\left(1-\dfrac{k-1}{n+1}\right) 
 \\
 &>\,\sum_{k=0}^{n} \dfrac{1}{k!}\left(1-\dfrac{1}{n}\right) \left(1-\dfrac{2}{n}\right) \dots\left(1-\dfrac{k-1}{n}\right)=a_n
 \end{aligned}
$$

であるから$\left\{ a_n \right\}$は単調増加。\
有界性\

$$
\begin{aligned}
 \forall n\ a_n 
 &=\, 
 \sum_{k=0}^{n} \dfrac{1}{k!}\left(1-\dfrac{1}{n}\right) \left(1-\dfrac{2}{n}\right) \dots\left(1-\dfrac{k-1}{n}\right) 
 <\sum_{k=0}^{n} \dfrac{1}{k!}\\
 &=\, 
 1+\dfrac{1}{1}+\dfrac{1}{2}+\dfrac{1}{2\cdot 3}+\dfrac{1}{2\cdot 3\cdot 4}+\dots \\
 &<\, 1+\dfrac{1}{1}+\dfrac{1}{2}+\dfrac{1}{2\cdot 2}+\dfrac{1}{2\cdot 2\cdot 2}+\dots=3
 \end{aligned}
$$

以上より$\left\{ a_n \right\}$は有界な単調増加数列であるから収束する。 ◻
:::

### マクローリン展開

$k\geq 1$のとき

$$
\begin{aligned}
\dfrac{d}{dt}\left\{ \dfrac{\left(x-t\right) ^k}{k!}f^{\left(k\right) }\left(t\right) \right\}=
-\dfrac{\left(x-t\right) ^{k-1}}{\left(k-1\right) !}f^{\left(k\right) }\left(t\right) 
+\dfrac{\left(x-t\right) ^{k}}{k !}f^{\left(k+1\right)}\left(t\right) \end{aligned}
$$

に注意すると

$$
\begin{aligned}
\dfrac{d}{dt}\left[ f\left(t\right) +\sum_{k=1}^{n-1} \left\{ \dfrac{\left(x-t\right) ^k}{k!}f^{\left(k\right) }\left(t\right) \right\} \right]
=\dfrac{\left(x-t\right) ^{n-1 }}{\left(n-1\right) !}f^{\left(n\right)}\left(t\right)\end{aligned}
$$

両辺$\left[a,x\right]$において積分すると

$$
\begin{aligned}
f\left(x\right) -f\left(a\right) -
\sum_{k=1}^{n-1} \left\{ \dfrac{\left(x-a\right) ^k}{k!}f^{\left(k\right) }\left(a\right) \right\} 
=\int_{a}^{x} \dfrac{\left(x-t\right) ^{n-1 }}{\left(n-1\right) !}f^{\left(n\right)}\left(t\right)\, dt \end{aligned}
$$

よって

$$
\begin{aligned}
f\left(x\right) =\sum_{k=0}^{n-1} \left\{ \dfrac{\left(x-a\right) ^k}{k!}f^{\left(k\right) }\left(a\right) \right\} +R_n\left(x\right) \end{aligned}
$$

と書ける。

#### 剰余項の計算 {#剰余項の計算 .unnumbered}

積分の平均値の定理より$c\in [a,x]$として

$$
\begin{aligned}
R_n\left(x\right) =\int_{a}^{x} \dfrac{\left(x-t\right) ^{n-1 }}{\left(n-1\right) !}f^{\left(n\right)}\left(t\right)\, dt =\int_{a}^{x} \dfrac{\left(x-t\right) ^{n-1 }}{\left(n-1\right) !}f^{\left(n\right)}\left(c\right)\, dt 
=\dfrac{\left(x-a\right) ^n}{n!}f^{\left(n\right) }\left(c\right)  \end{aligned}
$$

となる$c$が存在する。最右辺はラグランジュの剰余項である。より一般に$\left(x-t\right) ^{n-p}f^{\left(n\right) }\left(t\right)$に平均値の定理を使うと

$$
\begin{aligned}
R_n\left(x\right) =\int_{a}^{x} \dfrac{\left(x-c\right) ^{n-p }\left(x-t\right) ^{p-1}}{\left(n-1\right) !}f^{\left(n\right)}\left(c\right)\, dt 
=\dfrac{\left(x-a\right) ^p}{p\left(n-1\right) !}\left(x-c\right) ^{n-p}f^{\left(n\right) }\left(c\right)\end{aligned}
$$

$c=a+\theta \left(x-a\right)$とおくと$0\leq \theta \leq 1$であって

$$
\begin{aligned}
R_n\left(x\right) =\dfrac{\left(x-a\right) ^n}{p\left(n-1\right) !}\left(1-\theta \right) ^{n-p}f^{\left(n\right) }\left(c\right)\end{aligned}
$$

である。コーシーの剰余項である。

### 陰関数定理

::: theorem
[]{#中間値の定理 label="中間値の定理"}（中間値の定理）
$f:\mathbb{R}\to \mathbb{R}$として$f$は閉区間$[a,b]$上連続とする。$f\left(a\right)$と$f\left(b\right)$の間にある任意の$k$に対し$a\leq c\leq b$かつ$f\left(c\right) =k$となる$c$が存在する。
:::

::: proof
*Proof.*
$f\left(a\right) \leq f\left(b\right)$としても一般性を失わない。$c=\displaystyle \sup_{a\leq x\leq b}\left\{ x \:\middle|\: f\left(x\right) \leq k \right\}$とする。$f\left(c\right) \neq k$になると仮定して矛盾を示す。
$f\left(c\right) >k$としても$f\left(c\right) <k$としても($f\left(c\right) >k$のときは$\sup_{}$の性質より)$\displaystyle \lim_{n \to \infty}x_n=c$かつ$f\left(x_n\right) \leq k$となる数列$\left\{ x_n \right\}$が存在する。連続性より$f\left(x_n\right) \to f\left(c\right) \leq k$となる。一方$b$から$c$に近づく数列$\left\{ y_n \right\}$を考えると$f\left(y_n\right) >k$であり連続性より$f\left(y_n\right) \to f\left(c\right) \geq k$となる。
以上より$f\left(c\right) =k$となるがこれは仮定に矛盾する。背理法より示された。 ◻
:::

以降，$X$をベクトルとしてベクトル値関数$f(X)$のヤコビアンを$\delu{f}{x}$のように表すことにする。

::: theorem
[]{#陰関数定理 label="陰関数定理"}（陰関数定理）
$X=\left(x_1,\dots x_k\right)$，$Y=\left(y_1,\dots y_m\right)$とする$\left(k,m\in \mathbb{Z}_{\geq 1}\right)$。$\left(A,B\right) \in \left(X,
 Y\right)$において$m$個の関数$f_{1}\left(X,Y\right),\dots ,f_{m}\left(X,Y\right)$が

(i) $f_1=\dots=f_{m}=0$

(ii) $\left|\dfrac{\del f}{\del y}\right|=\vmat{
  \delu{f_1}{y_1}& \dots & \delu{f_1}{y_m}\\
  \vdots& \ddots & \vdots\\
  \delu{f_m}{y_1}& \dots& \delu{f_m}{y_m} 
  }\neq 0$

を満たすならばある$\varepsilon >0$が存在して$\left|X-A\right| <\varepsilon$上で$\varphi _1\left(X\right) ,\dots ,\varphi _m\left(X\right)$が存在して以下を満たす。

(1) $B=\left(\varphi _1\left(A\right) ,\dots , \varphi _m\left(A\right) \right)$

(2) $f_j\left(X,\varphi _1\left(X\right) ,\dots ,\varphi _m\left(X\right) \right) =0　\left(j=1,\dots, m\right)$

上記の命題を$P\left(k,m\right)$とおく。
:::

#### 証明 {#証明 .unnumbered}

##### $P\left(k,1\right)$について {#plk1rについて .unnumbered}

仮定は$X=\left(x_1,\dots ,x_k\right)，Y=y_1=y, A=\left(a_1,\dots , a_k\right)$，$B=b_1=b$として$\left(X,Y\right) =\left(A,b\right)$において

(i) $f\left(A,b\right) =0$

(ii) $\delu{f}{y}\neq 0$

であることである。(ii)よりある$\delta \neq 0$であって$f\left(A,b_1-\delta\right)<0< f\left(A,b_1+\delta\right)$となるものが存在する。$\delta$に対応する$\varepsilon >0$をうまくとれば$\left|X-A\right| <\varepsilon$ならば

$$
f\left(X,b-\delta \right) <0<f\left(X,b+\delta \right)
$$

とすることができる。中間値の定理（）と$\delu{f}{y}$の符号が一定であることにより$\left|X-A\right| <\varepsilon$のもとで

(1) $b=\varphi \left(X\right)$

(2) $f\left(X,\varphi \left(X\right) \right) =0$

を満たす$\varphi\left(X\right)$ が$b-\delta$と$b-\delta$
の間にただ一つ存在する。よって$P(k,1)$が示された。（証明終）

##### $\varphi$の連続性 {#varphiの連続性 .unnumbered}

$\left[b-\delta ,b+\delta \right]=I$とする。$\varphi \left(X_0+H\right)$が$H\to O$で$\varphi \left(X_0\right)$に収束しないと仮定すると
任意の$n$に対して$\left|X_0+H_n-A\right| <\varepsilon$かつ

$$
\left|\varphi \left(X_0+H_n\right) -\varphi \left(X_0\right) \right| \geq \varepsilon '
$$

を満たす，$O$に収束するベクトル列$H_n\in \mathbb{R}^k$と$\varepsilon '>0$が存在する。
任意の$n$に対し$\varphi \left(X_0+H_n\right) \in I$が成り立つので$\left\{ \varphi \left(X_0+H_n\right) \right\}$の部分列$\left\{ \varphi \left(X_0+H_{n_l}\right) \right\}$で$I$内のある値$\alpha$に収束するものが存在する。
任意の$l$に対し$\left|\varphi \left(X_0+H_{n_l}\right) -\varphi \left(X_0\right) \right| \geq \varepsilon '$であることより$\alpha \neq \varphi \left(X_0\right)$であるが
$f$の連続性から

$$
f\left(X_0,\alpha \right) =\lim_{l \to \infty} f\left(X_0+H_{n_l},\varphi \left( X_0+H_{n_l} \right)\right)=0
$$

より$f\left(X_0,y_0\right) =0$なる$y_0\in I$が$y_0=\varphi \left(X_0\right)$しかないことから$\alpha =\varphi \left(X_0\right)$ということになってしまい矛盾。

##### $\varphi$が微分可能であること {#varphiが微分可能であること .unnumbered}

$x_1$で偏微分可能なことを示す。$\left(x_2,\dots,x_k \right) =X'$とおく。\
テイラーの定理より$k_1=\varphi \left(x_1+h_1,X'\right) -\varphi \left(x_1,X' \right)$として

$$
\begin{aligned}
&f\left(x_1+h_1,X',\varphi \left(x_1+h_1,X'\right) \right) \\ 
&=\, f\left(x_1,X',\varphi (x_1,X')\right) 
+f_{x_1}\left(x_1+\theta h_1,X',\varphi(x_1,X')+\theta k_1\right)h_1 \\
&\qq 
+f_{y }\left(x_1+\theta h_1,X',\varphi(x_1,X')+\theta k_1\right)k_1 \end{aligned}
$$

である。
$f\left(x_1+h_1,X',\varphi \left(x_1+h_1,X'\right) \right) = f\left(x_1,X',\varphi (x_1,X')\right) =0$より

$$
\begin{aligned}
\dfrac{\varphi \left(x_1+h_1,X'\right) -\varphi \left(x_1,X'\right) }{h_1}=\dfrac{k_1}{h_1}=-\dfrac{f_{x_1}\left(x_1+\theta h_1,X',\varphi(x_1,X')+\theta k_1\right)}{f_{y }\left(x_1+\theta h_1,X',\varphi(x_1,X')+\theta k_1\right)}\end{aligned}
$$

$\varphi$の連続性より$h_1\to 0$で$k_1\to 0$。よって$f_{x_1},f_{y}$の連続性より

$$
\begin{aligned}
\lim_{h_1 \to 0}\dfrac{\varphi \left(x_1+h_1,X'\right) -\varphi \left(x_1,X'\right) }{h_1}
=-\dfrac{f_{x_1}\left(x_1,X',\varphi(x_1,X')\right)}{f_{y }\left(x_1,X',\varphi(x_1,X')\right)}\end{aligned}
$$

$x_2,\dots,x_k$も同様に考えて$i=1,2,\dots,k$において

$$
\begin{aligned}
\delu{\varphi }{x_i}=-\dfrac{f_{x_i}\left(X,\varphi(X)\right)}{f_{y }\left(X,\varphi(X)\right)}\end{aligned}
$$

となるので$\varphi$は微分可能であることが示された。

##### $P\left(k,m\right)$について {#plkmrについて .unnumbered}

$\forall k\ P\left(k,1\right)$が真であることをもとにして$P\left(k+1,m\right)$から$P\left(k,m+1\right)$を示すことで帰納法を完成させる。
$P\left(k+1,m\right)$が真であると仮定する。$P\left(k,m+1\right)$の仮定は

(i) $f_{j}(A,b_{1},\dots,b_{m},b_{m+1})=0 \quad(j=1,\dots,m,m+1)$

(ii) $(A,b_{1},\dots,b_{m},b_{m+1})$において

$$
\begin{aligned}
  \left|\dfrac{\partial f}{\partial y}\right|=\begin{vmatrix}
  \dfrac{\partial f_{1} }{\partial y_{1}} & \dots &\dfrac{\partial f_{1} }{\partial y_{m}}
  &\dfrac{\partial f_{1} }{\partial y_{m+1}}\\
  \vdots &\ddots &\vdots &\vdots\\
  \dfrac{\partial f_{m} }{\partial y_{1}}&\dots & \dfrac{\partial f_{m} }{\partial y_{m}}&\vdots \\
  \dfrac{\partial f_{m+1} }{\partial y_{1}}&\dots &\dots&\dfrac{\partial f_{m+1} }{\partial y_{m+1}} 
  \end{vmatrix}
  \neq 0
  \end{aligned}
$$


である。このとき(2)の余因子展開から，うまく$y_{1},\dots,y_{m+1}$を選べば

$$
\dfrac{\partial f_{m+1} }{\partial y_{m+1}} 
 \begin{vmatrix}
 \delu{f_1}{y_1}& \dots & \delu{f_1}{y_m}\\ 
 \vdots  & \ddots &  \vdots \\  
 \delu{f_m}{y_1}& \dots & \delu{f_m}{y_m}
\end{vmatrix}
\neq 0
 \text{　　特に　　}
\begin{vmatrix}
\dfrac{\partial f_{1} }{\partial y_{1}} & \dots & \dfrac{\partial f_{1}}{\partial y_{m}} \\
\vdots  & \ddots &\vdots \\
\dfrac{\partial f_{m} }{\partial y_{1}} & \dots & \dfrac{\partial f_{m}}{\partial y_{m}}
\end{vmatrix}
\neq 0
$$

よって$f_{j}(X,y_{1},\dots,y_{m},y_{m+1}) \,(j=1,\dots,m)$は$P(k+1,m)$の仮定を満たすから，ある$\varepsilon_{1}>0$に対し
$|(X,y_{m+1})-(A,b_{m+1})|<\varepsilon_{1}$ならば

(1) $(b_{1},\dots,b_{m})=(\varphi'_{1}(A,b_{m+1}),\dots,\varphi'_{m}(A,b_{m+1}))$

(2) $f_{j}(X,\varphi'_{1}(X,y_{m+1}),\dots,\varphi'_{m}(X,y_{m+1}),y_{m+1})=0 \q(j=1,\dots,m)$

を満たす$m$個の微分可能な関数$\varphi'_{1}(X),\dots,\varphi'_{m}(X)$が一意に存在する。\
$f_{j}(X,\varphi'_{1}(X),\dots,\varphi'_{m}(X))$を$F_{j}(X,y_{m+1})$とおく。

::: lemma
[]{#f/yneq0 label="f/yneq0"} $(A,b_{m+1})$ において
$\dfrac{\partial F_{m+1} }{\partial y_{m+1}}\neq 0$ が成り立つ。
:::

::: proof
*Proof.* $|(X,y_{m+1})-(A,b_{m+1})|<\varepsilon_{1}$において$F_{j}=0$
($0$の定数関数)\
ゆえに$(A,b_{m+1})$において\

$$
\begin{split}
 &\dfrac{\partial F_{1} }{\partial y_{m+1}}=
 \dfrac{\partial f_{1} }{\partial y_{1}}\dfrac{\partial \varphi'_{1} }{\partial y_{m+1}}
 +\dots
 +\dfrac{\partial f_{1} }{\partial y_{m}}\dfrac{\partial \varphi'_{m} }{\partial y_{m+1}}
 +\dfrac{\partial f_{1} }{\partial y_{m+1}}=0\\
 &\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad\vdots\\
 &\dfrac{\partial F_{m} }{\partial y_{m+1}}=
  \dfrac{\partial f_{m} }{\partial y_{1}}\dfrac{\partial \varphi'_{1} }{\partial y_{m+1}}
 +\dots
 +\dfrac{\partial f_{m} }{\partial y_{m}}\dfrac{\partial \varphi'_{m} }{\partial y_{m+1}}
 +\dfrac{\partial f_{m} }{\partial y_{m+1}}=0
 \end{split}
$$

このもとで

$$
\dfrac{\partial F_{m+1} }{\partial y_{m+1}}=
  \dfrac{\partial f_{m+1} }{\partial y_{1}}\dfrac{\partial \varphi'_{1} }{\partial y_{m+1}}
 +\dots
 +\dfrac{\partial f_{m+1} }{\partial y_{m}}\dfrac{\partial \varphi'_{m} }{\partial y_{m+1}}
 +\dfrac{\partial f_{m+1} }{\partial y_{m+1}}=0
$$

を仮定すると

$$
\begin{pmatrix}
  \dfrac{\partial f_{1} }{\partial y_{1}} & \dots &\dfrac{\partial f_{1} }{\partial y_{m}}&\dfrac{\partial f_{1} }{\partial y_{m+1}}\\
 \vdots &\ddots &\vdots  &\vdots \\
 \dfrac{\partial f_{m} }{\partial y_{1}} &\dots &\dfrac{\partial f_{m} }{\partial y_{m}}&\vdots \\
 \dfrac{\partial f_{m+1} }{\partial y_{1}}&\dots &\dots  &\dfrac{\partial f_{m+1} }{\partial y_{m+1}} 
 \end{pmatrix}
 \begin{pmatrix}
 \dfrac{\partial \varphi'_{1} }{\partial y_{m+1}}\\
 \vdots\\
 \dfrac{\partial \varphi'_{m} }{\partial y_{m+1}}\\
 \displaystyle{1}
 \end{pmatrix}=\bm{0}
$$

であるが，これは$\left|\delu{f}{y}\right|\neq 0$に反し矛盾する。 ◻
:::

以上より

(i) $F_{m+1}\left(A,b_{m+1}\right) =0$

(ii) $\left(A,b_{m+1}\right)$ において$\delu{F_{m+1}}{y_{m+1}}\neq 0$

から$P(k,1)$によってある$\varepsilon_{2}>0$に対し$|X-A|<\varepsilon_{2}$上で

(1) $b_{m+1}=\varphi_{m+1}\left(A\right)$

(2) $f_{m+1}(X,\varphi_{m+1}(X))=0$

を満たす関数$\varphi_{m+1}$が一意に存在する。\
したがって$\varphi'_{j}(X,\varphi_{m+1}(X))=\varphi_{j}(X)$
$(j=1,\dots,m)$とおくと$\varphi_{j}$は一意であり

$$
|(X,\varphi_{m+1}(X))-(A,b_{m+1})|< \varepsilon_{1}\text{　かつ　}|X-A|<\varepsilon_{2}
$$


になるように$|X-A|<\varepsilon$なる$\varepsilon$を定めれば

(1) $B=(\varphi_{1}(A),\dots,\varphi_{m}(A),\varphi_{m+1}(A))$

(2) $f_j(X,\varphi_{1}(X),\dots,\varphi_{m}(X),\varphi_{m+1}(X))=0\,(j=1,\dots,m+1)$

となる。以上より$P(k,m+1)$が示された。（証明終）

##### 補足 {#補足 .unnumbered}

$j=1,\dots,m$に対し

$$
\begin{aligned}
f_j\left(X,\varphi _1\left(X\right) ,\dots,\varphi _m\left(X\right) \right) :=G_j\left(X\right) \end{aligned}
$$

とおくと$G_j$はすべて$0$の定数関数なので

$$
\begin{aligned}
\delu{G_1}{x_1}=\delu{f_1}{x_1}+\delu{f_1}{y_1}\delu{\varphi _1}{x_1}+\dots+\delu{f_1}{y_m}\delu{\varphi _m}{x_1}=0\\ 
\vdots　　　　　　　　　　　　　\\ 
\delu{G_m}{x_1}=\delu{f_m}{x_1}+\delu{f_m}{y_1}\delu{\varphi _1}{x_1}+\dots+\delu{f_m}{y_m}\delu{\varphi _m}{x_1}=0\end{aligned}
$$

であるから

$$
\begin{aligned}
\begin{pmatrix}
 {\delu{f_1}{y_1}}& {\dots}& {\delu{f_1}{y_m}}\\
 \vdots& \ddots& \vdots\\
 \delu{f_m}{y_1}& \dots& \delu{f_m}{y_m}
\end{pmatrix}
\begin{pmatrix}
\delu{\varphi _1}{x_1}\\ \vdots \\\delu{\varphi _m}{x_1}
\end{pmatrix}
=
- \begin{pmatrix}
 \delu{f_1}{x_1}\\ \vdots\\ \delu{f_m}{x_1}
\end{pmatrix}\end{aligned}
$$

$i=2,\dots,k$で同じことを行うと

$$
\begin{aligned}
\begin{pmatrix}
 \delu{f_1}{y_1}& \dots& \delu{f_1}{y_m}\\
 \vdots& \ddots& \vdots\\
 \delu{f_m}{y_1}& \dots& \delu{f_m}{y_m}
\end{pmatrix}
\begin{pmatrix}
\delu{\varphi _1}{x_1}& \dots& \delu{\varphi _1}{x_k}\\
\vdots& \ddots& \vdots\\
\delu{\varphi _m}{x_1}& \dots& \delu{\varphi _m}{x_k} 
\end{pmatrix}
=
-
\begin{pmatrix}
 \delu{f_1}{x_1}& \dots& \delu{f_1}{x_k}\\
 \vdots& \ddots & \vdots\\
 \delu{f_m}{x_1}& \dots& \delu{f_m}{x_k}
\end{pmatrix}\end{aligned}
$$

より

$$
\begin{aligned}
\delu{f}{y}\delu{\varphi }{x}=-\delu{f}{x}\end{aligned}
$$

すなわち

$$
\begin{aligned}
\delu{\varphi }{x}=-\left(\delu{f}{y}\left(X,\varphi \left(X\right) \right) \right) ^{-1}\delu{f}{x}\left(X,\varphi \left(X\right) \right) \end{aligned}
$$


$$
\begin{aligned}
 \begin{pmatrix}
 \delu{\varphi _1}{x_1}& \dots& \delu{\varphi _1}{x_k}\\
 \vdots& \ddots& \vdots\\
 \delu{\varphi _m}{x_1}& \dots& \delu{\varphi _m}{x_k} 
 \end{pmatrix}
 =
 -\begin{pmatrix}
 \delu{f_1}{y_1}& \dots& \delu{f_1}{y_m}\\
 \vdots& \ddots& \vdots\\
 \delu{f_m}{y_1}& \dots& \delu{f_m}{y_m}
 \end{pmatrix}^{\raisebox{3zw}[1zw][0zw]{\(-1\)}}
 \begin{pmatrix}
 \delu{f_1}{x_1}& \dots& \delu{f_1}{x_k}\\
 \vdots& \ddots& \vdots\\
 \delu{f_m}{x_1}& \dots& \delu{f_m}{x_k}
 \end{pmatrix}
 \end{aligned}
$$

帰納法の概略は下図のようである。\

#### 陰関数定理の別証

写像$T:\mathbb{R}^{k+m}\to \mathbb{R}^m$を以下のように定める。

$$
\begin{aligned}
T\left(X,Y\right) =Y-\left(\delu{f}{y}\left(A,B\right) \right) ^{-1}\bm{f}\left(X,Y\right) \end{aligned}
$$

このとき$T\left(A,B\right) =\delu{T}{y}\left(A,B\right) =\bm{0}$である。$T,\delu{T}{y}$の連続性から$\rho,\delta _\rho$をあらためて小さく取ると$\left|X-A\right| <\delta _\rho$かつ$\left|Y-B\right| <\rho$ならば

$$
\begin{aligned}
\left|\left|\delu{T}{y}\left(X,Y\right) \right| \right| <\dfrac{1}{2},\left|T\left(X,Y\right) -T\left(X,Y'\right) \right| <\dfrac{1}{2}\rho\text{　　かつ　　}\left|T\left(X,B\right) -B\right| <\dfrac{\rho}{3}\end{aligned}
$$

とできる。ただし，$\left|\left|\cdot \right| \right|$を行列のノルム，すなわち行列の成分の絶対値の最大値とした。

::: lemma
[]{#リプシッツ連続 label="リプシッツ連続"}
上の範囲で$X,Y$を取ると$\left|T\left(X,Y\right) -B\right| <\rho$
:::

::: proof
*Proof.*

$$
\begin{aligned}
 \left|T\left(X,Y\right) -B\right|& \leq \left|T\left(X,Y\right) -T\left(X,B\right) \right| +\left|T\left(X,B\right) -B\right| \\ 
 & \leq \dfrac{1}{2}\left|Y-B\right| +\dfrac{\rho}{3}\\ 
 &\leq \dfrac{1}{2}\rho+\dfrac{\rho}{3}<\rho
 \end{aligned}
$$
 ◻
:::

::: theorem
[]{#（バナッハの不動点定理） label="（バナッハの不動点定理）"}
（バナッハの不動点定理）$\Omega\in \mathbb{R}^m$とし，写像$T:\Omega\to \Omega$は任意の$X,Y\in \Omega$において$k\in \left(0,1\right)$として

$$
\begin{aligned}
 T\left(X\right) -T\left(Y\right) \leq k\left|X-Y\right| 
 \end{aligned}
$$

を満たすとする。このとき写像$T$は不動点をただ一つもつ。
:::

$X\in R\left(A,\delta _\rho\right)$を固定して写像$S$を

$$
\begin{aligned}
S\colon R\left(B,\rho\right)\to R\left(B,\rho\right),Y\mapsto T\left(X,Y\right) \end{aligned}
$$

によって定める（により$T$も$R\left(B,\rho\right)$に属する）と，定理[\[（バナッハの不動点定理）\]](#（バナッハの不動点定理）){reference-type="ref"
reference="（バナッハの不動点定理）"}より

$$
\begin{aligned}
S\left(Y\right) =Y　すなわち　\bm{f}\left(X,Y\right) =0 \end{aligned}
$$

となる$Y$が$X$に対してただ一つ存在することが示された。

### ラグランジュの未定乗数法

::: theorem
[]{#ラグランジュの未定乗数法
label="ラグランジュの未定乗数法"}（ラグランジュの未定乗数法）
$X=(x_{1},\dots,x_{k}) ,\, Y=(y_{1},\dots,y_{m})$とする。
$g_j(X,Y)=0 \,(j=1,\dots,m)$のもとで，$f(X,Y)$は$(X,Y)=(A,B)$において極値を取るものとする。$(A,B)$において

$$
\left|\dfrac{\partial g}{\partial y}\right|=
 \vmat{
 \dfrac{\partial g_1}{\partial y_1}& \dots& \dfrac{\partial g_1}{\partial y_m}\\
 \vdots& \ddots& \vdots \\
 \dfrac{\partial g_m}{\partial y_1}& \dots& \dfrac{\partial g_m}{\partial y_m}
 } \neq 0
$$

であれば$\bm{g}(X,Y)=(g_1(X,Y),\dots,g_m(X,Y)),\\\bm{\la}=(\la_1,\dots,\la_m)^ \mathrm{T}$,$\bm{F}(X,Y,\bm{\la})=f(X,Y)-\bm{g}(X,Y)\bm{\la}$として$(A,B)$において

$$
\begin{aligned}
 \nabla \bm{F}=\bm{0}
 \end{aligned}
$$

すなわち

$$
\begin{aligned}
 \begin{pmatrix}
 \dfrac{\partial f}{\partial x_1}& \dfrac{\partial g_1}{\partial x_1}& \dots & \dfrac{\partial g_m}{\partial x_1}\\
 \vdots  & \vdots  & \ddots& \vdots  \\
 \dfrac{\partial f}{\partial x_k}& \dfrac{\partial g_1}{\partial x_k}& \dots & \dfrac{\partial g_m}{\partial x_k}\\
 \dfrac{\partial f}{\partial y_1}& \dfrac{\partial g_1}{\partial y_1}& \dots & \dfrac{\partial g_m}{\partial y_1}\\
 \vdots  & \vdots  & \ddots& \vdots  \\
 \dfrac{\partial f}{\partial y_m}& \dfrac{\partial g_1}{\partial y_m}& \dots& \dfrac{\partial g_m}{\partial y_m}
 \end{pmatrix}
 \begin{pmatrix}
 1 \\ -\la_1 \\ \vdots \\ -\la_m
 \end{pmatrix}=\bm{0}
 \text{かつ$\bm{g}=\bm{0}$}
 \end{aligned}
$$

を満たす$\bm{\la}=(\la_1,\dots,\la_m)^\mathrm{T}$が存在する。
:::

::: proof
*Proof.* よりある$\varepsilon >0$に対して$|X-A|<\varepsilon$ のもとで

(1) $B=(\varphi_1(A),\dots,\varphi_m(A))$

(2) $g_j(X,\varphi_1(X),\dots,\varphi_m(X))=0 \q(j=1,\dots,m)$

なる$m$個の関数$\varphi_1(X),\dots,\varphi_m(X)$が存在する。\
$f,g_j(X,\varphi_1(X),\dots,\varphi_m(X))=F,G_j(X)$とおく。各$i$について考える。極値を取るので$X=A$において

$$
\begin{aligned}
 \dfrac{\partial F}{\partial x_i}=\dfrac{\partial f}{\partial x_i}+\dfrac{\partial f}{\partial y_1}
 \dfrac{\partial \varphi_1}{\partial x_i} +\dots+\dfrac{\partial f}{\partial y_m}
 \dfrac{\partial \varphi_m}{\partial x_i}=0 
 \end{aligned}
$$

常に$0$なので

$$
\begin{aligned}
 \dfrac{\partial G_j}{\partial x_i}=\dfrac{\partial g_j}{\partial x_i}+\dfrac{\partial g_j}{\partial y_1}
 \dfrac{\partial \varphi_1}{\partial x_i} +\dots+\dfrac{\partial g_j}{\partial y_m}
 \dfrac{\partial \varphi_m}{\partial x_i}=0\q(j=1,\dots,m)
 \end{aligned}
$$

したがって$X=A$において

$$
\begin{aligned}
 \begin{pmatrix}
 \dfrac{\partial f}{\partial x_i} & \dfrac{\partial f}{\partial y_1} & \dots & \dfrac{\partial f}{\partial y_m}\\
 \dfrac{\partial g_1}{\partial x_i} & \dfrac{\partial g_1}{\partial y_1} & \dots & \dfrac{\partial g_1}{\partial y_m}\\
 \vdots& \vdots& \ddots& \vdots\\
 \dfrac{\partial g_m}{\partial x_i} & \dfrac{\partial g_m}{\partial y_1} & \dots & \dfrac{\partial g_m}{\partial y_m}\\
 \end{pmatrix}
 \begin{pmatrix}
 1 \\ \dfrac{\partial \varphi_1}{\partial x_i}\\ \vdots\\ \dfrac{\partial \varphi_m}{\partial x_i}
 \end{pmatrix}=\bm{0}\q(\text{左の行列$A_i$とおく})
 \end{aligned}
$$


より連立方程式$A_i \bm{x}=0$は$0$でない解を持つので$\rank(A_i)<m+1$。よって$\rank(A_i^ \mathrm{T})<m+1$より

$$
\begin{aligned}
 \begin{pmatrix}
 \dfrac{\partial f}{\partial x_i} & \dfrac{\partial g_1}{\partial x_i} & \dots & \dfrac{\partial g_m}{\partial x_i}\\
 \dfrac{\partial f}{\partial y_1} & \dfrac{\partial g_1}{\partial y_1} & \dots & \dfrac{\partial g_m}{\partial y_1}\\
 \vdots& \vdots& \ddots& \vdots\\
 \dfrac{\partial f}{\partial y_m} & \dfrac{\partial g_1}{\partial y_m} & \dots & \dfrac{\partial g_m}{\partial y_m}\\
 \end{pmatrix}
 \begin{pmatrix}
 \la'_f(i)\\ \la'_1(i)\\ \vdots\\ \la'_m(i) 
 \end{pmatrix}=\bm{0}
 \end{aligned}
$$

となる$(\la'_f(i),\la'_1(i),\dots,\la'_m(i))^ \mathrm{T}
 \neq \bm{0}$が存在する。
$\la'_f(i)\neq 0$を示す。$\la'_f(i)= 0$とすると

$$
\begin{aligned}
 \begin{pmatrix}
 \dfrac{\partial g_1}{\partial y_1} & \dots & \dfrac{\partial g_m}{\partial y_1}\\
 \vdots& \ddots& \vdots\\
  \dfrac{\partial g_1}{\partial y_m} & \dots & \dfrac{\partial g_m}{\partial y_m}\\
 \end{pmatrix}
 \begin{pmatrix}
  \la'_1(i)\\ \vdots\\ \la'_m(i) 
 \end{pmatrix}=\bm{0}\q\text{すなわち}\q\dfrac{\partial f}{\partial y}\bm{\la'}=\bm{0}
 \end{aligned}
$$

であって$\bm{\la'}\neq \bm{0}$なるものが存在するがこれは
$\left|\dfrac{\partial f}{\partial y}\right|\neq 0$に矛盾。
したがって$\la'_f(i) \neq 0$。
$-\dfrac{\la'_j(i)}{\la'_f(i)}=\la_j(i)$とすると，$i=1,\dots,k$に対し

$$
\begin{aligned}
 A_i^ \mathrm{T}
 \begin{pmatrix}
 1 \\ -\la_1(i)\\ \vdots\\ -\la_m(i)
 \end{pmatrix}
 =A_i^ \mathrm{T}
 \begin{pmatrix}
 1 \\
 -\bm{\la(i)}\end{pmatrix}=\bm{0}
 \end{aligned}
$$

となる。 $\bm{\la(i)}$は$i$によらず，

$$
\begin{aligned}
 \begin{pmatrix}
 \dfrac{\partial g_1}{\partial y_1} && \dots && \dfrac{\partial g_m}{\partial y_1}\\
 \vdots&& \ddots&& \vdots\\
  \dfrac{\partial g_1}{\partial y_m} && \dots && \dfrac{\partial g_m}{\partial y_m}\\
 \end{pmatrix}
 \begin{pmatrix}
 t_1\\ \vdots\\t_m
 \end{pmatrix}=
 \begin{pmatrix}
 \dfrac{\partial f}{\partial y_1}\\ \vdots\\ \dfrac{\partial f}{\partial y_m}
 \end{pmatrix}
 \end{aligned}
$$

の解であるが，$\left|\dfrac{\partial g}{\partial y}\right|\neq 0$よりそれは一つに限られる。
よって$\bm{\la(i)}$は$i$によらない。それを$\bm{\la(i)}=\bm{\la}=
 (
 \la_1, \dots, \la_m
 )^\mathrm{T}$とする。
すると$\bm{\la(i)}=\bm{\la}$は$\bm{F}(X,Y,\bm{\la})=f(X,Y)-\bm{g}(X,Y)\bm{\la}$として

$$
\begin{aligned}
 \nabla \bm{F}=\bm{0}
 \end{aligned}
$$

すなわち

$$
\begin{aligned}
 \begin{pmatrix}
 \dfrac{\partial f}{\partial x_1}& \dfrac{\partial g_1}{\partial x_1}& \dots& \dfrac{\partial g_m}{\partial x_1}\\
 \vdots  & \vdots  & \ddots& \vdots\\
 \dfrac{\partial f}{\partial x_k}& \dfrac{\partial g_1}{\partial x_k}& \dots& \dfrac{\partial g_m}{\partial x_k}\\
 \dfrac{\partial f}{\partial y_1}& \dfrac{\partial g_1}{\partial y_1}& \dots& \dfrac{\partial g_m}{\partial y_1}\\
 \vdots  & \vdots  & \ddots& \vdots\\
 \dfrac{\partial f}{\partial y_m}& \dfrac{\partial g_1}{\partial y_m}& \dots& \dfrac{\partial g_m}{\partial y_m}\\
 \end{pmatrix}
 \begin{pmatrix}
 1 \\ -\la_1 \\ \vdots \\ -\la_m
 \end{pmatrix}=\bm{0}\q
 \text{かつ}\q 
 \bm{g}=
 (g_1,\dots,g_m)=
 \bm{0}
 \end{aligned}
$$

を満たす。 ◻
:::

なお，

$$
\begin{aligned}
\bm{\la}=
\begin{pmatrix}
 \la_1\\\vdots\\\la_m
\end{pmatrix}
=
\begin{pmatrix}
 \delu{g_1}{y_1}&\dots&\delu{g_1}{y_m}\\
 \vdots&\ddots&\vdots\\
 \delu{g_m}{y_1}&\dots&\delu{g_m}{y_m}
\end{pmatrix}\left(A,B\right) 
^{\raisebox{3zw}[1zw][0zw]{\(-1\)}}
\begin{pmatrix}
 \delu{f}{y_1}\\\vdots\\\delu{f}{y_m}
\end{pmatrix} \left(A,B\right)\end{aligned}
$$

である。未定乗数法自体が極値を与える$\left(A,B\right)$を求めるために用いられるものなので$\bm{\la}$は$\left(X,Y\right)$の式として与えられることがほとんどである。

### フーリエ級数展開

### 楕円積分論

$K\left(k\right) =\displaystyle \int_{0}^{\dfrac{\pi }{2}} \dfrac{1}{\sqrt{1-k^2 \sin ^2 \theta }}\, d\theta ，E\left(k\right) =\displaystyle \int_{0}^{\dfrac{\pi }{2}} 
{\sqrt{1-k^2 \sin ^2 \theta }}\, d\theta$とおく。ルジャンドルの公式を示したい。

#### 算術幾何平均に収束すること {#算術幾何平均に収束すること .unnumbered}

$\displaystyle \int_{0}^{\dfrac{\pi }{2}} \dfrac{1}{\sqrt{a^2 \cos ^\theta +b^2 \sin ^2 \theta }}\, d\theta =M\left(a,b\right) =\lim_{n \to \infty}a_n=\lim_{n \to \infty}b_n$であることを示す。
ただし$a_{n+1}=\dfrac{1}{2}\left(a_n+b_n\right)， b_{n+1}=\sqrt{a_nb_n}$かつ$a_0=a,b_0=b$
とした。

#### 証明 {#証明-1 .unnumbered}

### リーマン積分の導入から円の面積を考える

行列式の定義，線形代数論，ベクトル解析，微分方程式，フーリエ変換，複素解析，複素関数への拡張，三角関数の部分分数展開，ジョルダン標準形
$n\geq 3 \Leftrightarrow \lnot \exists x,y,z \ s.t.\ x^n+y^n=z^n$
