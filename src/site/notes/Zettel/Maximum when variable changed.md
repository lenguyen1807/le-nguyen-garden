---
{"dg-publish":true,"permalink":"/zettel/maximum-when-variable-changed/"}
---


>[!note]+
>Cái này mình lấy từ [Bishop] vì nó quá hay 🥰.

>[!example]+ Giải bài 1.4
>
>![Pasted image 20240424110908.png](/img/user/Attachment/Pasted%20image%2020240424110908.png)

Giả sử ta có hàm khả vi $f(x)$ với $x$ là số thực (không phải biến ngẫu nhiên), để tìm giá trị lớn nhất của $f(x)$, ta đạo hàm $f'(x)$ sau đó cho $f'(x) = 0$ để tìm được giá trị $x$ thoả mãn, gọi là $\hat{x}$ đi.

Tiếp theo, ta có một biến mới là $y$ với $x = g(y)$. Đổi biến hàm $f(x)$ sang $f(g(y))$ (là một hàm của $y$), ta đặt $\tilde{f}(y) = f(g(y))$ (để biết đây là một hàm của $y$). Để tìm giá trị lớn nhất của $\tilde{f}(y)$, ta đạo hàm và sau đó cho bằng $0$. Đầu tiên đạo hàm:
$$
\begin{aligned}
\frac{d\tilde{f}(y)}{dy} &= \frac{df(g(y))}{g(y)} \frac{dg(y)}{y} \\
\implies  \tilde{f}'(y) &= f'(g(y))g'(y)
\end{aligned}
$$
Sau đó cho bằng $0$ (gọi giá trị làm đạo hàm bằng $0$ là $\hat{y}$):
$$
\tilde{f}'(\hat{y}) = 0 \implies f'(g(\hat{y})) = 0 \hspace{3pt} \text{hoặc} \hspace{3pt} g'(\hat{y}) = 0 \hspace{3pt} \text{hoặc cả 2 $=0$}
$$
Xét trường hợp $f'(g(\hat{y})) = 0$, ta thấy rằng $f'(\hat{x}) = 0$, do đó $f'(g(\hat{y})) = f'(\hat{x}) \implies g(\hat{y}) = \hat{x}$. Vậy có nghĩa là ta có thể tìm giá trị lớn nhất của $f(x)$ thông qua $y$ với $x = g(y)$. Tương tự với trường hợp $f'(g(\hat{y})) = 0$ và $g'(\hat{y}) = 0$.

Tuy nhiên ta cần để ý trường hợp chỉ $g'(\hat{y}) = 0$. Trong solution tác giả giả sử luôn $g'(\hat{y}) = 0$ bởi vì ta chỉ quan tâm đến trường hợp $f'(g(\hat{y})) = 0$ thôi, việc $g'(\hat{y}) = 0$ mà $f'(g(\hat{y})) \neq 0$ có thể được giải quyết bằng cách chọn một biến khác, gọi là $t$ đi, lúc này $x = \tilde{g}(t)$ và ta được $f'(\tilde{g}(\hat{t})) = 0$ và ta không cần quan tâm $\tilde{g}'(\hat{t})$ bằng $0$ hay khác $0$ nữa. Do mục đích là tìm giá trị lớn nhất của $f(x)$ thông qua một biến mới nào đó, do đó ta có thể chọn lại biến mới sao cho thoả mãn các giả sử của ta là được.

Vậy ở đây, tác giả muốn nói là, với $x$ và $y$ (liên quan với nhau thông qua $x = g(y)$) không là biến ngẫu nhiên thì ta có thể tìm giá trị lớn nhất của $f(x)$ thông qua $y$. Nhưng đối với hai biến ngẫu nhiên $X$ và $Y$ thì việc này không xảy ra (không thể tìm giá trị lớn $f(X)$ thông $Y$) do bị ảnh hưởng bởi jacobian factor.

