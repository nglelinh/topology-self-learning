---
layout: post
title: "Lecture 07.01: Singular Homology"
lang: vi
lang-ref: lecture-07-01
chapter: 7
lecture: 1
categories: [chapter07]
tags: [singular-homology, singular-simplices, functoriality]
description: "Singular homology: definition cho arbitrary spaces, functoriality, homotopy invariance - universal homology theory"
---

**Homology for Any Space - Functorial and Homotopy Invariant**

---

## 📖 Tổng quan

**Simplicial homology** mạnh mẽ nhưng có hạn chế:
> **Yêu cầu triangulation!**

Không phải mọi không gian đều có triangulation:
- Các tập con tùy ý của $\mathbb{R}^n$
- Các không gian hàm
- Các không gian vô hạn chiều
- Các không gian "wild" (không có cấu trúc đẹp)

**Singular homology giải quyết vấn đề này!**

> **$H_n(X)$ được định nghĩa cho BẤT KỲ topological space $X$.**

**Ý tưởng chính:** Thay vì triangulate $X$, chúng ta xem xét TẤT CẢ các ánh xạ liên tục $\Delta^n \to X$. Đây là một cách tiếp cận hoàn toàn khác—thay vì chia không gian thành các simplices, chúng ta xem xét tất cả các cách có thể ánh xạ standard simplex vào không gian.

**Cách mạng vì:**
- **Universal:** Hoạt động cho mọi không gian—không cần triangulation
- **Functorial:** $f: X \to Y$ cảm ứng $f_*: H_n(X) \to H_n(Y)$—mọi ánh xạ liên tục đều cảm ứng một homomorphism trên homology groups
- **Homotopy invariant:** $X \simeq Y$ ⇒ $H_n(X) \cong H_n(Y)$—homology groups chỉ phụ thuộc vào homotopy type
- **Coincides:** Đối với simplicial complexes, singular homology = simplicial homology—hai cách tiếp cận cho cùng kết quả
- **Powerful:** Nền tảng cho modern algebraic topology—đây là định nghĩa chuẩn được sử dụng trong topology hiện đại

