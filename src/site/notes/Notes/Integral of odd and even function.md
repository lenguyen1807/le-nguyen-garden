---
{"dg-publish":true,"permalink":"/notes/integral-of-odd-and-even-function/","noteIcon":"📝","created":"2024-08-02T10:46:38.344+07:00","updated":"2024-08-02T10:48:17.465+07:00"}
---


Đặt $f$ là một hàm số lẻ và $g$ là một hàm số chẵn (giả sử $f$ và $g$ đều liên tục trên đoạn $[-a, a]$). Khi đó:
$$
\begin{align*}
\int_{-a}^a f(x) dx &= 0 \\
\int_{-a}^a g(x) dx &= 2\int_{0}^{a}g(x)dx
\end{align*}
$$
Đối với $f$, ta có:
$$
\begin{align*}
\int_{-a}^a f(x)dx &= \int_{-a}^0 f(x)dx + \int_{0}^a f(x)dx \\
\end{align*}
$$
xét tích phân có $-a$, nếu ta đặt $-y = x$ thì $-dy = dx$ và $x$ chạy từ $-a \to 0$ thì $y$ chạy từ $a \to 0$. Khi đó:
$$
\begin{align*}
\int_{-a}^a f(x)dx &= -\int_{a}^0 f(-y)dy + \int_{0}^a f(x)dx \\
&= \int_{0}^a f(-y)dy + \int_{0}^a f(x)dx \\
&= -\int_{0}^a f(y)dy + \int_{0}^a f(x)dx \hspace{5pt} \text{($f$ là hàm lẻ)} \\
&= 0
\end{align*}
$$
Tương tự, đối với $g$, ta có:
$$
\begin{align*}
\int_{-a}^{a} g(x)dx &= \int_{-a}^0 g(x)dx + \int_{0}^a g(x)dx \\
\end{align*}
$$
xét tích phân có $-a$, đặt $-y = x$, ta có:
$$
\begin{align*}
\int_{-a}^a g(x)dx &= -\int_{a}^0 g(-y)dy + \int_{0}^a g(x)dx \\
&= \int_{0}^a g(-y)dy + \int_{0}^a g(x)dx \\
&= \int_{0}^a g(y)dy + \int_{0}^a g(x)dx \hspace{5pt} \text{($g$ là hàm lẻ)} \\
&= 2 \int_{0}^a g(x)dx
\end{align*}
$$

---
# References