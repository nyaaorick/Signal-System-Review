# Signal&System Review

# 第4章 傅里叶变换和系统的频域分析 - 4.2 傅里叶变换的性质

本章主要讨论连续时间傅里叶变换 (Continuous-Time Fourier Transform, CTFT) 的各种重要性质。傅里叶变换的定义如下：

* **正变换 (分析式):** $X(j\omega) = \mathcal{F}\{x(t)\} = \int_{-\infty}^{\infty} x(t)e^{-j\omega t} dt$
* **反变换 (综合式):** $x(t) = \mathcal{F}^{-1}\{X(j\omega)\} = \frac{1}{2\pi} \int_{-\infty}^{\infty} X(j\omega)e^{j\omega t} d\omega$

---

## 傅里叶变换的主要性质

### 1. 线性性质 (Linearity)

如果 $x_1(t) \longleftrightarrow X_1(j\omega)$ 且 $x_2(t) \longleftrightarrow X_2(j\omega)$，则对于任意常数 $a$ 和 $b$：
$$ a x_1(t) + b x_2(t) \longleftrightarrow a X_1(j\omega) + b X_2(j\omega) $$
**说明:**
* 若干信号线性组合的傅里叶变换等于各个信号傅里叶变换的相同线性组合。
* **例题:** (幻灯片中通常会给出基于已知变换对，利用线性性质求解复杂信号频谱的例子，例如求解 $f(t) = 1 - g_2(t)$ 的频谱，其中 $1 \leftrightarrow 2\pi\delta(\omega)$，$g_2(t)$ 为门函数。)

---

### 2. 时移性质 (Time Shifting)

如果 $x(t) \longleftrightarrow X(j\omega)$，则：
$$ x(t-t_0) \longleftrightarrow e^{-j\omega t_0} X(j\omega) $$
**说明:**
* 信号在时域的平移，其傅里叶变换的幅度谱不变，仅引入一个与平移量 $t_0$ 和频率 $\omega$ 相关的线性相移 $- \omega t_0$。
* **例题:** (幻灯片中可能包含求解如 $g_6(t-5)$ 等移位信号频谱的例子。)

---

### 3. 频移性质 (Frequency Shifting / Modulation)

如果 $x(t) \longleftrightarrow X(j\omega)$，则：
$$ e^{j\omega_0 t} x(t) \longleftrightarrow X(j(\omega-\omega_0)) $$
**说明:**
* 信号在时域乘以复指数 $e^{j\omega_0 t}$ (调制)，其频谱在频域发生搬移，从基带搬移到以 $\omega_0$ 为中心的位置。
* **重要推论 (余弦调制):**
    $$ x(t)\cos(\omega_0 t) = x(t) \frac{e^{j\omega_0 t} + e^{-j\omega_0 t}}{2} \longleftrightarrow \frac{1}{2}[X(j(\omega-\omega_0)) + X(j(\omega+\omega_0))] $$
    信号乘以余弦函数，频谱会分裂成两半，分别搬移到 $\pm \omega_0$ 处，幅度减半。
* **重要推论 (正弦调制):**
    $$ x(t)\sin(\omega_0 t) = x(t) \frac{e^{j\omega_0 t} - e^{-j\omega_0 t}}{2j} \longleftrightarrow \frac{1}{2j}[X(j(\omega-\omega_0)) - X(j(\omega+\omega_0))] $$
* **例题:**
    * $e^{j3t} \longleftrightarrow 2\pi\delta(\omega-3)$ (取 $x(t)=1 \leftrightarrow 2\pi\delta(\omega)$)
    * $\cos(\omega_0 t) \longleftrightarrow \pi[\delta(\omega-\omega_0) + \delta(\omega+\omega_0)]$ (取 $x(t)=1$)
    * $\sin(\omega_0 t) \longleftrightarrow \frac{\pi}{j}[\delta(\omega-\omega_0) - \delta(\omega+\omega_0)] = j\pi[\delta(\omega+\omega_0) - \delta(\omega-\omega_0)]$ (取 $x(t)=1$)
    * 求解矩形脉冲调幅信号 $g_\tau(t) \cos(\omega_0 t)$ 的频谱。

