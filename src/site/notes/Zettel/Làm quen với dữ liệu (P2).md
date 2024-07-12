---
{"dg-publish":true,"permalink":"/zettel/lam-quen-voi-du-lieu-p2/"}
---


# III. Phép đo độ tương đồng và khác biệt của dữ liệu (TT)

## 8. Jaccard Similarity

- **Độ tương đồng Jaccard** (jaccard similarity) hay **hệ số Jaccard** (jaccard index) được dùng để đo sự tương đồng giữa các *tập hợp* với nhau.
- Xét hai tập hợp $A$ và $B$, khi đó độ tương đồng Jaccard là:
$$
\text{JSim}(A, B) = \dfrac{|A \cap B|}{|A \cup B|} = \dfrac{|A \cap B|}{|A| + |B| - |A \cap B|}
$$
- Có thể thấy:
	- $\text{JSim}(A, B) = 0$ nếu $|A \cap B| = 0$, nghĩa là $A$ với $B$ không có phần tử chung.
	- $\text{JSim}(A, B) = 1$ nếu $|A \cap B| = |A \cup B|$, nghĩa là $A$ với $B$ giống nhau.
	- Hiểu một nghĩa khác, độ tương đồng Jaccard chính là xác suất chọn được một phần tử mà nằm trong cả $A$ và $B$.
	- Giả sử $A = B = \emptyset$ thì $|A \cup B| = 0$, điều này không thể xảy ra được 🥲, thế nhưng theo định nghĩa tương đồng thì rõ ràng $A$ với $B$ giống nhau (đều là $\emptyset$) nên người ta quy ước rằng $\text{JSim}(\emptyset, \emptyset) = 1$.
