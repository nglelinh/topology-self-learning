---
layout: post
title: "Lecture 00.01: Cartesian Products and Zorn's Lemma"
lang: vi
lang-ref: lecture-00-01
chapter: 0
lecture: 1
categories: [chapter00]
tags: [cartesian-product, axiom-of-choice, zorns-lemma, well-ordering]
description: "Tích Cartesian, Tiên đề Lựa chọn, Bổ đề Zorn và ứng dụng trong topology"
---

**Cartesian Products and Zorn's Lemma**

---

## 📖 Tổng quan

Trong bài trước, chúng ta đã học cách xây dựng các tập hợp cơ bản. Nhưng làm thế nào để tạo ra các không gian phức tạp từ các không gian đơn giản hơn? Câu trả lời là **tích Cartesian** (Cartesian product)—một trong những construction quan trọng nhất trong toán học.

Hãy tưởng tượng: nếu bạn có một đường thẳng (ℝ) và muốn tạo ra một mặt phẳng (ℝ²), bạn lấy "tích" của hai đường thẳng. Nếu bạn có hai không gian tô-pô, bạn có thể tạo ra không gian tô-pô mới bằng cách "nhân" chúng với nhau. Đây chính là ý tưởng đằng sau product topology—một trong những công cụ mạnh nhất để xây dựng không gian phức tạp.

Nhưng có một câu hỏi sâu xa hơn: **Liệu ta luôn có thể "chọn" một phần tử từ mỗi tập hợp?** Câu hỏi tưởng chừng đơn giản này dẫn đến một trong những tiên đề tranh cãi nhất trong toán học—**Axiom of Choice**—và công cụ mạnh mẽ **Bổ đề Zorn**.

**Tại sao bài này quan trọng?** Bài giảng này giới thiệu một trong những constructions fundamental nhất trong topology: **product topology**. Đây là cách chúng ta combine các không gian đơn giản để tạo ra không gian phức tạp, giống như cách ℝ² được tạo từ hai bản sao của ℝ. Nhưng construction này immediately raises một câu hỏi subtle: khi có vô hạn spaces, làm sao chúng ta "choose" elements from each one? Đây là lúc **Axiom of Choice** xuất hiện—một trong những tiên đề controversial nhất trong toán học, nhưng absolutely essential cho nhiều định lý topology. **Bổ đề Zorn** là một formulation equivalent mạnh mẽ của Axiom of Choice, providing công cụ để prove existence của maximal objects như bases for vector spaces, maximal ideals trong rings, và trong topology, bases cho topologies. Cuối cùng, **Well-Ordering Principle** (cũng equivalent với Axiom of Choice) là nền tảng cho transfinite induction—technique cho phép ta reason about uncountably infinite objects.

---

## 🎯 Từ Trực giác đến Hình thức

### Câu chuyện về Tích Cartesian

Hãy bắt đầu với một ví dụ quen thuộc. Giả sử bạn đang thiết kế áo thun và có tập màu sắc C = {đỏ, xanh, vàng} và tập kích cỡ S = {nhỏ, vừa, lớn}. Bạn muốn tạo ra tất cả các combinations có thể—mỗi màu với mỗi size. Đây chính là tích Cartesian: C × S = {(đỏ, nhỏ), (đỏ, vừa), (đỏ, lớn), (xanh, nhỏ), (xanh, vừa), (xanh, lớn), ...}, giving tổng cộng |C × S| = 3 × 3 = 9 possibilities.

**Geometric visualization** giúp ta hiểu deeper: nếu ta đặt C trên trục hoành và S trên trục tung, thì C × S chính là tất cả các điểm trên một "lưới" 3×3. Đây exactly là cách mà mặt phẳng ℝ² được construct từ hai đường thẳng ℝ—mỗi điểm (x, y) trong mặt phẳng là một ordered pair với x từ axis đầu tiên và y từ axis thứ hai.

![Cartesian product visualization](https://upload.wikimedia.org/wikipedia/commons/thumb/4/4e/Cartesian_Product_qtl1.svg/400px-Cartesian_Product_qtl1.svg.png)  
*Tích Cartesian của hai tập hợp - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Cartesian_Product_qtl1.svg)*

### Từ Hữu hạn đến Vô hạn

**Câu hỏi:** Nếu tôi có **vô hạn** tập hợp {A₁, A₂, A₃, ...}, làm sao tạo ra tích của chúng?

Đây là lúc mọi thứ trở nên phức tạp—và kỳ diệu—vì chúng ta cần **Axiom of Choice**.

---

## 📐 Định nghĩa Hình thức

