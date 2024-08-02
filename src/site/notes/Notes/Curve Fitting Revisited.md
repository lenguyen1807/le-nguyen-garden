---
{"dg-publish":true,"permalink":"/notes/curve-fitting-revisited/","noteIcon":"📝","created":"2024-08-02T10:46:38.338+07:00","updated":"2024-08-02T10:47:44.750+07:00"}
---


Ở phần [[Notes/Polynomial Curve Fitting\|Polynomial Curve Fitting]], ta đã biết cách để xấp xỉ một hàm đa thức $f(x, \mathbf{w}) = \sum_{n=0}^M x^n w_{n}$ bằng cách tối thiểu hàm mất mát
$$
E(\mathbf{w}) = \frac{1}{2} \sum_{n=1}^N [f(x_{n}, \mathbf{w}) - y_{n}]^2
$$
Ở phần này, ta cũng sẽ làm như vậy nhưng với góc nhìn xác suất Bayes. Vẫn dùng lại ví dụ cũ, giả sử LN thu thập được một bộ dữ liệu $\mathbf{x} = \{x_{1}, x_{2}, \dots, x_{N}\}^T$ sau $N$ lần mua, với mỗi số tiền $x_{i}$, LN mua được số bánh xèo $y_{i}$, vậy $\mathbf{y} = \{ y_{1}, y_{2}, \dots, y_{N}\}^T$ và LN giả sử dữ liệu tuân theo hàm đa thức:
$$
f(x, \mathbf{w}) = \sum_{n=0}^M x^{n} w_{n}
$$
Nhưng sẽ khác với ví dụ ban đầu ở chỗ này, ta giả sử với mỗi số bánh xèo $x$, số tiền $y$ tuân theo một phân phối chuẩn với trung bình là giá trị của đa thức $f(x, \mathbf{w})$ và phương sai là $\beta^{-1}$ (như ở phần [[Notes/Gaussian Distribution\|Gaussian Distribution]], $\beta$ là độ chính xác của phân phối và $\beta = 1 / \sigma^2$). Vậy ta có phân phối của $y$ với tham số là $x, \mathbf{w}, \beta$ là:
$$
p(y \mid x, \mathbf{w}, \beta) = \mathcal{N}(y \mid \mu = f(x, \mathbf{w}), \sigma^2 = \beta^{-1})
$$
>[!note]+
>Mình không biết tại sao tác giả lại chọn trung bình và phương sai có giá trị như này 🥲. Trung bình thì mình chịu, nhưng việc chọn độ chính xác ${} \beta^{-1} {}$ thay cho phương sai $\sigma^2$ sẽ có lợi ích như này.
>$$
\begin{align}
>\mathcal{N}(y \mid \mu, \beta^{-1}) &= \frac{1}{\sqrt{ 2\pi \beta^{-1} }} \exp\left( \frac{1}{2\beta^{-1}} (y - \mu)^2 \right) \\
&= \frac{\sqrt{ \beta }}{\sqrt{ 2\pi }} \exp\left( \frac{\beta}{2}(y -\mu)^2 \right)
\end{align}
>$$
>Có thể thấy các tham số đều của phân phối chuẩn đều nằm ở trên tử, điều này sẽ giúp cho việc tính toán dễ dàng hơn.

