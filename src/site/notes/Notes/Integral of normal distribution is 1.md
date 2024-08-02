---
{"dg-publish":true,"permalink":"/notes/integral-of-normal-distribution-is-1/","noteIcon":"📝","created":"2024-08-02T10:46:38.344+07:00","updated":"2024-08-02T10:48:14.808+07:00"}
---


Để chứng minh phân phối chuẩn $\mathcal{N}(x \mid \mu, \sigma^2)$ là một hàm mật độ xác suất thì ta cần chứng minh hai tính chất:
$$
\begin{aligned}
\mathcal{N}(x \mid \mu, \sigma^2) &\geq 0 \\
\int_{-\infty}^{\infty} \mathcal{N}(x \mid \mu, \sigma^2) dx &= 1
\end{aligned}
$$
Tính chất đầu tiên thì ta dễ thấy rồi, để chứng minh được tính chất thứ 2, ta phải tìm hiểu thêm một dạng nữa của phân phối chuẩn, được gọi là **phân phối chuẩn tắc** (standard normal distribution), kí hiệu $\varphi(z)$. Phân phối chuẩn tắc được định nghĩa như sau:
$$
\varphi(z) = \frac{1}{(2\pi)^{1/2}} \exp \left\{ -\frac{1}{2}z^2 \right\}
$$
Ngoài ra, phân phối chuẩn tắc có trung bình là $0$ và phương sai là $1$. Nếu đặt $z = (x - \mu) / \sigma$ thì ta có thể đưa phân phối chuẩn tắc về phân phối chuẩn như sau:
$$
\mathcal{N}(x \mid \mu, \sigma^2) = \frac{1}{(\sigma^2)^{1/2}} \varphi\left( \frac{x-\mu}{\sigma} \right)
$$
Giờ xét tích phân của phân phối chuẩn, ta có:
$$
\begin{aligned}
&\int_{-\infty}^{\infty} \frac{1}{(2\pi \sigma^2)^{1/2}} \exp \left\{ - \frac{1}{2\sigma^2} (x - \mu)^2 \right\} dx \\
= \frac{1}{(2\pi \sigma^2)^{1/2}} &\int_{-\infty}^{\infty} \exp \left\{ - \frac{1}{2\sigma^2} (x - \mu)^2 \right\} dx \\
\end{aligned}
$$

Đặt $z = (x - \mu) / \sigma$ (mục đích đưa tích phân trên về tích phân của phân phối chuẩn tắc), ta có $x = z \sigma + \mu \implies dx = \sigma dz$. Đổi biến tích phân trên từ $x$ sang $z$ ta được:
$$
\begin{aligned}
&\frac{1}{(2\pi \sigma^2)^{1/2}} \int_{-\infty}^{\infty} \exp \left\{ - \frac{1}{2} z^2 \right\} \sigma dz \\
= &\frac{1}{(2\pi)^{1/2}} \int_{-\infty}^{\infty} \exp \left\{ - \frac{1}{2} z^2 \right\} dz \\
\end{aligned}
$$

Lưu ý, tích phân sau:
$$
\int_{-\infty}^{\infty} \exp\{-y^2\}dy = \sqrt{ \pi }
$$

còn được gọi là **tích phân Gauss** ([[Gauss Integral\|Gauss Integral]]). Nếu tiếp tục đặt $y^2 = z^2 / 2 \implies \sqrt{ 2 } y = z$ thì ta có $\sqrt{ 2 }dy = dz$, ta được:
$$
\begin{aligned}
&\frac{1}{(2\pi)^{1/2}} \int_{-\infty}^{\infty} \exp \left\{ - y^2 \right\} \sqrt{ 2 } dy \\
&= \frac{1}{(2\pi)^{1/2}} \sqrt{ 2 } \sqrt{ \pi } \\
&= 1
\end{aligned}
$$

---
# References

- [Proof: Integral of PDF of Normal Distribution is Equal to 1 (in English) (youtube.com)](https://www.youtube.com/watch?v=8Ey7v8IoZjA)