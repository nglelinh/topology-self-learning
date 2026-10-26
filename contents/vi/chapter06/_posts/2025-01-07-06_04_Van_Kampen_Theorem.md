---
layout: post
title: "Lecture 06.04: Seifert-Van Kampen Theorem"
lang: vi
lang-ref: lecture-06-04
chapter: 6
lecture: 4
categories: [chapter06]
tags: [van-kampen, fundamental-group, free-product, amalgamated-product]
description: "Seifert-Van Kampen Theorem: computing π₁ từ decomposition, free products, amalgamated products"
---

**Computing π₁ from Pieces - Powerful Decomposition Method**

---

## 📖 Tổng quan

Đến giờ, chúng ta có hai phương pháp chính để tính toán $\pi_1$:
1. **Covering spaces:** Mạnh mẽ nhưng yêu cầu tìm covering space
2. **Homotopy equivalence:** Tốt nhưng giới hạn ở các không gian đơn giản

**Van Kampen's Theorem** cung cấp phương pháp THỨ BA—có thể nói là mạnh mẽ nhất:

> **Phân tích không gian $X = A \cup B$, tính toán $\pi_1(X)$ từ $\pi_1(A)$, $\pi_1(B)$, $\pi_1(A \cap B)$.**

**Tại sao đây là một cuộc cách mạng?**

Trước Van Kampen (1933), việc tính toán $\pi_1$ của các không gian phức tạp là cực kỳ khó khăn. Van Kampen đã chỉ ra rằng chúng ta có thể **chia để trị**—chia không gian phức tạp thành các phần đơn giản, sau đó kết hợp chúng lại bằng cách sử dụng **free product with amalgamation**—một cách kết hợp đại số các fundamental groups. Điều này cho phép **tính toán có hệ thống**—một thuật toán cho nhiều loại không gian. Đây là một lý thuyết đẹp—đại số thuần túy xác định topology.

