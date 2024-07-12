---
{"dg-publish":true,"permalink":"/zettel/introduction-prob/","noteIcon":"📝","created":"2024-06-30T19:11:48.451+07:00","updated":"2024-07-12T08:29:04.957+07:00"}
---


Một hôm LN định mua bánh, đến chợ thì có hai bà bán bánh là bà Hoa và bà Lan. Bà Lan hiện đang còn 2 cái bánh mì và 6 cái bánh xèo, bà Hoa hiện đang còn 3 cái bánh mì và 1 cái bánh xèo. 

Như mọi hôm, LN thích ăn bánh của bà Hoa làm hơn, do đó ở 10 lần đi mua trước, hết 6 lần LN đã chọn bà Hoa. Giả sử, việc LN chọn bánh nào cũng như nhau (không thích bánh nào hơn bánh nào, đói thì ăn).

>[!note]+
>- Ta gọi tập hợp các khả năng có thể xảy ra của một phép thử (ở ví dụ trên là đi mua bánh) là **không gian mẫu** và kí hiệu là $\Omega$. Một biến cố $A$ là một tập con của $\Omega$. Ta nói biến cố $A$ xảy ra nếu một kết quả trong $A$ xảy ra
>- Ví dụ, xét việc tung hai đồng xu, ta có $A = \{HT, HH\}$, nếu ta tung đồng xu thứ nhất được mặt ngửa ($H$) và đồng xu thứ 2 được mặt xấp ($T$) thì ta nói $A$ xảy ra.
>- Xác suất của một biến cố $A$ được kí hiệu là $p(A)$ và có giá trị từ $[0, 1]$. Ta có thể định nghĩa xác suất của $A$ là *số lần thử mà $A$ xảy ra chia tổng số lần thử*.

>[!note]+
>- Một biến ngẫu nhiên $X$ hiểu đơn giản là một cách để đưa các biến cố sang các số thực (hay là một ánh xạ từ $\Omega$ sang $\mathbb{R}$). 
>- Ngoài ra, ta nói $X$ là biến ngẫu nhiên *rời rạc* nếu tập xác định của $X$ là tập hữu hạn (như ví dụ trên $\{0, 1, \dots, 50\}$) hay vô hạn đếm được (ví dụ $\{0, 1, \dots\}$). Ngược lại, ta gọi $X$ là biến ngẫu nhiên *liên tục*.

>[!example]+
>Giả sử mình là cửa hàng gà rán, muốn lấy ý kiến 50 người về món gà rán đó ngon hay không, mình đặt $1$ là ngon và $0$ là dở. Nếu vậy, mình sẽ có $| \Omega| = 2^{50}$, mỗi lần khảo sát mình sẽ có một chuỗi $01$ với độ dài $50$ và như thế thì quá to 🥲. Nếu mình đặt $X$ là một biến ngẫu nhiên, $X$ đại diện cho số người trong $50$ người cho rằng ngon, tức là số số $1$ trong chuỗi $01$ độ dài $50$, vậy các giá trị có thể của $X$ là $\{0, 1, \dots, 50 \}$. Bằng việc sử dụng biến ngẫu nhiên, mình đã giảm số khả năng từ $2^{50}$ xuống còn $51$ (ví dụ được mình ăn cắp từ [Casella] trang 54).

>[!note]+
>Trong ví dụ phía dưới, mình lấy $A$ có tập xác định là $\{h, l\}$, vậy nó đâu phải số thực 🤨, thế nhưng nếu xem $h = 1$ và $l = 0$ thì nó cũng là số thực thôi, việc đặt chữ cho dễ hiểu hơn.
**
Nếu đặt $A$ là biến ngẫu nhiên cho bà bán bánh, thì $A = h$ tức là bà Hoa, $A = l$ tức là bà Lan. Đặt $B$ là biến ngẫu nhiên cho cái bánh, $B = x$ tức là bánh xèo, còn $B = m$ tức là bánh mì. Lúc này ta có xác suất:
$$
\begin{aligned}
p(A = h) &= \frac{6}{10} \hspace{5pt} \text{(do $6$ trên $10$ lần bà Hoa được mua)} \\
p(A = l) &= 1 - \frac{6}{10} = \frac{4}{10}
\end{aligned}
$$

