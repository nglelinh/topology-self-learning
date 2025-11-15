---
layout: post
title: "Lecture 03.01: Regular and Normal Spaces - Urysohn's Lemma"
lang: vi
lang-ref: lecture-03-01
chapter: 3
lecture: 1
categories: [chapter03]
tags: [regular-spaces, normal-spaces, urysohn-lemma, tietze-extension, T3, T4]
description: "T₃ (Regular) và T₄ (Normal) spaces, Urysohn's Lemma, Tietze Extension Theorem"
---

**Regular and Normal Spaces - Urysohn's Lemma**

---

## 📖 Tổng quan

Trong bài trước, chúng ta học về T₀, T₁, T₂ (Hausdorff)—cách "tách" hai **điểm** khác nhau. Giờ đây chúng ta nâng cấp: làm sao "tách" **điểm và tập closed**, hoặc **hai tập closed** disjoint?

**Hierarchy tiếp tục:**

$$
T_2 \subset T_3 \subset T_{3.5} \subset T_4
$$

**Động lực:**
- **T₃ (Regular):** Tách điểm và closed set
- **T₄ (Normal):** Tách hai closed sets disjoint
- **T₃.₅ (Completely Regular/Tychonoff):** Tách bằng continuous functions

**Ví dụ trực quan:**

Tưởng tượng Alice đứng **bên ngoài** một căn phòng (closed set). 
- **Regular:** Có thể xây "bức tường" (open sets) ngăn cách Alice và phòng
- **Normal:** Có hai phòng riêng biệt, có thể xây tường ngăn cách chúng
- **Tychonoff:** Có "gradient" (continuous function) từ Alice (=0) đến phòng (=1)