### 1. Ordered Pairs và Cartesian Product

**Định nghĩa (Ordered Pair - Cặp có thứ tự):**  
Cặp có thứ tự (a, b) được định nghĩa (theo Kuratowski) là:

$$
(a, b) := \{\{a\}, \{a, b\}\}
$$

**Tính chất quan trọng:**
$$
(a, b) = (c, d) \iff (a = c) \land (b = d)
$$

**Trực giác:** Thứ tự quan trọng: (1, 2) ≠ (2, 1).

**Định nghĩa (Cartesian Product - Tích Cartesian):**  
Với hai tập A và B, tích Cartesian là:

$$
A \times B = \{(a, b) : a \in A, b \in B\}
$$

**Ví dụ cụ thể:** ℝ × ℝ = ℝ² gives us the familiar plane; ℝ × ℝ × ℝ = ℝ³ constructs three-dimensional space; và {0,1} × {0,1} = {(0,0), (0,1), (1,0), (1,1)} là tập 4 phần tử representing tất cả bit-pairs.

**Tính chất quan trọng của Cartesian product:** Thứ nhất, nó không giao hoán—A × B khác B × A (trừ khi A = B) vì (a,b) ≠ (b,a) when a ≠ b. Order matters! Thứ hai, cardinality của product là product của cardinalities: |A × B| = |A| · |B| khi finite, và điều này extends sang infinite case (with appropriate definitions). Thứ ba, mọi product với empty set đều empty: A × ∅ = ∅, reflecting rằng không có cách nào form ordered pair khi một trong hai components không có elements.

---

### 2. Arbitrary Products (Tích Tùy ý)

**Vấn đề:** Làm sao định nghĩa tích của vô hạn tập hợp?

Giả sử có họ tập hợp {Aᵢ : i ∈ I} với I là tập chỉ số (index set).

**Cách tiếp cận ngây thơ:** "Chọn một phần tử từ mỗi Aᵢ"...

**Nhưng:** Làm sao "chọn" khi có vô hạn tập hợp?

**Định nghĩa (Product of indexed family):**  
Tích Cartesian của họ {Aᵢ}ᵢ∈I là:

$$
\prod_{i \in I} A_i = \left\{ f: I \to \bigcup_{i \in I} A_i \; \middle| \; \forall i \in I: f(i) \in A_i \right\}
$$

**Trực giác:** Mỗi phần tử của tích là một **hàm lựa chọn** (choice function) gán cho mỗi chỉ số i một phần tử từ Aᵢ.

**Ví dụ về infinite products:** ℝ^ℕ (product của countably nhiều copies của ℝ) là tập tất cả infinite sequences of real numbers—mỗi sequence (x₁, x₂, x₃, ...) là một choice function chọn xᵢ ∈ ℝ cho mỗi index i ∈ ℕ. Similarly, {0,1}^ℕ là tập tất cả infinite binary sequences, forming a fundamental object trong topology known as the Cantor space.

![Infinite product visualization](https://upload.wikimedia.org/wikipedia/commons/thumb/9/92/Binary_tree_structure.svg/400px-Binary_tree_structure.svg.png)  
*Cây nhị phân biểu diễn {0,1}^ℕ - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Binary_tree_structure.svg)*

---

### 3. Axiom of Choice (AC)

**Phát biểu (Informal):**  
Cho một họ các tập hợp không rỗng {Aᵢ}ᵢ∈I. Luôn tồn tại một "choice function" chọn đúng một phần tử từ mỗi Aᵢ.

**Phát biểu (Formal):**

$$
\forall \mathcal{F}: \left(\emptyset \notin \mathcal{F}\right) \implies \exists f: \mathcal{F} \to \bigcup \mathcal{F} \text{ sao cho } \forall A \in \mathcal{F}: f(A) \in A
$$

**Trực giác:** Nếu bạn có vô hạn cặp giày, bạn có thể chọn một chiếc từ mỗi cặp (chọn chiếc trái). Nhưng nếu bạn có vô hạn cặp tất (không phân biệt trái phải), làm sao bạn "chọn" một chiếc từ mỗi cặp mà không có quy tắc?

**Ví dụ nổi tiếng của Bertrand Russell** illuminate khi nào AC cần và không cần. Consider vô hạn pairs of shoes: bạn có thể choose một shoe from each pair mà không cần AC bằng cách simply chọn "chiếc trái" từ mỗi cặp—đây là một explicit rule. Nhưng với vô hạn pairs of socks (giả sử indistinguishable), không có "rule" nào để pick one sock from each pair. Bạn cần AC để assert rằng such a choice function exists, dù bạn không thể construct nó explicitly. Đây là điểm subtle: AC doesn't tell you *how* to choose, nó chỉ assert that a choice *can* be made.

