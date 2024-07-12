---
{"dg-publish":true,"permalink":"/zettel/lam-quen-voi-du-lieu-p1/"}
---

# I. Khái niệm dữ liệu

Cho tập dữ liệu khảo sát siêu anh hùng (gọi tắt là SH) dưới đây:

| Name          | Gender | Eye color | Race              | Hair | Height (cm) | Publisher         |
| ------------- | ------ | --------- | ----------------- | ---- | ----------- | ----------------- |
| A-Bomb        | Male   | yellow    | Human             | No   | 203         | Marvel Comics     |
| Abe Sapien    | Male   | blue      | Icthyo Sapien     | No   | 191         | Dark Horse Comics |
| Abin Sur      | Male   | blue      | Ungaran           | No   | 185         | DC Comics         |
| Abomination   | Male   | green     | Human / Radiation | No   | 203         | Marvel Comics     |
| Abraxas       | Male   | blue      | Cosmic Entity     | Yes  | 99          | Marvel Comics     |
| Absorbing Man | Male   | blue      | Human             | No   | 193         | Marvel Comics     |

>[!abstract]+ Định nghĩa
>Một **tập dữ liệu** (dataset) được tạo thành từ nhiều **đối tượng dữ liệu** (data object). Ví dụ trong tập dữ liệu bán hàng, các đối tượng dữ liệu có thể là khách hàng, các món hàng trong cửa hàng, ...

Dựa vào SH ta có thể thấy các đối tượng dữ liệu là những siêu anh hùng mà ta cần khảo sát ví dụ như *A-Bomb, Abe Sapien, ...*.

>[!note]
>Ta có thể gọi *đối tượng dữ liệu* là *mẫu* (sample), *dữ liệu điểm* (data point), *thể hiện* (instance).

>[!abstract]+ Định nghĩa
>Một **thuộc tính** (attribute) đại diện cho một đặc trưng của đối tượng dữ liệu mà ta muốn khảo sát.

Ví dụ trong SH, các thuộc tính của siêu anh hùng mà ta khảo sát là *gender, eye color, race, hair color, height, publisher*. 

>[!note]
>Trong machine learning, ta gọi thuộc tính là **đặc trưng** (feature), trong thống kê ta gọi là **biến** (variable) còn trong data engineering ta gọi là **chiều** (dimension).

Giá trị của một thuộc tính tại một đối tượng dữ liệu nào đó được gọi là một **quan sát** (observation).
## Phân loại thuộc tính

### 1. Định danh (nominal)

- Là những thuộc tính liên quan đến việc "phân loại" (categorize) đối tượng dữ liệu. 
- Thuộc tính định danh không thể dùng tính toán, đo đạc hay so sánh.

>[!example]+ Ví dụ
>Thuộc tính *Eye color* của SH, các giá trị của eye color là *yellow, blue, green, ...*
### 2. Nhị phân (binary)

- Là thuộc tính nominal nhưng thay vì có nhiều giá trị thì chỉ có thể có 2 giá trị (0 hoặc 1, đúng hoặc sai, nam hoặc nữ, ...)
- Thuộc tính nhị phân được gọi là **đối xứng** (symmetric) nếu cả hai giá trị đều ngang nhau. Ví dụ **nam** hoặc **nữ** thì gán 0 cho nam cũng được, nữ cũng được (và ngược lại) vì cả hai giá trị đều ngang nhau.
- Còn ngược lại là **không đối xứng** (asymmetric) nếu hai giá trị không ngang nhau. Ví dụ trong bài test HIV, kết quả dương tính thường hiếm xuất hiện hơn nên ta gán giá trị là 1, còn âm tính xuất hiện nhiều hơn nên ta gán giá trị là 0.
### 3. Thứ tự (ordinal)

- Là các thuộc tính mà giá trị của nó có tính thứ tự nào đó.
- Ngoài ra, các thuộc tính ordinal có thể so sánh với nhau được (vẫn không được dùng để tính toán).