---

### 4. 时间反转性质 (Time Reversal)

如果 $x(t) \longleftrightarrow X(j\omega)$，则：
$$ x(-t) \longleftrightarrow X(-j\omega) $$
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

* **进一步推论 (对于实信号 $x(t)$):**
    * 如果 $x(t)$ 是实偶函数 ($x(t)=x(-t)$)，则 $X(j\omega)$ 是实偶函数 (即 $I(\omega)=0$)。
        $$ x(t) \text{ (实偶)} \longleftrightarrow X(j\omega) \text{ (实偶)} $$
    * 如果 $x(t)$ 是实奇函数 ($x(t)=-x(-t)$)，则 $X(j\omega)$ 是纯虚奇函数 (即 $R(\omega)=0$)。
        $$ x(t) \text{ (实奇)} \longleftrightarrow X(j\omega) \text{ (纯虚奇)} $$
    * 实信号 $x(t)$ 的偶部 $x_e(t) = \frac{x(t)+x(-t)}{2}$ 的傅里叶变换等于 $X(j\omega)$ 的实部 $R(\omega)$。
        $$ x_e(t) \longleftrightarrow \text{Re}\{X(j\omega)\} $$
    * 实信号 $x(t)$ 的奇部 $x_o(t) = \frac{x(t)-x(-t)}{2}$ 的傅里叶变换等于 $j$ 乘以 $X(j\omega)$ 的虚部 $jI(\omega)$。
        $$ x_o(t) \longleftrightarrow j\text{Im}\{X(j\omega)\} $$
* **例题:**
    * 讨论 $e^{-a|t|}$ (实偶函数) 的频谱 $X(j\omega) = \frac{2a}{a^2+\omega^2}$ (实偶函数)。

---

### 6. 尺度变换性质 (Time and Frequency Scaling)

如果 $x(t) \longleftrightarrow X(j\omega)$，则对于非零实常数 $a$：
$$ x(at) \longleftrightarrow \frac{1}{|a|} X\left(j\frac{\omega}{a}\right) $$
**说明:**
* **时域压缩 ($|a|>1$):** 信号在时域被压缩，则其频谱在频域相应扩展，且幅度减小 $1/|a|$ 倍。
* **时域扩展 ($0<|a|<1$):** 信号在时域被扩展，则其频谱在频域相应压缩，且幅度增加 $1/|a|$ 倍。
* **$a=-1$ 时即为时间反转性质。**
* **重要结论:** 信号的持续时间与其有效带宽成反比。压缩时域信号会扩展其频带，反之亦然。这在通信系统中是重要的权衡因素。
* **例题:**
    * 已知 $f(t) \leftrightarrow F(j\omega)$，求 $f(at-b)$ 的傅里叶变换。
        * 解法1: 先时移后尺度变换: $f(t-b/a) \leftrightarrow e^{-j\omega b/a} F(j\omega)$，则 $f(a(t-b/a)) \leftrightarrow \frac{1}{|a|} e^{-j(\omega/a) b/a} F(j\omega/a) = \frac{1}{|a|} e^{-j\omega b/a^2} F(j\omega/a)$  (这里原PPT中似乎有一个小笔误，应为 $e^{-j\omega b/a} F(j\omega/a)$ 结合时移是在尺度变换之前的变量上)
        * 标准解法: 令 $y(t) = x(at)$，则 $Y(j\omega) = \frac{1}{|a|}X(j\frac{\omega}{a})$。令 $z(t) = y(t-b_0) = x(a(t-b_0))$。若要求 $f(at-b)=f(a(t-b/a))$，则 $t_0 = b/a$。
            $f(at-b) \longleftrightarrow \frac{1}{|a|} e^{-j(\omega/a)b} F\left(j\frac{\omega}{a}\right)$。
    * 考题形式：若 $F_1(j\omega) = \mathcal{F}\{f_1(t)\}$，则 $\mathcal{F}\{f_1(4-2t)\}$ 等于？
        $f_1(4-2t) = f_1(-2(t-2))$。令 $a=-2, t_0=2$。
        $\mathcal{F}\{f_1(-2(t-2))\} = \frac{1}{|-2|} e^{-j(\omega/(-2))2} F_1\left(j\frac{\omega}{-2}\right) = \frac{1}{2} e^{j\omega} F_1\left(-j\frac{\omega}{2}\right)$。

