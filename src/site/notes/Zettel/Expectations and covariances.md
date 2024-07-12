---
{"dg-publish":true,"permalink":"/zettel/expectations-and-covariances/"}
---


Kì vọng (expectation) là một trong nhất concept quan trọng nhất của xác suất. Giá trị trung bình của một hàm biến ngẫu nhiên $f(X)$ nào đó với $X$ có phân phối xác suất $p(x)$ được gọi là **kì vọng** của $f(X)$ và được kí hiệu là $\mathbb{E}[f]$ (ngoài ra ta cũng có thể viết $\mathbb{E}[f(X)]$).
- Nếu $x$ là một biến ngẫu nhiên rời rạc thì:
$$
\mathbb{E}[f] = \sum_{X} p(x)f(x)
$$
- Ta có thể thấy kì vọng của $f(X)$ với $X$ là biến ngẫu nhiên rời rạc sẽ là trung bình có trọng số của các giá trị $f(x)$, trong đó trọng số chính là xác suất của các giá trị $x$ khác nhau ($p(x)$).

>[!note]+
>Trung bình có trọng số của $(x_1, \dots, x_n)$ với trọng số $(w_1, \dots, w_n)$ sẽ là:
>$$
\dfrac{w_{1}x_{1} + \dots + w_{n}x_{n}}{w_{1} + \dots + w_{n}}
>$$
>Ở kì vọng của biến ngẫu nhiên rời rạc $X$, ta có trọng số là các xác suất $p(x)$ mà $\sum_{X}p(x) = 1$ do đó mẫu bị triệt tiêu.

- Nếu $X$ là một biến ngẫu nhiên liên tục (khi này $p(x)$ là mật độ xác suất của $x$), ta có:
$$
\mathbb{E}[f] = \int f(x)p(x)dx
$$
- Khi đó kì vọng của $f(X)$ với $X$ là biến ngẫu nhiên liên tục chính là tích phân của $f(x)p(x)$ trên toàn bộ giá trị của $x$ (hay là từ $-\infty$ đến $\infty$).

>[!note]+
>Vậy nếu $f(X) = X$ thì ta có:
>- Rời rạc:
>$$
>\mathbb{E}[X] = \sum_{X} p(x)x
>$$
>- Liên tục:
>$$
\mathbb{E}[X] = \int p(x)xdx
>$$
>
>Đây là công thức mà ta thường gặp hơn.

Ngoài ra, nếu lấy $N$ điểm ngẫu nhiên $(x_1, \dots, x_n)$ từ phân phối xác suất (nếu $x$ là rời rạc) hoặc mật độ xác suất (nếu $x$ là liên tục) thì ta có thể xấp xỉ giá trị kì vọng bằng cách sau:
$$
\mathbb{E}[f] \simeq \frac{1}{N} \sum_{n=1}^N f(x_{n})
$$
>[!info]+ Tại sao lại có thể xấp xỉ
>Việc xấp xỉ này dựa vào một phương pháp gọi là **Monte Carlo Integration**. Thật ra mình chưa đủ sức để hiểu rõ cái này, các bạn có thể tìm hiểu thêm ở [SP].

Đôi lúc, ta cũng quan tâm đến kì vọng của một hàm nhiều biến, ví dụ ta có hàm $f(X, Y)$ (2 biến) để kí hiệu kì vọng của 1 biến mà ta quan tâm, ví dụ biến ngẫu nhiên $X$, ta sẽ dùng $\mathbb{E}_{x}[f(X, Y)]$ (nghĩa là lấy trung bình trên biến $x$).
- Nếu $X, Y$ là các biến rời rạc thì:
$$
\mathbb{E}_{x}[f(X, Y)] = \sum_{x} f(x, y)p(x, y)
$$
- Nếu $X, Y$ là các biến liên tục thì:
$$
\mathbb{E}_{x}[f(X, Y)] = \int f(x, y)p(x, y)dx
$$
- Ta có thể thấy ở cả 2 trường hợp trên, $\mathbb{E}_{x}[f(X, Y)]$ là một hàm của $Y$, vậy khi lấy trung bình của biến nào, kì vọng sẽ phụ thuộc sẽ là hàm của biến còn lại. Tương tự với $\mathbb{E}_{y}[f(X, Y)]$.

