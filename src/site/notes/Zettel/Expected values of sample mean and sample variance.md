---
{"dg-publish":true,"permalink":"/zettel/expected-values-of-sample-mean-and-sample-variance/"}
---


Xét 1 mẫu $\mathcal{D}$ gồm $N$ quan sát ${} x_{1}, \dots, x_{N} {}$ và $\mathcal{D} \overset{i.i.d}{\sim} \mathcal{N}(\mu, \sigma^2)$. Đặt $\mu_{ML}$ là trung bình mẫu và $\sigma^2_{ML}$ là phương sai mẫu.

>[!note]+
>Ta biết $\mathbb{E}[X] = \mu$, $\mathbb{E}[X^{2}] = \mu^{2}+ \sigma^2$ và $\text{var}[X] = \sigma^2$ với $X$ có phân phối chuẩn $\mathcal{N}(\mu, \sigma^2)$. Chứng minh ở [[Zettel/Expected value and variance of normal distribution\|Expected value and variance of normal distribution]].
### Trung bình mẫu

Ta có:
$$
\begin{aligned}
\mathbb{E}[\mu_{ML}] &= \mathbb{E}\left[ \frac{1}{N} \sum_{n=1}^N x_{n} \right] \\
&= \frac{1}{N} \sum_{n=1}^N \mathbb{E}[x_{n}] \\
&= \frac{1}{N} \sum_{n=1}^N \mu \\
&= \mu
\end{aligned}
$$
### Phương sai mẫu