---

### 7. 时域微分与积分性质 (Differentiation and Integration in Time Domain)

#### A. 时域微分 (Differentiation)

如果 $x(t) \longleftrightarrow X(j\omega)$，则其 $k$ 阶导数：
$$ \frac{d^k x(t)}{dt^k} \longleftrightarrow (j\omega)^k X(j\omega) $$
**说明:**
* 时域的微分运算对应于频域乘以因子 $(j\omega)$。
* 微分运算会突出信号的高频分量。
* **应用条件:** 如果 $x(t)$ 包含冲激或不连续点，直接应用此性质求导后的傅里叶变换可能需要谨慎，有时需要结合广义函数理论。对于有直流分量的信号，积分性质使用时需注意 $\pi X(0)\delta(\omega)$ 项。
* **例题:**
    * 利用单位阶跃 $u(t)$ 的导数为 $\delta(t)$ 来验证。 $\mathcal{F}\{\delta(t)\} = 1$，$j\omega \mathcal{F}\{u(t)\} = j\omega (\pi\delta(\omega) + \frac{1}{j\omega}) = j\omega\pi\delta(\omega) + 1 = 1$ (因为 $\omega\delta(\omega)=0$)。
    * 求解三角波、锯齿波等分段线性信号的频谱，通常先对其求导得到矩形波或冲激串，求出导函数的频谱后再除以 $(j\omega)$。

#### B. 时域积分 (Integration)

如果 $x(t) \longleftrightarrow X(j\omega)$，则：
$$ \int_{-\infty}^{t} x(\tau)d\tau \longleftrightarrow \frac{1}{j\omega}X(j\omega) + \pi X(0)\delta(\omega) $$
其中 $X(0) = \int_{-\infty}^{\infty} x(t)dt$ (即频谱在 $\omega=0$ 处的值)。
**说明:**
* 时域的积分运算对应于频域除以因子 $(j\omega)$，并可能在 $\omega=0$ 处附加一个冲激项。
* $\pi X(0)\delta(\omega)$ 项表示积分后可能产生的新的直流分量。如果原信号的直流分量 $X(0)=0$ (即 $\int_{-\infty}^{\infty} x(t)dt = 0$)，则此冲激项为零。
* 积分运算会突出信号的低频分量。
* **常用形式 (若积分结果的直流分量为零):**
    如果 $\int_{-\infty}^{\infty} (\int_{-\infty}^{t} x(\tau)d\tau) dt = 0$，或者说如果能保证积分后信号的频谱在 $\omega=0$ 处没有冲激，则可以简化为 $\frac{1}{j\omega}X(j\omega)$。
    更准确地说，如果 $\int_{-\infty}^{\infty} x(t)dt = 0$，则 $\int_{-\infty}^{t} x(\tau)d\tau \longleftrightarrow \frac{1}{j\omega}X(j\omega)$。
* **例题:**
    * 利用 $\delta(t)$ 的积分为 $u(t)$ 来验证。$\mathcal{F}\{u(t)\} = \pi\delta(\omega) + \frac{1}{j\omega}$。$\frac{1}{j\omega}\mathcal{F}\{\delta(t)\} + \pi \mathcal{F}\{\delta(t)\}|_{\omega=0} \delta(\omega) = \frac{1}{j\omega}(1) + \pi (1) \delta(\omega)$。
    * 利用积分特性求已知导函数频谱的原始信号频谱。
    * 利用积分特性求图示信号 (如三角波由两个斜坡信号积分得到矩形脉冲的例子) 的频谱函数。

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