>[!example]+ Ví dụ
>Thuộc tính **drink_size** (kích thước ly nước) sẽ có các giá trị là *small, medium, large*. Có thể thấy các giá trị có thứ tự tăng dần. Ngoài ra thuộc tính **grade** (điểm) có các giá trị $[0, 0.5, 1, 1.5, ..., 9.5, 10]$ cũng là thuộc tính thứ tự.
### 4. Số (numeric)

>[!note]
>Các thuộc **nominal, binary, ordinal** đều là thuộc tính **định tính** (qualitative). Giá trị của các thuộc tính này thường là chữ, nếu là số (ví dụ như $0$ là nam, $1$ là nữ) thì chỉ có nghĩa là cách viết gọn hơn để dễ máy tính dễ xử lý chứ không thể dùng tính toán.

- Còn gọi là thuộc tính **định lượng** (quantitative). Có thể dùng để đo đạc, tính toán và so sánh với nhau.
- Gồm 2 loại:
	- **Interval-Scaled** (theo khoảng)
	- **Ratio-Scaled** (theo tỉ lệ)
# II. Các phương pháp đánh giá dữ liệu

## 1. Theo xu hướng tập trung (central tendency)

### a. Trung bình (mean)

Xét một thuộc tính $X$ có giá trị là $x_1, x_2, ..., x_n$ với $n$ đối tượng dữ liệu. Khi đó giá trị **trung bình** của thuộc tính $X$ là:
$$
\overline{X} = \dfrac{\sum_{i=1}^n x_i}{n}
$$
>[!example]+ Ví dụ
>Suppose we have the following values for salary (in thousands of dollars), shown in increasing order: $30, 36, 47, 50, 52, 52, 56, 60, 63, 70, 70, 110$. Khi đó:
>$$
>\overline{X} = \dfrac{30 + 36 + 47 + 50 + 52 + 52 + 56 + 60 + 63 + 70 + 70 + 110}{12} = 58
>$$
### b. Trung vị (median)

>[!note] Giả sử dữ liệu được sắp tăng dần hoặc giảm dần (theo thứ tự).

- Là giá trị mà chia dữ liệu thành 2 phần, một phần thấp một phần cao (các giá trị phần thấp đều thấp hơn phần cao). 
- Nếu số lượng dữ liệu là lẻ thì median là giá trị **chính giữa**, nếu là chẵn thì median là trung bình của hai giá trị nằm giữa.

>[!example]+ Ví dụ
>Cho dữ liệu sau: $30, 36, 47, 50, 52, 52, 56, 60, 63, 70, 70, 110$. Do số lượng dữ liệu là chẵn nên lấy hai trung bình hai giá trị nằm giữa.
>$$
>\text{median} = \dfrac{52+56}{2} = 54
>$$

- Ví dụ nếu ta có rất nhiều dữ liệu thì khi đó tìm giá trị nằm giữa sẽ rất *expensive* do vậy ta sẽ không tìm trực tiếp mà **xấp xỉ** nó. Ta sẽ gộp dữ liệu lại thành từng khoảng, mỗi khoảng sẽ có tần số (số giá trị trong khoảng đó) rồi dùng công thức sau:
$$
\text{median} \approx L_1 + \dfrac{N/2 + (\sum \text{freq})_l}{\text{freq}_{\text{median}}} \times \text{width}
$$
- Trong đó:
	- $L_1$ là cận dưới của khoảng giá trị ở giữa (gọi là khoảng median).
	- $N$ là số lượng giá trị của cả dữ liệu.
	- $(\sum \text{freq})_l$ là tổng tần số của các khoảng nhỏ hơn khoảng median.
	- $\text{width}$ là độ rộng của khoảng median.
	- $\text{freq}_{\text{median}}$ là tần số của khoảng median.