>[!note]+
>Đặt $A_1, ..., A_n$ là $n$ biến cố, nếu:
>- *Mutually exclusive* (loại trừ lẫn nhau): tức là với mỗi $A_i$ và $A_j$, nếu $A_i$ xảy ra thì $A_j$ không xảy ra và ngược lại ($A_i \cap A_j = \emptyset$).
>- $A_1 \cup A_2 \cup \dots \cup A_n = \Omega$.
>
>thì:
>$$
p(A_{1}) + \dots + p(A_{n}) = 1
>$$

>[!example]+
>Ở ví dụ trên, ta có thể thấy $A = h$ và $A = l$ là hai biến cố loại trừ lẫn nhau (nếu đã mua bà Hoa thì không mua bà Lan, giả sử thôi nha) và giao với nhau bằng không gian mẫu, do đó:
>$$
>p(A = h) + p(A = l) = 1
>$$

Giả sử vào hôm nay, LN đi mua về một cái bánh mì, mình hỏi LN đã mua từ ai, LN không nói, thế nên mình đã đặt ra câu hỏi "biết rằng LN đã mua cái bánh mì, vậy xác suất LN mua cái bánh đó từ bà Hoa là bao nhiêu". Trước khi trả lời câu hỏi này, cùng mình đi sâu hơn một chút về xác suất.

Xét hai biến ngẫu nhiên $X$ và $Y$, trong đó $X$ có thể nhận các giá trị $\{x_1, x_2, \dots, x_M\}$ và $Y$ có thể nhận các giá trị $\{y_{1}, \dots, y_{L}\}$. Tiếp theo ta thực hiện phép thử mà ta sẽ lấy ngẫu nhiên giá trị $X$ và $Y$. Ta thực hiện phép thử ấy trong $N$ lần, trong đó số lần thử mà $X = x_i$ và $Y = y_j$ xảy ra là $n_{ij}$. 

Ta gọi xác suất mà $X = x_i$ và $Y = y_j$ cùng xảy ra là **xác suất đồng thời** của $X = x_i$ và $Y = y_j$, kí hiệu là $p(X = x_i, Y = y_j)$.  Như đã nói ở trên, $p(X = x_i, Y = y_j)$ chính là số lần thử mà $X = x_i$ và $Y = y_j$ xảy ra ($n_{ij}$) chia cho tổng số lần thử ($N$).
$$
p(X = x_{i}, Y = y_{j}) = \frac{n_{ij}}{N}
$$
Ta gọi ${} p(X = x_{i}, Y = y_{i})$ là *xác suất đồng thời* (joint probability) của ${} X = x_{i}$ và $Y = y_{i}$. Ta có thể tưởng tượng $X$ và $Y$ tạo thành một bảng, trong đó $X$ tạo thành các cột, mỗi cột tương ứng với $x_1, \dots, x_M$ còn $Y$ tạo thành các dòng, mỗi dòng tương ứng với $y_1, ..., y_L$. Một ô ở vị trí $i, j$ của bảng sẽ tương ứng với $X = x_i$ và $Y = y_j$. 

Nếu ta xét trong $N$ lần thử, thì giả sử ta có $N$ viên bi, mỗi viên ứng với một lần thử. Ở mỗi lần thử, nếu kết quả xảy ra là $X = x_i$ và $Y = y_j$ thì ta bỏ viên bi vào ô $i, j$. Sau khi xong $N$ lần thử, ta chỉ cần đếm lại số viên bi ở ô $i, j$ để tìm ra số lần mà $X = x_i$ và $Y = y_j$ xảy ra, tức là $n_{ij}$ = số viên bi. Vậy ta có thể xem mỗi ô $i, j$ là số lần thử mà $X = x_i$ và $Y = y_j$ xảy ra. 

| **Biến ngẫu nhiên** | **$x_1$** | **$\dots$** | **$x_M$** |          |
| ------------------- | --------- | ----------- | --------- | -------- |
| **$y_1$**           | $n_{11}$  | $\dots$     | $n_{M1}$  | $r_1$    |
| **$\vdots$**        | $\vdots$  | $\ddots$    | $\vdots$  | $\vdots$ |
| **$y_L$**           | $n_{1L}$  | $\dots$     | $n_{ML}$  | $r_L$    |
|                     | $c_1$     | $\dots$     | $c_M$     |          |

