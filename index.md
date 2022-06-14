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
label="項別積分可能性"}（項別積分可能性）$f_n\l(x\r)$を$[a,b]$上の連続関数の列で$f\l(x\r)$に一様収束するものとする。$a \leq c \leq x\leq b$なる$\forall c,x$に対し$F_n\l(x\r) =\int_{c}^{x} f_n\l(t\r) \, dt$も
$F\l(x\r) =\int_{c}^{x} f\l(t\r) \, dt$に一様収束する。
:::

::: proof
*Proof.*

$$
\begin{aligned}
 \l|F_n\l(x\r) -F\l(x\r) \r| 
 &=\, \l|\int_{c}^{x} f_n\l(t\r) \, dt -\int_{c}^{x} f\l(t\r) \, d t \r| \\
 &\leq\, 
  \int_{c}^{x} \l|f_n\l(t\r) -f\l(t\r) \r| \, d t 
 \leq \int_{c}^{x} \sup_{c\leq t \leq x}\l|f_n\l(t\r) -f\l(t\r) \r|\, d t 
 \end{aligned}
$$

 より
 
$$
 \begin{aligned}
 0 \leq \sup_{a\leq x\leq b}\l|F_n\l(x\r) -F\l(x\r) \r| \leq 
 \sup_{a\leq x\leq b}\l(x-c\r) \sup_{c\leq t\leq x}\l|f_n\l(t\r) -f\l(t\r) \r| 
 \end{aligned}
$$

 一様収束性より
 
$$
 \begin{aligned}
  \lim_{n \to \infty} \sup_{c\leq t\leq x}\l|f_n\l(t\r) -f\l(t\r) \r| =0
 \end{aligned}
$$

 であるからはさみうちの原理より
 
$$
 \begin{aligned}
 \lim_{n \to \infty} \sup_{a\leq x\leq b}\l|F_n\l(x\r) -F\l(x\r) \r| =0
 \end{aligned}
$$

 すなわちa

$$
\int_{c}^{x} \lim_{n \to \infty}f_n\l(t\r) \, d t
 =\lim_{n \to \infty}  \int_{c}^{x} f_n\l(t\r) \, d t
$$

であるから一様収束するときは項別積分可能であることが示された。 ◻
:::

#### 整級数の一様収束性の例

たとえば$f_n\l(x\r) =\dis \sum_{i=0}^{n} (-x)^i$，$f\l(x\r) =\drac{1}{1+x}$とする。$0<t<1$とすると
$-t<x<t$において

$$
\begin{aligned}
\l|f_n\l(x\r) -f\l(x\r) \r| =\l|\drac{1-\l(-x\r)^n }{1-\l(-x\r) }-\drac{1}{1+x} \r| =\drac{\l|x\r| ^n}{1+x}<\drac{t^n}{1-t}\end{aligned}
$$

である。よって

$$
\begin{aligned}
0\leq \sup_{-t<x<t}\l|f_n\l(x\r) -f\l(x\r) \r|<\drac{t^n}{1-t}\end{aligned}
$$

であり最右辺は$n \to \infty$で$0$に収束するのではさみうちの原理より

$$
\begin{aligned}
\lim_{n \to \infty}\sup_{-t<x<t}\l|f_n\l(x\r) -f\l(x\r) \r|=0 \end{aligned}
$$

したがって$-t<x<t$において$f_n\l(x\r)$は$f\l(x\r)$に一様収束する。$\l[0,x\r]$において項別積分すると

$$
\begin{aligned}
\lim_{n \to \infty} \int_{0}^{x} \sum_{i=0}^{n} \l(-s\r) ^i \, d s=
 \int_{0}^{x} \drac{1}{1+s}\, ds \end{aligned}
$$

$t$は自由に動かせることに注意して$-1<x<1$において

$$
\begin{aligned}
\log \l(1+x\r) =\sum_{i=0}^{\infty} \l(-1\r) ^i\drac{x^{i+1}}{i+1}=x-\drac{1}{2}x^2+\drac{1}{3}x^3-\dots\end{aligned}
$$

である。