>[!example]+ Ví dụ
>Giả sử ta có dữ liệu đánh giá IQ của 72.000 người, thay vì ghi ra là 72.000 dòng dữ liệu thì ta sẽ gộp chỉ số IQ theo các khoảng và số người (tần số) trong khoảng đó như sau:
> 
> | IQ      | Số người |
> | ------- | -------- |
> | 118-125 | 32.344   |
> | 126-133 | 13.433   |
> | 134-142 | 15.334   |
> | 143-149 | 8.234    |
> | 150-157 | 2.655    |
> 
> Khi đó:
> - $L_1 = 134$
> - $N = 72000$
> - $(\sum \text{freq})_l = 32344 + 13433$
> - $\text{width} = 142-134 = 8$
> - $\text{freq}_{\text{median}} = 15334$
> 
> Vậy:
> $$
> \text{median} \approx 134 + \dfrac{72000/2 + (32344+13433)}{15334} \times 8
> $$
### c. Mode

- (tiếng việt là số yếu vị) Là giá trị xuất hiện nhiều nhất trong dữ liệu (hay có tần số xuất hiện cao nhất).

>[!example]+ Ví dụ
>Ta có dữ liệu sau: $30, 36, 47, 50, 52, 52, 56, 60, 63, 70, 70$. Khi đó mode là $52$ và $70$ do $52$ với $70$ xuất hiện 2 lần (nhiều nhất).

- Dữ liệu mà có một mode thì được gọi là **unimodal**, đúng hai mode gọi là **bimodal**, nhiều hơn 2 là **multimodal**. Có thể nhìn hình dưới (điểm nhô lên cao là mode):

![Pasted image 20240229091103.png](/img/user/Attachment/Pasted%20image%2020240229091103.png)

- Nếu dữ liệu mà có mean, median với mode **đều nằm ở center** thì được gọi là **dữ liệu đối xứng**.
- Nếu $\text{mode} < \text{median}$ thì được gọi là **lệch dương** (positively skewed) (ngoài ra còn gọi là *lệch phải*).
- Nếu $\text{mode} > \text{median}$ thì được gọi là **lệch âm** (negatively skewed) (ngoài ra còn gọi là *lệch trái*).

![Pasted image 20240229092230.png](/img/user/Attachment/Pasted%20image%2020240229092230.png)
### d. Midrange
- Là giá trị trung bình giữa giá trị lớn nhất trong dữ liệu ($x_{\max}$) và nhỏ nhất trong dữ liệu ($x_{\min}$).
$$
\text{midrange} = \dfrac{x_{\max} + x_{\min}}{2} 
$$
## 2. Theo xu hướng phân tán

### a. Range

- Là hiệu giữa giá trị lớn nhất trong dữ liệu ($x_{\max}$) và nhỏ nhất trong dữ liệu ($x_{\min}$).
$$
\text{range} = x_{\max} - x_{\min}
$$
### b. Quartiles (tứ phân vị)

- **q-quantile** gồm $q-1$ điểm chia phân phối (dữ liệu) thành $q$ phần bằng nhau. Vậy *2-quantile* gồm 1 điểm chia dữ liệu thành 2 phần bằng nhau.
- *4-quantile* còn được gọi là **quartile** (tứ phân vị). 
	- **First quartile** (tứ phân vị thứ nhất), kí hiệu là $Q1$, là điểm chia dữ liệu thành một phần tư đầu của phân phối và 3/4 còn lại.
	- **Second quantile** (tứ phân vị thứ hai) hay median.
	- **Third quartile**, kí hiệu là $Q3$, là điểm chia dữ liệu thành ba phần tư đầu và 1/4 còn lại.
	- Khoảng cách từ $Q1$ đến $Q3$ còn được gọi là **Interquartile range**, kí hiệu là $IQR$, với công thức:
$$
IQR = Q3- Q1
$$
- *100-quantile* còn được gọi là **percentile**.

