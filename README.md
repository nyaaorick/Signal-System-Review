# Signal&System Review

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