![Regular and Normal spaces](https://upload.wikimedia.org/wikipedia/commons/thumb/8/87/Normal_space.svg/500px-Normal_space.svg.png)  
*Normal space: hai closed sets có disjoint neighborhoods - Nguồn concept*

**Trong bài này:**
- **T₃ (Regular spaces):** Definition và examples
- **T₄ (Normal spaces):** Strongest separation trong "standard" hierarchy
- **Urysohn's Lemma:** Existence của continuous functions
- **Tietze Extension Theorem:** Extending continuous functions
- Applications trong analysis

**Tại sao quan trọng?**
- Urysohn's Lemma = powerful existence tool
- Normal spaces = "nice" spaces (ℝⁿ, compact Hausdorff, metric spaces)
- Tietze = extension property, key trong homotopy theory
- Metrization: T₃ + second countable ⇒ metrizable

---

## 📐 Định nghĩa Hình thức

### 1. T₃ Spaces (Regular)

**Định nghĩa (Regular Space):**  
X là **regular** nếu với mọi x ∈ X và closed set F không chứa x, tồn tại disjoint open neighborhoods.

$$
\forall x \in X, \forall F \text{ closed}: x \notin F \implies \exists U, V \in \tau: x \in U, F \subseteq V, U \cap V = \emptyset
$$

**Định nghĩa (T₃ Space):**  
X là **T₃** nếu X **regular** và **T₁** (hay T₀—authors vary).

**Convention:** Chúng ta dùng **T₃ = regular + T₁**.

**Trực giác:** Có thể "separate" điểm khỏi closed set bằng open sets disjoint.

![Regular space illustration](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f1/Regular_space.svg/400px-Regular_space.svg.png)  
*Regular: điểm và closed set có disjoint neighborhoods - Nguồn concept*

**Ví dụ 1: Metric Spaces**

**Định lý:** Mọi metric space là regular.

**Chứng minh:**  
Cho x ∉ F closed. Đặt d = d(x, F) = inf{d(x,y) : y ∈ F} > 0 (vì F closed).  
U = B(x, d/2), V = ⋃_{y∈F} B(y, d/2).  
U ∩ V = ∅ (triangle inequality). ✓

**Hệ quả:** ℝⁿ (Euclidean) là T₃.

**Ví dụ 2: Compact Hausdorff**

**Định lý:** Mọi compact Hausdorff space là regular.

**Chứng minh (sketch):**  
Cho x ∉ F closed. Với mọi y ∈ F:
- Hausdorff → ∃U_y ∋ x, V_y ∋ y disjoint.
{V_y} open cover của F → finite subcover (compact).
U = ⋂ U_{y_i}, V = ⋃ V_{y_i} là disjoint neighborhoods. ✓

**Non-example: Countable Complement Topology**

Trên uncountable set, cocountable topology **không regular**!

**Proof:** Xét x và F = {y} (singleton closed).  
Mọi open U ∋ x, V ∋ y đều uncountable → U ∩ V ≠ ∅. ✗

---

### 2. T₄ Spaces (Normal)

**Định nghĩa (Normal Space):**  
X là **normal** nếu với mọi hai closed sets disjoint A, B, tồn tại disjoint open neighborhoods.

$$
\forall A, B \text{ closed}: A \cap B = \emptyset \implies \exists U, V \in \tau: A \subseteq U, B \subseteq V, U \cap V = \emptyset
$$

**Định nghĩa (T₄ Space):**  
X là **T₄** nếu X **normal** và **T₁**.

![Normal space illustration](https://upload.wikimedia.org/wikipedia/commons/thumb/c/c3/T4_space.svg/400px-T4_space.svg.png)  
*Normal: hai closed sets disjoint có disjoint neighborhoods - Nguồn concept*

**Ví dụ 1: Metric Spaces**

**Định lý:** Mọi metric space là normal.

**Chứng minh:**  
Cho A, B closed disjoint.  
Define: d_A(x) = inf{d(x,a) : a ∈ A}, d_B(x) tương tự.  
U = {x : d_A(x) < d_B(x)}, V = {x : d_B(x) < d_A(x)}.  
U, V open, A ⊆ U, B ⊆ V, U ∩ V = ∅. ✓

**Ví dụ 2: Compact Hausdorff**

**Định lý:** Mọi compact Hausdorff space là normal.

**Chứng minh:** Tương tự như regular case, sử dụng compactness. ✓

**Non-example: Sorgenfrey Plane**

**Sorgenfrey line** ℝ_ℓ = ℝ với lower limit topology (basis {[a,b)}) là normal.  
Nhưng **Sorgenfrey plane** ℝ_ℓ × ℝ_ℓ **không normal**!

**Proof:** Kỳ diệu và phức tạp—famous counterexample.

**Ý nghĩa:** Normality **không** preserved by products (even finite!)

---

### 3. Urysohn's Lemma

**Định lý Urysohn (Urysohn's Lemma):**

> **Nếu X normal, A, B closed disjoint, thì tồn tại continuous function f: X → [0,1] với:**
> $$f(A) = \{0\}, \quad f(B) = \{1\}$$

**Nói bằng lời:** Trong normal space, có thể "separate" hai closed sets bằng continuous function!

![Urysohn Lemma visualization](https://upload.wikimedia.org/wikipedia/commons/thumb/5/56/Urysohn_function.svg/500px-Urysohn_function.svg.png)  
*Urysohn function: continuous separation - Nguồn concept*

**Ý nghĩa:**  
- Normality ⇒ existence của "many" continuous functions
- Basis cho metrization theorems
- Key tool trong homotopy theory

**Chứng minh (Construction):**

**Idea:** Construct f bằng cách xây dựng nested open sets.

**Step 1:** Sử dụng normality recursively để tạo họ open sets {U_r}_{r∈ℚ∩[0,1]} sao cho:
- A ⊆ U_0
- U_1^c ⊇ B (hay equivalently, cl(U_1) ∩ B = ∅)
- r < s ⇒ cl(U_r) ⊆ U_s

**Construction of {U_r}:**
1. U_0: normal → ∃U_0 ⊇ A với cl(U_0) ∩ B = ∅
2. U_1: normal → ∃V ⊇ B disjoint từ cl(U_0). Set U_1 = X \ cl(V)
3. U_{1/2}: normal applied to cl(U_0) và X \ U_1
4. Continue binary subdivision...

**Step 2:** Define f:
$$
f(x) = \begin{cases}
\inf\{r \in \mathbb{Q} \cap [0,1] : x \in U_r\} & \text{if } x \in U_1 \\
1 & \text{if } x \notin U_1
\end{cases}
$$

**Step 3:** Verify f continuous:  
f⁻¹([0,a)) = ⋃_{r<a} U_r open.  
f⁻¹((a,1]) = ⋃_{s>a} (X \ cl(U_s)) open.  
→ f continuous. ✓

**Verification:**
- x ∈ A → x ∈ U_r với mọi r → f(x) = 0
- x ∈ B → x ∉ U_1 → f(x) = 1 ✓

**Corollary quan trọng:**  
Normal space có "plenty" of continuous functions!

---

### 4. Tietze Extension Theorem

**Định lý Tietze (Tietze Extension Theorem):**

> **Nếu X normal, A ⊆ X closed, f: A → [a,b] continuous, thì tồn tại extension F: X → [a,b] continuous với F|_A = f.**

```
A ---f---> [a,b]
|          
i|         
v          
X ---F---> [a,b]
```

**Nói bằng lời:** Continuous functions trên closed subsets có thể extend lên toàn bộ space!

**Ý nghĩa:**
- Powerful trong homotopy theory
- Basis cho partition of unity
- Key trong differential topology

**Chứng minh (Sketch):**

**Idea:** Approximate f bằng sequence của extensions.

**WLOG:** Assume f: A → [-1,1] (scale if necessary).

**Step 1:** Apply Urysohn cho A₁ = f⁻¹([-1, -1/3]), A₂ = f⁻¹([1/3, 1]).  
Tồn tại g₁: X → [-1/3, 1/3] với g₁(A₁) = -1/3, g₁(A₂) = 1/3.

**Step 2:** Set f₁ = f - g₁|_A: A → [-2/3, 2/3].

**Step 3:** Iterate: construct g₂, g₃, ... với |gₙ| ≤ (2/3)ⁿ.

**Step 4:** F = ∑ gₙ converges uniformly → continuous. ✓

**Verification:** F|_A = ∑(f - f₁ + f₁ - f₂ + ...) = f. ✓

---

### 5. T₃.₅ Spaces (Completely Regular / Tychonoff)

**Định nghĩa (Completely Regular):**  
X là **completely regular** nếu với mọi x ∈ X và closed F ∋ x, tồn tại continuous f: X → [0,1] với f(x) = 0, f(F) = {1}.

**Định nghĩa (T₃.₅ / Tychonoff Space):**  
X là **Tychonoff** nếu completely regular và T₁.

**Hierarchy:**
$$
T_4 \implies T_{3.5} \implies T_3 \implies T_2 \implies T_1 \implies T_0
$$

**Ví dụ:**
- Metric spaces: Tychonoff ✓
- Compact Hausdorff: Tychonoff ✓
- Subspaces của Tychonoff: Tychonoff ✓

**Ý nghĩa:** Tychonoff spaces = spaces có "enough" continuous functions.

**Định lý:**  
X Tychonoff ⟺ X homeomorphic với subspace của [0,1]^I (product of intervals).

**Proof:** Embedding Theorem—advanced. ✓

---

### 6. Relationships và Properties

**Summary Diagram:**

```
                T₄ (Normal + T₁)
                      ↓
              T₃.₅ (Tychonoff)
                      ↓
              T₃ (Regular + T₁)
                      ↓
              T₂ (Hausdorff)
                      ↓
                  T₁ (Fréchet)
                      ↓
              T₀ (Kolmogorov)
```

**Key Facts:**
1. **Metric ⇒ T₄:** Mọi metric space normal
2. **Compact Hausdorff ⇒ T₄:** Compact + Hausdorff = normal
3. **T₄ ⇒ Urysohn's Lemma:** Existence của separating functions
4. **T₄ + Urysohn ⇒ Tietze:** Extension property
5. **Products:** Normality **không** preserved! (Sorgenfrey plane)

**Theorem (Preservation):**
- Subspace của T₃ là T₃
- Subspace của Tychonoff là Tychonoff
- Product của Tychonoff là Tychonoff (Tychonoff product theorem)
- Product của T₄ **không nhất thiết** T₄!

---

## 🧠 Fundamental Papers & References

### Classic Papers

1. **Pavel Urysohn** - *"Über die Mächtigkeit der zusammenhängenden Mengen"* (1925)  
   *Urysohn's Lemma - một trong những công cụ mạnh nhất*

2. **Heinrich Tietze** - *"Über Funktionen, die auf einer abgeschlossenen Menge stetig sind"* (1915)  
   *Tietze Extension Theorem*

3. **Andrey Tychonoff** - *"Über einen Funktionenraum"* (1935)  
   *Completely regular spaces*

### Textbooks

4. **James R. Munkres** - *Topology*, 2nd Ed., **§31–33: Normal Spaces**  
   *Complete proofs của Urysohn và Tietze*

5. **Stephen Willard** - *General Topology*, **Chapter 5**  
   *Advanced treatment*

6. **John L. Kelley** - *General Topology*, **Chapter 4**  
   *Classic exposition*

---

## 🔗 Applications and Connections

### Analysis - Extension Problems
**Hahn-Banach:** Tietze là topological analog của Hahn-Banach theorem (functional analysis).

### Differential Topology - Partitions of Unity
**Smooth Extensions:** Tietze + smoothing = partition of unity trên manifolds.

### Homotopy Theory
**CW Complexes:** Urysohn + Tietze essential trong constructing homotopies.

### Metrization
**Urysohn Metrization:** T₃ + second countable ⇒ metrizable (next lecture!)

---

## 🧩 Exercises

### Regular Spaces

1. **Metric Regular:**  
   Chứng minh chi tiết: mọi metric space là regular.

2. **Compact Hausdorff:**  
   Chứng minh: compact Hausdorff ⇒ regular.

3. **Subspace:**  
   Nếu X regular, A ⊆ X, chứng minh A regular (subspace topology).

### Normal Spaces

4. **Metric Normal:**  
   Chứng minh: mọi metric space là normal.

5. **Compact Hausdorff Normal:**  
   Chứng minh: compact Hausdorff ⇒ normal.

6. **Products:**  
   Tìm hiểu Sorgenfrey plane.  
   Tại sao ℝ_ℓ × ℝ_ℓ không normal?

### Urysohn's Lemma

7. **Apply Urysohn:**  
   X = ℝ, A = {0}, B = {1}.  
   Construct explicitly một Urysohn function f: ℝ → [0,1] với f(A) = 0, f(B) = 1.

8. **Uniqueness:**  
   Urysohn function có unique không? Nếu không, có bao nhiêu?

9. **Converse:**  
   Nếu X có property "mọi A, B closed disjoint có Urysohn function", thì X có normal không?

### Tietze Extension

10. **Apply Tietze:**  
    X = ℝ, A = [0,1], f: A → ℝ, f(x) = sin(πx).  
    Tìm extension F: ℝ → [-1,1].

11. **Non-example:**  
    X = ℚ (rationals), A = ℚ ∩ [0,1], f(x) = x.  
    Có thể extend f lên ℝ continuous không? Tại sao/tại sao không?

### Advanced

12. **T₃.₅:**  
    Chứng minh: T₄ ⇒ T₃.₅.  
    (*Hint:* Dùng Urysohn)

13. **Embedding:**  
    Chứng minh: Mọi Tychonoff space embeds vào [0,1]^I với I thích hợp.

14. **Counterexample:**  
    Tìm T₃ space không T₄.  
    (*Hint:* Tìm trong uncountable spaces)

15. **Metrization Preview:**  
    Nếu X T₃ và second countable, chứng minh X có countably many Urysohn functions "separating points from closed sets".

### Reflection

16. **Urysohn's Power:**  
    Giải thích tại sao Urysohn's Lemma "powerful"—nó guarantee existence của functions mà không cần construct!

17. **Normality vs Products:**  
    Tại sao normality không preserved bởi products, trong khi Hausdorff thì có?

---

## 📚 Further Reading

- **Munkres, Topology:** §31–33 (Normal Spaces, Urysohn, Tietze)
- **Willard, General Topology:** Chapter 5 (Normal and Completely Regular Spaces)
- **Engelking, General Topology:** Chapter 1.5 (Separation)
- **Steen & Seebach:** *Counterexamples* (Sorgenfrey plane, etc.)

---

## 🎓 Summary

Trong bài này, chúng ta nâng cấp separation hierarchy:

✅ **T₃ (Regular):** Tách điểm khỏi closed set  
✅ **T₄ (Normal):** Tách hai closed sets disjoint  
✅ **Urysohn's Lemma:** Normal ⇒ existence của continuous separating functions  
✅ **Tietze Extension:** Extend continuous functions từ closed subsets  
✅ **T₃.₅ (Tychonoff):** Separate bằng continuous functions  
✅ **Hierarchy:** T₄ ⇒ T₃.₅ ⇒ T₃ ⇒ T₂  

**Điểm chính:**
- Metric spaces, compact Hausdorff đều normal
- Urysohn = existence tool (không cần explicit construction!)
- Tietze = extension property
- Normality **không** preserved by products
- Applications: metrization, homotopy theory, partitions of unity

**Tiếp theo:** Lecture 03.02 về **Countability Axioms**—first/second countable, separable, Lindelöf spaces!

---

*"Urysohn's Lemma: In normal spaces, closed sets can be separated not just by open sets, but by continuous functions."* — Topological wisdom

🎯 **Master Urysohn and Tietze—they're everywhere in topology!** 🎯

---

**Previous:** [Lecture 03.00: T₀, T₁, T₂ Spaces](/contents/vi/topology-chapter03/03_00_Separation_Axioms_T0_T1_T2/)  
**Next:** [Lecture 03.02: Countability Axioms](/contents/vi/topology-chapter03/03_02_Countability_Axioms/)