>[!example]+ Ví dụ
>Xét dữ liệu sau:
>$$
>30, 36, 47, 50, 52, 52, 56, 60, 63, 70, 70, 110
>$$
>Dữ liệu gồm 12 phần, khi chia làm 4 phần thì mỗi phần 3 phần tử. Do đó:
>- $Q1$ là trung bình giữa phần tử thứ 3 và 4: $(50 + 47) / 2 = 48.5$
>- $Q3$ là trung bình giữ phần tử thứ 9 và 10: $(70  + 63) / 2 = 66.5$
>- $IQR = Q3 - Q1 = 66.5 - 48.5 = 18$.
### c. Boxplot

![Pasted image 20240409001603.png](/img/user/Attachment/Pasted%20image%2020240409001603.png)
### d. Variance (phương sai) và Standard Deviation (độ lệch chuẩn)

- Xét một thuộc tính $X$ có giá trị là $x_1, x_2, ..., x_n$ với $n$ đối tượng dữ liệu. Khi đó **phương sai** của thuộc tính $X$ là:
$$
\sigma^2 = \dfrac{\sum_{i=1}^n (x_i - \overline{X})^2}{n}
$$
- Và **độ lệch chuẩn** của $X$ sẽ là:
$$
\sigma = \sqrt{\text{phương sai}} = \sqrt{\sigma^2}
$$
## 3. Covariance (hiệp phương sai)

- Xét hai thuộc tính $X$ và $Y$ có giá trị lần lượt là $(x_1, x_2, ..., x_n)$ và $(y_1, y_2, ..., y_n)$.
- Ta có **kì vọng** (expected value) của $X$ là (tương tự với $Y$):
$$
\text{E}[X] = \overline{X} 
$$
- Hiệp phương sai giữa $X$ và $Y$ được định nghĩa như sau:
$$
\text{Cov}(X, Y) = \text{E}[(X - \overline{X})(Y - \overline{Y})] = \dfrac{\sum_{i=1}^n(x_i - \overline{X})(y_i - \overline{Y})}{n}
$$

# III. Phép đo độ tương đồng và khác biệt của dữ liệu

## 1. Ma trận dữ liệu (data matrix) và ma trận khác biệt (Dissimilarity matrix)

- Giả sử ta có $n$ đối tượng dữ liệu $x_1, x_2, ..., x_n$ và mỗi đối tượng dữ liệu có $p$ thuộc tính (giá trị của thuộc tính thứ $j$ của đối tượng dữ liệu $i$ sẽ là $x_{ij}$). Khi đó ma trận dữ liệu sẽ là:
$$
\begin{bmatrix}
x_{11} & x_{12} & \dots & x_{1p} \\
x_{21} & x_{22} & \dots & x_{2p} \\
\vdots & \vdots & \ddots & \vdots \\
x_{n1} & x_{n2} & \dots & x_{np}
\end{bmatrix}
$$
- Mỗi dòng của ma trận dữ liệu tương ứng một đối tượng dữ liệu, mỗi cột tương ứng một thuộc tính.
- Còn **ma trận khác biệt** (hay còn gọi là *ma trận khoảng cách*) của $n$ đối tượng dữ liệu là:
$$
\begin{bmatrix}
0 & & & & & \\
d(2, 1) & 0 & & & & \\
d(3, 1) & d(3, 2) & 0 & & &\\
\vdots & \vdots & \vdots & & & \\
d(n, 1) & d(n, 2) & \dots & \dots & 0 
\end{bmatrix}
$$
>[!note]
>Vì ma trận phía trên là ma trận đối xứng qua đường chéo chính nên ta không cần ghi $d(j, i)$.

- Trong đó $d(i, j)$ là "khoảng cách giữa" hai đối tượng dữ liệu $i$ và $j$, dùng để đo sự "khác biệt" giữa hai đối tượng dữ liệu $i$ và $j$.
- Ngoài ra để đo sự "tương đồng" (similarity) giữa $i$ và $j$, người ta dùng:
$$
\text{sim}(i , j) = 1 - d(i, j)
$$
## 2. Độ đo proximity cho thuộc tính nominal

>[!note] 
>Chữ proximity có nghĩa là "sự gần nhau", "sự giống nhau".

