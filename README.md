# Signal&System Review





是的，这个关系**非常重要**！可以说，它是连接时域分析、系统响应和变换域分析的桥梁之一。

### 为什么 $\int_{-\infty}^{t} \delta(\tau) d\tau = u(t)$ 很重要？

1.  **定义了最基本的信号关系**: 它从数学上将单位冲激 $\delta(t)$ 和单位阶跃 $u(t)$ 这两个最基本的构建模块联系在了一起。它的逆关系 $\frac{d}{dt}u(t)=\delta(t)$ 同样重要。
2.  [cite_start]**连接了冲激响应和阶跃响应**: 对于一个LTI系统，其单位阶跃响应 $s(t)$ 等于其单位冲激响应 $h(t)$ 的积分，即 $s(t) = \int_{-\infty}^{t} h(\tau) d\tau$。这个关系直接来自于你提出的公式。在你的试题册中，第11题就直接考察了冲激响应和阶跃响应的关系 [cite: 216, 217]。
3.  [cite_start]**是变换域性质的基础**: 这个关系是傅里叶变换和拉普拉斯变换中“时域积分性质”的基础。例如，在拉普拉斯域中，时域积分对应于在s域除以s。正是利用这个性质，我们可以从 $L\{\delta(t)\}=1$ 推导出 $L\{u(t)\} = \frac{1}{s}$ [cite: 306, 318]。

---

### 其他类似需要记牢的核心公式

[cite_start]除了这个积分关系，以下是一些在“信号与系统”课程中，特别是为了应对考试，强烈建议你记牢的核心公式和关系。这些内容在你的课件和考点大纲中都有体现 [cite: 268]。

#### 1. 冲激函数和阶跃函数相关

* **阶跃的导数是冲激**:
    $$\frac{d}{dt}u(t) = \delta(t)$$
* **筛选特性**:
    $$\int_{-\infty}^{\infty} x(t)\delta(t-t_0)dt = x(t_0)$$
* **乘积特性**:
    $$x(t)\delta(t-t_0) = x(t_0)\delta(t-t_0)$$
* **尺度变换**:
    $$\delta(at) = \frac{1}{|a|}\delta(t)$$

#### 2. LTI系统与卷积

* **时域卷积定义**:
    $$y(t) = x(t) * h(t) = \int_{-\infty}^{\infty} x(\tau) h(t-\tau) d\tau$$
* **与冲激的卷积 (筛选)**:
    $$x(t) * \delta(t-t_0) = x(t-t_0)$$
* [cite_start]**系统因果性**: $h(t) = 0$ 对于 $t<0$ [cite: 205]。
* [cite_start]**系统稳定性**: $\int_{-\infty}^{\infty} |h(t)| dt < \infty$ [cite: 204]。

#### 3. 傅里叶变换 (FT)

* **核心变换对 (必须记忆)**:
    * [cite_start]$\delta(t) \longleftrightarrow 1$ [cite: 15]
    * [cite_start]$1 \longleftrightarrow 2\pi\delta(\omega)$ [cite: 10]
    * [cite_start]$e^{-at}u(t) \longleftrightarrow \frac{1}{a+j\omega}, \quad (a>0)$ [cite: 8]
    * [cite_start]$e^{j\omega_0 t} \longleftrightarrow 2\pi\delta(\omega-\omega_0)$ [cite: 130]
    * [cite_start]$\cos(\omega_0 t) \longleftrightarrow \pi[\delta(\omega-\omega_0) + \delta(\omega+\omega_0)]$ [cite: 131]
* **核心性质 (必须会用)**:
    * [cite_start]**时移**: $x(t-t_0) \longleftrightarrow e^{-j\omega t_0}X(j\omega)$ [cite: 23, 64]
    * [cite_start]**频移**: $e^{j\omega_0 t}x(t) \longleftrightarrow X(j(\omega-\omega_0))$ [cite: 26, 68]
    * **时域微分**: $\frac{dx(t)}{dt} \longleftrightarrow j\omega X(j\omega)$
    * [cite_start]**时域卷积**: $x(t) * h(t) \longleftrightarrow X(j\omega)H(j\omega)$ [cite: 117]

#### 4. 拉普拉斯变换 (LT)

* **核心变换对**:
    * [cite_start]$\delta(t) \longleftrightarrow 1$ [cite: 318]
    * [cite_start]$u(t) \longleftrightarrow \frac{1}{s}$ [cite: 318]
    * [cite_start]$e^{-at}u(t) \longleftrightarrow \frac{1}{s+a}$ [cite: 318]
    * [cite_start]$t^n e^{-at}u(t) \longleftrightarrow \frac{n!}{(s+a)^{n+1}}$ (由s域微分性质可以推出) [cite: 304, 305]
* **核心性质**:
    * [cite_start]**时域微分**: $L\left\{\frac{dx(t)}{dt}\right\} = sX(s) - x(0^-)$ (零状态分析时通常为 $sX(s)$) [cite: 303]
    * **时域积分**: $L\left\{\int_{0}^{t} x(\tau) d\tau\right\} = \frac{1}{s}X(s)$
    * [cite_start]**时域卷积**: $x(t) * h(t) \longleftrightarrow X(s)H(s)$ [cite: 299]
    * **初值/终值定理** (对于因果信号):
        * [cite_start]初值: $x(0^+) = \lim_{s \to \infty} sX(s)$ [cite: 310, 316]
        * [cite_start]终值: $x(\infty) = \lim_{s \to 0} sX(s)$ (前提是系统稳定，极点在左半平面或原点有一个单极点) [cite: 313]

