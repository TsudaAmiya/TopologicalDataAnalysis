# 最尤法

## 定義

> **定義 1（最尤法）**
>
> $(\Omega, \mathcal{F}, \mu)$ を測度空間とする。
>
> $\Theta$ をパラメータ空間とし、各 $\theta \in \Theta$ に対して $p_\theta : \Omega \to [0,\infty)$ は可測関数であり、
>
> $$
> \int_{\Omega} p_\theta(x) \, d\mu(x) = 1
> $$
>
> を満たすものとする。(※つまり、$p_\theta$ によって定まる確率測度 $\mathbb{P}_\theta(A) := \int_A p_\theta(x) d\mu(x)$ を考えている。)
>
> 観測データ $x = (x_1, \dots, x_n) \in \Omega^n$ が得られたとき、**尤度関数** $L : \Theta \times \Omega^n \to [0, \infty)$ を：
>
> $$
> L(\theta; x) := \prod_{i=1}^n p_\theta(x_i)
> $$
>
> により定義する。
>
> そして、$x$ を固定したときにこの関数を最大化する $\theta \in \Theta$ を最尤推定量といい、その一つを$\theta_x$とかく。
>
> このとき、最尤推定は「$x$ を生じさせた真の分布は $(p_\theta)_{\theta \in \Theta}$ のうち何らかである」と仮定し、$x$ に最も尤もらしいパラメータ $\theta_x$ を推定する手法である。

> **定義 2（対数尤度関数）**
> 
> $\log$が単調増加であるので、$\theta$に対し、$L(\theta; x)$を最大化することと$\log L(\theta; x)$を最大化することは同値なので、そちらが計算が楽な場合はそちらで行いたい。
> $$
> l(\theta; x) := \log L(\theta; x)
> $$
> を対数尤度関数と呼ぶ。


## 例1 重さに偏りのあるコイン
> **現実の問題設定**
>
> 重さに偏りがあり、表が出る確率が $\theta \in [0,1]$の謎のコインがあるとする。
> 
> $10$回振ってみて結果が(表, 表, 表, 表, 表, 表, 表, 表, 裏, 裏)であった。
> 
> $\theta$はなんだったとするのが最も尤もらしい？

↓

> **数学の問題設定**
>
> $\Omega = \{0,1\}$, 
> 
> $\mathcal{F} = \{\emptyset, \{0\}, \{1\}, \{0,1\}\}$, 
> 
> $\mu(A) = \frac{1}{2} \cdot |A|$ （$|A|$ は集合 $A$ の要素数）
>
> $\Theta = [0,1]$
>
> $$
>p_\theta(x) :=
>\begin{cases}
>\theta & \text{if } x = 1 \\
>1 - \theta & \text{if } x = 0
>\end{cases}
>$$
>
> $x = (1,1,1,1,1,1,1,1,0,0)$
>
> この状況下で最尤推定を行え。


$$
L(\theta; x) := \prod_{i=1}^{10} p_\theta(x_i)
= \prod_{i=1}^{10} \theta^{x_i} (1 - \theta)^{1 - x_i}
$$

ここで、$x_i = 1$ が8回、$x_i = 0$ が2回なので、

$$
L(\theta; x) = \theta^8 (1 - \theta)^2
$$

である。ふつうに微分して増減表を書けば、$\theta = \frac{8}{10}$で最大となることがわかる。


---

## 例2 正規分布に従うデータ（平均・分散とも未知）

> **現実の問題設定**
>
> 身長のような連続的な量が正規分布に従うと仮定する。
> ある集団からランダムに5人を選んだところ、身長は次の通りであった：
> $170, 172, 168, 171, 169$（単位 cm）。
>
> この観測データを最もよく説明する正規分布の平均 $\mu$ および分散 $\sigma^2$ を推定せよ。

↓

> **数学の問題設定**
>
> 測度空間 $(\Omega, \mathcal{F}, \mu)$ を：
>
> $\Omega = \mathbb{R}$ 
> 
> $\mathcal{F}$：ルベーグ可測集合
> 
> $\mu$：ルベーグ測度
>
> パラメータ空間：$\Theta = \{ (\mu, \sigma) \in \mathbb{R} \times (0, \infty) \}$
>
> 各 $\theta = (\mu, \sigma)$ に対し、確率密度関数 $p_{\mu, \sigma}$ は：
>
> $$
> p_{\mu, \sigma}(x) := \frac{1}{\sqrt{2\pi \sigma^2}} \exp\left( -\frac{(x - \mu)^2}{2\sigma^2} \right)
> $$
>
> 観測データ：
>
> $$
> x = (170, 172, 168, 171, 169)
> $$
>
> このとき、最尤推定を行え。