::: theorem
[]{#項別微分可能性 label="項別微分可能性"}（項別微分可能性）
$F_n\l(x\r)$を$\l[a,b\r]$上の連続関数の列で$F\l(x\r)$に収束するものとする。$F_{n}'\l(x\r)$が$f\l(x\r)$に一様収束するならば$F'\l(x\r)=f\l(x\r)$である。
:::

::: proof
*Proof.*

$$
\begin{aligned}
 F\l(x\r) -F\l(c\r) 
 &=\, \lim_{n \to \infty} \left\{ F_n\l(x\r) -F_n\l(c\r) \right\} =\lim_{n \to \infty} \int_{c}^{x} F_n'\l(t\r) \, d t=\int_{c}^{x} \lim_{n \to \infty} F_n'\l(t\r) \, d t \\
 &=\, \int_{c}^{x} f\l(t\r) \, d t 
 \end{aligned}
$$

 の両辺を微分するだけ。 ◻
:::

::: theorem
[]{#絶対収束する級数の収束性
label="絶対収束する級数の収束性"}（絶対収束する級数の収束性）
$\dis \sum_{n=0}^{\infty} \l|a_n\r|$が収束するならば$\dis \sum_{n=0}^{\infty} a_n$も収束する。
:::

::: proof
*Proof.* $a_{n}^{+}=
 \begin{dcases}
 a_n &\l(a_n\geq 0\r) 
 \\ 0&\l(a_n<0\r) 
 \end{dcases}$ ， $a_{n}^{-}=
 \begin{dcases}
 0 &\l(a_n\geq 0\r) 
 \\ -a_n&\l(a_n<0\r) 
 \end{dcases}$ とする。\
$a_{n}^{+}，a_{n}^{-}\geq 0$であり$a_n=a_n^+-a_n^-,|a_n|=a_n^++a_n^-$である。$\dis \sum_{n=0}^{\infty} \l|a_n\r| =S$とする。

$$
S=\sum_{n=0}^{\infty} \l|a_n\r| =\sum_{n=0}^{\infty} a_n^+
 +\sum_{n=0}^{\infty} a_n^-\geq \sum_{n=0}^{\infty} a_n^+
$$

より$\sum_{}^{} a_n^+$は有界な正項級数であるから収束する。同様に$\sum_{}^{} a_n^-$も収束する。収束値をそれぞれ$S^+,S^-$とおくと

$$
\sum_{n=0}^{\infty} a_n=\sum_{n=0}^{\infty} \l(a_n^+-a_n^-\r) =S^+-S^-
$$

であるから収束する。よって示された。 ◻
:::

### 収束判定法

::: theorem
[]{#コーシーの収束判定法 label="コーシーの収束判定法"}
（コーシーの収束判定法）

$$
\lim_{n \to \infty}\sup_{m>n}\sqrt[m]{\l|a_m\r| } =l\text{が存在するとき} \sum_{n=0}^{\infty} a_n\text{は}
 \begin{dcases}
 \text{収束する}&\l(0<l<1\text{のとき}\r) \\ 
 \text{発散する}&\l(l>1\text{のとき}\r) 
 \end{dcases}
$$

:::

::: proof
*Proof.* 　

(i) $0<l<1$のとき\
 極限の定義より$l<t<1$となる$t$を考えると$n\geq N_0$ならば$\sqrt[n]{\l|a_n\r| }<t$すなわち$\l|a_n\r| <t^n$となる$N_0\in \mathbb{Z}_{\geq 0}$が存在する。$N>N_0$として
 
 
$$
 \begin{aligned}
 \sum_{n=0}^{N} \l|a_n\r| =
 \sum_{n=0}^{N_0-1} \l|a_n\r| 
 +\sum_{n=N_0}^{N} \l|a_n\r| <
 \sum_{n=0}^{N_0-1} \l|a_n\r| 
 +\sum_{n=N_0}^{N}t^n<\sum_{n=0}^{N_0-1} \l|a_n\r| +t^{N_0}\drac{1}{1-t}
 \end{aligned}
$$

 より$\sum_{}^{} |a_n|$は有界な正項級数なので収束する。よって$\sum_{}^{} a_n$は絶対収束するので収束する。

(ii) $l>1$のとき\
  $1<t<l$なる$t$を考えると$n\geq N_0$ならば$\sqrt[n]{\l|a_n\r| }>t$すなわち$\l|a_n\r| >t^n$となる$N_0\in \mathbb{Z}_{\geq 0}$が存在する。$n \to \infty$で$t^n$は発散するので追い出しの原理より$\l|a_n\r|$も発散。よって$a_n$も発散するので$\sum_{}^{} a_n$は発散する。

 ◻
:::

::: theorem
[]{#ダランベールの収束判定法
label="ダランベールの収束判定法"}（ダランベールの収束判定法）

$$
\lim_{n \to \infty}\l|\drac{a_{n+1}}{a_n}\r| =l\text{が存在するならば} \sum_{n=0}^{\infty} a_n\text{は}
 \begin{dcases}
 \text{収束する}&\l(0<l<1\text{のとき}\r) \\ 
 \text{発散する}&\l(l>1\text{のとき}\r) 
 \end{dcases}
$$

:::

::: proof
*Proof.* 　

(i) $0<l<1$のとき\
 極限の定義より$l<t<1$となる$t$を考えると$n\geq N_0$ならば$\l|\drac{a_{n+1}}{a_n}\r| <t$すなわち$\l|a_{n+1}\r| <t\l|a_{n}\r|$となる$N_0\in \mathbb{Z}_{\geq 0}$が存在する。$\l|a_n\r|<t\l|a_{n-1}\r| <\dots<\l|a_{N_0}\r| t^{n-N_0}$
 である。 $N>N_0$として
 
$$
 \begin{aligned}
 \sum_{n=0}^{N} \l|a_n\r| =
 \sum_{n=0}^{N_0-1} \l|a_n\r| 
 +\sum_{n=N_0}^{N} \l|a_n\r| 
 <\sum_{n=0}^{N_0-1} \l|a_n\r| 
 +\l|a_{N_0}\r| \sum_{n=N_0}^{N}t^{n-N_0}
 <\sum_{n=0}^{N_0-1} \l|a_n\r| +\drac{|a_{N_0}|}{1-t}
 \end{aligned}
$$

 より$\sum_{}^{} |a_n|$は有界な正項級数なので収束する。よって$\sum_{}^{} a_n$は絶対収束するので収束する。

(ii) $l>1$のとき\
  $1<t<l$なる$t$を考えると$n\geq N_0$ならば$\l|\drac{a_{n+1}}{a_n}\r| >t$となる$N_0\in \mathbb{Z}_{\geq 0}$が存在する。
  $\l|a_n\r|>t\l|a_{n-1}\r| >\dots>\l|a_{N_0}\r| t^{n-N_0}$である
  $n \to \infty$で$t^n$は発散するので追い出しの原理より$\l|a_n\r|$も発散。よって$a_n$も発散するので$\sum_{}^{} a_n$は発散する。

 ◻
:::

::: theorem
[]{#コーシーの収束半径 label="コーシーの収束半径"}（コーシーの収束半径）
$\sum_{}^{} a_nx^n$の収束半径$r$は
$\dis \lim_{n \to \infty}\dis \sup_{m>n}\sqrt[m]{\l|a_m\r| } =l$として$r=\drac{1}{l}$である。
:::

::: proof
*Proof.* 　

(i) $\l|x\r| <r$のとき\
 $x=0$では自明に収束。$0<\l|x\r|<r$とする。$0<l<\drac{1}{\l|x\r| }$である。$n\geq N_0$ならば$\sqrt[n]{\l|a_n\r| }<\drac{1}{2}\l(l+\drac{1}{\l|x\r| }\r)$となる$N_0\in \mathbb{Z}_{\geq 0}$が存在する。このもとで
 
 
$$
 \begin{aligned}
 \sum_{n=0}^{N} \l|a_nx^n\r| 
 &=\, \sum_{n=0}^{N_0-1} \l|a_nx^n\r| 
 +\sum_{n=N_0}^{N} (\sqrt[n]{\l|a_n\r|  }\l| x\r|)^n
 \\
 &\leq\, \sum_{n=0}^{N_0-1} \l|a_nx^n\r| +\sum_{n=N_0}^{N} 
 \l(\drac{1}{2}\l(l+\drac{1}{\l|x\r| }\r) \bigg/\drac{1}{\l|x\r| }\r)
 ^n
 \end{aligned}
$$

 であり$\l(\drac{1}{2}\l(l+\drac{1}{\l|x\r| }\r) \bigg/\drac{1}{\l|x\r| }\r)<1$より$\sum_{}^{}a_nx^n$は絶対収束するので収束する。

(ii) $\l|x\r| >r$のとき\
  $0<\drac{1}{\l|x\r| }<l$である。任意の$N_0\in \mathbb{Z}_{\geq 0}$に対して$n>N_0$かつ$\sqrt[n]{\l|a_n\r| }>\drac{1}{2}\l(l+\drac{1}{\l|x\r| }\r)$となる$n$が存在する。すなわち$\l|a_nx^n\r| =(\sqrt[n]{\l|a_n\r|  }\l| x\r|)^n=\l(\drac{1}{2}\l(l+\drac{1}{\l|x\r| }\r) \bigg/\drac{1}{\l|x\r| }\r)
  ^n>1$になるような$n>N_0$が任意の$N_0\in \mathbb{Z}_{\geq 0}$に対して存在するので数列$\left\{ a_nx^n \right\}$は$0$に収束しない。したがって級数も発散する。

 ◻
:::

::: theorem
[]{#ダランベールの収束半径
label="ダランベールの収束半径"}（ダランベールの収束半径）
$\sum a_nx^n$の収束半径$r$は存在するならば$r=\dis \lim_{n \to \infty}\l|\drac{a_n}{a_{n+1}}\r|$である。
:::

::: proof
*Proof.* 　

(i) $0 \leq x< r$のとき\
 $n\geq \exists N_0 \Rightarrow \l|\drac{a_n}{a_{n+1}}\r| >\drac{\l|x\r| +r}{2} \Leftrightarrow \l|a_{n+1}\r| <\left( 1\bigg/\drac{\l|x\r| +r}{2} \right)\l|a_n\r|$よりこれを繰り返し用いて$\l|a_n\r| <\left( 1\bigg/\drac{\l|x\r| +r}{2} \right)^{n-N_0}\l|a_{N_0}\r|$が得られる。
 
 
$$
 \begin{aligned}
 \sum_{n=0}^{N} \l|a_nx^n\r| <\sum_{n=0}^{N_0-1} \l|a_nx^n\r|+\sum_{n=N_0}^{N} \left( |x|\bigg/\drac{\l|x\r| +r}{2} \right)^{n-N_0}\l|a_{N_0}\r|
 \end{aligned}
$$

 であり$\left( |x|\bigg/\drac{\l|x\r| +r}{2} \right)<1$より$\sum_{}^{}a_nx^n$は絶対収束するので収束する。

(ii) $|x|>r$のとき\
  $n\geq \exists N_0 \Rightarrow \l|\drac{a_n}{a_{n+1}}\r| <\drac{\l|x\r| +r}{2} \Leftrightarrow \l|a_{n+1}\r| >\left( 1\bigg/\drac{\l|x\r| +r}{2} \right)\l|a_n\r|$よりこれを繰り返し用いて$\l|a_n\r| >\left( 1\bigg/\drac{\l|x\r| +r}{2} \right)^{n-N_0}\l|a_{N_0}\r|$が得られる。よって
 
 
$$
 \begin{aligned}
  \l|a_nx^n\r| >\left( |x|\bigg/\drac{\l|x\r| +r}{2} \right)^{n-N_0}\l|a_{N_0}\r| 
  \end{aligned}
$$

  であり$|x|\bigg/\drac{\l|x\r| +r}{2}>1$より左辺は発散する。追い出しの原理より$a_nx^n$が$0$に収束することはないので発散する。

 ◻
:::

### $e$の導入

::: theorem
[]{#eの存在 label="eの存在"}（$e$の存在）
$e:=\dis \lim_{n \to \infty}\l(1+\drac{1}{n}\r) ^n$が存在することを示す。
:::

::: proof
*Proof.* $a_n=\l(1+\drac{1}{n}\r) ^n$とする。\
単調増加性\
二項定理より

$$
\begin{aligned}
 a_n 
 &=\, \sum_{k=0}^{n} \binom{n}{k}\drac{1}{n^k}
 =\sum_{k=0}^{n} \drac{n\l(n-1\r)\l(n-2\r) \dots\l(n-k+1\r) }{k!n^k} \\
 &=\, \sum_{k=0}^{n} \drac{1}{k!}\l(1-\drac{1}{n}\r) \l(1-\drac{2}{n}\r) \dots\l(1-\drac{k-1}{n}\r) \\
 &=\, 2+\drac{1}{2!}\l(1-\drac{1}{n}\r) +\drac{1}{3!}\l(1-\drac{1}{n}\r) \l(1-\drac{2}{n}\r) +\dots+\drac{1}{n!}\l(1-\drac{1}{n}\r) \dots\l(1-\drac{n-1}{n}\r) 
 \\
 a_{n+1}
 &=\, \sum_{k=0}^{n+1} \drac{1}{k!}\l(1-\drac{1}{n+1}\r) \l(1-\drac{2}{n+1}\r) \dots\l(1-\drac{k-1}{n+1}\r) \\
 &>\, \sum_{k=0}^{n}\drac{1}{k!} \l(1-\drac{1}{n+1}\r) \l(1-\drac{2}{n+1}\r) \dots\l(1-\drac{k-1}{n+1}\r) 
 \\
 &>\,\sum_{k=0}^{n} \drac{1}{k!}\l(1-\drac{1}{n}\r) \l(1-\drac{2}{n}\r) \dots\l(1-\drac{k-1}{n}\r)=a_n
 \end{aligned}
$$

 であるから$\left\{ a_n \right\}$は単調増加。\
有界性\

$$
\begin{aligned}
 \forall n\ a_n 
 &=\, 
 \sum_{k=0}^{n} \drac{1}{k!}\l(1-\drac{1}{n}\r) \l(1-\drac{2}{n}\r) \dots\l(1-\drac{k-1}{n}\r) 
 <\sum_{k=0}^{n} \drac{1}{k!}\\
 &=\, 
 1+\drac{1}{1}+\drac{1}{2}+\drac{1}{2\cdot 3}+\drac{1}{2\cdot 3\cdot 4}+\dots \\
 &<\, 1+\drac{1}{1}+\drac{1}{2}+\drac{1}{2\cdot 2}+\drac{1}{2\cdot 2\cdot 2}+\dots=3
 \end{aligned}
$$

以上より$\left\{ a_n \right\}$は有界な単調増加数列であるから収束する。 ◻
:::

### マクローリン展開

$k\geq 1$のとき

$$
\begin{aligned}
\drac{d}{dt}\left\{ \drac{\l(x-t\r) ^k}{k!}f^{\l(k\r) }\l(t\r) \right\}=
-\drac{\l(x-t\r) ^{k-1}}{\l(k-1\r) !}f^{\l(k\r) }\l(t\r) 
+\drac{\l(x-t\r) ^{k}}{k !}f^{\l(k+1\r)}\l(t\r) \end{aligned}
$$

に注意すると

$$
\begin{aligned}
\drac{d}{dt}\left[ f\l(t\r) +\sum_{k=1}^{n-1} \left\{ \drac{\l(x-t\r) ^k}{k!}f^{\l(k\r) }\l(t\r) \right\} \right]
=\drac{\l(x-t\r) ^{n-1 }}{\l(n-1\r) !}f^{\l(n\r)}\l(t\r)\end{aligned}
$$

両辺$\l[a,x\r]$において積分すると

$$
\begin{aligned}
f\l(x\r) -f\l(a\r) -
\sum_{k=1}^{n-1} \left\{ \drac{\l(x-a\r) ^k}{k!}f^{\l(k\r) }\l(a\r) \right\} 
=\int_{a}^{x} \drac{\l(x-t\r) ^{n-1 }}{\l(n-1\r) !}f^{\l(n\r)}\l(t\r)\, dt \end{aligned}
$$

よって

$$
\begin{aligned}
f\l(x\r) =\sum_{k=0}^{n-1} \left\{ \drac{\l(x-a\r) ^k}{k!}f^{\l(k\r) }\l(a\r) \right\} +R_n\l(x\r) \end{aligned}
$$

と書ける。

#### 剰余項の計算 {#剰余項の計算 .unnumbered}

積分の平均値の定理より$c\in [a,x]$として

$$
\begin{aligned}
R_n\l(x\r) =\int_{a}^{x} \drac{\l(x-t\r) ^{n-1 }}{\l(n-1\r) !}f^{\l(n\r)}\l(t\r)\, dt =\int_{a}^{x} \drac{\l(x-t\r) ^{n-1 }}{\l(n-1\r) !}f^{\l(n\r)}\l(c\r)\, dt 
=\drac{\l(x-a\r) ^n}{n!}f^{\l(n\r) }\l(c\r)  \end{aligned}
$$

となる$c$が存在する。最右辺はラグランジュの剰余項である。より一般に$\l(x-t\r) ^{n-p}f^{\l(n\r) }\l(t\r)$に平均値の定理を使うと

$$
\begin{aligned}
R_n\l(x\r) =\int_{a}^{x} \drac{\l(x-c\r) ^{n-p }\l(x-t\r) ^{p-1}}{\l(n-1\r) !}f^{\l(n\r)}\l(c\r)\, dt 
=\drac{\l(x-a\r) ^p}{p\l(n-1\r) !}\l(x-c\r) ^{n-p}f^{\l(n\r) }\l(c\r)\end{aligned}
$$

$c=a+\theta \l(x-a\r)$とおくと$0\leq \theta \leq 1$であって

$$
\begin{aligned}
R_n\l(x\r) =\drac{\l(x-a\r) ^n}{p\l(n-1\r) !}\l(1-\theta \r) ^{n-p}f^{\l(n\r) }\l(c\r)\end{aligned}
$$

である。コーシーの剰余項である。

### 陰関数定理

::: theorem
[]{#中間値の定理 label="中間値の定理"}（中間値の定理）
$f:\mathbb{R}\to \mathbb{R}$として$f$は閉区間$[a,b]$上連続とする。$f\l(a\r)$と$f\l(b\r)$の間にある任意の$k$に対し$a\leq c\leq b$かつ$f\l(c\r) =k$となる$c$が存在する。
:::

::: proof
*Proof.*
$f\l(a\r) \leq f\l(b\r)$としても一般性を失わない。$c=\dis \sup_{a\leq x\leq b}\l\{ x \:\middle|\: f\l(x\r) \leq k \r\}$とする。$f\l(c\r) \neq k$になると仮定して矛盾を示す。
$f\l(c\r) >k$としても$f\l(c\r) <k$としても($f\l(c\r) >k$のときは$\sup_{}$の性質より)$\dis \lim_{n \to \infty}x_n=c$かつ$f\l(x_n\r) \leq k$となる数列$\left\{ x_n \right\}$が存在する。連続性より$f\l(x_n\r) \to f\l(c\r) \leq k$となる。一方$b$から$c$に近づく数列$\left\{ y_n \right\}$を考えると$f\l(y_n\r) >k$であり連続性より$f\l(y_n\r) \to f\l(c\r) \geq k$となる。
以上より$f\l(c\r) =k$となるがこれは仮定に矛盾する。背理法より示された。 ◻
:::

以降，$X$をベクトルとしてベクトル値関数$f(X)$のヤコビアンを$\delu{f}{x}$のように表すことにする。

::: theorem
[]{#陰関数定理 label="陰関数定理"}（陰関数定理）
$X=\left(x_1,\dots x_k\right)$，$Y=\left(y_1,\dots y_m\right)$とする$\l(k,m\in \mathbb{Z}_{\geq 1}\r)$。$\l(A,B\r) \in \l(X,
 Y\r)$において$m$個の関数$f_{1}\l(X,Y\r),\dots ,f_{m}\l(X,Y\r)$が

(i) $f_1=\dots=f_{m}=0$

(ii) $\l|\drac{\del f}{\del y}\r|=\vmat{
  \delu{f_1}{y_1}& \dots & \delu{f_1}{y_m}\\
  \vdots& \ddots & \vdots\\
  \delu{f_m}{y_1}& \dots& \delu{f_m}{y_m} 
  }\neq 0$

を満たすならばある$\varepsilon >0$が存在して$\l|X-A\r| <\varepsilon$上で$\varphi _1\l(X\r) ,\dots ,\varphi _m\l(X\r)$が存在して以下を満たす。

(1) $B=\l(\varphi _1\l(A\r) ,\dots , \varphi _m\l(A\r) \r)$

(2) $f_j\l(X,\varphi _1\l(X\r) ,\dots ,\varphi _m\l(X\r) \r) =0　\l(j=1,\dots, m\r)$

上記の命題を$P\l(k,m\r)$とおく。
:::

#### 証明 {#証明 .unnumbered}

##### $P\l(k,1\r)$について {#plk1rについて .unnumbered}

仮定は$X=\left(x_1,\dots ,x_k\right)，Y=y_1=y, A=\left(a_1,\dots , a_k\right)$，$B=b_1=b$として$\l(X,Y\r) =\l(A,b\r)$において

(i) $f\l(A,b\r) =0$

(ii) $\delu{f}{y}\neq 0$

であることである。(ii)よりある$\delta \neq 0$であって$f\l(A,b_1-\delta\r)<0< f\l(A,b_1+\delta\r)$となるものが存在する。$\delta$に対応する$\varepsilon >0$をうまくとれば$\l|X-A\r| <\varepsilon$ならば

$$
f\l(X,b-\delta \r) <0<f\l(X,b+\delta \r)
$$

とすることができる。中間値の定理（）と$\delu{f}{y}$の符号が一定であることにより$\l|X-A\r| <\varepsilon$のもとで

(1) $b=\varphi \l(X\r)$

(2) $f\l(X,\varphi \l(X\r) \r) =0$

を満たす$\varphi\l(X\r)$ が$b-\delta$と$b-\delta$
の間にただ一つ存在する。よって$P(k,1)$が示された。（証明終）

##### $\varphi$の連続性 {#varphiの連続性 .unnumbered}

$\left[b-\delta ,b+\delta \right]=I$とする。$\varphi \l(X_0+H\r)$が$H\to O$で$\varphi \l(X_0\r)$に収束しないと仮定すると
任意の$n$に対して$\l|X_0+H_n-A\r| <\varepsilon$かつ

$$
\l|\varphi \l(X_0+H_n\r) -\varphi \l(X_0\r) \r| \geq \varepsilon '
$$

を満たす，$O$に収束するベクトル列$H_n\in \mathbb{R}^k$と$\varepsilon '>0$が存在する。
任意の$n$に対し$\varphi \l(X_0+H_n\r) \in I$が成り立つので$\left\{ \varphi \l(X_0+H_n\r) \right\}$の部分列$\left\{ \varphi \l(X_0+H_{n_l}\r) \right\}$で$I$内のある値$\alpha$に収束するものが存在する。
任意の$l$に対し$\l|\varphi \l(X_0+H_{n_l}\r) -\varphi \l(X_0\r) \r| \geq \varepsilon '$であることより$\alpha \neq \varphi \l(X_0\r)$であるが
$f$の連続性から

$$
f\l(X_0,\alpha \r) =\lim_{l \to \infty} f\l(X_0+H_{n_l},\varphi \left( X_0+H_{n_l} \right)\r)=0
$$

より$f\l(X_0,y_0\r) =0$なる$y_0\in I$が$y_0=\varphi \l(X_0\r)$しかないことから$\alpha =\varphi \l(X_0\r)$ということになってしまい矛盾。

##### $\varphi$が微分可能であること {#varphiが微分可能であること .unnumbered}

$x_1$で偏微分可能なことを示す。$\l(x_2,\dots,x_k \r) =X'$とおく。\
テイラーの定理より$k_1=\varphi \l(x_1+h_1,X'\r) -\varphi \l(x_1,X' \r)$として

$$
\begin{aligned}
&f\l(x_1+h_1,X',\varphi \l(x_1+h_1,X'\r) \r) \\ 
&=\, f\l(x_1,X',\varphi (x_1,X')\r) 
+f_{x_1}\l(x_1+\theta h_1,X',\varphi(x_1,X')+\theta k_1\r)h_1 \\
&\qq 
+f_{y }\l(x_1+\theta h_1,X',\varphi(x_1,X')+\theta k_1\r)k_1 \end{aligned}
$$

である。
$f\l(x_1+h_1,X',\varphi \l(x_1+h_1,X'\r) \r) = f\l(x_1,X',\varphi (x_1,X')\r) =0$より