![Van Kampen decomposition](https://upload.wikimedia.org/wikipedia/commons/thumb/c/c9/Seifert-van_Kampen.svg/500px-Seifert-van_Kampen.svg.png)  
*Decomposing space for Van Kampen - Nguồn concept*

Trong bài học này, chúng ta sẽ khám phá định lý Van Kampen một cách có hệ thống. Chúng ta sẽ nghiên cứu **phát biểu** của định lý sử dụng free product with amalgamation—một cách kết hợp các fundamental groups của các phần khác nhau của không gian. Chúng ta sẽ khám phá các **trường hợp đặc biệt** như intersection simply connected và wedge sums—những trường hợp này đơn giản hóa đáng kể việc tính toán. Chúng ta sẽ xem xét **chứng minh sketch** từ góc nhìn của category theory—định lý Van Kampen nói rằng $\pi_1$ bảo toàn pushouts. Chúng ta sẽ nghiên cứu các **ví dụ** cụ thể như $S^1$, figure-eight, torus, surfaces, $\mathbb{R}P^2$, và CW complexes—những ví dụ này cho thấy sức mạnh của phương pháp. Chúng ta sẽ xem xét các **ứng dụng** trong tính toán có hệ thống và **lý thuyết nhóm** về free products và amalgamated products.

**Tại sao đây là kiến thức quan trọng?** Đây là **phương pháp linh hoạt nhất** để tính toán $\pi_1$—nó hoạt động cho nhiều loại không gian khác nhau. Nó **hoạt động cho CW complexes** (được xây dựng bằng cách dán các cells)—đây là một lớp không gian rất quan trọng trong topology. Nó **chứng minh các định lý tổng quát** (không chỉ các ví dụ)—cho phép chúng ta tính toán fundamental groups một cách có hệ thống. Cuối cùng, nó là một **cây cầu** giữa Topology và Group theory—cho thấy cách các công cụ đại số có thể được sử dụng để nghiên cứu topology.

---

## 🎯 Statement của Van Kampen

### 1. Free Product với Amalgamation

**Nhắc lại (Free Product):**  
Cho các nhóm $G$, $H$. **Free product** $G * H$ là nhóm được xây dựng bằng cách:
- Generators: các phần tử của $G$ và $H$
- Relations: chỉ những relations đã có trong $G$, $H$
- Không có relations mới giữa $G$ và $H$

Trực giác hình học là chúng ta kết hợp hai nhóm lại với nhau mà không tạo ra bất kỳ relations nào giữa chúng—mỗi nhóm giữ nguyên cấu trúc của nó, và chúng ta chỉ đơn giản là "dán" chúng lại với nhau.

**Ví dụ:** $\mathbb{Z} * \mathbb{Z}$ = free group trên 2 generators (không abelian!). Đây là một ví dụ quan trọng—free product của hai nhóm cyclic vô hạn là một nhóm không abelian, mặc dù mỗi nhóm ban đầu là abelian.

---

**Định nghĩa (Amalgamated Free Product):**  
Cho các nhóm $G$, $H$ với các homomorphisms $\phi: K \to G$, $\psi: K \to H$.

**Amalgamated product** $G *_K H$ được xây dựng bằng cách:
- Lấy free product $G * H$
- **Thêm các relations:** $\phi(k) = \psi(k)$ cho mọi $k \in K$

**Trực giác:** "Đồng nhất" các ảnh của $K$ trong $G$ và $H$. Điều này có nghĩa là nếu một phần tử $k \in K$ được ánh xạ đến $g \in G$ và $h \in H$, thì chúng ta đồng nhất $g$ và $h$ trong amalgamated product.

**Ký hiệu:** $G *_K H$ (amalgamate over $K$). Đây là một cách tổng quát hóa free product—thay vì chỉ đơn giản là kết hợp hai nhóm lại với nhau, chúng ta kết hợp chúng trong khi đồng nhất các phần tử từ nhóm con chung $K$.

---

### 2. Van Kampen's Theorem

**Định lý (Seifert-Van Kampen):**  
Cho $X$ là topological space, $A$, $B$ là các open subsets:
- **$X = A \cup B$** (cover $X$)
- **$A$, $B$, $A \cap B$ path-connected**
- **$x_0 \in A \cap B$** (basepoint trong intersection)

Khi đó:

$$
\pi_1(X, x_0) \cong \pi_1(A, x_0) *_{\pi_1(A \cap B, x_0)} \pi_1(B, x_0)
$$

**Amalgamation qua các inclusions:**
- $i_A: A \cap B \to A$ cảm ứng $(i_A)_*: \pi_1(A \cap B) \to \pi_1(A)$
- $i_B: A \cap B \to B$ cảm ứng $(i_B)_*: \pi_1(A \cap B) \to \pi_1(B)$

**Amalgamate over $\pi_1(A \cap B)$!** Đây là điểm quan trọng—chúng ta không chỉ đơn giản là lấy free product của $\pi_1(A)$ và $\pi_1(B)$, mà chúng ta amalgamate chúng qua fundamental group của intersection. Điều này phản ánh cách các loops trong intersection có thể được hiểu như các loops trong cả $A$ và $B$, và chúng ta cần đồng nhất các cách hiểu này.

---

**Góc nhìn Category Theory:**

Van Kampen nói rằng $\pi_1$ bảo toàn **pushouts**. Điều này có nghĩa là fundamental group của không gian được xây dựng như một pushout trong category của các topological spaces là pushout của các fundamental groups trong category của các groups.

```
π₁(A ∩ B) -----> π₁(A)
    |              |
    |              |
    ↓              ↓
  π₁(B)  -----> π₁(X)
```

Đây là một pushout diagram trong Grp (category của các groups). Điều này cho thấy một kết nối sâu sắc giữa topology và category theory—fundamental group là một functor bảo toàn pushouts.

---

### 3. Special Cases

**Trường hợp 1: $A \cap B$ Simply Connected**

Nếu $\pi_1(A \cap B) = \{e\}$ (tầm thường), thì:

$$
\pi_1(X) \cong \pi_1(A) * \pi_1(B)
$$

**Free product!** (Không cần amalgamation.) Đây là trường hợp đơn giản nhất—nếu intersection có fundamental group tầm thường, thì fundamental group của không gian tổng thể chỉ đơn giản là free product của các fundamental groups của các phần. Trực giác hình học là nếu intersection không có "lỗ" nào, thì các loops trong $A$ và $B$ không tương tác với nhau theo cách phức tạp.

---

**Trường hợp 2: $A$ hoặc $B$ Simply Connected**

Nếu $\pi_1(A) = \{e\}$, thì:

$$
\pi_1(X) \cong \pi_1(B) / N
$$

trong đó $N$ = normal subgroup được sinh bởi ảnh của $\pi_1(A \cap B)$. Điều này thường đơn giản hóa đáng kể việc tính toán—nếu một trong các phần có fundamental group tầm thường, thì fundamental group của không gian tổng thể chỉ là quotient của fundamental group của phần còn lại.

---

**Trường hợp 3: Wedge Sum**

$X = A \vee B$ (các không gian được nối tại một điểm duy nhất $x_0$), $A \cap B = \{x_0\}$.

$$
\pi_1(A \vee B) \cong \pi_1(A) * \pi_1(B)
$$

**Beautiful:** Wedge ↔ free product!

---

## 📊 Standard Applications

### Application 1: π₁(S¹) = ℤ

**Decomposition:**  
S¹ = A ∪ B where:
- A = S¹ \ {north pole} ≃ (0,1) contractible
- B = S¹ \ {south pole} ≃ (0,1) contractible
- A ∩ B = two arcs ≃ (0,1) ⊔ (0,1) (two contractible components)

**Problem:** A ∩ B not path-connected! Modified Van Kampen needed.

---

**Better decomposition:**  
Use slightly different A, B ensuring A ∩ B path-connected.

**Result (sketch):**  
Careful analysis ⇒ π₁(S¹) ≅ ℤ.

**Remark:** Covering space method easier for S¹! Van Kampen more useful for complex spaces.

---

### Application 2: π₁(Figure-Eight) = ℤ * ℤ

**X = S¹ ∨ S¹** (two circles joined at point x₀).

**Decomposition:**  
- A = slightly thickened first circle
- B = slightly thickened second circle
- A ∩ B = small neighborhood of x₀ ≃ disk (contractible)

**Apply Van Kampen:**
- π₁(A) ≅ ℤ (first circle)
- π₁(B) ≅ ℤ (second circle)
- π₁(A ∩ B) = {e} (contractible)

**Result:**

$$
\pi_1(X) \cong \mathbb{Z} * \mathbb{Z}
$$

**Free group on two generators!**

![Figure-eight fundamental group](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f8/Wedge_of_circles.svg/400px-Wedge_of_circles.svg.png)  
*Figure-eight và generators - Nguồn concept*

---

### Application 3: π₁(Torus) = ℤ × ℤ

**T² = S¹ × S¹.**

**Decomposition:**  
Write T² = solid torus glued to solid torus along boundary.

Alternatively: CW complex structure (1 vertex, 2 edges, 1 face).

**Better approach:** Use product theorem.

**Van Kampen verification:**  
Decompose T² cleverly ⇒ π₁(T²) ≅ ℤ × ℤ (abelian!).

**Key:** Commutator relation [a,b] = 1 from attaching 2-cell.

---

### Application 4: π₁(Σ_g) - Genus g Surface

**Σ_g = orientable surface genus g.**

**Decomposition:**  
Build from fundamental polygon (4g-gon with edges identified).

**Van Kampen application:**  
- Decompose systematically
- Track generators and relations

**Result:**

$$
\pi_1(\Sigma_g) = \langle a_1, b_1, \ldots, a_g, b_g \mid [a_1,b_1] \cdots [a_g,b_g] = 1 \rangle
$$

**2g generators, one relation (surface relation).**

**For g ≥ 2:** Non-abelian!

---

### Application 5: π₁(ℝP²) = ℤ/2ℤ

**ℝP² = projective plane.**

**Decomposition:**  
ℝP² = disk D² với boundary identified antipodally.

- A = slightly smaller disk (contractible)
- B = annulus around edge
- A ∩ B = annulus (≃ S¹)

**Van Kampen:**  
- π₁(A) = {e}
- π₁(B) ≅ ℤ (annulus ≃ S¹)
- π₁(A ∩ B) ≅ ℤ

Inclusion (A ∩ B) → B: identity on π₁.  
Inclusion (A ∩ B) → A: trivial.

**Amalgamation forces:** γ² = e in π₁(ℝP²).

**Result:** π₁(ℝP²) ≅ ℤ/2ℤ. ✓

---

### Application 6: Wedge of n Circles

**X = ⋁ᵢ₌₁ⁿ S¹** (n circles joined at point).

**Van Kampen (iteratively):**

$$
\pi_1\left(\bigvee_{i=1}^n S^1\right) \cong \mathbb{Z} * \mathbb{Z} * \cdots * \mathbb{Z} \quad (n \text{ times})
$$

**Free group F_n on n generators!**

**Generators:** One loop around each circle.

**Non-abelian for n ≥ 2.**

---

## 🧮 Proof Sketch

### 1. Key Ideas

**Theorem intuition:**  
Loops trong X can be written as:
- Segments trong A
- Segments trong B
- Transitions through A ∩ B

**Group structure:**  
- Elements from π₁(A) và π₁(B)
- Relations: those from A, B, and compatibility via A ∩ B

---

### 2. Construction

**Step 1:** Define map Φ: π₁(A) *_{π₁(A∩B)} π₁(B) → π₁(X).

Use inclusions j_A: A → X, j_B: B → X inducing homomorphisms.

**Step 2:** Show Φ well-defined (respects amalgamation).

**Step 3:** Show Φ surjective:  
Any loop γ in X can be subdivided into pieces in A, B.  
Each piece lifts to element of π₁(A) or π₁(B).

**Step 4:** Show Φ injective:  
If product = identity in π₁(X), can construct homotopy showing = identity in amalgamated product.

**Technical:** Requires careful analysis of homotopies respecting A, B.

**Conclusion:** Φ isomorphism. ✓ **QED**

---

## 🧠 Fundamental Papers & References

### Classic Works

1. **Herbert Seifert** - *"Konstruktion dreidimensionaler geschlossener Räume"* (1931)  
   *First version of theorem*

2. **Egbert van Kampen** - *"On the connection between the fundamental groups"* (1933)  
   *General formulation*

3. **Ronald Brown** - *"Groupoids and Van Kampen's theorem"* (1967)  
   *Modern categorical perspective*

### Textbooks

4. **Allen Hatcher** - *Algebraic Topology*, **§1.2: Van Kampen's Theorem**  
   *Best modern treatment, many examples*

5. **James R. Munkres** - *Topology*, **§70: Seifert-Van Kampen Theorem**  
   *Careful rigorous proof*

6. **William S. Massey** - *Algebraic Topology*, **Chapter 6**

7. **Glen E. Bredon** - *Topology and Geometry*, **Chapter II**

8. **Joseph J. Rotman** - *An Introduction to Algebraic Topology*, **Chapter 7**

---

## 🔗 Applications and Connections

### CW Complexes - Systematic Computation
**Building Spaces:** CW complexes built by attaching cells. Van Kampen computes π₁ inductively: attach n-cell ⇒ π₁ changes by adding relation.

### Knot Theory - Knot Groups
**Knot Complement:** K ⊆ S³ knot. Decompose S³ \ K via Van Kampen ⇒ compute knot group π₁(S³ \ K). Distinguishes knots!

### 3-Manifolds - Fundamental Groups
**Heegaard Splittings:** 3-manifold = two handlebodies glued. Van Kampen computes π₁ from gluing map.

### Robotics - Configuration Spaces
**Modular Robots:** Configuration space = product/union of simpler spaces. Van Kampen enables π₁ computation for motion planning.

### Group Theory - Amalgamated Products
**HNN Extensions:** Generalization of amalgamated products. Bass-Serre theory = algebraic analog of Van Kampen.

---

## Video tham khảo

- **xem trước** [Algebraic Topology 6: Seifert-Van Kampen Theorem](https://www.youtube.com/watch?v=pmNcHER9K9I) — Math at Andrews University, tiếng Anh. Phát biểu Seifert–van Kampen và cách dán nhóm cơ bản theo hai mảnh.
- [6. Applications and Proof of the van Kampen Theorem - Pierre Albin](https://www.youtube.com/watch?v=0msWLft-lT0) — Mat Neth, tiếng Anh. Pierre Albin chứng minh và áp dụng, sau khi phát biểu đã quen.

## 🧩 Exercises

### Understanding Statement

1. **Free Product:**  
   Compute ℤ * ℤ/2ℤ explicitly. List some elements. Is it abelian?

2. **Amalgamated Product:**  
   ℤ *_ℤ ℤ where both maps identity. What is this group? (Hint: ℤ.)

3. **Verify Hypothesis:**  
   Why need A, B, A ∩ B path-connected? Counterexample if not?

### Applications

4. **Figure-Eight:**  
   Detailed Van Kampen calculation for π₁(S¹ ∨ S¹) = ℤ * ℤ. Verify all steps.

5. **Three Circles:**  
   X = S¹ ∨ S¹ ∨ S¹. Use Van Kampen: π₁(X) = ℤ * ℤ * ℤ = F₃.

6. **Torus Computation:**  
   Use Van Kampen with appropriate decomposition to get π₁(T²) = ℤ².

### Surfaces

7. **Genus 2:**  
   Σ₂ (2-torus). Apply Van Kampen to get presentation ⟨a₁,b₁,a₂,b₂ | [a₁,b₁][a₂,b₂] = 1⟩.

8. **Klein Bottle:**  
   Use Van Kampen to compute π₁(K) = ⟨a,b | aba⁻¹b = 1⟩ (non-abelian).

9. **ℝP²:**  
   Detailed Van Kampen calculation showing π₁(ℝP²) = ℤ/2ℤ.

### CW Complexes

10. **Attach 2-cell:**  
    Start with X = S¹ (π₁ = ℤ). Attach 2-cell via loop γ² (wind twice).  
    Use Van Kampen: π₁ = ⟨a | a² = 1⟩ = ℤ/2ℤ.

11. **Dunce Hat:**  
    Triangle with all edges identified. Van Kampen shows contractible (π₁ = {e}).

12. **General CW:**  
    Explain how Van Kampen computes π₁ of any CW complex inductively.

### Advanced

13. **Pushout:**  
    Research categorical formulation: Van Kampen says π₁ preserves pushouts. Explain.

14. **Groupoids:**  
    Modern Van Kampen uses groupoids (not just groups). Read Brown's version briefly.

15. **Higher Van Kampen:**  
    Research higher-dimensional versions (Seifert-van Kampen for π_n). Much more complex!

### Comparison

16. **Three Methods:**  
    Compare computing π₁(S¹):  
    a) Covering space method  
    b) Van Kampen  
    c) Geometric argument  
    Which easiest?