$$
d(i, j) = \dfrac{p-m}{p}
$$
Trong đó:
- $m$ là số lượng thuộc tính nominal mà $i$ và $j$ có giá trị giống nhau.
- $p$ là tổng số lượng thuộc tính của đối tượng dữ liệu.

>[!example]+ Ví dụ
>Cho tập dữ liệu sau:
>
> |  Đối tượng |  Eye color  |
> | --- | --- |
> |  1  |  Green   |
> | 2 | Blue |
> | 3 | Yellow |
> | 4 | Green |
> 
> $$
> d(1, 4) = \dfrac{1 - 1}{1} = 0 \hspace{10pt} \text{và} \hspace{10pt} d(2, 4) = \dfrac{1 - 0}{1} = 1
> $$

## 3. Độ đo proximity cho thuộc tính binary

$$
d(i, j) = \dfrac{r + s}{q + r + s + t}
$$
Trong đó:
- $q$ là số lượng thuộc tính mà cả $i$ với $j$ đều có giá trị $1$.
- $r$ : $i = 1$ và $j = 0$.
- $s$ : $i = 0$ và $j = 1$.
- $t$ : cả $i$ và $j$ đều có giá trị là $0$.

>[!note]
>Nếu thuộc tính binary là không đối xứng thì người ta quy ước rằng $q$ quan trọng hơn $t$ (hai giá trị $1$ tốt hơn hai giá trị $0$) do đó:
>$$
>d(i, j) = \dfrac{r + s}{q + r + s}
>$$

## 4. Độ đo proximity cho thuộc tính numeric

Ta có thể dùng nhiều khoảng cách khác nhau để làm độ đo proximity cho thuộc tính numeric. Xét hai đối tượng dữ liệu gồm $p$ thuộc tính là $x = (x_1, x_2, ..., x_p)$ và $y = (y_1, y_2, ..., y_p)$, khi đó:

- **Khoảng cách Euclid** (euclidean distance):
$$
d(x, y) = \sqrt{(x_1 - y_1)^2 + (x_2 - y_2)^2 + ... + (x_p-y_p)^2} = \left[ \sum_{i=1}^p (x_i - y_i)^2 \right]^{1/2}
$$
- **Khoảng cách Manhattan** (mahattan distance): 
$$
d(x, y) = |x_1 - y_1| + |x_2 - y_2| + ... + |x_p - y_p| = \sum_{i=1}^p |x_i - y_i|
$$
- **Khoảng cách Minkowski**:
$$
d(x, y) = \sqrt[h]{|x_1-y_1|^h + |x_2-y_2|^h + ... + |x_p-y_p|^h} = \left[ \sum_{i=1}^p (x_i - y_i)^h \right]^{1/h}
$$
- **Khoảng cách Chebyshev**:
$$
d(x, y) = \max_i |x_i - y_i| = \max \{|x_1 - y_1|, |x_2 - y_2|, ..., |x_p -y_p|\}
$$

>[!note]
>- Khoảng cách Euclid còn được gọi là $L_2$-norm.
>- Khoảng cách Mahanttan là $L_1$-norm.
>- Khoảng cách Minkowski là $L_p$- norm
>- Khoảng cách Chebyshev là $L_{\infty}$-norm

- Nhìn theo khía cạnh hình học như hình dưới. Ta có thể thấy khi $L_p$-norm với $p \to \infty$ thì các cạnh của tứ giác màu tím càng *mở rộng* ra cho đến khi thành hình vuông cam.

![Pasted image 20240305165359.png](/img/user/Attachment/Pasted%20image%2020240305165359.png)

## 5. Metric