$$
\begin{aligned}
\drac{\varphi \l(x_1+h_1,X'\r) -\varphi \l(x_1,X'\r) }{h_1}=\drac{k_1}{h_1}=-\drac{f_{x_1}\l(x_1+\theta h_1,X',\varphi(x_1,X')+\theta k_1\r)}{f_{y }\l(x_1+\theta h_1,X',\varphi(x_1,X')+\theta k_1\r)}\end{aligned}
$$

$\varphi$の連続性より$h_1\to 0$で$k_1\to 0$。よって$f_{x_1},f_{y}$の連続性より

$$
\begin{aligned}
\lim_{h_1 \to 0}\drac{\varphi \l(x_1+h_1,X'\r) -\varphi \l(x_1,X'\r) }{h_1}
=-\drac{f_{x_1}\l(x_1,X',\varphi(x_1,X')\r)}{f_{y }\l(x_1,X',\varphi(x_1,X')\r)}\end{aligned}
$$

$x_2,\dots,x_k$も同様に考えて$i=1,2,\dots,k$において

$$
\begin{aligned}
\delu{\varphi }{x_i}=-\drac{f_{x_i}\l(X,\varphi(X)\r)}{f_{y }\l(X,\varphi(X)\r)}\end{aligned}
$$

となるので$\varphi$は微分可能であることが示された。

