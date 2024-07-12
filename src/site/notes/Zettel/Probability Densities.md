---
source: "[[Study/ML Bishop\|ML Bishop]]"
id: 202404191019
date_create: 2024-04-19
dg-publish: true
---
>[!example]+
>Giả sử mình đang xét biến ngẫu nhiên liên tục $X$ với $X$ đại diện cho chiều cao của công dân Việt Nam. Như thông thường, mình sẽ tìm xác suất $p(X = x)$ với $x$ là một số thực, nhưng ai lại quan tâm xác suất để chiều cao là $1.8072003 \hspace{3pt} (m)$ chứ 🥲. Vậy nên khi nói đến biến ngẫu nhiên liên tục, ta sẽ quan tâm xác suất để $X$ nằm trong một khoảng hơn, ví dụ xác suất để một công dân Việt Nam có chiều cao từ $1$ mét $6$ đến $1$ mét $9$, tức là $p(1.6 \leq X \leq 1.9)$. 

Xét $X$ là một biến ngẫu nhiên liên tục, nếu xác suất của $X$ nằm trong khoảng $(x, x + \delta x)$ được xác định bằng công thức $p(x)\delta x$ với $\delta x \to 0$, thì $p(x)$ được gọi là **mật độ xác suất** (probabilty density) trên $x$.

Xác suất để biến ngẫu nhiên $X$ nằm trong khoảng $(a, b)$ được xác định bằng:
$$
p(X \in (a, b)) = p(a < X < b) = \int_{a}^{b} p(x)dx
$$
>[!danger]
>Mình cảm thấy kí hiệu khá là weird, thông thường người ta kí hiệu mật độ xác suất là $f(x)$. Nhưng tác giả kí hiệu hai xác suất trùng nhau, mặc dù nó khác nhau. Giả sử $p(x)$ (đang nói đến mật độ xác suất) có thể khác không, thế nhưng (mình sẽ đặt mật độ xác suất là $f(x)$, nguyên hàm là $F(x)$):
>$$
p(X = x) = p(x) = p(X \in (x, x)) = \int_{x}^x f(x)dx = F(x) - F(x) = 0
>$$
>Xác suất $p(X = x) = p(x)$ (mình đang nói đến xác suất nằm trong một khoảng) tại một điểm $x$ sẽ luôn là $0$ với mọi $x$.
>
>Nhưng mà ta sẽ theo tác giả nhé, mình nghĩ khi tác giả nói đến $p(x)$ (với $x$ là số thực) thì $p(x)$ là mật độ xác suất, còn nói đến $p(X \in (a, b))$ thì tức là xác suất $X$ thuộc đoạn $(a, b)$ nào đó.

>[!note]+
>Như đã nói phía trên $p(X = x) = 0$ với mọi $x$, do đó $p(X = a) = p(X = b) = 0$ nên:
>$$
p(a < X < b) = p(a \leq X \leq b) = p(a \leq X < b) = p(a < X \leq b)
>$$

Tiếp theo, mật độ xác suất $p(x)$ phải thoả mãn một vài điều kiện:
- Xác suất là không âm:
$$
p(x) \geq 0
$$
- Ta đã biết, $p(X \in (a, b))$ là xác suất $X$ nằm trên khoảng $a, b$. Biến ngẫu nhiên $X$ mà ta đang xét là một số thực, do đó $X$ luôn nằm trong $\mathbb{R}$, tức là nằm trong đoạn $(-\infty, \infty)$. Vậy:
$$
p(X \in \mathbb{R}) = \int_{-\infty}^{\infty} p(x)dx = 1
$$
>[!note]+
>Như đã nói ở phần trước, nếu ta viết $p(X)$ thì ta sẽ xét toàn bộ tập xác định của $X$, gọi là $\mathcal{X}$. Khi đó:
>$$
>p(X) = p(X \in \mathcal{X}) = \int_{\mathcal{X}} p(x)dx
>$$
>Thông thường ta sẽ cố gắng đưa tập xác định $\mathcal{X}$ là $\mathbb{R}$, do đó:
>$$
p(X) = p(X \in \mathbb{R}) = 1
>$$

