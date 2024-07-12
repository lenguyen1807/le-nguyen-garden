---
source: "[[Study/Math knowledge\|Math knowledge]]"
id: 202404251854
date_create: 2024-04-25
dg-publish: true
---
>[!success]+ Nhắc lại
>Kì vọng của phân phối chuẩn:
>$$
\mathbb{E}[X] = \int_{-\infty}^{\infty} \mathcal{N}(x \mid \mu, \sigma^2) x dx = \mu
>$$
>Moment bậc 2 của phân phối chuẩn:
>$$
\mathbb{E}[X^2] = \int_{-\infty}^{\infty} \mathcal{N}(x \mid \mu, \sigma^2) x^2 dx = \mu^2 + \sigma^2
>$$
>
>Phương sai của phân phối chuẩn
>$$
\text{var}[X] = \sigma^2
>$$

Đầu tiên, đặt $z = x- \mu \implies x = z + \mu$ vậy $dx = dz$. Thay $z$ vào tích phân của $\mathbb{E}[X]$, ta được:
$$
\begin{align*}
\mathbb{E}[X] &= \int_{-\infty}^{\infty} \frac{1}{(2\pi \sigma^2)^{1/2}} \exp\left( \frac{-1}{2\sigma^2}z^2 \right) (z + \mu) dz \\
&= \frac{1}{(2\pi \sigma^2)^{1/2}} \left[ \int_{-\infty}^{\infty} \exp\left( -\frac{1}{2\sigma^2}z^2 \right) z dz + \mu \int_{-\infty}^{\infty} \exp\left( -\frac{1}{2\sigma^2} z^2 \right) dz \right] \\
\end{align*}
$$

Xét tích phân phía bên trái dấu $+$ nằm trong ngoặc vuông, đặt:
$$
f(z) = \exp\left( -\frac{1}{2\sigma^2} z^2 \right) z
$$
với mọi $z \in \mathbb{R}$, ta có:
$$
\begin{align*}
f(-z) &= \exp\left( -\frac{1}{2\sigma^2}(-z)^2 \right)(-z) \\
&= -\left[\exp\left( -\frac{1}{2\sigma^2}z^2 \right)z\right] \\
&= -f(z)
\end{align*}
$$
do đó phần tích phân mà ta đang xét là tích phân của hàm lẻ ([[Zettel/Integral of odd and even function\|Integral of odd and even function]]). 

>[!error]
>Ở đoạn này mình có nhìn qua solution nên mới biết được đó là hàm lẻ, kiểu how, how 🥲. Thế nên cũng không phải là mình tự làm lắm.

Vì vậy:
$$
\int_{-\infty}^{\infty} \exp\left( \frac{-1}{2\sigma^2} z^2 \right)z dz = 0
$$

>[!note]+
>Nếu các bạn đọc trong [[Zettel/Integral of odd and even function\|Integral of odd and even function]], thì ta đang xét trên đoạn $[-a, a]$, nhưng mở rộng ra $(-\infty, \infty)$ cũng không khó. Ví dụ $f$ là hàm lẻ thì ta có:
>$$
\begin{align*}
\int_{-\infty}^{\infty} f(x) dx &= \lim_{ a \to \infty } \int_{-a}^{a} f(x)dx \\
&= \lim_{ a \to \infty } 0 \\
&= 0
\end{align*}
>$$


Còn phần tích phân phía sau dấu $+$ trong ngoặc vuông đã được ta chứng minh ở bài 1.7 trong [[Zettel/Exercises Part I\|Exercises Part I]] (hoặc có thể dùng tích phân Gauss [[Zettel/Gauss Integral\|Gauss Integral]] rồi đổi biến) và có giá trị là $(2\pi \sigma^2)^{1/2}$. Vậy ta có:
$$
\begin{align*}
\mathbb{E}[X] &= \frac{1}{(2\pi \sigma^2)^{1/2}} [0 + \mu (2\pi \sigma^2)^{1/2}] \\
&= \mu
\end{align*}
$$
>[!note]+
>Ở phương trình tiếp theo ta phải đạo hàm tích phân, mà trước đó ta phải biết đạo hàm thông qua tích phân như nào, các bạn có thể tìm hiểu qua đây [[Zettel/Differentiating under integral\|Differentiating under integral]]. 