##### $P\l(k,m\r)$について {#plkmrについて .unnumbered}

$\forall k\ P\l(k,1\r)$が真であることをもとにして$P\l(k+1,m\r)$から$P\l(k,m+1\r)$を示すことで帰納法を完成させる。
$P\l(k+1,m\r)$が真であると仮定する。$P\l(k,m+1\r)$の仮定は

(i) $f_{j}(A,b_{1},\dots,b_{m},b_{m+1})=0 \quad(j=1,\dots,m,m+1)$

(ii) $(A,b_{1},\dots,b_{m},b_{m+1})$において

$$
\begin{aligned}
  \left|\drac{\partial f}{\partial y}\right|=\begin{vmatrix}
  \drac{\partial f_{1} }{\partial y_{1}} & \dots &\drac{\partial f_{1} }{\partial y_{m}}
  &\drac{\partial f_{1} }{\partial y_{m+1}}\\
  \vdots &\ddots &\vdots &\vdots\\
  \drac{\partial f_{m} }{\partial y_{1}}&\dots & \drac{\partial f_{m} }{\partial y_{m}}&\vdots \\
  \drac{\partial f_{m+1} }{\partial y_{1}}&\dots &\dots&\drac{\partial f_{m+1} }{\partial y_{m+1}} 
  \end{vmatrix}
  \neq 0
  \end{aligned}