17. **When to Use:**  
    For each method (covering, Van Kampen, homotopy equivalence), give space where it's best choice.

### Reflection

18. **Why Powerful?:**  
    Explain why Van Kampen so powerful. What types of spaces does it handle well?

19. **Limitations:**  
    Van Kampen doesn't help for every space. What are limitations?

20. **Group Theory Connection:**  
    Van Kampen theorem = pure group theory statement về amalgamated products. Explain connection topology ↔ algebra.

---

## 📚 Further Reading

- **Hatcher, §1.2:** Outstanding treatment with examples
- **Munkres, §70:** Rigorous proof
- **Massey, Chapter 6:** Comprehensive
- **Rotman, Chapter 7:** Detailed computations
- **Brown, "Topology and Groupoids":** Modern perspective

---

## 🎓 Summary

Trong bài này, chúng ta learned **Seifert-Van Kampen Theorem**—powerful decomposition method:

✅ **Statement:** π₁(X) ≅ π₁(A) *_{π₁(A∩B)} π₁(B) (amalgamated product)  
✅ **Special Cases:** Free product when A ∩ B simply connected  
✅ **Applications:** Figure-eight (ℤ * ℤ), surfaces, ℝP², CW complexes  
✅ **Wedge Sum:** π₁(A ∨ B) = π₁(A) * π₁(B)  
✅ **Systematic:** Algorithm for computing π₁  
✅ **Group Theory:** Free products, amalgamations central  