掌握这些核心的公式和关系，你就能解决绝大部分的“信号与系统”问题。它们是进行更复杂分析的基础。














# 第4章 傅里叶变换和系统的频域分析 - 4.2 傅里叶变换的性质

本章主要讨论连续时间傅里叶变换 (Continuous-Time Fourier Transform, CTFT) 的各种重要性质。傅里叶变换的定义如下：

* **正变换 (分析式):** $X(j\omega) = \mathcal{F}\{x(t)\} = \int_{-\infty}^{\infty} x(t)e^{-j\omega t} dt$
* **反变换 (综合式):** $x(t) = \mathcal{F}^{-1}\{X(j\omega)\} = \frac{1}{2\pi} \int_{-\infty}^{\infty} X(j\omega)e^{j\omega t} d\omega$

---

## 傅里叶变换的主要性质

### 1. 线性性质 (Linearity)

---

### 2. 时移性质 (Time Shifting)


---

### 3. 频移性质 (Frequency Shifting / Modulation)


**说明:**
* 信号在时域乘以复指数 $e^{j\omega_0 t}$ (调制)，其频谱在频域发生搬移，从基带搬移到以 $\omega_0$ 为中心的位置。
    * $\cos(\omega_0 t) \longleftrightarrow \pi[\delta(\omega-\omega_0) + \delta(\omega+\omega_0)]$ (取 $x(t)=1$)
    * $\sin(\omega_0 t) \longleftrightarrow \frac{\pi}{j}[\delta(\omega-\omega_0) - \delta(\omega+\omega_0)] = j\pi[\delta(\omega+\omega_0) - \delta(\omega-\omega_0)]$ (取 $x(t)=1$)
    * 求解矩形脉冲调幅信号 $g_\tau(t) \cos(\omega_0 t)$ 的频谱。

---

### 4. 时间反转性质 (Time Reversal)


**说明:**
* 时域信号的反转对应其频谱的反转。如果原频谱是 $X(j\omega)$，反转后的频谱是 $X(-j\omega)$。

---

### 5. 共轭对称性 (Conjugate Symmetry)

* **一般情况:** 如果 $x(t) \longleftrightarrow X(j\omega)$，则 $x^*(t) \longleftrightarrow X^*(-j\omega)$。

* **对于实信号 $x(t)$:** (即 $x(t) = x^*(t)$)
    $$ X(j\omega) = X^*(-j\omega) $$
    这意味着对于实信号 $x(t)$，其傅里叶变换 $X(j\omega) = R(\omega) + jI(\omega)$ 具有以下特性：
    * **实部偶对称:** $R(\omega) = R(-\omega)$
    * **虚部奇对称:** $I(\omega) = -I(-\omega)$
    * **模偶对称:** $|X(j\omega)| = |X(-j\omega)|$
    * **相位奇对称:** $\angle X(j\omega) = -\angle X(-j\omega)$

* **例题:**
    * 讨论 $e^{-a|t|}$ (实偶函数) 的频谱 $X(j\omega) = \frac{2a}{a^2+\omega^2}$ (实偶函数)。

---

### 6. 尺度变换性质 (Time and Frequency Scaling)

**说明:**
* **时域压缩 ($|a|>1$):** 信号在时域被压缩，则其频谱在频域相应扩展，且幅度减小 $1/|a|$ 倍。
* **时域扩展 ($0<|a|<1$):** 信号在时域被扩展，则其频谱在频域相应压缩，且幅度增加 $1/|a|$ 倍。
* **$a=-1$ 时即为时间反转性质。**
* **重要结论:** 信号的持续时间与其有效带宽成反比。压缩时域信号会扩展其频带，反之亦然。这在通信系统中是重要的权衡因素。

---

### 7. 时域微分与积分性质 (Differentiation and Integration in Time Domain)

#### A. 时域微分 (Differentiation)


#### B. 时域积分 (Integration)


---

### 8. 频域微分与积分性质 (Differentiation and Integration in Frequency Domain)

#### A. 频域微分 (Differentiation)

如果 $x(t) \longleftrightarrow X(j\omega)$，则：
$$ (-jt)^k x(t) \longleftrightarrow \frac{d^k X(j\omega)}{d\omega^k} $$
**说明:**
* 时域乘以因子 $(-jt)$ 对应于频域的微分运算。
* **例题:**
    * 求 $tu(t)$ 的频谱。已知 $u(t) \leftrightarrow \pi\delta(\omega) + \frac{1}{j\omega}$。
        $t u(t) \leftrightarrow j \frac{d}{d\omega} \left(\pi\delta(\omega) + \frac{1}{j\omega}\right) = j \left(\pi\delta'(\omega) - \frac{1}{j\omega^2}\right) = j\pi\delta'(\omega) + \frac{1}{\omega^2}$。
        (注: $\delta'(\omega)$ 是冲激偶。)

#### B. 频域积分 (Integration)

---

### 9. 对偶性 (Duality / Symmetry)

---

### 10. 卷积定理 (Convolution Theorem)

#### A. 时域卷积定理

#### B. 频域卷积定理 (通常也叫窗函数定理或乘积定理)

---

### 11. Parseval 定理 (Parseval's Relation / Energy Theorem)

---