如果 $x(t) \longleftrightarrow X(j\omega)$，则：
$$ \frac{x(t)}{-jt} + \pi x(0)\delta(t) \longleftrightarrow \int_{-\infty}^{\omega} X(j\eta)d\eta $$
其中 $x(0)$ 是时域信号在 $t=0$ 处的值。
或者，如果时域信号在原点值为零 (即 $x(0)=0$)：
$$ \frac{x(t)}{-jt} \longleftrightarrow \int_{-\infty}^{\omega} X(j\eta)d\eta \quad (\text{if } x(0)=0) $$
**说明:**
* 这是一个与时域积分对偶的性质，但不像时域积分那样常用。

---

### 9. 对偶性 (Duality / Symmetry)

如果 $x(t) \longleftrightarrow X(j\omega)$，那么将频谱函数 $X(j\omega)$ 中的 $j\omega$ 替换为 $jt$，得到的新时域函数 $X(jt)$，其傅里叶变换为 $2\pi x(-\omega)$ (即将原时域函数 $x(t)$ 中的 $t$ 换成 $-\omega$，再乘以 $2\pi$)。
$$ X(jt) \longleftrightarrow 2\pi x(-\omega) $$
**说明:**
* 傅里叶变换的正变换和反变换在形式上非常相似，这种相似性导致了对偶性质。
* 该性质可以方便地由已知的变换对推导出新的变换对。
* **例题:**
    * 已知 $\delta(t) \longleftrightarrow 1$。令 $x(t)=\delta(t)$, $X(j\omega)=1$。则 $X(jt)=1$ (时域信号为常数1)。
        $1 \longleftrightarrow 2\pi \delta(-\omega) = 2\pi \delta(\omega)$。
    * 已知矩形脉冲 $g_{2T_1}(t) = \begin{cases} 1, & |t|<T_1 \\ 0, & |t|>T_1 \end{cases} \longleftrightarrow 2T_1 \text{Sa}(\omega T_1)$ (其中 $\text{Sa}(x) = \sin(x)/x$)。
        令 $X(j\omega) = g_{2T_1}(\omega)$ (频域的矩形脉冲)。则 $X(jt) = g_{2T_1}(t)$ (时域的矩形脉冲)。
        根据对偶性，$g_{2T_1}(t) \longleftrightarrow 2\pi \left[ \frac{1}{2\pi} 2T_1 \text{Sa}(-t T_1) \right]$ (这里需要小心应用，形式应为 $X(j\omega)$)。
        应该这样用：
        已知 $x_1(t) = g_{2T_1}(t) \longleftrightarrow X_1(j\omega) = 2T_1 \text{Sa}(\omega T_1)$。
        现在考虑时域信号 $x_2(t) = 2T_1 \text{Sa}(t T_1)$。我们想求 $X_2(j\omega)$。
        根据对偶性，如果 $X_1(jt) \longleftrightarrow 2\pi x_1(-\omega)$。
        令 $X_1(j\omega)$ 的形式对应一个时域函数 $Y(t) = 2T_1 \text{Sa}(\omega_c t)$，其频谱是 $G(\omega)$。
        更直接的应用：
        我们有 $x(t) = \frac{\sin(W t)}{\pi t} = \frac{W}{\pi} \text{Sa}(Wt) \longleftrightarrow X(j\omega) = \begin{cases} 1, & |\omega|<W \\ 0, & |\omega|>W \end{cases}$ (即理想低通滤波器的冲激响应)。
        令 $X_0(t) = \begin{cases} 1, & |t|<W \\ 0, & |t|>W \end{cases}$ (时域矩形窗)。其频谱为 $2W \text{Sa}(\omega W)$。
        应用对偶性： $2W \text{Sa}(tW) \longleftrightarrow 2\pi \left( \begin{cases} 1, & |-\omega|<W \\ 0, & |-\omega|>W \end{cases} \right) = 2\pi \begin{cases} 1, & |\omega|<W \\ 0, & |\omega|>W \end{cases}$。
        所以 $\text{Sa}(tW) \longleftrightarrow \frac{\pi}{W} \begin{cases} 1, & |\omega|<W \\ 0, & |\omega|>W \end{cases}$。
    * 求 $\frac{2}{1+t^2}$ 的傅里叶变换。
        已知 $e^{-a|t|} \longleftrightarrow \frac{2a}{a^2+\omega^2}$。
        令 $a=1$, $x(t) = e^{-|t|} \longleftrightarrow X(j\omega) = \frac{2}{1+\omega^2}$。
        根据对偶性，$X(jt) = \frac{2}{1+(jt)^2} = \frac{2}{1-t^2}$ (这与例子不符，说明选取的初始对不对)。
        应选取 $X(jt)$ 为我们想求的函数形式。
        令 $X_1(j\omega) = e^{-a|\omega|}$。根据对偶性，时域信号 $x_1(t)$ 为 $\frac{1}{2\pi} \frac{2a}{a^2+t^2}$。
        所以 $\frac{2a}{a^2+t^2} \longleftrightarrow 2\pi e^{-a|-\omega|} = 2\pi e^{-a|\omega|}$。
        若要求 $\mathcal{F}\{\frac{2}{1+t^2}\}$，则令 $a=1$，得到 $\frac{2}{1+t^2} \longleftrightarrow 2\pi e^{-|\omega|}$。

