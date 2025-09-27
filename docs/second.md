---
title: 2次CPPLLモデル
tags:
  - PLL
---

## 元論文

- [Analysis of a charge-pump PLL: a new model (1994)](https://ieeexplore.ieee.org/document/297861)
- [Comment on "Analysis of a Charge-Pump PLL: A New Model" by M. van Paemel  (2019)](https://arxiv.org/abs/1810.02609)

## Corrected Van Paemel model

$\tau(k) \ge 0$ かつ $c \le 0$ のとき、

$$
\begin{align}
  \tau(k+1) = \frac{-b+\sqrt{b^2-4ac}}{2a}
\end{align}
$$

$\tau(k) \ge 0$ かつ $c > 0$ のとき、

$$
\begin{align}
  \tau(k+1) = \frac{1}{K_e v(k) + \omega_{vco}^{frec}} - T + (\tau(k) \pmod{T})
\end{align}
$$

$\tau(k) < 0$ かつ $l_b \le T$ のとき、

$$
\begin{align}
  \tau(k+1) = l_b - T
\end{align}
$$

$\tau(k) < 0$ かつ $l_b > T$ のとき、

$$
\begin{align}
  \tau(k+1) = \frac{-b+\sqrt{b^2-4ad}}{2a}
\end{align}
$$

ただし、

$$
\begin{align*}
  &a = \frac{K_v I_p}{2C} \\
  &b = \omega_\text{vco}(k) + K_v I_p R_2 \\
  &c = (T - (\tau(k) \pmod T))\times\omega_\text{vco}(k)  - 1 \\
  &l_b = \frac{1-S l_a}{\omega_\text{vco}(k)} \\
  &d = S l_a + T \omega_\text{vco}(k)  - 1 \\
  &S l_a = S l_k \pmod 1 \\
  &S l_k = -(\omega_\text{vco}(k) - I_p R_2 K_v)\tau(k) + K_v I_p \dfrac{\tau(k)^2}{2C}
\end{align*}
$$

電圧の更新式は、

$$
\begin{align}
  v(k+1) = v(k) + \frac{I_p}{C}\tau(k+1)
\end{align}
$$