Vậy nếu ta không phân biệt kì vọng của $X$ hay $Y$ thì khi đó:
- Đối với rời rạc:
$$
\mathbb{E}[f(X, Y)] = \mathbb{E}_{x, y}[f(X, Y)] = \sum_{Y} \sum_{X} f(x,y)p(x,y)
$$
- Đối với liên tục:
$$
\mathbb{E}[f(X, Y)] = \mathbb{E}_{x, y}[f(X, Y)] = \int \int f(x, y)p(x, y)dx dy
$$
Lưu ý rằng, lúc này kì vọng $\mathbb{E}[f(X, Y)]$ là một số thực, trong khi đó $\mathbb{E}_{x}[f(X, Y)]$ hay $\mathbb{E}_{y}[f(X, Y)]$ là một hàm phụ thuộc vào biến còn lại.

Ngoài ra, ta cũng quan tâm đến **kì vọng có điều kiện** (conditional expectation) của một hàm $f(X)$ trong đó $x$ có phân phối điều kiện là $p(x \mid y)$.
- Nếu $X$ là biến rời rạc:
$$
\mathbb{E}_{x}[f(X) \mid Y] = \sum_{X} p(x \mid y)f(x)
$$
- Tương tự với $X$ là biến liên tục:
$$
\mathbb{E}_{x}[f(X) \mid Y] = \int p(x \mid y) f(x) dx
$$
- Ta có thể thấy, ở hai trường hợp trên kì vọng có điều kiện $\mathbb{E}[f(X) \mid Y]$ là một hàm phụ thuộc vào $Y$.

**Phương sai** (variance) của hàm $f(X)$ với $X$ là biến ngẫu nhiên được kí hiệu là $\text{var}[f]$ và được định nghĩa như sau:
$$
\text{var}[f] = \mathbb{E}[(f(X) - \mathbb{E}[f(X)])^2]
$$
Có thể thấy, $\text{var}[f]$ là đại lượng cho thấy độ biến thiên (sự khác nhau) giữa giá trị $f(x)$ và trung bình $\mathbb{E}[f(X)]$ của nó (sự khác nhau $= (f(X) - \mathbb{E}[f(X)])^2$). Ngoài ra ta có thể viết:
$$
\text{var}[f] = \mathbb{E}[f(X)^2] - \mathbb{E}[f(X)]^2
$$