Ta có xác suất để $X$ nằm trong đoạn từ $(-\infty, z)$ là:
$$
P(z) = p(X \leq z) =  p(X < z) = \int_{-\infty}^z p(x)dx
$$
ta gọi $P(z)$ là **phân phối xác suất tích luỹ** (cumulative distribution function) của $X$ (viết tắt là **cdf**). Trong đó $P'(x) = p(x)$.

>[!note]+ Xác minh lại
>Việc $P'(x) = p(x)$ được suy ra dựa vào **Fundamental Theorem Of Calculus** ([Fundamental theorem of calculus - Wikipedia](https://en.wikipedia.org/wiki/Fundamental_theorem_of_calculus#:~:text=The%20fundamental%20theorem%20of%20calculus,cumulative%20effect%20of%20small%20contributions)), trong đó nói rằng, nếu $f(x)$ là một hàm số liên tục trên đoạn $[a, b]$. Ta định nghĩa hàm $F(x)$ như sau:
>$$
>F(x) = \int_{a}^x f(t)dt
>$$
>Thì $F'(x) = f(x)$ trên đoạn $[a,b]$. Nếu ta thay $[a, b]$ thành $(-\infty, \infty)$ thì ta vẫn có được $P'(x) = p(x)$ trên $\mathbb{R}$. Thông thường, ta sẽ cố gắng định nghĩa $p(x)$ (mật độ xác suất) sao cho $p(x)$ liên tục trên $\mathbb{R}$. 