---

### 尤度関数

観測データ $x = (x_1, \dots, x_5)$ に対して：

$$
L(\mu, \sigma; x) = \prod_{i=1}^5 \frac{1}{\sqrt{2\pi \sigma^2}} \exp\left( -\frac{(x_i - \mu)^2}{2\sigma^2} \right)
= \left( \frac{1}{\sqrt{2\pi \sigma^2}} \right)^5 \exp\left( -\frac{1}{2\sigma^2} \sum_{i=1}^5 (x_i - \mu)^2 \right)
$$

---

### 対数尤度関数

$$
l(\mu, \sigma; x) := \log L(\mu, \sigma; x) = -\frac{5}{2} \log(2\pi \sigma^2) - \frac{1}{2\sigma^2} \sum_{i=1}^5 (x_i - \mu)^2
$$


---

### Step 1: $\mu$ で偏微分して、最適条件を求める

まず、$\sigma$を固定して、$l(\mu, \sigma; x)$ を$\mu$で偏微分する。

$$
\frac{\partial l}{\partial \mu}
= -\frac{1}{2\sigma^2} \cdot 2 \sum_{i=1}^5 (x_i - \mu)(-1)
= \frac{1}{\sigma^2} \sum_{i=1}^5 (x_i - \mu)
$$

これが0になるとき、

$$
\sum_{i=1}^5 (x_i - \mu) = 0
\quad \Rightarrow \quad
5\mu = \sum_{i=1}^5 x_i \quad \Rightarrow \quad \mu = \frac{1}{5} \sum_{i=1}^5 x_i
$$

よって、最尤推定量 $\hat{\mu}$ は標本平均：

$$
\hat{\mu} = \bar{x} = \frac{170 + 172 + 168 + 171 + 169}{5} = \frac{850}{5} = 170
$$

---

### Step 2: $\sigma$ で偏微分して、最適条件を求める

$\mu = \hat{\mu}$ を代入して、$l$ を$\sigma$で偏微分する。

$$
\frac{\partial l}{\partial \sigma}
= -\frac{5}{\sigma} + \frac{1}{\sigma^3} \sum_{i=1}^5 (x_i - \hat{\mu})^2
$$

これを0とおくと、

$$
-\frac{5}{\sigma} + \frac{1}{\sigma^3} \sum_{i=1}^5 (x_i - \hat{\mu})^2 = 0
\quad \Rightarrow \quad
\frac{1}{\sigma^3} \sum_{i=1}^5 (x_i - \hat{\mu})^2 = \frac{5}{\sigma}
$$

両辺に$\sigma^3$をかけると、

$$
\sum_{i=1}^5 (x_i - \hat{\mu})^2 = 5\sigma^2
\quad \Rightarrow \quad
\hat{\sigma}^2 = \frac{1}{5} \sum_{i=1}^5 (x_i - \hat{\mu})^2
$$

---

### Step 3: 実際に数値を代入して計算

$\hat{\mu} = 170$ に対して：

$$
\begin{align*}
(x_i - \hat{\mu})^2 &= (170 - 170)^2 + (172 - 170)^2 + (168 - 170)^2 + (171 - 170)^2 + (169 - 170)^2 \\
&= 0^2 + 2^2 + (-2)^2 + 1^2 + (-1)^2 \\
&= 0 + 4 + 4 + 1 + 1 = 10
\end{align*}
$$

よって：

$$
\hat{\sigma}^2 = \frac{10}{5} = 2 \quad \Rightarrow \quad \hat{\sigma} = \sqrt{2}
$$

---

## **結論：最尤推定量**

* 平均の最尤推定値：

  $$
  \hat{\mu} = 170
  $$

* 分散の最尤推定値：

  $$
  \hat{\sigma}^2 = 2, \quad \hat{\sigma} = \sqrt{2}
  $$

この正規分布 $N(170, 2)$ が、与えられた観測データに対して最も尤もらしいモデル（＝最尤推定）になる。


