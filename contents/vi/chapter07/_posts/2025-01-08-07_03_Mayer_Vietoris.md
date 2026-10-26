---
layout: post
title: "Lecture 07.03: Mayer-Vietoris Sequence"
lang: vi
lang-ref: lecture-07-03
chapter: 7
lecture: 3
categories: [chapter07]
tags: [mayer-vietoris, exact-sequence, homology-computations]
description: "Mayer-Vietoris Sequence: powerful computational tool via decomposition, long exact sequences, connecting homomorphisms"
---

**Divide and Conquer for Homology**

---

## 📖 Tổng quan

Chúng ta đã biết:
- **Van Kampen:** Tính toán $\pi_1(X)$ từ decomposition $X = A \cup B$—một công cụ mạnh mẽ để tính toán fundamental group
- **Cellular homology:** Cho CW complexes—một phương pháp tính toán homology cho các không gian có cấu trúc CW

**Cần gì nữa?** Một phương pháp tổng quát cho arbitrary spaces! Chúng ta cần một công cụ có thể tính toán homology của bất kỳ không gian nào, không chỉ các CW complexes.

> **Mayer-Vietoris Sequence = "Van Kampen cho homology"**

**Ý tưởng chính:** $X = A \cup B$ (cover) ⇒ long exact sequence liên kết:
- $H_n(A \cap B)$—homology của intersection
- $H_n(A) \oplus H_n(B)$—tổng trực tiếp của homology của các phần
- $H_n(X)$—homology của không gian tổng thể

**Cách mạng vì:**
- **Universal:** Hoạt động cho mọi không gian $X$, mọi decomposition—không cần cấu trúc đặc biệt
- **Powerful:** Giảm không gian phức tạp $X$ xuống các phần đơn giản hơn—chia để trị
- **Systematic:** Thuật toán qua exact sequences—một phương pháp có hệ thống để tính toán
- **Inductive:** Tính toán $H_n$ từ $H_{n-1}$ (connecting homomorphism)—cho phép tính toán quy nạp