---

### 10. 卷积定理 (Convolution Theorem)

#### A. 时域卷积定理

如果 $x_1(t) \longleftrightarrow X_1(j\omega)$ 且 $x_2(t) \longleftrightarrow X_2(j\omega)$，则：
$$ x_1(t) * x_2(t) = \int_{-\infty}^{\infty} x_1(\tau)x_2(t-\tau)d\tau \longleftrightarrow X_1(j\omega)X_2(j\omega) $$
**说明:**
* 两个信号在时域的卷积，其傅里叶变换等于这两个信号傅里叶变换的乘积。
* 这是LTI（线性时不变）系统分析的核心。如果 $x(t)$ 是LTI系统的输入，$h(t)$ 是系统的单位冲激响应，则输出 $y(t) = x(t) * h(t)$。其频谱关系为 $Y(j\omega) = X(j\omega)H(j\omega)$，其中 $H(j\omega)$ 是系统的频率响应。
* **例题:** (通常涉及LTI系统响应的计算)

#### B. 频域卷积定理 (通常也叫窗函数定理或乘积定理)

如果 $x_1(t) \longleftrightarrow X_1(j\omega)$ 且 $x_2(t) \longleftrightarrow X_2(j\omega)$，则：
$$ x_1(t)x_2(t) \longleftrightarrow \frac{1}{2\pi} [X_1(j\omega) * X_2(j\omega)] = \frac{1}{2\pi} \int_{-\infty}^{\infty} X_1(j\eta)X_2(j(\omega-\eta))d\eta $$
**说明:**
* 两个信号在时域的乘积，其傅里叶变换等于这两个信号傅里叶变换的卷积，并乘以因子 $1/(2\pi)$。
* 此定理在调制、采样和加窗等操作的频谱分析中非常重要。
* **例题:** 解释调制过程的频域表现。例如 $x(t)\cos(\omega_0 t)$，其中 $\cos(\omega_0 t) \leftrightarrow \pi[\delta(\omega-\omega_0)+\delta(\omega+\omega_0)]$。
    $\mathcal{F}\{x(t)\cos(\omega_0 t)\} = \frac{1}{2\pi} X(j\omega) * (\pi[\delta(\omega-\omega_0)+\delta(\omega+\omega_0)]) = \frac{1}{2}[X(j(\omega-\omega_0)) + X(j(\omega+\omega_0))]$，与频移性质结果一致。