>[!note]+
>Dựa vào các tính chất sau của kì vọng:
>$$
\begin{aligned}
\mathbb{E}[f + g] &= \mathbb{E}[f] + \mathbb{E}[g] \\
\mathbb{E}[\alpha f] &= \alpha \mathbb{E}[f] \hspace{5pt} \text{với $\alpha \in \mathbb{R}$} \\
\mathbb{E}[c] &= c \hspace{5pt} \text{với $c \in \mathbb{R}$.}
\end{aligned}
>$$
>Khi đó:
>$$
\begin{aligned}
\text{var}[f] &= \mathbb{E}[(f(X) - \mathbb{E}[f(X)])^2] \\
&= \mathbb{E}[f(X)^2 - 2f(X)\mathbb{E}[f(X)] + \mathbb{E}[f(X)]^2] \\
&= \mathbb{E}[f(X)^2] -2\mathbb{E}[f(X)\mathbb{E}[f(X)]] + \mathbb{E}[\mathbb{E}[f(X)]^2] \\
&= \mathbb{E}[f(X)^2] - 2\mathbb{E}[f(X)]\mathbb{E}[f(X)] + \mathbb{E}[f(X)]^2 \\
&= \mathbb{E}[f(X)^2] - \mathbb{E}[f(X)]^2
\end{aligned}
>$$
>
>Một điểm đáng chú ý như ta đã nói ở trên, tại sao sự khác nhau giữa $f(X)$ và trung bình của nó lại lấy bình phương mà sao không lấy cách khác (ví dụ dùng giá trị tuyệt đối), có thể tìm hiểu thêm tại [definition - Why square the difference instead of taking the absolute value in standard deviation? - Cross Validated (stackexchange.com)](https://stats.stackexchange.com/questions/118/why-square-the-difference-instead-of-taking-the-absolute-value-in-standard-devia).

Xét hai biến ngẫu nhiên $X$ và $Y$, ta định nghĩa **hiệp phương sai** (covariance) của $X$ và $Y$ là:
$$
\begin{aligned}
\text{cov}[X, Y] &= \mathbb{E}_{x, y} [\{X - \mathbb{E}[X])(Y - \mathbb{E}[Y]\}] \\
&= \mathbb{E}_{x, y}[XY] - \mathbb{E}[X]\mathbb{E}[Y]
\end{aligned}
$$
>[!note]+
>Ta có:
>$$
\begin{aligned}
\text{cov}[X, Y] &= \mathbb{E}_{x, y} [\{X - \mathbb{E}[X])(Y - \mathbb{E}[Y]\}] \\
&= \mathbb{E}_{x, y}[XY - X\mathbb{E}[Y] - \mathbb{E}[X]Y + \mathbb{E}[X]\mathbb{E}[Y]] \\
&= \mathbb{E}_{x, y}[XY] - \mathbb{E}[Y]\mathbb{E}_{x,y}[X] - \mathbb{E}[X]\mathbb{E}_{x, y}[Y] + \mathbb{E}[X]\mathbb{E}[Y] \\
&= \mathbb{E}_{x, y}[XY] - \mathbb{E}[Y]\mathbb{E}[X] - \mathbb{E}[X]\mathbb{E}[Y] + \mathbb{E}[X]\mathbb{E}[Y] \\
&= \mathbb{E}_{x, y}[XY] - \mathbb{E}[X]\mathbb{E}[Y]
\end{aligned}
>$$

Nếu hai biến ngẫu nhiên $X$ và $Y$ độc lập với nhau thì hiệp phương sai của $X$ và $Y$ là $0$.

>[!note]+
>Giả sử $X$ và $Y$ là hai biến ngẫu nhiên liên tục độc lập với nhau (rời rạc ta làm tương tự), tức là $p(x, y) = p(x)p(y)$. Khi đó:
>$$
\begin{aligned}
\mathbb{E}_{x, y}[XY] &= \int \int p(x, y) \hspace{3pt} xy \hspace{3pt}  dx dy \\
&= \int \int p(x)p(y) \hspace{3pt} xy \hspace{3pt} dx dy \\
&= \int p(y)y \left[ \int p(x)xdx \right] dy \\
&= \int p(y)y \left[ \mathbb{E}[X] \right]dy \\
&= \mathbb{E}[X] \int p(y)y dy\\
&= \mathbb{E}[X] \mathbb{E}[Y]
\end{aligned}
>$$
>Do đó $\text{cov}[X, Y] = 0$.

Nếu ta xét hiệp phương sai giữa hai vector ngẫu nhiên $\mathbf{x} = (X_1, X_{2} \dots)$ và $\mathbf{y} = (Y_{1}, Y_{2}, \dots)$. Ta có:
$$
\begin{aligned}
\text{cov}[\mathbf{x}, \mathbf{y}] &= \mathbb{E}[(\mathbf{x} - \mathbb{E}[\mathbf{x}])(\mathbf{y} - \mathbb{E}[\mathbf{y}])] \\
&= \mathbb{E}_{\mathbf{x}, \mathbf{y}}[\mathbf{x}\mathbf{y}^T] + \mathbb{E}[\mathbf{x}]\mathbb{E}[\mathbf{y}^T]
\end{aligned}
$$
Nếu ta xét hiệp phương sai giữa biến ngẫu nhiên $X$ với chính nó, ta có thể viết $\text{cov}[X]$ thay cho $\text{cov}[X, X]$. Tương tự với vector ngẫu nhiên $\mathbf{x}$, $\text{cov}[\mathbf{x}, \mathbf{x}] \equiv \text{cov}[\mathbf{x}]$.

---

Phần trước: [[Zettel/Probability Densities\|Probability Densities]]
Phần sau: [[Zettel/Bayesian Probabilities\|Bayesian Probabilities]]

---
# References

- [Bishop] Pattern Recognition and Machine Learning - Bishop (chapter 1.2)
- [SP]  [Monte Carlo Methods in Practice (scratchapixel.com)](https://www.scratchapixel.com/lessons/mathematics-physics-for-computer-graphics/monte-carlo-methods-in-practice/monte-carlo-integration.html)