Giờ LN sẽ sử dụng bộ dữ liệu đã có $\{\mathbf{x}, \mathbf{y}\}$ để tìm giá trị $\mathbf{w}$ và $\beta$ sao cho $p(y \mid \mathbf{w}, \beta)$ là lớn nhất bằng cách dùng maximum log likehood. Giả sử rằng bộ dữ liệu của LN được lấy ra một cách độc lập từ phân phối chuẩn $\mathcal{N}(y \mid f(x, \mathbf{w}), \beta^{-1})$, ta có:
$$
\begin{align}
\ln p(\mathbf{y} \mid \mathbf{x}, \mathbf{w}, \beta) &= \ln \prod_{n=1}^N p(y_{n} \mid x_{n}, \mathbf{w}, \beta) \\ 
&= \sum_{n=1}^N \ln p(y_{n} \mid x_{n}, \mathbf{w}, \beta) \\
&= \sum_{n=1}^N \ln \mathcal{N}(y_{n} \mid f(x_{n}, \mathbf{w}), \beta^{-1})
\end{align}
$$
Ở [[Notes/Maximum Log likelihood\|Maximum Log likelihood]], ta đã đưa ra công thức tổng quát cho $\sum_{x} \ln \mathcal{N}(x \mid \mu, \sigma^2)$, giờ chỉ cần thay $x = y_{n}, \mu = f(x_{n}, \mathbf{w})$ và $\sigma^2 = \beta^{-1}$, ta được:
$$
\begin{align}
\sum_{n=1}^N \ln \mathcal{N}(y_{n} \mid f(x_{n}, \mathbf{w}), \beta^{-1}) &= \left[ -\frac{1}{2\beta^{-1}} \sum_{n=1}^N (y_{n} - f(x_{n}, \mathbf{w}))^2 \right] - \frac{N}{2}\ln 2\pi - \frac{N}{2} \ln \beta^{-1} \\
&= \left[ -\frac{\beta}{2} \sum_{n=1}^N (y_{n} - f(x_{n}, \mathbf{w}))^2 \right] - \frac{N}{2} \ln 2\pi +\frac{N}{2} \ln \beta
\end{align}
$$
Đầu tiên đối với tham số $\mathbf{w}$, ta thấy $-\frac{N}{2} \ln 2\pi$ và $\frac{N}{2} \ln \beta$ là các giá trị không liên quan đến $\mathbf{w}$, khi đạo hàm bằng $0$ do đó ta có thể bỏ đi hai giá trị đó, ngoài ra giá trị $-\frac{\beta}{2}$ là một hằng số, khi đạo hàm và lấy bằng $0$ ta không cần xét đến hằng số đó, ta có thể loại bỏ luôn đi $\beta$ và chỉ giữ lại $-\frac{1}{2}$ (mục đích để cho giống bài toán least square). Vậy mục đích của ta là tìm $\mathbf{w}$ sao cho hàm dưới đây là lớn nhất:
$$
-\frac{1}{2} \sum_{n=1}^N (y_{n} - f(x_{n}, \mathbf{w}))^2
$$
Để cực đại hàm log thì ta có thể cực tiểu hàm log âm, vậy ta tìm $\mathbf{w}$ sao cho hàm dưới đây là nhỏ nhất:
$$
\frac{1}{2} \sum_{n=1}^N (y_{n} - f(x_{n}, \mathbf{w}))^2
$$
Có thể thấy, bài toán tìm $\mathbf{w}$ sao cho log likehoood cực đại đã đưa về thành bài toán bình phương nhỏ nhất (least square) như ở bài [[Notes/Polynomial Curve Fitting\|Polynomial Curve Fitting]]. Đặt giá trị tối ưu $\mathbf{w}$ mà ta tìm được là $\mathbf{w}_{ML}$.

Còn đối với tham số $\beta$, nếu lấy đạo hàm của log likelihood, ta được:
$$
-\frac{1}{2} \sum_{n=1}^N (y_{n} - f(x_{n}, \mathbf{w}))^2 + \frac{N}{2} \frac{1}{\beta}
$$
Vậy để phương trình trên bằng $0$, ta có giá trị tối ưu $\beta_{ML}$ là:
$$
\frac{1}{\beta_{ML}} = \frac{1}{N} \sum_{n=1}^N (y_{n} - f(x_{n}, \mathbf{w}_{ML}))^2
$$
Do đã có hai tham số $\mathbf{w}$ và $\beta$ cần thiết là $\mathbf{w}_{ML}$ và $\beta_{ML}$ thông qua maximum likelihood, ta có được phân phối:
$$
p(y \mid x, \mathbf{w}_{ML}, \beta_{ML}) = \mathcal{N}(y \mid f(x, \mathbf{w}_{ML}), \beta^{-1}_{ML})
$$
ta gọi phân phối trên là **phân phối dự đoán** (predictive distribution). Khác với phần [[Notes/Polynomial Curve Fitting\|Polynomial Curve Fitting]], ta không tìm một giá trị $y$ cụ thể với $x$, mà ta tìm được cả một phân phối của $y$, khi thay một giá trị $x_{0}$ bất kì vào, ta tìm được phân phối $p(y \mid x_{0}, \mathbf{w}_{ML}, \beta_{ML})$. 

