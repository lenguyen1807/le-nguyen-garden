---
{"dg-publish":true,"permalink":"/zettel/bayesian-probabilities/","noteIcon":"📝","created":"2024-06-30T19:11:48.440+07:00","updated":"2024-07-12T08:26:56.139+07:00"}
---


Định lý Bayes cũng có thể áp dụng trong Machine Leanring như sau. Giả sử rằng ta có tập dữ liệu $\mathcal{D}$ và một model có bộ tham số là $\mathbf{w}$. Mục đích của ta là với tập dữ liệu $\mathcal{D}$ như này, bộ tham số $\mathbf{w}$ của ta như nào mới là tốt, tức là tìm xác suất $p(\mathbf{w} \mid \mathcal{D})$.

Giả sử ta đã chọn được một mô hình với bộ tham số $\mathbf{w}$. Trước khi có tập dữ liệu $\mathcal{D}$, ta ngầm giả định rằng $\mathbf{w}$ có phân phối là $p(\mathbf{w})$. Sử dụng định lý Bayes, ta có:
$$
p(\mathbf{w} \mid \mathcal{D}) = \frac{p(\mathcal{D} \mid \mathbf{w})p(\mathbf{w})}{p(\mathcal{D})}
$$
Phân phối $p(\mathcal{D} \mid \mathbf{w})$ ở bên phải của định lý Bayes là một hàm phụ thuộc vào $\mathcal{D}$, thế nhưng nếu ta xem phân phối ấy là một hàm phụ thuộc vào $\mathbf{w}$, thì khi đó ta gọi $p(\mathcal{D} \mid \mathbf{w})$ là **hàm likelihood** (likelihood function).

>[!note]+
>Thay vì viết $p(\mathcal{D} \mid \mathbf{w})$ để dễ bị nhầm lẫn giữa phân phối xác suất và hàm likelihood, ta sẽ kí hiệu:
>$$
\mathcal{L}(\mathbf{w} \mid \mathcal{D}) = p(\mathcal{D} \mid \mathbf{w})
>$$
>trong đó $\mathcal{L}(\mathbf{w} \mid \mathcal{D})$ là hàm likelihood có biến là $\mathbf{w}$ còn $p(\mathcal{D} \mid \mathbf{w})$ là phân phối có biến là $\mathcal{D}$.

Dựa vào định nghĩa của likelihood, ta có thể viết lại định lý Bayes như sau:
$$
\text{posterior} \propto \text{likelihood} \times \text{prior}
$$
>[!note]+
>Kí hiệu $\propto$ nghĩa là tỉ lệ. Ví dụ, chiều cao ($h$) $= 1.2 \times$ cân nặng ($w$), lúc này ta nói chiều cao tỉ lệ với cân nặng hay $h \propto w$. Ở định lý Bayes, nếu ta xem $1 / p(\mathcal{D})$ là một hằng số (mà nó là một hằng số thật, bởi vì $\mathcal{D}$ không đổi rồi) thì $p(\mathbf{w} \mid \mathcal{D}) \propto \mathcal{L}(\mathbf{w} \mid \mathcal{D})p(\mathbf{w})$.

trong đó $\text{likelihood}, \text{posterior}$ và $\text{prior}$ đều là các hàm phụ thuộc vào $\mathbf{w}$. Còn giá trị $p(\mathcal{D})$ dưới mẫu là một hằng số, dùng để đảm bảo rằng phân phối hậu nghiệm ở bên phải định lý Bayes đúng là một phân phối (mật độ xác suất).

