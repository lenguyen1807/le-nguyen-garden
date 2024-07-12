---
source: "[[Study/Math knowledge\|Math knowledge]]"
id: 202404261046
date_create: 2024-04-26
dg-publish: true
---
Như đã chứng minh ở [[Zettel/Maximum when variable changed\|Maximum when variable changed]], khi mà ta đổi biến ngẫu nhiên $X$ có phân phối xác suất $f_{X}$ sang biến ngẫu nhiên $Y$ với $X = g(Y)$ và $g$ là hàm tuyến tính thì ta có thể tìm giá trị lớn nhất của $f_{X}$ thông qua $f_{Y}$. Ngoài ra ta có thể tìm $f_{Y}$ thông qua công thức sau ([[Zettel/Change of random variable\|Change of random variable]]):
$$
f_{Y}(y) = f_{X}(g(y)) |g'(y)|
$$
Đặt $g(Y) = \sigma Y + \mu$ và $X \sim \mathcal{N}(\mu, \sigma^2)$, nên ta có:
$$
\begin{align*}
f_{X}(g(y)) &= \frac{1}{(2\pi\sigma^2)^{1/2}} \exp\left( -\frac{1}{2\sigma^2}[(\sigma y + \mu) - \mu]^2 \right) \\
&= \frac{1}{(2\pi \sigma^2)^{1/2}} \exp\left( -\frac{1}{2}y^2 \right) \\
\text{và} \hspace{5pt} g'(y) &= \sigma
\end{align*}
$$
do đó:
$$
\begin{align*}
f_{Y}(y) &= \frac{1}{(2\pi \sigma^2)^{1/2}} \exp\left( -\frac{1}{2}y \right) |\sigma| \\
&= \frac{1}{(2\pi \sigma^2)^{1/2}} \exp\left( -\frac{1}{2}y^2 \right) \sigma \\
&= \frac{1}{(2\pi)^{1/2}} \exp\left( -\frac{1}{2}y^2 \right)
\end{align*}
$$
Lấy đạo hàm bằng $0$, ta có:
$$
\begin{align*}
f_{Y}'(y) &=\frac{1}{(2\pi)^{1/2}} (-y) \exp\left( -\frac{1}{2}y^2 \right) \\
\implies f'_{Y}(y) &= 0  \\
\Leftrightarrow y &= 0 \\
\implies x &= \mu
\end{align*}
$$
Để xác minh giá trị đạo hàm bằng $0$ là cực đại, ta có:
$$
\begin{align*}
f''_{Y}(y) &= \frac{1}{(2\pi)^{1/2}} \left[ -\exp\left( -\frac{1}{2}y^2 \right) + y^2 \exp\left( -\frac{1}{2}y^2 \right)  \right] \\
&= \frac{1}{(2\pi)^{1/2}} \exp\left( -\frac{1}{2}y^2 \right) (y^2 - 1)
\end{align*}
$$
tại $y = 0$, $f''_{Y}(y) < 0$ do đó $y = 0$ là điểm làm cho $f_{Y}(y)$ cực đại.

Vậy giá trị  $x$ làm cho phân phối $f_{X}$ lớn nhất là $x = \mu$. Do đó $\mu$ chính là **mode** của phân phối chuẩn.

---
# References

- [probability - Gaussian distribution proof - Mathematics Stack Exchange](https://math.stackexchange.com/questions/1620579/gaussian-distribution-proof)