>[!danger]+ Lưu ý nhỏ
>Mật độ xác suất khác với xác suất, mật độ xác suất đại diện cho xác suất trên một đơn vị chiều dài của biến ngẫu nhiên $X$, giống như khối lượng riêng của một vật (tiếng anh khối lượng riêng là *density*) đại diện cho khối lượng trên một đơn vị thể tích. Do đó mật độ xác suất có thể lớn hơn $1$, nhưng điều quan trọng đó là diện tích nằm dưới đồ thị của mật độ xác suất $p(x)$ luôn là $1$ ([Can a probability distribution value exceeding 1 be OK? - Cross Validated (stackexchange.com)](https://stats.stackexchange.com/questions/4220/can-a-probability-distribution-value-exceeding-1-be-ok/4223#4223)) 

>[!info]+ Một chút giải thích của mình (Note on 13/06/2024: WTF bro, mình không hiểu mình đang giải thích gì nữa)
>Đây hoàn toàn là giải thích của mình nên có thể có sai sót trong đây.
>
>Các bạn có thể thấy, xác suất để $X$ nằm trong khoảng $(x, x + \delta x)$ được xấp xỉ bởi giá trị $p(x)\delta x$, bởi vì xác suất để $X$ nằm trong khoảng là phần diện tích dưới đồ thị $p(x)$ từ $x \to x + \delta x$, dựa theo tích phân Riemann, ta có thể xấp xỉ:
>$$
p(X \in (x , x+ \delta x)) = \int_{x}^{x + \delta x}p(x) dx \approx p(x)\delta x
>$$
>Tiếp tục dựa theo tích phân riemann, nếu chia đoạn $[a, b]$ thành $n$ điểm, ta có:
> $$
p(X \in (a, b)) = \int_{a}^b p(x)dx = \lim_{ \delta x \to 0 } \sum_{k=0}^{n-1} p(a + k \delta x) \delta x
> $$
>
>![Pasted image 20240419135539.png](/img/user/Attachment/Pasted%20image%2020240419135539.png)

 Xét hai biến ngẫu nhiên $X$ và $Y$ với $X = g(Y)$. Đặt $P_{x}$ là cdf của $X$ và $P_y$ là cdf của $Y$. Tương tự, đặt $p_x$ là mật độ xác suất của $X$ và $p_y$ là mật độ xác suất của $Y$. Khi đó:
$$
p_{y}(y) = p_{x}(g(y)) | g'(y) |
$$
Ta gọi $|g'(y)|$ là **jacobian factor**. Hàm mật độ xác suất $p_x(x)$ sau khi chuyển từ biến ngẫu nhiên $X$ sang biến ngẫu nhiên $Y$ bằng hàm không tuyến tính $g$ với $X = g(Y)$ sẽ bị biến đổi khác đi, từ một hàm đơn giản khác sang một hàm mới (có thể phức tạp hơn), điều này là do jacobian factor.

>[!note]+ Chứng minh
>[[Zettel/Change of random variable\|Change of random variable]]

Nếu ta có nhiều biến ngẫu nhiên $X_1, \dots, X_D$, được định nghĩa chung bằng vector $\mathbf{x} = (x_1, \dots, x_D)$, khi đó ta định nghĩa hàm **mật độ xác suất đồng thời** $p(\mathbf{x}) = p(x_1, \dots, x_D)$ sao cho xác suất $\mathbf{x}$ thuộc một phần thể tích vô cùng nhỏ (infinitesimal volume) $\delta \mathbf{x}$ (có chứa $\mathbf{x}$) được xác định bởi $p(\mathbf{x})\delta \mathbf{x}$.

>[!note]+
>Khi ở nhiều chiều hơn, một "khoảng" của ta sẽ trở nên khác. Ví dụ ở 1 chiều $\mathbf{x} = (x)$ thì khoảng ở đây sẽ là một khoảng trên đường thẳng từ $(a, b)$ nào đó, nếu ở 2 chiều $\mathbf{x} = (x_1, x_2)$ thì "khoảng" ở đây là một hình chữ nhật, ở 3 chiều là một hình hộp chữ nhật, ở 4 chiều thì chịu 🥲, đùa đấy, ở chiều cao hơn thì sẽ được gọi là **hyper-rectangle**. Ngoài ra chữ *infinitesimal* (vô cùng nhỏ) có nghĩa là một số $x$ nào đó rất gần $0$ và không có số nào gần hơn nó.

Tương tự như mật độ xác suất 1 biến, ta cũng có:
- Xác suất không âm:
$$
p(\mathbf{x}) \geq 0
$$
- Phần tổng diện tích (đúng hơn là thể tích với nhiều chiều) luôn là $1$:
$$
\int p(\mathbf{x}) d\mathbf{x} = 1
$$

>[!note]+
>Kí hiệu $\int$ có nghĩa là tích phân toàn bộ không gian của $\mathbf{x}$, giả sử trong không gian 2 chiều, ta có:
>$$
\int p(\mathbf{x}) d\mathbf{x} = \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} p(x_{1}, x_{2}) dx_{1} dx_{2} = 1
>$$
>Tương tự lên $3, 4, \dots$ chiều hay $N$ chiều, ta có:
>$$
\int p(\mathbf{x}) d\mathbf{x} = \int \dots \int p(x_{1}, \dots, x_{N}) dx_{1} \dots dx_{N} = 1
>$$
>Nếu xét trong 2 chiều, ta có xác suất để $\mathbf{x}$ nằm trong hình chữ nhật được tạo bởi 4 đường thẳng $X = a, X = b, Y = c, Y = d$ là:
>$$
p(a < X < b, c < Y < d) = \int_{c}^{d} \int_{a}^{b} p(x, y) dx dy
>$$
>Nếu ta viết (chỉ xét trong không gian 2 chiều):
>$$
\begin{aligned}
p(a < X < b) = p(a < X < b, Y) &= \int_{-\infty}^{\infty} \int_{a}^{b} p(x, y) dx dy \\
&= \int_{a}^{b} \left[ \int_{-\infty}^{\infty} p(x, y)dy \right] dx
\end{aligned}
>$$
>thì đây chính là xác suất biên (tổng cũng tương tự tích phân, ta lấy tổng các biến ngẫu nhiên còn lại như đã định nghĩa ở phần trước). Ta có thể thấy $\int_{-\infty}^{\infty} p(x, y)dy$ đóng vai trò như $p_x(x)$.

Nếu $X$ là biến ngẫu nhiên rời rạc, ta gọi $p(x)$ là **hàm khối xác suất** (probability mass function). Phân biệt một tí với hàm mật độ xác suất, hàm khối xác suất cũng thể được xem là xác suất của biến ngẫu nhiên rời rạc, do đó ta có thể gọi hàm khối xác suất $p(x)$ là phân phối xác suất của $X$, tức là $p(x) = p(X = x)$. Ta định nghĩa cdf của biến rời rạc cũng tương tự:
$$
P(z) = p(X \leq z) = \sum_{x \leq z} p(x)
$$
Tương tự như biến ngẫu nhiên rời rạc, sum rule, product rule và định lý Bayes vẫn có thể áp dụng với biến ngẫu nhiên liên tục. Đặt $X$ và $Y$ là hai biến ngẫu nhiên liên tục, ta có:
$$
\begin{aligned}
p(x) &= \int p(x, y) dy \\
p(x, y) &= p(y \mid x) p(x) \\
\implies p(x,y) &= \int p(y \mid x) p(x) dy \\
&= \int p(x \mid y) p(y) dy
\end{aligned}
$$
>[!bug]+
>Việc chứng minh hai công thức này thì mình chịu, vượt quá sức của mình rồi 🥲

>[!note]+ 
>Nếu ta tổng quát hoá việc đổi biến lên nhiều chiều, tức là đổi từ vector ngẫu nhiên $\mathbf{x}$ sang $\mathbf{y}$ với $\mathbf{x} = g(\mathbf{y})$, mỗi vector có mật độ xác suất tương ứng là $p_{\mathbf{x}}$ và $p_{\mathbf{y}}$. Khi đó:
>$$
>p_{\mathbf{y}}(\mathbf{y}) = p_{\mathbf{x}}(g(\mathbf{y})) \left| \det\left( \frac{\partial g(\mathbf{y})}{\partial \mathbf{y}} \right) \right|
>$$
>trong đó $\det$ là định thức và $\partial g(\mathbf{y}) / \partial y$ là ma trận Jacobian.

---

Phần trước: [[Zettel/Introduction (Prob)\|Introduction (Prob)]]
Phần sau: [[Zettel/Expectations and covariances\|Expectations and covariances]]

---
# References

- [Bishop] Pattern Recognition and Machine Learning - Bishop (chapter 1.2)
- [The idea of a probability density function - Math Insight](https://mathinsight.org/probability_density_function_idea)
- [calculus - Intuitive idea behind the probability density function - Mathematics Stack Exchange](https://math.stackexchange.com/questions/709209/intuitive-idea-behind-the-probability-density-function)
- [integration - Change of variable in a probability density function - Mathematics Stack Exchange](https://math.stackexchange.com/questions/1424388/change-of-variable-in-a-probability-density-function)
- [3.7: Transformations of Random Variables - Statistics LibreTexts](https://stats.libretexts.org/Bookshelves/Probability_Theory/Probability_Mathematical_Statistics_and_Stochastic_Processes_(Siegrist)/03%3A_Distributions/3.07%3A_Transformations_of_Random_Variables)
- [calculus - How is the derivative of the CDF of a random variable $X$ its PDF? - Mathematics Stack Exchange](https://math.stackexchange.com/questions/248269/how-is-the-derivative-of-the-cdf-of-a-random-variable-x-its-pdf)
- [distributions - Derivation of change of variables of a probability density function? - Cross Validated (stackexchange.com)](https://stats.stackexchange.com/questions/239588/derivation-of-change-of-variables-of-a-probability-density-function)
- [ch3withfigs.pdf (uchicago.edu)](https://www.stat.uchicago.edu/~stigler/Stat244/ch3withfigs.pdf)