Vậy làm sao để tìm giá trị $y_{0}$ nếu thay thế giá trị $x_{0}$ cho cả một phân phối thay vì một giá trị, thông thường người ta sẽ lấy trung bình của phân phối $p(y \mid x_{0}, \mathbf{w}_{ML}, \beta_{ML})$, tức là $y_{0} = f(x_{0}, \mathbf{w}_{ML})$ (à thì ra đấy là lý do tại sao chọn trung bình là ${} f(x, \mathbf{w})$ 💀). Vậy cũng quay ngược lại giống với phần [[Notes/Polynomial Curve Fitting\|Polynomial Curve Fitting]], thế nhưng việc có thêm phân phối dự đoán, ta có được nhiều thứ để làm hơn:
- Làm sao để đánh giá được độ tốt của dự đoán (thông qua phân phối dự đoán).
- Giả sử có nhiều mô hình, làm sao để chọn mô hình tốt (thông qua phân phối dự đoán).
- Và nhiều hơn thế nữa (mình copy từ [Comp.ai] 🥲).

Thế nhưng hướng tiếp cận của ta vẫn nằm ở frequentist khi còn dùng maximum likelihood, giờ theo bayesian, ta giả sử rằng tham số $\mathbf{w}$ là một biến ngẫu nhiên và có phân phối là:
$$
p(\mathbf{w} \mid \alpha) = \mathcal{N}(\mathbf{w} \mid \mathbf{0}, \alpha^{-1}\mathbf{I}) = \left( \frac{\alpha}{2\pi} \right)^{(M+1) / 2} \exp\left\{-\frac{\alpha}{2} \mathbf{w}^T \mathbf{w} \right\}
$$
với $\alpha$ là độ chính xác của phân phối và $M+1$ là số phần tử của $\mathbf{w}$ ($\mathbf{w}$ là hệ số của đa thức bậc $M$).

>[!note]+
>Nhớ lại phân phối Gaussian cho một vector ngẫu nhiên $D$ chiều ở [[Notes/Gaussian Distribution\|Gaussian Distribution]], ta có:
>$$
>\mathcal{N}(\mathbf{x} \mid \pmb{\mu}, \pmb{\Sigma}) = \frac{1}{(2\pi)^{D/2}} \frac{1}{|\pmb{\Sigma}|^{1/2}} \exp \left\{ -\frac{1}{2} (\mathbf{x} - \pmb{\mu})^T \pmb{\Sigma}^{-1} (\mathbf{x} - \pmb{\mu}) \right\}
>$$
>Với $\pmb{\mu}$ là vector trung bình, ở đây ta giả sử $\mathbf{w}$ có phân phối chuẩn tắc, do đó $\pmb{\mu}=\mathbf{0}$.  Còn $\pmb{\Sigma}$ là ma trận hiệp phương sai của phân phối. Ta định nghĩa độ chính xác của phân phối là $\pmb{\beta} = \pmb{\Sigma}^{-1}$ hay ${} \pmb{\beta}^{-1} = \pmb{\Sigma} {}$. Nếu chọn $\pmb{\beta} = \alpha \mathbf{I}$ với $\mathbf{I}$ là ma trận đơn vị thì ${} \pmb{\Sigma} = \pmb{\beta}^{-1} = \alpha^{-1} \mathbf{I}$ do đó $|\pmb{\Sigma}| = (\alpha^{-1})^{M+1} = \alpha^{-(M+1)} {}$ (bởi vì ${} \pmb{\Sigma}$ là một ma trận chéo, và định thức ma trận chéo bằng tích các phần tử trên đường chéo).
>
>Cuối cùng thay $\mathbf{w}$ có chiều $M+1$ cho $\mathbf{x}$, ta được:
>$$
\begin{align}
\mathcal{N}(\mathbf{\mathbf{w}} \mid \mathbf{0}, \alpha^{-1}\mathbf{I}) &= \frac{1}{(2\pi)^{M+1/2}} \frac{1}{(\alpha^{-(M+1)})^{1/2}} \exp\left\{ -\frac{1}{2}\mathbf{w}^T \alpha \pmb{I} \mathbf{w} \right\} \\ \\
&= \left( \frac{\alpha}{2\pi} \right)^{(M+1)/2} \exp\left\{ -\frac{\alpha}{2}\mathbf{w}^T\mathbf{w} \right\}
\end{align}
>$$

Ta thấy khi thay đổi giá trị $\alpha$ thì thay đổi luôn cả phân phối của $\mathbf{w}$, do đó những giá trị như $\alpha$ được gọi là **siêu tham số** (hyperameter). Những siêu tham số này được ta đặt trước (hoặc có thể tìm luôn) trước khi khi huấn luyện mô hình dựa trên dữ liệu có được.