>[!note]+
>Ta đọc dấu $,$ trong công thức xác suất đồng thời là "và", tức là $p(X = x_i, Y = Y_j)$ sẽ đọc là "xác suất của $X = x_i$ và $Y = y_j$". Do là phép "và" nên có tính đối xứng, nghĩa là $p(X =x_i, Y = y_j) = p(Y = y_j, X = x_i)$. Hiểu một cách khác thì ô $i, j$ hay ô $j, i$ đều như nhau nên số viên bi tại đó là bằng nhau.

Dựa vào ý tưởng trên, nếu ta xét số lần thử mà $X = x_i$ xuất hiện, không kể đến $Y$, tức là ta sẽ đếm số viên bi ở cả cột $x_i$, gọi số viên bi (hoặc số lần thử) đó là $c_i$, vậy $c_i = \sum_{j=1}^L n_{ij}$. Tương tự, nếu ta xét số lần thử mà $Y = y_j$ xuất hiện, không kể đến $X$, gọi là $r_j$ thì ta sẽ đếm số viên bi ở cả dòng $y_j$, vậy $r_j = \sum_{i=1}^{M} n_{ij}$.

Giờ nếu ta xét $p(X = x_i)$, tức là ta chỉ quan tâm đến xác suất $X = x_i$ xảy ra mà không quan tâm đến $Y$ xảy ra như nào.  Vậy:
$$
p(X = x_{i}) = \frac{c_{i}}{N} = \frac{\sum_{j=1}^{L} n_{ij}}{N}
$$
Từ công thức phía trên ta có thể viết lại như sau:
$$
p(X = x_{i}) = \sum_{j=1}^L \frac{n_{ij}}{N} = \sum_{j=1}^L p(X = x_{i}, Y = y_{j})
$$
ta gọi công thức mới viết lại là **sum rule** (hay *quy tắc cộng*) của xác suất. Tương tự, ta cũng có thể viết như sau:
$$
p(Y = y_{j}) = \sum_{i=1}^M p(X = x_{i}, Y = y_{j})
$$
ngoài ra, giá trị $p(X = x_i)$ còn được gọi là **xác suất biên** (*marginal probability*), có thể hiểu là xác suất mà ta có được bằng cộng lại các biến khác (đối với $p(X = x_i)$ thì các biến khác là $Y$).

Giờ nếu mình chỉ quan tâm đến những viên bi nằm ở cột $x_i$, và mình đếm xem trong số viên bi đó có bao nhiêu viên thuộc hàng $y_j$. Tức là mình đang muốn xem xác suất của $Y = y_j$ (mình đang đếm xem bao nhiêu viên thuộc hàng $y_j$) là bao nhiêu biết rằng $X = x_i$ đã xảy ra (mình biết được bao nhiêu viên bi ở cột $x_i$ và mình chỉ đếm dựa trên số viên bi ở cột $x_i$ thôi). 