![Mayer-Vietoris decomposition](https://upload.wikimedia.org/wikipedia/commons/thumb/9/93/Mayer-Vietoris.svg/500px-Mayer-Vietoris.svg.png)  
*Decomposing space for Mayer-Vietoris - Nguồn concept*

Trong bài học này, chúng ta sẽ khám phá Mayer-Vietoris sequence một cách có hệ thống. Chúng ta sẽ nghiên cứu **Exact sequences**—nền tảng đại số cho lý thuyết này. Chúng ta sẽ học **Mayer-Vietoris theorem**—phát biểu và chứng minh sketch. Chúng ta sẽ tìm hiểu **Connecting homomorphism $\partial$**—ý nghĩa hình học của nó. Chúng ta sẽ xem xét các **ví dụ** cụ thể như $S^n$, $T^2$, surfaces, $\mathbb{R}P^n$—những ví dụ này cho thấy sức mạnh của phương pháp. Chúng ta sẽ học về **Snake Lemma**—kỹ thuật chứng minh quan trọng. Cuối cùng, chúng ta sẽ xem xét các **ứng dụng** trong tính toán có hệ thống.

**Tại sao đây là kiến thức quan trọng?** Đây là **công cụ tính toán linh hoạt nhất**—Mayer-Vietoris sequence có thể được áp dụng cho nhiều loại không gian khác nhau. Nó **bổ sung** cho cellular homology (hoạt động mà không cần cấu trúc CW)—đây là một công cụ bổ sung mạnh mẽ. Nó **chứng minh các định lý** (không chỉ các ví dụ)—cho phép chúng ta chứng minh các kết quả tổng quát. Cuối cùng, nó là **nền tảng** cho spectral sequences (advanced)—một công cụ nâng cao trong topology đại số.

---

## 🔗 Exact Sequences Review

### 1. Definition

**Định nghĩa (Exact Sequence):**  
Một dãy các abelian groups và các homomorphisms:

$$
\cdots \to A_{n+1} \xrightarrow{f_{n+1}} A_n \xrightarrow{f_n} A_{n-1} \to \cdots
$$

là **exact** nếu:

$$
\text{im}(f_{n+1}) = \ker(f_n) \quad \forall n
$$

**"Output của map trước = kernel của map sau."** Trực giác hình học là một exact sequence là một dãy các groups và maps sao cho image của mỗi map bằng kernel của map tiếp theo—điều này đảm bảo rằng thông tin được "bảo toàn" qua dãy.

---

**Các ví dụ:**

**Short exact sequence:**

$$
0 \to A \xrightarrow{f} B \xrightarrow{g} C \to 0
$$

Exactness ngụ ý:
- $f$ injective ($\ker f = 0$)—$f$ là đơn ánh
- $g$ surjective ($\text{im } g = C$)—$g$ là toàn ánh
- $\text{im } f = \ker g$ (middle exactness)—image của $f$ bằng kernel của $g$

**Trực giác:** $B$ "kết hợp" $A$ và $C$. Điều này có nghĩa là $B$ có thể được hiểu như một cách kết hợp $A$ và $C$ lại với nhau, với $A$ được nhúng vào $B$ và $B$ được ánh xạ lên $C$.

---

**Split exact sequence:**  
Tồn tại section $s: C \to B$ với $g \circ s = id$.

Khi đó: $B \cong A \oplus C$ (direct sum). Đây là một trường hợp đặc biệt—nếu exact sequence "split", thì $B$ là tổng trực tiếp của $A$ và $C$.

---

### 2. Long Exact Sequence

**Chain complexes:**  
C_•: ... → C_{n+1} → C_n → C_{n-1} → ...

Short exact sequence of chain complexes induces **long exact sequence in homology:**

$$
\cdots \to H_n(A) \to H_n(B) \to H_n(C) \xrightarrow{\partial} H_{n-1}(A) \to \cdots
$$

**Connecting homomorphism ∂** = key!

---

## 🎯 Mayer-Vietoris Theorem

### 1. Statement

**Định lý (Mayer-Vietoris):**  
Cho $X$ là topological space, $A$, $B$ là các open subsets với $X = A \cup B$.

**Long exact sequence:**

$$
\cdots \to H_n(A \cap B) \xrightarrow{\phi_n} H_n(A) \oplus H_n(B) \xrightarrow{\psi_n} H_n(X) \xrightarrow{\partial_n} H_{n-1}(A \cap B) \to \cdots
$$

**Các maps:**
- **$\phi_n([c]) = ([c], -[c])$** (include trong $A$ và $B$ với dấu)—map này nhúng homology của intersection vào tổng trực tiếp của homology của các phần, với dấu trừ để đảm bảo exactness
- **$\psi_n([a], [b]) = [a] + [b]$** (sum trong $X$)—map này cộng các homology classes từ các phần để tạo thành homology class trong không gian tổng thể
- **$\partial_n$ = connecting homomorphism** (sẽ được giải thích)—map này liên kết homology ở chiều $n$ với homology ở chiều $n-1$

---

**Exactness:** Tại mỗi vị trí, image = kernel. Điều này đảm bảo rằng dãy là exact—thông tin được "bảo toàn" qua dãy.

**Giải thích:** Liên kết homology của:
- **$A \cap B$:** Vùng overlap—phần giao của hai tập mở
- **$A \oplus B$:** Tổng trực tiếp (các phần riêng biệt)—homology của các phần được xem xét riêng biệt
- **$X = A \cup B$:** Toàn bộ không gian—homology của không gian tổng thể

---

### 2. Connecting Homomorphism ∂

**Xây dựng hình học:**

Lấy $[\alpha] \in H_n(X)$.

**Bước 1:** Biểu diễn $\alpha$ = chain trong $X$.

**Bước 2:** Subdivide: viết $\alpha = a + b$ ($a$ trong $A$, $b$ trong $B$).  
Không duy nhất, nhưng $\partial\alpha = 0$ trong $X$. Trực giác hình học là chúng ta chia chain thành hai phần, mỗi phần nằm trong một tập mở.

**Bước 3:** $\partial a = -\partial b$ (trong $A \cap B$).  
(Vì $\partial(a+b) = 0$ trong $X$) Điều này có nghĩa là boundaries của các phần triệt tiêu lẫn nhau trong intersection.

**Bước 4:** $\partial([\alpha]) = [\partial a] \in H_{n-1}(A \cap B)$.

**Điểm quan trọng:** Mặc dù $\alpha$ đóng, các phần $a$, $b$ KHÔNG đóng, nhưng boundaries tương thích! Đây là điểm quan trọng—connecting homomorphism đo lường cách các phần không đóng một cách riêng biệt, nhưng boundaries của chúng tương thích trong intersection.

---

**Trực giác:** $\partial$ đo lường "cách các phần không đóng một cách riêng biệt." Đây là ý nghĩa hình học của connecting homomorphism—nó đo lường cách một cycle trong không gian tổng thể được "chia" thành các phần trong các tập mở, và cách các boundaries của các phần này tương tác trong intersection.

---

## 🧮 Examples

### Example 1: Computing H_n(S²)

**Decomposition:**  
S² = U ∪ V where:
- U = northern hemisphere + equator (≃ D² contractible)
- V = southern hemisphere + equator (≃ D² contractible)
- U ∩ V = equator (≃ S¹)

**Homology:**
- H_n(U) = H_n(V) = 0 (n > 0), H₀ = ℤ
- H_n(U ∩ V) = H_n(S¹) = ℤ (n=0,1), 0 else

---

**Mayer-Vietoris (n=2):**

$$
H_2(U) \oplus H_2(V) \to H_2(S^2) \xrightarrow{\partial} H_1(U \cap V)
$$

$$
0 \to H_2(S^2) \xrightarrow{\partial} \mathbb{Z}
$$

Exactness: ∂ must be 0 (to have ker ∂ = H₂(S²)).

Next term: H₁(U) ⊕ H₁(V) = 0.

Exactness: im ∂ = 0.

**Conclusion:** H₂(S²) ≅ ℤ. ✓

---

**Mayer-Vietoris (n=1):**

$$
H_1(S^1) \to H_1(U) \oplus H_1(V) \to H_1(S^2) \to H_0(S^1)
$$

$$
\mathbb{Z} \to 0 \to H_1(S^2) \to \mathbb{Z}
$$

Exactness: H₁(S²) = 0. ✓

**Result:** H₀(S²) = ℤ, H₁ = 0, H₂ = ℤ. ✓

---

### Example 2: Computing H_n(Sⁿ) Inductively

**Induction:**

**Base:** H_*(S⁰) known.

**Step:** Assume H_*(Sⁿ⁻¹) known. Decompose Sⁿ as above.

**Mayer-Vietoris:**  
H_n(Sⁿ) → H_{n-1}(Sⁿ⁻¹).

Careful analysis của exact sequence ⇒ H_n(Sⁿ) ≅ ℤ. ✓

**Recursive algorithm!**

---

### Example 3: Torus T²

**Decomposition:**  
T² = S¹ × S¹.

Alternative: T² = (solid torus) ∪ (solid torus).

**Choose:** A = T² \ {meridian disk}, B = T² \ {longitudinal disk}.  
Both ≃ S¹ (deformation retract).  
A ∩ B ≃ S¹ ∨ S¹.

**Mayer-Vietoris (n=2):**

$$
H_2(A) \oplus H_2(B) \to H_2(T^2) \to H_1(A \cap B)
$$

$$
0 \to H_2(T^2) \to \mathbb{Z}^2
$$

Analysis: H₂(T²) ≅ ℤ. ✓

**Similar for H₁:** Get ℤ². ✓

---

### Example 4: Computing H_n(ℝP²)

**Decomposition:**  
ℝP² = D² với antipodal boundary identification.

Let:
- A = interior (≃ ℝ² contractible)
- B = neighborhood of boundary (≃ Möbius strip)
- A ∩ B ≃ S¹

**Mayer-Vietoris reveals:** H₁(ℝP²) = ℤ/2ℤ (torsion!).

---

## 🔍 Proof Sketch

### 1. Short Exact Sequence của Chain Complexes

**Chain groups:**

$$
C_n(A \cap B) \xrightarrow{\alpha} C_n(A) \oplus C_n(B) \xrightarrow{\beta} C_n(X)
$$

**Maps:**
- α(c) = (i_A(c), -i_B(c)) (include with sign)
- β(a, b) = j_A(a) + j_B(b) (sum)

**Exactness:** Verify im α = ker β (subdivision argument).

---

### 2. Snake Lemma

**Snake Lemma:** Short exact sequence of chain complexes induces long exact sequence in homology với connecting homomorphism ∂.

**Diagram chasing:** Construct ∂ explicitly.

---

### 3. Result

**Long exact Mayer-Vietoris sequence.** ✓

**Full proof:** See Hatcher §2.2 or Bredon Chapter IV.

---

## 🧠 Fundamental Papers & References

### Classic Works

1. **Leopold Vietoris** - *"Über den höheren Zusammenhang kompakter Räume"* (1927)  
   *Early formulation*

2. **Walther Mayer** - *"Über abstrakte Topologie"* (1929)  
   *General version*

3. **Solomon Eilenberg, Norman Steenrod** - *"Foundations of Algebraic Topology"* (1952)  
   *Modern systematic treatment*

### Textbooks

4. **Allen Hatcher** - *Algebraic Topology*, **§2.2: Mayer-Vietoris Sequence**

5. **Glen E. Bredon** - *Topology and Geometry*, **Chapter IV**

6. **James R. Munkres** - *Elements of Algebraic Topology*, **Chapter 4**

7. **Edwin H. Spanier** - *Algebraic Topology*, **Chapter 4**

---

## 🔗 Applications

### Computational Topology
**Algorithm:** Decompose complicated space ⇒ compute homology inductively via Mayer-Vietoris.

### Robotics - Motion Planning
**Configuration Space:** Decompose complex configuration space. Compute homology to understand connectivity, holes, obstructions.

### Data Science - TDA
**Persistent Homology:** Mayer-Vietoris enables efficient computation on large datasets. Union of patches ⇒ global homology.

---

## Video tham khảo

- **xem trước** [Algebraic Topology 18: Mayer-Vietoris](https://www.youtube.com/watch?v=LdJlbh7Tpls) — Math at Andrews University, tiếng Anh. Dãy Mayer–Vietoris: dán đồng điều của hai mảnh và của giao.
- [20. Euler Characteristic; Mayer-Vietoris Sequence - Pierre Albin](https://www.youtube.com/watch?v=W1RVwbeQy48) — Mat Neth, tiếng Anh. Pierre Albin: đặc trưng Euler rồi dãy Mayer–Vietoris, đúng cặp công cụ của bài.

## 🧩 Exercises

### Exact Sequences

1. **Verify Exactness:**  
   0 → ℤ →^(×2) ℤ →^(mod 2) ℤ/2ℤ → 0. Check at each position.

2. **Split:**  
   When does 0 → A → B → C → 0 split? Give example and counterexample.

### Mayer-Vietoris

3. **S²:**  
   Verify full Mayer-Vietoris sequence for S² = U ∪ V (hemispheres). Check all H_n.

4. **S³:**  
   Decompose S³ similar to S². Compute H_n(S³) = ℤ, 0, 0, ℤ.

### Computations

5. **Figure-Eight:**  
   X = S¹ ∨ S¹. Decompose và use Mayer-Vietoris to get H₁ = ℤ².

6. **Genus 2 Surface:**  
   Compute H_n(Σ₂) via Mayer-Vietoris.

### Torus

7. **Product:**  
   T² = S¹ × S¹. Try decomposition T² = (S¹ × D¹) ∪ (S¹ × D¹).  
   Use Mayer-Vietoris: H₁(T²) = ℤ².

### Advanced

8. **Klein Bottle:**  
   Compute H_n(Klein bottle) using Mayer-Vietoris.  
   (Answer: H₁ = ℤ ⊕ ℤ/2ℤ)

9. **ℝP³:**  
   Decompose và compute H_n.

10. **Complement:**  
    X = S³ \ (knot K). Use Mayer-Vietoris to relate H_n(X) to knot properties.

### Connecting Homomorphism

11. **Geometric Understanding:**  
    For S² decomposition, describe ∂: H₂(S²) → H₁(S¹) geometrically.

12. **Compute:**  
    Explicit element [α] ∈ H₂(S²), compute ∂([α]) step by step.

### Long Exact Sequence

13. **Deduce Relations:**  
    From exactness at H₁(X) in Mayer-Vietoris, derive relation between ranks.

14. **Betti Numbers:**  
    Use Mayer-Vietoris to prove: β_n(X) ≤ β_n(A) + β_n(B) + β_{n-1}(A∩B).

### Applications

15. **CW Complex:**  
    Compare Mayer-Vietoris vs cellular homology for T². Which easier?

16. **Union:**  
    X = union of two solid tori glued along boundary tori. Compute H_n(X).

### Reflection

17. **Van Kampen vs Mayer-Vietoris:**  
    Compare similarities and differences.

18. **Why Exact?:**  
    Explain why Mayer-Vietoris gives exact sequence (not just random maps).

19. **Connecting ∂:**  
    Why does ∂ decrease dimension by 1?

20. **Power:**  
    Give example where Mayer-Vietoris essential (can't easily use cellular homology).

---

## 📚 Further Reading

- **Hatcher, §2.2:** Best modern exposition với detailed examples
- **Bredon, Chapter IV:** Comprehensive advanced treatment
- **Munkres, Elements:** Careful proofs
- **Spanier:** Encyclopedic reference

---

## 🎓 Summary

**Mayer-Vietoris = powerful computational tool:**

✅ **Decomposition:** X = A ∪ B ⇒ relate homologies  
✅ **Long exact sequence:** ... → H_n(A∩B) → H_n(A)⊕H_n(B) → H_n(X) → ...  
✅ **Connecting ∂:** Measures how pieces fail to close  
✅ **Examples:** Spheres, torus, surfaces systematically  
✅ **Inductive:** Compute H_n from simpler spaces  
✅ **Universal:** Works for any decomposition  
✅ **Foundation:** Exact sequences central to algebraic topology  

**Key insight:**
- Divide complex space into simple pieces
- Exact sequence encodes gluing information
- Inductively determine H_n(X)
- Complements cellular homology (different perspective)

**Practical wisdom:**
- Choose decomposition with A, B, A∩B as simple as possible
- Use contractible pieces when possible
- Connecting homomorphism often vanishes (simplifies sequence)
- Combine with homotopy equivalence for maximum power

**Tiếp theo:** Cohomology—dual theory with rich algebraic structure!

---

**Previous:** [Lecture 07.02: Homology Computations](/contents/vi/topology-chapter07/07_02_Homology_Computations/)  
**Next:** [Lecture 07.04: Cohomology Introduction](/contents/vi/topology-chapter07/07_04_Cohomology_Introduction/)