Một hàm khoảng cách $d(i, j)$ được gọi là **metric** nếu thoả mãn 4 điều kiện (còn gọi là 4 tiên đề) sau với mọi $i, j$.
- **Positivity**: Nếu $i \neq j$ thì $d(i, j) > 0$ (khoảng cách từ hai đối tượng khác nhau luôn dương)
- **Identity of indiscernibles**: $d(i, i) = 0$ (khoảng cách từ một đối tượng đến chính nó là $0$.
- **Symmetry**: $d(i, j) = d(j, i)$.
- **Triangle inequality**: $d(i, j) \leq d(i, k) + d(k, j)$ 
## 6. Độ đo proximity cho thuộc tính ordinal

- Giả sử $f$ là một trong những thuộc tính thứ tự trong các thuộc tính thứ tự của đối tượng dữ liệu. Để tính proximity thì ta làm các bước như sau:
	- Giá trị của $f$ tại đối tượng dữ liệu $x_i$ là $x_{if}$ và $f$ có $M_f$ giá trị (ví dụ $M_f = 3$ nếu $f$ là drink_size gồm small, medium, large). 
	- Sau đó số hoá các giá trị $f$ thành $(1, ..., M_f)$ (ví dụ $f$ là drink_size thì small = 1, medium = 2, large = 3).
	- Tiếp theo đó thay thế $x_{if}$ thành $r_{if} \in (1, ..., M_f)$ (ví dụ $x_{if} = \text{small}$ thì $r_{if} = 1$).
	- Tiếp theo tính trọng số:
$$
z_{if} = \dfrac{r_{if} - 1}{M_f - 1}
$$
- Cuối cùng là dùng $z_{if}$ đại diện cho giá trị của $x_i$ tại thuộc tính $f$. Vì $z_{if}$ là số nên ta cứ tính bằng cách dùng độ đo proximity cho thuộc tính numeric.

## 7. Độ đo proximity cho nhiều thuộc tính khác nhau

Giả sử một tập dữ liệu có $p$ thuộc tính khác nhau. Khi đó:

$$
d(i, j) = \dfrac{\sum_{f=1}^p \delta^{(f)}_{ij} d^{(f)}_{ij}}{\sum_{f=1}^p \delta^{(f)}_{ij}} 
$$
Trong đó:
- $\delta_{ij}^{(f)} = 0$ nếu:
	- $x_{if}$ hoặc $x_{jf}$ bị thiếu (nghĩa là thuộc tính $f$ không có tại đối tượng dữ liệu $x_i$ hoặc $x_j$).
	- $x_{if} = x_{jf} = 0$ và $f$ là thuộc tính binary không đối xứng.
- Ngược lại $\delta_{ij}^{(f)} = 1$.
- Với mỗi $f$, ta có cách tính $d_{ij}^{(f)}$ khác nhau:
	- **Nếu $f$ là numeric**: $d_{ij}^{(f)} = \dfrac{|x_{if} - x_{jf}|}{\max_f - \min_f}$ trong đó $\max_f$ và $\min_f$ là giá trị lớn nhất và nhỏ nhất của thuộc tính $f$.
	- **Nếu $f$ là nominal hoặc binary**: $d_{ij}^{(f)} = 0$ nếu $x_{if} = x_{jf} = 0$; ngược lại $d_{ij}^{(f)} = 1$.
	- **Nếu $f$ là ordinal**: tính $z_{if}$ như cách tính proximity cho ordinal sau đó xem $z_{if}$ như numeric và áp dụng như phía trên.

---

Phần sau: [[Zettel/Làm quen với dữ liệu (P2)\|Làm quen với dữ liệu (P2)]]

---
# References

- [Data Mining. Concepts and Techniques, 3rd Edition (The Morgan Kaufmann Series in Data Management Systems) (sabanciuniv.edu)](https://myweb.sabanciuniv.edu/rdehkharghani/files/2016/02/The-Morgan-Kaufmann-Series-in-Data-Management-Systems-Jiawei-Han-Micheline-Kamber-Jian-Pei-Data-Mining.-Concepts-and-Techniques-3rd-Edition-Morgan-Kaufmann-2011.pdf) (chương 2)
- Note trên lớp của bạn [Phạm Thái Huy](https://drive.google.com/file/d/1CYyAvVTZRllo2Js0npYOVF1x5YzQDLTd/view?usp=sharing)