---

### 11. Parseval 定理 (Parseval's Relation / Energy Theorem)

对于能量信号 $x(t)$ (即能量有限 $\int_{-\infty}^{\infty} |x(t)|^2 dt < \infty$)，如果 $x(t) \longleftrightarrow X(j\omega)$，则：
$$ E = \int_{-\infty}^{\infty} |x(t)|^2 dt = \frac{1}{2\pi} \int_{-\infty}^{\infty} |X(j\omega)|^2 d\omega $$
**说明:**
* 信号在时域的总能量等于其傅里叶变换模的平方在频域积分并除以 $2\pi$。
* $|X(j\omega)|^2$ 称为信号的**能量谱密度 (Energy Spectral Density, ESD)**，表示单位频率带宽内的信号能量。
* 此定理表明傅里叶变换保持了信号的能量。
* **应用:**
    * 计算信号能量。
    * 计算积分，例如计算 $\int_{-\infty}^{\infty} \text{Sa}^2(t) dt$。
        已知矩形脉冲 $g_1(t) = \begin{cases} 1, & |t|<1/2 \\ 0, & \text{else} \end{cases} \longleftrightarrow \text{Sa}(\omega/2)$。
        能量 $E_g = \int_{-1/2}^{1/2} 1^2 dt = 1$。
        $1 = \frac{1}{2\pi} \int_{-\infty}^{\infty} |\text{Sa}(\omega/2)|^2 d\omega$。令 $u=\omega/2$, $d\omega=2du$。
        $1 = \frac{1}{2\pi} \int_{-\infty}^{\infty} \text{Sa}^2(u) (2du) = \frac{1}{\pi} \int_{-\infty}^{\infty} \text{Sa}^2(u) du$。
        所以 $\int_{-\infty}^{\infty} \text{Sa}^2(u) du = \pi$。
        因此 $\int_{-\infty}^{\infty} \text{Sa}^2(t) dt = \pi$。
* **例题:**
    * 试确定信号 $x(t) = \frac{\sin(t)}{\pi t}$ 的能量。
        $x(t) = \text{Sa}(t)/\pi$。已知 $\text{Sa}(t) \longleftrightarrow \pi \cdot g_2(\omega)$ (其中 $g_2(\omega)$ 是幅度为1，宽度从-1到1的矩形窗)。
        $X(j\omega) = \mathcal{F}\{\text{Sa}(t)/\pi\} = g_2(\omega) = \begin{cases} 1, & |\omega|<1 \\ 0, & \text{else} \end{cases}$。
        $E_x = \frac{1}{2\pi} \int_{-\infty}^{\infty} |g_2(\omega)|^2 d\omega = \frac{1}{2\pi} \int_{-1}^{1} 1^2 d\omega = \frac{1}{2\pi} [ \omega ]_{-1}^{1} = \frac{1}{2\pi}(1 - (-1)) = \frac{2}{2\pi} = \frac{1}{\pi}$。

---

### 总结与应用

傅里叶变换的这些性质极大地简化了信号与系统（特别是LTI系统）的分析。通过将时域运算（如卷积、微分）转换到频域进行更简单的代数运算（如乘积、乘以 $j\omega$），可以更方便地求解系统响应、分析信号频谱特性等。讲义中通常会包含多个综合运用这些性质的例题和思考题。

例如：
* 已知输入信号 $x(t)$ 和系统冲激响应 $h(t)$，求输出 $y(t)$ 的频谱 $Y(j\omega)$ 或时域表达式 $y(t)$。
* 已知 $x(t) \leftrightarrow X(j\omega)$，利用性质求更复杂信号（如 $x(at-b)$, $t^n x(t)$, $x_1(t)x_2(t)$ 等）的频谱。
* 利用Parseval定理计算信号能量或特定积分值。

