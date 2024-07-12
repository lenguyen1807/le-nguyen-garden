---
{"dg-publish":true,"permalink":"/zettel/poisson-distribution-and-stirling-approximation/","noteIcon":"📝","created":"2024-06-30T19:11:48.454+07:00","updated":"2024-07-12T08:42:41.479+07:00"}
---


Xét phân phối $X$ như dưới đây:
$$
P(X = r \mid \lambda) = e^{-\lambda} \dfrac{\lambda^r}{r!} \hspace{5pt} \text{với $r \in \{0, 1, 2, \dots\}$}.
$$
ta gọi phân phối trên là **phân phối Poisson**.

>[!note]+
>Phân phối chuẩn hay còn gọi là phân phối gaussian có công thức như sau:
>$$
>P(X = x \mid \mu, \sigma^2) = \dfrac{1}{\sigma\sqrt{2 \pi}} e^{\dfrac{-(x - \mu)^2}{2\sigma^2}}.
>$$
>trong đó $\mu$ là trung bình của $X$, $\sigma^2$ là phương sai của $X$ và $\sigma$ là độ lệch chuẩn của $X$.

Khi $\lambda$ đủ lớn (thông thường là $\lambda > 1000$), ta có thể xấp xỉ phân phối Poisson với phân phối chuẩn có $\mu = \lambda$ và $\sigma^2 = \lambda \implies \sigma = \sqrt{\lambda}$ (tìm hiểu thêm ở [đây](https://stats.stackexchange.com/questions/83283/normal-approximation-to-the-poisson-distribution?rq=1)), vậy:
$$
e^{-\lambda} \dfrac{\lambda^r}{r!} \simeq\dfrac{1}{\sqrt{2\pi \lambda}} e^{\dfrac{-(r - \lambda)^2}{2\lambda}}.
$$
Xét phương trình xấp xỉ phía trên, nếu thay $r = \lambda$, ta được:
$$
\begin{aligned}
e^{-\lambda} \dfrac{\lambda^\lambda}{\lambda!} &\simeq \dfrac{1}{\sqrt{2\pi \lambda}} e^{\dfrac{-(\lambda - \lambda)^2}{2\lambda}} \\
\Leftrightarrow e^{-\lambda} \dfrac{\lambda^\lambda}{\lambda!} &\simeq \dfrac{1}{\sqrt{2\pi \lambda}} \\
\Leftrightarrow \lambda! &\simeq \lambda^{\lambda} e^{-\lambda} \sqrt{2\pi\lambda}.
\end{aligned}
$$
Ở phương trình xấp xỉ trên, ta có thể thấy giai thừa của một số được xấp xỉ bằng một công thức khác, ta gọi công thức đó là **xấp xỉ Stirling** ([Stirling's approximation](https://en.wikipedia.org/wiki/Stirling%27s_approximation)). Nếu ta lấy $\ln$ của xấp xỉ stirling, ta được:
$$
\begin{aligned}
\ln x! &\simeq \ln x^xe^{-x}\sqrt{2\pi x} \\
&\simeq \ln x^x  + \ln e^{-x} + \ln \sqrt{ 2\pi x } \\
&\simeq x\ln x - x + \frac{1}{2}\ln 2 \pi x.
\end{aligned}
$$
>[!note]+
>Ngoài cách viết như trên, người ta cũng thường viết như sau:
>$$
>x\ln x - x + O(\ln x).
>$$

Giá trị nằm phía cuối $\frac{1}{2} \ln 2\pi x$ được gọi là *next-order correction term* (mình cũng không rõ đoạn này), ta hoàn toàn có thể bỏ nó và sử dụng:
$$
x! \simeq x\ln x - x.
$$
Ta biết rằng:
$$
{N \choose r} = \frac{N!}{(N - r)! r!}.
$$
Do đó, ta hoàn toàn có thể xấp xỉ $N \choose r$ bằng cách dùng xấp xỉ Stirling:
$$
\begin{aligned}
\ln \frac{N!}{(N - r)! r!} &= \ln N! - \ln (N-r)! - \ln r \\
&\simeq N\ln N - N - (N-r)\ln(N-r) + (N-r) - r\ln r + r \\
&= N\ln N - (N-r)\ln(N-r) - r\ln r \\
&= (N-r)\ln N - (N-r)\ln(N-r) + r\ln N - r\ln r\\
&= (N-r)\ln \frac{N}{N-r} + r\ln \frac{N}{r}.
\end{aligned}
$$
Ta biết rằng:
$$
\log_{2}x = \frac{\log_{e}x}{\log_{e}2} = \frac{\ln x}{\ln 2}.
$$
tức là giữa $\ln x$ và $\log_{2} x$ (nếu chỉ viết $\log$ thì ta hiểu đây là $\log_{2}$) chỉ khác nhau một hằng số, do đó việc xấp xỉ $\ln x!$ có thể thay thế thành $\log x!$ mà không cần thay đổi công thức, chỉ thêm hằng số vào, do đó có thể bỏ luôn hằng số đó trong khi xấp xỉ.
$$
\log{N\choose r} \simeq (N-r)\log \frac{N}{N-r} + r\log \frac{N}{r}.
$$
---
# References

- [MacKay] Information Theory, Inference and Learning Algorithms - MacKay (chapter 1)