Sử dụng định lý Bayes, phân phối hậu nghiệm của $\mathbf{w}$ tỉ lệ với tích của phân phối tiên nghiệm và hàm likelihood
$$
p(\mathbf{w} \mid \mathbf{x}, \mathbf{y}, \alpha, \beta) \propto p(\mathbf{y} \mid \mathbf{x}, \mathbf{w}, \beta)p(\mathbf{w} \mid \alpha)
$$
khi ấy phân phối hậu nghiệm của $\mathbf{w}$ điều kiện với dữ liệu ($\mathbf{x}, \mathbf{y}, \beta$) (chính là $p(\mathbf{w} \mid \mathcal{D})$ ở phần [[Notes/Bayesian Probabilities\|Bayesian Probabilities]]) và siêu tham số $\alpha$ sẽ tỉ lệ với tích của hàm likelihood ${} p(\mathbf{y} \mid \mathbf{x}, \mathbf{w}, \beta)$ (nó chính là $p(\mathcal{D} \mid \mathbf{w})$ ở phần [[Notes/Bayesian Probabilities\|Bayesian Probabilities]] nếu ta xem $\mathcal{D}$ gồm $\mathbf{y}$ và $\mathbf{y}$ điều kiện $\mathbf{x}, \beta$) và phân phối tiên nghiệm $p(\mathbf{w} \mid \alpha)$ (phân phối xác suất của $\mathbf{w}$ trước khi quan sát dữ liệu).

>[!danger]+ Giải thích có thể sai (mình sẽ cố gắng giải thích)
>Ta có (dùng định lý Bayes):
>$$
\begin{aligned}
p(\mathbf{w} \mid \mathbf{x}, \mathbf{y}, \alpha, \beta) &= \frac{p(\mathbf{y} \mid \mathbf{x}, \mathbf{w}, \alpha, \beta)p(\mathbf{x}, \mathbf{w}, \alpha, \beta)}{p(\mathbf{x}, \mathbf{y}, \alpha, \beta)} \\
\implies p(\mathbf{w} \mid \mathbf{x}, \mathbf{y}, \alpha, \beta) &\propto p(\mathbf{y} \mid \mathbf{x}, \mathbf{w}, \alpha, \beta)p(\mathbf{x}, \mathbf{w}, \alpha, \beta)
\end{aligned}
>$$
>Tiếp tục áp dụng định lý Bayes cho $p(\mathbf{x}, \mathbf{w}, \alpha, \beta)$ ta có:
>$$
\begin{aligned}
p(\mathbf{x}, \mathbf{w}, \alpha, \beta) &= p(\mathbf{w} \mid \mathbf{x}, \alpha, \beta)p(\mathbf{x}, \alpha, \beta) \\
\implies p(\mathbf{x}, \mathbf{w}, \alpha, \beta) &\propto p(\mathbf{w} \mid \mathbf{x}, \alpha, \beta)
\end{aligned}
>$$
>Ta có định nghĩa sau, nếu:
>$$
>P(A \mid B,C) = P(A \mid B)
>$$
>khi đó $A$ **độc lập điều kiện** với $C$ điều kiện $B$, tức là $A \mid B$ độc lập với $C \mid B$ (kí hiệu này mình dùng bừa cho dễ hiểu ấy chứ nó không chắc là đúng đâu 🥲) hay sau khi quan sát $B$ thì $A$ với $C$ độc lập với nhau.
>
>Từ định nghĩa trên, nếu mình xem $\mathbf{w} \mid \alpha$ độc lập điều kiện với $\mathbf{x}, \beta \mid \alpha$ thì $p(\mathbf{w} \mid \mathbf{x}, \alpha, \beta) = p(\mathbf{w} \mid \alpha)$. Tương tự, $\mathbf{y} \mid \mathbf{x}, \mathbf{w}, \beta$ độc lập điều kiện với $\alpha \mid \mathbf{x}, \mathbf{w}, \beta$, do đó $p(\mathbf{y} \mid \mathbf{x}, \mathbf{w}, \alpha, \beta) = p(\mathbf{y} \mid \mathbf{x}, \mathbf{w}, \beta)$. Vậy:
>$$
>p(\mathbf{w} \mid \mathbf{x}, \mathbf{y}, \alpha, \beta) \propto p(\mathbf{y} \mid \mathbf{x}, \mathbf{w}, \beta)p(\mathbf{w} \mid \alpha)
>$$
>
>Tuy nhiên có 1 điều mình không giải thích, là tại sao lại độc lập điều kiện với nhau, still a bí ẩn 😭.