>[!note]+
>Áp dụng sum rule và product rule ([[Zettel/Probability Densities\|Probability Densities]]) cho biến tục, ta có:
>$$
>p(\mathcal{D}) = \int p(\mathcal{D} \mid \mathbf{w}) p(\mathbf{w}) d\mathbf{w}
>$$
>Vậy:
>$$
\begin{aligned}
\int_{-\infty}^{\infty} p(\mathbf{w} \mid \mathcal{D}) d\mathbf{w} &= \int_{-\infty}^{\infty} \frac{p(\mathcal{D} \mid \mathbf{w})p(\mathbf{w})}{p(\mathcal{D})} d\mathbf{w} \\
&= \frac{\int p(\mathcal{D}\mid \mathbf{w})p(\mathbf{w}) d\mathbf{w}}{\int p(\mathcal{D}\mid \mathbf{w})p(\mathbf{w}) d\mathbf{w}} = 1
\end{aligned}
>$$
>Còn việc $p(\mathbf{w} \mid \mathcal{D}) \geq 0$ mình nghĩ khá là dễ thấy rồi.

Vậy sinh ra cái Bayes này làm gì, mục đích của chúng ta đó là cố gắng tìm bộ tham số $\mathbf{w}$ sao cho $p(\mathbf{w} \mid \mathcal{D})$ là tốt nhất, kiểu như ta đã biết trước tập dữ liệu $\mathcal{D}$ (tức là ta đã biết trước kết quả rồi), ta cần tìm mô hình (tham số $\mathbf{w}$) phù hợp với $\mathcal{D}$ nhất (tức là ta đi tìm nguyên nhân cho ra kết quả và nguyên nhân đó phải là phù hợp với kết quả nhất, vậy là tìm xác suất $p(\mathbf{w}\mid \mathcal{D})$ lớn nhất) (mình copy cách giải thích này từ [VHT]).

>[!note]+
>Ngoài cách giải thích trên, ta hãy xem xác suất như *mức độ của niềm tin* (degree of belief) tức là xác suất càng cao, ta càng tin là nó sẽ tốt (hoặc sẽ xảy ra). Trước khi có data quan sát được dữ liệu $\mathcal{D}$, ta tin rằng $\mathbf{w}$ sẽ tốt (là một mô hình phù hợp với $\mathcal{D}$) ở một mức độ nào đó, tức là $p(\mathbf{w})$, sau khi quan sát được dữ liệu ${} \mathcal{D}$ rồi, niềm tin về độ phù hợp của $\mathbf{w}$ với ${} \mathcal{D} {}$ sẽ thay đổi và có giá trị là $p(\mathbf{w} \mid \mathcal{D})$.

Đối với frequentist thì ta sẽ dùng phương pháp **maximum likelihood** (MLE) để tìm giá trị $p(\mathcal{D} \mid \mathbf{w})$ lớn nhất từ đó tìm được $p(\mathbf{w} \mid \mathcal{D})$ lớn nhất (frequentist giả sử rằng $p(\mathbf{w})$ và $p(\mathcal{D})$ là các hằng số, ở góc nhìn của frequentist, ta sẽ xem $\mathbf{w}$ như là một giá trị mà ta ước lượng được, do đó $p(\mathbf{w})$ là một hằng số) Ta sẽ tìm hiểu phương pháp này ở phần [[Zettel/Gaussian Distribution\|Gaussian Distribution]].

Còn đối với bayesian, ta có phương pháp gọi là **maximum a posteriori estimation** (MAP). Bayesian cho rằng $\mathbf{w}$ là một biến ngẫu nhiên chứ không phải một giá trị, do đó $p(\mathbf{w})$ là một phân phối. Vậy để tìm được $p(\mathbf{w} \mid \mathcal{D})$ lớn nhất ta phải tìm cả likelihood $p(\mathcal{D} \mid \mathbf{w})$ và prior $\mathcal{p}(\mathbf{w})$.

---

Phần trước: [[Zettel/Expectations and covariances\|Expectations and covariances]]
Phần sau: [[Zettel/Gaussian Distribution\|Gaussian Distribution]]

---
# References

- [Bishop] Pattern Recognition and Machine Learning - Bishop (chapter 1.2)
- [VHT]  [Machine Learning cơ bản (machinelearningcoban.com) - Bài 31](https://machinelearningcoban.com/2017/07/17/mlemap/)
- [Bayesian Machine Learning (cam.ac.uk)](https://mlg.eng.cam.ac.uk/zoubin/bayesian.html)