Đặt:
$$
f(\sigma^2) = \int_{-\infty}^{\infty} \mathcal{N}(x \mid \mu, \sigma^2) dx
$$
Theo [[Zettel/Differentiating under integral\|Differentiating under integral]], ta có:
$$
\begin{align*}
\frac{\partial f(\sigma^2)}{\partial \sigma^2} &= \int_{-\infty}^{\infty} \frac{\partial\mathcal{N}(x \mid \mu, \sigma^2)}{\partial \sigma^2} dx \\
\end{align*}
$$
Giờ vấn đề là ta phải đạo hàm phân phối chuẩn theo $\sigma^2$, trước tiên, ta đặt:
$$
\begin{align*}
g(\sigma^2) &= \frac{1}{(2\pi \sigma^2)^{1/2}} \\
h(\sigma^2) &= \exp\left( -\frac{1}{2\sigma^2} (x-\mu)^2 \right) \\
\implies \mathcal{N}(x \mid \mu, \sigma^2) &= g(\sigma^2)h(\sigma^2) \\
\end{align*}
$$
Vậy:
$$
\frac{\partial \mathcal{N}(x \mid \mu, \sigma^2)}{\partial \sigma^2} = \frac{\partial g(\sigma^2)}{\partial \sigma^2}h(\sigma^2) + g(\sigma^2) \frac{\partial h(\sigma^2)}{\partial \sigma^2}
$$
Để giải được phương trình trên, ta tìm từng đạo hàm, đầu tiên là $g(\sigma^2)$:
$$
\begin{align*}
\frac{\partial g(\sigma^2)}{\partial \sigma^2} &= \frac{1}{(2\pi)^{1/2}} \frac{\partial 1 / [(\sigma^2)^{1/2}]}{\partial \sigma^2} \\
&= \frac{1}{(2\pi)^{1/2}} \left( -\frac{1}{2} \frac{1}{(\sigma^2)^{3/2}} \right) \\
&= \frac{1}{(2\pi)^{1/2}} \left( -\frac{1}{2} \frac{1}{(\sigma^2)^{1/2}\sigma^2} \right) \\
&= -\frac{1}{2\sigma^2}g(\sigma^2)
\end{align*}
$$
tiếp theo là $h(\sigma^2)$:
$$
\begin{align*}
\frac{\partial h(\sigma^2)}{\partial \sigma^2} &= -\frac{\partial 1/(2\sigma^2)}{\partial \sigma^2}[(x-\mu)^2 h(\sigma^2)]  \\
&= \frac{1}{2} \frac{1}{\sigma^4} (x-\mu)^2 h(\sigma^2) \\\\
&= \frac{1}{2\sigma^2} \frac{(x-\mu)^2}{\sigma^2} h(\sigma^2)
\end{align*}
$$
Kết hợp lại, ta được:
$$
\begin{align*}
\frac{\partial \mathcal{N}(x \mid \mu, \sigma^2)}{\partial \sigma^2} &= -\frac{1}{2\sigma^2}g(\sigma^2)h(\sigma^2) + \frac{1}{2\sigma^2} \frac{(x-\mu)^2}{\sigma^2} g(\sigma^2)h(\sigma^2) \\
&= \frac{1}{2\sigma^2}g(\sigma^2)h(\sigma^2) \left[\frac{(x-\mu)^2}{\sigma^2} - 1 \right] \\
&= \frac{1}{2\sigma^2}\left[ \frac{(x-\mu)^2}{\sigma^2} - 1 \right] \mathcal{N}(x \mid \mu, \sigma^2)
\end{align*}
$$
Thực hiện đạo hàm 2 vế, ta có:
$$
\begin{align*}
&\frac{\partial f(\sigma^2)}{\partial \sigma^2} = \frac{\partial 1}{\partial \sigma^2} \\
&\Leftrightarrow \int_{-\infty}^{\infty} \frac{1}{2\sigma^2}\left[ \frac{(x-\mu)^2}{\sigma^2} - 1 \right] \mathcal{N}(x \mid \mu, \sigma^2) dx = 0 \\
&\Leftrightarrow \frac{1}{\sigma^2}\int_{-\infty}^{\infty} (x-\mu)^2 \mathcal{N}(x \mid \mu, \sigma^2) dx - \int_{-\infty}^{\infty} \mathcal{N}(x \mid \mu, \sigma^2) dx = 0 \\
&\Leftrightarrow \frac{1}{\sigma^2}\int_{-\infty}^{\infty} (x-\mu)^2 \mathcal{N}(x \mid \mu, \sigma^2) dx - 1 = 0 \\
&\Leftrightarrow \int_{-\infty}^{\infty} (x-\mu)^2 \mathcal{N}(x \mid \mu, \sigma^2) dx = \sigma^2 \\
&\Leftrightarrow \mathbb{E}[(X-\mu)^2] = \sigma^2 \\
&\Leftrightarrow \text{var}[X] = \sigma^2
\end{align*}
$$
Vậy ta chứng minh được phương sai của phân phối chuẩn là $\sigma^2$, tiếp theo:
$$
\begin{align*}
\text{var}[X] &= \mathbb{E}[X^2] - \mathbb{E}[X] \\
\implies \mathbb{E}[X^2] &= var[X] + \mathbb{E}[X] \\
&= \sigma^2 + \mu^2
\end{align*}
$$

---
# References

- [Bishop] Pattern Recoginition and Machine Learning (exercises of I.Introduction).