Ta có:
$$
\begin{aligned}
\mathbb{E}[\sigma^2_{ML}] &= \mathbb{E}\left[ \frac{1}{N} \sum_{n=1}^N (x_{n} - \mu_{{ML}})^2 \right] \\
&= \frac{1}{N} \sum_{n=1}^N \mathbb{E}[(x_{n} - \mu_{ML})^2] \\
&= \frac{1}{N} \sum_{n=1}^N \mathbb{E}[x_{n}^2 -2x_{n}\mu_{ML} + \mu_{ML}^2] \\
&= \frac{1}{N} \sum_{n=1}^N \mathbb{E}[x_{n}^2] -2\mathbb{E}[x_{n}\mu_{ML}] + \mathbb{E}[\mu_{ML}^2] \\
\end{aligned}
$$
Như ta đã biết ở phần trên, moment bậc 2 của $x_n$ hay $\mathbb{E}[x_n^2]$ sẽ là:
$$
\mathbb{E}[x_{n}^2] = \sigma^2 + \mu^2
$$
Còn giá trị $\mathbb{E}[x_n\mu_{ML}]$ sẽ được tính như sau (nhớ là các quan sát độc lập với nhau, do đó với hai quan sát $x_i$ và $x_j$ bất kì, ta có $\mathbb{E}[x_ix_j] = \mathbb{E}[x_i]\mathbb{E}[x_j]$):
$$
\begin{aligned}
\mathbb{E}[x_{n}\mu_{ML}] &= \mathbb{E}\left[ x_{n} \frac{1}{N} \sum_{i=1}^N x_{i} \right] \\
&= \frac{1}{N} \left[ \sum_{j \neq n} \mathbb{E}[x_{n}x_{j}] + \mathbb{E}[x_{n}^2] \right] \\
&= \frac{1}{N} \left[ (N-1)\mu^2 + \mu^2 + \sigma^2 \right] \\
&= \mu^2 + \frac{\sigma^2}{N}
\end{aligned}
$$
Ta chỉ cần tính giá trị còn lại là $\mathbb{E}[\mu_{ML}^2]$. Trước tiên ta cần biết công thức sau:
$$
\left( \sum_{n=1}^N x_{n} \right)^2 = \sum_{n=1}^N a_{n}^2 + 2\sum_{j=1}^N\sum_{i=1}^j a_{i}a_{j}
$$
Chứng minh này công thức này mình thua (các bạn có thể xem thêm ở [algebra precalculus - What is the square of summation? - Mathematics Stack Exchange](https://math.stackexchange.com/questions/329344/what-is-the-square-of-summation)). Sau khi có công thức rồi thì tính thôi nào:
$$
\begin{aligned}
\mathbb{E}[\mu_{ML}^2] &= \mathbb{E}\left[ \frac{1}{N^2} \left( \sum_{n=1}^N x_{n} \right)^2 \right] \\
&= \frac{1}{N^2} \mathbb{E}\left[ \sum_{n=1}^N x_{n}^2 + \sum_{j=1}^N\sum_{i=1}^{j-1} x_{i}x_{j} \right] \\
&= \frac{1}{N^2} \left[ \sum_{n=1}^N \mathbb{E}[x_{n}^2] + \sum_{j=1}^N\sum_{i=1}^{j-1} \mathbb{E}[x_{i}x_{j}] \right] \\
&= \frac{1}{N^2} \left( N(\mu^2 + \sigma^2) + 2\sum_{j=1}^N\sum_{i=1}^{j-1} \mu^2 \right)
\end{aligned}
$$
Ở đoạn cuối, ta thấy như sau:
$$
\begin{aligned}
\sum_{j=1}^N\sum_{i=1}^{j-1} \mu^2 &= \mu^2 + 2\mu^2 + \dots + (N-1)\mu^2 \\
&= \frac{N(N-1)}{2} \mu^2 \\
\end{aligned}
$$
Thay ngược vào phương trình của $\mathbb{E}[\mu_{ML}^2]$ ta được:
$$
\begin{aligned}
\mathbb{E}[\mu_{ML}^2] &= \frac{1}{N^2} \left( N(\mu^2 + \sigma^2) + N(N-1)\mu^2 \right) \\
&= \mu^2 + \frac{\sigma^2}{N} = \mathbb{E}[x_{n}\mu_{ML}]
\end{aligned}
$$
Sau khi đã có cả 3, ta chứng minh được, mình đi ngủ đây, dài vãi 💀.
$$
\begin{aligned}
\mathbb{E}[\sigma^2_{ML}] &= \frac{1}{N} \sum_{n=1}^N \mathbb{E}[x_{n}^2] -\mathbb{E}[x_{n}\mu_{ML}] \\
&= \frac{1}{N} \sum_{n=1}^N \left( \sigma^2 + \mu^2 - \mu^2 - \frac{\sigma^2}{N} \right) \\
&= \frac{1}{N} \sum_{n=1}^N \left( \frac{N-1}{N} \sigma^2 \right) \\
&= \frac{(N-1)}{N} \sigma^2
\end{aligned}
$$

>[!note] My honest reaction:
><center><img width=300 height=300 src="https://preview.redd.it/man-im-dead-v0-ymr5u3c0bjsa1.jpg?auto=webp&s=364c87d710ec0cda25a8e23fcbf1dbd692d0a597"> </center>

Có thể thấy, nếu ta chọn chia $N-1$ thay vì $N$ ở phương sai mẫu thì ta có:
$$
\begin{aligned}
\mathbb{E}[\sigma^2_{ML}] &= \mathbb{E}\left[ \frac{1}{N-1} \sum_{n=1}^N (x_{n} - \mu_{ML})^2 \right] \\
&= \frac{1}{N-1} \mathbb{E}\left[ \sum_{n=1}^N (x_{n} - \mu_{ML})^2 \right] \\
&= \frac{1}{N-1} \sum_{n=1}^N \left( \frac{N-1}{N} \sigma^2 \right) \\
&= \sigma^2
\end{aligned}
$$
Vậy đây chính là lý do mà người ta thường chia cho $N-1$ thay vì $N$ ở phương sai mẫu.

---
# References

- [probability - Expectation of sample variance - Mathematics Stack Exchange](https://math.stackexchange.com/questions/4017763/expectation-of-sample-variance)