![Singular simplices](https://upload.wikimedia.org/wikipedia/commons/thumb/9/9c/Singular_simplex.svg/400px-Singular_simplex.svg.png)  
*Singular simplices mapping to space - Nguồn concept*

Trong bài học này, chúng ta sẽ khám phá singular homology một cách có hệ thống. Chúng ta sẽ nghiên cứu **Standard simplex $\Delta^n$**—universal template mà chúng ta sẽ sử dụng để ánh xạ vào các không gian khác nhau. Chúng ta sẽ định nghĩa **Singular simplices**—các ánh xạ liên tục $\Delta^n \to X$ từ standard simplex vào không gian $X$. Chúng ta sẽ xây dựng **Singular chains $C_n(X)$**—free abelian group trên các singular simplices. Chúng ta sẽ định nghĩa **Boundary operator $\partial$**—được cảm ứng từ các face maps của standard simplex. Chúng ta sẽ tính toán **Singular homology $H_n(X)$**—$\ker(\partial) / \text{im}(\partial)$, các nhóm này phát hiện các lỗ $n$-chiều trong không gian. Chúng ta sẽ nghiên cứu **Functoriality**—cách các ánh xạ liên tục cảm ứng các homomorphisms trên homology groups. Cuối cùng, chúng ta sẽ chứng minh **Homotopy invariance**—tính chất cơ bản cho phép chúng ta tính toán homology bằng cách sử dụng homotopy equivalence.

**Tại sao đây là kiến thức quan trọng?** Đây là **định nghĩa chuẩn** trong modern topology—singular homology là cách tiếp cận được sử dụng rộng rãi nhất trong topology đại số hiện đại. Đây là **lý thuyết homology tổng quát nhất**—nó hoạt động cho mọi không gian tô-pô. Nó **có thể tính toán được** thông qua CW complexes—chúng ta có thể tính toán singular homology bằng cách sử dụng các kỹ thuật từ CW complexes. Cuối cùng, **tất cả các định lý chính** đều sử dụng singular homology—đây là công cụ chuẩn trong topology đại số.

---

## 🔺 Standard Simplex

### 1. Definition

**Định nghĩa (Standard n-Simplex):**

$$
\Delta^n = \left\{(t_0, \ldots, t_n) \in \mathbb{R}^{n+1} : t_i \geq 0, \sum_{i=0}^n t_i = 1\right\}
$$

**Vertices:** 
- $e_0 = (1, 0, \ldots, 0)$
- $e_1 = (0, 1, 0, \ldots, 0)$
- $\ldots$
- $e_n = (0, \ldots, 0, 1)$

**Barycentric coordinates:** Điểm $(t_0, \ldots, t_n)$ = weighted average của vertices. Trực giác hình học là mỗi điểm trong standard simplex có thể được biểu diễn như một tổ hợp lồi của các vertices, với các hệ số $t_i$ là các trọng số.

---

**Các ví dụ:**

**$\Delta^0$:** Single point $\{(1)\}$—một điểm duy nhất trong $\mathbb{R}^1$.

**$\Delta^1$:** Interval $[0,1]$ = $\{(t, 1-t) : t \in [0,1]\}$—một đoạn thẳng từ $(1,0)$ đến $(0,1)$ trong $\mathbb{R}^2$.

**$\Delta^2$:** Triangle = $\{(t_0,t_1,t_2) : t_i \geq 0, \sum t_i = 1\}$ trong $\mathbb{R}^3$—một tam giác với các đỉnh $(1,0,0)$, $(0,1,0)$, $(0,0,1)$.

**$\Delta^3$:** Tetrahedron trong $\mathbb{R}^4$—một tứ diện với các đỉnh là các vectors đơn vị trong $\mathbb{R}^4$.

---

### 2. Face Maps

**Định nghĩa (i-th Face Map):**

$$
\delta_i : \Delta^{n-1} \to \Delta^n
$$

**Formula:** Insert 0 at position i:

$$
\delta_i(t_0, \ldots, t_{n-1}) = (t_0, \ldots, t_{i-1}, 0, t_i, \ldots, t_{n-1})
$$

**Ý nghĩa hình học:** $\delta_i$ nhúng $(n-1)$-simplex như i-th face (bỏ qua vertex $e_i$). Trực giác hình học là face map $\delta_i$ ánh xạ standard $(n-1)$-simplex vào face đối diện với vertex $e_i$ của standard $n$-simplex.

---

**Ví dụ ($n=2$):**

$\Delta^1 \to \Delta^2$ (ba face maps):

- $\delta_0$: $(t, 1-t) \mapsto (0, t, 1-t)$ [opposite $e_0$]—ánh xạ edge vào cạnh đối diện với vertex $(1,0,0)$
- $\delta_1$: $(t, 1-t) \mapsto (t, 0, 1-t)$ [opposite $e_1$]—ánh xạ edge vào cạnh đối diện với vertex $(0,1,0)$
- $\delta_2$: $(t, 1-t) \mapsto (t, 1-t, 0)$ [opposite $e_2$]—ánh xạ edge vào cạnh đối diện với vertex $(0,0,1)$

**Ba edges của tam giác!** Đây là ba cách nhúng edge vào tam giác—mỗi cách tương ứng với một cạnh của tam giác.

---

### 3. Degeneracy Maps

(Used in simplicial sets theory—advanced topic)

**sᵢ: Δⁿ → Δⁿ⁻¹** collapses edge.

Not needed for basic homology.

---

## 🔗 Singular Simplices

### 1. Definition

**Định nghĩa (Singular n-Simplex):**  
**Singular n-simplex in $X$** = continuous map:

$$
\sigma : \Delta^n \to X
$$

**Bất kỳ ánh xạ liên tục nào!** Đây là điểm quan trọng—chúng ta không yêu cầu ánh xạ phải là embedding hoặc có tính chất đặc biệt nào khác, chỉ cần liên tục.

**Trực giác:** $\sigma$ "wraps" standard $n$-simplex quanh $X$ (có thể một cách "wild"). Hãy tưởng tượng chúng ta có một standard simplex làm "khuôn mẫu", và chúng ta có thể "bóp méo" nó một cách liên tục để ánh xạ vào không gian $X$.

---

**Các ví dụ:**

**$X = S^1$:**
- **Constant map:** $\sigma(\Delta^n)$ = single point—ánh xạ toàn bộ simplex vào một điểm
- **Wrapping once:** $\sigma: \Delta^1 \to S^1$ traverses circle once—ánh xạ edge một lần quanh hình tròn
- **Wrapping twice:** $\sigma$ traverses twice—ánh xạ edge hai lần quanh hình tròn
- **Backwards:** $\sigma$ traverses clockwise—ánh xạ edge theo chiều ngược lại

**Vô số singular simplices!** Đây là một điểm quan trọng—có vô số cách ánh xạ standard simplex vào hình tròn, và chúng ta xem xét tất cả chúng.

---

**$X = \mathbb{R}^n$:**

Mọi simplex $[v_0, \ldots, v_n] \subseteq \mathbb{R}^n$ cho một singular simplex:

$\sigma(t_0, \ldots, t_n) = \sum t_i v_i$ (affine map).

Bao gồm simplicial complexes như một trường hợp đặc biệt. Điều này có nghĩa là mọi geometric simplex trong simplicial homology đều có thể được xem như một singular simplex, và do đó simplicial homology là một trường hợp đặc biệt của singular homology.

---

### 2. Geometric vs Singular

**Geometric simplices (simplicial homology):**
- Actual subsets của không gian $X$—các simplices là các tập con thực sự của không gian
- $X$ phải là simplicial complex—không gian phải có cấu trúc simplicial
- Finite cho finite complexes—số lượng simplices là hữu hạn

**Singular simplices:**
- Continuous maps $\Delta^n \to X$—các ánh xạ liên tục từ standard simplex vào không gian
- Hoạt động cho BẤT KỲ không gian $X$—không cần cấu trúc đặc biệt
- Thường là vô hạn (ngay cả đối với các không gian hữu hạn!)—có vô số cách ánh xạ standard simplex vào một không gian

**Key insight:** Vô số singular simplices là OK vì chúng ta chỉ quan tâm đến các tổng hình thức (chains) và cấu trúc đại số. Điều này có nghĩa là mặc dù có vô số singular simplices, chúng ta chỉ làm việc với các tổng hữu hạn của chúng, và điều này đủ để xác định homology groups.

---

## 🔗 Singular Chain Complex

### 1. Chain Groups

**Định nghĩa (Singular Chain Group):**

$$
C_n(X) = \text{free abelian group on singular } n\text{-simplices in } X
$$

**Các phần tử:** Các tổng hình thức:

$$
c = \sum_{i=1}^k m_i \sigma_i, \quad m_i \in \mathbb{Z}, \sigma_i : \Delta^n \to X
$$

**Tổng hữu hạn** (mặc dù có vô số $\sigma_i$ tồn tại). Điều này có nghĩa là mỗi chain là một tổ hợp tuyến tính hữu hạn của các singular simplices với các hệ số nguyên. Trực giác hình học là một chain là một "tổ hợp tuyến tính" của các cách ánh xạ standard simplex vào không gian.

---

**Các tính chất:**
- **Free abelian:** Không có relations (basis = tất cả các singular simplices). Điều này có nghĩa là mỗi singular simplex là một generator độc lập, và không có relations nào giữa chúng.
- **Functorial:** $f: X \to Y$ cảm ứng $C_n(f): C_n(X) \to C_n(Y)$. Đây là một tính chất quan trọng—mọi ánh xạ liên tục đều cảm ứng một homomorphism trên chain groups.
- **Large:** Thường được sinh bởi vô số generators (ngay cả đối với các không gian đơn giản $X$). Đây là một điểm khác biệt so với simplicial homology—chain groups thường rất lớn, nhưng điều này không phải là vấn đề vì chúng ta chỉ làm việc với các tổng hữu hạn.

---

### 2. Boundary Operator

**Định nghĩa (Boundary):**  
Cho singular simplex $\sigma: \Delta^n \to X$.

**i-th face:** $\sigma \circ \delta_i: \Delta^{n-1} \to \Delta^n \to X$. Đây là composition của singular simplex với face map—chúng ta ánh xạ standard $(n-1)$-simplex vào face thứ $i$ của standard $n$-simplex, sau đó ánh xạ vào $X$.

**Boundary:**

$$
\partial_n \sigma = \sum_{i=0}^n (-1)^i (\sigma \circ \delta_i)
$$

**Alternating sum của faces!** Trực giác hình học là boundary của một singular simplex là tổng alternating của tất cả các faces của nó, với các dấu được chọn để đảm bảo orientation nhất quán.

**Mở rộng tuyến tính:** $\partial(\sum m_i \sigma_i) = \sum m_i \partial\sigma_i$. Điều này có nghĩa là boundary operator là một homomorphism—nó tương thích với phép cộng và phép nhân với số nguyên.

---

**Ví dụ ($n=1$):**  
$\sigma: \Delta^1 \to X$.

$$
\partial \sigma = \sigma \circ \delta_1 - \sigma \circ \delta_0
$$

$\delta_1(0) = e_1$, $\delta_0(0) = e_0$.

$$
\partial \sigma = \sigma(e_1) - \sigma(e_0)
$$

**(Endpoint - starting point)**—giống như geometric simplices! Trực giác hình học là boundary của một singular 1-simplex (một path) là điểm cuối trừ đi điểm đầu—điều này hoàn toàn giống với cách chúng ta tính boundary của một geometric edge trong simplicial homology.

---

### 3. Key Property: ∂² = 0

**Định lý:** $\partial_{n-1} \circ \partial_n = 0$.

**Chứng minh:** Composition của các face maps:

$$
\delta_i \circ \delta_j = \delta_{j+1} \circ \delta_i \quad (i \leq j)
$$

Khi mở rộng $\partial(\partial\sigma)$, mỗi composition xuất hiện hai lần với các dấu đối nhau. Điều này xảy ra vì khi chúng ta tính boundary của boundary, chúng ta phải đi qua hai face maps, và các cách đi qua chúng xuất hiện theo cặp với các dấu đối nhau.

**Cancellation ⇒ $\partial^2 = 0$.** ✓ Đây là tính chất cơ bản cho phép chúng ta định nghĩa homology groups—nếu không có tính chất này, chúng ta không thể định nghĩa cycles và boundaries một cách nhất quán.

**Cùng cấu trúc đại số như simplicial homology!** Điều này có nghĩa là mặc dù singular homology được định nghĩa một cách khác, nó có cùng cấu trúc đại số cơ bản như simplicial homology—boundary operator vẫn thỏa mãn $\partial^2 = 0$, và homology groups được định nghĩa theo cùng cách.

---

## 📊 Singular Homology Groups

### 1. Definition

**Chain complex:**

$$
\cdots \to C_n(X) \xrightarrow{\partial_n} C_{n-1}(X) \to \cdots \to C_0(X) \to 0
$$

**Cycles:** $Z_n(X) = \ker(\partial_n)$—các chains không có boundary

**Boundaries:** $B_n(X) = \text{im}(\partial_{n+1})$—các chains là boundaries của một chain ở chiều cao hơn

**Homology:**

$$
H_n(X) = \frac{Z_n(X)}{B_n(X)}
$$

**Cùng định nghĩa như simplicial!** Điều này có nghĩa là mặc dù cách xây dựng khác nhau, định nghĩa của homology groups là hoàn toàn giống nhau—chúng ta vẫn lấy quotient của cycles modulo boundaries.

---

**Các tính chất:**

1. **Abelian groups:** $H_n(X)$ luôn luôn abelian—đây là một lợi thế lớn so với fundamental group
2. **Homotopy invariant:** $X \simeq Y$ ⇒ $H_n(X) \cong H_n(Y)$—homology groups chỉ phụ thuộc vào homotopy type
3. **Functorial:** $f: X \to Y$ cảm ứng $f_*: H_n(X) \to H_n(Y)$—mọi ánh xạ liên tục đều cảm ứng một homomorphism trên homology groups
4. **Dimension axiom:** $H_n(\text{point}) = \mathbb{Z}$ ($n=0$), $0$ ($n>0$)—điểm có một thành phần liên thông và không có lỗ ở chiều cao hơn

---

### 2. Functoriality

**Định lý (Functoriality):**  
Cho ánh xạ liên tục $f: X \to Y$ cảm ứng:

$$
f_* : H_n(X) \to H_n(Y)
$$

**Xây dựng:**  
Cho singular simplex $\sigma: \Delta^n \to X$.  
Compose: $f \circ \sigma: \Delta^n \to Y$. Trực giác hình học là chúng ta ánh xạ singular simplex từ $X$ sang $Y$ bằng cách compose với $f$.

Chain map: $C_n(f)(\sigma) = f \circ \sigma$ (mở rộng tuyến tính). Điều này có nghĩa là chúng ta ánh xạ mỗi singular simplex trong $X$ thành một singular simplex trong $Y$ bằng cách compose với $f$.

**Commutes với boundary:** $\partial(f \circ \sigma) = f \circ (\partial\sigma)$. Đây là một tính chất quan trọng—boundary operator tương thích với composition, và điều này đảm bảo rằng chain map cảm ứng một map trên homology groups.

Induces map on homology: $f_*[c] = [f(c)]$. Điều này có nghĩa là nếu $c$ là một cycle trong $X$, thì $f(c)$ là một cycle trong $Y$, và map trên homology groups được định nghĩa bằng cách ánh xạ homology class của $c$ thành homology class của $f(c)$.

---

**Các tính chất:**
- **$(f \circ g)_* = f_* \circ g_*$**—composition của các ánh xạ cảm ứng composition của các homomorphisms
- **$id_* = id$**—ánh xạ đồng nhất cảm ứng ánh xạ đồng nhất trên homology groups

**Category theory:** $H_n$ = functor Top → Ab. Đây là một khái niệm quan trọng trong category theory—homology groups không chỉ là các nhóm được gán cho mỗi không gian, mà còn là một functor từ category của các topological spaces đến category của các abelian groups.

---

### 3. Homotopy Invariance

**Định lý (Homotopy Invariance):**  
Nếu $f, g: X \to Y$ đồng luân, thì $f_* = g_*: H_n(X) \to H_n(Y)$.

**Hệ quả:** $X \simeq Y$ ⇒ $H_n(X) \cong H_n(Y)$.

**Homology = homotopy invariant!** Đây là một tính chất cực kỳ mạnh mẽ—homology groups chỉ phụ thuộc vào homotopy type của không gian, không phụ thuộc vào chi tiết cụ thể của cấu trúc tô-pô. Điều này cho phép chúng ta tính toán homology bằng cách sử dụng homotopy equivalence để đơn giản hóa không gian.

---

**Chứng minh sketch:**  
Cho homotopy $F: X \times [0,1] \to Y$ từ $f$ đến $g$.

Xây dựng **chain homotopy** $P: C_n(X) \to C_{n+1}(Y)$:

$$
\partial P + P \partial = g_\# - f_\#
$$

Tại mức homology: $\partial P[c] + P\partial[c] = g_*[c] - f_*[c]$.

Vì $[c]$ là cycle: $\partial[c] = 0$.  
$\partial P[c]$ là boundary, nên triệt tiêu trong homology. Điều này có nghĩa là $g_*[c] = f_*[c]$ trong homology, và do đó $f_* = g_*$.

**Conclusion:** g_*[c] - f_*[c] = 0 in H_n. ⇒ f_* = g_*. ✓

**Powerful:** Reduces many computations to homotopy equivalent spaces!

---

## 🧮 Examples và Computations

### Example 1: Point

X = {pt}.

**Singular simplices:** σₙ: Δⁿ → {pt} (unique constant map).

C_n(X) = ℤ (rank 1).

**Boundary:** All ∂ = 0 (only one n-simplex).

**Homology:**  
H₀(pt) = ℤ (cycles mod boundaries = ℤ/0)  
H_n(pt) = 0 (n > 0)

**Connected, no higher holes.**

---

### Example 2: Contractible Space

X contractible ⇒ X ≃ point.

**Homotopy invariance:**  
H_n(X) ≅ H_n(point).

**Result:**  
H₀(X) = ℤ, H_n(X) = 0 (n > 0).

**Examples:** ℝⁿ, disk Dⁿ, star-shaped regions.

---

### Example 3: Sphere Sⁿ

**Result (to be proved later):**

$$
H_k(S^n) = \begin{cases}
\mathbb{Z} & k = 0, n \\
0 & \text{otherwise}
\end{cases}
$$

**Interpretation:**
- Connected (H₀ = ℤ)
- n-dimensional hole (Hₙ = ℤ)
- No other holes

---

### Example 4: Circle S¹

H₀(S¹) = ℤ (connected)  
H₁(S¹) = ℤ (1-dimensional loop)  
H_n(S¹) = 0 (n ≥ 2)

**Generator of H₁:** Loop wrapping once around circle.

---

## 🧠 Fundamental Papers & References

### Classic Works

1. **Henri Poincaré** - *"Analysis Situs"* (1895-1904)  
   *Introduced homology concepts*

2. **Solomon Lefschetz** - *"Topology"* (1930)  
   *Singular homology development*

3. **Samuel Eilenberg** - *"Singular homology theory"* (1944)  
   *Rigorous modern formulation*

### Textbooks

4. **Allen Hatcher** - *Algebraic Topology*, **§2.1: Singular Homology**

5. **Glen E. Bredon** - *Topology and Geometry*, **Chapter IV**

6. **James R. Munkres** - *Elements of Algebraic Topology*, **Chapter 4**

7. **Edwin H. Spanier** - *Algebraic Topology*, **Chapter 4**

---

## 🔗 Applications

### Topological Data Analysis
**Computational Homology:** Algorithms compute singular homology của data. Detect features, clusters, voids.

### Algebraic Geometry
**Sheaf Cohomology:** Generalization via sheaves. Fundamental tool in modern geometry.

### Physics - Field Theory
**Characteristic Classes:** Homology/cohomology classify gauge fields, anomalies.

---

## 🧩 Exercises

### Standard Simplex

1. **Verify:** Δ¹ = [0,1] via coordinate transformation.

2. **Face Maps:**  
   Compute δ₀, δ₁, δ₂: Δ¹ → Δ² explicitly.

3. **Boundary:**  
   Δ² có 3 faces. Verify each = image of some δᵢ.

### Singular Simplices

4. **Count:**  
   X = {pt}. How many distinct singular n-simplices? (One!)

5. **Circle:**  
   Give example singular 1-simplex σ: Δ¹ → S¹ wrapping twice.

6. **Image:**  
   Can singular simplex be surjective? Give example or explain why not.

### Boundary

7. **Compute:**  
   σ: Δ² → X. Write ∂σ explicitly using δᵢ.

8. **Verify ∂² = 0:**  
   σ: Δ² → X. Compute ∂(∂σ) = 0 step by step.

### Functoriality

9. **Induced Map:**  
   f: S¹ → S¹ (identity). What is f_*: H₁(S¹) → H₁(S¹)?

10. **Composition:**  
    Verify (f ∘ g)_* = f_* ∘ g_* in simple example.

### Homotopy Invariance

11. **Contractible:**  
    X = ℝ². Use homotopy invariance: H_n(ℝ²) = ?

12. **Cylinder:**  
    S¹ × [0,1] ≃ S¹. Compute H_n.

### Comparison

13. **Simplicial vs Singular:**  
    For simplicial complex K, why H_n^{simplicial}(K) ≅ H_n^{singular}(|K|)?

### Advanced

14. **Exactness:**  
    Research: Long exact sequence của pair (X, A).

15. **Relative Homology:**  
    H_n(X, A) measures "holes in X not coming from A."

---

## 📚 Further Reading

- **Hatcher, §2:** Comprehensive treatment
- **Bredon, Chapter IV:** Advanced perspective
- **Spanier:** Encyclopedic reference

---

## 🎓 Summary

**Singular homology = universal homology theory:**

✅ **Singular simplices:** σ: Δⁿ → X (any continuous map)  
✅ **Chain groups C_n(X):** Free abelian on singular simplices  
✅ **Boundary ∂:** Via face maps, ∂² = 0  
✅ **Homology H_n(X):** ker(∂) / im(∂)  
✅ **Functorial:** f: X → Y induces f_*  
✅ **Homotopy invariant:** X ≃ Y ⇒ H_n(X) ≅ H_n(Y)  
✅ **Universal:** Works for ANY space  

**Tiếp theo:** Computing homology systematically!

---

**Previous:** [Lecture 07.00: Simplicial Homology](/contents/vi/topology-chapter07/07_00_Simplicial_Homology/)  
**Next:** [Lecture 07.02: Homology Computations](/contents/vi/topology-chapter07/07_02_Homology_Computations/)
