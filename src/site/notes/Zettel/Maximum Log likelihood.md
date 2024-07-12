---
source: "[[Study/Math knowledge\|Math knowledge]]"
id: 202404251638
date_create: 2024-04-25
dg-publish: true
---
Ta có:
$$
\begin{aligned}
\ln \mathcal{L}(\mu, \sigma^2 \mid \mathcal{D}) &= \ln \prod_{i=1}^N p(x_{i} \mid \mu, \sigma^2) \\
&= \sum_{i=1}^N \ln p(x_{i} \mid \mu, \sigma^2) \\
&= \sum_{=1}^N \ln \frac{1}{(2\pi\sigma^2)^{1/2}} \exp \left\{ -\frac{1}{2\sigma^2} (x_{i} - \mu)^2 \right\} \\
&= \sum_{i=1}^N \left[\ln (2\pi\sigma^2)^{-1/2} -\frac{1}{2\sigma^2} (x_{i} - \mu)^2 \right] \\
&= \sum_{i=1}^N \left[- \frac{1}{2}\ln 2\pi -\frac{1}{2}\ln \sigma^2 - \frac{1}{2\sigma^2} (x_{i} - \mu)^2 \right] \\
&= \left[-\frac{1}{2\sigma^2} \sum_{i=1}^N (x_{i} - \mu)^2 \right] - \frac{N}{2} \ln 2\pi - \frac{N}{2}\ln \sigma^2
\end{aligned}
$$
Để tìm giá trị cực đại của một hàm, ta đạo hàm sau đó lấy bằng $0$. Ta biết rằng $\ln$ là một hàm đồng biến trên $\mathbb{R}$ do đó giá trị tại dạo hàm bằng $0$ cũng chính là cực đại. Ta sẽ viết gọn $\ln \mathcal{L}(\mu, \sigma^2 \mid \mathcal{D})$ thành $\mathcal{L}$.

Xét cực đại bằng $\mu$, ta có:
$$
\frac{\partial\mathcal{L}}{\partial\mu} = -\frac{1}{2\sigma^2} \sum_{n=1}^N -2x_{n} + 2\mu 
$$
Khi đó, giá trị cần tìm là:
$$
\begin{aligned}
-\frac{1}{2\sigma^2} \sum_{n=1}^N -2x_{n} + 2\mu &= 0 \\
\implies \sum_{n=1}^N -2x_{n} + 2\mu &= 0 \\
\Leftrightarrow 2\sum_{n=1}^N -x_{n} + 2N\mu &= 0 \\
\Leftrightarrow \mu = \frac{1}{N} \sum_{n=1}^N x_{n}
\end{aligned}
$$

Xét cực đại bằng $\sigma^2$, ta có:
$$
\frac{\partial \mathcal{L}}{\partial \sigma^2} = \frac{1}{2\sigma^4} \sum_{n=1}^N (x_{n} - \mu)^2 - \frac{N}{2} \frac{1}{\sigma^2}
$$
Khi đó, giá trị cần tìm là:
$$
\begin{aligned}
\frac{1}{2\sigma^4} \sum_{n=1}^N (x_{n} - \mu)^2 - \frac{N}{2} \frac{1}{\sigma^2} = 0 \\
\implies \frac{1}{\sigma^2} \sum_{n=1}^N (x_{n} - \mu)^2 - N = 0 \\
\Leftrightarrow \sigma^2 = \frac{1}{N} \sum_{n=1}^N (x_{n} - \mu)^2
\end{aligned}
$$

---
# References