Để tìm giá trị $\mathbf{w}$ tối ưu được $p(\mathbf{w} \mid \mathbf{x}, \mathbf{y}, \beta, \alpha)$ ta phải tối ưu cả hai hàm là hàm likelihood $p(\mathbf{y} \mid \mathbf{x}, \mathbf{w}, \beta)$ và phân phối tiên nghiệm $p(\mathbf{w} \mid \alpha)$ (việc tối ưu này được gọi là *MAP* hay *Maximum Posterior* được giới thiệu trong [[Notes/Bayesian Probabilities\|Bayesian Probabilities]], khác với maximum likelihood chỉ tối ưu mỗi hàm likelihood). Tương tự như maximum likelihood, ta sẽ tối đa hàm log thay vì hàm chính, ngoài ra mình có thể dùng hàm log âm luôn nên sẽ tối thiểu thay cho tối đa:
$$
\begin{aligned}
-\ln p(\mathbf{w} \mid \mathbf{x}, \mathbf{y}, \beta, \alpha) &\propto \ln [p(\mathbf{y} \mid \mathbf{x}, \mathbf{w}, \beta)p(\mathbf{w} \mid \alpha) ] \\
&= -\ln p(\mathbf{y} \mid \mathbf{x}, \mathbf{w}, \beta) + [-\ln p(\mathbf{w} \mid \alpha)]
\end{aligned}
$$
Như đã biết ở phía trên, mình sẽ bỏ đi các giá trị dư thừa ở phần bên trái của hàm log âm đầu tiên là bỏ đi $- \frac{N}{2} \ln 2\pi +\frac{N}{2} \ln \beta$. Ta được:
$$
\frac{\beta}{2} \sum_{n=1}^N (y_{n} - f(x_{n}, \mathbf{w}))^2
$$
Ở phía bên phải cũng tương tự, mình sẽ bỏ đi các giá trị dư thừa (bởi vì đạo hàm xuống cũng bằng $0$ hết rồi), đầu tiên là bỏ đi $\frac{\alpha}{2\pi}^{(M+1) / 2}$ bởi vì đây là hằng số, tiếp theo:
$$
\begin{aligned}
-\ln p(\mathbf{w} \mid \alpha) &\propto -\ln \exp\left\{ -\frac{\alpha}{2}\mathbf{w}^T\mathbf{w} \right\} \\
&= \frac{\alpha}{2} \mathbf{w}^T\mathbf{w}
\end{aligned}
$$
Vậy kết hợp cả hai lại, ta được phương trình mới cần tối thiểu là:
$$
\frac{\beta}{2} \sum_{n=1}^N (y_{n} - f(x_{n}, \mathbf{w}))^2 + \frac{\alpha}{2} \mathbf{w}^T\mathbf{w}
$$
Nếu nhìn kĩ thì phương này có dạng của bình phương nhỏ nhất kèm với phần chính quy hoá, ta có $\mathbf{w}^T \mathbf{w} = ||\mathbf{w}||$, tiếp tục đặt $\lambda =\alpha / \beta$ và bỏ đi hằng số $\beta$ (ta cũng không quan tâm đến nó), ta có:
$$
\begin{aligned}
\beta \left(\frac{1}{2} \sum_{n=1}^N (y_{n} - f(x_{n}, \mathbf{w}))^2 + \frac{\lambda}{2} ||\mathbf{w}|| \right) \\
\implies 
\frac{1}{2} \sum_{n=1}^N (y_{n} - f(x_{n}, \mathbf{w}))^2 + \frac{\lambda}{2} ||\mathbf{w}||
\end{aligned}
$$

---

Phần trước: [[Notes/Gaussian Distribution\|Gaussian Distribution]]
Phần sau: [[Notes/Bayesian Curve Fitting\|Bayesian Curve Fitting]]

---
# References

- [Bishop] Pattern Recognition and Machine Learning - Bishop (chapter 1.2)
- [Comp.ai]  [comp.ai.neural-nets FAQ, Part 3 of 7: GeneralizationSection - What is Bayesian Learning? (faqs.org)](http://www.faqs.org/faqs/ai-faq/neural-nets/part3/section-7.html)
- [Stuck with handling of conditional probability in Bishop's "Pattern Recognition and Machine Learning" (1.66) - Mathematics Stack Exchange](https://math.stackexchange.com/questions/171226/stuck-with-handling-of-conditional-probability-in-bishops-pattern-recognition)