**Hệ quả quan trọng:**

**Định lý:**  
Với họ không rỗng {Aᵢ}ᵢ∈I, nếu mỗi Aᵢ ≠ ∅, thì:

$$
\prod_{i \in I} A_i \neq \emptyset \iff \text{Axiom of Choice}
$$

**Tại sao Axiom of Choice quan trọng trong topology?** Nhiều định lý fundamental trong topology absolutely require AC. **Tychonoff's Theorem** states rằng arbitrary product của compact spaces là compact—đây là một trong những theorems central nhất trong topology, và nó equivalent với AC! Không có AC, ta không thể prove theorem này for uncountable products. **Basis Theorem** trong linear algebra (every vector space has a basis) cũng requires AC khi không gian vô hạn chiều. Trong topology, **Stone-Čech compactification**—cách canonical để embed một completely regular space vào một compact space—existence của nó cần AC. Những results này không phải là technical curiosities; chúng là workhorses của modern topology và analysis.

---

### 4. Zorn's Lemma

**Định nghĩa (Partially Ordered Set - Poset):**  
Một **poset** (A, ≤) là tập A cùng với quan hệ ≤ thỏa mãn:
1. **Reflexive:** a ≤ a
2. **Antisymmetric:** (a ≤ b) ∧ (b ≤ a) ⇒ (a = b)
3. **Transitive:** (a ≤ b) ∧ (b ≤ c) ⇒ (a ≤ c)

**Ví dụ về posets:** Real numbers với usual ordering (ℝ, ≤) form một poset where transitivity và antisymmetry hold. Power set 𝒫(X) với set inclusion (𝒫(X), ⊆) là another poset—two sets A, B satisfy A ⊆ B and B ⊆ A exactly when A = B. Đặc biệt relevant cho topology là collection của tất cả topologies trên một fixed set X, ordered by inclusion: topology τ₁ ⊆ τ₂ means τ₁ is coarser (has fewer open sets) than τ₂.

**Định nghĩa (Chain - Xích):**  
Một **chain** (hoặc totally ordered subset) trong poset (A, ≤) là tập con C ⊆ A sao cho mọi a, b ∈ C đều so sánh được: a ≤ b hoặc b ≤ a.

**Định nghĩa (Upper Bound - Cận trên):**  
Phần tử u ∈ A là **upper bound** của C nếu ∀c ∈ C: c ≤ u.

**Định nghĩa (Maximal Element - Phần tử cực đại):**  
Phần tử m ∈ A là **maximal** nếu không tồn tại a ∈ A với m < a.

**Chú ý:** Maximal ≠ Maximum! Có thể có nhiều maximal elements.

