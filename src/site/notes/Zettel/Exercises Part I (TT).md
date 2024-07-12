---
{"dg-publish":true,"permalink":"/zettel/exercises-part-i-tt/"}
---


>[!example]+ Giải bài 1.9
>
>![Pasted image 20240426102814.png](/img/user/Attachment/Pasted%20image%2020240426102814.png)

Đã được giải trong [[Zettel/Mode of normal distribution\|Mode of normal distribution]] (còn mode cho phân phối chuẩn nhiều biến thì mình thua vậy 💀).

>[!example]+ Giải bài 1.10
>
>![Pasted image 20240426112341.png](/img/user/Attachment/Pasted%20image%2020240426112341.png)

Khi hai biến ngẫu nhiên $X$ và $Z$ độc lập với nhau thì $p(x, z) = p_{x}(x)p_{z}(z)$ với $p(x, z)$ là mật độ xác suất đồng thời của $X$ và $Z$, còn $p_{x}$ và $p_{z}$ lần lượt là mật độ xác suất của $X$ và $Z$.

Ta có:
$$
\begin{align*}
\mathbb{E}[X + Z] &= \iint (x + z)p(x, z)dxdz \\
&= \iint (x+z)p_{x}(x)p_{z}(z)dxdz \\
&= \iint xp_{x}(x)p_{z}(z)dxdz + \iint zp_{x}(x)p_{z}(z)dxdz \\
&= \int p_{z}(z)\left[ \int xp_{x}(x)dx \right]dz + \int p_{x}(x)\left[ \int zp_{z}(z)dz \right]dx \\
&= \mathbb{E}[X] \int p_{z}(z)dz + \mathbb{E}[Z] \int p_{x}(x)dx \\
&= \mathbb{E}[X] + \mathbb{E}[Z]
\end{align*}
$$
>[!note]+
>Do $p_{x}$ là một hàm mật độ xác suất nên:
>$$
>\int_{-\infty}^{\infty} p_{x}(x) dx = 1
>$$
>tương tự với $p_{z}$.

Ta có:
$$
\text{var}[X + Z] = \mathbb{E}[(X+Z)^2] - (\mathbb{E}[X+Z])^2 \\
$$
Bây giờ, ta sẽ phân tích $\mathbb{E}[(X +Z)^2]$ thử:
$$
\begin{align*}
&\mathbb{E}[(X+Z)^2] = \iint (x+z)^2 p(x, z)dxdz \\
&= \iint (x^2 + 2xz + z^2) p(x, z)dxdz \\
&= \iint x^2p_{x}(x)p_{z}(z)dxdz + 2\iint xzp_{x}(x)p_{z}(z)dxdz + \iint z^2p_{x}(x)p_{z}(z)dxdz \\
&= \int p_{z}(z) \left[ \int x^2 p_{x}(x)dx \right]dz + \int p_{x}(x) \left[ \int z^2 p_{z}(z)dz \right]dx + 2\int xp_{x}(x)dx \int zp_{z}(z)dz \\
&= \mathbb{E}[X^2] + \mathbb{E}[Z^2] + 2\mathbb{E}[X] \mathbb{E}[Y]
\end{align*}
$$
Thay vào phương trình $\text{var}[X + Z]$, ta có:
$$
\begin{align*}
\text{var}[X + Z] &= E[X^2] + \mathbb{E}[X^2] + 2\mathbb{E}[X] - (\mathbb{E}[X] + \mathbb{E}[Z])^2 \\
&= (\mathbb{E}[X^2] - \mathbb{E}[X]^2) + (\mathbb{E}[Z^2] - \mathbb{E}[Z]^2) \\
&= \text{var}[X] + \text{var}[Z]
\end{align*}
$$

>[!example]+ Giải bài 1.11
>
>![Pasted image 20240429090725.png](/img/user/Attachment/Pasted%20image%2020240429090725.png)

Đã được giải trong [[Zettel/Maximum Log likelihood\|Maximum Log likelihood]].

>[!example]+ Giải bài 1.12
>
>![Pasted image 20240429090755.png](/img/user/Attachment/Pasted%20image%2020240429090755.png)

Ở $\mathbb{E}[x_{n}x_{m}]$ nếu $n = m$ thì ta có $\mathbb{E}[x_{n}x_{m}] = \mathbb{E}[x_{n}^2] = \sigma^2 + \mu^2$. Vậy:
$$
\mathbb{E}[x_{n}x_{m}] = \sigma^2 + \mu^2 \hspace{5pt} \text{(nếu $m = n$)}
$$
Còn nếu $n \neq m$ (ta hãy nhớ hai biến ngẫu nhiên độc lập thì kì vọng tích bằng tích kì vọng) thì:
$$
\begin{align*}
\mathbb{E}[x_{n}x_{m}] &= \mathbb{E}[x_{n}] \mathbb{E}[x_{m}] \\
&= \mu^2 \hspace{5pt} \text{(nếu $m \neq n$)}
\end{align*}
$$
Đặt $I_{nm} = 1$ nếu $m = n$ và $I_{mn} = 0$ nếu $n \neq m$, ta được:
$$
\mathbb{E}[x_{n}x_{m}] = \mu^2 + I_{mn}\sigma^2
$$

>[!example]+ Giải bài 1.13
>
>![Pasted image 20240429091347.png](/img/user/Attachment/Pasted%20image%2020240429091347.png)

Phương trình 1.56:
$$
\sigma^2_{ML} = \frac{1}{N} \sum_{n=1}^N (x_{n} - \mu_{ML}^2) 
$$
Nếu thay trung bình mẫu $\mu_{ML}^2$ thành trung bình thật sự của phân phối là $\mu$, ta có:
$$
\sigma^2_{ML} = \frac{1}{N} \sum_{n=1}^N (x_{n} - \mu^2) 
$$
Lúc này ta có (trung bình thật sự $\mu$ là một hằng số):
$$
\begin{align*}
\mathbb{E}[\sigma^2_{ML}] &= \frac{1}{N} \sum_{n=1}^N \mathbb{E}[x_{n}^2 - 2x_{n}\mu + \mu^2] \\ 
&= \frac{1}{N} \sum_{n=1}^N (\mathbb{E}[x_{n}^2] - 2\mathbb{E}[x_{n}\mu] + \mathbb{E}[\mu^2]) \\
&= \frac{1}{N} \sum_{n=1}^N (\mathbb{E}[x_{n}^2] - 2\mu\mathbb{E}[x_{n}] + \mu^2) \\
&= \frac{1}{N} \sum_{n=1}^N (\sigma^2 + \mu^2 - 2\mu^2 + \mu^2) \\
&= \frac{1}{N} \sum_{n=1}^N \sigma^2 \\
&= \sigma^2
\end{align*}
$$
Vậy khi phương sai mẫu $\sigma^2_{ML}$ được tính bằng trung bình thật sự $\mu$ thì giá trị ước lượng này đúng với phương sai thật sự $\sigma^2$.

---

Phần trước: [[Zettel/Exercises Part I\|Exercises Part I]]
Phần sau:

---
# References

- [Bishop] Pattern Recoginition and Machine Learning (exercises of I.Introduction).