$$


である。このとき(2)の余因子展開から，うまく$y_{1},\dots,y_{m+1}$を選べば

$$
\drac{\partial f_{m+1} }{\partial y_{m+1}} 
 \begin{vmatrix}
 \delu{f_1}{y_1}& \dots & \delu{f_1}{y_m}\\ 
 \vdots  & \ddots &  \vdots \\  
 \delu{f_m}{y_1}& \dots & \delu{f_m}{y_m}
 \end{vmatrix}
 \neq 0
 \text{　　特に　　}
 \begin{vmatrix}
 \drac{\partial f_{1} }{\partial y_{1}} & \dots & \drac{\partial f_{1}}{\partial y_{m}} \\
 \vdots  & \ddots &\vdots \\
 \drac{\partial f_{m} }{\partial y_{1}} & \dots & \drac{\partial f_{m}}{\partial y_{m}}
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
$\drac{\partial F_{m+1} }{\partial y_{m+1}}\neq 0$ が成り立つ。
:::

::: proof
*Proof.* $|(X,y_{m+1})-(A,b_{m+1})|<\varepsilon_{1}$において$F_{j}=0$
($0$の定数関数)\
ゆえに$(A,b_{m+1})$において\

$$
\begin{split}
 &\drac{\partial F_{1} }{\partial y_{m+1}}=
 \drac{\partial f_{1} }{\partial y_{1}}\drac{\partial \varphi'_{1} }{\partial y_{m+1}}
 +\dots
 +\drac{\partial f_{1} }{\partial y_{m}}\drac{\partial \varphi'_{m} }{\partial y_{m+1}}
 +\drac{\partial f_{1} }{\partial y_{m+1}}=0\\
 &\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad\vdots\\
 &\drac{\partial F_{m} }{\partial y_{m+1}}=
 \drac{\partial f_{m} }{\partial y_{1}}\drac{\partial \varphi'_{1} }{\partial y_{m+1}}
 +\dots
 +\drac{\partial f_{m} }{\partial y_{m}}\drac {\partial \varphi'_{m} }{\partial y_{m+1}}
 +\drac{\partial f_{m} }{\partial y_{m+1}}=0
 \end{split}
$$

 このもとで

$$
\drac{\partial F_{m+1} }{\partial y_{m+1}}=
  \drac{\partial f_{m+1} }{\partial y_{1}}\drac{\partial \varphi'_{1} }{\partial y_{m+1}}
 +\dots
 +\drac{\partial f_{m+1} }{\partial y_{m}}\drac{\partial \varphi'_{m} }{\partial y_{m+1}}
 +\drac{\partial f_{m+1} }{\partial y_{m+1}}=0
$$

 を仮定すると

$$
\begin{pmatrix}
  \drac{\partial f_{1} }{\partial y_{1}} & \dots &\drac{\partial f_{1} }{\partial y_{m}}&\drac{\partial f_{1} }{\partial y_{m+1}}\\
 \vdots &\ddots &\vdots  &\vdots \\
 \drac{\partial f_{m} }{\partial y_{1}} &\dots &\drac{\partial f_{m} }{\partial y_{m}}&\vdots \\
 \drac{\partial f_{m+1} }{\partial y_{1}}&\dots &\dots  &\drac{\partial f_{m+1} }{\partial y_{m+1}} 
 \end{pmatrix}
 \begin{pmatrix}
 \drac{\partial \varphi'_{1} }{\partial y_{m+1}}\\
 \vdots\\
 \drac{\partial \varphi'_{m} }{\partial y_{m+1}}\\
 \displaystyle{1}
 \end{pmatrix}=\bm{0}
$$

であるが，これは$\left|\delu{f}{y}\right|\neq 0$に反し矛盾する。 ◻
:::

以上より

(i) $F_{m+1}\l(A,b_{m+1}\r) =0$

(ii) $\l(A,b_{m+1}\r)$ において$\delu{F_{m+1}}{y_{m+1}}\neq 0$

から$P(k,1)$によってある$\varepsilon_{2}>0$に対し$|X-A|<\varepsilon_{2}$上で

(1) $b_{m+1}=\varphi_{m+1}\l(A\r)$

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
f_j\l(X,\varphi _1\l(X\r) ,\dots,\varphi _m\l(X\r) \r) :=G_j\l(X\r) \end{aligned}
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
\pmat{
{\delu{f_1}{y_1}}& {\dots}& {\delu{f_1}{y_m}}\\
\vdots& \ddots& \vdots\\
\delu{f_m}{y_1}& \dots& \delu{f_m}{y_m}}
\pmat{ \delu{\varphi _1}{x_1}\\ \vdots \\\delu{\varphi _m}{x_1}}
=
- \pmat{
 \delu{f_1}{x_1}\\ \vdots\\ \delu{f_m}{x_1}
} \end{aligned}
$$

$i=2,\dots,k$で同じことを行うと

$$
\begin{aligned}
\pmat{
 \delu{f_1}{y_1}& \dots& \delu{f_1}{y_m}\\
 \vdots& \ddots& \vdots\\
 \delu{f_m}{y_1}& \dots& \delu{f_m}{y_m}
}
\pmat{
\delu{\varphi _1}{x_1}& \dots& \delu{\varphi _1}{x_k}\\
\vdots& \ddots& \vdots\\
\delu{\varphi _m}{x_1}& \dots& \delu{\varphi _m}{x_k} 
}
=
-
\pmat{
 \delu{f_1}{x_1}& \dots& \delu{f_1}{x_k}\\
 \vdots& \ddots & \vdots\\
 \delu{f_m}{x_1}& \dots& \delu{f_m}{x_k}
}\end{aligned}
$$

より

$$
\begin{aligned}
\delu{f}{y}\delu{\varphi }{x}=-\delu{f}{x}\end{aligned}
$$

すなわち

$$
\begin{aligned}
\delu{\varphi }{x}=-\l(\delu{f}{y}\l(X,\varphi \l(X\r) \r) \r) ^{-1}\delu{f}{x}\l(X,\varphi \l(X\r) \r) \end{aligned}
$$


$$
\begin{aligned}
 \pmat{
 \delu{\varphi _1}{x_1}& \dots& \delu{\varphi _1}{x_k}\\
 \vdots& \ddots& \vdots\\
 \delu{\varphi _m}{x_1}& \dots& \delu{\varphi _m}{x_k} 
 }
 =
 -\pmat{
 \delu{f_1}{y_1}& \dots& \delu{f_1}{y_m}\\
 \vdots& \ddots& \vdots\\
 \delu{f_m}{y_1}& \dots& \delu{f_m}{y_m}
 }^{\raisebox{3zw}[1zw][0zw]{\(-1\)}}
 \pmat{
 \delu{f_1}{x_1}& \dots& \delu{f_1}{x_k}\\
 \vdots& \ddots& \vdots\\
 \delu{f_m}{x_1}& \dots& \delu{f_m}{x_k}
 }
 \end{aligned}
$$

 帰納法の概略は下図のようである。\

#### 陰関数定理の別証

写像$T:\mathbb{R}^{k+m}\to \mathbb{R}^m$を以下のように定める。

$$
\begin{aligned}
T\l(X,Y\r) =Y-\l(\delu{f}{y}\l(A,B\r) \r) ^{-1}\bm{f}\l(X,Y\r) \end{aligned}
$$

このとき$T\l(A,B\r) =\delu{T}{y}\l(A,B\r) =\bm{0}$である。$T,\delu{T}{y}$の連続性から$\rho,\delta _\rho$をあらためて小さく取ると$\l|X-A\r| <\delta _\rho$かつ$\l|Y-B\r| <\rho$ならば

$$
\begin{aligned}
\l|\l|\delu{T}{y}\l(X,Y\r) \r| \r| <\drac{1}{2},\l|T\l(X,Y\r) -T\l(X,Y'\r) \r| <\drac{1}{2}\rho\text{　　かつ　　}\l|T\l(X,B\r) -B\r| <\drac{\rho}{3}\end{aligned}
$$

とできる。ただし，$\l|\l|\cdot \r| \r|$を行列のノルム，すなわち行列の成分の絶対値の最大値とした。

::: lemma
[]{#リプシッツ連続 label="リプシッツ連続"}
上の範囲で$X,Y$を取ると$\l|T\l(X,Y\r) -B\r| <\rho$
:::

::: proof
*Proof.*

$$
\begin{aligned}
 \l|T\l(X,Y\r) -B\r|& \leq \l|T\l(X,Y\r) -T\l(X,B\r) \r| +\l|T\l(X,B\r) -B\r| \\ 
 & \leq \drac{1}{2}\l|Y-B\r| +\drac{\rho}{3}\\ 
 &\leq \drac{1}{2}\rho+\drac{\rho}{3}<\rho
 \end{aligned}
$$
  ◻
:::

::: theorem
[]{#（バナッハの不動点定理） label="（バナッハの不動点定理）"}
（バナッハの不動点定理）$\Omega\in \mathbb{R}^m$とし，写像$T:\Omega\to \Omega$は任意の$X,Y\in \Omega$において$k\in \l(0,1\r)$として

$$
\begin{aligned}
 T\l(X\r) -T\l(Y\r) \leq k\l|X-Y\r| 
 \end{aligned}
$$

を満たすとする。このとき写像$T$は不動点をただ一つもつ。
:::

$X\in R\l(A,\delta _\rho\r)$を固定して写像$S$を

$$
\begin{aligned}
S\colon R\l(B,\rho\r)\to R\l(B,\rho\r),Y\mapsto T\l(X,Y\r) \end{aligned}
$$

によって定める（により$T$も$R\l(B,\rho\r)$に属する）と，定理[\[（バナッハの不動点定理）\]](#（バナッハの不動点定理）){reference-type="ref"
reference="（バナッハの不動点定理）"}より

$$
\begin{aligned}
S\l(Y\r) =Y　すなわち　\bm{f}\l(X,Y\r) =0 \end{aligned}
$$

となる$Y$が$X$に対してただ一つ存在することが示された。

### ラグランジュの未定乗数法

::: theorem
[]{#ラグランジュの未定乗数法
label="ラグランジュの未定乗数法"}（ラグランジュの未定乗数法）
$X=(x_{1},\dots,x_{k}) ,\, Y=(y_{1},\dots,y_{m})$とする。
$g_j(X,Y)=0 \,(j=1,\dots,m)$のもとで，$f(X,Y)$は$(X,Y)=(A,B)$において極値を取るものとする。$(A,B)$において

$$
\left|\drac{\partial g}{\partial y}\right|=
 \vmat{
 \drac{\partial g_1}{\partial y_1}& \dots& \drac{\partial g_1}{\partial y_m}\\
 \vdots& \ddots& \vdots \\
 \drac{\partial g_m}{\partial y_1}& \dots& \drac{\partial g_m}{\partial y_m}
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
 \pmat{
 \drac{\partial f}{\partial x_1}& \drac{\partial g_1}{\partial x_1}& \dots & \drac{\partial g_m}{\partial x_1}\\
 \vdots  & \vdots  & \ddots& \vdots  \\
 \drac{\partial f}{\partial x_k}& \drac{\partial g_1}{\partial x_k}& \dots & \drac{\partial g_m}{\partial x_k}\\
 \drac{\partial f}{\partial y_1}& \drac{\partial g_1}{\partial y_1}& \dots & \drac{\partial g_m}{\partial y_1}\\
 \vdots  & \vdots  & \ddots& \vdots  \\
 \drac{\partial f}{\partial y_m}& \drac{\partial g_1}{\partial y_m}& \dots& \drac{\partial g_m}{\partial y_m}
 }
 \pmat{
 1 \\ -\la_1 \\ \vdots \\ -\la_m
 }=\bm{0}
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
 \drac{\partial F}{\partial x_i}=\drac{\partial f}{\partial x_i}+\drac{\partial f}{\partial y_1}
 \drac{\partial \varphi_1}{\partial x_i} +\dots+\drac{\partial f}{\partial y_m}
 \drac{\partial \varphi_m}{\partial x_i}=0 
 \end{aligned}
$$

 常に$0$なので
 
$$
 \begin{aligned}
 \drac{\partial G_j}{\partial x_i}=\drac{\partial g_j}{\partial x_i}+\drac{\partial g_j}{\partial y_1}
 \drac{\partial \varphi_1}{\partial x_i} +\dots+\drac{\partial g_j}{\partial y_m}
 \drac{\partial \varphi_m}{\partial x_i}=0\q(j=1,\dots,m)
 \end{aligned}
$$

 したがって$X=A$において
 
$$
 \begin{aligned}
 \pmat{
 \drac{\partial f}{\partial x_i} & \drac{\partial f}{\partial y_1} & \dots & \drac{\partial f}{\partial y_m}\\
 \drac{\partial g_1}{\partial x_i} & \drac{\partial g_1}{\partial y_1} & \dots & \drac{\partial g_1}{\partial y_m}\\
 \vdots& \vdots& \ddots& \vdots\\
 \drac{\partial g_m}{\partial x_i} & \drac{\partial g_m}{\partial y_1} & \dots & \drac{\partial g_m}{\partial y_m}\\
 }
 \pmat{
 1 \\ \drac{\partial \varphi_1}{\partial x_i}\\ \vdots\\ \drac{\partial \varphi_m}{\partial x_i}
 }=\bm{0}\q(\text{左の行列$A_i$とおく})
 \end{aligned}
$$


より連立方程式$A_i \bm{x}=0$は$0$でない解を持つので$\rank(A_i)<m+1$。よって$\rank(A_i^ \mathrm{T})<m+1$より

$$
\begin{aligned}
 \pmat{
 \drac{\partial f}{\partial x_i} & \drac{\partial g_1}{\partial x_i} & \dots & \drac{\partial g_m}{\partial x_i}\\
 \drac{\partial f}{\partial y_1} & \drac{\partial g_1}{\partial y_1} & \dots & \drac{\partial g_m}{\partial y_1}\\
 \vdots& \vdots& \ddots& \vdots\\
 \drac{\partial f}{\partial y_m} & \drac{\partial g_1}{\partial y_m} & \dots & \drac{\partial g_m}{\partial y_m}\\
 }
 \pmat{
 \la'_f(i)\\ \la'_1(i)\\ \vdots\\ \la'_m(i) 
 }=\bm{0}
 \end{aligned}
$$

となる$(\la'_f(i),\la'_1(i),\dots,\la'_m(i))^ \mathrm{T}
 \neq \bm{0}$が存在する。
$\la'_f(i)\neq 0$を示す。$\la'_f(i)= 0$とすると

$$
\begin{aligned}
 \pmat{
 \drac{\partial g_1}{\partial y_1} & \dots & \drac{\partial g_m}{\partial y_1}\\
 \vdots& \ddots& \vdots\\
  \drac{\partial g_1}{\partial y_m} & \dots & \drac{\partial g_m}{\partial y_m}\\
 }
 \pmat{
  \la'_1(i)\\ \vdots\\ \la'_m(i) 
 }=\bm{0}\q\text{すなわち}\q\drac{\partial f}{\partial y}\bm{\la'}=\bm{0}
 \end{aligned}
$$

であって$\bm{\la'}\neq \bm{0}$なるものが存在するがこれは
$\left|\drac{\partial f}{\partial y}\right|\neq 0$に矛盾。
したがって$\la'_f(i) \neq 0$。
$-\drac{\la'_j(i)}{\la'_f(i)}=\la_j(i)$とすると，$i=1,\dots,k$に対し

$$
\begin{aligned}
 A_i^ \mathrm{T}
 \pmat{
 1 \\ -\la_1(i)\\ \vdots\\ -\la_m(i)
 }
 =A_i^ \mathrm{T}
 \pmat{
 1 \\
 -\bm{\la(i)}}=\bm{0}
 \end{aligned}
$$

 となる。 $\bm{\la(i)}$は$i$によらず，

$$
\begin{aligned}
 \pmat{
 \drac{\partial g_1}{\partial y_1} && \dots && \drac{\partial g_m}{\partial y_1}\\
 \vdots&& \ddots&& \vdots\\
  \drac{\partial g_1}{\partial y_m} && \dots && \drac{\partial g_m}{\partial y_m}\\
 }
 \pmat{
 t_1\\ \vdots\\t_m
 }=
 \pmat{
 \drac{\partial f}{\partial y_1}\\ \vdots\\ \drac{\partial f}{\partial y_m}
 }
 \end{aligned}
$$

の解であるが，$\left|\drac{\partial g}{\partial y}\right|\neq 0$よりそれは一つに限られる。
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
 \pmat{
 \drac{\partial f}{\partial x_1}& \drac{\partial g_1}{\partial x_1}& \dots& \drac{\partial g_m}{\partial x_1}\\
 \vdots  & \vdots  & \ddots& \vdots\\
 \drac{\partial f}{\partial x_k}& \drac{\partial g_1}{\partial x_k}& \dots& \drac{\partial g_m}{\partial x_k}\\
 \drac{\partial f}{\partial y_1}& \drac{\partial g_1}{\partial y_1}& \dots& \drac{\partial g_m}{\partial y_1}\\
 \vdots  & \vdots  & \ddots& \vdots\\
 \drac{\partial f}{\partial y_m}& \drac{\partial g_1}{\partial y_m}& \dots& \drac{\partial g_m}{\partial y_m}\\
 }
 \pmat{
 1 \\ -\la_1 \\ \vdots \\ -\la_m
 }=\bm{0}\q
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
\pmat{
 \la_1\\\vdots\\\la_m
}
=
\pmat{
 \delu{g_1}{y_1}&\dots&\delu{g_1}{y_m}\\
 \vdots&\ddots&\vdots\\
 \delu{g_m}{y_1}&\dots&\delu{g_m}{y_m}
}\l(A,B\r) 
^{\raisebox{3zw}[1zw][0zw]{\(-1\)}}
\pmat{
 \delu{f}{y_1}\\\vdots\\\delu{f}{y_m}
} \l(A,B\r)\end{aligned}
$$

である。未定乗数法自体が極値を与える$\l(A,B\r)$を求めるために用いられるものなので$\bm{\la}$は$\l(X,Y\r)$の式として与えられることがほとんどである。

### フーリエ級数展開

### 楕円積分論

$K\l(k\r) =\dis \int_{0}^{\drac{\pi }{2}} \drac{1}{\sqrt{1-k^2 \sin ^2 \theta }}\, d\theta ，E\l(k\r) =\dis \int_{0}^{\drac{\pi }{2}} 
{\sqrt{1-k^2 \sin ^2 \theta }}\, d\theta$とおく。ルジャンドルの公式を示したい。

#### 算術幾何平均に収束すること {#算術幾何平均に収束すること .unnumbered}

$\dis \int_{0}^{\drac{\pi }{2}} \drac{1}{\sqrt{a^2 \cos ^\theta +b^2 \sin ^2 \theta }}\, d\theta =M\l(a,b\r) =\lim_{n \to \infty}a_n=\lim_{n \to \infty}b_n$であることを示す。
ただし$a_{n+1}=\drac{1}{2}\l(a_n+b_n\r)， b_{n+1}=\sqrt{a_nb_n}$かつ$a_0=a,b_0=b$
とした。

#### 証明 {#証明-1 .unnumbered}

### リーマン積分の導入から円の面積を考える

行列式の定義，線形代数論，ベクトル解析，微分方程式，フーリエ変換，複素解析，複素関数への拡張，三角関数の部分分数展開，ジョルダン標準形
$n\geq 3 \Leftrightarrow \lnot \exists x,y,z \ s.t.\ x^n+y^n=z^n$