Mình gọi xác suất mình đang tìm kiếm là **xác suất có điều kiện của $Y = y_j$ biết rằng $X = x_i$** và viết là $P(Y = y_j \mid X = X_i)$.
$$
p(Y = y_{j} \mid X = x_{i}) = \frac{n_{ij}}{c_{i}}
$$
>[!note]+
>Xác suất $p(Y = y_j \mid X = x_i)$ chỉ có nghĩa khi $p(X = x_i) = c_i \neq 0$. Nếu $p(X = x_i) = 0$ thì biến cố $X = x_i$ không chắc chắn xảy ra (xác suất là $0$ khác với không thể xảy ra [Almost surely - Wikipedia](https://en.wikipedia.org/wiki/Almost_surely)).

Từ công thức trên, ta có:
$$
\begin{aligned}
p(Y = y_{j} \mid X = x_{i}) &= \frac{n_{ij}}{c_{i}} \\
&= \frac{n_{ij}}{N} \frac{N}{c_{i}} \\
&= \frac{p(Y = y_{j}, X=x_{i})}{p(X = x_{i})}
\end{aligned}
$$
Biến đổi một chút, ta lại có:
$$
p(X = x_{i}, Y = y_{j}) = p(Y = y_{j} \mid X = x_{i}) p(X = x_{i})
$$
ta gọi công thức biến đổi phía trên là **product rule** (*quy tắc nhân*) của xác suất.

>[!info]+ Cách kí hiệu
>- Có thể thấy phía trên việc kí hiệu $p(X = x_i)$ nghĩa là xác suất của $X = x_i$. Mình có thể viết $p(x_i)$, thì ta có thể hiểu xác suất của $X = x_i$ (nếu ngữ cảnh rõ ràng). Hoặc mình viết $p(X)$ tức là phân phối của $X$ (là xác suất của $X = x$ với $x$ là giá trị bất kỳ hay là biến). Giả sử mình có $p(X = 1) = 2, p(X = 2) = 3, \dots$, vậy mình có thể viết $p(X) = x + 1$.
>- Vậy nếu mình viết $p(X, Y)$ thì ta sẽ hiểu là phân phối đồng thời của $X$ và $Y$ hay $p(X \mid Y)$ thì ta sẽ hiểu là phân phối có điều kiện của $X$ biết rằng $Y$.

Vậy tổng hợp lại, nãy giờ chúng ta biết được:

>[!done]+ **Sum rule**
>$$
p(X) = \sum_{Y} p(X, Y)
>$$
>Note: $\sum_{Y}$ có nghĩa là tổng các giá trị mà $Y$ có thể có, ví dụ các giá trị $Y$ có thể nhận là $\{y_1, \dots, y_n\}$ thì
>$$
>\sum_{Y} p(X, Y) = \sum_{i=1}^n p(X, Y = y_{i})
>$$

>[!done]+ **Product rule**
>$$
>p(X, Y) = p(Y \mid X) p(X) = p(X \mid Y)p(Y)
>$$

Từ product rule, mình có thể viết như sau:
$$
\begin{aligned}
p(Y \mid X) &= \frac{p(X, Y)}{p(X)} \\
&= \frac{p(X \mid Y)p(Y)}{p(X)}
\end{aligned}
$$
ta gọi công thức trên (từ dấu $=$ thứ ba) là **định lý Bayes** (*Bayes' Theorem*). Đây là định lý cực kỳ quan trọng nên chúng ta đưa luôn vào đầu nhé 🥲.

Tiếp tục dùng sum rule cho mẫu của định lý Bayes, ta có:
$$
p(Y \mid X) = \frac{p(X \mid Y)P(Y)}{\sum_{Y} p(X, Y)} =\frac{p(X \mid Y)p(Y)}{\sum_{Y} p(X \mid Y) p(Y)}
$$
ta có thể thấy phần mẫu của định lý Bayes giúp ta chắc chắn rằng $\sum_{Y} p(Y \mid X) = 1$, điều này nên có bởi vì trong các giá trị mà $Y$ nhận được thì $Y = y_i$ và $Y = y_j$ không cùng xảy ra (mutually exclusive) và các giá trị $Y = y_i$ hợp lại tạo thành các giá trị mà $Y$ có thể có (không gian mẫu), do đó xác suất của $\sum_{Y} p(Y \mid X) = 1$.

Giờ quay về ví dụ mua bánh xèo nhé. Như ta đã biết:
$$
\begin{aligned}
p(A = h) &= \frac{6}{10} \\
p(A = l) &= \frac{4}{10}
\end{aligned}
$$
Tiếp theo, nếu ta đã chọn mua bà Lan, vậy xác suất ta chọn được cái bánh xèo chính là số bánh xèo bà Lan có chia cho tổng số bánh:
$$
p(B = x \mid A = l) = \frac{6}{8} = \frac{3}{4}
$$
Tương tự với các xác suất còn lại:
$$
\begin{aligned}
p(B = m \mid A = l) &= \frac{2}{8} = \frac{1}{4}\\
p(B = x \mid A = h) &= \frac{1}{4} \\
p(B = m \mid A = h) &= \frac{3}{4}
\end{aligned}
$$
Để tìm được xác suất LN sẽ mua bánh mì (không quan tâm mua từ bà bán bánh nào), ta sẽ dùng sum rule và product rule:
$$
\begin{aligned}
p(B = m) &= p(B = m, A = l) + p(B = m, A = h) \\
&= p(B = m \mid A = l)p(A = l) + p(B = m \mid A = h)p(A = h) \\
&= \frac{1}{4} \frac{4}{10} + \frac{3}{4} \frac{6}{10} = \frac{11}{20}
\end{aligned}
$$
Tương tự mình cũng có xác suất LN sẽ mua bánh xèo (không quan tâm bà bán):
$$
p(B = x) = 1 - p(B = m) = \frac{9}{20}
$$
Bây giờ đến lúc trả lời câu hỏi mình đã đặt ra, xác suất để LN mua cái bánh xèo đó từ bà Hoa là bao nhiêu ? Tức là mình đã biết trước LN mua cái bánh xèo ($B = x$) và tìm xác suất mua từ bà Hoa dựa trên đó ($A = h$) $\implies$ Mình cần tìm $p(A = h \mid B = x)$, do đó áp dụng định lý Bayes:
$$
\begin{aligned}
p(A = h \mid B = x) &= \frac{p(B = x \mid A = h)p(A = h)}{p(B = x)} \\
&= \dfrac{1 / 4 \times 6 / 10 }{9 / 20} = \frac{1}{3}
\end{aligned}
$$
Tương tự, mình cũng có xác suất LN mua cái bánh xèo đó từ bà Lan:
$$
p(A = l \mid B = x) = 1 - \frac{1}{3} = \frac{2}{3}
$$
Vậy có thể thấy, mặc dù yêu thích bà Hoa hơn, nhưng khả năng LN chọn mua cái bánh xèo từ bà Lan lại cao hơn.

Trong công thức Bayes của $p(X \mid Y)$, ta gọi $p(X)$ là **xác suất tiên nghiệm** (prior probability), $p(Y \mid X)$ là **likelihood**, $p(Y)$ được gọi là **xác suất biên** (marginal probability), $Y$ được gọi là **bằng chứng** (evidence), $X$ được gọi là **giả thiết** (hypothesis) và $p(X \mid Y)$ là **xác suất hậu nghiệm** (posterior probability). 

>[!note]
>Trong bài toán trên, ta có thể formal nó thành $p(A \mid B)$, trong đó $p(A)$ sẽ là xác suất tiên nghiệm. Trước khi biết LN mua cái bánh nào, thì khi được hỏi LN sẽ mua bánh từ bà bán bánh nào, thông tin duy nhất ta biết là LN thích bà bán bánh nào hơn, tức là chỉ biết được $p(A$). Thế nhưng sau khi ta biết được LN đã mua cái bánh nào, thì khi được hỏi LN sẽ mua bánh từ bà bán bánh nào, ta có thể dùng công thức Bayes để tính ra, do đó xác suất $p(A \mid B)$ được gọi là xác suất hậu nghiệm, bởi vì ta có được xác suất này sau khi *quan sát* được LN đã mua cái bánh nào (bằng chứng $B$).  Có thể thấy, bà Lan sẽ có số bánh xèo nhiều hơn do đó việc quan sát rằng LN đã chọn mua bánh xèo sẽ khiến quyết định nghĩ rằng LN mua từ bà Lan đã cao hơn.

>[!success]+ Độc lập
>Nếu một xác suất đồng thời $p(X, Y)$ có thể đưa về thành tích của hai xác suất biên $p(X)$ và $p(Y)$, nghĩa là:
>$$
>p(X, Y) = p(X)p(Y)
>$$
>thì ta nói $X$ với $Y$ độc lập với nhau.

Nếu $X$ với $Y$ độc lập với nhau thì:
$$
p(X \mid Y) = \frac{p(X, Y)}{p(Y)} = p(X)
$$
tức là xác suất của $X$ cho dù biết $Y$ hay không thì cũng không bị ảnh hưởng. Suy ngược lại, nếu $p(X \mid Y) = p(X)$ (tương tự $p(Y \mid X) = p(Y)$) thì ta nói $X$ và $Y$ độc lập với nhau.

---

>[!danger]+
>Việc định nghĩa xác suất, biến cố hay kể cả không gian mẫu như trên có thể xảy ra nhiều bất cập, nếu muốn chặt chẽ và formal hơn, các bạn có thể tìm hiểu về *measure theory* và một trong những cuốn sách mình thích về cái này là [Amazon.com: Probability and Measure Theory: 9780120652020: Robert B. Ash, Catherine A. Doléans-Dade: Books](https://www.amazon.com/Probability-Measure-Theory-Robert-Ash/dp/0120652021).

---

Phần trước: [[Zettel/Polynomial Curve Fitting\|Polynomial Curve Fitting]]
Phần sau: [[Zettel/Probability Densities\|Probability Densities]]

---
# References

- [Casella]  [Statistical Inference (wordpress.com)](https://mybiostats.files.wordpress.com/2015/03/casella-berger.pdf)
- [Bishop] Pattern Recognition and Machine Learning - Bishop (chapter 1.2)
- [Bayesian inference - Wikipedia](https://en.wikipedia.org/wiki/Bayesian_inference)