Giờ xét $X$ và $Y$ là hai biến ngẫu nhiên với $X = g(Y$) (lưu ý $g$ là hàm khả nghịch). Đặt $p_x$ và $p_y$ lần lượt là hàm mật độ xác suất của $X$ và $Y$. Để tìm được mật độ xác suất của $Y$, ta dùng công thức 1.17 như sau:
$$
p_{y}(y) = p_{x}(g(y)) \hspace{2pt} |g'(y)|
$$
Giả sử giá trị $\hat{x}$ là giá trị để làm cho $p_x$ lớn nhất, tức là $p_{x}'(\hat{x}) = 0$. Để tìm giá trị lớn nhất của $p_y(y)$ ta đạo hàm và sau đó cho giá trị đạo hàm bằng $0$. Giả sử $g'(y) \neq 0$ (khi đó ta mới có thể đạo hàm $|g'(y)|$) và đặt $|g'(y)| = sg'(y)$ với $s \in \{-1, 1\}$.

Đầu tiên ta lấy đạo hàm:
$$
\begin{aligned}
p_{y}'(y) = \frac{dp_{y}(y)}{dy} &= \frac{dp_{x}(g(y))}{dy} sg'(y) + p_{x}(g(y)) \frac{dsg'(y)}{dy} \\
&= sp_{x}'(g(y))g'(y)\hspace{1pt}|g'(y)| + p_{x}(g(y))\hspace{1pt}sg''(y) \\
&= sp_{x}'(g(y))[g'(y)]^2 + sp_{x}(g(y))\hspace{1pt}g''(y) \\
\end{aligned}
$$
Giả sử giá trị $\hat{y}$ là giá trị để làm cho $p_y$ lớn nhất và **giả sử** $\hat{x} = g(\hat{y})$, tức là $p_x(\hat{x}) = p_x(g(\hat{y})) = 0$ (tương tự như $x$ và $y$ không là biến ngẫu nhiên). Khi đó:
$$
\begin{aligned}
p_{y}'(\hat{y}) &= sp_{x}'(g(\hat{y}))[g'(\hat{y})]^2 + sp_{x}(g(\hat{y}))\hspace{1pt}g''(\hat{y}) \\ 
&= sp_{x}(g(\hat{y}))g''(\hat{y}) \neq 0
\end{aligned}
$$
Vậy rõ ràng nếu $\hat{y}$ là giá trị làm cho $p_y$ lớn nhất và $\hat{x} =g(\hat{y})$ thì điều này lại sai, do đó $\hat{x} \neq g(\hat{y})$. Tức là nếu $X$ và $Y$ là biến ngẫu nhiên thì không có quan hệ nào giữa $\hat{x}$ và $g(\hat{y})$, do đó ta không thể tìm giá trị $X$ làm cho $p_x$ lớn nhất bằng cách tìm giá trị $Y$ làm cho $p_y$ lớn nhất.

Tuy nhiên, nếu ta chọn $g(Y) = X$ sao cho $g$ là một hàm tuyến tính thì mọi chuyện sẽ khác. Giả sử $X = g(Y) = \alpha Y + \beta$. Khi đó:
$$
p'_{y}(\hat{y}) = sp_{x}(g(\hat{y}))g''(\hat{y}) = 0
$$
Do nếu $g(y) = \alpha y + \beta$ thì $g''(y) = 0$ với mọi $y$.

Vậy $p_y'(\hat{y}) = 0 \implies p_x'(g(\hat{y})) = 0 \implies p_x'(\hat{x}) = p_{x}(g(\hat{y})) = 0 \implies  \hat{x} = g(\hat{y})$. Ta có thể thấy bằng việc chọn $g$ là một hàm tuyến tính thì $\hat{x} = g(\hat{y})$, do đó việc chọn hàm $g$ để biến đổi từ $X$ sang $Y$ là rất quan trọng.

---
# References

- [Bishop] Pattern Recoginition and Machine Learning (exercises of I.Introduction).
- [prml-web-sol.dvi (microsoft.com)](https://www.microsoft.com/en-us/research/wp-content/uploads/2016/05/prml-web-sol-2009-09-08.pdf)
- [real analysis - Exercise 1.4 from PRML: Process of Using Transformations to Find Modes of PDFs - Mathematics Stack Exchange](https://math.stackexchange.com/questions/3494289/exercise-1-4-from-prml-process-of-using-transformations-to-find-modes-of-pdfs)
- [real analysis - Linear/non-linear change of variables: $\tilde{f} \ ' (\tilde{y}) = f'(g(\tilde{y})) g'(\tilde{y}) = 0$ and assuming $g'(\tilde{y}) \not= 0$ - Mathematics Stack Exchange](https://math.stackexchange.com/questions/3510938/linear-non-linear-change-of-variables-tildef-tildey-fg-tilde)