**Điểm chính:**
- Decompose space ⇒ compute π₁ from pieces
- Amalgamated product captures gluing
- Most versatile method (works for CW complexes)
- Pure algebra determines topology
- Proof uses pushout (category theory)

**Geometric intuition:**
- Break complex space into simple pieces
- Each piece contributes generators
- Intersection determines relations
- Algebraic combination = topological structure

**Practical wisdom:**
- Choose decomposition wisely (make A, B, A∩B simple)
- Simply connected intersection ⇒ free product
- Works excellently for CW complexes
- Combine with other methods when needed

**Chapter 06 Complete!** Chúng ta mastered:
- Homotopy và path homotopy
- Fundamental group π₁(X, x₀)
- Computing π₁ (examples, covering spaces)
- Van Kampen's theorem

**Tiếp theo:** Chapter 07 về **Homology Theory**—second algebraic invariant, more computable, detects all dimensional holes!

---

*"Van Kampen: divide and conquer, from topology to algebra."*

🎯 **Master Van Kampen! It's the systematic way to compute π₁.** 🎯

---

**Previous:** [Lecture 06.03: Covering Spaces](/contents/vi/topology-chapter06/06_03_Covering_Spaces/)  
**Next Chapter:** [Chapter 07: Homology Theory](/contents/vi/topology-chapter07/)
