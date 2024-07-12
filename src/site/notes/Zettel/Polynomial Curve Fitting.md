---
{"dg-publish":true,"permalink":"/zettel/polynomial-curve-fitting/"}
---


Giả sử bạn LN có số tiền là $x \in \mathbb{R}$ và LN muốn dự đoán xem với số tiền $x$ này, LN có thể mua được bao nhiêu cái bánh xèo, bởi vì bà bán bánh xèo bả không muốn tiết lộ giá 1 cái bánh xèo và giá có thể mỗi ngày thay đổi (nhưng bánh xèo ngon).

Gọi số bánh xèo mua được là $y \in \mathbb{R}$ (trong thực tế số bánh sẽ là số nguyên, nhưng mà mình giả sử bà bán bánh có khả năng nào đó bán được số bánh xèo là số thực).

>[!important]
>Bài toán dùng một giá trị đầu vào $x$ để dự đoán một giá trị số thực $y$ nào đó được gọi là bài toán **hồi quy** (regression).

Giả sử LN thu thập dữ liệu cho việc dự đoán của mình thông qua $N$ lần mua, đặt là $\mathbf{x} \equiv (x_1, ..., x_N)^T$. Với mỗi $x_i$, LN biết được số bánh xèo mua được là $y_i$, vậy ta có $\mathbf{y} \equiv (y_1, ..., y_N)^T$. Ta gọi dữ liệu mà LN thu thập được $\{ (x_1, y_1), ..., (x_N, y_N) \}$ là **tập huấn luyện** (training set). Dựa trên tập huấn luyện ấy, LN muốn dự đoán giá trị $\hat{y}$ cho một giá trị $\hat{x}$ mới (lần mua mới). Vì vậy LN cần tìm ra một mô hình nào đó, để khi đưa vào input $\hat{x}$, mô hình cho ra được giá trị $\hat{y}$ phù hợp.

![Pasted image 20240415140535.png](/img/user/Attachment/Pasted%20image%2020240415140535.png)
Hình: Dữ liệu mà LN thu thập được sau $N = 10$ lần mua

>[!note]
>Đường cong màu xanh lá tương ứng với hàm $f(x) = \sin(2\pi x) + 2$, mình dùng hàm này để sinh ra data, sau đó cộng thêm với giá trị random được lấy từ phân phối chuẩn với $\mu = 0$ và $\sigma = 0.3$ (mục đích là để tạo ra noise cho giống với data thực tế) cho ra các giá trị $y$ màu đỏ (theo [Bishop]). Mục đích của chúng ta là dựa trên data để tìm ra hàm $f$ tốt nhất, thế nhưng data thông thường sẽ có rất nhiều noise và hàm $f$ trong thực tế rất khó tìm.

LN đoán rằng, việc dùng một hàm đa thức như dưới có thể dự đoán được số bánh:
$$
f(x, \mathbf{w}) = w_{0} + w_{1}x + w_{2}x^2 + \dots w_{M}x^M = \sum_{i=0}^M w_{i}x^i
$$
trong đó $\mathbf{w} = (w_0, w_1, ..., w_M)^T$ là bộ tham số của hàm đa thức $f(x, \mathbf{w})$ mà LN chọn và $M$ là *bậc* của đa thức ấy. Vậy có hai thứ mà ta cần để ý khi dùng đa thức (hay mô hình) này, đó chính là $M$ và $\mathbf{w}$, để tìm được mô hình phù hợp với data đã có, ta cần tìm $\mathbf{w}$ và $M$ phù hợp.

>[!note]
>Mặc dù $f(x, \mathbf{w})$ là một hàm không tuyến tính của $x$ nhưng lại là một hàm tuyến tính của $\mathbf{w}$, vì vậy ta có thể xem bài toán này là một bài toán **hồi quy tuyến tính** (linear regression) bởi vì đây là bài toán regression và ta dùng mô hình linear 🤯.

Để tìm được $\mathbf{w}$ phù hợp với dữ liệu, ta cần một hàm để đánh giá xem, liệu giá trị $\mathbf{w}$ mà ta chọn tốt hay là không (không tốt thì chọn lại, chọn nào tốt thì thôi 👌). Hàm đánh giá đó được gọi là **hàm lỗi** (error function), kí hiệu $E(\mathbf{w})$, $E(\mathbf{w})$ càng thấp (lỗi càng ít) thì $\mathbf{w}$ càng phù hợp với dữ liệu, do đó mục tiêu tối thượng 😤 là phải tìm giá trị $\mathbf{w}^\star$ sao cho $E(\mathbf{w}^\star)$ là nhỏ nhất.

Với mỗi loại bài toán khác nhau thì ta sẽ chọn error function khác nhau. Để cho dễ, mình sẽ chọn hàm lỗi như sau:
$$
E(\mathbf{w}) = \frac{1}{2} \sum_{i=1}^N [f(x_{i}, \mathbf{w}) - y_{i}]^2
$$
ta có thể hiểu hàm lỗi này là tổng bình phương độ lỗi (hay độ khác nhau) giữa số bánh dự đoán $f(x_i, \mathbf{w})$ và số bánh thực sự mua được $y_i$. Ngoài ra $E(\mathbf{w}) = 0$ khi và chỉ khi $f(x_{i}, \mathbf{w}) = y_{i} \hspace{3pt} \forall i = 1\dots N$, nghĩa là không có lỗi nào ở đây, $f(x, \mathbf{w})$ khớp hoàn toàn với dữ liệu.

>[!note]+
>Với hàm lỗi như trên, ta hoàn toàn có thể tìm được giá trị $\mathbf{w}^\star$ bởi vì $f(x_i, \mathbf{w})$ là một hàm linear nên $[f(x_{i}, \mathbf{w}) - y_{i}]^2$ là một hàm bậc 2, do đó đạo hàm của $E(\mathbf{w})$ theo $w_i$ là một hàm linear, do đó tồn tại một nghiệm duy nhất.
>$$
\dfrac{\partial E(\mathbf{w})}{\partial \mathbf{w}} = \begin{bmatrix}
\dfrac{\partial{E(\mathbf{w})}}{\partial w_{0}} \dots 
\dfrac{\partial{E(\mathbf{w})}}{\partial w_{N}}
\end{bmatrix}^T
>$$

Vấn đề tìm theo đó chính là tìm giá trị $M$ phù hợp. 

---

Phần sau: [[Zettel/Introduction (Prob)\|Introduction (Prob)]]

---
# References

- [Bishop] Pattern Recognition and Machine Learning - Bishop (chapter 1.1).