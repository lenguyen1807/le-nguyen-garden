---
source: "[[Study/Math knowledge\|Math knowledge]]"
id: 202403031037
date_create: 2024-03-03
dg-publish: true
---
Cho $A$ và $B$ là hai tập hợp. Một **quan hệ** $R$ từ $A$ đến $B$ là một tập hợp con của $A \times B$. Nếu $R$ là một quan hệ từ $A$ đến $A$ thì ta nói $R$ là một quan hệ **trên** $A$.

>[!example]+
>Xét $A = \{1, 2, 3, 4, 5\}$, ta định nghĩa $R$ = $\{(1, 2), (1, 3), (1, 4), (1, 5)\}$, ta thấy $R \subseteq A \times B$ do đó $R$ là một quan hệ trên $A$.

Cho $A$ là một tập rỗng, ta nói một quan hệ $\sim$ trên $A$ là một **quan hệ tương đương** nếu thoả mãn ba điều kiện sau:
- (**Tính phản xạ**) Với mỗi $a \in A$, $a \sim a$.
- (**Tính đối xứng**) Với mọi $x, y \in A$, nếu $x \sim y$ thì $y \sim x$.
- (**Tính bắc cầu**) Với mọi $x, y, z \in A$, nếu $x \sim y$ và $y \sim z$ thì $x \sim z$.
Nếu $x \sim y$ thì ta nói $x$ tương đương với $y$.

>[!example]+

Cho $\sim$ là một quan hệ tương đương trên $A$. Với mỗi $x \in A$, lớp tương đương của $a$ được xác định bởi $\sim$ được định nghĩa như sau:
$$
[a] = \{x \in A \mid x \sim a\}
$$
$[a]$ được gọi là **lớp tương đương** của $a$.

>[!example]+

---
# References
- [7.2: Equivalence Relations - Mathematics LibreTexts](https://math.libretexts.org/Bookshelves/Mathematical_Logic_and_Proof/Book%3A_Mathematical_Reasoning__Writing_and_Proof_(Sundstrom)/07%3A_Equivalence_Relations/7.02%3A_Equivalence_Relations)
- [7.3: Equivalence Classes - Mathematics LibreTexts](https://math.libretexts.org/Bookshelves/Mathematical_Logic_and_Proof/Book%3A_Mathematical_Reasoning__Writing_and_Proof_(Sundstrom)/07%3A_Equivalence_Relations/7.03%3A_Equivalence_Classes)