**Bổ đề Zorn (Zorn's Lemma):**

> **Nếu mọi chain trong poset (A, ≤) đều có upper bound, thì A có ít nhất một phần tử maximal.**

$$
\left(\forall \text{ chain } C \subseteq A: \exists u \in A: \forall c \in C: c \leq u\right) \implies \exists m \in A: m \text{ is maximal}
$$

![Zorn's Lemma visualization](https://upload.wikimedia.org/wikipedia/commons/thumb/e/e5/Hasse_diagram_of_powerset_of_3.svg/300px-Hasse_diagram_of_powerset_of_3.svg.png)  
*Hasse diagram minh họa maximal elements - Nguồn: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Hasse_diagram_of_powerset_of_3.svg)*

**Trực giác:** Nếu bạn có thể "leo lên" dọc theo mọi "đường mòn" (chain) và luôn có "đỉnh tạm thời", thì phải tồn tại một "đỉnh cuối cùng" mà bạn không thể leo cao hơn.

---

### 5. Equivalence: AC ⟺ Zorn ⟺ WOP

Ba phát biểu sau đây **tương đương** (trong ZF):

1. **Axiom of Choice (AC)**
2. **Zorn's Lemma (ZL)**
3. **Well-Ordering Principle (WOP):** Mọi tập hợp đều có thể well-ordered.

**Định nghĩa (Well-ordered):**  
Một tập A với quan hệ thứ tự ≤ là **well-ordered** nếu mọi tập con không rỗng của A đều có phần tử nhỏ nhất.

**Ví dụ về well-ordering:** Natural numbers (ℕ, ≤) are well-ordered—every non-empty subset has a least element, which là why induction works! Integers (ℤ, ≤) are NOT well-ordered vì ℤ itself không có phần tử nhỏ nhất (goes to -∞). Similarly, real numbers (ℝ, ≤) are not well-ordered; for instance, open interval (0,1) có không smallest element.

**Well-Ordering Principle:**  
Tồn tại một quan hệ thứ tự trên ℝ (khác ≤ thông thường) sao cho (ℝ, ≼) well-ordered!

**Triết học:** WOP có vẻ "ngược" với trực giác, nhưng nó tương đương với AC—một công cụ chúng ta sử dụng mỗi ngày.

---

### 6. Ứng dụng trong Topology

**Ứng dụng 1: Tồn tại Basis**

**Định lý:**  
Mọi không gian tô-pô có một basis.

**Chứng minh (sketch):** Dùng Zorn's Lemma trên poset của các họ tập mở với quan hệ bao hàm. Mọi chain có upper bound (là hợp của chain). Do đó tồn tại basis maximal.

**Ứng dụng 2: Tychonoff's Theorem**

**Định lý Tychonoff:**  
Tích tùy ý các không gian compact là compact (trong product topology).

**Chú ý:** Chứng minh CẦN Axiom of Choice! Thực tế, Tychonoff's Theorem tương đương với AC.

**Ứng dụng 3: Hausdorff Maximal Principle**

**Định lý:**  
Mọi chain trong poset có thể mở rộng thành maximal chain.

**Ý nghĩa:** Trong topology, dùng để chứng minh sự tồn tại của ultrafilters, compactifications, etc.

---

## 🧠 Fundamental Papers & References

### Classic Papers

1. **Ernst Zermelo** - *"Beweis, daß jede Menge wohlgeordnet werden kann"* (1904)  
   *Chứng minh đầu tiên của Well-Ordering Theorem (và ngầm định AC)*

2. **Max Zorn** - *"A Remark on Method in Transfinite Algebra"* (1935)  
   *Giới thiệu "Zorn's Lemma" - công cụ thay thế cho transfinite induction*

3. **Kurt Gödel** - *"The Consistency of the Axiom of Choice"* (1938)  
   *Chứng minh AC consistent với ZF*

4. **Paul Cohen** - *"The Independence of the Continuum Hypothesis"* (1963)  
   *Chứng minh AC độc lập với ZF (Fields Medal!)*

### Textbooks

5. **James R. Munkres** - *Topology*, 2nd Ed., **§9: Infinite Sets and Axiom of Choice**  
   *Trình bày rõ ràng về AC và product topology*

6. **Thomas Jech** - *The Axiom of Choice* (1973)  
   *Monograph toàn diện về AC và các hệ quả*

7. **Kelley, John L.** - *General Topology* (1955), **Chapter 0**  
   *Classic treatment của choice principles*

---

## 🔗 Applications and Connections

### Physics - Quantum Mechanics
**Fock Spaces:** Trong quantum field theory, ta xây dựng không gian Fock bằng cách lấy tổng trực tiếp của các tensor products. AC đảm bảo basis tồn tại cho các không gian vô hạn chiều này.

### Functional Analysis
**Hahn-Banach Theorem:** Một trong những định lý quan trọng nhất trong giải tích hàm, chứng minh CẦN Axiom of Choice (hoặc Zorn's Lemma).

### Algebra
**Basis of Vector Spaces:** Mọi không gian vector có basis—điều này cần Zorn's Lemma! Không có AC, có thể tồn tại không gian vector không có basis.

### Computer Science
**Banach-Tarski Paradox:** Sử dụng AC, có thể "chia" một quả bóng thành 5 mảnh và "lắp ráp" lại thành 2 quả bóng giống hệt quả ban đầu! (Không thể thực hiện trong thực tế vì các mảnh không đo được)

### Real-World Example
**Database Joins:** Khi join hai bảng trong database, ta thực hiện Cartesian product của các rows. Số lượng kết quả = |Table1| × |Table2|. Product topology là phiên bản tô-pô của khái niệm này.

---

## 🧩 Exercises

### Conceptual Questions

1. **Visualize Products:**  
   Vẽ hình minh họa [0,1] × [0,1] (hình vuông đơn vị) và S¹ × [0,1] (cylinder).  
   - Mô tả topology trên các không gian này.
   - S¹ × S¹ trông như thế nào? (Hint: Torus!)

2. **Cardinality of Products:**  
   Chứng minh rằng |ℝ × ℝ| = |ℝ| bằng cách xây dựng bijection tường minh.  
   (*Hint:* Cantor's "interleaving" trick)

3. **Choice Function:**  
   Cho họ tập hợp {% raw %}{{1}, {1,2}, {1,2,3}, ...}{% endraw %}.  
   - Viết tường minh một choice function.
   - Điều này có cần Axiom of Choice không? Tại sao?

4. **Zorn's Lemma Application:**  
   Xét poset (𝒫(ℕ), ⊆) của tất cả tập con của ℕ.
   - Liệt kê một chain trong poset này.
   - Upper bound của chain đó là gì?
   - Các maximal elements là gì?

5. **Well-Ordering Challenge:**  
   Giả sử (ℝ, ≼) well-ordered.
   - Nếu x₀ là phần tử nhỏ nhất, x₀ là số nào?
   - Successor của x₀ (nếu có) là gì?
   - Điều này có phù hợp với trực giác về ℝ không?

### Advanced Problems

6. **Countable vs Uncountable Products:**  
   - Chứng minh: Nếu mỗi Aᵢ có ít nhất 2 phần tử, thì ∏ᵢ₌₁^∞ Aᵢ là uncountable.
   - Kết luận gì về {0,1}^ℕ?

7. **Topology Preview:**  
   Trong ℝ² = ℝ × ℝ, xét tập U = {(x,y) : x² + y² < 1} (đĩa mở).
   - U có dạng A × B với A, B ⊆ ℝ không?
   - Điều này gợi ý gì về cách xây dựng "open sets" trong product topology?

8. **AC Independence:**  
   Tìm hiểu về "Dedekind-finite sets"—các tập hợp không song ánh với tập con thực sự của chính nó.
   - Trong ZF (không có AC), có thể tồn tại Dedekind-finite nhưng vô hạn!
   - Điều này có thể xảy ra với AC không?

### Reflection Questions

9. **Philosophical Debate:**  
   Một số toán học gia từ chối Axiom of Choice vì nó "non-constructive".  
   - Tại sao AC được coi là "không xây dựng"?
   - Bạn có nghĩ chúng ta nên chấp nhận AC không? Tại sao?

10. **Big Picture:**  
    So sánh AC, Zorn's Lemma, và Well-Ordering Principle.  
    - Phát biểu nào "trực quan" nhất?
    - Phát biểu nào hữu ích nhất trong topology?

---

## 📚 Further Reading

- **Munkres, Topology:** §9 (Infinite Sets and AC)
- **Kelley, General Topology:** Chapter 0 (Preliminaries on Set Theory)
- **Halmos, Naive Set Theory:** §15–16 (Axiom of Choice)
- **Jech, The Axiom of Choice:** Chapters 1–3 (Comprehensive treatment)
- **Herrlich, Axiom of Choice (Lecture Notes in Math):** Modern perspective

---

## 🎓 Summary

Trong bài giảng này, chúng ta đã khám phá:

✅ **Cartesian Product:** Công cụ xây dựng không gian mới từ không gian cũ  
✅ **Infinite Products:** Cần choice functions để định nghĩa  
✅ **Axiom of Choice:** Tiên đề mạnh mẽ nhưng controversial  
✅ **Zorn's Lemma:** Công cụ chứng minh sự tồn tại  
✅ **Equivalence:** AC ⟺ Zorn ⟺ Well-Ordering Principle  

**Điểm chính:**
- Tích Cartesian là nền tảng của product topology
- AC tưởng chừng "hiển nhiên" nhưng có hệ quả sâu sắc
- Zorn's Lemma là công cụ powerful để chứng minh tồn tại maximal objects
- Ba phát biểu AC, Zorn, WOP tương đương—chọn cái nào tiện cho bài toán

**Connection đến topology:**
- Product topology: ℝⁿ, tori, infinite-dimensional spaces
- Tychonoff's Theorem: Compact × Compact = Compact
- Basis existence: Mọi topology có basis

**Tiếp theo:** Trong Lecture 00.02, chúng ta sẽ học về **Logic và Proof Techniques**—cách lập luận chặt chẽ trong toán học, nền tảng để hiểu các chứng minh tô-pô phức tạp.

---

*"The Axiom of Choice is obviously true, the Well-Ordering Principle obviously false, and who can tell about Zorn's Lemma?"* — Jerry Bona

🎯 **Hãy vẽ Cartesian products và suy nghĩ về infinity!** 🎯

---

**Previous:** [Lecture 00.00: Set Theory, Functions, and Relations](/contents/vi/topology-chapter00/00_00_Set_Theory_Functions_Relations/)  
**Next:** [Lecture 00.02: Logic and Mathematical Proofs](/contents/vi/topology-chapter00/00_02_Logic_Mathematical_Proofs/)