- Ngoài ra ta có **khoảng cách Jaccard** là:
$$
\text{JDist}(A, B) = 1 - \text{JSim}(A, B) = \dfrac{|A \cup B| - |A \cap B|}{|A \cup B|}
$$
>[!note]
>Chứng minh Jaccard Distance là một metric:
>- [1611.02696.pdf (arxiv.org)](https://arxiv.org/pdf/1612.02696.pdf)
>- [book3.dvi (stanford.edu)](http://infolab.stanford.edu/~ullman/mmds/ch3.pdf)
>- [algorithms - How Jaccard similarity can be approximated with minhash similarity? - Mathematics Stack Exchange](https://math.stackexchange.com/questions/880581/how-jaccard-similarity-can-be-approximated-with-minhash-similarity?rq=1)
>- [elementary set theory - Jaccard dissimilarity and the triangle inequality - Mathematics Stack Exchange](https://math.stackexchange.com/questions/1287118/jaccard-dissimilarity-and-the-triangle-inequality)
>- [inequalities - Is the Jaccard distance a distance? - MathOverflow](https://mathoverflow.net/questions/18084/is-the-jaccard-distance-a-distance)

Giả sử ta có 2 đối tượng dữ liệu có thuộc tính binary $A$ và $B$, nếu xem $A$ và $B$ như các tập hợp, ta sẽ có các trường hợp:
- $A \cap B$, nghĩa là thuộc tính tại $A = 0$ và $B = 0$ (gọi là $q$) hoặc tại $A = 1$ và tại $B = 1$ (gọi là $t$). Do đó $|A \cap B| = q + t$.
- Còn lại bao gồm $A = 1$ và $B = 0$ (gọi là $r$) hoặc $A = 0$ và $B = 1$ (gọi là $s$).
- Do đó $|A \cup B| = r + s + q + t$.
- Khi đó độ tương đồng Jaccard giống với độ đo proximity ở [[Zettel/Làm quen với dữ liệu (P1)#III. Phép đo độ tương đồng và khác biệt của dữ liệu\|Làm quen với dữ liệu (P1)#III. Phép đo độ tương đồng và khác biệt của dữ liệu#3. Độ đo proximity cho thuộc tính binary]]:
$$
\begin{aligned}
\text{JSim}(A, B) &= \dfrac{|A \cap B|}{|A \cup B|} = \dfrac{q + t}{q + r + s + t} \\
\Rightarrow \hspace{5pt} \text{JDist}(A, B) &= 1 - \text{JSim}(A, B) = \dfrac{r + s}{q + r + s + t} = d(A, B)
\end{aligned}
$$

>[!summary]+ Tóm tắt
>- Dùng cho tập hợp
>- Nếu dùng cho biến binary thì tương tự như độ đo proximity cho thuộc tính binary ở [[Zettel/Làm quen với dữ liệu (P1)\|Làm quen với dữ liệu (P1)]]
## 9. Cosine Similarity

- Cho 2 đối tượng dữ liệu $X = (x_1, x_2, ..., x_p)$ và $Y = (y_1, y_2, ..., y_p)$ gồm $p$ thuộc tính. Khi đó **độ tương đồng cosine** giữa $X$ và $Y$ là:
$$
\text{sim}(X, Y) = \dfrac{X \cdot Y}{||X|| \hspace{3pt} ||Y||}
$$
- Trong đó:
	- $X \cdot Y$ là tích vô hướng của $X$ và $Y$.
	- $||X||$ là độ dài của $X$ hay là $L_2$-norm của $X$. Tương tự với $||Y||$.
- Nếu ta áp dụng lên *văn bản* thì $X$ và $Y$ là các *term-frequency* vector của hai văn bản mà ta muốn so sánh.
- Ngoài ra, ta có **khoảng cách cosine** là:
$$
d(X, Y) = 1 - \text{sim}(X, Y) 
$$
- Thế nhưng *khoảng cách cosine không phải là 1 metric*, xét ví dụ đơn giản sau đây: Giả sử ta có 2 vector $a = (1, 2)$ và $b = (2, 4)$ khi đó $\text{sim}(a, b) = 1$ nên $d(a, b) = 0$ nhưng khoảng cách giữa hai đối tượng khác nhau phải luôn $> 0$.

>[!summary]+ Tóm tắt
>- Dùng cho thuộc tính numeric
>- Nếu văn bản thì tìm term-frequency (hoặc tf-idf) sau đó tính cosine similarity
## 10. (Pearson) Correlation Coefficient

- Cho hai đối tượng dữ liệu gồm $p$ thuộc tính $X = (x_1, x_2, ..., x_p)$ và $Y = (y_1, y_2, ..., y_p)$ khi đó **hệ số tương quan pearson** giữa $X$ và $Y$ là:
$$
\text{Corr}(X, Y) = \dfrac{\sum_{i=1}^p(x_i - \overline{X})(y_i - \overline{Y})}{\sqrt{\sum_{i=1}^p(x_i - \overline{X})^2}\sqrt{\sum_{i=1}^p(y_i - \overline{Y})^2}} = \dfrac{\text{Cov}(X, Y)}{\sigma_X\sigma_Y}
$$
- Trong đó:
	- $\overline{X}$ là mean của $X$. Tương tự với $Y$.
	- $\sigma_X$ là độ lệch chuẩn của $X$. Tương tự với $Y$.
	- $\text{Cov}(X, Y)$ là hiệp phương sai của $X$ và $Y$.
- Thông thường, ta gọi vector $X'$ là vector **chuẩn hoá** của $X$ nếu $X' = X - \overline{X} = (x_1 - \overline{X}, ..., x_p - \overline{X})$. Thế nên ở công thức trên, $\text{Corr}(X, Y)$ chính là độ tương đồng cosine giữa các vector chuẩn hoá. 
- Đối với các giá trị pearson khác nhau thì ta có thể trực quan như sau:

![Pasted image 20240305195836.png](/img/user/Attachment/Pasted%20image%2020240305195836.png)

## 11. Distance cho các thuộc tính xếp hạng

Cho 2 rank vector $r_A = (a_1, ..., a_n)$ và $r_B = (b_1, ..., b_n)$, khi đó **khoảng cách spearman** là:
$$
d(A, B) = |a_1 - b_1| + |a_2 - b_2| + ... + |a_n - b_n|
$$
Ngoài ra, ta có **khoảng cách kendal's tau** là số cặp items có thứ tự khác nhau.

>[!example]+ Ví dụ
>- Giả sử ta hỏi 2 người $A$ và $B$ về hãng đồ ăn nào ngon hơn. Ta có $A = (McDonald, Jolibee, Lotte)$ và $B = (Lotte, McDonald, Jolibee)$ (xếp theo độ ngon tăng dần).
>- Đầu tiên, chọn một người làm vector chính, còn gọi là **pattern-vector**, giả sử chọn $A$. Do đó ta có rank vector $r_A = (1, 2, 3)$ với $1 = McDonald, 2 = Jolibee$ và $3 = Lotte$. Khi đó $r_B = (3, 1, 2)$.
>- Khoảng cách spearman là:
>$$
>d(A, B) = |1 - 3| + |2 - 1| + |3 - 2| = 6
>$$
>- Khoảng cách kendall = 3 do có 3 cặp items khác thứ tự bao gồm $(1, 3)$, $(2, 1)$ và $(3, 2)$.

>[!warning]
>Theo tài liệu từ nguồn [Ordinal Distance Tutorial (revoledu.com)](https://people.revoledu.com/kardi/tutorial/Similarity/OrdinalVariables.html) thì khoảng cách spearman và kendell tau khác công thức phía trên (tại sao lại khác thì mình chịu). Theo mình tham khảo từ nhiều nguồn (kể cả wiki) thì đa số khác công thức phía trên.
>- [Kendall tau distance - Wikipedia](https://en.wikipedia.org/wiki/Kendall_tau_distance)
>- [Spearman Distance Tutorial (revoledu.com)](https://people.revoledu.com/kardi/tutorial/Similarity/SpearmanDistance.html)
>- [Kendall Distance Tutorial (revoledu.com)](https://people.revoledu.com/kardi/tutorial/Similarity/KendallDistance.html)
>
>Trong đó:
>- Khoảng cách spearman:
>$$
>d(A, B) = ||A - B|| = \sum_{i=1}^n (a_i - b_i)^2
>$$
>- Khoảng cách kendall: Là số lần để swap để đưa một vector về thành pattern vector. Nói cách khác là số bước của "bubble sort" để sort vector ta cần xét về thành pattern vector.

## 12. Khoảng cách Hamming

- Dùng cho các vector bit, ví dụ như $X = (1, 0, 1, 0, 1, 0)$. **Khoảng cách Hamming** giữa hai vector bit $X$ và $Y$ là số vị trí mà tại đó bit của $X$ và $Y$ khác nhau.

>[!example]+ Ví dụ
>Cho 2 vector bit:
>- $X = (1, 0, 1, 1)$
>- $Y = (1, 1, 0, 1)$
>
>Khoảng cách Hamming = 2 (khác tại vị trí $1$ và $2$, vị trí bắt đầu là $0$)

- Có thể sử dụng khoảng cách Hamming lên thuộc tính phân loại (nominal, ordinal). Khi đó khoảng cách hamming giữa $X$ và $Y$ là số vị trí mà tại đó $X$ và $Y$ khác giá trị.

>[!example]+ Ví dụ
>Cho 2 đối tượng dữ liệu sau:
>- $X = (married, sad, rich)$
>- $Y = (single, happy, rich)$
>
>Khoảng cách Hamming = 2 (khác tại vị trí $0$ và $1$)

## 13. Khoảng cách Edit

- Được dùng để đo khoảng cách giữa hai chuỗi.
- Ta có thể hiểu khoảng cách edit giữa chuỗi $A$ và chuỗi $B$ là **số phép toán để biến chuỗi $A$ thành chuỗi $B$**. 
- Có nhiều công thức cho khoảng cách edit:
	- **Chuỗi con chung dài nhất** (Longest Common Subsequence): chỉ có thể dùng hai phép toán là *xoá* (delete) và *thêm* (insert) ký tự để biến chuỗi $A$ thành chuỗi $B$.
	- **Khoảng cách Levenshtein**: có thể xem như bản nâng cấp của LCS khi cho phép thêm *thay thế* (substitution) để thay ký tự này thành ký tự khác (trong slide thì phép thay thế gọi là *đột biến*).

>[!example]+ Ví dụ
>Xét 2 chuỗi $A = kitten$ và $B = sitting$. Khi đó:
>- Khoảng cách LCS = 5. Trong đó:
>	- Xoá "k" để $kitten \to itten$.
>	- Thêm "s" để $itten \to sitten$.
>	- Xoá "e" để $sitten \to sittn$.
>	- Thêm "i" để $sittn \to sittin$.
>	- Thêm "g" để $sittin \to sitting$.
>- Khoảng cách Levenshtein = 3. Trong đó:
>	- Thay "s" thành "k" để $kitten \to sitten$.
>	- Thay "e" thành "i" để $sitten \to sittin$.
>	- Thêm "g" để $sittin \to sitting$.

- Nếu ta xem một chuỗi là vector các ký tự thì vẫn có thể áp dụng khoảng cách Hamming. Khi đó khoảng cách Hamming là số vị trí mà ký tự của hai chuỗi khác nhau (chỉ áp dụng cho các chuỗi cùng độ dài).

## 14. Khoảng cách giữa hai phân phối

Xét hai phân phối $P$ và $Q$ trên không gian mẫu $\mathcal{X}$. Ta có thể dùng nhiều công thức để tìm khoảng cách giữa hai phân phối xác suất.

**Phân kỳ Kullback-Leibler** (Kullback-Leibler Divergence): Kí hiệu là $D_{KL}(P \mid \mid Q)$, trong đó:
- Nếu $P$ và $Q$ cùng là *phân phối rời rạc*:
$$
D_{KL}(P \mid \mid Q) = \sum_{x \in \mathcal{X}} P(x) \log \left( \dfrac{P(x)}{Q(x)} \right)
$$
- Nếu $P$ và $Q$ cùng là *phân phối liên tục*:
$$
D_{KL}(P \mid \mid Q) = \int_{-\infty}^{\infty} P(x) \log \left( \dfrac{P(x)}{Q(x)} \right) dx
$$

>[!note]+
>- Mặc dù là một công thức khoảng cách nhưng phân kỳ KL không là một metric
>- Bởi vì phân kỳ KL không thoả mãn tính đối xứng, tức là $d(x, y) \neq d(y, x)$ (https://stats.stackexchange.com/a/188904).

**Phân kỳ Jensen-Shannon**: Kí hiệu là $\text{JS}(P \mid \mid Q)$, trong đó:
$$
\text{JS}(P \mid \mid Q) = \dfrac{1}{2} D_{KL}(P \mid \mid M) + \dfrac{1}{2} D_{KL}(Q \mid \mid M)
$$
với $M = \frac{1}{2}(P + Q)$.

>[!note]
>Giống như bản nâng cấp của phân kỳ KL, phân kỳ JS thoả mãn tính đối xứng.

---

Phần trước: [[Zettel/Làm quen với dữ liệu (P1)\|Làm quen với dữ liệu (P1)]]
Phần sau: [[Zettel/Xử lý dữ liệu\|Xử lý dữ liệu]]

---
# References

- [book3.dvi (stanford.edu)](http://infolab.stanford.edu/~ullman/mmds/ch3.pdf)
- [Data Mining. Concepts and Techniques, 3rd Edition (The Morgan Kaufmann Series in Data Management Systems) (sabanciuniv.edu)](https://myweb.sabanciuniv.edu/rdehkharghani/files/2016/02/The-Morgan-Kaufmann-Series-in-Data-Management-Systems-Jiawei-Han-Micheline-Kamber-Jian-Pei-Data-Mining.-Concepts-and-Techniques-3rd-Edition-Morgan-Kaufmann-2011.pdf) (chương 2)